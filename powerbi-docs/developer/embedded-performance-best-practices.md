---
title: Melhores práticas para o desempenho do Power BI Embedded
description: Este artigo fornece recomendações de melhores práticas para a análise incorporada
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: d0f4ca29e30e5f6e6176f036dc535601eb580471
ms.sourcegitcommit: 298db44200b78b1281b3ae6dfe7cce7a89865ec9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/13/2018
ms.locfileid: "53329884"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Melhores práticas para o desempenho do Power BI Embedded

Este artigo fornece recomendações para uma composição mais rápida de relatórios, dashboards e mosaicos na sua aplicação

## <a name="embed-parameters"></a>Parâmetros de incorporação

O método powerbi.embed() recebe poucos parâmetros para incorporar um relatório, dashboard ou mosaico. Estes parâmetros afetam o desempenho.

### <a name="embed-url"></a>URL de Incorporação

Evite gerar o seu próprio URL de incorporação. Em vez disso, certifique-se de que obtém o URL de Incorporação ao chamar a API [Obter relatórios](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Freports%2Fgetreportsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=22lkqRM2w1MQfrM8dooedaPqqIU8PufTq9TT4VDzRo0%3D&reserved=0), [Obter dashboards](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgetdashboardsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=nfWRgbSoXVF42Rg%2Ba9491u19uksXp%2FAyz%2Fa%2Ba7%2FCtdA%3D&reserved=0) ou [Obter mosaicos](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgettilesingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256178318&sdata=LgZ27TynNpqQJDrb3aHWGQXIS%2FzichAO9De5M2uhF1Q%3D&reserved=0). Adicionámos um novo parâmetro ao URL, chamado **_config_**, que é utilizado para melhorar o desempenho.

### <a name="permissions"></a>Permissões

Conceda permissões **Ver** se não tencionar incorporar um relatório no **Modo de Edição**. Desta forma, o código de incorporação não inicializa os componentes, que são utilizados para o Modo de Edição.

### <a name="filters-bookmarks-and-slicers"></a>Filtros, marcadores e segmentações

Normalmente, os elementos visuais de relatórios são guardados com dados em cache. Os dados em cache são utilizados para fornecer o desempenho percetível. Os relatórios compõem os dados em cache enquanto as consultas são executadas. Se forem fornecidos filtros, marcadores ou segmentações, os dados em cache não são relevantes. Nesse caso, os elementos visuais só são compostos após a execução da consulta do elemento visual.

Se incorporar relatórios com os mesmos filtros, para evitar passar uma lista de filtros na configuração de carregamento, guarde o relatório com os filtros já aplicados.

## <a name="preload"></a>Preload

Utilize a API JavaScript *preload* para melhorar o desempenho para o utilizador final.
Powerbi.preload() transfere ficheiros CSS, JavaScript e outros artefactos, que são utilizados posteriormente para incorporar num relatório.

Chame a API preload se não pretender incorporar o relatório de imediato. Por exemplo, se incorporar um relatório no clique de um botão, é aconselhável chamar a API preload quando a página anterior for carregada. Assim, quando o utilizador da aplicação clicar no botão, a composição será mais rápida.

## <a name="measure-performance"></a>Medição do desempenho

Para medir o desempenho, utilize:

1. Loaded: tempo até o relatório ser inicializado (o utilizador não vê o ícone de progresso).
2. Rendered: tempo até o relatório ser completamente composto com os dados reais. O evento Rendered é acionado sempre que o relatório é composto novamente (ou seja, após aplicar filtros). Para medir um relatório primeiro, certifique-se de que faz os cálculos no primeiro evento gerado.

Os dados em cache são compostos quando estão disponíveis, mas ainda não temos um evento para estes dados.

## <a name="update-tools-and-sdk-packages"></a>Ferramentas de atualização e pacotes SDK

Mantenha as ferramentas e os pacotes SDK atualizados.

* Utilize sempre a versão mais recente do [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

* Instale a versão mais recente do [cliente SDK do Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Continuaremos a lançar melhorias, por isso volte de vez em quando.

* Pacotes para instalar:
    * Pacote Npm: powerbi-client
    * Pacote NuGet: Microsoft.PowerBI.JavaScript

> [!Note]
> Lembre-se de que o tempo de carregamento depende principalmente dos elementos relevantes para o relatório e dos próprios dados, por exemplo, o número de elementos visuais, o tamanho dos dados e a complexidade das consultas e das medidas calculadas. Siga as [melhores práticas](../power-bi-reports-performance.md) para melhorar o tempo de carregamento dos relatórios.

## <a name="next-steps"></a>Próximos passos

* [Desempenho dos relatórios](../power-bi-reports-performance.md)
* [Como resolver problemas do Power BI Embedded](embedded-troubleshoot.md)
* [FAQ do Power BI Embedded](embedded-faq.md)
