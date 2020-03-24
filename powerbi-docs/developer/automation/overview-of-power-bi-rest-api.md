---
title: O que posso fazer com a API Power BI
description: O que posso fazer com a API Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 03/25/2019
ms.openlocfilehash: 1a74d856ad46dc6843546919aa4234dc86d2be5c
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488438"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>O que podem os programadores fazer com a API Power BI?

A API REST do Power BI permite-lhe criar aplicações que integram mosaicos, dashboards e relatórios do Power BI.

Com a API REST do Power BI, pode realizar tarefas de gestão em objetos do Power BI como relatórios, conjuntos de dados e áreas de trabalho.

Aqui estão algumas das coisas que pode fazer com as APIs do Power BI.

| **Para saber mais** | **Veja estas informações** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Incorporar relatórios, dashboards e mosaicos para utilizadores do Power BI e pessoas que não utilizam o Power BI. | [Como incorporar os seus dashboards, relatórios e mosaicos do Power BI](../embedded/embed-sample-for-customers.md) |
| Realize tarefas de gestão em objetos do Power BI. | [Referência da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) |
| Expanda um fluxo de trabalho empresarial existente para enviar dados importantes por push para um dashboard do Power BI. | [Push data into a dashboard ](walkthrough-push-data.md)(Emitir dados para um dashboard) |
| Autenticação no Power BI. | [Autenticar-se no Power BI ](../embedded/get-azuread-access-token.md) |

> [!NOTE]
> As APIs Power BI ainda se referem às áreas de trabalho como grupos. Quaisquer referências a grupos significam que está a trabalhar com áreas de trabalho.

## <a name="api-developer-tools"></a>Ferramentas de Programação da API

| Ferramentas | Descrição |  |  |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| [Ferramenta Playground](https://microsoft.github.io/PowerBI-JavaScript/demo) | Experimente exemplos completos sobre a utilização das APIs de JavaScript do Power BI. Esta ferramenta também proporciona uma forma rápida de testar vários tipos de exemplos do Power BI Embedded. |  |  |
| [Wiki de JavaScript do Power BI](https://github.com/Microsoft/powerbi-javascript/wiki) | Para obter mais informações sobre as APIs de JavaScript do Power BI. |  |  |
| [Postman](https://www.getpostman.com/) | Execute pedidos, testes, depurações, monitorizações, testes automatizados e mais. |

## <a name="push-data-into-power-bi"></a>Enviar dados por push para o Power BI

Pode utilizar a API do Power BI para [enviar dados por push para um conjunto de dados](walkthrough-push-data.md). Esta funcionalidade permite-lhe adicionar uma linha a uma tabela num conjunto de dados. Os novos dados são então refletidos nos mosaicos num dashboard e em elementos visuais do seu relatório.

![Exemplo de dados emitidos via push](media/overview-of-power-bi-rest-api/powerbi-push-data.png)

## <a name="github-repositories"></a>Repositórios do GitHub

* [Amostras do Power BI Developer](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [API de JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)

## <a name="next-steps"></a>Próximos Passos

* [Envio de dados por push para um conjunto de dados](walkthrough-push-data.md)
* [Desenvolver um elemento visual do Power BI](../visuals/custom-visual-develop-tutorial.md)
* [Referência da API REST do Power BI](rest-api-reference.md)
* [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)