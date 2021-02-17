---
title: Papel branco de segurança do Power BI
description: Um livro branco que discute e descreve arquitetura de segurança e implementação para Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/11/2021
LocalizationGroup: Conceptual
ms.openlocfilehash: 0c6fb504cd985103d811b820cc85212aaa72bc76
ms.sourcegitcommit: 9a00abaca80d0cdb2bd0cd9270f99db62df8a2ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2021
ms.locfileid: "100569610"
---
# <a name="power-bi-security-white-paper"></a>Papel branco de segurança do Power BI

**Resumo:** Power BI é um serviço de software online *(SaaS*, ou Software como um serviço) que lhe permite criar facilmente e rapidamente os dashboards de Business Intelligence, relatórios, conjuntos de dados e visualizações. Com o Power BI, pode ligar a várias origens de dados diferentes, combinar e formatar os dados dessas ligações, e criar relatórios e dashboards que podem ser partilhados com outras pessoas.

**Escritores:** Yitzhak Kesselman, Paddy Osborne, Matt Neely, Tony Bencic, Srinivasan Turuvekere, Cristian Petculescu, Adi Regev, Naveen Sivaraj, Ben Glastein, Evgeny Tshiorny, Arthi Ramasubramanian Iyer, Sid Jayadevan, Ronald Chang, Ori Eduar, Anton Fritz, Idan Sheinberg, Ron Gilad, Sagiv Hadaya, Paul Inbar, Igor Uzhviev, Michael Roth, Jamie Tarquino, Gennady Pats, Orion Lee, Yury Berezansky, Maya Shenhav, Romit Chattopadhyay, Yariv Maimon, Bogdan Crivat

**Revisores Técnicos:** Cristian Petculescu, Amir Netz, Sergei Gundorov

**Aplica-se a:** Power BI SaaS, Power BI Desktop, Power BI Premium, Power BI Embedded Analytics, Power BI Mobile

> [!NOTE]
> Pode guardar ou imprimir este papel branco selecionando **Imprimir** no seu navegador e, em seguida, selecionar **Guardar como PDF**.

## <a name="introduction"></a>Introdução

O Power BI é uma oferta de serviço de software online (*SaaS* ou Software como Serviço) da Microsoft que permite criar rápida e facilmente dashboards, relatórios, conjuntos de dados e visualizações de Business Intelligence de gestão personalizada. Com o Power BI, pode ligar a várias origens de dados diferentes, combinar e formatar os dados dessas ligações, e criar relatórios e dashboards que podem ser partilhados com outras pessoas.

O mundo está a mudar rapidamente; as organizações estão a passar por uma transformação digital acelerada, e estamos a assistir a um aumento maciço do trabalho remoto, ao aumento da procura de serviços online por parte dos clientes e ao aumento do uso de tecnologias avançadas nas operações e na tomada de decisões empresariais. E tudo isto é alimentado pela nuvem.

À medida que a transição para a nuvem mudou de uma gota para uma inundação, e com a nova área  de superfície exposta que vem com ela, cada vez mais empresas perguntam quão seguros são *os meus dados na nuvem?* E para as plataformas bi que muitas vezes lidam com algumas das informações mais estratégicas da empresa, estas questões são duplamente importantes.

As fundações antigas do modelo de segurança do BI - segurança ao nível dos objetos e ao nível da linha - embora ainda importantes, claramente já não são suficientes para fornecer o tipo de segurança necessária na era da nuvem. Em vez disso, as organizações devem procurar uma solução de segurança nativa, multi-tiered e de defesa para os seus dados de inteligência empresarial.

O Power BI foi construído para fornecer proteção completa e hermética líder do setor para os dados. O produto obteve as mais altas classificações de segurança disponíveis no setor, e hoje muitas agências de segurança nacionais, instituições financeiras e prestadores de cuidados de saúde confiam-lhe as suas informações mais sensíveis.

Tudo começa com a fundação. Após um período difícil no início dos anos 2000, a Microsoft fez investimentos maciços para resolver as suas vulnerabilidades de segurança, e nas décadas seguintes construiu uma pilha de segurança muito forte que vai tão fundo como o kernel de bios on-chip da máquina e estende-se até às experiências do utilizador final. Estes investimentos profundos continuam, e hoje mais de 3.500 engenheiros da Microsoft estão empenhados em construir e melhorar a pilha de segurança da Microsoft e abordar proativamente o cenário de ameaças em mudança. Com biliões de computadores, triliões de logins e inúmeros zettabytes de informação confiados à proteção da Microsoft, a empresa possui agora a pilha de segurança mais avançada da indústria tecnológica e é amplamente vista como a líder global na luta contra atores maliciosos.

Power BI baseia-se nesta base muito forte. Usa a mesma pilha de segurança que ganhou ao Azure o direito de servir e proteger os dados mais sensíveis do mundo, e integra-se com as ferramentas de proteção e conformidade de informação mais avançadas da Microsoft 365. Além destes, oferece segurança através de medidas de segurança em várias camadas, resultando numa proteção de ponta a ponta projetada para lidar com os desafios únicos da era da nuvem.

Para fornecer uma solução de ponta a ponta para proteger ativos sensíveis, a equipa de produtos precisava de responder a preocupações desafiantes dos clientes em múltiplas frentes simultâneas:
* *Como controlamos quem se pode ligar, de onde se ligam e como se ligam?* *Como podemos controlar as ligações?*
* *Como são armazenados os dados?* *Como é encriptado?* *Que controlos tenho nos meus dados?*
* *Como controlo e protejo os meus dados sensíveis?* *Como posso garantir que estes dados não podem vazar para fora da organização?*
* *Como faço a auditoria a quem conduz que operações?* *Como reajo rapidamente se há atividade suspeita no serviço?*

Este artigo fornece uma resposta abrangente a todas estas questões. Começa com uma visão geral da arquitetura de serviço e explica como os principais fluxos do sistema funcionam. Em seguida, passa a descrever como os utilizadores autenticam o Power BI, como as ligações de dados são estabelecidas e como o Power BI armazena e movimenta dados através do serviço. A última secção discute as funcionalidades de segurança que lhe permitem, como administrador de serviço, proteger os seus bens mais valiosos.

