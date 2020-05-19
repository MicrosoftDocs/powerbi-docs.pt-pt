---
title: Exemplos de elementos visuais do Power BI
description: Este artigo apresenta elementos visuais do Power BI de exemplo, incluindo segmentações de dados, mais de 20 tipos de gráficos, WebGL, elementos visuais R e scripts.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132950"
---
# <a name="samples-of-power-bi-visuals"></a>Exemplos de elementos visuais do Power BI

Pode transferir, utilizar e modificar estes elementos visuais do Power BI a partir do GitHub. Estes exemplos ilustram como lidar com situações comuns ao programar com o Power BI.

## <a name="slicers"></a>Segmentações

Uma segmentação de dados restringe a parte dos dados apresentada noutras visualizações num relatório. A segmentação de dados é uma de várias formas de filtrar dados no Power BI.

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Segmentação de Teclas](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Apresente botões de imagens ou de texto que funcionam como um filtro na tela noutros elementos visuais | [Segmentação de linha cronológica](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Seletor de intervalo de datas de gráfico que filtra por data | [Exemplo de segmentação de dados](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Demonstra a utilização da API de Filtragem Avançada

## <a name="charts"></a>Gráficos

Inspire-se na nossa galeria, incluindo gráficos de barras, gráficos circulares, Balão de Palavras e outros.

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [Gráfico Aster](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>Uma variante de um gráfico de anel padrão, que utiliza um segundo valor para gerar o ângulo de abertura | [Gráfico de marcadores ](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Um gráfico de barras com elementos visuais extra para proporcionar contexto útil para fins de controlo | [Cordas](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Um método gráfico que apresenta as relações entre os dados numa matriz
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [Gráfico de pontos](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Mostra a distribuição de frequências de uma forma visualmente apelativa | [Dual KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Efficiently visualizes two measures over time, showing their trend on a joint timeline | [Gráfico de Dispersão Avançada](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Melhorias no gráfico de dispersão existente
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [Gráfico de Força](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Diagrama de esquema de forças com um caminho curvo, o que é útil para mostrar ligações entre as entidades | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Um gráfico de barras que ilustra uma linha cronológica do projeto ou um agendamento com recursos | [Mapa de Calor de Tabela](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Compare dados fácil e intuitivamente, com recurso a cores numa tabela
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [Gráfico de histograma](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualizes the distribution of data over a continuous interval or certain time period | [Gráfico de Linhas e Pontos](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Um gráfico de linhas animado com pontos animados, que promovem o envolvimento do público com os dados | [Gráfico Mekko](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Uma mistura de gráfico de colunas 100% empilhadas e de gráfico de barras 100% empilhadas combinados numa única vista
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Multi KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Uma visualização Multi KPI avançada com um KPI chave, juntamente com múltiplos gráficos sparkline de dados de suporte | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Um Indicador KPI avançado com etiquetas e gráfico multilinhas para as variações, valores e datas atuais | [Matriz do Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Monitorize tabelas de indicadores equilibradas e um número ilimitado de métricas e KPIs numa lista compacta e fácil de ler
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [Gráfico de Pontos Temporais](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Este gráfico de linhas anotado com eventos-chave é perfeito para narrativas com dados| [Gráfico de radar](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Apresenta várias medidas desenhadas sobre um eixo de categorias, útil para comparar atributos | [Gráfico Sankey](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Diagrama de fluxo em que a largura da série é proporcional à quantidade do fluxo
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [Gráfico de fluxo](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Um gráfico de áreas empilhadas com interpolação suave, que frequentemente serve para apresentar os valores ao longo do tempo | [Gráfico circular de vários níveis](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Gráfico de anel de vários níveis para visualizar dados hierárquicos| [Gráfico de tornado](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Compare a importância relativa das variáveis entre dois grupos
 | <img src="media/samples/word-cloud.png" width="200">
 | [Nuvem de Palavras](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Create a fun visual from frequent text in your data

## <a name="webgl"></a>WebGL

O WebGL permite que o conteúdo Web utilize uma API baseada no OpenGL ES 2.0 para a composição 2D e 3D numa tela HTML.

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Mapa de Globo](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Desenhe localizações num mapa 3D interativo

## <a name="r-visuals"></a>Visuais R

Estes exemplos demonstram como pode aproveitar o poder analítico e visual dos elementos visuais R e dos scripts R.

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [Regras de associação](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Descubra relações entre dados, aparentemente, não relacionados com instruções “if-then” | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Localize grupos semelhantes nos dados com o algoritmo k-means | [Clustering com valores atípicos](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Localize grupos semelhantes e valores atípicos nos dados
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [Desenho de correlação](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Realça as variáveis mais correlacionadas numa tabela de dados | [Gráfico de árvore de decisões](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Diagrama esquemático em forma de árvore para determinar a probabilidade estatística com criação de partições recursivas | [Previsões TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Previsão de séries temporais para séries que têm várias sazonalidades com o modelo TBATS
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Previsão com ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Preveja valores futuros com base em dados históricos com a Média Móvel Integrada de Regressão Automática (ARIMA) | [Gráfico de funil](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Localize valores atípicos nos dados, com um gráfico de funil | [Deteção de valores atípicos](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Localize valores atípicos nos dados com o método e gráfico adequado
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [Gráfico de curva polinomial](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Visualize e compreenda dados irrelevantes | [Gráfico de decomposição de série temporal](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Compreenda os componentes da série temporal com a “decomposição de Tendência e Sazonal com Loess" | [Gráfico de séries temporal e previsão](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Using exponential smoothing model to predict future values based on previously observed values

## <a name="next-steps"></a>Próximos passos

Para experimentar a criação de elementos visuais do Power BI, veja [Tutorial: desenvolver um elemento visual do Power BI](custom-visual-develop-tutorial.md).
