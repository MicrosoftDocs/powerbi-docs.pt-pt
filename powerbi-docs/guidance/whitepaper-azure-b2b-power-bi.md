---
title: Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure Active Directory B2B
description: Whitepaper que descreve como usar o Diretório Ativo Azure B2B para distribuir Power BI a utilizadores externos
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 7ab103c5d7b568e7315f67193da4d8da25b77a6c
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565443"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure Active Directory B2B

**Resumo:** Trata-se de um livro branco técnico que descreve como distribuir conteúdos a utilizadores fora da organização utilizando a integração do Azure Ative Directory Business-to-Business (Azure AD B2B).

**Escritores:** Lukasz Pawlowski

**Revisores Técnicos:** Adam Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Maya Shenhav, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> Pode guardar ou imprimir este livro branco selecionando **Imprimir** do seu navegador e, em seguida, selecionando **Guardar como PDF**.

## <a name="introduction"></a>Introdução

O Power BI dá às organizações uma visão de 360 graus do seu negócio e capacita todos nestas organizações a tomarem decisões inteligentes usando dados. Muitas destas organizações têm relações fortes e de confiança com parceiros externos, clientes e empreiteiros. Estas organizações precisam de fornecer acesso seguro aos dashboards e relatórios do Power BI aos utilizadores destes parceiros externos.

O Power BI integra-se com o [Azure Ative Directory Business-to-Business (Azure AD B2B)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) para permitir a distribuição segura de conteúdos power BI aos utilizadores convidados fora da organização – mantendo ainda o controlo e regulando o acesso aos dados internos.

Este livro branco cobre todos os detalhes necessários para compreender a integração do Power BI com o Azure Ative Directory B2B. Cobrimos o seu caso de uso mais comum, configuração, licenciamento e segurança ao nível da linha.

> [!NOTE]
> Ao longo deste livro branco, referimo-nos ao Azure Ative Directory como Azure AD e Azure Ative Directory Business para Negócios como Azure AD B2B.

## <a name="scenarios"></a>Cenários

A Contoso é um fabricante automóvel e trabalha com muitos fornecedores diversos que lhe fornecem todos os componentes, materiais e serviços necessários para executar as suas operações de fabrico. A Contoso quer dinamizar a sua logística da cadeia de fornecimento e planeia utilizar o Power BI para monitorizar as principais métricas de desempenho da sua cadeia de fornecimento. Contoso quer partilhar com parceiros de cadeia de fornecimento externos aanálise de forma segura e manejável.

A Contoso pode permitir as seguintes experiências para utilizadores externos utilizando o Power BI e o Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc por partilha de item

Contoso trabalha com um fornecedor que constrói radiadores para os carros de Contoso. Muitas vezes, precisam de otimizar a fiabilidade dos radiadores utilizando dados de todos os carros de Contoso. Um analista da Contoso usa o Power BI para partilhar um relatório de fiabilidade do radiador com um Engenheiro no fornecedor. O Engenheiro recebe um e-mail com um link para ver o relatório.

Como acima descrito, esta partilha ad-hoc é realizada pelos utilizadores empresariais de forma necessária. O link enviado pelo Power BI para o utilizador externo é um link de convite Azure AD B2B. Quando o utilizador externo abre o link, é-lhes pedido que se juntem à organização Azure AD da Contoso como utilizador convidado. Após a aceitação do convite, o link abre o relatório ou painel específico. O administrador do Azure Ative Directory delega a permissão para convidar utilizadores externos para a organização e escolhe o que esses utilizadores podem fazer quando aceitarem o convite descrito na secção de Governação deste documento. O analista da Contoso só pode convidar o utilizador convidado porque o administrador da AD Azure permitiu essa ação e o administrador do Power BI permitiu que os utilizadores convidassem os hóspedes a visualizar conteúdos nas definições de inquilinos do Power BI.

