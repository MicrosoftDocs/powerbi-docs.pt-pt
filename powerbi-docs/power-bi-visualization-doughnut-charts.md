---
title: "Gráficos em anel no Power BI (Tutorial)"
description: "Tutorial: gráficos em anel no Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 12/23/2017
ms.author: mihart
ms.openlocfilehash: f3401fac7b0e7e6b5b5404a5a837822772e1d70f
ms.sourcegitcommit: 74fbbca81a056dda19b3647ae058005aba5296f5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/03/2018
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Gráficos em anel no Power BI (Tutorial)
Um gráfico em anel é semelhante a um gráfico circular que mostra a relação das partes com um todo. A única diferença é que o centro está em branco e permite ter espaço para uma etiqueta ou ícone.

## <a name="create-a-doughnut-chart"></a>Criar um gráfico em anel
Estas instruções utilizam o Exemplo de Análise de Revenda para criar um gráfico em anel que apresenta as vendas deste ano por categoria. Para acompanhar, [transfira o exemplo](sample-datasets.md) do serviço do Power BI (app.powerbi.com) ou o Power BI Desktop.

1. Comece numa [página de relatório em branco ](power-bi-report-add-page.md) e selecione o campo **SalesStage** \> **Fase de Vendas**. Se estiver a utilizar o serviço Power BI, garanta que abre o relatório na [Vista de edição](service-interact-with-a-report-in-editing-view.md).

2. No painel Campos, selecione **Vendas** \> **Vendas do Ano Passado**.  
   
3. No painel Visualizações, selecione o ícone de gráfico em anel ![ícone de gráfico em anel]() para converter o gráfico de barras num gráfico em anel. Se as **Vendas do Ano Passado** não estiverem na área **Valores**, arraste-as para aí.
     
   ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Selecione **Item** \> **Categoria** para adicioná-lo à área **Legenda**. 
     
    ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Opcionalmente, [ajuste o tamanho e a cor do texto do gráfico](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* A soma dos valores do gráfico em anel deve somar até 100%.
* Muitas categorias são difíceis de ler e interpretar.
* Os gráficos em anel são melhor utilizados para comparar uma determinada secção com o todo, em vez de comparar secções individuais entre si. 

## <a name="next-steps"></a>Passos seguintes
[Relatórios no Power BI](service-reports.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
