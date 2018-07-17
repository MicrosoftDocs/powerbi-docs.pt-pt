---
title: Incorporação com o Power BI
description: O Power BI oferece APIs para incorporar os seus dashboards e relatórios em aplicações.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 06/22/2018
ms.author: maghan
ms.openlocfilehash: 82a4c9c58567f5ace943363b7bed59fa744e85a5
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "36944106"
---
# <a name="embedding-with-power-bi"></a>Incorporação com o Power BI
O Power BI oferece APIs para incorporar os seus dashboards e relatórios em aplicações. As APIs do Power BI oferecem um conjunto consistente de capacidades e acesso às funcionalidades mais recentes do Power BI, como dashboards, gateways e áreas de trabalho de aplicações, ao incorporar conteúdos.

## <a name="a-single-api"></a>Uma API única
Existem dois cenários principais ao incorporar conteúdos do Power BI.  Incorporação para utilizadores na sua organização (que possuem licenças do Power BI) e incorporação para os seus utilizadores e clientes sem que necessitem de licenças do Power BI. A API REST do Power BI permite ambos os cenários. 

No caso de clientes e utilizadores sem licenças do Power BI, pode incorporar dashboards e relatórios na sua aplicação personalizada, utilizando a mesma API para servir a sua organização ou os seus clientes. Os seus clientes veem os dados que são geridos pela aplicação. No caso dos utilizadores do Power BI na sua organização, estes terão as opções adicionais para ver *os seus próprios dados* diretamente no Power BI ou no contexto da aplicação incorporada. Pode tirar total partido das APIs REST e JavaScript para as suas necessidades de incorporação.

Para ver um exemplo de como a incorporação funciona, consulte o [exemplo de incorporação de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Incorporar para a sua organização
A incorporação para a sua organização permite-lhe alargar o serviço Power BI. Isto requer que os utilizadores da sua aplicação iniciem sessão no serviço Power BI quando pretendem ver os seus conteúdos. Quando alguém na sua organização iniciar sessão, esta pessoa só terá acesso aos relatórios e dashboards de que é proprietária ou que foram partilhados com ela no serviço Power BI. 

*Alguns exemplos de incorporação para a sua organização incluem a aplicação Web interna, a peça Web do SharePoint Online e a [integração no Microsoft Teams (tem de ter direitos de administrador)](https://powerbi.microsoft.com/en-us/blog/power-bi-teams-up-with-microsoft-teams/).*

Para incorporação na sua organização, consulte o seguinte:

* [Integrar uma relatório numa aplicação](integrate-report.md)
* [Integrar um dashboard numa aplicação](integrate-dashboard.md)
* [Integrar um mosaico numa aplicação](integrate-tile.md)

Capacidades self-service, como editar, guardar, entre outras, estão disponíveis na [API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) na incorporação para utilizadores do Power BI.

Pode utilizar a [Ferramenta de experiência de inclusão para incorporar para a sua organização](https://aka.ms/embedsetup/UserOwnsData) e começar a utilizar e transferir rapidamente uma aplicação de exemplo que o orienta ao longo da integração de um relatório para a sua organização.

## <a name="embedding-for-your-customers"></a>Incorporar para os seus clientes
A incorporação para os seus clientes permite-lhe incorporar dashboards e relatórios para utilizadores que não têm uma conta para o Power BI. Os seus clientes não precisam de ter conhecimentos sobre o Power BI. É necessária, no mínimo, uma conta do Power BI Pro para criar uma aplicação incorporada. A conta do Power BI Pro atua como uma conta principal para a sua aplicação. É como se fosse uma conta proxy. A conta do Power BI Pro também permite gerar tokens de incorporação que fornecem acesso a dashboards e relatórios no serviço Power BI que são propriedade da/geridos pela sua aplicação. 

*Um exemplo de incorporação para os seus clientes é uma aplicação ISV vendida a outras empresas.*

![Fluxo de incorporação para incorporar para os seus clientes](media/embedding/powerbi-embed-flow.png)

Para incorporar dashboards, relatórios e mosaicos, utiliza-se a mesma API que se utiliza para incorporar na sua organização.

> [!IMPORTANT]
> Apesar de a incorporação ter uma dependência no serviço Power BI, não existe uma dependência no Power BI para os seus clientes. Os utilizadores não terão de se inscrever no Power BI para ver o conteúdo incorporado na aplicação.
> 

Quando estiver pronto para passar à produção, terá de ser atribuída uma capacidade à sua área de trabalho de aplicação. O Power BI Embedded, no Microsoft Azure, disponibiliza a capacidade de utilização com as suas aplicações.

Para obter detalhes sobre como incorporar, consulte [Como incorporar os seus dashboards, relatórios e mosaicos do Power BI](embedding-content.md).

Pode utilizar a [Ferramenta de experiência de inclusão para incorporar para os seus clientes](https://aka.ms/embedsetup/AppOwnsData) e começar a utilizar e transferir rapidamente uma aplicação de exemplo que o orienta ao longo da integração de um relatório na sua aplicação.

Se estava a utilizar o serviço Coleções de Áreas de Trabalho do Power BI no Power BI, consulte [Migrar conteúdos do serviço do Azure Coleções de Áreas de Trabalho do Power BI](migrate-from-powerbi-embedded.md) para obter informações sobre como migrar os seus conteúdos.

## <a name="next-steps"></a>Próximos passos
[Como incorporar os dashboards, relatórios e mosaicos do Power BI](embedding-content.md)  
[Como migrar conteúdos da coleção de áreas de trabalho do Power BI Embedded para o Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium – o que é?](../service-premium.md)  
[Repositório Git da API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Exemplo de incorporação de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Documento técnico de planeamento da capacidade de análise incorporada](https://aka.ms/pbiewhitepaper)  
[Documento técnico do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