![Convide os hóspedes para o Power BI usando a AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. O processo começa com um utilizador interno da Contoso a partilhar um dashboard ou um relatório com um utilizador externo. Se o utilizador externo já não for hóspede no Azure AD de Contoso, são convidados. Um e-mail é enviado para o seu endereço de e-mail que inclui um convite para a AD Azure de Contoso
2. O destinatário aceita o convite para o Azure AD de Contoso e é adicionado como utilizador convidado no Azure AD de Contoso.
3. O destinatário é então redirecionado para o painel de instrumentos, relatório ou aplicação power BI, que são apenas para o utilizador.

O processo é considerado ad-hoc uma vez que os utilizadores empresariais em Contoso realizam a ação de convite conforme necessário para os seus fins comerciais. Cada item partilhado é uma única ligação que o utilizador externo pode aceder para visualizar o conteúdo.

Uma vez que o utilizador externo tenha sido convidado a aceder aos recursos da Contoso, poderá ser criada uma conta-sombra para eles em Contoso Azure AD e não precisam de ser novamente convidados.  A primeira vez que tentam aceder a um recurso contoso como um painel power bi, passam por um processo de consentimento, que redime o convite.  Se não completarem o consentimento, não podem aceder a nenhum dos conteúdos de Contoso.  Se tiverem dificuldade em resgatar o seu convite através do link original fornecido, um administrador da AD Azure pode ressentir-se de um link de convite específico para eles resgatarem.

### <a name="planned-per-item-sharing"></a>Planejada por partilha de itens

Contoso trabalha com um subempreiteiro para realizar análises de fiabilidade dos radiadores. O subempreiteiro tem uma equipa de 10 pessoas que precisam de acesso a dados no ambiente Power BI de Contoso. O administrador da AD Contoso Azure está envolvido em convidar todos os utilizadores e lidar com quaisquer adições/alterações como pessoal na alteração do subcontratante. O administrador da AD Azure cria um grupo de segurança para todos os funcionários do subempreiteiro. Utilizando o grupo de segurança, os colaboradores da Contoso podem facilmente gerir o acesso aos relatórios e garantir que todo o pessoal subcontratado necessário tenha acesso a todos os relatórios, dashboards e aplicações Power BI necessários. O administrador da AD Azure também pode evitar estar envolvido no processo de convite, optando por delegar direitos de convite a um funcionário de confiança na Contoso ou no subempreiteiro para garantir a gestão atempada do pessoal.

Algumas organizações exigem mais controlo sobre quando os utilizadores externos são adicionados, estão a convidar muitos utilizadores numa organização externa, ou muitas organizações externas. Nestes casos, a partilha planeada pode ser usada para gerir a escala da partilha, para impor políticas organizacionais e até para delegar direitos a indivíduos de confiança para convidar e gerir utilizadores externos. O Azure AD B2B suporta convites planeados para serem enviados diretamente [do portal Azure por um administrador](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)de TI , ou através da PowerShell utilizando o gestor de [convites API](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) onde um conjunto de utilizadores pode ser convidado numa ação. Utilizando a abordagem de convites planeada, a organização pode controlar quem pode convidar os utilizadores e implementar processos de aprovação. Capacidades avançadas de AD Azure, como grupos dinâmicos, podem facilitar a manutenção automática da adesão ao grupo de segurança.


![Controlo que os hóspedes podem ver conteúdo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. O processo é protagonizado por um administrador de TI convidando o utilizador convidado manualmente ou através da API fornecida pelo Azure Ative Directory
2. O utilizador aceita o convite para a organização.
3. Uma vez que o utilizador tenha aceitado o convite, um utilizador no Power BI pode partilhar um relatório ou painel com o utilizador externo, ou um grupo de segurança em que se encontram. Tal como com a partilha regular no Power BI, o utilizador externo recebe um e-mail com o link para o item.
4. Quando o utilizador externo acede ao link, a sua autenticação no seu diretório é passada para o Azure AD de Contoso e utilizada para aceder ao conteúdo do Power BI.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Partilha ad hoc ou planeada de Aplicações Power BI

A Contoso tem um conjunto de relatórios e dashboards que precisam de partilhar com um ou mais Fornecedores. Para garantir que todos os utilizadores externos necessários tenham acesso a este conteúdo, este é embalado como uma aplicação Power BI. Os utilizadores externos são adicionados diretamente à lista de acesso à aplicação ou através de grupos de segurança. Alguém na Contoso envia então o URL da aplicação a todos os utilizadores externos, por exemplo, num e-mail. Quando os utilizadores externos abrem o link, vêem todo o conteúdo numa única experiência fácil de navegar.

A utilização de uma aplicação Power BI facilita a construção de um Portal BI para os seus fornecedores. Uma única lista de acesso controla o acesso a todos os conteúdos necessários, reduzindo a verificação de tempo desperdiçado e definindo permissões de nível de item. O Azure AD B2B mantém o acesso à segurança utilizando a identidade nativa do Fornecedor para que os utilizadores não necessitem de credenciais adicionais de login. Se utilizar convites planeados com grupos de segurança, a gestão de acesso à app à medida que o pessoal roda para dentro ou para fora do projeto é simplificada. A adesão em grupos de segurança manualmente ou utilizando [grupos dinâmicos,](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups)para que todos os utilizadores externos de um fornecedor sejam automaticamente adicionados ao grupo de segurança apropriado.


![Controlar conteúdos com AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. O processo começa pelo utilizador a ser convidado para a organização Azure AD da Contoso através do portal Azure ou PowerShell
2. O utilizador pode ser adicionado a um grupo de utilizadores em Azure AD. Um grupo de utilizadores estático ou dinâmico pode ser usado, mas grupos dinâmicos ajudam a reduzir o trabalho manual.
3. Os utilizadores externos têm acesso à Aplicação Power BI através do grupo de utilizadores. O URL da aplicação deve ser enviado diretamente para o utilizador externo ou colocado num site a que tenha acesso. O Power BI faz o melhor esforço para enviar um e-mail com o link da app para utilizadores externos, mas ao utilizar grupos de utilizadores cuja adesão pode mudar, o Power BI não é capaz de enviar a todos os utilizadores externos geridos através de grupos de utilizadores.
4. Quando o utilizador externo acede ao URL da aplicação Power BI, estes são autenticados pela AD Azure de Contoso, a aplicação é instalada para o utilizador, e o utilizador pode ver todos os relatórios e dashboards contidos dentro da app.

As aplicações também têm uma funcionalidade única que permite aos autores de aplicações instalarem a aplicação automaticamente para o utilizador, pelo que esta está disponível quando o utilizador faz login. Esta funcionalidade instala-se apenas automaticamente para utilizadores externos que já fazem parte da organização da Contoso no momento em que a aplicação é publicada ou atualizada. Assim, é melhor utilizado com a abordagem de convites planeados, e depende da aplicação ser publicada ou atualizada após a adição dos utilizadores à AD Azure de Contoso. Os utilizadores externos podem sempre instalar a aplicação utilizando o link da aplicação.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Comentar e subscrever conteúdos entre organizações

À medida que contoso continua a trabalhar com os seus subempreiteiros ou fornecedores, os Engenheiros externos precisam de trabalhar em estreita colaboração com os analistas da Contoso. O Power BI fornece várias funcionalidades de colaboração que ajudam os utilizadores a comunicar sobre conteúdos que podem consumir. O comentário do dashboard (e logo reportar comentários) permite que os utilizadores discutam os pontos de dados que vêem e comuniquem com os autores do relatório para fazerperguntas.

Atualmente, os utilizadores externos podem participar em comentários deixando comentários e lendo as respostas. No entanto, ao contrário dos utilizadores internos, os utilizadores de hóspedes não podem ser e não recebem notificações de @mentioned que receberam um comentário. Os utilizadores convidados não podem utilizar a funcionalidade de subscrições dentro do Power BI no momento da escrita. Numa próxima versão, essas restrições serão levantadas e o utilizador convidado receberá um e-mail quando uma @mentions subscrição for entregue no seu e-mail que contenha um link para o conteúdo em Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Aceder a conteúdos nas aplicações móveis Power BI

Num próximo comunicado, quando os utilizadores de Contoso partilharem relatórios ou dashboards com os seus homólogos externos, o Power BI enviará um e-mail a notificar o Hóspede. Quando o utilizador convidado abrir o link para o relatório ou painel de instrumentos no seu dispositivo móvel, o conteúdo será aberto nas aplicações móveis nativas do Power BI no seu dispositivo, caso estejam instalados. O utilizador convidado poderá então navegar entre conteúdos partilhados com eles no inquilino externo e voltar ao seu próprio conteúdo a partir do seu inquilino.

> [!NOTE]
> O utilizador convidado não pode abrir a aplicação móvel Power BI e navegar imediatamente para o inquilino externo, devendo começar com um link para um item no inquilino externo. As sobras comuns são descritas nos links de distribuição de conteúdos na secção [Power BI da organização-mãe](#distributing-links-to-content-in-the-parent-organizations-power-bi) mais tarde neste documento.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Edição e gestão de conteúdos power bi

A Contoso e os seus Fornecedores e subempreiteiros trabalham cada vez mais em conjunto. Muitas vezes, um analista no subempreiteiro precisa de métricas adicionais ou visualizações de dados para ser adicionado a um relatório que Contoso partilhou com eles. Os dados devem residir no inquilino power bi da Contoso, mas os utilizadores externos devem ser capazes de editá-lo, criar novos conteúdos e até distribuí-lo a indivíduos apropriados.

O Power BI oferece uma opção que permite aos **utilizadores externos poderem editar e gerir conteúdos** na organização. Por padrão, os utilizadores externos têm uma experiência orientada para o consumo apenas para leitura. No entanto, esta nova definição permite ao administrador do Power BI escolher quais os utilizadores externos que podem editar e gerir conteúdos dentro da sua própria organização. Uma vez permitido, o utilizador externo pode editar relatórios, dashboards, publicar ou atualizar aplicações, trabalhar em espaços de trabalho e ligar-se aos dados que têm permissão para usar.

Este cenário é descrito em detalhe na secção Permitindo aos utilizadores externos editar e gerir conteúdos dentro do Power BI mais tarde neste documento.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Relações organizacionais utilizando Power BI e Azure AD B2B

Quando todos os utilizadores do Power BI são internos para a organização, não há necessidade de utilizar o Azure AD B2B. No entanto, uma vez que duas ou mais organizações querem colaborar em dados e insights, o apoio do Power BI ao Azure AD B2B torna-o fácil e rentável para o fazer.

Abaixo estão as estruturas organizacionais tipicamente encontradas que são bem adequadas para a colaboração transversal estilo Azure AD B2B em Power BI. A Azure AD B2B funciona bem na maioria dos casos, mas em algumas situações as abordagens alternativas comuns abrangidas no final deste documento merecem ser consideradas.

### <a name="case-1-direct-collaboration-between-organizations"></a>Caso 1: Colaboração direta entre organizações

A relação de Contoso com o seu fornecedor de radiadores é um exemplo de colaboração direta entre organizações. Uma vez que existem relativamente poucos utilizadores na Contoso e seu fornecedor que precisam de acesso a informações de fiabilidade do radiador, a utilização da partilha externa baseada em Azure AD B2B é ideal. É fácil de usar e simples de administrar. Este é também um padrão comum nos serviços de consultoria onde um consultor pode precisar de construir conteúdo para uma organização.

![Partilhar entre organizações](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Tipicamente, esta partilha ocorre inicialmente usando Ad hoc por partilha de item. No entanto, à medida que as equipas crescem ou as relações se aprofundam, a abordagem planeada por partilha de itens torna-se o método preferido para reduzir a sobrecarga de gestão. Além disso, a partilha ad hoc ou planeada de Aplicações Power BI, comentários e subscrição de conteúdos entre organizações, acesso a conteúdos em aplicações móveis também pode entrar em jogo, e edição e gestão de conteúdos de Power BI. Importante, se os utilizadores de ambas as organizações tiverem licenças Power BI Pro nas respetivas organizações, podem usar essas licenças Pro nos ambientes power bi de cada uma. Isto fornece um licenciamento vantajoso, uma vez que a organização convidativa pode não precisar de pagar uma licença Power BI Pro para os utilizadores externos. Isto é discutido mais detalhadamente na secção de Licenciamento mais tarde neste documento.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Caso 2: A mãe e as suas filiais ou filiais

Algumas estruturas de organização são mais complexas, incluindo subsidiárias parcial ou totalmente detidas, empresas afiliadas ou relações geridas de prestadores de serviços. Estas organizações têm uma organização-mãe, como uma holding, mas as organizações subjacentes operam semi-autónomamente, por vezes sob diferentes requisitos regionais. Isto leva a que cada organização tenha o seu próprio ambiente Azure AD e separe os inquilinos do Power BI.

![Trabalhar com subsidiárias](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


Nesta estrutura, a organização-mãe normalmente precisa de distribuir insights padronizados às suas subsidiárias. Tipicamente, esta partilha ocorre usando a abordagem Ad hoc ou planeada de Power BI Apps, como ilustrado na imagem seguinte, uma vez que permite a distribuição de conteúdo autoritário padronizado para o público alargado. Na prática, é utilizada uma combinação de todos os Cenários mencionados anteriormente neste documento.

![Combinando cenários](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Segue-se o seguinte processo:

1. Os utilizadores de cada Subsidiária são convidados para a AD Azure da Contoso
2. Em seguida, a aplicação Power BI é publicada para dar a estes utilizadores acesso aos dados necessários
3. Finalmente, os utilizadores abrem a app através de um link que lhes foi dado para ver os relatórios

Vários desafios importantes são enfrentados pelas organizações desta estrutura:

- Como distribuir links para conteúdos no Power BI da organização-mãe
- Como permitir que os utilizadores subsidiários acedam à fonte de dados hospedada pela organização-mãe

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribuir links para conteúdos no Power BI da organização-mãe

Três abordagens são comumente usadas para distribuir links para o conteúdo. O primeiro e mais básico é enviar o link para a app para os utilizadores necessários ou colocá-lo num site Do SharePoint Online a partir do qual pode ser aberto. Os utilizadores podem então marcar o link nos seus navegadores para um acesso mais rápido aos dados de que necessitam.

A segunda abordagem baseia-se na edição e gestão de conteúdos power bi. A organização Parent permite que os utilizadores das subsidiárias acedam ao seu Power BI e controlem o que podem aceder através da permissão. Isto dá acesso ao Power BI Home onde o utilizador da subsidiária vê uma lista completa de conteúdos partilhados no inquilino da organização Dos Pais. Em seguida, o URL para o ambiente Power BI das organizações parentais é dado aos utilizadores das subsidiárias.

A abordagem final usa uma aplicação Power BI criada dentro do inquilino Power BI para cada subsidiária. A aplicação Power BI inclui um dashboard com [azulejos configurados com a opção](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink)de ligação externa . Quando o utilizador pressiona o azulejo, são levados para o relatório, painel ou app apropriados no Power BI da organização-mãe. Esta abordagem tem a vantagem adicional de que a aplicação pode ser instalada automaticamente para todos os utilizadores da subsidiária e está disponível para eles sempre que eles iniciarem o seu próprio ambiente Power BI. Uma vantagem adicional desta abordagem é que funciona bem com as aplicações móveis Power BI que podem abrir o link de forma nativa. Também pode combiná-lo com a segunda abordagem para permitir uma troca mais fácil entre ambientes Power BI.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Permitir que os utilizadores subsidiários acedam a fontes de dados hospedadas pela organização-mãe

Muitas vezes, os analistas de uma subsidiária precisam de criar as suas próprias análises utilizando dados fornecidos pela organização-mãe. Neste caso, geralmente, fontes de dados em nuvem são usadas para enfrentar o desafio.

A primeira abordagem aproveita a [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) para construir um armazém de dados de nível empresarial que sirva as necessidades dos Analistas em toda a empresa e suas subsidiárias, como mostra a imagem seguinte. A Contoso pode acolher os dados e utilizar capacidades como segurança ao nível da linha para garantir que os utilizadores de cada subsidiária só podem aceder aos seus dados. Os analistas de cada organização podem aceder ao armazém de dados através do Power BI Desktop e publicar análises resultantes aos respetivos inquilinos do Power BI.

![Como a partilha ocorre com os inquilinos do Power BI](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


A segunda abordagem aproveita a Base de [Dados Azure SQL](https://azure.microsoft.com/services/sql-database/) para construir um armazém de dados relacionais para fornecer acesso aos dados. Isto funciona da mesma forma com a abordagem dos Serviços de Análise Azure, embora algumas capacidades como a segurança ao nível da linha possam ser mais difíceis de implementar e manter entre subsidiárias.

Abordagens mais sofisticadas também são possíveis, no entanto, as acima são, de longe, as mais comuns.

### <a name="case-3-shared-environment-across-partners"></a>Caso 3: Ambiente partilhado entre parceiros

A Contoso pode entrar em parceria com um concorrente para construir conjuntamente um carro numa linha de montagem partilhada, mas para distribuir o veículo sob diferentes marcas ou em diferentes regiões. Isto requer uma ampla colaboração e co-apropriação de dados, inteligência e análise entre organizações. Esta estrutura também é comum no setor de serviços de consultoria onde uma equipa de consultores pode fazer análises baseadas em projetos para um cliente.

![Ambiente compartilhado entre parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



Na prática, estas estruturas são complexas, como mostra a imagem seguinte, e exigem que o pessoal se mantenha. Para ser eficaz, esta estrutura baseia-se na edição e gestão de conteúdos power bi, uma vez que permite que as organizações reutilizem as licenças Power BI Pro adquiridas para os respetivos inquilinos do Power BI.

![Licenças e conteúdos de organização partilhada](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Para estabelecer um inquilino partilhado do Power BI, é necessário criar um Diretório Ativo Azure e pelo menos uma conta de utilizador power BI Pro precisa de ser adquirida para um utilizador nesse diretório ativo. Este utilizador convida os utilizadores necessários para a organização partilhada. Importante, neste cenário, os utilizadores de Contoso são tratados como utilizadores externos quando operam dentro do Power BI da Organização Partilhada.

O processo é o seguinte:

1. A Organização Partilhada é estabelecida como um novo Diretório Ativo Azure e pelo menos uma conta de utilizador é criada na nova organização. Esse utilizador deve ter uma licença Power BI Pro atribuída a eles.
2. Este utilizador estabelece então um inquilino Power BI e convida os utilizadores necessários da Contoso e da organização Partner. O utilizador também estabelece quaisquer ativos de dados partilhados como o Azure Analysis Services. Os contoso e os utilizadores do Partner podem aceder ao Power BI da organização partilhada como utilizadores convidados. Se for permitido editar e gerir conteúdos no Power BI, os utilizadores externos podem utilizar o Power BI em casa, usar espaços de trabalho, carregar ou editar conteúdos e partilhar relatórios. Normalmente, todos os ativos partilhados são armazenados e acedidos a partir da organização partilhada.
3. Dependendo da forma como as partes concordam em colaborar, é possível que cada organização desenvolva os seus próprios dados e análises usando ativos de armazém de dados partilhados. Podem distribuí-los aos respetivos utilizadores internos utilizando os seus inquilinos internos do Power BI.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Caso 4: Distribuição a centenas ou milhares de parceiros externos

Enquanto Contoso criou um relatório de fiabilidade do radiador para um fornecedor, agora Contoso deseja criar um conjunto de relatórios padronizados para centenas de Fornecedores. Isto permite que a Contoso garanta que todos os fornecedores tenham a análise de que necessitam para fazer melhorias ou corrigir defeitos de fabrico.

![Distribuição a muitos parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Quando uma organização precisa de distribuir dados e insights padronizados a muitos utilizadores/organizações externos, eles podem usar o cenário de Ad hoc ou a partilha planeada de Aplicações Power BI para construir um Portal BI rapidamente e sem custos de desenvolvimento extensivos. O processo de construção de tal portal utilizando uma aplicação Power BI está coberto no Case Study: Building a BI Portal utilizando instruções Power BI + Azure AD B2B – Step-by-Step mais tarde neste documento.

Uma variante comum deste caso é quando uma organização está a tentar partilhar insights com os consumidores, especialmente quando procura utilizar o Azure B2C com o Power BI. O Power BI não suporta de forma nativa o Azure B2C. Se estiver a avaliar as opções para este caso, considere utilizar a Alternativa Option 2 na alternativa comum aproxima-se da secção mais tarde neste documento.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Estudo de Caso: Construção de um Portal BI utilizando instruções power BI + Azure AD B2B – Step-by-Step

A integração do Power BI com o Azure AD B2B dá ao Contoso uma forma perfeita e sem aborrecimentos para proporcionar aos utilizadores convidados um acesso seguro ao seu portal BI. Contoso pode configurar isto com três passos:

![Construção de um portal](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Criar portal do BI no Power BI

    A primeira tarefa para Contoso é criar o seu portal BI em Power BI. O portal BI da Contoso será composto por uma coleção de dashboards construídos de propósito e relatórios que serão disponibilizados a muitos utilizadores internos e convidados. A forma recomendada de o fazer no Power BI é construir uma aplicação Power BI. Saiba mais sobre [aplicações no Power BI.](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/)

- Equipa bi de Contoso cria espaço de trabalho no Power BI

    ![área de trabalho](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Outros autores são adicionados ao espaço de trabalho

    ![Adicionar autores](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- O conteúdo é criado dentro do espaço de trabalho

    ![Criar conteúdo dentro do espaço de trabalho](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Agora que o conteúdo é criado num espaço de trabalho, a Contoso está pronta para convidar utilizadores convidados em organizações parceiras a consumir em este conteúdo.

2. Convidar Utilizadores

    Existem duas formas de o Contoso convidar os utilizadores convidados para o seu portal BI no Power BI:

    * Convites Planeados
    * Convites ad hoc

    **Convites Planeados**

    Nesta abordagem, a Contoso convida os utilizadores convidados para o seu Azure AD com antecedência e depois distribui-lhes conteúdo power BI. A Contoso pode convidar utilizadores convidados do portal Azure ou utilizar o PowerShell. Aqui estão os passos para convidar os utilizadores convidados do portal Azure:

    - Administrador da AD Azure da Contoso navega para **o portal Azure > Diretório Ativo do Azure > Utilizadores e grupos > Todos os utilizadores > Novo utilizador convidado**

    ![Utilizador convidado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Adicione uma mensagem de convite para os utilizadores convidados e clique em Convidar

    ![Adicionar convite](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Para convidar utilizadores convidados do portal Azure, você precisa de um administrador para o Diretório Ativo Azure do seu inquilino.

    Se Contoso quer convidar muitos utilizadores convidados, eles podem fazê-lo usando powerShell. O administrador da AD Azure da Contoso armazena os endereços de e-mail de todos os utilizadores convidados num ficheiro CSV. Aqui estão o código de [colaboração Azure Ative Directory B2B e amostras](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) e instruções powerShell.

    Após o convite, os utilizadores convidados recebem um e-mail com o link de convite.

    ![Link de convite](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Assim que os utilizadores de hóspedes clicarem no link, podem aceder a conteúdos no inquilino da AD Contoso Azure.

    > [!NOTE]
    > É possível alterar o layout do e-mail de convite utilizando a funcionalidade de marca Azure AD como descrito [aqui](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Convites ad hoc**

    E se contoso não conhecer todos os utilizadores convidados que quer convidar com antecedência? Ou, e se o analista em Contoso que criou o portal BI quiser distribuir conteúdo aos próprios utilizadores convidados? Também apoiamos este cenário no Power BI com convites ad-hoc.

    O analista pode apenas adicionar os utilizadores externos à lista de acesso da app quando a publicarem. Os utilizadores convidados recebem um convite e uma vez que o aceitam, são automaticamente redirecionados para o conteúdo do Power BI.

    ![Adicionar utilizador externo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Os convites são necessários apenas na primeira vez que um utilizador externo é convidado para a sua organização.


3. Distribuir Conteúdo

    Agora que a equipa bi da Contoso criou o portal BI e convidou os utilizadores convidados, podem distribuir o seu portal aos seus utilizadores finais, dando aos utilizadores convidados acesso à app e publicando-a. O Power BI completa automaticamente os nomes dos utilizadores convidados que foram previamente adicionados ao inquilino de Contoso. Neste momento, os convites adhoc para outros utilizadores convidados também podem ser adicionados.

    > [!NOTE]
    > Se utilizar grupos de Segurança para gerir o acesso à aplicação para utilizadores externos, utilize a abordagem "Convites Planeados" e partilhe a ligação da aplicação diretamente com cada utilizador externo que tenha de aceder à sua aplicação. Caso contrário, o utilizador externo pode não ser capaz de instalar ou visualizar conteúdos a partir da aplicação._

    Os utilizadores convidados recebem um e-mail com um link para a aplicação.

    ![Link de convite por e-mail](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Ao clicar neste link, os utilizadores convidados são convidados a autenticar com a identidade da sua própria organização.

    ![Página de início de sessão](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Uma vez autenticados com sucesso, são redirecionados para a aplicação BI de Contoso.

    ![Ver conteúdo partilhado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Posteriormente, os utilizadores podem chegar à aplicação de Contoso clicando no link no e-mail ou marcando o link. A Contoso também pode facilitar aos utilizadores convidados adicionando este link a qualquer portal extranet existente que os utilizadores convidados já utilizam.

4. Próximos passos

    Utilizando uma aplicação Power BI e Azure AD B2B, a Contoso conseguiu rapidamente criar um Portal BI para os seus fornecedores de forma sem código. Esta distribuição muito simplificada de análises padronizadas a todos os fornecedores que dela necessitassem.

    Embora o exemplo mostrasse como um único relatório comum poderia ser distribuído entre fornecedores, o Power BI pode ir muito mais longe. Para garantir que cada parceiro só vê dados relevantes para si mesmos, a Segurança de Nível de Linha pode ser adicionada facilmente ao relatório e ao modelo de dados. A secção de segurança de dados para parceiros externos mais tarde neste documento descreve este processo em detalhes.

    Muitas vezes, relatórios individuais e dashboards precisam de ser incorporados num portal existente. Isto também pode ser realizado reutilizando muitas das técnicas mostradas no exemplo. No entanto, nestas situações, pode ser mais fácil incorporar relatórios ou tabliers diretamente de um espaço de trabalho. O processo de convite e atribuição de permissão de segurança aos utilizadores necessários permanece o mesmo.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Sob o capuz: Como é que a Lucy do Supplier1 consegue aceder ao conteúdo do Power BI do inquilino de Contoso?

Agora que vimos como o Contoso é capaz de distribuir sem problemas os conteúdos do Power BI aos utilizadores convidados em organizações parceiras, vamos ver como isto funciona sob o capot.

Quando Contoso convidou [lucy@supplier1.com](mailto:lucy@supplier1.com) para o seu diretório, a Azure AD cria uma ligação entre [Lucy@supplier1.com](mailto:Lucy@supplier1.com) o inquilino da AD Contoso Azure. Este link permite à Azure AD saber que Lucy@supplier1.com pode aceder a conteúdos no inquilino contoso.

Quando Lucy tenta aceder à aplicação DeSons o's Power BI, a Azure AD verifica que Lucy pode aceder ao inquilino contoso e, em seguida, fornece power BI um símbolo que indica que Lucy é autenticada para aceder a conteúdos no inquilino Contoso. O Power BI usa este token para autorizar e garantir que lucy tem acesso à aplicação Power BI de Contoso.

![Verificação e autorização](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

A integração do Power BI com o Azure AD B2B funciona com todos os endereços de e-mail de negócios. Se o utilizador não tiver uma identidade AD Azure, pode ser solicitado a criar um. A imagem seguinte mostra o fluxo detalhado:

![Gráfico de fluxo de integração](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


É importante reconhecer que a conta Azure AD será usada ou criada no Azure AD do partido externo, o que permitirá à Lucy usar o seu próprio nome de utilizador e senha e as suas credenciais deixarão automaticamente de trabalhar noutros inquilinos sempre que lucy deixar a empresa quando a sua organização também usar a AD Azure.

## <a name="licensing"></a>Licensing

A Contoso pode escolher uma das três abordagens para licenciar utilizadores convidados dos seus fornecedores e organizações parceiras para ter acesso aos conteúdos do Power BI.

> [!NOTE]
> _O nível livre do Azure AD B2B é suficiente para utilizar o Power BI com o Azure AD B2B. Algumas funcionalidades avançadas do Azure AD B2B, como grupos dinâmicos, requerem licenciamento adicional. Consulte a documentação Azure AD B2B para obter informações adicionais:_[_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Abordagem 1: Contoso usa Power BI Premium

Com esta abordagem, a Contoso adquire a capacidade do Power BI Premium e atribui o seu conteúdo do portal BI a esta capacidade. Isto permite aos utilizadores convidados de organizações parceiras aceder à aplicação Power BI da Contoso sem qualquer licença Power BI.

Os utilizadores externos também estão sujeitos ao consumo apenas experiências oferecidas aos utilizadores "Gratuitos" no Power BI ao consumirem conteúdo dentro do Power BI Premium.

A Contoso também pode aproveitar outras capacidades premium power BI para as suas apps, como taxas de atualização aumentadas, capacidade dedicada e grandes tamanhos de modelo.

![Capacidades adicionais](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Abordagem 2: Contoso atribui licenças power BI Pro aos utilizadores convidados

Com esta abordagem, contoso atribui licenças pro a utilizadores convidados de organizações parceiras – isso pode ser feito a partir do centro de administração Microsoft 365 da Contoso. Isto permite que os utilizadores convidados de organizações parceiras acedam à aplicação Power BI da Contoso sem adquirirem uma licença por si mesmas. Isto pode ser apropriado para a partilha com utilizadores externos cuja organização ainda não tenha adotado o Power BI.

> [!NOTE]
> A licença pro de Contoso aplica-se apenas aos utilizadores convidados quando acedem a conteúdos no inquilino contoso. As licenças Pro permitem o acesso a conteúdos que não se encontra na capacidade do Power BI Premium. No entanto, os utilizadores externos com licença Pro são restringidos por padrão a uma experiência de consumo apenas. Isto pode ser alterado utilizando a abordagem descrita na _enableing utilizadores externos para editar e gerir conteúdos dentro_ da secção Power BI mais tarde neste documento.

![Informações de licença](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Abordagem 3: Os utilizadores convidados trazem a sua própria licença Power BI Pro

Com esta abordagem, o Fornecedor 1 atribui uma licença Power BI Pro à Lucy. Podem então aceder à aplicação Power BI da Contoso com esta licença. Uma vez que lucy pode usar a sua licença Pro da sua própria organização ao aceder a um ambiente externo de Power BI, esta abordagem é por vezes referida como _trazer a sua própria licença_ (BYOL). Se ambas as organizações estiverem a utilizar o Power BI, isto oferece um licenciamento vantajoso para a solução de análise global e minimiza a sobrecarga de atribuição de licenças a utilizadores externos.

> [!NOTE]
> A licença profissional dada a Lucy pelo Fornecedor 1 aplica-se a qualquer inquilino da Power BI onde lucy é uma utilizadora convidada. As licenças Pro permitem o acesso a conteúdos que não se encontra na capacidade do Power BI Premium. No entanto, os utilizadores externos com licença Pro são restringidos por padrão a uma experiência de consumo apenas. Isto pode ser alterado utilizando a abordagem descrita na _enableing utilizadores externos para editar e gerir conteúdos dentro_ da secção Power BI mais tarde neste documento.

![Requisitos de licença pro](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Segurança de dados para parceiros externos

Comumente quando se trabalha com vários fornecedores externos, a Contoso precisa de garantir que cada fornecedor vê dados apenas sobre os seus próprios produtos. A segurança baseada no utilizador e a segurança dinâmica do nível da linha tornam isto fácil de realizar com o Power BI.

### <a name="user-based-security"></a>Segurança baseada no utilizador

Uma das características mais poderosas do Power BI é a Segurança de Nível de Linha. Esta funcionalidade permite que contoso crie um único relatório e conjunto de dados, mas ainda aplica diferentes regras de segurança para cada utilizador. Para obter uma explicação aprofundada, consulte a [segurança de nível de linha (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

A integração do Power BI com o Azure AD B2B permite que a Contoso atribua regras de Segurança de Nível de Linha aos utilizadores convidados assim que são convidados para o inquilino contoso. Como já vimos antes, Contoso pode adicionar utilizadores convidados através de convites planeados ou ad-hoc. Se A Contoso quiser impor a segurança ao nível da linha, é fortemente recomendado utilizar convites planeados para adicionar os utilizadores convidados com antecedência e atribuindo-os às funções de segurança antes de partilhar o conteúdo. Se Contoso utilizar convites ad-hoc, poderá haver um curto período de tempo em que os utilizadores convidados não poderão ver quaisquer dados.

> [!NOTE]
> Este atraso no acesso a dados protegidos pelo RLS ao utilizar convites ad-hoc pode levar a pedidos de suporte à sua equipa de TI, uma vez que os utilizadores verão relatórios/dashboards em branco ou quebrados ao abrir um link de partilha no e-mail que recebem. Portanto, é fortemente recomendado usar convites planeados neste cenário.**

Vamos passar por isto com um exemplo.

Como mencionado anteriormente, contoso tem fornecedores em todo o mundo, e eles querem garantir que os utilizadores das suas organizações fornecedoras obtêm insights de dados apenas do seu território.  Mas os utilizadores de Contoso podem aceder a todos os dados. Em vez de criar vários relatórios diferentes, Contoso cria um único relatório e filtra os dados baseados no utilizador que os vê.

![Conteúdo partilhado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Para garantir que o Contoso pode filtrar dados com base em quem está a ligar, são criadas duas funções no ambiente de trabalho power BI. Um para filtrar todos os dados do Território Comercial "Europa" e outro para "América do Norte".

![Gerir funções](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Sempre que as funções são definidas no relatório, um utilizador deve ser atribuído a uma função específica para que possam ter acesso a quaisquer dados. A atribuição de funções ocorre dentro do serviço Power BI **(Datasets > Security)**

![Definição de segurança](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Isto abre uma página onde a equipa bi de Contoso pode ver os dois papéis que criaram.  Agora, a equipa bi de Contoso pode atribuir aos utilizadores as funções.

![Segurança ao Nível da Linha](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

No exemplo, Contoso está adicionando um utilizador numa organização parceira com endereço de e-mail [adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com) " ao papel da Europa:

![Definições de segurança ao nível da linha](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Quando isto for resolvido pela Azure AD, Contoso pode ver o nome aparecer na janela pronto para ser adicionado:

![Mostrar papéis](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Agora, quando este utilizador abre a app que foi partilhada com eles, eles só vêem um relatório com dados da Europa:

![Ver conteúdos](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Segurança dinâmica do nível da linha

Outro tópico interessante é ver como a segurança dinâmica de nível de linha (RLS) funciona com O Azure AD B2B.

Em suma, a segurança de nível dinâmico funciona filtrando dados no modelo com base no nome de utilizador da pessoa que liga ao Power BI. Em vez de adicionar várias funções para grupos de utilizadores, define os utilizadores no modelo. Não descreveremos o padrão em detalhe aqui. Kasper de Jong oferece uma escrita detalhada sobre todos os sabores de segurança de nível de linha na folha de batota de [segurança Power BI Desktop Dynamic](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/), e neste livro [branco.](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx)

Vejamos um pequeno exemplo - Contoso tem um relatório simples sobre vendas por grupos:

![Conteúdo da amostra](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Agora este relatório precisa de ser partilhado com dois utilizadores convidados e um utilizador interno - o utilizador interno pode ver tudo, mas os utilizadores convidados só podem ver os grupos a que têm acesso. Isto significa que devemos filtrar os dados apenas para os utilizadores convidados. Para filtrar os dados adequadamente, Contoso utiliza o padrão Dynamic RLS conforme descrito no whitepaper e no blog post. Isto significa que Contoso adiciona os nomes de utilizador aos próprios dados:

![Ver utilizadores de RLS para os próprios dados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Em seguida, Contoso cria o modelo de dados certo que filtra os dados adequadamente com as relações certas:

![Os dados adequados são apresentados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Para filtrar os dados automaticamente com base em quem está registado, contoso precisa de criar uma função que passe no utilizador que está a ligar. Neste caso, contoso cria duas funções – a primeira é a "função de segurança" que filtra a tabela Utilizadores com o nome de utilizador atual do utilizador que acedeu ao Power BI (isto funciona até para utilizadores convidados do Azure AD B2B).

![Gerir funções](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso também cria outro "AllRole" para os seus utilizadores internos que podem ver tudo – este papel não tem nenhum predicado de segurança.

Depois de enviar o ficheiro de desktop Power BI para o serviço, a Contoso pode atribuir aos utilizadores convidados o "SecurityRole" e os utilizadores internos ao "AllRole"

Agora, quando os utilizadores convidados abrem o relatório, só vêem vendas do grupo A:

![Apenas do grupo A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

Na matriz à direita pode ver o resultado da função USERNAME() e USERPRINCIPALNAME() ambos devolverem o endereço de e-mail dos utilizadores convidados.

Agora o utilizador interno pode ver todos os dados:

![Todos os dados mostrados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Como pode ver, o Dynamic RLS funciona com utilizadores internos ou convidados.

> [!NOTE]
> Este cenário também funciona quando se utiliza um modelo nos Serviços de Análise Azure. Normalmente, o seu Serviço de Análise Azure está ligado ao mesmo Azure AD que o seu Power BI - nesse caso, o Azure Analysis Services também conhece os utilizadores convidados convidados através do Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Ligação a fontes de dados no local

O Power BI oferece a capacidade de Contoso alavancar em fontes de dados premissas como [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) ou [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) diretamente graças à gateway de dados [On-Premises](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). É até possível subscrever essas fontes de dados com as mesmas credenciais utilizadas com o Power BI.

> [!NOTE]
> Ao instalar uma porta de entrada para ligar ao seu inquilino Power BI, deve utilizar um utilizador criado dentro do seu inquilino. Os utilizadores externos não podem instalar um portal e ligá-lo ao seu inquilino._

Para os utilizadores externos, isto pode ser mais complicado, uma vez que os utilizadores externos geralmente não são conhecidos da AD no local. O Power BI oferece uma suver para isso, permitindo que os administradores da Contoso mapeiem os nomes de utilizadores externos para nomes de utilizadores internos, conforme descrito na Fonte de [Dados - Serviços](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)de Análise . Por exemplo, [lucy@supplier1.com](mailto:lucy@supplier1.com) pode ser mapeado para [lucy \_ fornecedor1 \_ com# EXT@contoso.com ](mailto:lucy_supplier1_com).

![Mapeando nomes de utilizadores](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Este método é bom se Contoso tiver apenas um punhado de utilizadores ou se Contoso pode mapear todos os utilizadores externos para uma única conta interna. Para cenários mais complexos onde cada utilizador precisa das suas próprias credenciais, existe uma abordagem mais avançada que utiliza [atributos adáticos personalizados](https://technet.microsoft.com/library/cc961737.aspx) para fazer o mapeamento como descrito na Fonte de [Dados - Serviços](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)de Análise . Isto permitiria ao administrador da Contoso definir um mapeamento para cada utilizador do seu Azure AD (também utilizadores externos de B2B).  Estes atributos podem ser definidos através do modelo de objeto AD usando scripts ou código para que Contoso possa automatizar totalmente o mapeamento em convite ou em cadência programada.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Permitir aos utilizadores externos editar e gerir conteúdos dentro do Power BI

A Contoso pode permitir que utilizadores externos contribuam com conteúdo dentro da organização, tal como descrito anteriormente na secção de edição e gestão de conteúdos power bi.

> [!NOTE]
> Para editar e gerir conteúdos dentro do Power BI da sua organização, o utilizador deve ter uma licença Power BI Pro num espaço de trabalho diferente do meu espaço de trabalho. Os utilizadores podem obter licenças Pro conforme abrangidos pela secção _de Licenciamento_ deste documento.

O Power BI Admin Portal fornece o permitir que os utilizadores externos de **hóspedes editem e gerem conteúdos na** definição da organização nas definições do Arrendatário. Por predefinição, a definição está definida para desativar, o que significa que os utilizadores externos obtêm uma experiência restrita de leitura apenas por padrão. A definição aplica-se aos utilizadores com userType definido para O Hóspede em Azure AD. A tabela abaixo descreve os comportamentos que os utilizadores experimentam dependendo do seu UserType e como as definições são configuradas.

| **Tipo de utilizador em AD Azure** | **Permitir que os utilizadores externos de hóspedes editem e gerem a definição de conteúdos** | **Comportamento** |
| --- | --- | --- |
| Convidado | Desativado para o utilizador (Predefinido) | Por artigo só vista. Permite o acesso apenas a relatórios, dashboards e aplicações quando visualizado através de um URL enviado ao utilizador convidado. As aplicações Power BI Mobile fornecem uma visão apenas para o utilizador convidado. |
| Convidado | Habilitado para o utilizador | O utilizador externo tem acesso a toda a experiência Power BI, embora algumas funcionalidades não estejam disponíveis para os mesmos. O utilizador externo deve iniciar sessão no Power BI utilizando o URL do Power BI Service com as informações do arrendatário incluídas. O utilizador obtém a experiência Home, um My Workspace, e com base em permissões pode navegar, visualizar e criar conteúdo. </br></br> As aplicações Power BI Mobile fornecem uma visão apenas para o utilizador convidado. |

> [!NOTE]
> Os utilizadores externos em AD Azure também podem ser definidos para userType Member. Isto não é atualmente suportado no Power BI.

No portal Power BI Admin, a configuração é mostrada na imagem seguinte.

![Definições de administrador](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Os utilizadores convidados obtêm a experiência padrão de leitura e que podem editar e gerir conteúdos. O predefinido é Desativado, o que significa que todos os utilizadores do Hóspede têm a experiência de leitura. O Power BI Admin pode permitir a definição para todos os utilizadores convidados da organização ou para grupos de segurança específicos definidos em Azure AD. Na imagem seguinte, o Administrador De Poder de Contoso criou um grupo de segurança na Azure AD para gerir quais os utilizadores externos que podem editar e gerir conteúdos no inquilino Contoso.

Para ajudar estes utilizadores a iniciar sessão no Power BI, forneça-lhes o URL do Tenant. Para encontrar o URL de inquilino, siga estes passos:

1. No serviço Power BI, no menu superior, selecione ajuda ( **?** ), em **seguida, sobre o Power BI**.
2. Procure o valor ao lado da URL do **Inquilino.** Este é o URL do inquilino que pode partilhar com os seus utilizadores convidados.

    ![URL de Inquilino](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Ao utilizar o Permitir que os utilizadores externos editem e gerem conteúdos na organização, os utilizadores convidados especificados têm acesso ao Power BI da sua organização e vêem qualquer conteúdo a que tenham permissão. Podem aceder ao Home, navegar e contribuir com conteúdos para espaços de trabalho, instalar aplicações onde estão na lista de acesso, e ter um Espaço de Trabalho My. Podem criar ou ter o cargo de Administrador de áreas de trabalho que utilizem a nova experiência de área de trabalho.

> [!NOTE]
> Ao utilizar esta opção, certifique-se de rever a secção de governação deste documento, uma vez que as definições padrão de AD Do Azure impedem os utilizadores de utilizar certas funcionalidades, como os pickers de pessoas, o que pode levar a uma experiência reduzida.**

Para os utilizadores convidados habilitados através do Permitir que os utilizadores externos de hóspedes editem e gerem conteúdos no ambiente de inquilinos da organização, algumas experiências não estão disponíveis para eles. Para atualizar ou publicar relatórios, os utilizadores convidados precisam de usar o UI web do serviço Power BI, incluindo o Get Data para carregar ficheiros power BI Desktop. As seguintes experiências não são suportadas:

- A publicação direta do Power BI Desktop para o serviço Power BI
- Os utilizadores convidados não podem utilizar o Power BI Desktop para ligar a conjuntos de dados de serviço no serviço Power BI
- Espaços de trabalho clássicos ligados aos Grupos Microsoft 365: O utilizador convidado não pode criar ou ser Administradores destes espaços de trabalho. No entanto, pode ser membro.
- O envio de convites ad-hoc não é suportado para listas de acesso de áreas de trabalho
- O Power BI Publisher para Excel não é suportado para utilizadores convidados
- Os utilizadores convidados não podem instalar o Power BI Gateway e ligá-lo à sua organização
- Os utilizadores convidados não podem instalar aplicações de publicações para toda a organização
- Os utilizadores convidados não podem utilizar, criar, atualizar ou instalar pacotes de conteúdos organizacionais
- Os utilizadores convidados não podem utilizar a funcionalidade Analisar no Excel
- Os utilizadores convidados não podem comentar @mentioned ( esta funcionalidade será adicionada num próximo lançamento)
- Os utilizadores não podem utilizar subscrições (esta funcionalidade será adicionada num próximo lançamento)
- Os utilizadores convidados que utilizem esta funcionalidade devem ter uma conta escolar ou profissional. Os utilizadores convidados que usam contas Pessoais experimentam mais limitações devido a restrições de inscrição.



## <a name="governance"></a>Governação

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Definições adicionais de AD Azure que afetam experiências em Power BI relacionadas com Azure AD B2B

Ao utilizar a partilha Azure AD B2B, o administrador do Diretório Ativo Azure controla aspetos da experiência do utilizador externo. Estes são controlados na página de definições de colaboração Externa dentro das definições de Diretório Ativo Azure para o seu Inquilino.

Os detalhes sobre as definições estão disponíveis aqui:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Por padrão, as permissões dos utilizadores convidados são opções limitadas para Sim, pelo que os utilizadores convidados dentro do Power BI têm experiências limitadas especialmente partilha de surround onde as UIs picker das pessoas não funcionam para esses utilizadores. É importante trabalhar com o seu administrador da AD Azure para defini-lo para Nº, como mostrado abaixo para garantir uma boa experiência.**

![Definições de colaboração externa](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Convidar convidados de controlo

Os administradores do Power BI podem controlar a partilha externa apenas para o Power BI visitando o portal de administração power BI. Mas os administradores de inquilinos também podem controlar a partilha externa com várias políticas da AD Azure.  Estas políticas permitem aos administradores de inquilinos

- Desligue os convites por utilizadores finais
- Apenas administradores e utilizadores no papel de Convidado convidado podem convidar
- Administradores, o papel de Convidado convidado, e membros podem convidar
- Todos os utilizadores, incluindo os hóspedes, podem convidar

Pode ler mais sobre estas políticas nos [convites delegados para a colaboração Azure Ative Directory B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Todas as ações do Power BI por utilizadores externos também são [auditadas no nosso portal](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)de auditoria.

### <a name="conditional-access-policies-for-guest-users"></a>Políticas de Acesso Condicional para utilizadores convidados

A Contoso pode impor políticas de acesso condicional aos utilizadores convidados que acedam a conteúdos do inquilino contoso. Pode encontrar instruções detalhadas no acesso condicional aos utilizadores de [colaboração B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Abordagens alternativas comuns

Embora o Azure AD B2B facilite a partilha de dados e relatórios entre organizações, existem várias outras abordagens que são comumente usadas e podem ser superiores em certos casos.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Opção Alternativa 1: Criar identidades duplicadas para utilizadores parceiros

Com esta opção, Contoso teve de criar manualmente identidades duplicadas para cada utilizador parceiro no Inquilino Contoso, como mostra a seguinte imagem. Em seguida, dentro do Power BI, Contoso pode partilhar com as identidades atribuídas os relatórios apropriados, dashboards ou apps.

![Definição de mapeamentos e nomes apropriados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Razões para escolher esta alternativa:

- Uma vez que a identidade do utilizador é controlada pela sua organização, qualquer serviço relacionado, como e-mail, SharePoint, etc. também está sob o controlo da sua organização. Os seus Administradores de TI podem redefinir senhas, desativar o acesso a contas ou auditar atividades nestes serviços.
- Os utilizadores que utilizam contas pessoais para os seus negócios muitas vezes estão impedidos de aceder a determinados serviços, pelo que podem necessitar de uma conta organizacional.
- Alguns serviços funcionam apenas sobre os utilizadores da sua organização. Por exemplo, não é possível utilizar o Intune para gerir conteúdos nos dispositivos pessoais/móveis de utilizadores externos que utilizem o Azure B2B.

Razões para não escolher esta alternativa:

- Os utilizadores de organizações parceiras devem lembrar-se de dois conjuntos de credenciais: um para aceder a conteúdos da sua própria organização e o outro para aceder a conteúdos a partir de Contoso. Este é um aborrecimento para estes utilizadores convidados e muitos utilizadores convidados estão confusos com esta experiência.
- A Contoso deve adquirir e atribuir licenças por utilizador a estes utilizadores. Se um utilizador precisar de receber e-mails ou usar aplicações de escritório, precisa das licenças apropriadas, incluindo o Power BI Pro para editar e partilhar conteúdos no Power BI.
- Contoso pode querer impor políticas de autorização e governação mais rigorosas para utilizadores externos em comparação com os utilizadores internos. Para isso, o Contoso precisa de criar uma nomenclatura interna para utilizadores externos e todos os utilizadores de Contoso precisam de ser educados sobre esta nomenclatura.
- Quando o utilizador deixa a sua organização, eles continuam a ter acesso aos recursos de Contoso até que o administrador do Contoso apague manualmente a sua conta
- Os administradores da Contoso têm de gerir a identidade para o hóspede, incluindo criação, resets de senha, etc.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Opção Alternativa 2: Criar uma aplicação personalizada power BI incorporada usando a autenticação personalizada

Outra opção para A Contoso é construir a sua própria aplicação power BI personalizada com autenticação personalizada[('App possui dados').](https://docs.microsoft.com/power-bi/developer/embedded/embed-sample-for-customers) Embora muitas organizações não tenham tempo ou recursos para criar uma aplicação personalizada para distribuir conteúdo do Power BI aos seus parceiros externos, para algumas organizações esta é a melhor abordagem e merece séria consideração.

Muitas vezes, as organizações têm portais parceiros existentes que centralizam o acesso a todos os recursos organizacionais para parceiros, fornecem isolamento dos recursos organizacionais internos e proporcionam experiências simplificadas para os parceiros apoiarem muitos parceiros e seus utilizadores individuais.

![Muitos portais parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

No exemplo acima, os utilizadores de cada fornecedor iniciam login no Portal parceiro da Contoso que utiliza a AAD como fornecedor de identidade. Poderia utilizar AAD B2B, Azure B2C, identidades nativas ou federado com qualquer número de outros fornecedores de identidade. O utilizador entraria e acederia a um portal de parceiros construído utilizando a Azure Web App ou uma infraestrutura semelhante.

Dentro da aplicação web, os relatórios power BI são incorporados a partir de uma implementação incorporada de Power BI. A aplicação web simplificaria o acesso aos relatórios e a quaisquer serviços conexos numa experiência coesa que visasse facilitar a interação dos fornecedores com contoso. Este ambiente portal seria isolado do ambiente interno da AAD e do Sistema BI interno de Contoso para garantir que os fornecedores não pudessem aceder a esses recursos. Normalmente, os dados seriam armazenados num armazém de dados separado do Partner para garantir o isolamento dos dados também. Este isolamento tem benefícios, uma vez que limita o número de utilizadores externos com acesso direto aos dados da sua organização, limitando quais os dados que podem estar potencialmente disponíveis para o utilizador externo, e limitando a partilha acidental com utilizadores externos.

Utilizando o Power BI Embedded, o portal pode alavancar o licenciamento vantajoso, utilizando o token da app ou o utilizador principal mais a capacidade premium adquirida no modelo Azure, o que simplifica as preocupações com a atribuição de licenças aos utilizadores finais, e pode escalar para cima/para baixo com base no uso esperado. O portal pode oferecer uma experiência globalmente mais alta e consistente, uma vez que os parceiros acedem a um único portal projetado com todas as necessidades de um Parceiro em mente. Por último, uma vez que as soluções baseadas em Power BI são tipicamente concebidas para serem multi-inquilinos, torna-se mais fácil garantir o isolamento entre organizações parceiras.

Razões para escolher esta alternativa:

- Mais fácil de gerir à medida que o número de organizações parceiras cresce. Uma vez que os parceiros são adicionados a um diretório separado isolado do diretório interno da AAD de Contoso, simplifica os deveres de governação da TI e ajuda a prevenir a partilha acidental de dados internos a utilizadores externos.
- Os Típicos Portals de Parceiros são experiências de grande marca com experiências consistentes entre parceiros e simplificadas para atender às necessidades dos parceiros típicos. Por isso, a Contoso pode oferecer uma melhor experiência global aos parceiros, integrando todos os serviços necessários num único portal.
- Os custos de licenciamento para cenários avançados como a Edição de conteúdos dentro do Power BI Embedded são cobertos pelo Power BI Premium adquirido pelo Azure, e não requer a atribuição de licenças Power BI Pro a esses utilizadores.
- Proporciona um melhor isolamento entre parceiros se for arquitetado como uma solução multi-arrendatária.
- O Portal do Parceiro inclui frequentemente outras ferramentas para parceiros para além dos relatórios power BI, dashboards e apps.

Razões para não escolher esta alternativa:

- É necessário um esforço significativo para construir, operar e manter tal portal, tornando-o um investimento significativo em recursos e tempo.
- O tempo para a solução é muito mais longo do que usar a partilha B2B, uma vez que é necessário um planeamento e execução cuidadosos em vários fluxos de trabalho.
- Quando houver um número menor de parceiros, o esforço necessário para esta alternativa é provavelmente demasiado elevado para justificar.
- A colaboração com a partilha ad-hoc é o cenário primordial enfrentado pela sua organização.
- Os relatórios e os dashboards são diferentes para cada parceiro. Esta alternativa introduz a gestão aérea para além de apenas partilhar diretamente com parceiros.



## <a name="faq"></a>FAQ

**Pode Contoso enviar um convite que é automaticamente redimido, para que o utilizador esteja apenas "pronto para ir"? Ou o utilizador tem sempre de clicar no URL de resgate?**

O utilizador final deve sempre clicar na experiência de consentimento antes de poder aceder ao conteúdo.

Se você vai convidar muitos utilizadores convidados, recomendamos que você delege isso a partir dos seus administradores de AD Azure [core, adicionando um utilizador ao papel](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role)de convidado convidado na organização de recursos . Este utilizador pode convidar outros utilizadores na organização do parceiro utilizando os scripts UI, PowerShell ou APIs de inscrição. Isto reduz os encargos administrativos para os administradores da AD Azure para convidar ou ressentir-se de convites aos utilizadores da organização parceira.

**A Contoso pode forçar a autenticação de vários fatores para os utilizadores convidados se os seus parceiros não tiverem a autenticação multifactor?**

Yes. Para mais informações, consulte [acesso condicional para utilizadores de colaboração B2B.](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions)

**Como funciona a colaboração b2B quando o parceiro convidado está a usar a federação para adicionar a sua própria autenticação no local?**

Se o parceiro tiver um inquilino Azure AD federado para a infraestrutura de autenticação no local, no local é automaticamente alcançado um único sinal on (SSO) no local. Se o parceiro não tiver um inquilino DaD Azure, poderá ser criada uma conta Azure AD para novos utilizadores.

**Posso convidar utilizadores convidados com contas de e-mail de consumo?**

Convidar utilizadores convidados com contas de email de consumo é suportado no Power BI. Isto inclui domínios como hotmail.com, outlook.com e gmail.com. No entanto, estes utilizadores podem experimentar limitações para além do que os utilizadores com contas de trabalho ou de escola encontram.
