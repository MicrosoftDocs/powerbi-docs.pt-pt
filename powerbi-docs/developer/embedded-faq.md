---
title: Perguntas frequentes sobre o Power BI Embedded
description: Procure uma lista de perguntas frequentes e respostas sobre o Power BI Embedded.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 1bdc31d550573b926d45776307b8fcade95f0dc0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222183"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Perguntas frequentes sobre o Power BI Embedded

* Se tiver outras perguntas, [experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/).
* Ainda tem problemas? Visite a [Página de suporte do Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Geral

### <a name="what-is-power-bi-embedded"></a>O que é o Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) permite aos programadores de aplicações incorporar relatórios deslumbrantes e totalmente interativos nas suas aplicações sem ter de criar suas próprias visualizações de dados e controles do zero.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Qual é o público alvo do Power BI Embedded?

Os programadores e empresas de software, os fornecedores de software também conhecido como independentes (ISVs), aplicativos de codificação.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Qual a diferença entre o serviço do Power BI Embedded e do Power BI?

O Power BI é uma solução de análise de software como um serviço que dá às organizações uma vista única dos seus dados empresariais mais críticos.

A Microsoft desenvolveu Power BI Embedded para ISVs que pretendem integrar visuais a seus aplicativos para ajudar os clientes a tomarem decisões de análise. Isso spares ISVs da necessidade de criar a solução de sua própria análise propriamente ditas. [Análises incorporadas](embedding.md) permite que os usuários de negócios acessar dados corporativos e executar consultas em relação a ele para gerar insights na aplicação.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Qual é a diferença entre o Power BI Premium e o Power BI Embedded?

O Power BI Premium é capacidade destinada a empresas que pretendem uma solução de BI completa que fornece uma visão única da sua organização, parceiros, clientes e fornecedores. O Power BI Premium ajuda a organização a tomar decisões. O Power BI Premium é um produto de SaaS que permite que os utilizadores consumirem conteúdo através de aplicações móveis, aplicações desenvolvidas internamente, ou no portal do Power BI.

Power BI Embedded é para ISVs que pretendem integrar visuais nas suas aplicações. O Power BI Embedded ajuda os clientes a tomarem decisões porque é para programadores de aplicações, clientes dessa aplicação podem consumir conteúdo armazenado na capacidade do Power BI Embedded, incluindo qualquer pessoa no interior ou exterior da organização. Não é possível partilhar Power BI Embedded conteúdo de capacidade por meio de um clique publicar na Web ou num único clique publicar no SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Quais as recomendações da Microsoft aos clientes em relação à compra do Power BI Premium vs. o Power BI Embedded?

A Microsoft recomenda que as empresas compram o Power BI Premium, um nível empresarial, a solução de BI em cloud self-service. Recomendamos que ISVs compram Power BI Embedded para seus componentes de análise incorporada com tecnologia de cloud. No entanto, um cliente não tem restrição no qual produto comprar.

Pode haver alguns casos em que um ISV (geralmente de grande dimensão), além de incorporar aplicações, quer utilizar um P SKU para receber os benefícios adicionais do serviço Power BI pré-embalado dentro da organização. Algumas empresas poderão decidir utilizar SKUs A no Azure se só estiverem interessadas na criação de aplicações de linha de negócio e na incorporação das análises nas aplicações e não pretenderem utilizar o serviço Power BI pré-embalado.

### <a name="how-many-embed-tokens-can-i-create"></a>Quantos tokens de incorporação posso criar?

Incorpore tokens com a licença PRO destinam-se para desenvolvimento, teste, para que a conta do Power BI mestra ou [principal de serviço](embed-service-principal.md) só pode gerar um número limitado de tokens. [Compre uma capacidade](#technical) para incorporar num ambiente de produção. Não há nenhum limite para quantas tokens que pode gerar quando compra uma capacidade de incorporação. Aceda a [Funcionalidades Disponíveis](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) para verificar o valor de utilização que indica a utilização atual incorporada em valores percentuais.

## <a name="technical"></a>Parte Técnica

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Qual a diferença entre os A SKUs no Azure e os EM SKUs no Office 365?

PowerBI.com é uma empresa de Software como uma solução de serviço (SaaS) com muitos recursos, como colaboração social, subscrição de e-mail e outros recursos. PowerBI.com ajuda ISVs gerir a sua solução de análise incorporada conteúda e definições de nível de inquilino.

Power BI Embedded é uma plataforma como serviço (PaaS) do conjunto de desenvolvedores APIs pode utilizar para criar uma solução de análise incorporada.

Aqui está uma lista parcial das diferenças de recursos.

| Feature | Power BI Incorporado | Capacidade do Power BI Premium | Capacidade do Power BI Premium |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (A SKUs) | (EM SKUs) | (P SKUs) |
| Incorporar artefactos de uma área de trabalho da Aplicação Power BI | Capacidade do Azure | Capacidade do Office 365 | Capacidade do Office 365 |
| Consumir relatórios do Power BI numa aplicação do Embedded | Sim | Sim | Sim |
| Consumir relatórios do Power BI no SharePoint | Não | Sim | Sim |
| Consumir relatórios do Power BI no Dynamics | Não | Sim | Sim |
| Consumir relatórios do Power BI no Teams (exclui a aplicação móvel) | Não | Sim | Sim |
| Aceder a conteúdos com uma licença GRATUITA do Power BI em Powerbi.com e no Power BI Mobile | Não | Não | Sim |
| Aceder a conteúdos com uma licença GRATUITA do Power BI incorporada nas aplicações do Microsoft Office | Não | Sim | Sim |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Agora, o Power BI oferece três SKUs para incorporação: A SKUs, EM SKUs, e P SKUs. Qual deles deve adquirir para o meu cenário?

|  |A SKU (Power BI Embedded)  |EM SKU (Power BI Premium)  |P SKU (Power BI Premium)  |
|---------|---------|---------|---------|
|Purchase  |Portal do Azure |Office |Office |
|Casos de utilização | Incorporar conteúdo na sua própria aplicação | <li> Incorporar conteúdo na sua própria aplicação <br><br><br> <li> Incorporar conteúdo nas aplicações do MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (exclui a aplicação móvel)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Incorporar conteúdo na sua própria aplicação <br><br><br> <li> Incorporar conteúdo nas aplicações do MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (exclui a aplicação móvel)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> Partilhar conteúdo com os utilizadores do Power BI através do [serviço Power BI](https://powerbi.microsoft.com/)  |
|Faturação |Hora a hora |Mensal |Mensal |
|Alocação  |Sem alocação |Anual  |Mensal/anual |
|Diferenciação |Elasticidade completa-pode aumentar/reduzir verticalmente, colocar em pausa/retomar recursos no portal do Azure ou através da API  |Pode utilizar para incorporar o conteúdo no SharePoint Online e Microsoft Teams (exclui a aplicação móvel) |Combinar a integração nas aplicações e utilizar o serviço do Power BI na mesma capacidade |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quais são os pré-requisitos para criar uma capacidade PBIE no Azure?

* Inicie sessão no seu diretório organizacional (Microsoft contas não são suportadas).
* Tem de ter um inquilino do Power BI, ou seja, pelo menos um utilizador no seu diretório se inscreveu no Power BI. 
* Tem de ter uma subscrição do Azure no seu diretório organizacional.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Como posso monitorizar o consumo da capacidade do Power BI Embedded?

* Ao utilizar o [portal de Administração do Power BI](../service-admin-portal.md#power-bi-embedded).

* Ao transferir a [aplicação de métrica](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) no Power BI.

* Ao utilizar o [registo de diagnósticos do Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Minha capacidade pode dimensionar automaticamente para ajustar ao meu consumo de aplicações?

Embora haja agora de dimensionamento não automático, todas as APIs estão disponíveis para serem dimensionadas a qualquer momento.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Porque é que criar/dimensionar/retomar uma capacidade faz com que esta seja colocada num estado de suspensão?

Aprovisionamento de capacidade (horizontal/retomar/criar) poderá falhar. Pode utilizar a API para obter detalhes para verificar ProvisioningState uma capacidade: [Capacidades – Obter Detalhe](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Só posso criar capacidades do Power BI Embedded numa região específica?

Com a funcionalidade [Multi-geo (Pré-visualização)](embedded-multi-geo.md), pode comprar uma [capacidade do Power BI Embedded](azure-pbie-create-capacity.md) numa região diferente da localização principal do inquilino

### <a name="how-can-i-find-my-pbi-tenant-region"></a>Como posso encontrar minha região de inquilino do PBI?

Pode utilizar o portal PBI para encontrar a sua região de inquilino de PBI.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > Sobre o Power BI

![Sobre o Power BI](media/embedded-faq/about-01.png)
![Região de inquilino](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>O que suporta o canal de fornecedor de soluções Cloud (CSP)?

* Pode criar uma capacidade PBIE para o seu inquilino com o tipo de subscrição CSP
* A conta de parceiro pode iniciar sessão no inquilino de cliente e adquirir o PBIE para o mesmo, bem como especificar um utilizador do inquilino de cliente como administrador de capacidades do Power BI

### <a name="why-do-i-get-an-unsupported-account-message"></a>Porque é que estou a receber uma mensagem de conta não suportada?

O Power BI exige que se inscreva com uma conta escolar ou profissional. A tentar inscrever-se no Power BI com uma conta Microsoft não é suportada.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Pode utilizar as APIs para criar e gerir as capacidades do Azure?

Sim, existem cmdlets do Powershell e APIs de REST do Gestor de recursos do Azure que pode utilizar para criar e gerir recursos PBIE.

* [REST APIs](https://docs.microsoft.com/rest/api/power-bi-embedded/)
* [Cmdlets do PowerShell](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Qual é a função de capacidade dedicada do Power BI Embedded numa solução do Power BI Embedded?

Para [promova a sua solução para produção](embed-sample-for-customers.md#move-to-production), tem de atribuir o conteúdo do Power BI (área de trabalho de aplicação) a sua aplicação utiliza a uma capacidade do Power BI Embedded (um SKU).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>Em que regiões do Azure é PBI incorporado disponível?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) – veja Gestor de disponibilidade do produto

Regiões disponíveis (16 – o mesmo número de regiões do Power BI)

* E.U.A. (6) – E.U.A Leste, E.U.A. Leste 2, E.U.A. Centro-Norte, E.U.A. Centro-Sul, E.U.A. Oeste, E.U.A. Oeste 2
* Europa (2) – Europa do Norte, Europa Ocidental
* Ásia-Pacífico (2) – Sudeste Asiático, Ásia Oriental
* Brasil (1) – Sul do Brasil
* Japão (1) – Leste do Japão
* Austrália (1) – Sudeste da Austrália
* Índia (1) – Oeste da Índia
* Canadá (1) – Canadá Central
* Reino Unido (1) – Sul do Reino Unido

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>O que é o modelo de autenticação do Power BI Embedded?

Power BI Embedded continua a utilizar para autenticação de utilizador principal (um utilizador licença Power BI Pro designado), ou com o Azure AD [principal de serviço](embed-service-principal.md) para autenticar a aplicação no interior do Power BI.  

 Um ISV pode implementar sua própria autenticação e autorização para seus aplicativos.

Pode utilizar o seu diretório existente se já tiver um inquilino do Azure AD. Também pode criar um novo inquilino do Azure AD para sua segurança de conteúdos de aplicações incorporadas.

Para obter um token do AAD, pode utilizar uma das [Bibliotecas de Autenticação do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Existem bibliotecas cliente disponíveis para múltiplas plataformas.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>A minha Aplicação já utiliza o AAD para a Autenticação de Utilizadores. Como podemos utilizar esta Identidade ao efetuar a autenticação no Power BI num cenário "Os Dados Pertencem ao Utilizador"?

É padrão em-nome-de fluxo do OAuth (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Terá de configurar a sua aplicação para exigir as permissões de serviço (com os âmbitos necessários) do Power BI. Depois de ter um token de utilizador à sua aplicação, basta chamar a ADAL AcquireTokenAsync de API através do acesso de utilizador do token e especifique o URL de recurso do Power BI como o ID de recurso:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>O objeto que ID é o ID de objeto do principal de serviço?

O *ID de objeto* na tela principal de um aplicativo registrado é o ID de objeto para a aplicação.

O objeto ID encontrado no *aplicação gerida no diretório local > propriedades* seção é o ID de objeto do principal de serviço tem de utilizar. Este ID de objeto é fazer referência a um principal de serviço para operações de ou para fazer alterações ao objeto do principal de serviço ID. Como a aplicação de um principal de serviço como um administrador para uma área de trabalho.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Qual a diferença entre o Power BI Embedded e os outros serviços do Azure?

Tem de ter uma conta do Power BI antes de adquirir o Power BI Embedded no Azure. O Power BI Embedded implementado região determina sua conta do Power BI. Faça a gestão dos recursos do Power BI Embedded no Azure para:

* Aumentar/reduzir verticalmente
* Adicionar administradores de capacidade
* Serviço de colocação em pausa/retomar

Utilize o PowerBI.com para atribuir/anular a atribuição de áreas de trabalho para a capacidade do Power BI Embedded.

### <a name="what-are-the-supported-deploy-regions"></a>O que são suportadas as regiões de implementação?

Sudeste da Austrália, Sul do Brasil, Canadá Central, E.U.A Leste 2, Oeste da Índia, Leste do Japão, EUA Centro-Norte, Europa do Norte, EUA Centro-Sul, Sudeste Asiático, Sul do Reino Unido, Europa Ocidental, EUA Oeste e EUA Oeste 2.

### <a name="what-content-pack-data-types-can-you-embed"></a>Que tipos de dados do pacote de conteúdos pode incorporar?

*Não é possível* incorporar **Dashboards** e **mosaicos** criados a partir de conjuntos de dados do pacote de conteúdos. No entanto, *pode* incorporar **relatórios** criados a partir de um conjunto de dados do pacote de conteúdos.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Qual é a diferença entre usar a segurança ao nível da linha (RLS) vs. os filtros de JavaScript?

É frequente confusão em relação ao utilizar a RLS em comparação com os filtros de JavaScript, porque um dos métodos é sobre como controlar o que pode ver um utilizador específico e o outro é sobre a otimização de vista do usuário.

Na RLS, o programador de ISV controla a filtragem de dados como parte da criação de modelos e da geração de tokens de incorporação. O utilizador final vê apenas aquilo que o ISV permite. Neste caso, o utilizador pode optar por ver menos do que está a ser filtrado, mas não pode ignorar a configuração da RLS e ver mais do que está autorizado.

Para o lado do cliente filtragem (JavaScript), o ISV pode decidir o que o usuário final vê a exibição inicial, mas eles não é possível controlar as alterações que o utilizador final podem aplicar-se para a própria exibição. Uma vez que o utilizador. o código de cliente Javascript pode acionar a filtragem de back-end de dados, ele não pode ser considerado seguro.

Consulte [RLS vs. filtros de JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters) para obter mais detalhes.

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Como posso gerir as permissões dos principais de serviço com o Power BI?

Após habilitar [principal de serviço](embed-service-principal.md) para utilizar com o Power BI, as permissões do AD da aplicação não entrem em vigor mais. Em seguida, as permissões da aplicação serão geridas através do portal de administração do Power BI.

Os principais de serviço herdam as permissões de todas as definições do inquilino do Power BI do respetivo grupo de segurança. Para restringir as permissões, criar um grupo de segurança dedicado para principais de serviço e adicione-o para o **exceto grupos de segurança específicos** lista para que as definições do Power BI relevantes, ativadas.

Esta situação é importante quando adicionar o principal de serviço como um **administrador** à nova área de trabalho. Pode gerir esta tarefa através das [APIs](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) ou com o serviço Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Quando devo utilizar um ID da aplicação vs. um ID do objeto do principal de serviço?

O **[ID da aplicação](embed-sample-for-customers.md#application-id)** é utilizado para criar o token de acesso ao passar o ID da aplicação para autenticação.

Para fazer referência a um principal de serviço para operações ou fazer alterações, é utilizado o **[ID do objeto do principal de serviço](embed-service-principal.md#how-to-get-the-service-principal-object-id)** – por exemplo, para aplicar um principal de serviço como um administrador a uma área de trabalho.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>É possível gerir um gateway de dados no local com o principal de serviço?

Não é possível gerir um gateway de dados no local (gateway de dados) com um [principal de serviço](embed-service-principal.md) como pode fazê-lo com uma conta principal.

Com uma conta principal, pode instalar um gateway de dados, adicionar utilizadores ao gateway, ligar a origens de dados e realizar outras tarefas administrativas.

Com um principal de serviço, pode configurar a [segurança ao nível da linha (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview) através de uma origem de dados de ligação em direto no local do SQL Server Analysis Services (SSAS). Desta forma, pode gerir utilizadores e o respetivo acesso aos dados no SSAS durante a integração com o **Power BI Embedded** através de um principal de serviço.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>É possível iniciar sessão no serviço Power BI com o principal de serviço?

Não é possível iniciar sessão no Power BI com o principal de serviço.

Além disso, não é possível consumir conteúdos como um utilizador em aplicações externas (incorporação do SSAS). Só é possível fazê-lo quando gerar um token de incorporação.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Quais são as melhores práticas para melhorar o desempenho?

[Desempenho do Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licensing

### <a name="how-do-i-purchase-power-bi-embedded"></a>Como posso adquirir o Power BI Embedded?

O Power BI Embedded está disponível através do Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>O que acontece se já adquiri o Power BI Premium e agora pretendo algumas de de Power BI Embedded em benefícios do Azure?

Os clientes continuam a pagar por quaisquer compras existentes do Power BI Premium até ao fim do prazo atual do contrato e, em seguida, nessa altura, podem mudar suas compras do Power BI Premium conforme necessário.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Ainda é necessário comprar o Power BI Premium para ter acesso ao Power BI Embedded?

Não, o Power BI Embedded inclui a capacidade baseada no Azure que vai precisar para implementar e distribuir a sua solução aos clientes.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Qual é o compromisso de compra do Power BI Embedded?

Os clientes podem mudar a respetiva utilização numa base horária. Não existe nenhum compromisso mensal nem anual para o serviço Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Como é que a utilização do Power BI Embedded aparece detalhada na minha fatura?

O Power BI Embedded é faturado numa taxa por hora previsível, com base no tipo de nós implementados. É cobrado desde que o recurso está ativo, mesmo que não exista utilização. Tem de colocar em pausa o recurso para parar a faturação.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Quem necessita de uma licença do Power BI Pro para o Power BI Embedded e por que motivo?

Precisa de uma licença do Power BI Pro ou [principal de serviço](embed-service-principal.md) utilizar REST APIs. Para adicionar relatórios numa área de trabalho do Power BI, um analista tem uma licença do Power BI Pro ou o serviço principal. Para gerir o inquilino do Power BI e a capacidade, um administrador é necessário ter uma licença do Power BI Pro.

Como o Power BI Embedded permite utilizar portal do Power BI para gerir e validar o conteúdo incorporado, a licença do Power BI Pro é necessário para autenticar a aplicação no PowerBI.com para ter acesso aos relatórios nos repositórios certos.

No entanto, para [criar/editar relatórios incorporados](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) na sua aplicação, o utilizador final não precisa de uma licença Pro, uma vez que não é obrigatório que seja um utilizador do Power BI.

### <a name="can-i-get-started-for-free"></a>Pode começar a utilizar gratuitamente?

Sim, pode utilizar os seus [créditos do Azure](https://azure.microsoft.com/free/) para o Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Posso obter uma experiência de avaliação para o Power BI Embedded no Azure?

Uma vez que o Power BI Embedded é uma parte do Azure, é possível utilizar o serviço com o [crédito de 200 EUR recebido ao inscrever-se para o Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>O Power BI Embedded está disponível para clouds nacionais (US Government, Alemanha, China)?

Power BI Embedded também está disponível para [clouds nacionais](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>O Power BI Embedded está disponível para entidades educacionais e sem fins lucrativos?

Não há nenhum especial os preços do Azure para as entidades educacionais e sem fins lucrativos.

## <a name="power-bi-workspace-collection"></a>Coleção de Áreas de Trabalho do Power BI

### <a name="what-is-power-bi-workspace-collection"></a>O que é a Coleção de Áreas de Trabalho do Power BI?

**Coleção de área de trabalho de BI de energia** (**Power BI Embedded** versão 1) é uma solução baseada no **coleção de área de trabalho do Power BI** recursos do Azure. Esta solução permite-lhe criar aplicações **Power BI Embedded** para os seus clientes com conteúdo do Power BI por meio da solução **Coleção de Áreas de Trabalho do Power BI**, APIs dedicadas e chaves de área de trabalho para autenticar a aplicação para o Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Posso migrar conteúdos da Coleção de Áreas de Trabalho do Power BI para o Power BI Embedded?

1. Pode utilizar a ferramenta de migração para clonar conteúdo da **Coleção de Áreas de Trabalho do Power BI** para o Power BI – https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Comece pelas POC da aplicação **Power BI Embedded** que utilizam o conteúdo do Power BI.

3. Assim que estiver pronto para a produção, compre uma capacidade dedicada do **Power BI Embedded** e atribua o seu conteúdo do Power BI (área de trabalho) a essa capacidade.

    > [!Note]
    > Pode continuar a utilizar a **Coleção de Áreas de Trabalho do Power BI** durante a criação em paralelo com uma solução **Power BI Embedded**. Assim que tudo estiver pronto, pode mover o seu cliente para a nova solução **Power BI Embedded** e descontinuar a solução **Coleção de Áreas de Trabalho do Power BI**.

Para obter mais informações, veja [Como migrar conteúdos da Coleção de Áreas de Trabalho do Power BI para o Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded)

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>É a coleção de área de trabalho do Power BI num caminho de preterição?

Sim, mas os clientes que já estiver a utilizar o **coleção de área de trabalho do Power BI** solução pode continuar a utilizá-lo até preterição. Os clientes também podem criar novas coleções de áreas de trabalho, bem como quaisquer aplicações do **Power BI Embedded** que ainda utilizem a solução **Coleção de Áreas de Trabalho do Power BI**.

No entanto, isso também significa que não são adicionadas novas funcionalidades para qualquer **coleção de área de trabalho do Power BI** soluções. Encorajamos os clientes a planear a sua migração para o novo **Power BI Embedded** solução.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Quando é que o suporte da Coleção de Áreas de Trabalho do Power BI será descontinuado?

Os clientes que já estejam a utilizar a solução **Coleção de Áreas de Trabalho do Power BI** podem continuar a utilizá-la até ao fim de junho de 2018 ou até ao fim do contrato de suporte.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>Em que regiões posso criar uma coleção de área de trabalho de PBI?

As regiões disponíveis são o Sudeste da Austrália, Sul do Brasil, Canadá Central, EUA Leste 2, Oeste da Índia, Leste do Japão, EUA Centro-Norte, Europa do Norte, EUA Centro-Sul, Sudeste Asiático, Sul do Reino Unido, Europa Ocidental e EUA Oeste.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Porque devo migrar conteúdos da Coleção de Áreas de Trabalho do PBI para o Power BI Embedded?

Existem algumas novas **Power BI Embedded** recursos de solução e as funcionalidades que não é possível fazer com **coleção de área de trabalho do Power BI**.

Algumas das funcionalidades são:
* Todas as origens de dados PBI são suportadas. Apenas dois **coleção de área de trabalho do Power BI** origens de dados são suportadas. 
* As novas funcionalidades, como Perguntas e Respostas, atualizar, marcadores, incorporação de dashboards e mosaicos e menus personalizados só são suportadas na solução **Power BI Embedded**.
* Modelo de faturação de capacidade.

## <a name="embedding-setup-tool"></a>Ferramenta de configuração de incorporação

### <a name="what-is-the-embedding-setup-tool"></a>O que é a Ferramenta de configuração de incorporação?

A [Ferramenta de configuração de incorporação](https://aka.ms/embedsetup) permite-lhe começar e transferir rapidamente uma aplicação de exemplo para começar a incorporar com o Power BI.

### <a name="which-solution-should-i-choose"></a>Que solução devo escolher?

* A solução [Incorporar para os seus clientes](embedding.md#embedding-for-your-customers) permite-lhe incorporar dashboards e relatórios para utilizadores que não têm uma conta para o Power BI. Execute a solução [Incorporar para os seus clientes](https://aka.ms/embedsetup/AppOwnsData).
* A solução [Incorporar para a sua organização](embedding.md#embedding-for-your-organization) permite-lhe alargar o serviço Power BI. Execute a solução [Incorporar a sua organização](https://aka.ms/embedsetup/UserOwnsData).

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Transferi a aplicação de exemplo. Que solução devo escolher?

Se estiver a trabalhar com a experiência **Incorporar para os seus clientes**, guarde e descomprima o ficheiro *PowerBI-Developer-Samples.zip*. Em seguida, abra a pasta *PowerBI-Developer-Samples-master\App Owns Data* e execute o ficheiro *PowerBIEmbedded_AppOwnsData.sln*.

Se estiver a trabalhar com a experiência **Incorporar para a sua organização**, guarde e descomprima o ficheiro *PowerBI-Developer-Samples.zip*. Em seguida, abra a pasta *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-ap* e execute o ficheiro *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>Como posso editar a minha aplicação registada?

Para saber como editar aplicações registadas no Azure AD, veja [Guia de Início Rápido: atualizar uma aplicação no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Como posso editar os meus dados ou o meu perfil de utilizador do Power BI?

Pode saber como editar os seus dados do Power BI [aqui](https://docs.microsoft.com/power-bi/service-basic-concepts).

Para obter mais informações, veja [Resolver problemas da sua aplicação incorporada](embedded-troubleshoot.md).

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
