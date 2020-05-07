---
title: Gráficos em anel no Power BI
description: Gráficos em anel no Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0e870163552e64594e574669ed8dea6937633282
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75757728"
---
# <a name="create-and-use-doughnut-charts-in-power-bi"></a>Criar e utilizar gráficos em anel no Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Um gráfico em anel é semelhante a um gráfico circular que mostra a relação das partes com um todo. A única diferença é que o centro está em branco e permite ter espaço para uma etiqueta ou ícone.

## <a name="prerequisite"></a>Pré-requisito

Este tutorial utiliza o [ficheiro PBIX do Exemplo de Análise de Revenda](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Na secção superior esquerda da barra de menus, selecione **Ficheiro** > **Abrir**.
   
2. Procure a sua cópia do **ficheiro PBIX do Exemplo de Análise de Revenda**

1. Abra o **Ficheiro PBIX do Exemplo de Análise de Revenda** na vista de relatório ![Captura de ecrã a mostrar o ícone da vista de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleção ![Captura de ecrã do separador amarelo.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.


## <a name="create-a-doughnut-chart"></a>Criar um gráfico de anel

1. Comece numa página de relatório em branco e, no painel Campos, selecione **Vendas** \> **Vendas do Ano Passado**.  
   
3. No painel Visualizações, selecione o ícone de gráfico em anel ![ícone de gráfico em anel](media/power-bi-visualization-doughnut-charts/power-bi-icon.png) para converter o gráfico de barras num gráfico em anel. Se as **Vendas do Ano Passado** não estiverem na área **Valores**, arraste-as para aí.
     
   ![Painel de visualização com gráfico em anel selecionado](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Selecione **Item** \> **Categoria** para adicioná-lo à área **Legenda**. 
     
    ![gráfico em anel junto ao painel Campos](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Opcionalmente, [ajuste o tamanho e a cor do texto do gráfico](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* A soma dos valores do gráfico em anel deve somar até 100%.
* Muitas categorias são difíceis de ler e interpretar.
* Os gráficos em anel são melhor utilizados para comparar uma determinada secção com o todo, em vez de comparar secções individuais entre si. 

## <a name="next-steps"></a>Próximas etapas
[Gráficos de funil no Power BI](power-bi-visualization-funnel-charts.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


