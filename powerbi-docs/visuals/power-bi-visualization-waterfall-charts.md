---
title: Gráficos de cascata no Power BI
description: Gráficos de cascata no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c9ad87d851f52db6cd2720c9e3bd5d4bb7b189a7
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67409056"
---
# <a name="waterfall-charts-in-power-bi"></a>Gráficos de cascata no Power BI

Os gráficos de cascata mostram um total em execução conforme o Power BI adiciona e subtrai valores. São úteis para entender como um valor inicial (como a receita líquida) é afetado por uma série de alterações positivas e negativas.

As colunas são codificadas para que possa verificar rapidamente os aumentos e as diminuições. Muitas vezes, as colunas de valores iniciais e finais [começam no ](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "eixo horizontal"), enquanto os valores intermediários são colunas flutuantes. Devido a esse estilo, os gráficos de cascata também são chamados de gráficos de ponte.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Quando utilizar um gráfico de cascata

Os gráficos de cascata são uma ótima opção:

* Quando existirem alterações na medida ao longo do tempo, uma série ou categorias diferentes.

* Para auditar as principais alterações que contribuem para o valor total.

* Para traçar o lucro anual da empresa ao mostrar várias origens de receita e chegar ao lucro total (ou perda).

* Para ilustrar o número de funcionários inicial e final da sua empresa num ano.

* Para visualizar a quantidade de dinheiro ganho e gasto em cada mês, e o saldo parcial da sua conta.

## <a name="prerequisites"></a>Pré-requisitos

* O serviço Power BI ou Power BI Desktop

* Relatório de Exemplo de Análise de Revenda

## <a name="get-the-retail-analysis-sample-report"></a>Obter o relatório de Exemplo de Análise de Revenda

Essas instruções utilizam o Exemplo de Análise de Revenda. A criação de uma visualização exige permissões de edição para o conjunto de dados e para o relatório. Felizmente, todos os exemplos do Power BI são editáveis. Se alguém partilhar um relatório consigo, não poderá criar visualizações nos relatórios. Para acompanhar, obtenha o [relatório de Exemplo de Análise de Revenda](../sample-datasets.md).

Depois de obter o conjunto de dados **Exemplo de Análise de Revenda**, pode começar a trabalhar.

## <a name="create-a-waterfall-chart"></a>Criar um gráfico de cascata

Vai criar um gráfico de cascata que mostra a variação de vendas (vendas estimadas vs. vendas reais) por mês.

1. Em **A Minha Área de Trabalho**, selecione **Conjuntos de dados** > **Criar um relatório**.

    ![Captura de ecrã de Conjuntos de dados > Criar um relatório.](media/power-bi-visualization-waterfall-charts/power-bi-create-a-report.png)

1. No painel **Campos**, selecione **Vendas**  > **Variação de Vendas Total**.

   ![Captura de ecrã de Vendas > Variação de Vendas Total e o elemento visual resultante.](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. Selecione o ícone de cascata ![Captura de ecrã do ícone de cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png) para converter o gráfico num treemap.

    Se a **Variação de Vendas Total** não estiver na área do **Eixo Y**, arraste-a para lá.

    ![Modelos de visualização](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)

1. Selecione **Altura** > **MêsFiscal** para o adicionar à caixa **Categoria**.

    ![cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Confirme que o Power BI ordenou o gráfico de cascata por ordem cronológica. Selecione as reticências (...) no canto superior direito do gráfico.

    Verifique se existe um indicador amarelo junto ao lado esquerdo das opções **Ordenação ascendente** e **MêsFiscal**

    ![Selecione ordenar por > MêsFiscal](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    Também pode observar os valores do Eixo X e ver se estão por ordem, de **Jan** o **Ago**.

    Aprofunde um pouco mais para ver o que contribui mais para as alterações mês a mês.

1. Arraste **Arquivo** > **Território** para o registo **Divisão**.

    ![Mostra Arquivo no registo Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Por predefinição, o Power BI adiciona os cinco principais contribuintes de aumentos ou diminuições por mês.

    ![Mostra Arquivo no registo Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    Apenas está interessado nos dois principais contribuintes.

1. No painel **Formatação**, selecione **Divisão** e defina **Máximo de divisões** como **2**.

    ![Formatação > Divisão](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    Uma análise rápida revela que as zonas de Ohio e Pensilvânia são os maiores contribuintes para o movimento, tanto negativo como positivo, no seu gráfico de cascata.

    ![gráfico de cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

    É uma conclusão interessante. Ohio e Pensilvânia têm um impacto tão significativo porque as vendas nestes dois territórios são muito superiores às dos outros territórios? Pode verificar.

1. Crie um mapa que apresente o valor de vendas deste ano e as vendas do último ano por território.

    ![grande plano do mapa em PA e Ohio](media/power-bi-visualization-waterfall-charts/power-bi-map.png)

    O mapa suporta a sua teoria. Mostra que estes dois territórios tiveram o valor mais elevado de vendas no ano passado (tamanho da bolha) e neste ano (sombreado da bolha).

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada

Para obter informações sobre como utilizar o painel **Filtros**, veja [Adicionar um filtro a um relatório na Vista de edição](../power-bi-report-add-filter.md).

Realçar uma coluna num gráfico de cascata faz uma filtragem cruzada nas outras visualizações na página do relatório, e vice-versa. No entanto, a coluna **Total** não aciona o destaque nem responde à filtragem cruzada.

## <a name="next-steps"></a>Próximos passos

* [Alterar a forma como os elementos visuais interagem num relatório do Power BI](../service-reports-visual-interactions.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
