---
title: Análise incorporada com o Power BI
description: O Power BI oferece APIs para utilizar análises incorporadas nos seus dashboards e relatórios em aplicações. Saiba mais sobre a incorporação com o Power BI, num ambiente de PaaS e num ambiente de SaaS com software de análise incorporado, ferramentas de análise incorporadas ou ferramentas de business intelligence incorporadas.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051073"
---
# <a name="embedded-analytics-with-power-bi"></a>Análise incorporada com o Power BI

O serviço Power BI (SaaS) e o serviço Power BI Embedded no Azure (PaaS) têm APIs para incorporar os seus dashboards e relatórios. Ao incorporar conteúdos, isso lhe dá acesso para as funcionalidades mais recentes do Power BI, como dashboards, gateways e áreas de trabalho de aplicação.

Pode utilizar a [Ferramenta de configuração de incorporação](https://aka.ms/embedsetup) para começar rapidamente e transferir uma aplicação de exemplo.

Escolha a solução mais adequada para si:

* A solução [Incorporar para a sua organização](embedding.md#embedding-for-your-organization) permite-lhe alargar o serviço Power BI. Para fazer isso, implementar o [incorporação para a sua organização](https://aka.ms/embedsetup/UserOwnsData) solução.
* [Incorporar para os seus clientes](embedding.md#embedding-for-your-customers) permite-lhe incorporar dashboards e relatórios para os utilizadores que não tem uma conta do Power BI. Para fazer isso, implementar o [incorporação para os seus clientes](https://aka.ms/embedsetup/AppOwnsData) solução.

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Utilize as APIs

Existem dois cenários principais para incorporar conteúdo do Power BI:
- A incorporar para os utilizadores da sua organização (que possuem licenças do Power BI). 
 
- A incorporar para os seus utilizadores e os clientes que não precisam de licenças do Power BI. 

O [API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) permite ambos os cenários.

No caso de clientes e utilizadores sem licenças do Power BI, pode incorporar dashboards e relatórios na sua aplicação personalizada, utilizando a mesma API para servir a sua organização ou os seus clientes. Os seus clientes veem os dados de aplicativo gerenciado. Além disso, os utilizadores do Power BI da sua organização tem opções adicionais para ver *seus dados* diretamente no Power BI ou no contexto da aplicação incorporado. Pode tirar total partido das APIs REST e JavaScript para as suas necessidades de incorporação.

Para compreender como a incorporação funciona, veja a [exemplo de incorporação de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Incorporar para a sua organização

A solução **Incorporar para a sua organização** permite-lhe alargar o serviço Power BI. Este tipo de incorporação requer o início de sessão de utilizadores da sua aplicação no serviço Power BI para ver o conteúdo. Quando alguém na sua organização iniciar sessão, essa pessoa só terá acesso aos relatórios e dashboards de que é proprietária ou que alguém partilhou com a mesma no serviço Power BI.

Exemplos de incorporação de organização incluem aplicativos internos, tal como [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [integração do Microsoft Teams (tem de ter direitos de administrador)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), e [doMicrosoftDynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Para incorporar para a sua organização, consulte [Tutorial: Incorporar conteúdo do Power BI numa aplicação para a sua organização](embed-sample-for-your-organization.md).

Capacidades self-service, como editar, guardar, entre outras, estão disponíveis na [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) na incorporação para utilizadores do Power BI.

Pode avançar para o [ferramenta de configuração de incorporar](https://aka.ms/embedsetup/UserOwnsData) para começar a utilizar e transferir uma aplicação de exemplo que explica-lhe integrar um relatório para a sua organização.

## <a name="embedding-for-your-customers"></a>Incorporar para os seus clientes

**Incorporar para os seus clientes** permite-lhe incorporar dashboards e relatórios para os utilizadores que não tem uma conta do Power BI. Este incorporar é também conhecido como *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) é um **Microsoft Azure** serviço que permite que fornecedores independentes de software (ISVs) e os desenvolvedores de rapidamente incorporar elementos visuais, relatórios e dashboards numa aplicação. Este tipo de incorporação é feito através de um modelo com tráfego limitado com base na capacidade, por hora.

![Fluxo de incorporação para incorporar para os seus clientes](media/embedding/powerbi-embed-flow.png)

O Power BI Embedded tem vantagens para um ISV e para os respetivos programadores e clientes. Por exemplo, um ISV pode começar a criar elementos visuais gratuitamente com o Power BI Desktop. Ao minimizarem os esforços de desenvolvimento de análise visual, ISVs alcançar um tempo de comercialização e destacarem-se da concorrência com experiências de dados diferenciadas. Os ISVs também podem optar por cobrar um valor adicional criaram com análise incorporada.

Com o Power BI Embedded, os seus clientes não precisam de ter conhecimentos sobre o Power BI. Pode usar dois métodos diferentes para criar uma aplicação incorporada:
- Conta do Power BI Pro 
- Service principal (Principal de serviço) 

A conta do Power BI Pro atua como conta de principal de seu aplicativo (Imagine isso como uma conta de proxy). Esta conta permite gerar tokens de incorporação que fornecem acesso a relatórios e dashboards do Power BI da sua aplicação.

O [principal de serviço](embed-service-principal.md) pode incorporar conteúdos do Power BI numa aplicação através de um token **só para aplicações**. Ele também permite gerar tokens de incorporação que fornecem acesso a relatórios e dashboards do Power BI da sua aplicação.

Os desenvolvedores que utilizam o Power BI Embedded podem gastar tempo focados na criação do seu aplicativo funcionalidade principal em vez de gastos tempo a desenvolver elementos visuais e análise. Rapidamente podem satisfazer as exigências de relatórios e dashboards do cliente e incorporá-los facilmente com totalmente documentadas APIs e SDKs. Ao ativar a exploração de dados de fácil navegação nas aplicações, os ISVs permitem que os clientes tomem decisões rápidas e baseadas em dados de acordo com o contexto a partir de qualquer dispositivo.

> [!IMPORTANT]
> Enquanto a incorporar exige que o serviço Power BI, os seus clientes não é necessário ter uma conta do Power BI para ver o conteúdo incorporado do seu aplicativo. 

Quando estiver pronto para passar à produção, terá de ser atribuída uma capacidade dedicada à sua área de trabalho de aplicação. O Power BI Embedded, no Microsoft Azure, disponibiliza [capacidades dedicadas](azure-pbie-create-capacity.md) para as suas aplicações.

Para incorporar os detalhes, consulte [como incorporar conteúdo do Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Próximos passos

Agora, pode tentar incorporar conteúdo do Power BI numa aplicação ou tentar incorporar conteúdo do Power BI para os seus clientes.

> [!div class="nextstepaction"]
> [Incorporar para a sua organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [O que é o Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Incorporar para os seus clientes](embed-sample-for-customers.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
