---
title: Documento técnico de segurança do Power BI
description: Documento técnico que aborda e descreve a arquitetura e a implementação de segurança para o Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/24/2019
LocalizationGroup: Conceptual
ms.openlocfilehash: 50c8416573b995c34d62129d11926e70d9d4242d
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381405"
---
# <a name="power-bi-security-whitepaper"></a>Documento técnico de segurança do Power BI

**Resumo:** Power BI é um serviço de software online *(SaaS*, ou Software como um Serviço) que permite criar facilmente e rapidamente dashboards de Business Intelligence, relatórios, conjuntos de dados e visualizações. Com o Power BI, pode ligar a várias origens de dados diferentes, combinar e formatar os dados dessas ligações, e criar relatórios e dashboards que podem ser partilhados com outras pessoas.

**Escritor:** David Iseminger

**Revisores Técnicos:** Pedram Rezaei, Cristian Petculescu, Siva Harinath, Tod Manning, Haydn Richardson, Adam Wilson, Ben Childs, Robert Bruckner, Sergei Gundorov, Kasper de Jonge

**Aplica-se a:** Power BI SaaS, Power BI Desktop, Power BI Incorporado, Power BI Premium

> [!NOTE]
> Pode guardar ou imprimir este documento técnico ao selecionar **Imprimir** no seu browser e, em seguida, ao selecionar **Guardar como PDF**.

## <a name="introduction"></a>Introdução

O **Power BI** é uma oferta de serviço de software online (_SaaS_ ou Software como Serviço) da Microsoft que permite criar rápida e facilmente dashboards, relatórios, conjuntos de dados e visualizações de Business Intelligence de gestão personalizada. Com o Power BI, pode ligar a várias origens de dados diferentes, combinar e formatar os dados dessas ligações, e criar relatórios e dashboards que podem ser partilhados com outras pessoas.

