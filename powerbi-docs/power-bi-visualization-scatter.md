---
title: "Gráficos de dispersão no Power BI (Tutorial)"
description: "Tutorial: Gráficos de dispersão no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: PVcfPoVE3Ys
qualityfocus: identified
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/23/2017
ms.author: mihart
ms.openlocfilehash: 44c248d1a99a10c69b3fb7c78e68320fdc5cd2b2
ms.sourcegitcommit: 259d7689bcb1683d4d63a245a9b02becea072139
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="scatter-charts-and-bubble-charts-in-power-bi-tutorial"></a>Gráficos de dispersão e de bolhas no Power BI (Tutorial)
Um gráfico de dispersão tem sempre dois eixos de valor para mostrar um conjunto de dados numéricos num eixo horizontal e outro conjunto de valores numéricos num eixo vertical. O gráfico mostra pontos na intersecção de um valor numérico de x e y e combina estes valores em pontos de dados individuais. Estes pontos de dados podem ser distribuídos de forma uniforme ou não pelo eixo horizontal, consoante os dados.

Os gráficos de bolhas substituem os pontos de dados por bolhas, sendo que o *tamanho* das bolhas representa uma dimensão adicional dos dados.

![](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

## <a name="when-to-use-a-scatter-chart-or-bubble-chart"></a>Quando usar um gráfico de dispersão ou um gráfico de bolhas
### <a name="scatter-charts-are-a-great-choice"></a>Os gráficos de dispersão são uma ótima opção:
* para mostrar as relações entre dois (dispersão) ou três (bolhas) valores **numéricos**.
* Para representar dois grupos de números como uma série de coordenadas xy.
* Em vez de um gráfico de linhas quando quiser alterar a escala do eixo horizontal    
* Para transformar o eixo horizontal numa escala logarítmica.
* Para mostrar os dados da folha de cálculo que incluem pares ou conjuntos de valores agrupados. Num gráfico de dispersão, pode ajustar as escalas independentes dos eixos para revelar mais informações sobre os valores agrupados.
* Para mostrar padrões em grandes conjuntos de dados, por exemplo, ao mostrar tendências lineares ou não lineares, clusters e valores atípicos.
* para comparar grandes números de pontos de dados sem considerar o tempo    Quanto mais dados incluir num gráfico de dispersão, melhores serão as comparações que poderá fazer.

### <a name="bubble-charts-are-a-great-choice"></a>Os gráficos de bolhas são uma ótima opção:
* Se os dados tiverem três séries de dados que contêm um conjunto de valores cada um.
* Para apresentar dados financeiros.  Os diferentes tamanhos de bolha são úteis para destacar visualmente os valores específicos.
* Para utilizar com quadrantes.

## <a name="create-a-scatter-chart"></a>Criar um gráfico de dispersão
Assista a este vídeo para ver o Will a criar um gráfico de dispersão e, em seguida, siga os passos abaixo para criar um sozinho.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Essas instruções utilizam o Exemplo de Análise de Revenda. Para acompanhar, [transfira o exemplo](sample-datasets.md) do serviço do Power BI (app.powerbi.com) ou o Power BI Desktop.   

1. Comece numa [página de relatório em branco](power-bi-report-add-page.md) e selecione os campos **Vendas** \> **Vendas por Metro Quadrado** e **Vendas**  >  **% da Variação do Total de Vendas**. Se estiver a utilizar o serviço Power BI, garanta que abre o relatório na [Vista de edição](service-interact-with-a-report-in-editing-view.md).
 
2. No painel Campos, selecione **Distrito > Distrito**.
   
    ![](media/power-bi-visualization-scatter/power-bi-bar-chart.png)
4. Converter num gráfico de dispersão. No painel Visualização, selecione o ícone do Gráfico de dispersão.
   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_icon.png).
5. Arraste **Distrito** de **Detalhes** para **Legenda**.
   
    ![](media/power-bi-visualization-scatter/power-bi-scatter.png)

Agora temos um gráfico de dispersão que traça a % da Variação do Total de Vendas no eixo Y e as Vendas por Pé Quadrado no eixo X.  As cores do ponto de dados representam as regiões.  Agora, vamos adicionar uma terceira dimensão.

## <a name="create-a-bubble-chart"></a>Criar um gráfico de bolhas
1. No painel Campos, arraste **Vendas** > **Vendas Deste Ano** > **Valor** para a área **Tamanho**. 
   
   ![](media/power-bi-visualization-scatter/power-bi-bubble.png)
2. Coloque o cursor sobre uma bolha.  O tamanho da bolha reflete o valor das **Vendas Deste Ano**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)
3. Opcionalmente, [formate as cores de visualização, rótulos, títulos, fundo e muito mais](service-getting-started-with-color-formatting-and-axis-properties.md).

## <a name="accessibility"></a>Acessibilidade

Pode tornar o seu gráfico de dispersão ou gráfico de bolhas mais acessível para as pessoas portadoras de deficiências ao utilizar as *Formas de marcador*. 

Para seleciona uma forma do marcador, selecione a secção **Formato** no painel **Visualizações**, expanda a secção **Formas** e selecione uma forma de marcador.

![Forma de marcador](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e Resolução de Problemas
### <a name="your-scatter-chart-has-only-one-data-point"></a>**O gráfico de dispersão tem apenas um ponto de dados**
O gráfico de dispersão contém apenas um ponto de dados que agrega todos os valores nos eixos X e Y?  Ou talvez agregue todos os valores numa única linha horizontal ou vertical?

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Adicione um campo à área **Detalhes** para informar o Power BI sobre como agrupar os valores. O campo tem de ser exclusivo para cada ponto que quer representar.  
Como um número de linha simples ou campo de ID:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Ou então, se não tiver isto nos dados, pode criar um campo que concatena os valores X e Y juntos em algo exclusivo por ponto:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Para criar um novo campo [utilize o Editor de Consultas do Power BI Desktop para adicionar uma Coluna de Índice](desktop-add-custom-column.md) ao conjunto de dados.  Em seguida, adicione esta coluna à área **Detalhes** da visualização.

## <a name="next-steps"></a>Passos seguintes
 [Visualization types in Power BI (Tipos de visualização no Power BI)](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Experimente - é gratuito!](https://powerbi.com/)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

