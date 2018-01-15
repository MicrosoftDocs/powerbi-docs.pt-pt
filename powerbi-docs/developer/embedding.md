---
title: "Incorporação com o Power BI"
description: "O Power BI oferece APIs para incorporar os seus dashboards e relatórios em aplicações."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: 36eb4231b6b3d3278d571722bde731051ffdf05e
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="embedding-with-power-bi"></a>Incorporação com o Power BI
O Power BI oferece APIs para incorporar os seus dashboards e relatórios em aplicações. As APIs do Power BI oferecem um conjunto consistente de capacidades e acesso às funcionalidades mais recentes do Power BI, como dashboards, gateways e áreas de trabalho de aplicações, ao incorporar os seus conteúdos.

## <a name="a-single-api"></a>Uma API única
Existem dois cenários principais ao incorporar conteúdos do Power BI. Incorporação para a sua organização e incorporação para os seus clientes. A API REST do Power BI permite ambos os cenários. Isto irá permitir-lhe a incorporação de dashboards e relatórios na sua aplicação personalizada, utilizando a mesma API para servir a sua organização ou os seus clientes. Pode tirar total partido das APIs REST e JavaScript para as suas necessidades de incorporação.

Para ver um exemplo de como a incorporação funciona, consulte o [exemplo de incorporação de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Incorporar para a sua organização
A incorporação para a sua organização permite-lhe alargar o serviço Power BI. Isto requer que o utilizador final da sua aplicação inicie sessão no serviço Power BI quando pretender ver os seus conteúdos. Quando alguém na sua organização iniciar sessão, esta pessoa só terá acesso aos relatórios e dashboards que foram partilhados com os mesmos no serviço Power BI. 

*Alguns exemplos de incorporação para a sua organização incluem a aplicação Web interna, a peça Web do SharePoint Online e a integração no Microsoft Teams.*

Para incorporação na sua organização, consulte o seguinte:

* [Integrar um dashboard numa aplicação](integrate-dashboard.md)
* [Integrar um mosaico numa aplicação](integrate-tile.md)
* [Integrar uma relatório numa aplicação](integrate-report.md)

Capacidades self-service, como editar, guardar, entre outras, estão disponíveis na [API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) na incorporação para utilizadores do Power BI.

## <a name="embedding-for-your-customers"></a>Incorporar para os seus clientes
A incorporação para os seus clientes permite-lhe incorporar dashboards e relatórios para utilizadores que não têm uma conta para o Power BI. Os seus clientes não precisam de ter conhecimentos sobre o Power BI. É necessária pelo menos uma conta do Power BI Pro. A conta do Power BI Pro atua como uma conta principal para a sua aplicação. É como se fosse uma conta proxy. A conta do Power BI Pro também permite gerar tokens de incorporação que fornecem acesso a dashboards e relatórios no serviço Power BI. 

*Um exemplo de incorporação para os seus clientes é uma aplicação ISV vendida a outras empresas.*

![Fluxo de incorporação para incorporar para os seus clientes](media/embedding/powerbi-embed-flow.png)

Para incorporar dashboards, relatórios e mosaicos, utiliza-se a mesma API que se utiliza para incorporar na sua organização.

> [!IMPORTANT]
> Apesar de a incorporação ter uma dependência no serviço Power BI, não existe uma dependência do Power BI para os seus clientes. Os utilizadores não terão de se inscrever no Power BI para ver o conteúdo incorporado na aplicação.
> 
> 

Quando estiver pronto para passar à produção, terá de ser atribuída uma capacidade à sua área de trabalho de aplicação. O Power BI Embedded, no Microsoft Azure, disponibiliza a capacidade de utilização com as suas aplicações.

Para obter detalhes sobre como incorporar, consulte [Como incorporar os seus dashboards, relatórios e mosaicos do Power BI](embedding-content.md).

Se estava a utilizar o serviço Coleções de Áreas de Trabalho do Power BI no Power BI, consulte [Migrar conteúdos do serviço do Azure Coleções de Áreas de Trabalho do Power BI](migrate-from-powerbi-embedded.md) para obter informações sobre como migrar os seus conteúdos.

## <a name="next-steps"></a>Próximos passos
[Como incorporar os dashboards, relatórios e mosaicos do Power BI](embedding-content.md)  
[Como migrar conteúdo da coleção de áreas de trabalho do Power BI Embedded para o Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium – o que é?](../service-premium.md)  
[Repositório Git da API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Repositório Git C# do Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Exemplo de incorporação de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Documento técnico de planeamento da capacidade de análise incorporada](https://aka.ms/pbiewhitepaper)  
[Documento técnico do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

