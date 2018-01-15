---
title: "Gráfico de área básico (Tutorial)"
description: "Tutorial: Gráfico de Área básico."
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
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 42e068b11c22c32f1a6736a6ca8f9020594fb40a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="basic-area-chart-tutorial"></a>Gráfico de área básico (Tutorial)
O gráfico de área básico (também conhecido como gráfico de área em camadas) baseia-se no gráfico de linhas. A área entre o eixo e a linha é preenchida com cores para indicar o volume. 

Os gráficos de área realçam a magnitude da alteração ao longo do tempo e podem ser utilizados para chamar a atenção para o valor total numa tendência. Por exemplo, os dados que representam o lucro ao longo do tempo podem ser representados num gráfico de área para realçar o lucro total.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>Quando utilizar um gráfico de área básico
Os gráficos de área básicos são uma ótima opção:

* para ver e comparar as tendências de volume em série de tempo 
* para as séries individuais que representam um conjunto contável fisicamente

## <a name="create-a-basic-area-chart"></a>Criar um gráfico de área básico
Para acompanhar, inicie sessão no Power BI e selecione **Obter Dados \> Exemplos \> Exemplo de Análise de Revenda**. 

1. No dashboard "Exemplo de Análise de Revenda", selecione o mosaico **Total de Lojas** para abrir o relatório "Exemplo de Análise de Revenda".
2. Selecione **Editar Relatório** para abrir o relatório na Vista de Edição.
3. Adicione uma nova página de relatório.
4. Crie um novo gráfico de área que mostre as vendas deste ano e do ano passado por mês.
   
   a.  No **painel Campos**, selecione **Vendas \> Vendas do Ano Passado** e **Vendas Deste Ano > Valor**.
   
   b.  Converta o gráfico num gráfico de área básico.    
   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Selecione **Hora \> Mês** para adicioná-lo à área **Eixo**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Para mostrar o gráfico por mês, selecione as reticências (canto superior direito do visual) e selecione **Ordenar por mês**.

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como utilizar o painel Filtros, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Para selecionar uma área, clique dentro dessa área ou ao longo da linha superior.  Os gráficos de área básicos não fazem filtragem cruzada das outras visualizações na página do relatório. No entanto, os gráficos de área são um alvo de filtragem cruzada acionado por outras visualizações na página do relatório.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Os gráficos de área básicos não são eficazes para comparar os valores devido à oclusão nas áreas em camadas. O Power BI utiliza transparência para indicar a sobreposição das áreas. No entanto, só funciona corretamente com duas ou três áreas diferentes. Quando precisar comparar tendências para mais de três medidas, tente usar os gráficos de linhas. Quando precisar de comparar volume para mais de três medidas, tente usar os gráficos de linhas.

## <a name="next-steps"></a>Passos seguintes
[Relatórios no Power BI](service-reports.md)  
[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)  
[Power BI - Conceitos Básicos](service-basic-concepts.md)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

