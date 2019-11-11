---
title: Gráficos de linhas no Power BI
description: Gráficos de linhas no Power BI
author: mihart
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e46aa05ac326b5c959da8a29329fa92f4aec0b4d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871064"
---
# <a name="line-charts-in-power-bi"></a>Gráficos de linhas no Power BI
Um gráfico de linhas é uma série de pontos de dados representados por pontos e ligados por linhas retas. Um gráfico de linhas pode ter uma ou várias linhas. Os gráficos de linhas têm um eixo X e um eixo Y. 

![gráfico de linhas simples](media/power-bi-line-charts/power-bi-line.png)

## <a name="create-a-line-chart"></a>Criar um gráfico de linhas
Estas instruções utilizam a aplicação Exemplo de Vendas e Marketing para criar um gráfico de linhas que apresenta as vendas deste ano por categoria. Para acompanhar, obtenha a aplicação de exemplo em appsource.com.

1. Comece numa página de relatório em branco. Se estiver a utilizar o serviço Power BI, garanta que abre o relatório na [Vista de Edição](../service-interact-with-a-report-in-editing-view.md).

2. No painel Campos, selecione **FactosDeVendas** \> **Total de unidades** e, em seguida, **Data** > **Mês**.  O Power BI cria um gráfico de colunas na tela do relatório.

    ![Selecionar a partir do painel Campos](media/power-bi-line-charts/power-bi-step1.png)

4. Converta-o num gráfico de linhas ao selecionar o modelo de gráfico de linhas no painel Visualizações. 

    ![converter num gráfico de linhas](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filtre o gráfico de linhas para mostrar os dados de 2012 a 2014. Se o painel Filtros estiver fechado, expanda-o agora. No painel Campos, selecione **Data** \> **Ano** e arraste para o painel Filtros. Largue sob o título **Filtros neste elemento visual**. 
     
    ![linha junto ao painel Campos](media/power-bi-line-charts/power-bi-year-filter.png)

    Altere **Filtros avançados** para **Filtros básicos** e selecione **2012**, **2013** e **2014**.

    ![Filtrar por Ano](media/power-bi-line-charts/power-bi-filter-year.png)

6. Opcionalmente, [ajuste o tamanho e a cor do texto do gráfico](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Aumentar o tamanho do tipo de letra e alterar o tipo de letra do eixo Y](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Adicionar outras linhas ao gráfico
Os gráficos de linhas podem ter várias linhas diferentes. Em alguns casos, os valores das linhas podem ser tão divergentes que não são adequadamente apresentados em conjunto. Vamos ver como adicionar outras linhas ao gráfico atual e, em seguida, saber como o formatar quando os valores representados pelas linhas são muito diferentes. 

### <a name="add-additional-lines"></a>Adicionar outras linhas
Em vez de apresentarmos o total de unidades para todas as regiões como uma única linha no gráfico, vamos dividi-lo por região. Adicione outras linhas ao arrastar **Área geográfica** > **Região** para o espaço de Legenda.

   ![Uma linha para cada região](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Utilizar dois eixos Y
E se pretender examinar o total de vendas e o total de unidades no mesmo gráfico? Os números de vendas são muito superiores aos números de unidades, o que torna o gráfico de linhas inutilizável. Na verdade, a linha vermelha que representa o total de unidades parece estar no zero.

   ![valores altamente divergentes](media/power-bi-line-charts/power-bi-diverging.png)

Para apresentar valores altamente divergentes num gráfico, utilize um gráfico de combinação. Pode saber tudo sobre os gráficos de combinação ao ler [Gráficos de combinação no Power BI](power-bi-visualization-combo-chart.md). No exemplo a seguir, podemos apresentar as vendas e o total de unidades em conjunto num gráfico ao adicionar um segundo eixo Y. 

   ![valores altamente divergentes](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como utilizar o painel Filtros, veja [Adicionar um filtro a um relatório](../power-bi-report-add-filter.md).

Selecionar um ponto de dados num gráfico de linhas realça e filtra de forma cruzada as outras visualizações na página de relatório e vice-versa. Para acompanhar, abra o separador **Quota de Mercado**.  

Num gráfico de linhas, um único ponto de dados é a intersecção de um ponto no eixo X e no eixo Y. Quando seleciona um ponto de dados, o Power BI adiciona marcadores que indicam que ponto (se existir uma única linha) ou pontos (se existirem duas ou mais linhas) são a origem para o realce e a filtragem cruzados dos outros elementos visuais na página de relatório. Se o seu elemento visual for muito denso, o Power BI irá selecionar o ponto mais próximo do local onde clica no elemento visual.

Neste exemplo, selecionámos um ponto de dados que abrange: julho de 2014, % da Participação no Mercado de Unidades R12 de 33,16 e % da Participação no Mercado de Unidades de 34,74.

![selecionar um único ponto de dados num gráfico de linhas](media/power-bi-line-charts/power-bi-single-select.png)

Repare como o gráfico de colunas apresenta um realce cruzado e o medidor apresenta uma filtragem cruzada.

Para gerir a forma como os gráficos se destacam e filtram entre si de forma cruzada, veja [Interações de visualização num relatório do Power BI](../service-reports-visual-interactions.md)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Um gráfico de uma linha não pode ter eixos Y duplos.  Em alternativa, terá de utilizar um gráfico de combinação.
* Nos exemplos acima, os gráficos foram formatados para aumentar o tamanho do tipo de letra, alterar a cor do tipo de letra, adicionar títulos dos eixos, centrar o título e a legenda do gráfico, começar ambos os eixos em zero e muito mais. O painel Formatação (ícone de rolo de pintura) tem um conjunto aparentemente interminável de opções para dar o aspeto que pretende aos seus gráficos. A melhor forma de aprender consiste em abrir o painel Formatação e explorar.

## <a name="next-steps"></a>Próximos passos

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


