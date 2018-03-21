---
title: Perguntas frequentes sobre o Power BI Embedded
description: Procure uma lista de perguntas frequentes e respostas sobre o Power BI Embedded.
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/07/2018
ms.author: maghan
ms.openlocfilehash: 52ff1095c063be867354a23e0e8e4908a4b4e1d7
ms.sourcegitcommit: ee5d044db99e253c27816e0ea6bdeb9e39a2cf41
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Perguntas frequentes sobre o Power BI Embedded

* Se tiver outras perguntas, [experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/).
* Ainda tem problemas? Visite a [página de suporte do Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Geral

### <a name="what-is-power-bi-embedded"></a>O que é o Power BI Embedded?

O Microsoft Power BI Embedded permite aos programadores de aplicações integrarem espetaculares relatórios totalmente interativos, dashboards e mosaicos em aplicações sem o tempo e a despesa de criar as suas próprias visualizações e controlos de raiz.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Qual é o público alvo do Power BI Embedded?

Os programadores e empresas de software que criam as suas próprias aplicações, conhecidos como fornecdores de software independentes (ISVs).

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Qual a diferença entre o serviço do Power BI Embedded e do Power BI?

O Power BI Embedded destina-se a ISVs ou programadores que estão a criar aplicações e pretendem integrar visuais nas suas aplicações para ajudar os clientes a tomarem decisões sem construirem uma solução de análises de raiz. As análises integradas permitem aos utilizadores empresariais acederem aos dados do negócio e efetuarem consultas para gerar informações utilizando estes dados na aplicação.

Por outro lado, o Power BI é uma solução de análise de software como um serviço que dá às organizações uma vista única dos seus dados empresariais mais críticos.

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Qual é a diferença entre o Power BI Premium e o Power BI Embedded?

O Power BI Premium destina-se às empresas que pretendem uma solução completa de BI que forneça uma vista única da respetiva organização, parceiros, clientes e fornecedores. O Power BI Premium ajuda a organização a tomar decisões. O Power BI Premium é um produto SaaS e tem a capacidade para os utilizadores consumirem conteúdo através do portal do Power BI, aplicação móvel e através de aplicações desenvolvidas internamente.

O Power BI Embedded é para ISVs ou programadores que estão a construir aplicações e pretendem integrar visuais nessas aplicações. O Power BI Embedded ajuda os clientes a tomarem decisões porque é para programadores de aplicações, clientes dessa aplicação podem consumir conteúdo armazenado na capacidade do Power BI Embedded, incluindo qualquer pessoa no interior ou exterior da organização. Não é possível partilhar o conteúdo de capacidade do Power BI Embedded através da publicação com um único clique na Web ou a publicação com um único clique no SharePoint e não suporta relatórios SSRS.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Quais as recomendações da Microsoft aos clientes em relação à compra do Power BI Premium vs o Power BI Embedded?

A recomendação da Microsoft é que as empresas compram o Power BI Premium, uma solução BI personalizada na nuvem ao nível empresarial e ISVs compram Power BI Embedded, componentes de análise integrados suportados pela nuvem. No entanto, não existem restrições em relação ao produto que um cliente pode comprar.

Podem ocorrer situações em que um ISV (geralmente de grande dimensão) pretende utilizar um P SKU para receber os benefícios adicionais do serviço pré-embalado do Power BI na organização, bem como integrar as suas aplicações. E claro, algumas empresas podem decidir utilizar A SKUs no Azure se só estiverem interessados na construção da linha de aplicações empresariais e na integração das análises nas aplicações e não pretenderem utilizar o serviço Power BI pré-embalado.

### <a name="how-many-embed-tokens-can-i-create"></a>Quantos tokens de incorporação posso criar?

Os tokens de incorporação com a licença PRO destinam-se a testes de desenvolvimento e de programadores. O número de tokens de incorporação que uma conta principal do Power BI pode gerar é limitado. Tem de [comprar capacidade](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) para poder incorporar num ambiente de produção. Não existe limite de número de tokens de incorporação que pode gerar quando compra capacidade.

### <a name="when-will-power-bi-embedded-be-available-in-azure"></a>Quando é que o Power BI Embedded estará disponível no Azure?

O Power BI Embedded já está disponível.

## <a name="technical"></a>Parte Técnica

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Qual a diferença entre os A SKUs no Azure e os EM SKUs no Office 365?

PowerBI.com é uma solução empresarial que inclui muitas funcionalidades de colaboração social, subscrição de e-mail, etc. num software como oferta de serviços

Power BI Embedded é um conjunto de APIs disponíveis para os programadores criarem uma solução de análise integrada numa Plataforma como oferta de serviços. Para o cenário de análise do Embedded, deve utilizar-se PowerBI.com para ajudar os ISVs e os programadores a gerir o conteúdo da solução de análise integrada e as definições ao nível do inquilino.

Segue-se uma lista parcial de diferenças que pode utilizar para cada um.

|Destaque  |Power BI Embedded<br>(A SKUs) |Capacidade do Power BI Premium<br>(EM SKUs)  |
|---------|---------|---------|
|Incorporar artefactos de áreas de trabalho da aplicação Power BI     |Capacidade do Azure |Capacidade do Office 365 |
|Licença do Power BI necessária para consumir relatórios |No  |Sim |
|Consumir relatórios do Power BI numa aplicação do Embedded |Sim  |Sim |
|Consumir relatórios do Power BI no SharePoint |No |Sim |
|Consumir relatórios do Power BI no Teams |No |Sim |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Agora, o Power BI oferece três SKUs para incorporar: A SKUs, EM SKUs e P SKUs. Qual deles deve adquirir para o meu cenário?

|  |A SKU (Power BI Embedded)  |EM SKU (Power BI Premium)  |P SKU (Power BI Premium)  |
|---------|---------|---------|---------|
|Comprar     |Portal do Azure |Office |Office |
|Casos de utilização |* Integrar o conteúdo na sua própria aplicação |* Integrar o conteúdo na sua própria aplicação<br>* Partilhar conteúdo com utilizadores LIVRES de Power BI fora de PowerBI.com e integrar nas outras aplicações SaaS (SharePoint, Teams) |* Integrar o conteúdo na sua própria aplicação<br>* Partilhar conteúdo com utilizadores LIVRES de Power BI fora de PowerBI.com e integrar nas outras aplicações SaaS (SharePoint, Teams)<br>* Partilhar conteúdo com os utilizadores LIVRES do Power BI através de PowerBI.com  |
|Faturação |Hora a hora |Mensal |Mensal |
|Alocação  |Sem alocação |Anual  |Mensal/anual |
|Diferenciação |Elasticidade completa-pode aumentar/reduzir verticalmente, colocar em pausa/retomar recursos no portal do Azure ou através da API  |Pode ser utilizado para incorporar o conteúdo no SharePoint Online e Microsoft Teams |Combinar a integração nas aplicações e utilizar o serviço do Power BI na mesma capacidade |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quais são os pré-requisitos para criar uma capacidade PBIE no Azure?

- Tem de iniciar sessão no diretório organizacional (as contas MSA não são suportadas).
- Tem de ter um inquilino do Power BI, ou seja, pelo menos um utilizador no seu diretório tem de estar inscrito no Power BI. 
- Tem de ter uma subscrição do Azure no seu diretório organizacional.

### <a name="how-can-i-monitor-capacity-consumption"></a>Como posso monitorizar o consumo de capacidade?

A monitorização através do Azure está planeada a curto prazo. O recurso do Azure, Power BI Embedded, irá incluir KPIs de monitorização que apresentação o estado de funcionamento e a utilização.

### <a name="will-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>A minha capacidade será dimensionada automaticamente para ajustar para o consumo da minha aplicação?

Apesar de não existir qualquer dimensionamento automatizado agora, todas as APIs estão disponíveis para serem dimensionadas a qualquer momento.

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>O que é o modelo de autenticação para o Power BI Embedded?

O Power BI Embedded continuará a utilizar o Azure AD para autenticação do utilizador principal (um utilizador com licença Power BI Pro designado), ao autenticar a aplicação no interior do Power BI.

A autenticação e a autorização dos utilizadores da aplicação serão implementadas por de ISV, o ISV pode implementar a sua própria autenticação para as respetivas aplicações.

Se já tiver um inquilino do Azure AD, pode utilizar o seu diretório existente ou pode criar um novo inquilino do Azure AD para a segurança do conteúdo de aplicações incorporadas.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Qual a diferença entre o Power BI Embedded e os outros serviços do Azure?

O ISV/programador tem de ter uma conta do Power BI antes de comprar o Power BI Embedded no Azure. A sua região de implementação do Power BI Embedded é determinada pela sua conta do Power BI. Faça a gestão dos recursos do Power BI Embedded no Azure para:

* Aumentar/reduzir verticalmente
* Adicionar administradores de capacidade
* Colocar em pausa/retomar o serviço

Utilize o PowerBI.com para atribuir/anular a atribuição de áreas de trabalho para a capacidade do Power BI Embedded.

### <a name="what-deploy-regions-are-supported"></a>Quais as regiões de implementação suportadas?

Sudeste da Austrália, Sul do Brasil, Canadá Central, E.U.A Leste 2, Índia Ocidental, Leste do Japão, EUA Centro-Norte, Europa do Norte, EUA Centro-Sul, Sudeste Asiático, Sul do Reino Unido, Europa Ocidental, EUA Oeste e EUA Oeste 2.

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>Que tipo de dados do pacote de conteúdos pode ser incorporado?

Os **dashboards** e **mosaicos** criados a partir de conjuntos de dados do pacote de conteúdos *não podem* ser incorporados, no entanto os **relatórios** criados a partir de um conjunto de dados do pacote de conteúdos *podem* ser incorporados.

## <a name="licensing"></a>Licenças

### <a name="how-do-i-purchase-power-bi-embedded"></a>Como posso adquirir o Power BI Embedded?

O Power BI Embedded está disponível através do Azure.

### <a name="how-power-bi-embedded-be-metered"></a>Como é calculado o Power BI Embedded?

O Power BI Embedded terá um medidor de horas.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Como é que a utilização do Power BI Embedded aparece detalhada na minha fatura?

O Power BI Embedded é faturado numa taxa por hora previsível, com base no tipo de nós implementados. Tenha em atenção que será cobrado mesmo que não exista utilização, basta que o seu recurso esteja ativo. Para parar de ser cobrado, tem de colocar ativamente o seu recurso em pausa. Pode colocar o seu recurso em pausa através do Azure ou de APIs do ARM.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>O que acontece se já adquiri o Power BI Premium e agora pretendo algumas das vantagens do Power BI Embedded no Azure?

Os clientes continuarão a pagar por quaisquer compras existentes do Power BI Premium até ao fim do respetivo termo atual do contrato e, em seguida, podem mudar as compras do Power BI Premium, conforme necessário nesse momento.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Ainda é necessário comprar o Power BI Premium para ter acesso ao Power BI Embedded?

Não, o Power BI Embedded inclui o Azure com base na capacidade que necessita para implementar e distribuir a sua solução aos clientes.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Quem necessita de uma licença do Power BI Pro para o Power BI Embedded e por que motivo?

É necessário que qualquer analista que tenha de adicionar relatórios a uma área de trabalho do Power BI, qualquer programador que necessita de utilizar as APIs REST, qualquer administrador de inquilinos que tenha de gerir o inquilino do Power BI e a capacidade necessitará de uma licença do Power BI Pro.

Como o Power BI Embedded permite utilizar o portal do Power BI para gerir e validar o conteúdo integrado, é necessária uma licença do Power BI Pro para autenticar a aplicação no PowerBI.com para ter acesso aos relatórios nos repositórios certos.

### <a name="can-i-get-started-for-free"></a>Pode começar a utilizar gratuitamente?

Sim, pode utilizar os seus [créditos do Azure](https://azure.microsoft.com/free/) para o Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Posso obter uma experiência de avaliação para o Power BI Embedded no Azure?

Uma vez que o Power BI Embedded faz parte do Azure é possível utilizar o serviço com o [crédito de 200 EUR recebido ao inscrever-se para o Azure](https://azure.microsoft.com/free/).

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Qual é o compromisso de compra do Power BI Embedded? 

Os clientes podem mudar a respetiva utilização numa base horária. Não existe um compromisso mensal nem anual para o serviço do Power BI Embedded.

### <a name="where-is-power-bi-embedded-available-us-government-germany-china-what-is-the-timing"></a>Onde está disponível o Power BI Embedded? Governo dos EUA? Alemanha? China? Qual é o período de tempo?

O Power BI Embedded está disponível nas clouds comerciais do Azure e na cloud da administração pública dos Estados Unidos.  A disponibilidade da cloud soberana será adicionada para a Alemanha e a China no futuro.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>O Power BI Embedded está disponível para entidades educacionais e sem fins lucrativos?

As entidades educacionais e sem fins lucrativos podem comprar o Azure. Não existe nenhum preço especial para estes tipos de clientes no Azure.

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
