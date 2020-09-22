---
title: Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure Active Directory B2B
description: Whitepaper que descreve como usar o Azure Ative Directory B2B para distribuir Power BI a utilizadores convidados externos
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 9125c87f96641852a16410d3f8287c714816fb4b
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965366"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure Active Directory B2B

**Resumo:** Este é um papel técnico que descreve como distribuir conteúdo a utilizadores fora da organização utilizando a integração do Azure Ative Directory Business-to-business (Azure AD B2B).

**Escritores:** Lukasz Pawlowski

**Revisores Técnicos:** Adam Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Maya Shenhav, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> Pode guardar ou imprimir este papel branco selecionando **Imprimir** no seu navegador e, em seguida, selecionar **Guardar como PDF**.

## <a name="introduction"></a>Introdução

O Power BI dá às organizações uma visão de 360 graus do seu negócio e capacita todos nestas organizações para tomarem decisões inteligentes usando dados. Muitas destas organizações têm relações fortes e confiáveis com parceiros externos, clientes e empreiteiros. Estas organizações precisam de fornecer acesso seguro aos dashboards e relatórios do Power BI aos utilizadores destes parceiros externos.

O Power BI [integra-se com o Azure Ative Directory Business-to-business (Azure AD B2B)](/azure/active-directory/b2b/what-is-b2b) para permitir a distribuição segura de conteúdos power BI a utilizadores convidados fora da organização – mantendo o controlo e regendo o acesso aos dados internos.

Este livro branco cobre todos os detalhes necessários para entender a integração do Power BI com o Azure Ative Directory B2B. Cobrimos o seu caso de uso mais comum, configuração, licenciamento e segurança de nível de linha.

> [!NOTE]
> Ao longo deste livro branco, referimo-nos ao Azure Ative Directory como Azure AD e Azure Ative Directory Business to Business como Azure AD B2B.

## <a name="scenarios"></a>Cenários

A Contoso é um fabricante automóvel e trabalha com muitos fornecedores diversos que lhe fornecem todos os componentes, materiais e serviços necessários para executar as suas operações de fabrico. A Contoso quer dinamizar a logística da sua cadeia de abastecimento e planeia utilizar o Power BI para monitorizar as principais métricas de desempenho da sua cadeia de fornecimento. A Contoso quer partilhar com os parceiros externos da cadeia de fornecimento analítica de forma segura e manejável.

A Contoso pode permitir as seguintes experiências para utilizadores externos utilizando o Power BI e o Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc por partilha de item

A Contoso trabalha com um fornecedor que constrói radiadores para os carros da Contoso. Muitas vezes, precisam de otimizar a fiabilidade dos radiadores utilizando dados de todos os carros de Contoso. Um analista da Contoso usa o Power BI para partilhar um relatório de fiabilidade do radiador com um Engenheiro no fornecedor. O Engenheiro recebe um e-mail com um link para ver o relatório.

Conforme descrito acima, esta partilha ad-hoc é realizada pelos utilizadores empresariais numa base necessária. O link enviado pelo Power BI ao utilizador externo é um link de convite Azure AD B2B. Quando o utilizador externo abre o link, é-lhes pedido que se juntem à organização Azure AD da Contoso como utilizador convidado. Após a aceitação do convite, o link abre o relatório específico ou o painel de instrumentos. O Azure Ative Directory delega permissão para convidar utilizadores externos para a organização e escolhe o que esses utilizadores podem fazer uma vez que aceitam o convite como descrito na secção de Governação deste documento. O analista contoso só pode convidar o utilizador Convidado porque o administrador da AD Azure permitiu que a ação e o administrador do Power BI permitissem que os utilizadores convidassem os hóspedes a visualizar conteúdos nas configurações do power bi.

