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
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 2f428095eb57c5358770f1d6d8572316d2b84c37
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Gráficos em anel no Power BI (Tutorial)
Um gráfico de anel é semelhante a um gráfico circular que mostra a relação das partes com um todo. A única diferença é que o centro está em branco e permite ter espaço para uma etiqueta ou ícone.

## <a name="create-a-doughnut-chart"></a>Criar um gráfico de anel
Para acompanhar, inicie sessão no Power BI e selecione **Obter Dados** \> **Exemplos** \> **Exemplo de Análise de Revenda** \> **Ligar**. 

1. No dashboard, selecione o mosaico **Arquivos Totais** para abrir o relatório "Exemplo de Análise de Revenda".
2. Selecione **Editar Relatório** para abrir o relatório na Vista de Edição.
3. [Adicione uma nova página de relatório](power-bi-report-add-page.md).
4. Crie um Gráfico de anel que mostre as vendas deste ano por categoria.
   
   * No painel **Campos**, selecione **Vendas** \> **Vendas do Ano Passado**.
   * Converta num gráfico de anel. Se as Vendas do Ano passado não estiverem na área **Valores**, arraste-as para aí.
     
       ![](media/power-bi-visualization-doughnut-charts/convertdonut.png)
   * Selecione **Item** \> **Categoria** para adicioná-lo à área **Legenda**. 
     
       ![](media/power-bi-visualization-doughnut-charts/doughnuttutorial.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* A soma dos valores do gráfico em anel deve somar até 100%.
* Muitas categorias são difíceis de ler e interpretar.
* Os gráficos em anel são melhor utilizados para comparar uma determinada secção com o todo, em vez de comparar secções individuais entre si. 

## <a name="next-steps"></a>Passos seguintes
[Relatórios no Power BI](service-reports.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