O serviço Power BI é regido pelos [Termos do Microsoft Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31) e a [Declaração de Privacidade do Microsoft Enterprise](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx). Para a localização do tratamento de dados, consulte a localização dos termos de processamento de dados nos [Termos dos Serviços Online](http://www.microsoftvolumelicensing.com/Downloader.aspx?DocumentId=9555) da Microsoft e a [Adenda de Proteção de Dados](https://www.microsoft.com/download/details.aspx?id=101581). No que toca a informações de conformidade, o [Microsoft Trust Center](https://www.microsoft.com/trustcenter) é o principal recurso para o Power BI. A equipa do Power BI está empenhada em proporcionar aos seus clientes produtividade e as mais recentes inovações. Saiba mais sobre o cumprimento das ofertas de conformidade da [Microsoft.](/compliance/regulatory/offering-home)

O serviço Power BI segue o Ciclo de Vida para o Desenvolvimento de Segurança (SDL), práticas de segurança rigorosas que suportam requisitos de segurança e conformidade. O SDL ajuda os desenvolvedores a construir software mais seguro, reduzindo o número e a gravidade das vulnerabilidades no software, reduzindo ao mesmo tempo o custo de desenvolvimento. Saiba mais na [Microsoft Security Development Lifecycle Practices](https://www.microsoft.com/securityengineering/sdl/practices).

## <a name="power-bi-architecture"></a>Arquitetura power BI

O serviço Power BI é construído no Azure, [a plataforma de computação em nuvem](https://azure.microsoft.com/overview/what-is-azure/)da Microsoft. O Power BI está a ser implementado em vários datacenters em todo o mundo. Existem diversas implementações ativas disponibilizadas para clientes nas regiões servidas por esses datacenters e um número equivalente de implementações passivas que funcionam como cópias de segurança para cada implementação ativa.

![O WFE e o Back-end](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

### <a name="web-front-end-cluster-wfe"></a>Cluster frontal web (WFE)

O cluster WFE fornece ao navegador do utilizador o conteúdo inicial da página HTML na carga do site e gere o processo inicial de ligação e autenticação para o Power BI, utilizando o Azure Ative Directory (Azure AD) para autenticar clientes e fornecer fichas para as ligações subsequentes do cliente ao serviço back-end Power BI.

![O Cluster WFE](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

Um cluster WFE é composto por um website ASP.NET em execução no [Azure App Service Environment](/azure/app-service/environment/intro). Quando os utilizadores tentam ligar-se ao serviço Power BI, o serviço DNS do cliente pode comunicar com o Gestor de Tráfego Azure para encontrar o centro de dados mais adequado (geralmente mais próximo) com uma implementação de Power BI. Para obter mais informações sobre este processo, consulte [o método de encaminhamento de tráfego de desempenho para O Gestor de Tráfego Azure](/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method).

O cluster WFE atribuído ao utilizador gere a sequência de login e autenticação (descrito mais tarde neste artigo) e obtém um token de acesso AD AZure assim que a autenticação for bem sucedida. O componente ASP.NET dentro do cluster WFE analisa o token para determinar a organização a que o utilizador pertence e, em seguida, consulta o Power BI Global Service. O WFE especifica para o navegador que o cluster back-end abriga o inquilino da organização. Uma vez que um utilizador é autenticado, as interações subsequentes do cliente para os dados do cliente ocorrem diretamente com o cluster back-end ou Premium, sem que o WFE seja um intermediador para esses pedidos.

Recursos estáticos como **.js*, **.css*, e ficheiros de imagem são armazenados maioritariamente na Rede de Entrega de Conteúdos Azure (CDN) e recuperados diretamente pelo navegador. Note que as implantações de clusters do Governo Soberano são uma exceção a esta regra, e por razões de conformidade omitirá o CDN e, em vez disso, utilizará um cluster WFE de uma região conforme para hospedar conteúdo estático.

### <a name="power-bi-back-end-cluster-be"></a>Power BI cluster back-end (BE)

O cluster back-end é a espinha dorsal de toda a funcionalidade disponível no Power BI. É composto por vários pontos finais de serviço consumidos por clientes Web Front End e API, bem como serviços de trabalho de fundo, bases de dados, caches e vários outros componentes.

A parte traseira está disponível na maioria das regiões de Azure, e está a ser implantada em novas regiões à medida que se tornam disponíveis. Uma única região de Azure acolhe um ou mais aglomerados de back-end que permitem uma escala horizontal ilimitada do serviço Power BI uma vez esgotados os limites de escala vertical e horizontal de um único cluster.

Cada aglomerado de back-end é imponente e acolhe todos os dados de todos os inquilinos designados para aquele cluster. Um cluster que contém os dados de um inquilino específico é referido como o aglomerado de casas do inquilino. A informação do cluster doméstico de um utilizador autenticado é fornecida pela Global Service e utilizada pela Web Front End para encaminhar os pedidos para o cluster do arrendatário.

Cada cluster back-end é composto por múltiplas máquinas virtuais combinadas em vários conjuntos de escala redimensionável sintonizados para executar tarefas específicas, recursos imponentes, tais como bases de dados SQL, contas de armazenamento, autocarros de serviço, caches e outros componentes de nuvem necessários.

Os metadados e dados dos inquilinos são armazenados dentro dos limites do cluster, com exceção da replicação de dados a um cluster secundário de back-end numa região de Azure emparelhada na mesma geografia azul. O cluster secundário de back-end serve como um aglomerado de failover em caso de paragem regional, e é passivo em qualquer outro momento.

A funcionalidade back-end é servida por micro-serviços em execução em diferentes máquinas dentro da rede virtual do cluster que não são acessíveis a partir do exterior, exceto para dois componentes que podem ser acedidos a partir da internet pública:
* Serviço Gateway
* API Management do Azure

![O aglomerado de back-end](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

### <a name="power-bi-premium-infrastructure"></a>Infraestrutura Power BI Premium

O Power BI Premium oferece um serviço para assinantes que necessitam de funcionalidades premium do Power BI, tais como Dataflows, Relatórios Paginated, IA, etc. Quando um cliente se inscreve para uma subscrição Power BI Premium, a capacidade Premium é criada através do Azure Resource Manager.

As capacidades Power BI Premium são hospedadas em clusters back-end que são independentes da extremidade traseira power bi regular – ver acima). Isto proporciona um melhor isolamento, alocação de recursos, apoio, isolamento de segurança e escalabilidade da oferta Premium.

O seguinte diagrama ilustra a arquitetura da infraestrutura Power BI Premium:

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

A ligação à infraestrutura Power BI Premium pode ser feita de várias formas, dependendo do cenário do utilizador. Os clientes Power BI Premium podem ser o navegador de um utilizador, uma extremidade traseira regular do Power BI, ligações diretas através de clientes XMLA, APIs ARM, etc.

A infraestrutura Power BI Premium numa região de Azure é composta por múltiplos clusters Power BI Premium (o mínimo é um). A maioria dos recursos Premium são encapsulados dentro de um cluster (por exemplo, cálculo), e existem alguns recursos regionais comuns (por exemplo, armazenamento de metadados). A infraestrutura premium permite duas formas de alcançar a escalabilidade horizontal numa região: aumentar os recursos dentro dos clusters e/ou adicionar mais clusters à procura, se necessário (se os recursos de cluster estiverem a aproximar-se dos seus limites).

A espinha dorsal de cada cluster são recursos computetados geridos por [Conjuntos de Escala de Máquina Virtual (VMSS)](/azure/virtual-machine-scale-sets/overview) e [Tecido de Serviço Azure](/azure/service-fabric/service-fabric-overview). A VMSS e o Service Fabric permitem um aumento rápido e indolor dos nós computacional à medida que o uso cresce e orquestra a implementação, gestão e monitorização dos serviços e aplicações Power BI Premium.

Existem muitos recursos circundantes que garantem uma infraestrutura segura e fiável: equilibradores de carga, redes virtuais, grupos de segurança de rede, autocarro de serviço, armazenamento, etc. Quaisquer segredos, chaves e certificados necessários para o Power BI Premium são geridos exclusivamente pela [Azure Key Vault.](/azure/key-vault/general/basic-concepts) Qualquer autenticação é feita através da integração com a Azure AD exclusivamente.

Qualquer pedido que venha à infraestrutura Power BI Premium vai primeiro para os nós frontais – são os únicos nós disponíveis para ligações externas. O resto dos recursos estão escondidos atrás de redes virtuais. Os nosdes front-end autenticam o pedido, manuseiam-no ou encaminham-no para os recursos apropriados (por exemplo, nos nosdes de back-end).

Os nós de back-end fornecem a maioria das capacidades e funcionalidades power BI Premium.

### <a name="power-bi-mobile"></a>Power BI Mobile

Power BI Mobile é uma coleção de aplicações desenhadas para as três plataformas móveis primárias: Android, iOS e Windows (UWP). Considerações de segurança para as aplicações Power BI Mobile enquadram-se em duas categorias:
* Comunicação do dispositivo
* A aplicação e os dados no dispositivo

Para a comunicação do dispositivo, todas as aplicações Power BI Mobile comunicam com o serviço Power BI e utilizam as mesmas sequências de ligação e autenticação utilizadas pelos navegadores, que são descritas em detalhe no início deste livro branco. As aplicações móveis Power BI para iOS e Android trazem uma sessão de navegador dentro da própria aplicação, enquanto a aplicação móvel do Windows traz um corretor para estabelecer o canal de comunicação com o Power BI (para o processo de inscrição).

A tabela a seguir mostra suporte de autenticação baseada em certificados (CBA) para Power BI Mobile, com base na plataforma de dispositivos móveis:


|Apoio da ACB  |iOS  |Android  |Windows  |
|---------|---------|---------|---------|
|Power BI (iniciar sessão no serviço)    |Suportado         |Suportado         |Não suportado         |
|SSRS ADFS on-prem (ligar ao servidor SSRS)     |Não suportado         |Suportado         |Não suportado         |
|Procuração de aplicativo SSRS     |Suportado         |Suportado         |Não suportado         |

As aplicações do Power BI Mobile comunicam ativamente com o serviço Power BI. A telemetria é usada para recolher estatísticas de utilização de aplicações móveis e dados semelhantes, que são transmitidos a serviços que são utilizados para monitorizar o uso e a atividade; nenhum dado do cliente é enviado com telemetria.

A aplicação Power BI armazena dados no dispositivo que facilita a utilização da app:
* O Azure AD e os tokens de atualização são armazenados num mecanismo seguro no dispositivo, utilizando medidas de segurança padrão da indústria.
* Os dados e as definições (pares de valor-chave para a configuração do utilizador) estão em cache no armazenamento do dispositivo e podem ser encriptados pelo SISTEMA. No iOS isto é feito automaticamente quando o utilizador define uma senha. No Android isto pode ser configurado nas definições. No Windows é realizado utilizando o BitLocker.
* Para as aplicações Android e iOS, os dados e configurações (pares de valor-chave para a configuração do utilizador) estão em cache no armazenamento do dispositivo numa caixa de areia e armazenamento interno que é acessível apenas à aplicação. Para a aplicação Do Windows, os dados só são acessíveis pelo utilizador (e administração do sistema).
* A geolocalização é ativada ou desativada explicitamente pelo utilizador. Se ativado, os dados de geolocalização não são guardados no dispositivo e não são partilhados com a Microsoft.
* As notificações são ativadas ou desativadas explicitamente pelo utilizador. Se estiver ativado, o Android e o iOS não suportam requisitos de residência de dados geográficos para notificações.

A encriptação de dados pode ser melhorada aplicando encriptação de nível de ficheiro através do Microsoft Intune, um serviço de software que fornece a gestão de dispositivos móveis e aplicações. Todas as três plataformas para as quais o Power BI Mobile está disponível suportam o Intune. Com o Intune ativado e configurado, os dados no dispositivo móvel são encriptados e a própria aplicação Power BI não pode ser instalada num cartão SD. [Saiba mais sobre o Microsoft Intune.](https://www.microsoft.com/cloud-platform/microsoft-intune)

A aplicação Windows também suporta a [Proteção de Informação do Windows (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).

Para implementar o SSO, alguns valores de armazenamento seguros relacionados com a autenticação baseada em token estão disponíveis para outras aplicações do 1º partido da Microsoft (como o Microsoft Authenticator) e são geridos pela Azure Ative Directory Authentication Library (ADAL) SDK.  

Os dados em cache do Power BI Mobile são eliminados quando a aplicação é removida, quando o utilizador assina fora do Power BI Mobile, ou quando o utilizador não consegue iniciar sação (como por exemplo, após um evento de expiração simbólico ou alteração de senha). A cache de dados inclui dashboards e relatórios acedidos anteriormente através da aplicação do Power BI Mobile.

O Power BI Mobile não acede a outras pastas de aplicação ou ficheiros no dispositivo.

As aplicações Power BI para iOS e Android permitem proteger os seus dados configurando uma identificação adicional, como fornecer Face ID, Touch ID ou uma senha para iOS, e dados biométricos (ID de impressão digital) para Android. [Saiba mais sobre a identificação adicional.](../consumer/mobile/mobile-native-secure-access.md)

## <a name="authentication-to-the-power-bi-service"></a>Autenticação no serviço Power BI

A autenticação de utilizadores no serviço Power BI consiste numa série de pedidos, respostas e redirecionamentos entre o browser do utilizador e o serviço Power BI ou os serviços do Azure utilizados pelo Power BI. Esta sequência descreve o processo de autenticação do utilizador no Power BI, que segue o [fluxo de concessão de código auth do Azure Ative Directory](/azure/active-directory/develop/v2-oauth2-auth-code-flow). Para obter mais informações sobre as opções para os modelos de autenticação de utilizadores de uma organização (modelos de inscrição), consulte [escolher um modelo de inscrição para o Microsoft 365](https://blogs.office.com/2014/05/13/choosing-a-sign-in-model-for-office-365/).

### <a name="authentication-sequence"></a>Sequência de autenticação

A sequência de autenticação do utilizador para o serviço Power BI ocorre conforme descrito nos seguintes passos, que são ilustrados na imagem que os segue.

1. Um utilizador inicia uma ligação ao serviço Power BI a partir de um browser, quer digitando o endereço Power BI na barra de endereços, quer selecionando *Iniciar sing in na* página de aterragem power BI https://powerbi.microsoft.com) (. A ligação é estabelecida através de TLS 1.2 e HTTPS, e todas as comunicações subsequentes entre o browser e o serviço Power BI utilizam HTTPS.

1. O Gestor de Tráfego Azure verifica o registo DNS do utilizador para determinar o centro de dados mais adequado (geralmente mais próximo) onde o Power BI é implantado, e responde ao DNS com o endereço IP do cluster WFE para o qual o utilizador deve ser enviado.

1. Em seguida, a WFE redireciona o utilizador para a página de login dos Serviços Online da Microsoft.

1. Depois de o utilizador ter sido autenticado, a página de login redireciona o utilizador para o cluster WFE do serviço de poder de poder mais próximo previamente determinado com um código de auth.

1. O cluster WFE verifica com o serviço Azure AD para obter um sinal de segurança Azure AD utilizando o código auth. Quando a Azure AD devolve a autenticação bem sucedida do utilizador e devolve um sinal de segurança Azure AD, o cluster WFE consulta o Power BI Global Service, que mantém uma lista de inquilinos e seus locais de cluster back-end Power BI e determina qual o cluster de serviço back-end Power BI que contém o inquilino do utilizador. Em seguida, o cluster WFE devolve uma página de aplicação ao navegador do utilizador com a sessão, acesso e informação de encaminhamento necessárias para o seu funcionamento.

1. Agora, quando o navegador do cliente requer dados do cliente, irá enviar pedidos para o endereço de cluster back-end com o token de acesso AZure no cabeçalho de Autorização. O cluster back-end Power BI lê o token de acesso Azure AD e valida a assinatura para garantir que a identidade do pedido é válida. O [token de acesso Azure AD tem um prazo de vida predefinido de 1 hora](/azure/active-directory/develop/active-directory-configurable-token-lifetimes#configurable-token-lifetime-properties-after-the-retirement), e para manter a sessão atual o navegador do utilizador irá fazer pedidos periódicos para renovar o token de acesso antes de expirar.

![Sequência de autenticação](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

## <a name="data-residency"></a>Residência dos dados

Salvo indicação em contrário na documentação, o Power BI armazena os dados dos clientes numa geografia Azure que é atribuída quando um [inquilino da AZure AD](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings) se inscreve nos serviços de Power BI pela primeira vez. Um inquilino da AZure AD abriga as identidades, grupos e outras informações relevantes que dizem respeito a uma organização e à sua segurança. 

A atribuição de uma geografia Azure para armazenamento de dados de inquilinos é feita mapeando o país ou região selecionado como parte da configuração do inquilino Azure AD para a geografia Azure mais adequada onde existe uma implantação de Power BI. Uma vez feita esta determinação, todos os dados do cliente do Power BI serão armazenados nesta geografia Azure selecionada (também conhecida como *geo doméstico),* exceto nos casos em que as organizações utilizam implementações multi-geo.

### <a name="multiple-geographies-multi-geo"></a>Múltiplas geografias (multi-geo)

Algumas organizações têm uma presença global e podem necessitar de serviços de Power BI em várias geografias Azure. Por exemplo, uma empresa pode ter a sua sede nos Estados Unidos, mas também pode fazer negócios noutras áreas geográficas, como a Austrália. Nestes casos, a empresa pode exigir que certos dados do Power BI permaneçam armazenados em repouso na região remota para cumprir as normas locais. Esta característica do serviço Power BI é referida como *multi-geo.*

A camada de execução de consultas, caches de consulta e dados de artefactos atribuídos a um espaço de trabalho multi-geo são hospedados e permanecem na capacidade remota Azure geografia. No entanto, alguns metadados de artefactos, como a estrutura do relatório, podem permanecer armazenados em repouso na casa do arrendatário geo. Além disso, alguns dados de trânsito e processamento podem ainda acontecer na casa do arrendatário geo, mesmo para espaços de trabalho que estão hospedados numa capacidade multi-geo Premium.

Consulte o [suporte Configure Multi-Geo para Power BI Premium](../admin/service-admin-premium-multi-geo.md) para obter mais informações sobre a criação e gestão de implementações do Power BI que abrangem várias geografias Azure.

### <a name="regions-and-datacenters"></a>Regiões e centros de dados

Os serviços de Power BI estão disponíveis em geografias específicas do Azure, conforme descrito no [Microsoft Trust Center.](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) Para obter mais informações sobre onde os seus dados são armazenados e como são utilizados, consulte o [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/Transparency/default.aspx#_You_know_where). Os compromissos relativos à localização dos dados dos clientes em repouso estão especificados nos Termos de Processamento de Dados dos [Termos dos Serviços Online da Microsoft.](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31)

A Microsoft também fornece datacenters para entidades soberanas. Para obter mais informações sobre a disponibilidade do serviço Power BI para clouds nacionais, veja as [clouds nacionais do Power BI](https://powerbi.microsoft.com/clouds/). 

## <a name="data-handling"></a>Processamento de dados

Esta secção descreve práticas de tratamento de dados power BI quando se trata de armazenar, processar e transferir dados do cliente.

### <a name="data-at-rest"></a>Dados inativos

Power BI utiliza dois tipos de recursos primários de armazenamento de dados:
* Storage do Azure
* Bases de Dados SQL do Azure

Na maioria dos cenários, o Azure Storage é utilizado para persistir os dados dos artefactos Power BI, enquanto as bases de dados Azure SQL são usadas para persistir metadados de artefactos. 

Todos os dados persistidos pelo Power BI são encriptados por padrão utilizando as teclas geridas pela Microsoft. Os dados do cliente armazenados nas Bases de Dados Azure SQL são totalmente encriptados utilizando a tecnologia [Transparente de Encriptação de Dados (TDE) da Azure SQL.](/azure/sql-database/transparent-data-encryption-azure-sql) Os dados do cliente armazenados no armazenamento Azure Blob são encriptados utilizando [a encriptação de armazenamento Azure](/azure/storage/common/storage-service-encryption).

Opcionalmente, as organizações podem utilizar o Power BI Premium para usar as suas próprias chaves para encriptar dados em repouso que são importados num conjunto de dados. Esta abordagem é normalmente descrita como Bring Your Own Key (BYOK). A utilização da BYOK ajuda a garantir que, mesmo em caso de erro do operador de serviço, os dados do cliente não serão expostos – algo que não pode ser facilmente alcançado através de encriptação transparente do lado do serviço. Consulte [as suas próprias chaves de encriptação para Power BI](../admin/service-encryption-byok.md) para obter mais informações.

Os conjuntos de dados do Power BI permitem uma variedade de modos de ligação de fonte de dados que determinam se os dados de origem de dados são ou não persistidos no serviço.

|Modo de conjunto de dados (tipo)   |Dados Persistiram no Power BI |
|----------------------|---------------------------|
|Importar                |Sim |
|Consulta Direta          |Não |
|Live Connect          |Não |
|Composto             |Se contiver uma fonte de dados de importação |
|Transmissão em Fluxo             |Se configurado para persistir |

Independentemente do modo de conjunto de dados utilizado, o Power BI pode cache temporariamente quaisquer dados recuperados para otimizar a consulta e reportar o desempenho da carga.

### <a name="data-in-processing"></a>Dados no tratamento

Os dados estão em processamento quando estão a ser utilizados ativamente por um ou mais utilizadores como parte de um cenário interativo, ou quando um processo de fundo, como a refresh, toca nestes dados. O Power BI carrega dados tratados ativamente no espaço de memória de uma ou mais cargas de trabalho de serviço. Para facilitar a funcionalidade requerida pela carga de trabalho, os dados tratados na memória não são encriptados.

### <a name="data-in-transit"></a>Dados em trânsito
O Power BI requer que todos os tráfegos HTTP de entrada sejam encriptados utilizando o TLS 1.2 ou superior. Quaisquer pedidos que tentem utilizar o serviço com TLS 1.1 ou inferior serão rejeitados.

## <a name="authentication-to-data-sources"></a>Autenticação em fontes de dados

Ao ligar-se a uma fonte de dados, um utilizador pode optar por importar uma cópia dos dados para o Power BI ou ligar-se diretamente à fonte de dados. 

No caso de importação, um utilizador estabelece uma ligação com base no login do utilizador e acede aos dados com a credencial. Após a publicação do conjunto de dados para o serviço Power BI, o Power BI utiliza sempre a credencial deste utilizador para importar dados. Uma vez importados os dados, a visualização dos dados em relatórios e dashboards não acede à fonte de dados subjacente. O Power BI suporta uma autenticação única para fontes de dados selecionadas. Se a ligação estiver configurada para utilizar um único sinal de acesso, as credenciais do titular do conjunto de dados são utilizadas para se ligar à fonte de dados.

Se uma fonte de dados estiver ligada diretamente utilizando credenciais pré-configuradas, as credenciais pré-configuradas são utilizadas para se ligar à fonte de dados quando qualquer utilizador vê os dados. Se uma fonte de dados estiver ligada diretamente utilizando um único sinal, as credenciais do utilizador atual são utilizadas para se ligar à fonte de dados quando um utilizador vê os dados. Quando utilizado com um único sinal, a Segurança de Nível de Linha (RLS) pode ser implementada na fonte de dados. Isto permite que os utilizadores vejam apenas dados a que têm privilégios de acesso. Quando a ligação é para fontes de dados na nuvem, a autenticação AZure AD é usada para um único sinal; para fontes de dados on-prem, Kerberos, Security Assertion Markup Language (SAML) e Azure AD são suportados.

Se a fonte de dados for Azure Analysis Services ou serviços de análise no local, e o RLS estiver configurado, o serviço Power BI aplicará essa segurança de nível de linha, e os utilizadores que não possuam credenciais suficientes para aceder aos dados subjacentes (o que pode ser uma consulta usada num dashboard, relatório ou outro artefacto de dados) não verão dados para os quais não têm privilégios suficientes.

## <a name="premium-features"></a>Características premium

### <a name="dataflows-architecture"></a>Arquitetura de fluxos de dados

Os fluxos de dados fornecem aos utilizadores a capacidade de configurar operações de processamento de dados de fundo que irão extrair dados de fontes de dados polimórficas, executar lógica de transformação contra os dados e, em seguida, aterrar num modelo-alvo para uso em várias tecnologias de apresentação de relatórios. Qualquer utilizador que tenha um membro, colaborador ou função de administrador num espaço de trabalho pode criar um fluxo de dados. Os utilizadores na função de espectador podem ver os dados tratados pelo fluxo de dados, mas podem não fazer alterações na sua composição. Uma vez que um fluxo de dados tenha sido autor, qualquer membro, colaborador ou administrador do espaço de trabalho pode agendar atualizações, bem como visualizar e editar o fluxo de dados tomando posse do mesmo.

Cada fonte de dados configurada está ligada a uma tecnologia do cliente para aceder a essa fonte de dados. A estrutura das credenciais necessárias ao acesso aos mesmos é formada de forma a corresponder aos detalhes de implementação exigidos da fonte de dados. A lógica de transformação é aplicada pelos serviços de Consulta de Energia enquanto os dados estão em fuga. Para fluxos de dados premium, os serviços de consulta de energia executam em nós de back-end. Os dados podem ser retirados diretamente das fontes de nuvem ou através de um gateway instalado nas instalações. Quando puxado diretamente de uma fonte de nuvem para o serviço ou para o gateway, o transporte utiliza metodologia de proteção específica para a tecnologia do cliente, se aplicável. Quando os dados são transferidos do portal para o serviço de nuvem, é encriptado. Consulte a secção [de Dados no Processamento](#data-in-processing) acima.

Quando as fontes de dados especificadas pelo cliente requerem credenciais de acesso, o proprietário/criador do fluxo de dados fornecerá-as durante a autoria. São armazenados utilizando um armazenamento credencial padrão em todo o produto. Consulte a secção [autenticação para fontes de dados](#authentication-to-data-sources) acima. Existem várias abordagens que os utilizadores podem configurar para otimizar a persistência e acesso de dados. Por predefinição, os dados são colocados numa conta de armazenamento de propriedade power BI e protegida. A encriptação de armazenamento está ativada nos recipientes de armazenamento Blob para proteger os dados enquanto este está em repouso. Consulte a secção [Dados em Repouso](#data-at-rest) abaixo. No entanto, os utilizadores podem configurar a sua própria conta de armazenamento associada à sua própria subscrição Azure. Ao fazê-lo, é concedido a um responsável de serviço power BI acesso a essa conta de armazenamento para que possa escrever os dados lá durante a atualização. Neste caso, o proprietário do recurso de armazenamento é responsável por configurar a encriptação na conta de armazenamento ADLS configurada. Os dados são sempre transmitidos ao armazenamento blob através da encriptação.

Uma vez que o desempenho ao aceder a contas de armazenamento pode ser subóptima para alguns dados, os utilizadores também têm a opção de usar um motor computacional power BI hospedado para aumentar o desempenho. Neste caso, os dados são armazenados de forma redundante numa base de dados SQL que está disponível para DirectQuery através do acesso pelo sistema power bi back-end. Os dados são sempre encriptados no sistema de ficheiros. Se o utilizador fornecer uma chave para encriptar os dados armazenados na base de dados SQL, essa chave será usada para criptografá-lo duplamente.

Ao consultar o DirectQuery, o protocolo de transporte encriptado HTTPS é utilizado para aceder à API. Toda a utilização secundária ou indireta do DirectQuery é controlada pelos mesmos controlos de acesso previamente descritos. Uma vez que os fluxos de dados estão sempre ligados a um espaço de trabalho, o acesso aos dados é sempre fechado pelo papel do utilizador nesse espaço de trabalho. Um utilizador deve pelo menos ter acesso lido para poder consultar os dados através de qualquer meio.

Quando o Power BI Desktop é utilizado para aceder a dados num fluxo de dados, deve primeiro autenticar o utilizador utilizando a AD Azure para determinar se o utilizador tem direitos suficientes para visualizar os dados. Em caso afirmativo, uma chave SaS é adquirida e utilizada para aceder ao armazenamento diretamente utilizando o protocolo de transporte encriptado HTTPS.

O tratamento de dados em todo o oleoduto emite eventos de auditoria do Office 365. Alguns destes eventos irão capturar operações de segurança e privacidade.

### <a name="paginated-reports"></a>Relatórios paginados

Os repositórios paginados são concebidos para serem impressos ou partilhados. Designam-se paginados porque são formatados para se ajustarem a uma página. Os relatórios paginados apresentam todos os dados numa tabela, mesmo que a tabela ocupe múltiplas páginas. Também são chamados imagem perfeita, uma vez que pode controlar o esquema de página do relatório com exatidão.

Os relatórios paginados suportam expressões ricas e poderosas escritas no Microsoft Visual Basic .NET. As expressões são amplamente utilizadas nos relatórios paginados do Report Builder do Power BI para obter, calcular, apresentar, agrupar, ordenar, filtrar, parametrizar e formatar dados.

As expressões são criadas pelo autor do relatório com acesso ao vasto leque de características do quadro .NET. O processamento e execução de relatórios paginados é realizado dentro de uma caixa de areia.

As definições de relatório paginado (.rdl) são armazenadas no Power BI e para publicar e/ou prestar um relatório paginado que um utilizador precisa de autenticar e autorizar da mesma forma que descrito na [Autenticação para a](#authentication-to-the-power-bi-service) secção Power BI Service acima.

O token AD AZure obtido durante a autenticação é utilizado para comunicar diretamente do navegador para o cluster Power BI Premium.

Para a Premium Gen1, existe uma única caixa de areia por cada uma das capacidades do arrendatário, e é partilhada pelos espaços de trabalho atribuídos à capacidade.

![Relatórios paginados da Gen 1](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen1.png)

Para a Premium Gen2 (em pré-visualização), é criada uma caixa de areia efémera individual e exclusiva para cada uma das renderizações de um relatório, proporcionando um maior nível de isolamento entre os utilizadores.

![Relatórios paginados Gen 2](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen2.png)

Um relatório paginado pode aceder a um vasto conjunto de fontes de dados como parte da prestação do relatório. A caixa de areia não comunica diretamente com nenhuma das fontes de dados, mas comunica com o processo de confiança para solicitar dados, e depois o processo de confiança anexa as credenciais necessárias à ligação. Desta forma, a caixa de areia nunca tem acesso a qualquer credencial ou segredo. 

Para suportar funcionalidades como mapas Bing ou chamadas para Funções Azure, a caixa de areia tem acesso à internet.

### <a name="power-bi-embedded-analytics"></a>Análise incorporada ao Power BI

Os Fornecedores independentes de Software (ISVs) e fornecedores de soluções têm dois modos principais de incorporação de artefactos Power BI nas suas aplicações e portais web: [incorporados para a sua organização](../developer/embedded/embed-sample-for-your-organization.md) e [incorporados para os seus clientes.](../developer/embedded/embed-sample-for-customers.md) O artefacto está incorporado num iframe na aplicação ou portal. Um iframe não é permitido ler ou escrever dados a partir da aplicação ou portal da web externa, e a comunicação com o iframe é feita utilizando o Power BI Client SDK usando mensagens POST.

Num [cenário incorporado no seu](../developer/embedded/embed-sample-for-your-organization.md) cenário de organização, os utilizadores do Azure AD acedem aos seus próprios conteúdos Power BI através de portais personalizados pelas suas empresas e ITs. Todas as políticas e capacidades do Power BI descritas neste artigo, como a Row Level Security (RLS) são automaticamente aplicadas a todos os utilizadores independentemente de acederem ao Power BI através do [portal Power BI](https://app.powerbi.com/) ou através de portais personalizados.

Num [cenário incorporado para os seus clientes, os](../developer/embedded/embed-sample-for-customers.md) ISVs são normalmente donos de inquilinos power bi e artefactos Power BI (dashboards, relatórios, conjuntos de dados, etc.). É da responsabilidade de um serviço de back-end ISV autenticar os seus utilizadores finais e decidir quais os artefactos e qual o nível de acesso adequado para esse utilizador final. As decisões de política do ISV são encriptadas num [token incorporado](/rest/api/power-bi/embedtoken) gerado pelo Power BI e transmitidas para o back-end ISV para posterior distribuição aos utilizadores finais de acordo com a lógica de negócio do ISV. Os utilizadores finais que usam um navegador ou outras aplicações de clientes não são capazes de desencriptar ou modificar fichas incorporadas. SDKs do lado do cliente, tais como [APIs do cliente Power BI](/javascript/api/overview/powerbi/) anexam automaticamente o token incorporado encriptado aos pedidos de Power BI como uma Autorização: Cabeçalho *EmbedToken.* Com base neste cabeçalho, o Power BI irá impor todas as políticas (como o acesso ou o RLS) precisamente como foi especificado pelo ISV durante a geração.

Para permitir a incorporação e automação, e gerar os tokens incorporados acima descritos, o Power BI expõe um rico conjunto de [APIs REST](/rest/api/power-bi/embedtoken). Estes APIs power BI REST suportam tanto os [métodos de](/azure/active-directory/develop/v2-permissions-and-consent) autenticação e autorização do diretor de [serviço](../admin/service-premium-service-principal.md) Azure Ad.

A análise incorporada do Power BI e as suas APIs de REST suportam todas as capacidades de isolamento da rede Power BI descritas neste artigo: por exemplo, [Tags de Serviço](#service-tags) e Links [Privados](#private-link-integration).

### <a name="ai-features"></a>Características de IA

O Power BI suporta atualmente duas grandes categorias de funcionalidades de IA no produto de hoje: visuais de IA e enriquecimentos de IA. As funcionalidades de IA de nível visual incluem capacidades como Key-Influencers, Decomposition-Tree, Smart-Narrative, Anomaly-Detection, R-visual, Python-visual, Clustering, Forecasting, Q&A, Quick-Insights etc. As capacidades de enriquecimento de IA incluem capacidades como AutoML, AzureML, CognitiveServices, R/Python transforma-se etc. 

A maioria das funcionalidades acima mencionadas são suportadas em espaços de trabalho partilhados e premium hoje em dia. No entanto, os AutoML e os CognitiveServices são suportados apenas em espaços de trabalho Premium, devido a restrições de IP. Hoje, com a integração AutoML no Power BI, um utilizador pode construir e treinar um modelo ML personalizado (por exemplo, Previsão, Classificação, Regressão, etc.) e aplicá-lo para obter previsões enquanto carrega dados num fluxo de dados definido num espaço de trabalho Premium. Além disso, os utilizadores de Power BI podem aplicar várias APIs de Serviços Cognitivos, tais como TextAnalytics e ImageTagging, para transformar dados antes de os carregar num dataflow/dataset definido num espaço de trabalho Premium. 

As funcionalidades de enriquecimento premium AI podem ser melhor vistas como uma coleção de funções/transformações apátridas de IA que podem ser usadas pelos utilizadores do Power BI nos seus oleodutos de integração de dados utilizados por um conjunto de dados Power BI ou fluxo de dados. Note que estas funções também podem ser acedidas a partir de ambientes de autoria de dataflow/dataset atuais no Power BI Service e Power BI Desktop. Estas funções/transformações de IA funcionam sempre num espaço de trabalho/capacidade Premium. Estas funções são surgidas no Power BI como uma fonte de dados que requer um token AD Azure para o utilizador Power BI que está a utilizar a função de IA. Estas fontes de dados de IA são especiais porque não surfacem nenhum dos seus próprios dados e apenas fornecem estas funções/transformações. Durante a execução, estas funcionalidades não fazem chamadas de saída para outros serviços para transmitir os dados do cliente. Analisemos individualmente os cenários Premium para compreender os padrões de comunicação e os detalhes relevantes relacionados com a segurança que lhes dizem respeito. 

Para a formação e aplicação de um modelo AutoML, o Power BI utiliza o Azure AutoML SDK e executa toda a formação na capacidade power bi do cliente. Durante as iterações de treino, o Power BI chama um serviço AzureML de experimentação para selecionar um modelo e hiper-parâmetros adequados para a iteração atual. Nesta chamada de saída, apenas são enviados metadados de experiência relevantes (por exemplo, precisão, algoritmo ml, parâmetros de algoritmo, etc.) da iteração anterior. A formação AutoML produz um modelo ONNX e dados de relatório de formação que são depois guardados no fluxo de dados. Mais tarde, os utilizadores do Power BI podem então aplicar o modelo ML treinado como uma transformação para operacionalizar o modelo ML numa base programada. Para as APIs textanalytics e ImageTagging, o Power BI não liga diretamente para o serviço CognitivoServices APIs, mas utiliza um SDK interno para executar as APIs na capacidade Power BI Premium. Hoje estes APIs são suportados tanto em fluxos de dados power BI como em conjuntos de dados. Ao mesmo tempo que possuem um conjunto de dados no Power BI Desktop, os utilizadores só podem aceder a esta funcionalidade se tiverem acesso a um espaço de trabalho Premium Power BI. Assim, os clientes são solicitados a fornecer as suas credenciais AZURE AD. 

## <a name="network-isolation"></a>Isolamento da rede

Esta secção descreve funcionalidades avançadas de segurança no Power BI. Algumas das características têm requisitos específicos de licenciamento. Veja as secções abaixo para mais detalhes.

### <a name="service-tags"></a>Etiquetas de serviço

Uma etiqueta de serviço representa um grupo de prefixos de endereço IP de um determinado serviço Azure. Ajuda a minimizar a complexidade de atualizações frequentes às regras de segurança da rede. Os clientes podem utilizar tags de serviço para definir controlos de acesso à rede em [Grupos de Segurança de Rede](/azure/virtual-network/security-overview#security-rules) ou [Azure Firewall.](/azure/firewall/service-tags) Os clientes podem utilizar tags de serviço em vez de endereços IP específicos ao criar regras de segurança. Ao especificar o nome da etiqueta de serviço (por exemplo, PowerBI) no campo de origem ou destino apropriado (para APIs) de uma regra, os clientes podem permitir ou negar o tráfego para o serviço correspondente. A Microsoft gere os prefixos de endereços englobados pela etiqueta de serviço e atualiza automaticamente a etiqueta de serviço à medida que os endereços mudam.

### <a name="private-link-integration"></a>Integração de Ligação Privada

A rede Azure fornece a funcionalidade Azure Private Link que permite ao Power BI fornecer acesso seguro através de pontos finais privados da Azure Networking. Com o Azure Private Link e os pontos finais privados, o tráfego de dados é enviado em privado usando a infraestrutura de rede de espinha dorsal da Microsoft, e assim os dados não atravessam a Internet.

O Private Link garante que os utilizadores de Power BI usam a espinha dorsal da rede privada microsoft quando vão para recursos no serviço Power BI.

A utilização de Ligação Privada com o Power BI proporciona os seguintes benefícios:
* A Private Link garante que o tráfego fluirá sobre a espinha dorsal do Azure para um ponto final privado para os recursos baseados na nuvem de Azure.
* O isolamento do tráfego de rede de infraestruturas não baseadas em Azure, como o acesso ao local, exigiria que os clientes tivessem o ExpressRoute ou uma Rede Privada Virtual (VPN) configurada.

Consulte [links privados para aceder ao Power BI](../admin/service-security-private-links.md) para obter informações adicionais.

### <a name="vnet-connectivity-preview---coming-soon"></a>Conectividade VNet (pré-visualização - em breve)

Embora a funcionalidade de integração private Link forneça ligações seguras de entrada ao Power BI, a funcionalidade de conectividade VNet permite uma conectividade de saída segura do Power BI para fontes de dados dentro de um VNet. 

Os gateways VNet (geridos pela Microsoft) eliminarão a sobrecarga de instalação e monitorização de gateways de dados no local para ligação a fontes de dados associadas a um VNet. No entanto, continuarão a seguir o processo familiar de gestão de fontes de segurança e de dados, como acontece com uma porta de dados no local.

Segue-se uma visão geral do que acontece quando interage com um relatório Power BI que está ligado a uma fonte de dados dentro de um VNet utilizando gateways VNet:

1. O serviço de nuvem Power BI (ou um dos outros serviços de nuvem suportado) inicia uma consulta e envia a consulta, detalhes de fonte de dados e credenciais para o serviço VNet da Plataforma De Energia (PP VNet).

1. Em seguida, o serviço PP VNet injeta de forma segura um contentor que executa um gateway VNet na sub-rede. Este recipiente pode agora ligar-se aos serviços de dados acessíveis a partir desta sub-rede.

1. O serviço PP VNet envia então a consulta, dados de origem de dados e credenciais para o gateway VNet. 

1. O gateway VNet obtém a consulta e conecta-se às fontes de dados com essas credenciais.

1. A consulta é então enviada para a fonte de dados para execução.

1. Após a execução, os resultados são enviados para o gateway VNet, e o serviço PP VNet empurra os dados do recipiente para o serviço de nuvem Power BI.

Esta funcionalidade estará disponível em breve em visualização pública.

### <a name="service-principals"></a>Principais de serviço

O Power BI suporta a utilização de princípios de serviço. Armazenar quaisquer credenciais principais de serviço usadas para encriptar ou aceder ao Power BI num Cofre-Chave, atribuir políticas de acesso adequadas ao cofre e rever regularmente permissões de acesso.

Consulte [o espaço de trabalho do Automatismo Premium e as tarefas do conjunto de dados com os principais serviços](../admin/service-premium-service-principal.md) para obter mais detalhes.

## <a name="data-loss-prevention-dlp"></a>Prevenção da perda de dados (DLP)

### <a name="microsoft-365-sensitivity-labels"></a>Etiquetas de sensibilidade Microsoft 365

O Power BI tem uma integração profunda com os rótulos de sensibilidade microsoft Information Protection (MIP), que permitem às organizações ter uma solução única e integrada para a gestão, auditoria e conformidade de políticas DLP em toda a suite do Office.

Quando as etiquetas de sensibilidade estiverem ativadas no Power BI:
* Os dados sensíveis, tanto no serviço Power BI (GA) como no Power BI Desktop (pré-visualização), podem ser classificados e rotulados utilizando as mesmas etiquetas familiares de sensibilidade à Proteção de Informação da Microsoft utilizadas no Office e no Azure Purview. 
* As políticas de governação podem ser aplicadas, mesmo quando o conteúdo do Power BI é exportado para ficheiros Excel, PowerPoint, PDF ou *.pbix,* para ajudar a garantir que os dados são protegidos mesmo quando sai do Power BI.
* Os ficheiros *.pbix* podem ser encriptados de acordo com as políticas de etiquetas MIP quando uma etiqueta MIP é aplicada no ficheiro *.pbix* no Desktop, garantindo que apenas os utilizadores autorizados podem editar este ficheiro.
* É fácil classificar e proteger ficheiros *.pbix* tal como é feito com ficheiros Excel, Word e PowerPoint. Com apenas dois cliques, um ficheiro pode ser marcado de acordo com o seu nível de sensibilidade, e, ainda mais, ser encriptado se contiver dados confidenciais ao negócio.
* Os livros de excel herdam automaticamente as etiquetas de sensibilidade quando se ligam ao Power BI (pré-visualização), tornando possível manter a classificação de ponta a ponta e aplicar proteção quando o conjunto de dados Power BI é analisado no Excel.
* As etiquetas de sensibilidade aplicadas nos relatórios e dashboards power BI serão visíveis nas aplicações móveis Power BI e Android.
* As etiquetas de sensibilidade persistirão quando um relatório Power BI estiver incorporado em Equipas, SharePoint ou num website seguro (pré-visualização). Isto ajuda as organizações a manter a classificação e a proteção aquando da exportação ao incorporar o conteúdo do Power BI.
* A herança de etiqueta sobre a criação de novos conteúdos no serviço Power BI garante que a etiqueta aplicada num conjunto de dados no serviço Power BI será aplicada em novos conteúdos criados em cima do conjunto de dados. 
* [As APIs de digitalização](/rest/api/power-bi/admin/workspaceinfo_getscanresult) de administração power BI podem extrair um rótulo de sensibilidade de um artefacto Power BI, permitindo que os administradores power BI e InfoSec monitorizem a rotulagem no serviço Power BI e produzam relatórios executivos. 
* O Power BI garante que apenas os utilizadores autorizados podem alterar ou remover etiquetas com definições de proteção no serviço Power BI. 
* Em breve
    * Power BI admin APIs para aplicar etiquetas MIP para permitir que as equipas centrais identificem conteúdo programático no serviço Power BI.  
    * Os administradores poderão impor a aplicação de rótulos em conteúdos novos ou editados com uma política de etiquetas obrigatória no serviço Power BI (pré-visualização).
    * Rotulagem automática de artefactos a jusante dentro do serviço Power BI. Quando uma etiqueta num conjunto de dados é aplicada ou alterada, a etiqueta será automaticamente aplicada em todos os conteúdos a jusante ligados a este artefacto.

Consulte a documentação do [rótulo de sensibilidade da Proteção de Informação](../admin/service-security-sensitivity-label-overview.md) da Microsoft no Power BI para obter mais detalhes.

### <a name="microsoft-cloud-app-security-mcas-for-power-bi"></a>Microsoft Cloud App Security (MCAS) para Power BI

O Microsoft Cloud App Security é um dos principais corretores de segurança de acesso à nuvem do mundo, nomeado como líder no Quadrante Mágico da Gartner para o mercado do Cloud Access Security Broker (CASB). A segurança da aplicação cloud é usada para garantir o uso de aplicações na nuvem. Permite que as organizações monitorizem e controlem, em tempo real, sessões de Power BI arriscadas, como o acesso do utilizador a dispositivos não geridos. Os administradores de segurança podem definir políticas para controlar as ações dos utilizadores, tais como descarregar relatórios com informações sensíveis.

Com a Cloud App Security, as organizações podem ganhar as seguintes capacidades DLP: 
* Deslo deixe de ser definidos controlos em tempo real para impor sessões de utilizador arriscadas no Power BI. Por exemplo, se um utilizador ligar-se ao Power BI de fora do seu país, a sessão pode ser monitorizada pelos controlos em tempo real da Cloud App Security, e as ações de risco, como o descarregamento de dados marcados com uma etiqueta de sensibilidade "Altamente Confidencial", podem ser bloqueadas imediatamente.
* Investigue a atividade do utilizador power bi com o registo de atividade da Cloud App Security. O registo de atividades de Segurança da Cloud App inclui a atividade do Power BI capturada no registo de auditoria do Office 365, que contém informações sobre todas as atividades de utilizador e administração, bem como informações de etiquetas de sensibilidade para atividades relevantes como aplicar, alterar e remover o rótulo. Os administradores podem aproveitar os filtros avançados da Cloud App Security e ações rápidas para uma investigação eficaz de problemas. 
* Crie políticas personalizadas para alertar sobre a atividade suspeita do utilizador no Power BI. A funcionalidade de política de atividade da Cloud App Security pode ser aproveitada para definir as suas próprias regras personalizadas, para ajudá-lo a detetar o comportamento do utilizador que se desvia da norma, e até mesmo possivelmente agir automaticamente, se parecer demasiado perigoso.
* Trabalhe com a deteção de anomalias incorporadas da Cloud App Security. As políticas de deteção de anomalias da Cloud App Security fornecem análises comportamentais e machine learning do utilizador fora da caixa, de modo a que esteja pronto desde o início para executar uma deteção avançada de ameaças em todo o seu ambiente em nuvem. Quando uma política de deteção de anomalias identifica um comportamento suspeito, desencadeia um alerta de segurança. 
* Power BI papel de administrador no portal Cloud App Security. Cloud App Security fornece uma função de administração específica de aplicações que pode ser usada para conceder aos administradores power BI apenas as permissões que precisam para aceder a dados relevantes do Power BI no portal, tais como alertas, utilizadores em risco, registos de atividade e outras informações relacionadas com o Power BI.

Consulte [a utilização dos controlos de segurança da aplicação da Cloud Cloud em Power BI](../admin/service-security-using-microsoft-cloud-app-security-controls.md) para obter mais detalhes.

## <a name="preview-security-features"></a>Pré-visualizar funcionalidades de segurança

Este tópico lista funcionalidades que estão previstas para ser lançadas até março de 2021. Como este tópico lista funcionalidades que podem ainda não ter sido **lançadas, os prazos de entrega podem mudar e a funcionalidade projetada pode ser lançada mais tarde, até março de 2021, ou pode não ser lançada de todo**. Para mais informações, sobre pré-visualizações, por favor reveja os [Termos de Serviços Online.](https://www.microsoft.com/licensing/product-licensing/products)

### <a name="bring-your-own-log-analytics-byola"></a>Traga o seu próprio log analytics (BYOLA)

Bring Your Own Log Analytics permite a integração entre Power BI e Azure Log Analytics. Esta integração inclui o motor analítico avançado do Azure Log Analytics, a linguagem de consulta interativa e as construções de aprendizagem automática incorporada.

## <a name="power-bi-security-questions-and-answers"></a>Perguntas e respostas de segurança do Power BI

Seguem-se perguntas e respostas comuns relacionadas com a segurança do Power BI. Estas são organizadas com base no momento em que foram adicionadas a este livro branco, para facilitar a sua capacidade de encontrar rapidamente novas perguntas e respostas quando este trabalho for atualizado. As perguntas mais recentes são adicionadas ao fim desta lista.

**Como é que os utilizadores se ligam e obtêm acesso às origens de dados ao utilizar o Power BI?**

* Power BI gere credenciais para fontes de dados para cada utilizador para credenciais de nuvem ou para conectividade através de um gateway pessoal. As fontes de dados geridas por um gateway de dados no local podem ser partilhadas em toda a empresa e as permissões a estas fontes de dados podem ser geridas pelo Gateway Admin. Ao configurar um conjunto de dados, o utilizador é autorizado a selecionar uma credencial a partir da sua loja pessoal ou a utilizar uma porta de dados no local para utilizar uma credencial partilhada.

    No caso da importação, um utilizador estabelece uma ligação com base no login do utilizador e acede aos dados com a credencial. Após a publicação do conjunto de dados para o serviço Power BI, o Power BI utiliza sempre a credencial deste utilizador para importar dados. Uma vez importados os dados, a visualização dos dados nos relatórios e no painel de instrumentos não acede à fonte de dados subjacente. O Power BI suporta uma autenticação única para fontes de dados selecionadas. Se a ligação estiver configurada para utilizar um único sinal de acesso, a credencial do titular do conjunto de dados é utilizada para se ligar à fonte de dados.

    Para relatos que estejam ligados ao DirectQuery, a fonte de dados está ligada diretamente utilizando uma credencial pré-configurada, a credencial pré-configurada é usada para ligar à fonte de dados quando qualquer utilizador vê os dados. Se uma fonte de dados estiver ligada diretamente utilizando um único sinal, a credencial do utilizador atual é utilizada para ligar à fonte de dados quando o utilizador visualiza os dados. Ao utilizar com um único sinal de acesso, a Row Level Security (RLS) pode ser implementada na fonte de dados, o que permite que os utilizadores vejam dados a que têm privilégios de acesso. Quando a ligação é para fontes de dados na nuvem, a autenticação AZure AD é utilizada para uma única sação; para fontes de dados on-prem, Kerberos, SAML e Azure AD são suportados.  

    Ao ligar-se com kerberos, a UPN do utilizador é passada para o gateway, e utilizando a delegação restrita kerberos, o utilizador é personificado e ligado às respetivas fontes de dados. A SAML também é suportada no Gateway para fonte de dados SAP HANA. Mais informações estão disponíveis no [resumo de um único sinal de entrada para gateways](../connect-data/service-gateway-sso-overview.md).

    Se a fonte de dados for a Azure Analysis Services ou no local Os Serviços de Análise e Segurança de Nível de Linha (RLS) estiver configurado, o serviço Power BI aplicará essa segurança ao nível da linha, e os utilizadores que não possuam credenciais suficientes para aceder aos dados subjacentes (o que pode ser uma consulta utilizada num dashboard, relatório ou outro artefacto de dados) não verá dados para os quais o utilizador não tem privilégios suficientes.

    [A segurança do nível de linha com o Power BI](../admin/service-admin-rls.md) pode ser usada para restringir o acesso de dados a determinados utilizadores. Os filtros restringem o acesso aos dados ao nível da linha, e pode definir filtros dentro do papel.  

**Como é que os dados são transferidos para o Power BI?**

* Todos os dados solicitados e transmitidos pelo Power BI são encriptados em trânsito utilizando HTTPS (exceto quando a fonte de dados escolhida pelo cliente não suporta HTTPS) para ligar da fonte de dados ao serviço Power BI. É estabelecida uma ligação segura com o fornecedor de dados e apenas quando essa ligação for estabelecida é que os dados percorrerão a rede.

**Como é que o Power BI coloca em cache dados de relatórios, dashboards ou modelos e é garantida a segurança desse processo?**

* Quando uma fonte de dados é acedida, o serviço Power BI segue o processo descrito na secção [Autenticação a Fontes de Dados](#authentication-to-data-sources) anteriormente neste documento.

**Os clientes colocam em cache dados de páginas Web localmente?**

* Quando os clientes de browser acedem ao Power BI, os servidores Web do Power BI definem a diretiva *Cache-Control* para *no-store*. A diretiva *no-store* instrui os browsers para não colocarem em cache a página Web que está a ser visualizada pelo utilizador e não para a armazenarem na pasta de cache do cliente.

**E a segurança baseada em funções, a partilha de relatórios ou dashboards e ligações de dados? Como é que isso funciona em termos de acesso a dados, visualização do painel de instrumentos, acesso ao relatório ou atualização?**

* Para origens de dados não compatíveis com a **Segurança ao Nível da Função (RLS)**, se um dashboard, relatório ou modelo de dados for partilhado com outros utilizadores através do Power BI, os dados são disponibilizados aos utilizadores com os quais são partilhados para visualização e interação. O Power BI *não* autentica novamente os utilizadores relativamente à origem de dados original. Assim que os dados forem carregados para o Power BI, o utilizador autenticado relativamente à origem de dados é responsável por gerir que outros utilizadores e grupos podem ver os dados.

  Quando as ligações de dados são feitas a uma fonte de dados capaz de **RLS,** como uma fonte de dados dos Serviços de Análise, apenas os dados do dashboard são cached no Power BI. Sempre que um relatório ou conjunto de dados é visualizado ou acedido no Power BI e utiliza dados da origem de dados adequada para RLS, o serviço Power BI acede à origem de dados para obter dados com base nas credenciais do utilizador e, se existirem permissões suficientes, os dados são carregados para o relatório ou modelo de dados para esse utilizador. Se a autenticação falhar, será apresentado um erro ao utilizador.

  Para mais informações, consulte a secção [Autenticação para Fontes de Dados](#authentication-to-data-sources) no documento.

**Os nossos utilizadores conectam-se sempre às mesmas fontes de dados, algumas das quais requerem credenciais que diferem das suas credenciais de domínio. Como podem evitar ter de inserir estas credenciais sempre que fazem uma ligação de dados?**

* O Power BI disponibiliza o [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md), uma funcionalidade que permite aos utilizadores criar credenciais para múltiplas origens de dados diferentes e, em seguida, utilizar automaticamente essas credenciais ao aceder posteriormente a cada uma dessas dados origens. Para obter mais informações, veja [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md).

**Quais portas são utilizadas por gateway de dados no local e gateway pessoal? Há algum nome de domínio que precise de ser permitido para fins de conectividade?**

* A resposta detalhada a esta pergunta está disponível no seguinte link: [Gateway ports](/data-integration/gateway/service-gateway-communication#ports)

**Ao trabalhar com o portal de dados no local, como são utilizadas as chaves de recuperação e onde são armazenadas? E a gestão de credenciais seguras?**

* Durante a instalação e a configuração do gateway, o administrador introduz uma **Chave de Recuperação** do mesmo. Esta **Chave de Recuperação** é usada para gerar uma chave simétrica forte da AES. Uma chave assimétrica RSA também é criada ao mesmo tempo.

    As teclas geradas (RSA e AES) estão guardadas num ficheiro localizado na máquina local. Esse ficheiro também é encriptado. O conteúdo do ficheiro só pode ser desencriptado por esse computador Windows específico e apenas por essa conta do serviço de gateway específica.

    Quando um utilizador introduz credenciais da origem de dados na IU do serviço Power BI, as mesmas são encriptadas com a chave pública no browser. O gateway desencripta as credenciais utilizando a chave privada RSA e reencripta-as com uma chave simétrica AES antes de os dados serem armazenados no serviço Power BI. Com esse processo, o serviço Power BI nunca tem acesso aos dados não encriptados.

**Que protocolos de comunicação são utilizados pelo gateway de dados no local e como são protegidos?**

* O gateway suporta os dois seguintes protocolos de comunicações:

  - AMQP 1.0 – TCP + TLS: Este protocolo requer que as portas 443, 5671-5672 e 9350-9354 estejam abertas para comunicação de saída. Esse protocolo é preferível, uma vez que tem uma menor sobrecarga de comunicações.

  - HTTPS – WebSockets over HTTPS + TLS: Este protocolo utiliza apenas a porta 443. O WebSocket é iniciado por uma única mensagem HTTP CONNECT. Assim que o canal é estabelecido, a comunicação é essencialmente TCP + TLS. Pode forçar a porta de entrada a utilizar este protocolo modificando uma definição descrita [no artigo de gateway no local](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

**Qual é a função da CDN do Azure no Power BI?**

* Conforme mencionado anteriormente, o Power BI utiliza a Rede de Entrega de Conteúdos (CDN) do Azure para distribuir de modo eficiente o conteúdo e os ficheiros estáticos necessários para os utilizadores com base na região geográfica. Mais especificamente, o serviço Power BI utiliza múltiplas CDNs para distribuir de forma eficiente o conteúdo e os ficheiros estáticos necessários aos utilizadores através da Internet pública. Estes ficheiros estáticos incluem transferências de produtos (como o Power BI Desktop, o gateway de dados no local ou aplicações Power BI a partir de vários fornecedores de serviço independentes), ficheiros de configuração do browser utilizados para iniciar e estabelecer quaisquer ligações posteriores ao serviço Power BI, bem como a página de início de sessão seguro inicial do Power BI.

  Com base nas informações fornecidas durante uma ligação inicial ao serviço Power BI, o browser do utilizador contacta a CDN do Azure especificada (ou, para alguns ficheiros, o WFE) para transferir a coleção de ficheiros comuns especificados necessários para permitir a interação do browser com o serviço Power BI. A página do navegador inclui então o token AD AD Azure, informações de sessão, a localização do cluster back-end associado e a recolha de ficheiros descarregados do cluster Azure CDN e WFE, durante a duração da sessão de navegador de serviço Power BI.

**Para os visuais power BI, a Microsoft efetua alguma avaliação de segurança ou privacidade do código visual personalizado antes de publicar artigos na Galeria?**

* Não. É da responsabilidade do cliente analisar e determinar se o código do elemento visual personalizado é confiável. Todos os códigos de elementos visuais personalizados são processados num ambiente sandbox, de forma que qualquer código anómalo num elemento visual personalizado não afete negativamente o resto do serviço Power BI.

**Existem outros elementos visuais do Power BI que enviam informações para fora da rede do cliente?**

* Sim. Os elementos visuais do Mapas Bing e da ESRI transmitem dados para fora do serviço Power BI, caso utilizem esses serviços.

**Para aplicações de modelo, a Microsoft realiza alguma avaliação de segurança ou privacidade da aplicação do modelo antes de publicar itens na Galeria?**
* Não. O editor da aplicação é responsável pelo conteúdo enquanto é da responsabilidade do cliente rever e determinar se deve confiar no editor de aplicações do modelo. 

**Existem aplicações de modelo que podem enviar informações fora da rede de clientes?**
* Sim. É da responsabilidade do cliente rever a política de privacidade da editora e determinar se deve instalar a aplicação do modelo no arrendatário. A editora é responsável por informar o cliente sobre o comportamento e capacidades da aplicação.

**E a soberania dos dados? Podemos fornecer inquilinos em centros de dados localizados em geografias específicas, para garantir que os dados não saem das fronteiras do país?**

* Alguns clientes em determinadas localizações geográficas têm a opção de criar um inquilino numa cloud nacional, onde o armazenamento e o processamento de dados é mantido separado de todos os outros datacenters. As clouds nacionais têm um tipo de segurança ligeiramente diferente, uma vez que um administrador de dados em separado opera o serviço Power BI da cloud nacional em nome da Microsoft.

  Em alternativa, os clientes também podem criar um inquilino numa região específica. No entanto, estes inquilinos não têm um administrador de dados separado da Microsoft. Os preços das clouds nacionais são diferentes dos preços do serviço Power BI comercial disponível para o público. Para obter mais informações sobre a disponibilidade do serviço Power BI para clouds nacionais, veja as [clouds nacionais do Power BI](https://powerbi.microsoft.com/clouds/).

**Como é que a Microsoft trata as ligações para clientes que têm subscrições Power BI Premium? Essas ligações são diferentes das estabelecidas para o serviço de BI de potência não Premium?**

* As ligações estabelecidas para clientes com subscrições Power BI Premium implementam um processo de autorização [Azure Business-to-Business (B2B),](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) utilizando a Azure AD para permitir o controlo e autorização de acesso. O Power BI processa ligações de subscritores do Power BI Premium para recursos do Power BI Premium tal como faria com qualquer utilizador do Azure AD.

## <a name="feedback-and-suggestions"></a>Feedback e sugestões

Valorizamos o seu feedback. Estamos interessados em ouvir quaisquer sugestões que tenha para melhorias, adições ou esclarecimentos a este livro branco, ou outros conteúdos relacionados com o Power BI. Envie as suas sugestões para [pbiss@microsoft.com](mailto:pbiss@microsoft.com) .

## <a name="additional-resources"></a>Recursos adicionais

Para obter mais informações sobre o Power BI, veja os recursos seguintes.

* [Introdução ao Power BI Desktop](../fundamentals/desktop-getting-started.md)
* [API REST do Power BI – Descrição Geral](/rest/api/power-bi/)
* [Referência da API do Power BI](/rest/api/power-bi/)
* [On-premises data gateway (Gateway de dados no local)](../connect-data/service-gateway-onprem.md)
* [Clouds Nacionais do Power BI](https://powerbi.microsoft.com/clouds/)
* [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Descrição geral do início de sessão único (SSO) para gateways no Power BI](../connect-data/service-gateway-sso-overview.md)