![Convidar os hóspedes para o Power BI usando a AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. O processo começa com um utilizador interno da Contoso a partilhar um dashboard ou um relatório com um utilizador externo. Se o utilizador externo já não for um hóspede no Azure AD da Contoso, eles são convidados. Um e-mail é enviado para o seu endereço de e-mail que inclui um convite para a Ad Azure da Contoso
2. O destinatário aceita o convite para o Azure AD de Contoso e é adicionado como um utilizador convidado no Azure AD de Contoso.
3. O destinatário é então redirecionado para o painel, relatório ou app Power BI, que são apenas de leitura para o utilizador.

O processo é considerado ad-hoc uma vez que os utilizadores empresariais em Contoso realizam a ação de convite conforme necessário para os seus fins comerciais. Cada item partilhado é um único link que o utilizador externo pode aceder para ver o conteúdo.

Uma vez que o utilizador externo tenha sido convidado a aceder aos recursos do Contoso, pode ser criada uma conta sombra para eles em Contoso AD e não precisam de ser convidados novamente.  A primeira vez que tentam aceder a um recurso Contoso como um dashboard Power BI, passam por um processo de consentimento, que resgata o convite.  Se não completarem o consentimento, não podem aceder a nenhum dos conteúdos de Contoso.  Se tiverem dificuldade em resgatar o seu convite através do link original fornecido, um administrador da AD Azure pode ressentir-se de um link de convite específico para que eles possam resgatar.

### <a name="planned-per-item-sharing"></a>Planejado por partilha de item

Contoso trabalha com um subempreiteiro para realizar análises de fiabilidade dos radiadores. O subempreiteiro tem uma equipa de 10 pessoas que precisam de acesso aos dados no ambiente Power BI da Contoso. O administrador da Contoso Azure AD está envolvido para convidar todos os utilizadores e lidar com quaisquer adições/alterações como pessoal na mudança do subempreiteiro. O administrador da AD Azure cria um grupo de segurança para todos os colaboradores do subempreiteiro. Utilizando o grupo de segurança, os colaboradores da Contoso podem facilmente gerir o acesso aos relatórios e garantir que todo o pessoal subcontratado necessário tenha acesso a todos os relatórios, dashboards e aplicações power bi necessários. O administrador da AD Azure também pode evitar participar completamente no processo de convite, optando por delegar direitos de convite a um funcionário de confiança na Contoso ou no subcontratado para garantir a gestão atemida do pessoal.

Algumas organizações exigem mais controlo quando os utilizadores externos são adicionados, estão convidando muitos utilizadores numa organização externa, ou muitas organizações externas. Nestes casos, a partilha planeada pode ser usada para gerir a escala da partilha, para impor políticas organizacionais, e até para delegar direitos a pessoas de confiança para convidar e gerir utilizadores externos. O Azure AD B2B suporta convites planeados para serem enviados diretamente [do portal Azure por um administrador de TI](/azure/active-directory/b2b/add-users-administrator), ou através do [PowerShell utilizando o gestor de convites API,](/azure/active-directory/b2b/customize-invitation-api) onde um conjunto de utilizadores pode ser convidado numa única ação. Utilizando a abordagem de convites planeada, a organização pode controlar quem pode convidar os utilizadores e implementar processos de aprovação. As capacidades avançadas de Azure AD, como grupos dinâmicos, podem facilitar a manutenção automática da adesão ao grupo de segurança.


![Controlo que os hóspedes podem ver conteúdo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. O processo começa com um administrador de TI convidando o utilizador convidado manualmente ou através da API fornecida pelo Azure Ative Directory
2. O utilizador aceita o convite para a organização.
3. Uma vez que o utilizador tenha aceite o convite, um utilizador no Power BI pode partilhar um relatório ou painel com o utilizador externo, ou um grupo de segurança em que se encontre. Tal como acontece com a partilha regular no Power BI, o utilizador externo recebe um e-mail com o link para o item.
4. Quando o utilizador externo acede ao link, a sua autenticação no seu diretório é transmitida ao Azure AD da Contoso e utilizado para aceder ao conteúdo do Power BI.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Partilha ad hoc ou planeada de Power BI Apps

A Contoso tem um conjunto de relatórios e dashboards que precisam de partilhar com um ou mais Fornecedores. Para garantir que todos os utilizadores externos necessários tenham acesso a este conteúdo, este é embalado como uma aplicação Power BI. Os utilizadores externos são adicionados diretamente à lista de acesso à aplicação ou através de grupos de segurança. Alguém na Contoso envia então o URL da aplicação a todos os utilizadores externos, por exemplo, num e-mail. Quando os utilizadores externos abrem o link, vêem todo o conteúdo numa única experiência fácil de navegar.

A utilização de uma aplicação Power BI facilita a construção de um Portal BI para os seus fornecedores. Uma única lista de acesso controla o acesso a todos os conteúdos necessários, reduzindo as permissões de tempo desperdiçados e definindo permissões de nível de produto. O Azure AD B2B mantém o acesso à segurança utilizando a identidade nativa do Fornecedor para que os utilizadores não necessitem de credenciais de login adicionais. Se utilizar convites planeados com grupos de segurança, a gestão de acesso à app à medida que o pessoal gira para dentro ou para fora do projeto é simplificada. A adesão a grupos de segurança manualmente ou utilizando [grupos dinâmicos](/azure/active-directory/b2b/use-dynamic-groups), de modo a que todos os utilizadores externos de um fornecedor sejam automaticamente adicionados ao grupo de segurança apropriado.


![Controlar conteúdo com AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. O processo começa pelo utilizador ser convidado para a organização Azure AD da Contoso através do portal Azure ou PowerShell
2. O utilizador pode ser adicionado a um grupo de utilizadores em Azure AD. Um grupo de utilizadores estático ou dinâmico pode ser usado, mas grupos dinâmicos ajudam a reduzir o trabalho manual.
3. Os utilizadores externos têm acesso à Aplicação Power BI através do grupo de utilizadores. O URL da aplicação deve ser enviado diretamente para o utilizador externo ou colocado num site a que tenha acesso. O Power BI faz um melhor esforço para enviar um e-mail com o link da aplicação para utilizadores externos, mas ao utilizar grupos de utilizadores cuja adesão pode mudar, o Power BI não é capaz de enviar a todos os utilizadores externos geridos através de grupos de utilizadores.
4. Quando o utilizador externo acede ao URL da aplicação Power BI, são autenticados pelo Azure AD da Contoso, a aplicação é instalada para o utilizador, e o utilizador pode ver todos os relatórios e dashboards contidos dentro da app.

As aplicações também têm uma funcionalidade única que permite aos autores de aplicações instalar a aplicação automaticamente para o utilizador, pelo que está disponível quando o utilizador iniciar sessão. Esta funcionalidade apenas se instala automaticamente para utilizadores externos que já fazem parte da organização da Contoso no momento em que a aplicação é publicada ou atualizada. Assim, é melhor utilizado com a abordagem de convites planeada, e depende da aplicação ser publicada ou atualizada após a adição dos utilizadores ao Azure AD de Contoso. Os utilizadores externos podem sempre instalar a aplicação utilizando o link da aplicação.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Comentar e subscrever conteúdos entre organizações

Enquanto a Contoso continua a trabalhar com os seus subempreiteiros ou fornecedores, os Engenheiros Externos precisam de trabalhar em estreita colaboração com os analistas da Contoso. O Power BI fornece várias funcionalidades de colaboração que ajudam os utilizadores a comunicar sobre conteúdos que podem consumir. O painel de comentários (e logo reportar comentários) permite que os utilizadores discutam pontos de dados que vêem e comunicam com autores de relatórios para fazer perguntas.

Atualmente, os utilizadores de hóspedes externos podem participar em comentários deixando comentários e lendo as respostas. No entanto, ao contrário dos utilizadores internos, os utilizadores convidados não podem estar @mentioned e não recebem notificações de que receberam um comentário. Os utilizadores convidados não podem utilizar a funcionalidade de subscrições dentro do Power BI no momento da escrita. Numa próxima versão, essas restrições serão levantadas e o utilizador do Guest receberá um e-mail quando um @mentions comentário, ou quando uma subscrição for entregue no seu e-mail que contenha um link para o conteúdo no Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Aceder a conteúdos nas aplicações móveis Power BI

Numa próxima versão, quando os utilizadores de Contoso partilharem relatórios ou dashboards com os seus homólogos externos do Guest, o Power BI enviará um e-mail a notificar o Convidado. Quando o utilizador convidado abrir o link para o relatório ou painel de instrumentos no seu dispositivo móvel, o conteúdo abrir-se-á nas aplicações móveis power BI nativas do seu dispositivo, se forem instaladas. O utilizador convidado poderá então navegar entre conteúdos partilhados com eles no arrendatário externo e voltar ao seu próprio conteúdo a partir do seu inquilino de casa.

> [!NOTE]
> O utilizador convidado não pode abrir a aplicação móvel Power BI e navegar imediatamente para o inquilino externo, deve começar com um link para um item no inquilino externo. As soluções comuns são descritas nas ligações de distribuição de conteúdos na secção [Power BI da organização-mãe](#distributing-links-to-content-in-the-parent-organizations-power-bi) mais tarde neste documento.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Edição e gestão inter-organizacional de conteúdos do Power BI

A Contoso e os seus Fornecedores e subempreiteiros trabalham cada vez mais em conjunto. Muitas vezes, um analista do subempreiteiro precisa de métricas adicionais ou visualizações de dados para ser adicionado a um relatório que Contoso partilhou com eles. Os dados devem residir no inquilino power bi da Contoso, mas os utilizadores externos devem ser capazes de editá-lo, criar novos conteúdos e até distribuí-lo para indivíduos apropriados.

O Power BI fornece uma opção que permite que **os utilizadores externos possam editar e gerir conteúdos** na organização. Por padrão, os utilizadores externos têm uma experiência orientada para o consumo apenas para leitura. No entanto, esta nova definição permite ao administrador power BI escolher quais os utilizadores externos que podem editar e gerir conteúdos dentro da sua própria organização. Uma vez permitido, o utilizador externo pode editar relatórios, dashboards, publicar ou atualizar aplicações, trabalhar em espaços de trabalho e ligar-se aos dados que tem permissão para usar.

Este cenário é descrito em detalhe na secção Permitindo que os utilizadores externos editem e gerem conteúdos dentro do Power BI mais tarde neste documento.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Relações organizacionais usando Power BI e Azure AD B2B

Quando todos os utilizadores do Power BI são internos para a organização, não há necessidade de usar Azure AD B2B. No entanto, uma vez que duas ou mais organizações querem colaborar em dados e insights, o apoio do Power BI ao Azure AD B2B torna fácil e rentável fazê-lo.

Abaixo estão tipicamente encontradas estruturas organizacionais que são adequadas para a colaboração inter-organização do estilo Azure AD B2B no Power BI. O Azure AD B2B funciona bem na maioria dos casos, mas em algumas situações as abordagens alternativas comuns abrangidas no final deste documento merecem ser considerados.

### <a name="case-1-direct-collaboration-between-organizations"></a>Caso 1: Colaboração direta entre organizações

A relação de Contoso com o seu fornecedor de radiadores é um exemplo de colaboração direta entre organizações. Uma vez que existem relativamente poucos utilizadores na Contoso e no seu fornecedor que precisam de acesso a informações de fiabilidade do radiador, a utilização de partilha externa baseada em Azure AD B2B é ideal. É fácil de usar e simples de administrar. Este é também um padrão comum em serviços de consultoria onde um consultor pode precisar de construir conteúdo para uma organização.

![Partilhar entre organizações](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Tipicamente, esta partilha ocorre inicialmente usando ad hoc por partilha de item. No entanto, à medida que as equipas crescem ou as relações se aprofundam, a abordagem planeada por partilha de item torna-se o método preferido para reduzir a sobrecarga de gestão. Além disso, a partilha ad hoc ou planeada de Power BI Apps, Comentando e subscrevendo conteúdos em todas as organizações, o acesso a conteúdos em aplicações móveis também pode entrar em jogo, e edição e gestão inter-organizacional de conteúdos power bi. Importante, se os utilizadores de ambas as organizações tiverem licenças Power BI Pro nas respetivas organizações, podem usar essas licenças Pro nos ambientes power bi uns dos outros. Isto proporciona um licenciamento vantajoso, uma vez que a organização convidativa pode não precisar de pagar uma licença Power BI Pro para os utilizadores externos. Isto é discutido mais detalhadamente na secção de licenciamento mais tarde neste documento.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Caso 2: Pai e suas filiais ou filiais

Algumas estruturas de organização são mais complexas, incluindo subsidiárias, empresas afiliadas ou relações de prestadores de serviços parcial ou integralmente detidas. Estas organizações têm uma organização-mãe, como uma holding, mas as organizações subjacentes operam semi-autónoma, por vezes sob diferentes requisitos regionais. Isto leva a que cada organização tenha o seu próprio ambiente Azure AD e inquilinos de Power BI separados.

![Trabalhar com subsidiárias](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


Nesta estrutura, a organização-mãe normalmente precisa de distribuir insights padronizados às suas subsidiárias. Tipicamente, esta partilha ocorre usando a partilha ad hoc ou planejada da abordagem Power BI Apps como ilustrado na imagem seguinte, uma vez que permite a distribuição de conteúdo autorizado padronizado para amplos públicos. Na prática, é utilizada uma combinação de todos os cenários mencionados anteriormente neste documento.

![Combinando cenários](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Segue-se o seguinte processo:

1. Os utilizadores de cada Subsidiária são convidados para o AD Azure da Contoso
2. Em seguida, a aplicação Power BI é publicada para dar a estes utilizadores acesso aos dados necessários
3. Finalmente, os utilizadores abrem a app através de um link que lhes foi dado para ver os relatórios

Vários desafios importantes são enfrentados por organizações desta estrutura:

- Como distribuir links para conteúdos no Power BI da organização-mãe
- Como permitir que os utilizadores subsidiários acedam à fonte de dados hospedada pela organização-mãe

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribuição de links para conteúdos no Power BI da organização-mãe

Três abordagens são geralmente usadas para distribuir links para o conteúdo. A primeira e mais básica é enviar o link para a app para os utilizadores necessários ou colocá-lo num site SharePoint Online a partir do qual pode ser aberto. Os utilizadores podem então reservar o link nos seus navegadores para um acesso mais rápido aos dados de que necessitam.

A segunda abordagem baseia-se na edição e gestão de conteúdos power bi. A organização Parent permite que os utilizadores das subsidiárias acedam ao seu Power BI e controlam o que podem aceder através de permissão. Isto dá acesso ao Power BI Home onde o utilizador da subsidiária vê uma lista completa de conteúdos partilhados com eles no inquilino da organização-mãe. Em seguida, o URL para o ambiente Power BI das organizações-mãe é dado aos utilizadores das subsidiárias.

A abordagem final utiliza uma aplicação Power BI criada dentro do inquilino Power BI para cada subsidiária. A aplicação Power BI inclui um dashboard com [azulejos configurados com a opção de ligação externa.](../create-reports/service-dashboard-edit-tile.md#hyperlink) Quando o utilizador pressiona o azulejo, são levados para o relatório apropriado, painel de instrumentos ou app no Power BI da organização-mãe. Esta abordagem tem a vantagem adicional de que a aplicação pode ser instalada automaticamente para todos os utilizadores da subsidiária e está disponível para eles sempre que eles iniciarem seduca no seu próprio ambiente Power BI. Uma vantagem adicional desta abordagem é que funciona bem com as aplicações móveis Power BI que podem abrir o link de forma nativa. Também pode combinar isto com a segunda abordagem para permitir uma melhor comutação entre ambientes Power BI.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Permitir que os utilizadores subsidiários acedam a fontes de dados hospedadas pela organização-mãe

Muitas vezes, os analistas de uma subsidiária precisam de criar a sua própria análise utilizando dados fornecidos pela organização-mãe. Neste caso, as fontes de dados em nuvem são usadas para enfrentar o desafio.

A primeira abordagem aproveita a [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) para construir um armazém de dados de nível empresarial que atende às necessidades dos Analistas em toda a empresa-mãe e nas suas subsidiárias, como mostra a imagem a seguir. A Contoso pode hospedar os dados e usar capacidades como segurança ao nível da linha para garantir que os utilizadores em cada subsidiária só podem aceder aos seus dados. Os analistas de cada organização podem aceder ao armazém de dados através do Power BI Desktop e publicar análises resultantes aos respetivos inquilinos do Power BI.

![Como a partilha ocorre com os inquilinos do Power BI](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


A segunda abordagem aproveita a [Base de Dados Azure SQL](https://azure.microsoft.com/services/sql-database/) para construir um armazém de dados relacional para fornecer acesso aos dados. Isto funciona da mesma forma com a abordagem dos Serviços de Análise Azure, embora algumas capacidades como a segurança ao nível da linha possam ser mais difíceis de implementar e manter em todas as subsidiárias.

Abordagens mais sofisticadas também são possíveis, no entanto as acima são, de longe, as mais comuns.

### <a name="case-3-shared-environment-across-partners"></a>Caso 3: Ambiente partilhado entre parceiros

A Contoso pode entrar em parceria com um concorrente para construir em conjunto um carro numa linha de montagem partilhada, mas para distribuir o veículo por diferentes marcas ou em diferentes regiões. Isto requer uma colaboração extensiva e copropriedade de dados, inteligência e análise entre organizações. Esta estrutura também é comum no setor dos serviços de consultoria onde uma equipa de consultores pode fazer análises baseadas em projetos para um cliente.

![Ambiente compartilhado entre parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



Na prática, estas estruturas são complexas como mostrado na imagem seguinte, e exigem que o pessoal se mantenha. Para ser eficaz, esta estrutura baseia-se na edição e gestão inter-organizacional da capacidade de conteúdo do Power BI, uma vez que permite às organizações reutilizar as licenças Power BI Pro adquiridas para os respetivos inquilinos do Power BI.

![Licenças e conteúdo de organização partilhada](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Para estabelecer um inquilino de Power BI partilhado, é necessário criar um Diretório Ativo Azure e pelo menos uma conta de utilizador Power BI Pro precisa de ser adquirida para um utilizador nesse diretório ativo. Este utilizador convida os utilizadores necessários para a organização partilhada. Importante, neste cenário, os utilizadores da Contoso são tratados como utilizadores externos quando operam dentro do Power BI da Organização Partilhada.

O processo é o seguinte:

1. A Organização Partilhada é criada como um novo Diretório Ativo Azure e pelo menos uma conta de utilizador é criada na nova organização. Esse utilizador deve ter uma licença Power BI Pro atribuída a eles.
2. Este utilizador estabelece então um inquilino power BI e convida os utilizadores necessários da Contoso e da organização Partner. O utilizador também estabelece quaisquer ativos de dados partilhados como os Azure Analysis Services. Contoso e os utilizadores do Partner podem aceder ao Power BI da organização partilhada como utilizadores convidados. Se for permitido editar e gerir conteúdos no Power BI, os utilizadores externos podem usar a casa Power BI, utilizar espaços de trabalho, carregar ou editar conteúdos e partilhar relatórios. Normalmente, todos os ativos partilhados são armazenados e acedidos a partir da organização partilhada.
3. Dependendo da forma como as partes concordam em colaborar, é possível que cada organização desenvolva os seus próprios dados e análises utilizando ativos de armazém de dados partilhados. Podem distribuí-las aos respetivos utilizadores internos utilizando os seus inquilinos internos do Power BI.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Caso 4: Distribuição a centenas ou milhares de parceiros externos

Enquanto Contoso criou um relatório de fiabilidade do radiador para um Fornecedor, agora Contoso deseja criar um conjunto de relatórios padronizados para centenas de Fornecedores. Isto permite que a Contoso garanta que todos os fornecedores têm a análise necessária para fazer melhorias ou corrigir defeitos de fabrico.

![Distribuição a muitos parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Quando uma organização precisa de distribuir dados e insights padronizados a muitos utilizadores/organizações externos, eles podem usar o cenário ad hoc ou a partilha planeada de Power BI Apps para construir um Portal BI rapidamente e sem custos de desenvolvimento extensivos. O processo de construção de tal portal através de uma aplicação Power BI é abordado no Case Study: Building a BI Portal utilizando o Power BI + Azure AD B2B – Instruções passo a passo mais tarde neste documento.

Uma variante comum deste caso é quando uma organização está a tentar partilhar insights com os consumidores, especialmente quando procura usar o Azure B2C com o Power BI. O Power BI não suporta de forma nativa o Azure B2C. Se estiver a avaliar opções para este caso, considere utilizar a Opção Alternativa 2 na alternativa Comum, aborda a secção mais tarde neste documento.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Estudo de Caso: Construção de um Portal BI utilizando Power BI + Azure AD B2B – Instruções passo a passo

A integração do Power BI com o Azure AD B2B dá à Contoso uma forma perfeita e sem problemas de fornecer aos utilizadores convidados um acesso seguro ao seu portal BI. Contoso pode configurar isto com três passos:

![Construção de um portal](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Criar portal do BI no Power BI

    A primeira tarefa para o Contoso é criar o seu portal BI no Power BI. O portal DE BI da Contoso será composto por uma coleção de dashboards e relatórios construídos de propósito que serão disponibilizados a muitos utilizadores internos e convidados. A forma recomendada para o fazer no Power BI é construir uma aplicação Power BI. Saiba mais sobre [aplicativos no Power BI.](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/)

- Equipa de BI da Contoso cria espaço de trabalho no Power BI

    ![área de trabalho](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Outros autores são adicionados ao espaço de trabalho

    ![Adicionar autores](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- O conteúdo é criado dentro do espaço de trabalho

    ![Criar conteúdo dentro do espaço de trabalho](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Agora que os conteúdos são criados num espaço de trabalho, a Contoso está pronta para convidar utilizadores convidados em organizações parceiras a consumirem este conteúdo.

2. Convidar Utilizadores

    Existem duas formas de a Contoso convidar os utilizadores convidados para o seu portal BI no Power BI:

    * Convites Planeados
    * Convites Ad hoc

    **Convites Planeados**

    Nesta abordagem, a Contoso convida os utilizadores convidados para o seu AD Azure com antecedência e, em seguida, distribui conteúdo power BI para eles. A Contoso pode convidar utilizadores convidados a partir do portal Azure ou usando o PowerShell. Aqui estão os passos para convidar os utilizadores convidados do portal Azure:

    - Administrador da AD Azure da Contoso navega para o **portal Azure > Azure Ative Directory > Utilizadores e grupos > Todos os utilizadores > Novo utilizador convidado**

    ![Utilizador convidado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Adicione uma mensagem de convite para os utilizadores convidados e clique em Convidar

    ![Adicionar convite](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Para convidar utilizadores convidados do portal Azure, precisa de um administrador para o Diretório Ativo Azure do seu inquilino.

    Se a Contoso quiser convidar muitos utilizadores convidados, podem fazê-lo usando o PowerShell. O administrador da AD Azure da Contoso armazena os endereços de e-mail de todos os utilizadores convidados num ficheiro CSV. Aqui estão o [código de colaboração B2B do Azure Ative Directory b2B e as amostras](/azure/active-directory/b2b/code-samples) e instruções powerShell.

    Após o convite, os utilizadores convidados recebem um e-mail com o link de convite.

    ![Link de convite](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Assim que os utilizadores convidados clicarem no link, podem aceder ao conteúdo do inquilino DaD Contoso Azure.

    > [!NOTE]
    > É possível alterar o layout do e-mail de convite usando a funcionalidade de marca Azure AD, conforme descrito [aqui.](/azure/active-directory/active-directory-b2b-invitation-email)


    **Convites Ad hoc**

    E se a Contoso não conhecer todos os utilizadores convidados que quer convidar com antecedência? Ou, e se o analista em Contoso que criou o portal BI quer distribuir conteúdo aos próprios utilizadores convidados? Também apoiamos este cenário no Power BI com convites ad-hoc.

    O analista pode apenas adicionar os utilizadores externos à lista de acesso da app quando estiverem a publicá-la. Os utilizadores convidados recebem um convite e assim que o aceitam, são automaticamente redirecionados para o conteúdo do Power BI.

    ![Adicionar utilizador externo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Os convites são necessários apenas a primeira vez que um utilizador externo é convidado para a sua organização.


3. Distribuir Conteúdo

    Agora que a equipa de BI da Contoso criou o portal bi e convidou os utilizadores convidados, podem distribuir o seu portal aos seus utilizadores finais, dando aos utilizadores convidados acesso à app e publicando-a. O Power BI completa automaticamente os nomes dos utilizadores convidados que foram previamente adicionados ao inquilino contoso. Os convites adhoc para outros utilizadores convidados também podem ser adicionados neste momento.

    > [!NOTE]
    > Se utilizar grupos de Segurança para gerir o acesso à aplicação para utilizadores externos, utilize a abordagem Convites Planeados e partilhe a ligação da aplicação diretamente com cada utilizador externo que deve aceder à sua. Caso contrário, o utilizador externo poderá não conseguir instalar ou visualizar conteúdos a partir do app._

    Os utilizadores convidados recebem um e-mail com um link para a aplicação.

    ![Link de convite de e-mail](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Ao clicar neste link, os utilizadores convidados são convidados a autenticar com a identidade da sua própria organização.

    ![Página de início de sessão](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Uma vez autenticados com sucesso, são redirecionados para a aplicação BI da Contoso.

    ![Ver conteúdo partilhado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Os utilizadores convidados podem posteriormente chegar à app do Contoso clicando no link no e-mail ou marcando o link. O Contoso também pode facilitar a vida aos utilizadores dos hóspedes, adicionando este link a qualquer portal de extranet existente que os utilizadores já utilizem.

4. Passos seguintes

    Utilizando uma aplicação Power BI e Azure AD B2B, a Contoso conseguiu rapidamente criar um Portal BI para os seus fornecedores de forma sem código. Esta distribuição muito simplificada da análise padronizada a todos os fornecedores que dela necessitavam.

    Embora o exemplo mostrasse como um único relatório comum poderia ser distribuído entre fornecedores, o Power BI pode ir muito mais longe. Para garantir que cada parceiro vê apenas dados relevantes para si mesmos, a Row Level Security pode ser adicionada facilmente ao relatório e modelo de dados. A secção de segurança de dados para parceiros externos mais tarde neste documento descreve este processo em detalhes.

    Muitas vezes, os relatórios individuais e os dashboards precisam de ser incorporados num portal existente. Isto também pode ser realizado reutilizando muitas das técnicas mostradas no exemplo. No entanto, nestas situações, pode ser mais fácil incorporar relatórios ou dashboards diretamente de um espaço de trabalho. O processo de convite e atribuição de permissão de segurança aos utilizadores requerendo permanecer o mesmo.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Sob o capot: Como é que a Lucy do Fornecedor1 consegue aceder ao conteúdo do Power BI do inquilino de Contoso?

Agora que vimos como a Contoso é capaz de distribuir sem problemas conteúdos Power BI a utilizadores convidados em organizações parceiras, vamos ver como isto funciona sob o capot.

Quando Contoso convidou [lucy@supplier1.com](mailto:lucy@supplier1.com) para o seu diretório, a Azure AD cria uma ligação entre [Lucy@supplier1.com](mailto:Lucy@supplier1.com) o inquilino da AD Contoso Azure. Este link permite à Azure AD saber que Lucy@supplier1.com pode aceder a conteúdos no inquilino contoso.

Quando Lucy tenta aceder à aplicação Power BI de Contoso, a Azure AD verifica que Lucy pode aceder ao inquilino contoso e, em seguida, fornece ao Power BI um símbolo que indica que Lucy é autenticada para aceder a conteúdos no inquilino contoso. Power BI usa este símbolo para autorizar e garantir que Lucy tem acesso à aplicação Power BI de Contoso.

![Verificação e autorização](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

A integração do Power BI com o Azure AD B2B funciona com todos os endereços de e-mail de negócios. Se o utilizador não tiver uma identidade AD Azure, poderá ser solicitado a criar um. A imagem a seguir mostra o fluxo detalhado:

![Gráfico de fluxo de integração](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


É importante reconhecer que a conta AZure AD será usada ou criada no AD Azure do partido externo, o que permitirá que a Lucy utilize o seu próprio nome de utilizador e palavra-passe e as suas credenciais deixarão automaticamente de trabalhar noutros inquilinos sempre que a Lucy deixar a empresa quando a sua organização também utiliza a AD Azure.

## <a name="licensing"></a>Licensing

A Contoso pode escolher uma das três abordagens para licenciar utilizadores convidados dos seus fornecedores e organizações parceiras para terem acesso ao conteúdo do Power BI.

> [!NOTE]
> _O nível livre do Azure AD B2B é suficiente para utilizar o Power BI com Azure AD B2B. Algumas funcionalidades avançadas do Azure AD B2B, como grupos dinâmicos, requerem licenças adicionais. Consulte a documentação do Azure AD B2B para obter informações adicionais:_[_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Abordagem 1: Contoso usa Power BI Premium

Com esta abordagem, a Contoso compra a capacidade Power BI Premium e atribui o seu conteúdo do portal BI a esta capacidade. Isto permite que utilizadores convidados de organizações parceiras acedam à aplicação Power BI da Contoso sem qualquer licença Power BI.

Os utilizadores externos também estão sujeitos ao consumo apenas experiências oferecidas aos utilizadores "gratuitos" no Power BI ao consumirem conteúdo dentro do Power BI Premium.

A Contoso também pode tirar partido de outras capacidades premium do Power BI para as suas apps, como taxas de atualização aumentadas, capacidade dedicada e grandes tamanhos de modelo.

![Capacidades adicionais](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Abordagem 2: Contoso atribui licenças Power BI Pro a utilizadores convidados

Com esta abordagem, a Contoso atribui licenças pro a utilizadores convidados de organizações parceiras – isto pode ser feito a partir do centro de administração Microsoft 365 da Contoso. Isto permite que utilizadores convidados de organizações parceiras acedam à aplicação Power BI da Contoso sem adquirirem uma licença por si mesmos. Isto pode ser apropriado para a partilha com utilizadores externos cuja organização ainda não adotou o Power BI.

> [!NOTE]
> A licença profissional de Contoso aplica-se apenas aos utilizadores convidados quando acedem a conteúdos no inquilino contoso. As licenças pro permitem o acesso a conteúdos que não se inseem na capacidade power BI Premium. No entanto, os utilizadores externos com licença Pro são restringidos por padrão a uma experiência de consumo único. Isto pode ser alterado utilizando a abordagem descrita no _Enableing utilizadores externos para editar e gerir conteúdos dentro_ da secção Power BI mais tarde neste documento.

![Informações sobre licenças](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Abordagem 3: Os utilizadores convidados trazem a sua própria licença Power BI Pro

Com esta abordagem, o Fornecedor 1 atribui uma licença Power BI Pro à Lucy. Podem então aceder à aplicação Power BI da Contoso com esta licença. Uma vez que a Lucy pode usar a sua licença Pro da sua própria organização ao aceder a um ambiente de Power BI externo, esta abordagem é por vezes referida como _trazer a sua própria licença_ (BYOL). Se ambas as organizações estiverem a utilizar o Power BI, este oferece um licenciamento vantajoso para a solução global de análise e minimiza a sobrecarga da atribuição de licenças a utilizadores externos.

> [!NOTE]
> A licença profissional dada à Lucy by Supplier 1 aplica-se a qualquer inquilino do Power BI onde a Lucy seja uma utilizadora convidada. As licenças pro permitem o acesso a conteúdos que não se inseem na capacidade power BI Premium. No entanto, os utilizadores externos com licença Pro são restringidos por padrão a uma experiência de consumo único. Isto pode ser alterado utilizando a abordagem descrita no _Enableing utilizadores externos para editar e gerir conteúdos dentro_ da secção Power BI mais tarde neste documento.

![Requisitos de licença pro](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Segurança de dados para parceiros externos

Geralmente quando trabalha com vários fornecedores externos, a Contoso precisa de garantir que cada fornecedor vê apenas dados sobre os seus próprios produtos. A segurança baseada no utilizador e a segurança dinâmica do nível da linha tornam isto fácil de realizar com o Power BI.

### <a name="user-based-security"></a>Segurança baseada no utilizador

Uma das características mais poderosas do Power BI é a Segurança de Nível de Linha. Esta funcionalidade permite que o Contoso crie um único relatório e conjunto de dados, mas ainda assim aplica regras de segurança diferentes para cada utilizador. Para obter uma explicação aprofundada, consulte [a segurança ao nível da linha (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

A integração do Power BI com o Azure AD B2B permite que a Contoso atribua regras de Segurança de Nível de Linha aos utilizadores convidados assim que são convidados para o inquilino contoso. Como vimos antes, o Contoso pode adicionar utilizadores convidados através de convites planeados ou ad-hoc. Se a Contoso quer impor a segurança ao nível da linha, recomenda-se vivamente a utilização de convites planeados para adicionar os utilizadores convidados com antecedência e atribuí-los às funções de segurança antes de partilhar o conteúdo. Se o Contoso, em vez disso, utilizar convites ad-hoc, poderá haver um curto período de tempo em que os utilizadores convidados não poderão ver quaisquer dados.

> [!NOTE]
> Este atraso no acesso aos dados protegidos pelo RLS ao utilizar convites ad-hoc pode levar a pedidos de suporte à sua equipa de TI, pois os utilizadores verão relatórios/dashboards de aparência em branco ou quebrados ao abrir um link de partilha no e-mail que recebem. Portanto, é fortemente recomendado usar convites planeados neste cenário.**

Vamos passar por isto com um exemplo.

Como mencionado anteriormente, a Contoso tem fornecedores em todo o mundo, e querem garantir que os utilizadores das suas organizações fornecedoras obtenham informações a partir de dados apenas do seu território.  Mas os utilizadores de Contoso podem aceder a todos os dados. Em vez de criar vários relatórios diferentes, o Contoso cria um único relatório e filtra os dados baseados no utilizador que o vê.

![Conteúdo partilhado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Para garantir que o Contoso pode filtrar dados com base em quem está a ligar, são criadas duas funções no ambiente de trabalho Power BI. Um para filtrar todos os dados do SalesTerritory "Europe" e outro para a "América do Norte".

![Gerir funções](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Sempre que as funções forem definidas no relatório, um utilizador deve ser atribuído a uma função específica para que possa ter acesso a quaisquer dados. A atribuição de funções ocorre dentro do serviço Power BI **(Datasets > Security)**

![Definição de segurança](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Isto abre uma página onde a equipa de BI de Contoso pode ver os dois papéis que criaram.  Agora a equipa de BI da Contoso pode atribuir os utilizadores às funções.

![Segurança ao nível da linha](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

No exemplo, a Contoso está a adicionar um utilizador numa organização parceira com endereço de e-mail [adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com) " " ao papel da Europa:

![Definições de segurança ao nível da linha](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Quando isto é resolvido pela Azure AD, Contoso pode ver o nome aparecer na janela pronto para ser adicionado:

![Mostrar papéis](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Agora, quando este utilizador abre a app que foi partilhada com eles, só vêem um relatório com dados da Europa:

![Ver conteúdos](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Segurança dinâmica do nível da linha

Outro tópico interessante é ver como a segurança dinâmica do nível de linha (RLS) funciona com Azure AD B2B.

Em suma, a segurança do nível da linha Dynamic funciona filtrando dados no modelo com base no nome de utilizador da pessoa que se liga ao Power BI. Em vez de adicionar várias funções para grupos de utilizadores, define os utilizadores no modelo. Não descreveremos o padrão em detalhe aqui. Kasper de Jong oferece uma escrita detalhada sobre todos os sabores da segurança de nível de linha na [power BI Desktop Dynamic security cheat sheet](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/), e neste papel [branco](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx) .

Vejamos um pequeno exemplo - Contoso tem um relatório simples sobre vendas por grupos:

![Conteúdo da amostra](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Agora este relatório precisa de ser partilhado com dois utilizadores convidados e um utilizador interno - o utilizador interno pode ver tudo, mas os utilizadores de hóspedes só podem ver os grupos a que têm acesso. Isto significa que devemos filtrar os dados apenas para os utilizadores convidados. Para filtrar os dados de forma adequada, o Contoso utiliza o padrão Dynamic RLS, conforme descrito no whitepaper e no blog post. Isto significa que, Contoso adiciona os nomes de utilizador aos dados em si:

![Ver utilizadores RLS para os próprios dados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Em seguida, Contoso cria o modelo de dados certo que filtra os dados adequadamente com as relações certas:

![São apresentados dados adequados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Para filtrar os dados automaticamente com base em quem está registado, o Contoso precisa de criar uma função que passe no utilizador que está a ligar. Neste caso, a Contoso cria duas funções – a primeira é a "segurança" que filtra a tabela Utilizadores com o nome de utilizador atual do utilizador iniciado no Power BI (isto funciona mesmo para os utilizadores convidados Azure AD B2B).

![Gerir funções](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso também cria outro "AllRole" para os seus utilizadores internos que podem ver tudo – este papel não tem qualquer predicado de segurança.

Depois de carregar o ficheiro de desktop Power BI para o serviço, o Contoso pode atribuir utilizadores convidados ao "SecurityRole" e aos utilizadores internos para o "AllRole"

Agora, quando os utilizadores convidados abrem o relatório, só vêem vendas do grupo A:

![Apenas do grupo A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

Na matriz à direita pode ver o resultado da função USERNAME () e USERPRINCIPALNAME() ambos devolvem o endereço de e-mail dos utilizadores convidados.

Agora o utilizador interno pode ver todos os dados:

![Todos os dados mostrados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Como pode ver, o Dynamic RLS trabalha com utilizadores internos ou convidados.

> [!NOTE]
> Este cenário também funciona quando se utiliza um modelo nos Serviços de Análise Azure. Normalmente, o seu Serviço de Análise Azure está ligado ao mesmo AD AZure que o seu Power BI - nesse caso, a Azure Analysis Services também conhece os utilizadores convidados através do Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Ligação a fontes de dados das instalações

O Power BI oferece a capacidade de o Contoso alavancar fontes de dados no local, como [os SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) ou o [SQL Server,](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) diretamente graças ao [gateway de dados on-in.](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/) É até possível subscrever essas fontes de dados com as mesmas credenciais utilizadas com o Power BI.

> [!NOTE]
> Ao instalar uma porta de entrada para ligar ao seu inquilino Power BI, deve utilizar um utilizador criado dentro do seu inquilino. Os utilizadores externos não podem instalar um portal e conectá-lo ao seu tenant._

Para os utilizadores externos, isto pode ser mais complicado, uma vez que os utilizadores externos normalmente não são conhecidos da AD no local. O Power BI oferece uma solução alternativa para isso, permitindo aos administradores da Contoso mapear os nomes de utilizadores externos para nomes de utilizadores internos, conforme descrito na [Gestão da sua fonte de dados - Serviços de Análise](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Por exemplo, [lucy@supplier1.com](mailto:lucy@supplier1.com) pode ser mapeado para [Lucy \_ Supplier1 \_ com# EXT@contoso.com ](mailto:lucy_supplier1_com).

![Mapeamento de nomes de utilizadores](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Este método é bom se o Contoso tiver apenas um punhado de utilizadores ou se o Contoso conseguir mapear todos os utilizadores externos para uma única conta interna. Para cenários mais complexos onde cada utilizador precisa das suas próprias credenciais, existe uma abordagem mais avançada que utiliza [atributos de AD personalizados](/previous-versions/windows/it-pro/windows-2000-server/cc961737(v=technet.10)) para fazer o mapeamento como descrito na [Gerir a sua fonte de dados - Serviços de Análise](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Isto permitiria ao administrador da Contoso definir um mapeamento para cada utilizador no seu AD Azure (também utilizadores externos de B2B).  Estes atributos podem ser definidos através do modelo de objeto AD usando scripts ou código para que Contoso possa automatizar totalmente o mapeamento no convite ou numa cadência programada.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Permitir que utilizadores externos editem e gerem conteúdos dentro do Power BI

A Contoso pode permitir que os utilizadores externos contribuam com conteúdos dentro da organização, conforme descrito anteriormente na edição e gestão de conteúdos power bi.

> [!NOTE]
> Para editar e gerir conteúdos dentro do Power BI da sua organização, o utilizador deve ter uma licença Power BI Pro num espaço de trabalho diferente do meu espaço de trabalho. Os utilizadores podem obter licenças Pro conforme abrangida pela secção de _Licenciamento_ deste documento.

O Portal Power BI Admin fornece o **permitir que utilizadores convidados externos editem e gerem conteúdos na configuração da organização** nas definições de Inquilino. Por predefinição, a definição é definida para desativada, o que significa que os utilizadores externos obtêm uma experiência de leitura limitada apenas por padrão. A definição aplica-se aos utilizadores com UserType definido para Guest in AZure AD. A tabela abaixo descreve os comportamentos que os utilizadores experimentam dependendo do seu UserType e como as definições são configuradas.

| **Tipo de utilizador em Azure AD** | **Permitir que utilizadores externos de hóspedes editem e gerem a definição de conteúdo** | **Comportamento** |
| --- | --- | --- |
| Convidado | Desativado para o utilizador (Predefinição) | Por ponto de consumo apenas vista. Permite o acesso apenas à leitura de relatórios, dashboards e aplicações quando visualizado através de um URL enviado ao utilizador convidado. As aplicações Power BI Mobile fornecem uma vista apenas de leitura para o utilizador convidado. |
| Convidado | Ativado para o utilizador | O utilizador externo tem acesso a toda a experiência Power BI, embora algumas funcionalidades não estejam disponíveis para eles. O utilizador externo deve iniciar sessão no Power BI utilizando o URL de serviço power BI com as informações do inquilino incluídas. O utilizador obtém a experiência Home, um My Workspace, e com base em permissões podem navegar, visualizar e criar conteúdo. </br></br> As aplicações Power BI Mobile fornecem uma vista apenas de leitura para o utilizador convidado. |

> [!NOTE]
> Os utilizadores externos em Azure AD também podem ser definidos para Membro do UserType. Isto não é atualmente suportado no Power BI.

No portal Power BI Admin, a definição é mostrada na imagem seguinte.

![Definições de administrador](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Os utilizadores convidados obtêm a experiência padrão apenas de leitura e que podem editar e gerir conteúdos. O padrão é desativado, o que significa que todos os utilizadores de Hóspedes têm a experiência apenas de leitura. O Power BI Admin pode ativar a definição para todos os utilizadores convidados na organização ou para grupos de segurança específicos definidos em Azure AD. Na imagem seguinte, o Contoso Power BI Admin criou um grupo de segurança em Azure AD para gerir quais os utilizadores externos que podem editar e gerir conteúdos no inquilino contoso.

Para ajudar estes utilizadores a iniciar sessão no Power BI, forneça-lhes o URL do inquilino. Para encontrar o URL de inquilino, siga estes passos:

1. No serviço Power BI, no menu superior, selecione ajuda ( **?** ), em  **seguida, Sobre o Power BI**.
2. Procure o valor ao lado **do URL do inquilino.** Este é o URL do inquilino que pode partilhar com os seus utilizadores convidados.

    ![URL de Inquilino](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Ao utilizar o Allow external guest para editar e gerir conteúdos na organização, os utilizadores convidados especificados têm acesso ao Power BI da sua organização e vêem qualquer conteúdo ao qual tenham permissão. Podem aceder ao Home, navegar e contribuir com conteúdo para espaços de trabalho, instalar aplicações onde estão na lista de acesso e ter um Espaço de Trabalho My. Podem criar ou ter o cargo de Administrador de áreas de trabalho que utilizem a nova experiência de área de trabalho.

> [!NOTE]
> Ao utilizar esta opção, certifique-se de rever a secção de governação deste documento uma vez que as definições padrão de AD do Azure impedem os utilizadores de Escolher certas funcionalidades, como pickers de pessoas, o que pode levar a uma experiência reduzida.**

Para os utilizadores convidados habilitados através do Allow external guest para editar e gerir conteúdos na configuração do inquilino da organização, algumas experiências não estão disponíveis para eles. Para atualizar ou publicar relatórios, os utilizadores convidados precisam de utilizar o UI do serviço Power BI, incluindo obter dados para carregar ficheiros power BI desktop. As seguintes experiências não são suportadas:

- A publicação direta do Power BI Desktop para o serviço Power BI
- Os utilizadores convidados não podem utilizar o Power BI Desktop para ligar a conjuntos de dados de serviço no serviço Power BI
- Espaços de trabalho clássicos ligados a Grupos Microsoft 365: O utilizador convidado não pode criar ou ser Administrador destes espaços de trabalho. No entanto, pode ser membro.
- O envio de convites ad-hoc não é suportado para listas de acesso de áreas de trabalho
- O Power BI Publisher para Excel não é suportado para utilizadores convidados
- Os utilizadores convidados não podem instalar o Power BI Gateway e ligá-lo à sua organização
- Os utilizadores convidados não podem instalar aplicações de publicações para toda a organização
- Os utilizadores convidados não podem utilizar, criar, atualizar ou instalar pacotes de conteúdos organizacionais
- Os utilizadores convidados não podem utilizar a funcionalidade Analisar no Excel
- Os utilizadores convidados não podem estar @mentioned em comentários (esta funcionalidade será adicionada numa próxima versão)
- Os utilizadores convidados não podem utilizar subscrições (esta funcionalidade será adicionada numa próxima versão)
- Os utilizadores convidados que utilizem esta funcionalidade devem ter uma conta escolar ou profissional. Os utilizadores convidados que usam contas pessoais experimentam mais limitações devido a restrições de inscrição.



## <a name="governance"></a>Governação

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Definições adicionais de AD Azure que afetam experiências no Power BI relacionadas com Azure AD B2B

Ao utilizar a partilha Azure AD B2B, o administrador do Azure Ative Directory controla aspetos da experiência do utilizador externo. Estes são controlados na página de definições de colaboração externa dentro das definições do Diretório Ativo Azure para o seu Inquilino.

Os detalhes sobre as definições estão disponíveis aqui:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Por padrão, as permissões dos utilizadores do Guest são uma opção limitada é definida como Sim, pelo que os utilizadores convidados dentro do Power BI têm experiências limitadas, especialmente partilhas surround onde as UIs picker de pessoas não funcionam para esses utilizadores. É importante trabalhar com o seu administrador AD Azure para defini-lo para Nº, como mostrado abaixo para garantir uma boa experiência.**

![Definições de colaboração externa](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Convites de convidados de controlo

Os administradores do Power BI podem controlar a partilha externa apenas para o Power BI visitando o portal de administração Power BI. Mas os administradores de inquilinos também podem controlar a partilha externa com várias políticas de AD Azure.  Estas políticas permitem que os administradores de inquilinos

- Desligue os convites pelos utilizadores finais
- Só os administradores e utilizadores no papel de Convidado convidado podem convidar
- Administradores, o papel de Convidado Convidado, e membros podem convidar
- Todos os utilizadores, incluindo convidados, podem convidar

Pode ler mais sobre estas políticas em [convites delegados para a colaboração do Azure Ative Directory B2B](/azure/active-directory/active-directory-b2b-delegate-invitations).

Todas as ações do Power BI por utilizadores externos também são [auditadas no nosso portal de auditoria.](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)

### <a name="conditional-access-policies-for-guest-users"></a>Políticas de acesso condicional para utilizadores convidados

A Contoso pode impor políticas de acesso condicional aos utilizadores convidados que acedam ao conteúdo do arrendatário do Contoso. Pode encontrar instruções detalhadas no [acesso condicional para utilizadores de colaboração B2B.](/azure/active-directory/active-directory-b2b-mfa-instructions)

## <a name="common-alternative-approaches"></a>Abordagens alternativas comuns

Embora o Azure AD B2B facilite a partilha de dados e relatórios entre organizações, existem várias outras abordagens que são comumente usadas e podem ser superiores em certos casos.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Opção Alternativa 1: Criar identidades duplicadas para utilizadores parceiros

Com esta opção, a Contoso teve de criar manualmente identidades duplicadas para cada utilizador parceiro no Inquilino Contoso, como mostra a imagem seguinte. Em seguida, dentro do Power BI, Contoso pode partilhar às identidades atribuídas os relatórios, dashboards ou apps apropriados.

![Definição de mapeamentos e nomes apropriados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Razões para escolher esta alternativa:

- Uma vez que a identidade do utilizador é controlada pela sua organização, qualquer serviço relacionado, como e-mail, SharePoint, etc. também está sob o controlo da sua organização. Os seus Administradores de TI podem redefinir palavras-passe, desativar o acesso a contas ou atividades de auditoria nestes serviços.
- Os utilizadores que utilizam contas pessoais para o seu negócio muitas vezes estão impedidos de aceder a determinados serviços, pelo que podem necessitar de uma conta organizacional.
- Alguns serviços apenas funcionam sobre os utilizadores da sua organização. Por exemplo, a utilização do Intune para gerir conteúdos nos dispositivos pessoais/móveis de utilizadores externos que utilizam o Azure B2B pode não ser possível.

Razões para não escolher esta alternativa:

- Os utilizadores de organizações parceiras devem lembrar-se de dois conjuntos de credenciais: um para aceder a conteúdos da sua própria organização e o outro para aceder a conteúdos a partir de Contoso. Este é um problema para estes utilizadores convidados e muitos utilizadores convidados estão confusos com esta experiência.
- A Contoso deve adquirir e atribuir licenças por utilizador a estes utilizadores. Se um utilizador precisar de receber e-mails ou usar aplicações de escritório, precisa das licenças apropriadas, incluindo o Power BI Pro para editar e partilhar conteúdos no Power BI.
- A Contoso pode querer impor políticas de autorização e governação mais rigorosas para os utilizadores externos em comparação com os utilizadores internos. Para isso, a Contoso precisa de criar uma nomenclatura interna para utilizadores externos e todos os utilizadores do Contoso precisam de ser educados sobre esta nomenclatura.
- Quando o utilizador deixa a sua organização, continuam a ter acesso aos recursos de Contoso até que o administrador Contoso apague manualmente a sua conta.
- Os administradores do Contoso têm de gerir a identidade do hóspede, incluindo a criação, resets de password, etc.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Opção Alternativa 2: Criar uma aplicação personalizada Power BI Incorporada usando a autenticação personalizada

Outra opção para a Contoso é construir a sua própria aplicação power bi personalizada com autenticação personalizada[('App detém dados').](../developer/embedded/embed-sample-for-customers.md) Embora muitas organizações não tenham tempo ou recursos para criar uma aplicação personalizada para distribuir conteúdo do Power BI aos seus parceiros externos, para algumas organizações esta é a melhor abordagem e merece séria consideração.

Muitas vezes, as organizações têm portais parceiros existentes que centralizam o acesso a todos os recursos organizacionais para parceiros, proporcionam isolamento dos recursos organizacionais internos e proporcionam experiências simplificadas para os parceiros apoiarem muitos parceiros e seus utilizadores individuais.

![Muitos portais de parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

No exemplo acima, os utilizadores de cada fornecedor iniciam login no Portal de Parceiros da Contoso que utiliza a AAD como fornecedor de identidade. Poderia utilizar AAD B2B, Azure B2C, identidades nativas ou federados com qualquer número de outros fornecedores de identidade. O utilizador entraria e acederia a um portal de parceiros usando a Azure Web App ou uma infraestrutura semelhante.

Dentro da aplicação web, os relatórios Power BI são incorporados a partir de uma implementação embutida em Power BI. A aplicação web simplificaria o acesso aos relatórios e a quaisquer serviços relacionados numa experiência coesa destinada a facilitar a interação dos fornecedores com a Contoso. Este ambiente de portal seria isolado do ambiente interno da AAD e do Contoso para garantir que os fornecedores não pudessem aceder a esses recursos. Normalmente, os dados seriam armazenados num armazém de dados separado do Parceiro para garantir o isolamento dos dados também. Este isolamento tem benefícios, uma vez que limita o número de utilizadores externos com acesso direto aos dados da sua organização, limitando quais os dados que poderiam estar potencialmente disponíveis para o utilizador externo, e limitando a partilha acidental com utilizadores externos.

Utilizando o Power BI Embedded, o portal pode aproveitar o licenciamento vantajoso, utilizando o token da app ou o principal utilizador mais a capacidade premium adquirida no modelo Azure, o que simplifica as preocupações com a atribuição de licenças aos utilizadores finais, e pode escalar para cima/para baixo com base no uso esperado. O portal pode oferecer uma experiência global de maior qualidade e consistente, uma vez que os parceiros acedem a um único portal projetado com todas as necessidades de um Parceiro em mente. Por último, uma vez que as soluções baseadas em forma de Power BI são tipicamente concebidas para serem multi-arrendantes, torna-se mais fácil garantir o isolamento entre organizações parceiras.

Razões para escolher esta alternativa:

- Mais fácil de gerir à medida que o número de organizações parceiras cresce. Uma vez que os parceiros são adicionados a um diretório separado isolado do diretório interno da Contoso, simplifica os deveres de governação da TI e ajuda a prevenir a partilha acidental de dados internos a utilizadores externos.
- Os Típicos Portais de Parceiros são experiências altamente marcadas com experiências consistentes entre parceiros e simplificadas para atender às necessidades dos parceiros típicos. A Contoso pode, portanto, oferecer uma melhor experiência global aos parceiros, integrando todos os serviços necessários num único portal.
- Os custos de licenciamento para cenários avançados como o conteúdo de Edição dentro do Power BI Embedded são cobertos pelo Azure adquirido Power BI Premium, e não requer atribuição de licenças Power BI Pro a esses utilizadores.
- Proporciona um melhor isolamento entre os parceiros se fordotado como uma solução multi-inquilino.
- O Portal do Parceiro inclui frequentemente outras ferramentas para parceiros além de relatórios de Power BI, dashboards e apps.

Razões para não escolher esta alternativa:

- É necessário um esforço significativo para construir, operar e manter tal portal, tornando-o um investimento significativo em recursos e tempo.
- O tempo para a solução é muito mais longo do que a utilização da partilha B2B, uma vez que é necessário um planeamento e execução cuidadosos em vários fluxos de trabalho.
- Quando há um número menor de parceiros, o esforço necessário para esta alternativa é provavelmente demasiado elevado para justificar.
- A colaboração com a partilha ad-hoc é o cenário principal enfrentado pela sua organização.
- Os relatórios e os dashboards são diferentes para cada parceiro. Esta alternativa introduz a gestão para além de apenas partilhar diretamente com os Parceiros.



## <a name="faq"></a>FAQ

**O Contoso pode enviar um convite que é automaticamente resgatado, para que o utilizador esteja apenas "pronto para ir"? Ou o utilizador tem sempre de clicar no URL de redenção?**

O utilizador final deve clicar sempre na experiência de consentimento antes de poder aceder ao conteúdo.

Se convidar muitos utilizadores convidados, recomendamos que o delegue a partir dos seus administradores AD Azure, [adicionando um utilizador ao papel de convidado convidado na organização de recursos.](/azure/active-directory/active-directory-b2b-add-guest-to-role) Este utilizador pode convidar outros utilizadores na organização do parceiro utilizando os scripts UI, PowerShell ou APIs de inscrição. Isto reduz os encargos administrativos dos seus administradores Azure AD para convidar ou ressentir-se dos convites aos utilizadores da organização parceira.

**A Contoso pode forçar a autenticação multi-factor para os utilizadores convidados se os seus parceiros não tiverem autenticação multi-factor?**

Sim. Para obter mais informações, consulte [o acesso condicional aos utilizadores da colaboração B2B.](/azure/active-directory/active-directory-b2b-mfa-instructions)

**Como funciona a colaboração B2B quando o parceiro convidado está a usar a federação para adicionar a sua própria autenticação no local?**

Se o parceiro tiver um inquilino AD Azure que é federado para a infraestrutura de autenticação no local, no local é automaticamente alcançado um único sign-on (SSO). Se o parceiro não tiver um inquilino AZure AD, pode ser criada uma conta Azure AD para novos utilizadores.

**Posso convidar utilizadores convidados com contas de e-mail de consumo?**

Convidar utilizadores convidados com contas de e-mail de consumo é suportado no Power BI. Isto inclui domínios como hotmail.com, outlook.com e gmail.com. No entanto, estes utilizadores podem experimentar limitações para além do que os utilizadores com contas de trabalho ou escola encontram.