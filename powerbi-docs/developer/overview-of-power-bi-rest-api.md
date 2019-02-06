---
title: O que posso fazer com a API Power BI
description: O que posso fazer com a API Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: d8cad602b178dd55184e00e2a318c374433b1a46
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762335"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>O que podem os programadores fazer com a API Power BI?

O Power BI apresenta dashboards interativos e que podem ser criados e atualizados a partir de várias origens de dados diferentes em tempo real. Utilize qualquer linguagem de programação que suporte chamadas REST para criar aplicações que se integram num dashboard do Power BI em tempo real. Também pode integrar mosaicos e relatórios do Power BI em aplicações.

Os programadores também podem criar as suas próprias visualizações de dados que podem ser utilizadas em relatórios e dashboards interativos.

Aqui estão algumas das coisas que pode fazer com as APIs do Power BI.

| **Para tal** | **Clique aqui** |
| --- | --- |
| Incorporar dashboards, relatórios e mosaicos para utilizadores do Power BI e utilizadores que não utilizam o Power BI (a aplicação é proprietária dos dados) |[Como incorporar os seus dashboards, relatórios e mosaicos do Power BI](embedding-content.md) |
| Expanda um fluxo de trabalho empresarial existente para enviar dados importantes por push para um dashboard do Power BI. |[Push data into a dashboard (Enviar dados por push para um dashboard)](walkthrough-push-data.md) |
| Autenticação no Power BI. |[Autenticação no Power BI](get-azuread-access-token.md) |
| Crie um elemento visual personalizado. |[Developing a Power BI custom visual](custom-visual-develop-tutorial.md) (Desenvolver um elemento visual personalizado do Power BI) |

> [!NOTE]
> As APIs do Power BI ainda se referem às áreas de trabalho de aplicações como grupos. Quaisquer referências a grupos significam que está a trabalhar com áreas de trabalho de aplicações.

## <a name="power-bi-developer-samples"></a>Exemplos para Programadores do Power BI

As amostras do Power BI Developer incluem itens para incorporar dashboards, relatórios e mosaicos.

[Amostras do Power BI Developer](https://github.com/Microsoft/PowerBI-Developer-Samples)

* Amostras dentro de **A Aplicação é Proprietária dos Dados** são para incorporar com utilizadores não Power BI.
* Amostras dentro de **O Utilizador é Proprietário dos Dados** são para incorporar com utilizadores Power BI.

## <a name="github-repositories"></a>Repositórios do GitHub

* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)
* [Elementos Visuais Personalizados](https://github.com/Microsoft/PowerBI-visuals)

## <a name="developer-tools"></a>Ferramentas de programador

Seguem-se as ferramentas que pode utilizar como ajuda no desenvolvimento de itens do Power BI.

Pode utilizar a [ferramenta de configuração de Incorporação](https://aka.ms/embedsetup) para começar rapidamente e transferir uma aplicação de exemplo sobre como incorporar conteúdos do Power BI.

Escolha a solução mais adequada para si:

* A solução [Incorporar para os seus clientes](embedding.md#embedding-for-your-customers) permite-lhe incorporar dashboards e relatórios para utilizadores que não têm uma conta para o Power BI. Execute a solução [Incorporar para os seus clientes](https://aka.ms/embedsetup/AppOwnsData).

* A solução [Incorporar para a sua organização](embedding.md#embedding-for-your-organization) permite-lhe alargar o serviço Power BI. Execute a solução [Incorporar a sua organização](https://aka.ms/embedsetup/UserOwnsData).

Para obter um exemplo completo de utilização da API de JavaScript, pode utilizar a [ferramenta Playground](https://microsoft.github.io/PowerBI-JavaScript/demo). Esta ferramenta proporciona uma forma rápida de testar vários tipos de exemplos do Power BI Embedded. Também pode obter mais informações sobre a API de JavaScript ao visitar a página [PowerBI-JavaScript wiki (wiki do PowerBI-JavaScript)](https://github.com/Microsoft/powerbi-javascript/wiki).

## <a name="push-data-into-power-bi"></a>Enviar dados por push para o Power BI

Pode utilizar a API do Power BI para enviar dados por push para um conjunto de dados. Esta funcionalidade permite-lhe adicionar uma linha a uma tabela num conjunto de dados. Os novos dados podem então ser refletidos nos mosaicos num dashboard e em elementos visuais dentro do seu relatório.

![Exemplo de dados emitidos via push](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Próximos passos

[Envio de dados por push para um conjunto de dados](walkthrough-push-data.md)  
[Developing a Power BI custom visual](custom-visual-develop-tutorial.md) (Desenvolver um elemento visual personalizado do Power BI)  
[Referência da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
