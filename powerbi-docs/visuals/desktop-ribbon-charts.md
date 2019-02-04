---
title: Utilizar gráficos de friso no Power BI
description: Criar e consumir gráficos de friso no serviço Power BI e no Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 08a2de32b092ba24b66ddd9f173be1eaea8819ab
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/31/2019
ms.locfileid: "55429872"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Utilizar gráficos de friso no Power BI
Pode utilizar gráficos de friso para visualizar dados e, rapidamente, descobrir que categoria de dados tem a classificação mais elevada (maior valor). Os gráficos de friso são uma forma eficaz de mostrar as alterações de classificação, com a classificação (valor) mais elevada sempre mostrada na parte superior de cada período temporal. 

![gráfico do friso](media/desktop-ribbon-charts/ribbon-charts_01.png)

## <a name="create-a-ribbon-chart"></a>Criar um gráfico de friso
Para acompanhar, abra o [exemplo de relatório Análise de revenda](../sample-retail-analysis.md). 

1. Para criar um gráfico de friso, selecione **Gráfico de friso** no painel **Visualizações**.

    ![modelos de visualização](media/desktop-ribbon-charts/ribbon-charts_02.png)

    Os gráficos de friso ligam uma categoria de dados ao longo do período de tempo visualizado através de frisos, permitindo-lhe ver qual a classificação de uma determinada categoria ao longo do eixo X do gráfico (que é normalmente a linha cronológica).

2. Selecione os campos para **Eixo**, **Legenda** e **Valor**.  Neste exemplo, selecionámos o seguinte: **Date** (Data), **Category** (Categoria) e **This year sales** (Vendas deste ano).  

    ![campos selecionados](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Como o conjunto de dados contém somente dados de um ano, também removemos o campo **Year** (Ano) do **Eixo**. 

3. O gráfico do friso mostra a classificação dos restantes meses. Observe como a classificação muda ao longo do tempo.  Por exemplo, a categoria Home (Casa) passa da terceira para a quarta posição e regressa novamente à terceira posição. A categoria Juniors (Júnior) mudou da terceira para a quinta posição em julho. 

    ![gráfico do friso](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Formatar um gráfico de friso
Ao criar um gráfico de friso, tem opções de formatação disponíveis na secção **Formatar** do painel **Visualizações**. As opções de formatação para gráficos de friso são semelhantes às opções para um gráfico de colunas empilhadas, com opções de formatação adicionais específicas dos frisos.

![modelo de friso no painel Visualização](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Estas opções de formatação para gráficos de friso permitem-lhe fazer ajustes.

* **Espaçamento** permite-lhe ajustar a quantidade de espaço entre frisos. O número corresponde à percentagem da altura máxima da coluna.
* **Coincidir cor de série** permite-lhe fazer corresponder a cor dos frisos à cor da série. Quando está definido como **desativado**, os frisos estão cinzentos.
* **Transparência** especifica o grau de transparência dos frisos, com uma predefinição de 30.
* **Limite** permite-lhe colocar um limite escuro nas partes superior e inferior dos frisos. Por predefinição, os frisos estão desativados.

Visto que o gráfico do friso não possui etiquetas do eixo Y, poderá adicionar etiquetas de dados. No painel Formatação, selecione **Etiquetas de dados**. 

![opções de formatação para etiquetas de dados](media/desktop-ribbon-charts/power-bi-labels.png)

Defina as opções de formatação das suas etiquetas de dados.  Neste exemplo, definimos a cor do texto para branco, as casas decimais para zero e as unidades de apresentação para milhares. 

![modelo de friso no painel Visualização](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Passos seguintes

[Gráficos de dispersão e de bolhas no Power BI](power-bi-visualization-scatter.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)