O serviço Power BI é regido pelos [Termos do Microsoft Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31) e a [Declaração de Privacidade do Microsoft Enterprise](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx). Para obter a localização do processamento de dados, veja os termos da Localização do Processamento de Dados nos Termos do Microsoft Online Services. No que toca a informações de conformidade, o [Microsoft Trust Center](https://www.microsoft.com/trustcenter) é o principal recurso para o Power BI. A equipa do Power BI está empenhada em proporcionar aos seus clientes produtividade e as mais recentes inovações. O Power BI encontra-se atualmente no nível D do Quadro de Conformidade do [Instituto 365](https://download.microsoft.com/download/1/4/3/1434ABAB-B8E9-412D-8C3A-187B5FCB7A2F/Compliance%20Framework%20document.pdf).

Este artigo descreve a segurança do Power BI ao fornecer uma explicação sobre a arquitetura do Power BI e sobre como os utilizadores efetuam a autenticação no Power BI e são estabelecidas as ligações de dados, e, em seguida, ao descrever como o Power BI armazena e move dados através do serviço. A última secção é dedicada a perguntas e respostas relacionadas com segurança.

## <a name="power-bi-architecture"></a>Arquitetura do Power BI

O serviço **Power BI** baseia-se no **Azure**, a [plataforma de computação na cloud](https://azure.microsoft.com/overview/what-is-azure/) da Microsoft. O Power BI está a ser implementado em vários datacenters em todo o mundo. Existem diversas implementações ativas disponibilizadas para clientes nas regiões servidas por esses datacenters e um número equivalente de implementações passivas que funcionam como cópias de segurança para cada implementação ativa.

Cada implementação do Power BI consiste em dois clusters – um cluster de Front-end da Web (**WFE**) e um cluster de **Back-end**. Estes dois clusters são apresentados na seguinte imagem e servem de base para o resto deste artigo. 

![O WFE e o Back-end](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

O Power BI utiliza o Azure Active Directory (**AAD**) para a gestão e a autenticação de contas. O Power BI também utiliza o **Gestor de Tráfego do Azure (ATM)** para direcionar o tráfego de utilizador para o datacenter mais próximo, determinado pelo registo DNS do cliente que está a tentar ligar, para o processo de autenticação e para transferir conteúdo e ficheiros estáticos. O Power BI utiliza o WFE geograficamente mais próximo para distribuir eficientemente os conteúdos e ficheiros estáticos necessários aos utilizadores, com exceção dos visuais power BI que são entregues através da Rede de Entrega de **Conteúdos Azure (CDN)** .

### <a name="the-wfe-cluster"></a>O Cluster WFE

O cluster **WFE** gere o processo de ligação e autenticação inicial do Power BI, através do AAD para autenticar os clientes e fornecer tokens para ligações de cliente subsequentes ao serviço Power BI.

![O Cluster WFE](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

Quando os utilizadores tentam ligar ao serviço Power BI, o serviço DNS do cliente poderá comunicar com o **Gestor de Tráfego do Azure** para localizar o datacenter mais próximo com uma implementação do Power BI. Para obter mais informações sobre este processo, veja [Método de encaminhamento de tráfego de desempenho do Gestor de Tráfego](https://azure.microsoft.com/documentation/articles/traffic-manager-routing-methods/#performance-traffic-routing-method).

O cluster WFE mais próximo do utilizador gere a sequência de início de sessão e autenticação (descrita mais adiante neste artigo) e fornece um token do AAD ao utilizador assim que a autenticação for bem-sucedida. O componente ASP.NET no cluster WFE analisa o pedido para determinar a organização à qual o utilizador pertence e, em seguida, consulta o **Serviço Global** do Power BI. O Serviço Global é uma Tabela do Azure única partilhada entre todos os clusters WFE e de Back-end em todo o mundo que mapeia os utilizadores e as organizações dos clientes ao datacenter que aloja o respetivo inquilino do Power BI. O WFE especifica no browser que cluster de Back-end aloja o inquilino da organização. Assim que um utilizador é autenticado, ocorrem interações de cliente subsequentes diretamente com o cluster de Back-end, sem que o WFE seja um intermediário para esses pedidos.

### <a name="the-power-bi-back-end-cluster"></a>O Cluster de Back-end do Power BI

O cluster de **Back-end** é como os clientes autenticados interagem com o serviço Power BI. O cluster de **Back-end** gere as visualizações, os dashboards do utilizador, os conjuntos de dados, os relatórios, o armazenamento de dados, as ligações de dados, a atualização de dados e outros aspetos da interação com o serviço Power BI.

![O Cluster de Back-end](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

A **Função do Gateway** age como um gateway entre os pedidos de utilizador e o serviço Power BI. Os utilizadores não interagem diretamente com nenhuma função, exceto a Função do Gateway.

**Importante:** É imperativo notar que _apenas_ as funções Azure API Management **(APIM)** e Gateway **(GW)** são acessíveis através da Internet pública. Fornecem autenticação, autorização, proteção contra DDoS, Limitação, Balanceamento de Carga, Encaminhamento e outras capacidades.

A linha pontilhada na imagem do cluster de **Back-end**, representada acima, esclarece o limite entre as duas únicas funções que podem ser acedidas pelos utilizadores (à esquerda da linha ponteada) e as funções que só podem ser acedidas pelo sistema. Quando um utilizador autenticado se liga ao Serviço Power BI, a ligação e qualquer pedido feito pelo cliente são aceites e geridos pela **Função do Gateway** e pela **Gestão de API do Azure**, que em seguida interage em nome do utilizador com o resto do Serviço Power BI. Por exemplo, quando um cliente tenta ver um dashboard, a **Função do Gateway** aceita esse pedido e envia separadamente um pedido para a **Função de Apresentação** para obter os dados necessários para o browser compor o dashboard.

![A função de Gateway](media/whitepaper-powerbi-security/powerbi-security-whitepaper_04.png)

### <a name="power-bi-premium"></a>Power BI Premium

O **Power BI Premium** proporciona uma área de trabalho de serviço dedicada, aprovisionada e particionada aos subscritores que necessitam de recursos dedicados para as respetivas atividades do Power BI. Quando um cliente se inscreve numa subscrição do Power BI Premium, a capacidade Premium é criada através do **Azure Resource Manager**. A implementação dessa subscrição atribui um conjunto de máquinas virtuais proporcional ao nível da subscrição, no datacenter em que o respetivo inquilino do Power BI está alojado (com exceção de ambientes Multi-Geo, conforme descrito mais adiante neste documento), iniciado como uma implementação do **Azure Service Fabric**.

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

Após a criação, todas as comunicações com o cluster Premium são encaminhadas através do cluster de Back-end do Power BI, sendo estabelecida uma ligação às máquinas virtuais dedicadas da subscrição do **Power BI Premium** do cliente.

### <a name="data-storage-architecture"></a>Arquitetura de armazenamento de dados

O Power BI utiliza dois repositórios principais para armazenar e gerir dados: os dados carregados pelos utilizadores são normalmente enviados para o armazenamento de **Blobs do Azure**, enquanto todos os metadados e os artefactos do próprio sistema são armazenados com uma firewall na **Base de Dados SQL do Azure**.

![Armazenamento de dados](media/whitepaper-powerbi-security/powerbi-security-whitepaper_06.png)

Por exemplo, quando um utilizador importa um livro do Excel para o serviço Power BI, é criada uma base de dados em tabela do Analysis Services na memória e os dados são armazenados na memória durante, no máximo, uma hora (ou até que a pressão de memória ocorra no sistema). Os dados são também enviados para o armazenamento de **Blobs do Azure**.

Os metadados sobre a subscrição do Power BI de um utilizador, como dashboards, relatórios, origens de dados recentes, áreas de trabalho, informações organizacionais e informações sobre o inquilino, assim como outros metadados sobre o sistema, são armazenados e atualizados na **Base de Dados SQL do Azure**. Todas as informações armazenadas na Base de Dados SQL do Azure são totalmente encriptadas com a tecnologia de [Encriptação de Dados Transparente (TDE) do SQL do Azure](https://msdn.microsoft.com/library/dn948096.aspx). Todos os dados armazenados no armazenamento de Blobs do Azure também são encriptados. Existem mais informações sobre o processo de carregamento, armazenamento e transferência de dados na secção **Armazenamento e Movimento de Dados**.

## <a name="tenant-creation"></a>Criação do Inquilino

Um inquilino é uma instância dedicada do serviço Azure AD que uma organização recebe e detém quando se inscreve num serviço na cloud da Microsoft, como o Azure, o Microsoft Intune, o Power BI ou o Office 365. Cada inquilino do Azure AD é diferente e separado de outros inquilinos do Azure AD.

Um inquilino aloja os utilizadores de uma empresa e as informações sobre os mesmos, ou seja, as suas palavras-passe, dados de perfil de utilizador, permissões, etc. Contém também grupos, aplicações e outras informações relativas a uma organização e à sua segurança. Para obter mais informações, veja [O que é um inquilino do Windows Azure AD?](https://msdn.microsoft.com/library/azure/jj573650.aspx#BKMK_WhatIsAnAzureADTenant).

Um inquilino do Power BI é criado no datacenter considerado mais próximo do país (ou da região) e são fornecidas informações de estado para o inquilino no Azure Active Directory, que foi fornecido quando o serviço do Office 365 ou Power BI foi inicialmente aprovisionado. O inquilino do Power BI não é atualmente movido dessa localização do datacenter.

### <a name="multiple-geographies-multi-geo"></a>Múltiplas Localizações Geográficas (Multi-Geo)

Algumas organizações exigem uma presença do Power BI em múltiplas localizações geográficas ou regiões com base nas necessidades empresariais. Por exemplo, uma empresa pode ter o seu inquilino Power BI nos Estados Unidos, mas também pode fazer negócios noutras áreas geográficas, como a Austrália, e precisa de certos dados do Power BI para permanecer em repouso nessa região remota para cumprir as normas locais. A partir do segundo semestre de 2018, as organizações com o seu arrendatário de uma só geografia também podem fornecer e aceder aos recursos do Power BI localizados noutra geografia. Esta funcionalidade é denominada **Multi-Geo** para conveniência e referência ao longo deste documento.

O artigo mais atual e primário para informações multi-geo é o [suporte multi-Geo configurado para artigo Power BI Premium.](service-admin-premium-multi-geo.md) 

Existem múltiplos detalhes técnicos que devem ser avaliados no contexto das leis e regulamentos locais quando operam em diferentes geografias. Estes detalhes incluem o seguinte:

- Uma camada de execução de consulta remota está alojada na região de capacidade remota, para garantir que o modelo de dados, caches e a maioria do processamento de dados permaneçam na região de capacidade remota. Existem algumas exceções, conforme detalhado no artigo [multi-geo para Power BI Premium.](service-admin-premium-multi-geo.md)
- Um texto de consulta em cache e resultado correspondente armazenado numa região remota permanecerão nessa região em repouso, no entanto outros dados em trânsito podem ir e vir entre várias geografias.
- Os ficheiros PBIX ou XLSX que são publicados (carregados) para uma capacidade multi-geodo do serviço Power BI podem resultar na armazenamento temporária de uma cópia no armazenamento da Blob Azure na região de inquilinos do Power BI. Nestas circunstâncias, os dados são encriptados utilizando a Encriptação do Serviço de Armazenamento Azure (SSE), e a cópia está programada para recolha de lixo assim que o processamento e transferência de conteúdo de ficheiros para a região remota estiver em conclusão. 
- Ao mover dados através de regiões num ambiente multi-geo, a instância dos dados na região fonte será eliminada dentro de 7 a 30 dias. 

### <a name="datacenters-and-locales"></a>Datacenters e Regiões

O Power BI é disponibilizado em determinadas regiões com base no local onde os clusters do Power BI estão implementados em datacenters regionais. A Microsoft tenciona expandir a sua infraestrutura do Power BI para datacenters adicionais.

As seguintes ligações fornecem informações adicionais sobre os datacenters do Azure.

- [Regiões do Azure](https://azure.microsoft.com/regions/) – informações sobre a presença global e as localizações do Azure
- [Serviços do Azure, por região](https://azure.microsoft.com/regions/#services) – uma lista completa dos serviços do Azure (tanto serviços de infraestrutura como serviços de plataforma) disponibilizados pela Microsoft em cada região.

Atualmente, o serviço Power BI está disponível em regiões específicas, servido por datacenters como descrito no [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). A seguinte ligação apresenta um mapa dos datacenters do Power BI. Pode pairar com o ponteiro do rato por cima de uma região para ver os datacenters da mesma:

* [Datacenters do Power BI](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)

A Microsoft também fornece datacenters para soberanias. Para obter mais informações sobre a disponibilidade do serviço Power BI para clouds nacionais, veja as [clouds nacionais do Power BI](https://powerbi.microsoft.com/clouds/).

Para obter mais informações sobre o local onde os seus dados são armazenados e como são utilizados, consulte o [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/Transparency/default.aspx#_You_know_where). Os compromissos sobre a localização dos dados de clientes inativos encontram-se especificados nos **Termos do Processamento de Dados** dos [Termos do Microsoft Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31).

## <a name="user-authentication"></a>Autenticação de Utilizadores

A autenticação de utilizadores no serviço Power BI consiste numa série de pedidos, respostas e redirecionamentos entre o browser do utilizador e o serviço Power BI ou os serviços do Azure utilizados pelo Power BI. Essa sequência descreve o processo de autenticação de utilizadores no Power BI. Para obter mais informações sobre as opções para os modelos de autenticação de utilizadores de uma organização (modelos de início de sessão), veja [Choosing a sign-in model for Office 365](https://blogs.office.com/2014/05/13/choosing-a-sign-in-model-for-office-365/) (Escolher um modelo de início de sessão para o Office 365).

### <a name="authentication-sequence"></a>Sequência de Autenticação

A sequência de autenticação de utilizadores no serviço Power BI ocorre conforme descrito nos seguintes passos, ilustrados nas imagens abaixo.

1. Um utilizador inicia uma ligação ao serviço Power BI num browser ao escrever o endereço do Power BI na barra de endereço (como https://app.powerbi.com)) ou ao selecionar _Iniciar Sessão_ na página de destino do Power BI (https://powerbi.microsoft.com)). A ligação é estabelecida através de TLS 1.2 e HTTPS, e todas as comunicações subsequentes entre o browser e o serviço Power BI utilizam HTTPS. O pedido é enviado para o **Gestor de Tráfego do Azure**.

2. O **Gestor de Tráfego do Azure** verifica o registo DNS do utilizador para determinar o datacenter mais próximo no qual o Power BI está implementado e envia uma resposta para o DNS com o endereço IP do cluster WFE para o qual o utilizador deve ser enviado.

3. Em seguida, o WFE redireciona o utilizador para a página de início de sessão do Microsoft Online Services.

    ![Sequência de autenticação](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

1. Assim que o utilizador é autenticado, a página de início de sessão redireciona o utilizador para o **cluster WFE** do serviço Power BI mais próximo anteriormente determinado.

2. O browser submete um cookie obtido do início de sessão com êxito para o Microsoft Online Services, sendo inspecionado pelo **serviço ASP.NET** no **cluster WFE**.

3. O cluster WFE contacta o serviço do **Azure Active Directory** (**AAD**) para autenticar a subscrição do serviço Power BI do utilizador e obter um token de segurança do AAD. Quando o AAD devolve a autenticação bem-sucedida do utilizador e um token de segurança do AAD, o cluster WFE consulta o **Serviço Global do Power BI**, que mantém uma lista de inquilinos e das respetivas localizações de clusters de Back-end do Power BI, e determina que cluster do serviço Power BI contém o inquilino do utilizador. Em seguida, o cluster WFE direciona o utilizador para o cluster do Power BI, onde o seu inquilino se encontra, e devolve uma coleção de itens para o browser do utilizador:

      - O **token de segurança do AAD**
      - **Informações de sessão**
      - O endereço Web do cluster de **Back-end** com o qual o utilizador pode comunicar e interagir

1. Em seguida, o browser do utilizador contacta a CDN do Azure especificada ou, para alguns dos ficheiros, o WFE para transferir a coleção de ficheiros comuns especificados necessários para permitir a interação do browser com o serviço Power BI. A página do browser passa a incluir o token do AAD, informações de sessão, a localização do cluster de Back-end associado e a coleção de ficheiros transferidos da CDN do Azure e do cluster WFE, enquanto durar a sessão do browser com o serviço Power BI.

![Interação da CDN do Azure](media/whitepaper-powerbi-security/powerbi-security-whitepaper_09.png)

Após a conclusão desses itens, o browser inicia o contacto com o cluster de Back-end especificado e é iniciada a interação do utilizador com o serviço Power BI. Deste ponto em diante, todas as chamadas para o serviço Power BI são efetuadas com o cluster de Back-end especificado e todas as chamadas incluem o token do AAD do utilizador. O token do AAD tem um tempo limite de uma hora. O WFE atualiza periodicamente o token se a sessão de um utilizador permanecer aberta, para manter o acesso.

## <a name="data-storage-and-movement"></a>Armazenamento e Movimento de Dados

No serviço Power BI, os dados encontram-se _inativos_ (dados disponíveis para um utilizador do Power BI que não estão a ser alvo de ações) ou _em processamento_ (por exemplo, consultas em execução, ligações de dados e modelos que estão a ser alvo de ações, dados e/ou modelos que estão a ser carregados para o serviço Power BI e outras ações que os utilizadores ou o serviço Power BI poderá executar nos dados que estão a ser ativamente acedidos ou atualizados). Os dados que se encontram em processamento são conhecidos como _dados em processamento_. Os dados inativos no Power BI são encriptados. Os dados que se encontram em trânsito, ou seja, que estão a ser enviados ou recebidos pelo serviço Power BI, também são encriptados.

O serviço Power BI também gere os dados de forma diferente consoante sejam acedidos com uma **DirectQuery** ou importados. Por conseguinte, existem duas categorias de dados de utilizador para o Power BI: dados acedidos por DirectQuery e dados não acedidos por DirectQuery.

Uma **DirectQuery** é uma consulta para a qual a consulta de um utilizador do Power BI foi traduzida da linguagem Data Analysis Expressions (DAX) da Microsoft, ou seja, a linguagem utilizada pelo Power BI e outros produtos da Microsoft para criar consultas, e que se encontra na linguagem de dados nativa da origem de dados (por exemplo, T-SQL ou outras linguagens de bases de dados nativas). Os dados associados a uma DirectQuery são armazenados apenas por referência, o que significa que os dados de origem não são armazenados no Power BI quando a DirectQuery não está ativa (exceto para os dados de visualização utilizados para apresentar dashboards e relatórios, conforme descrito na secção _Dados em o processamento (movimento de dados)_ abaixo). Em vez disso, são armazenadas as referências aos dados de DirectQuery que permitem aceder a esses dados quando a DirectQuery é executada. Uma DirectQuery contém todas as informações necessárias para executar a consulta, incluindo a cadeia de ligação e as credenciais utilizadas para aceder às origens de dados, o que permite que a DirectQuery ligue às origens de dados incluídas para atualização automática. Com uma DirectQuery, as informações de modelos de dados subjacentes são incorporadas na mesma.

Uma consulta para um conjunto de dados importados consiste numa coleção de consultas DAX que _não_ são traduzidas diretamente para a linguagem nativa de qualquer origem de dados subjacente. As consultas de importação não incluem as credenciais para os dados subjacentes e estes são carregados para o serviço Power BI, a menos que se tratem de dados no local acedidos através de um [Power BI Gateway](service-gateway-onprem.md) e, nesse caso, a consulta só armazena referências aos dados no local.

A seguinte tabela descreve os dados do Power BI com base no tipo de consulta utilizado. Um **X** indica a presença de dados do Power BI ao utilizar o tipo de consulta associado.


|  |Importar  |DirectQuery  |Live Connect  |
|---------|---------|---------|---------|
|Esquema     |     X    |    X     |         |
|Dados da linha     |    X     |         |         |
|Colocação em cache dos dados dos elementos visuais     |    X     |     X    |    X     |

A distinção entre uma DirectQuery e outras consultas determina a forma como o serviço Power BI processa os dados inativos e se a própria consulta é encriptada. As secções seguintes descrevem os dados inativos e em movimento, e explicam a encriptação, a localização e o processo de tratamento de dados.

### <a name="data-at-rest"></a>Dados inativos

Quando os dados estão inativos, o serviço Power BI armazena conjuntos de dados, relatórios e mosaicos de dashboards da forma descrita nas subsecções seguintes. Conforme mencionado anteriormente, os dados inativos no Power BI são encriptados. ETL corresponde a Extrair, Transformar e Carregar nas secções seguintes.

#### <a name="encryption-keys"></a>Chaves de Encriptação

- As chaves de encriptação para as chaves de Blobs do Azure são armazenadas encriptadas no Azure Key Vault.
- As chaves de encriptação da tecnologia TDE das Bases de Dados SQL do Azure são geridas pelo próprio SQL do Azure.
- As chave de encriptação do serviço Movimento de Dados e do gateway de dados no local são armazenadas da seguinte forma:
  - No gateway de dados no local, na infraestrutura do cliente – para origens de dados no local
  - Na Função de Movimento de Dados – para origens de dados baseadas na cloud

A chave de encriptação de conteúdo (CEK) utilizada para encriptar o Armazenamento De Blob microsoft Azure é uma chave de 256 bits gerada aleatoriamente. O algoritmo que a CEK utiliza para encriptar o conteúdo é o AES\_CBC\_256.

A Chave de Encriptação da Chave (KEK) utilizada para posteriormente encriptar a CEK é uma chave de 256 bits predefinida. O algoritmo da KEK para encriptar a CEK é o A256KW.

As chaves de encriptação de gateways baseadas na chave de recuperação nunca saem de uma infraestrutura no local. O Power BI não consegue aceder aos valores das credenciais encriptadas no local e não consegue intercetar essas credenciais. Os clientes Web encriptam as credenciais com uma chave pública associada ao gateway específico com o qual comunica.

Para origens de dados baseado na cloud, a Função de Movimento de Dados encripta as chaves de encriptação com os métodos [Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx). Para saber mais, veja [Always Encrypted database feature](https://msdn.microsoft.com/library/mt163865.aspx) (Funcionalidade de base de dados Always Encrypted).

#### <a name="datasets"></a>Conjuntos de dados

1. Metadados (tabelas, colunas, medidas, cálculos, cadeias de ligação, etc.)

    a. Para o Analysis Services no local, nada é armazenado no serviço, exceto uma referência a essa base de dados armazenada e encriptada no SQL do Azure.

    b. Todos os outros metadados de ETL e DirectQuery, e Dados Push são encriptados e armazenados no armazenamento de Blobs do Azure.

1. Credenciais para as origens de dados originais
  
      a. Analysis Services no local – não são necessárias credenciais e, por conseguinte, não são armazenadas credenciais.

      b. DirectQuery – se o modelo for criado no serviço diretamente, será armazenado na cadeia de ligação e encriptado no Blob do Azure; se o modelo for importado do Power BI Desktop, as credenciais serão armazenadas encriptadas na Base de Dados SQL do Azure do Movimento de Dados. A chave de encriptação é armazenada no computador com o Gateway na infraestrutura do cliente.

      c. Dados enviados por push – não aplicável

      d. ETL

      - Para o **Salesforce** ou o **OneDrive** – os tokens de atualização são armazenados encriptados na Base de Dados SQL do Azure do serviço Power BI.
      - Caso contrário:
        - Se o conjunto de dados estiver definido para atualização, as credenciais serão armazenadas encriptadas na Base de Dados SQL do Azure do Movimento de Dados. A chave de encriptação é armazenada no computador com o Gateway na infraestrutura do cliente.
        - Se o conjunto de dados não estiver definido para atualização, não haverá credenciais armazenadas para as origens de dados.

1. Dados

    a. Analysis Services no local e DirectQuery – nada é armazenado no serviço Power BI.

    b. ETL – encriptação no armazenamento de Blobs do Azure, mas todos os dados atualmente no armazenamento de Blobs do Azure do serviço Power BI utilizam a [Encriptação do Serviço de Armazenamento (SSE) do Azure](https://docs.microsoft.com/azure/storage/common/storage-service-encryption), também conhecida como encriptação do lado do servidor. A Multi-Geo também utiliza a SSE.

    c. Dados Push v1 – encriptação no armazenamento de Blobs do Azure, mas todos os dados atualmente no armazenamento de Blobs do Azure, no serviço Power BI, utilizam a [Encriptação do Serviço de Armazenamento (SSE) do Azure](https://docs.microsoft.com/azure/storage/common/storage-service-encryption), também conhecida como encriptação do lado do servidor. A Multi-Geo também utiliza a SSE. Os dados push v1 foram descontinuados a partir de 2016. 

    d. Dados Push v2 – armazenamento encriptado no SQL do Azure.

O Power BI utiliza a abordagem de encriptação do lado do cliente, ao empregar o modo de encadeamento de blocos de cifras (CBC) com a norma AES (Advanced Encryption Standard) para encriptar o respetivo armazenamento de Blobs do Azure. [Saiba mais sobre a encriptação do lado do cliente](https://azure.microsoft.com/documentation/articles/storage-client-side-encryption/).

O Power BI proporciona a monitorização da integridade dos dados das seguintes formas:

* Para dados inativos no SQL do Azure, o Power BI utiliza o DBCC, a TDE e a soma de verificação de páginas constante como parte das ofertas nativas do SQL.

* Para dados inativos no armazenamento de Blobs do Azure, o Power BI utiliza a encriptação do lado do cliente e o HTTPS para transferir dados para o armazenamento, o que inclui verificações de integridade durante a obtenção dos dados. [Saiba mais sobre a segurança do armazenamento de Blobs do Azure](https://azure.microsoft.com/documentation/articles/storage-security-guide/).

#### <a name="reports"></a>Reports (Relatórios)

1. Metadados (definição do relatório)

   a. Os relatórios podem ser do Excel, para relatórios do Office 365, ou do Power BI. O seguinte aplica-se aos metadados com base no tipo de relatório:
        
    &ensp; &ensp;. Os metadados do Excel Report são armazenados encriptados no SQL Azure. Os metadados também estão armazenados no Office 365.

    &ensp; &ensp; b. Os relatórios power BI são armazenados encriptados na base de dados Azure SQL.

2. Dados estáticos

   Os dados estáticos incluem artefactos como imagens de fundo e visuais power BI.

    &ensp; &ensp;. Para relatórios criados com o Excel para o Office 365, nada é armazenado.

    &ensp; &ensp; b. Para relatórios do Power BI, os dados estáticos são armazenados e encriptados no armazenamento de Blobs do Azure.

3. caches

    &ensp; &ensp;. Para relatórios criados com o Excel para o Office 365, nada é colocado em cache.

    &ensp; &ensp; b. Para relatórios do Power BI, os dados dos elementos visuais apresentados são colocados em cache e encriptados na Base de Dados SQL do Azure.
 

4. Ficheiros do Power BI Desktop (.pbix) ou do Excel (.xlsx) originais publicados no Power BI

    Por vezes, uma cópia ou uma cópia sombra dos ficheiros .xlsx ou .pbix é armazenada no armazenamento de Blobs do Azure do Power BI e, quando isso ocorre, os dados são encriptados. Todos esses relatórios armazenados no serviço Power BI, no armazenamento de Blobs do Azure, utilizam a [Encriptação do Serviço de Armazenamento (SSE) do Azure](https://docs.microsoft.com/azure/storage/common/storage-service-encryption), também conhecida como encriptação do lado do servidor. A Multi-Geo também utiliza a SSE.

#### <a name="dashboards-and-dashboard-tiles"></a>Dashboards e Mosaicos de Dashboards

1. Caches – normalmente, os dados necessários para os elementos visuais no dashboard são colocados em cache e armazenados encriptados na Base de Dados SQL do Azure. Outros mosaicos, como elementos visuais afixados do Excel ou do SQL Server Reporting Services (SSRS), são armazenados no Blob do Azure como imagens e também são encriptados.

2. Dados estáticos – que incluem artefactos como imagens de fundo e visuais Power BI que são armazenados, encriptados, no armazenamento do Azure Blob.

Independentemente do método de encriptação utilizado, a Microsoft gere a encriptação de chaves em nome dos clientes num arquivo de segredos ou no Azure Key Vault.

### <a name="data-transiently-stored-on-non-volatile-devices"></a>Dados Armazenados transitoriamente em Dispositivos Não Voláteis

Dispositivos não voláteis são dispositivos que têm memória que persiste sem energia constante. Segue-se uma descrição dos dados armazenados transitoriamente em dispositivos não voláteis. 

#### <a name="datasets"></a>Conjuntos de dados

1. Metadados (tabelas, colunas, medidas, cálculos, cadeias de ligação, etc.)

2. Alguns artefactos relacionados com esquemas podem ser armazenados no disco dos nós de computação durante um período de tempo limitado. Alguns artefactos também podem ser armazenados não encriptados na Cache de Redis do Azure durante um período de tempo limitado.

3. Credenciais para as origens de dados originais

    a. Analysis Services no local – nada é armazenado.

    b. DirectQuery – se o modelo for criado no serviço diretamente, será armazenado na cadeia de ligação num formato encriptado, com a chave de encriptação armazenada em texto não encriptado no mesmo local (juntamente com as informações encriptadas); se o modelo for importado do Power BI Desktop, as credenciais não serão armazenadas em dispositivos não voláteis.

    > [!NOTE]
    > A funcionalidade de criação do modelo do lado do serviço foi descontinuada a partir de 2017.

    c. Dados enviados por push – nenhumas (não aplicável).

    d. ETL – nenhumas (nada é armazenado no nó de computação nem o procedimento é diferente do explicado na secção **Dados Inativos** acima).
4. Dados

    Alguns artefactos de dados podem ser armazenados no disco dos nós de computação durante um período de tempo limitado.

### <a name="data-in-process"></a>Dados em processamento

Os dados encontram-se em processamento quando estão a ser utilizados ou acedidos ativamente por um utilizador. Por exemplo, os dados encontram-se em processamento quando um utilizador acede a um conjunto de dados, consulta ou modifica um dashboard ou um relatório, ou quando ocorre uma atualização ou outras atividades de acesso a dados. Quando qualquer um desses eventos ocorre e os dados são colocados em processamento, a **Função de Dados** no serviço Power BI cria uma base de dados do Analysis Services (AS) na memória e o conjunto de dados é carregado para a mesma. Independentemente de o conjunto de dados ser ou não baseado numa DirectQuery, os dados carregados na base de dados do AS encontram-se não encriptados, para permitir o acesso à **Função de Dados**, e são mantidos na memória para acesso posterior até que o serviço Power BI deixe de necessitar do conjunto de dados. Para os clientes com uma subscrição do Power BI Premium, o Power BI cria uma base de dados do Analysis Services (AS) na memória, na coleção de máquinas virtuais do Power BI do cliente aprovisionada em separado.

Assim que os dados forem alvo de ações, o que inclui carregar inicialmente os dados para o Power BI, o serviço Power BI poderá colocar em cache os dados de visualização numa **Base de Dados SQL do Azure** encriptada, independentemente de o conjunto de dados ser baseado numa DirectQuery.

Para monitorizar a integridade dos dados em processamento, o Power BI utiliza o HTTPS, TCP/IP e TLS para garantir que os dados são encriptados e mantém a integridade durante o transporte.

## <a name="user-authentication-to-data-sources"></a>Autenticação de Utilizadores para Origens de Dados

Com cada fonte de dados, um utilizador estabelece uma ligação com base no seu login e acede aos dados com essas credenciais. Em seguida, podem criar consultas, dashboards e relatórios com base nos dados subjacentes.

Quando um utilizador partilha consultas, dashboards, relatórios ou qualquer visualização, o acesso a esses dados e visualizações está dependente de as origens de dados subjacentes suportarem a Segurança ao Nível da Função (RLS).

Se uma origem de dados subjacente for adequada para a **Segurança ao Nível da Função (RLS) do Power BI**, o serviço Power BI irá aplicá-la e os utilizadores que não tiverem credenciais suficientes para aceder aos dados subjacentes (por exemplo, uma consulta utilizada num dashboard, num relatório ou noutros artefactos de dados) não irão ver os dados para os quais não têm privilégios suficientes. Se o acesso de um utilizador aos dados subjacentes for diferente do acesso do utilizador que criou o dashboard ou o relatório, as visualizações e outros artefactos serão apenas apresentados com base no nível de acesso que esse utilizador tem aos dados.

Se uma origem de dados **não** aplicar a RLS, as credenciais de início de sessão do Power BI serão aplicadas à origem de dados subjacente ou, se outras credenciais forem fornecidas durante a ligação, essas mesmas credenciais fornecidas serão aplicadas. Quando um utilizador carrega dados para o serviço Power BI de origens de dados sem RLS, os dados são armazenados no Power BI conforme descrito na secção **Armazenamento e Movimento de Dados** deste documento. Para origens de dados sem RLS, quando os dados são partilhados com outros utilizadores (por exemplo, através de um dashboard ou relatório) ou ocorre uma atualização dos dados, as credenciais originais são utilizadas para apresentar ou aceder aos dados.

![Segurança ao nível da função (RLS)](media/whitepaper-powerbi-security/powerbi-security-whitepaper_10.png)

Como exemplo rápido para comparar as origens de dados com e sem RLS, suponha que o Samuel cria um relatório e um dashboard, e que depois os partilha com a Adriana e o Duarte. Se as origens de dados utilizadas no relatório e no dashboard **não** suportarem a RLS, a Adriana e o Duarte poderão ver os dados que o Samuel incluiu no dashboard (que foi carregado para o serviço Power BI) e, em seguida, ambos poderão interagir com os dados. Por outro lado, se o Samuel criar um relatório e um dashboard de origens de dados que suportam a RLS e, em seguida, os partilhar com a Adriana e o Duarte, quando a Adriana tentar ver o dashboard, ocorrerá o seguinte:

1. Uma vez que o dashboard é de uma origem de dados RLS, as visualizações do mesmo serão apresentadas por breves instantes com uma mensagem de &quot;carregamento&quot;, enquanto o serviço Power BI consulta a origem de dados para obter o conjunto de dados atual especificado na cadeia de ligação associada à consulta subjacente do dashboard.

2. Os dados são acedidos e obtidos com base nas credenciais e na função da Adriana, e apenas os dados para os quais a Adriana tem autorização suficiente são carregados para o dashboard e o relatório.

3. As visualizações no dashboard e no relatório são apresentadas com base no nível de função da Adriana.

Se o Duarte acedesse ao dashboard ou ao relatório partilhado, a mesma sequência ocorreria com base no seu nível de função.

## <a name="power-bi-mobile"></a>Power BI Mobile

Power BI Mobile é uma coleção de aplicações projetadas para as três principais plataformas móveis: Android, iOS e Windows Mobile. As considerações de segurança para as aplicações do Power BI Mobile dividem-se em duas categorias:

* Comunicação do dispositivo
* A aplicação e os dados no dispositivo

Relativamente à **comunicação do dispositivo**, todas as aplicações do Power BI Mobile comunicam com o serviço Power BI e utilizam as mesmas sequências de ligação e autenticação utilizadas pelos browsers, que foram descritas anteriormente em detalhe neste documento técnico. As aplicações do Power BI Mobile para iOS e Android iniciam uma sessão de browser na própria aplicação e a aplicação do Windows Mobile apresenta um mediador para estabelecer o canal de comunicação com o Power BI.

A seguinte tabela apresenta o suporte da autenticação baseada em certificados (CBA) do Power BI Mobile, com base na plataforma do dispositivo móvel:

| **Suporte CBA** | **iOS** | **Android** | **Windows** |
| --- | --- | --- | --- |
| **Power BI** (iniciar sessão no serviço) | Suportado | Suportado | Não suportado |
| **ADFS do SSRS** (ligar ao servidor SSRS) | Não suportado | Suportado | Não suportado |

As aplicações do Power BI Mobile comunicam ativamente com o serviço Power BI. É utilizada telemetria para recolher estatísticas de utilização de aplicações móveis e dados semelhantes, que são transmitidos aos serviços utilizados para monitorizar a utilização e a atividade. Não são enviados dados pessoais com os dados de telemetria.

A **aplicação Power BI no dispositivo** armazena dados no dispositivo que facilitam a utilização da aplicação:

* São armazenados tokens do Azure Active Directory e de atualização num mecanismo seguro no dispositivo, com medidas de segurança padrão do setor.

* São colocados em cache dados no armazenados do dispositivo, sem encriptação direta efetuada pela própria aplicação.

* São também armazenadas definições não encriptadas no dispositivo, mas não são armazenados dados efetivos do utilizador.

A cache de dados do Power BI Mobile permanece no dispositivo durante duas semanas ou até a aplicação ser removida, o utilizador terminar sessão no Power BI Mobile ou o utilizador não conseguir iniciar sessão (por exemplo, um evento de expiração de token ou uma alteração de palavra-passe). A cache de dados inclui dashboards e relatórios acedidos anteriormente através da aplicação do Power BI Mobile.

As aplicações do Power BI Mobile não analisam pastas no dispositivo. 

As três plataformas para as quais o Power BI Mobile está disponível suportam o Microsoft Intune, um serviço de software que permite gerir dispositivos e aplicações móveis. Com o Intune ativado e configurado, os dados no dispositivo móvel são encriptados e a própria aplicação Power BI não pode ser instalada num cartão SD. [Saiba mais sobre o Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="power-bi-security-questions-and-answers"></a>Perguntas e Respostas sobre a Segurança do Power BI

Seguem-se perguntas e respostas comuns relacionadas com a segurança do Power BI. Estão organizadas com base na data em que foram adicionadas a este documento técnico para facilitar a sua capacidade de localizar rapidamente novas perguntas e respostas ao atualizar este documento. As perguntas mais recentes são adicionadas ao fim desta lista.

**Como é que os utilizadores se ligam e obtêm acesso às origens de dados ao utilizar o Power BI?**

* **Credenciais de Power BI e credenciais** de domínio: Os utilizadores iniciaram sessão no Power BI através de um endereço de e-mail; quando um utilizador tenta ligar-se a um recurso de dados, o Power BI passa o endereço de e-mail de login Power BI como credenciais. Para recursos ligados por domínio (no local ou baseados na cloud), é efetuada a correspondência do e-mail de início de sessão com um _Nome Principal de Utilizador_ ([UPN](https://msdn.microsoft.com/library/windows/desktop/aa380525(v=vs.85).aspx)) pelo serviço de diretório, para determinar se existem credenciais suficientes para permitir o acesso. Para organizações que utilizam endereços de e-mail profissionais para iniciar sessão no Power BI (o mesmo e-mail que utilizam para iniciar sessão em recursos de trabalho, como _david@contoso.com_ ), o mapeamento pode ocorrer de forma totalmente integrada. Para organizações que não utilizam endereços de e-mail profissionais (como _david@contoso.onmicrosoft.com_ ), é necessário estabelecer o mapeamento do diretório para permitir o acesso a recursos no local com as credenciais de início de sessão do Power BI.

* **Serviços de Análise de Servidores SQL e Power BI:** Para organizações que utilizam no local os Serviços de Análise de Servidores SQL, o Power BI oferece o gateway de dados no local do Power BI (que é um **Gateway**, como referenciado em secções anteriores).  O gateway de dados no local do Power BI pode impor a segurança ao nível da função (RLS) em origens de dados. Para obter mais informações sobre a RLS, veja **Autenticação de Utilizadores para Origens de Dados** mais acima neste documento. Para obter mais informações sobre gateways, consulte o [portal de dados no local](service-gateway-onprem.md).

  Além disso, as organizações podem utilizar o Kerberos para o **início de sessão único** (SSO) e ligar-se facilmente através do Power BI a origens de dados no local, como o SQL Server, SAP HANA e Teradata. Para obter mais informações e os requisitos de configuração específicos, veja [**Use Kerberos for SSO from Power BI to on-premises data sources**](https://docs.microsoft.com/power-bi/service-gateway-kerberos-for-sso-pbi-to-on-premises-data) (Utilizar o Kerberos para SSO através do Power BI para origens de dados no local).

* **Ligações não-domínio**: Para ligações de dados que não sejam unidas ao domínio e não sejam capazes de Segurança de Nível de Função (RLS), o utilizador deve fornecer credenciais durante a sequência de ligação, que o Power BI passa então para a fonte de dados para estabelecer a ligação. Se as permissões forem suficientes, os dados são carregados da origem de dados para o serviço Power BI.

**Como é que os dados são transferidos para o Power BI?**

* Todos os dados pedidos e transmitidos pelo Power BI são encriptados em trânsito através de HTTPS para ligar da origem de dados ao serviço Power BI. É estabelecida uma ligação segura com o fornecedor de dados e apenas quando essa ligação for estabelecida é que os dados percorrerão a rede.

**Como é que o Power BI coloca em cache dados de relatórios, dashboards ou modelos e é garantida a segurança desse processo?**

* Quando uma origem de dados é acedida, o serviço Power BI segue o processo descrito anteriormente na secção **Armazenamento e Movimento de Dados** deste documento.

**Os clientes colocam em cache dados de páginas Web localmente?**

* Quando os clientes de browser acedem ao Power BI, os servidores Web do Power BI definem a diretiva _Cache-Control_ para _no-store_. A diretiva _no-store_ instrui os browsers para não colocarem em cache a página Web que está a ser visualizada pelo utilizador e não para a armazenarem na pasta de cache do cliente.

**E a segurança baseada em papéis, relatórios de partilha ou dashboards e ligações de dados? Como é que isso funciona em termos de acesso a dados, visualização de dashboards, acesso a relatório ou atualização?**

* Para origens de dados não compatíveis com a **Segurança ao Nível da Função (RLS)** , se um dashboard, relatório ou modelo de dados for partilhado com outros utilizadores através do Power BI, os dados são disponibilizados aos utilizadores com os quais são partilhados para visualização e interação. O Power BI *não* autentica novamente os utilizadores relativamente à origem de dados original. Assim que os dados forem carregados para o Power BI, o utilizador autenticado relativamente à origem de dados é responsável por gerir que outros utilizadores e grupos podem ver os dados.

  Quando as ligações de dados são efetuadas para uma origem de dados adequada para **RLS**, como uma origem de dados do Analysis Services, apenas os dados de dashboards são colocados em cache no Power BI. Sempre que um relatório ou conjunto de dados é visualizado ou acedido no Power BI e utiliza dados da origem de dados adequada para RLS, o serviço Power BI acede à origem de dados para obter dados com base nas credenciais do utilizador e, se existirem permissões suficientes, os dados são carregados para o relatório ou modelo de dados para esse utilizador. Se a autenticação falhar, será apresentado um erro ao utilizador.

  Para obter mais informações, veja a secção **Autenticação de Utilizadores para Origens de Dados** mais acima neste documento.

**Os nossos utilizadores ligam-se sempre às mesmas fontes de dados, algumas das quais requerem credenciais que diferem das suas credenciais de domínio. Como podem evitar ter de inserir estas credenciais cada vez que fazem uma ligação de dados?**

* O Power BI disponibiliza o [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846), uma funcionalidade que permite aos utilizadores criar credenciais para múltiplas origens de dados diferentes e, em seguida, utilizar automaticamente essas credenciais ao aceder posteriormente a cada uma dessas dados origens. Para obter mais informações, veja [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846).

**Como funcionam os Grupos do Power BI?**

* Os Grupos do Power BI permitem aos utilizadores colaborar rápida e facilmente na criação de dashboards, relatórios e modelos de dados em equipas estabelecidas. Por exemplo, se tiver um Grupo do Power BI que inclui todas as pessoas na sua equipa próxima, pode facilmente colaborar com todos ao selecionar o Grupo no Power BI. Os Grupos do Power BI são equivalentes aos Grupos Universais do Office 365 (sobre os quais pode [saber mais](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1), podendo [criá-los](https://support.office.com/Article/View-create-and-delete-Groups-in-the-Office-365-admin-center-a6360120-2fc4-46af-b105-6a04dc5461c7) e [geri-los](https://support.office.com/Article/Manage-Group-membership-in-the-Office-365-admin-center-e186d224-a324-4afa-8300-0e4fc0c3000a)) e utilizam os mesmos mecanismos de autenticação utilizados no Azure Active Directory para proteger dados. Pode [criar grupos no Power BI](https://support.powerbi.com/knowledgebase/articles/654250) ou criar um Grupo Universal no centro de administração do Microsoft 365. Seja qual for a escolha, o resultado para a criação de Grupos no Power BI é o mesmo.

  Tenha em atenção que os dados partilhados com Grupos do Power BI seguem as mesmas considerações de segurança de todos os dados partilhados no Power BI. Para origens de dados **sem RLS**, o Power BI **não** autentica novamente os utilizadores relativamente à origem de dados original e, assim que os dados forem carregados para o Power BI, o utilizador autenticado relativamente à origem de dados é responsável por gerir que outros utilizadores e grupos podem ver os dados. Para obter mais informações, veja a secção **Autenticação de Utilizadores para Origens de Dados** mais acima neste documento.

  Obtenha mais informações sobre [Grupos no Power BI](https://support.powerbi.com/knowledgebase/articles/654247).

**Que portas são usadas por gateway de dados no local e gateway pessoal? Há algum nome de domínio que precise ser permitido para fins de conectividade?**

* A resposta detalhada a esta pergunta está disponível no seguinte link: [Gateway ports](/data-integration/gateway/service-gateway-communication#ports)

**Ao trabalhar com o portal de dados no local, como são utilizadas as chaves de recuperação e onde são armazenadas? E a gestão segura da credencial?**

* Durante a instalação e a configuração do gateway, o administrador introduz uma **Chave de Recuperação** do mesmo. Esta **Chave de Recuperação** é usada para gerar uma chave simétrica **AES** forte. Uma chave assimétrica **RSA** também é criada ao mesmo tempo.

    Essas chaves geradas (**RSA** e **AES**) são armazenadas num ficheiro no computador local. Esse ficheiro também é encriptado. O conteúdo do ficheiro só pode ser desencriptado por esse computador Windows específico e apenas por essa conta do serviço de gateway específica.

    Quando um utilizador introduz credenciais da origem de dados na IU do serviço Power BI, as mesmas são encriptadas com a chave pública no browser. O gateway desencripta as credenciais utilizando a chave privada RSA e encripta-as novamente com uma chave simétrica AES antes de os dados serem armazenados no serviço Power BI. Com esse processo, o serviço Power BI nunca tem acesso aos dados não encriptados.

**Que protocolos de comunicação são utilizados pelo gateway de dados no local e como são protegidos?**

* O gateway suporta os dois seguintes protocolos de comunicações:

  - **AMQP 1.0 – TCP + TLS**: Este protocolo exige que as portas 443, 5671-5672 e 9350-9354 estejam abertas para comunicação de saída. Esse protocolo é preferível, uma vez que tem uma menor sobrecarga de comunicações.

  - **HTTPS – WebSockets over HTTPS + TLS**: Este protocolo utiliza apenas a porta 443. O WebSocket é iniciado por uma única mensagem HTTP CONNECT. Assim que o canal é estabelecido, a comunicação é essencialmente TCP + TLS. Pode forçar a porta de entrada a utilizar este protocolo modificando uma definição descrita no artigo de [gateway no local.](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus)

**Qual é a função da CDN do Azure no Power BI?**

* Conforme mencionado anteriormente, o Power BI utiliza a **Rede de Entrega de Conteúdos (CDN) do Azure** para distribuir de modo eficiente o conteúdo e os ficheiros estáticos necessários para os utilizadores com base na região geográfica. Mais especificamente, o serviço Power BI utiliza múltiplas **CDNs** para distribuir de forma eficiente o conteúdo e os ficheiros estáticos necessários aos utilizadores através da Internet pública. Estes ficheiros estáticos incluem transferências de produtos (como o **Power BI Desktop**, o **gateway de dados no local** ou aplicações Power BI a partir de vários fornecedores de serviço independentes), ficheiros de configuração do browser utilizados para iniciar e estabelecer quaisquer ligações posteriores ao serviço Power BI, bem como a página de início de sessão seguro inicial do Power BI.

  Com base nas informações fornecidas durante uma ligação inicial ao serviço Power BI, o browser do utilizador contacta a **CDN** do Azure especificada (ou, para alguns ficheiros, o **WFE**) para transferir a coleção de ficheiros comuns especificados necessários para permitir a interação do browser com o serviço Power BI. A página do browser passa a incluir o token do AAD, informações de sessão, a localização do cluster de **Back-end** associado e a coleção de ficheiros transferidos da **CDN** do Azure e do cluster **WFE**, enquanto durar a sessão do browser com o serviço Power BI.

**Para os visuais do Power BI, a Microsoft realiza alguma avaliação de segurança ou privacidade do código visual personalizado antes de publicar artigos na Galeria?**

* N.º É da responsabilidade do cliente analisar e determinar se o código do elemento visual personalizado é confiável. Todos os códigos de elementos visuais personalizados são processados num ambiente sandbox, de forma que qualquer código anómalo num elemento visual personalizado não afete negativamente o resto do serviço Power BI.

**Existem outros elementos visuais do Power BI que enviam informações para fora da rede do cliente?**

* Sim. Os elementos visuais do Mapas Bing e da ESRI transmitem dados para fora do serviço Power BI, caso utilizem esses serviços.

**Para aplicações de modelo, a Microsoft realiza alguma avaliação de segurança ou privacidade da aplicação Modelo antes de publicar itens na Galeria?**
* N.º A editora de aplicações é responsável pelo conteúdo, enquanto o cliente é responsável por rever e determinar se confia na editora de aplicações Do Modelo. 

**Existem aplicações de modelo que podem enviar informações fora da rede de clientes?**
* Sim. É da responsabilidade do cliente rever a política de privacidade da editora e determinar se deve instalar a aplicação Modelo no Tenant. Além disso, a editora é responsável por notificar o comportamento e as capacidades da aplicação.

**E a soberania dos dados? Podemos fornecer inquilinos em centros de dados localizados em geografias específicas, para garantir que os dados não saem das fronteiras do país?**

* Alguns clientes em determinadas localizações geográficas têm a opção de criar um inquilino numa cloud nacional, onde o armazenamento e o processamento de dados é mantido separado de todos os outros datacenters. As clouds nacionais têm um tipo de segurança ligeiramente diferente, uma vez que um administrador de dados em separado opera o serviço Power BI da cloud nacional em nome da Microsoft.

  Em alternativa, os clientes podem também configurar um inquilino numa região específica, embora esses inquilinos não tenham um administrador de dados em separado da Microsoft. Os preços das clouds nacionais são diferentes dos preços do serviço Power BI comercial disponível para o público. Para obter mais informações sobre a disponibilidade do serviço Power BI para clouds nacionais, veja as [clouds nacionais do Power BI](https://powerbi.microsoft.com/clouds/).

**Como é que a Microsoft trata as ligações para clientes que têm subscrições power BI Premium? Estas ligações são diferentes das estabelecidas para o serviço não Premium Power BI?**

* As ligações estabelecidas para clientes com subscrições do Power BI Premium implementam um processo de autorização [Empresa-Empresa (B2B) do Azure](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) através do Azure Active Directory (AD), para ativar o controlo e a autorização de acessos. O Power BI processa ligações de subscritores do Power BI Premium para recursos do Power BI Premium tal como faria com qualquer utilizador do Azure AD.

## <a name="conclusion"></a>Conclusão

A arquitetura do serviço Power BI baseia-se em dois clusters: o cluster de Front-end da Web (WFE) e o cluster de Back-end. O cluster WFE é responsável pela ligação e autenticação inicial do serviço Power BI e, uma vez autenticado, o Back-end processa todas as interações de utilizador subsequentes. O Power BI utiliza o Azure Active Directory (AAD) para armazenar e gerir identidades de utilizador e gere o armazenamento de dados e metadados através do Blob do Azure e da Base de Dados SQL do Azure, respetivamente.

O armazenamento e o processamento de dados no Power BI são diferentes consoante o acesso aos dados seja efetuado através de uma DirectQuery, além de estarem dependentes de as origens de dados se encontrarem na cloud ou no local. O Power BI também tem a capacidade de impor a Segurança ao Nível da Função (RLS) e interagir com Gateways que fornecem acesso a dados no local.

## <a name="feedback-and-suggestions"></a>Feedback e Sugestões

Valorizamos o seu feedback. Estamos interessados em receber as sugestões que possa ter relativamente a melhorias, adições ou esclarecimentos sobre este documento técnico, ou outros conteúdos relacionados com o Power BI. Envie as suas sugestões para [pbidocfeedback@microsoft.com](mailto:pbidocfeedback@microsoft.com).

## <a name="additional-resources"></a>Recursos Adicionais

Para obter mais informações sobre o Power BI, veja os recursos seguintes.

- [Grupos no Power BI](https://support.powerbi.com/knowledgebase/articles/654247)
- [Introdução ao Power BI Desktop](https://support.powerbi.com/knowledgebase/articles/471664)
- [API REST do Power BI – Descrição Geral](https://msdn.microsoft.com/library/dn877544.aspx)
- [Referência da API do Power BI](https://msdn.microsoft.com/library/mt147898.aspx)
- [Gateway de dados no local](service-gateway-onprem.md)
- [Clouds Nacionais do Power BI](https://powerbi.microsoft.com/clouds/)
- [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
- [Utilizar o Kerberos para SSO a partir do Power BI para origens de dados no local](service-gateway-sso-overview.md)
