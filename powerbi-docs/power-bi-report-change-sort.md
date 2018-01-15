---
title: "Alterar a forma como um gráfico é ordenado num relatório do Power BI"
description: "Alterar a forma como um gráfico é ordenado num relatório do Power BI"
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
ms.date: 09/08/2017
ms.author: mihart
ms.openlocfilehash: 37161fab1e19e6ce00eb0f02c96b6e5cbdd60f18
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Alterar a forma como um gráfico é ordenado num relatório do Power BI
No Power BI, pode ordenar os gráficos alfabeticamente pelos nomes das categorias ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico está ordenado por nome de loja.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

Em vez disso, é fácil ordená-lo do valor de vendas mais alto ao mais baixo por metros quadrados.

1. Selecione as reticências (...) e selecione **Ordenar por Vendas Por Metro Quadrado**.
2. Se necessário, selecione o ícone de ordenação ![](media/power-bi-report-change-sort/sorticon.png) para alterar para **Descendente**.
   
   ![](media/power-bi-report-change-sort/sortby.gif)
   
   **NOTA**: nem todos os elementos visuais podem ser ordenados.  Por exemplo, os seguintes visuais não podem ser ordenados: Treemap, Mapa, Mapa de Manchas, Dispersão, Medidor, Cartão, Cartão de Linhas Múltiplas e Cascata.

## <a name="sorting-using-other-criteria"></a>Ordenar através de outros critérios
Às vezes, deseja ordenar o seu visual através de um campo diferente ou outros critérios.  Por exemplo, talvez queira ordenar por mês (e não por ordem alfabética) ou por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  

Em alguns casos, poderá conseguir ordenar o visual da forma que pretende (por exemplo, por mês).  Se não conseguir, poderá dever-se ao facto de o conjunto de dados associado ao relatório precisar de alguns ajustes. Seguem-se várias soluções:

* No Power BI Desktop, [utilize o separador Modelação das Ferramentas de Dados para ordenar por uma coluna diferente](desktop-sort-by-column.md).
* No Excel, se for o proprietário do conjunto de dados, adicione uma nova coluna que concatene o nome e o número do mês. Em seguida, atualize ou importe novamente o conjunto de dados para ver a nova coluna na área Campos.
* No Excel, certifique-se de que as colunas numéricas estão marcadas como "número inteiro" ou "decimal" e não como "texto".

## <a name="next-steps"></a>Passos seguintes
Mais sobre [Visualizações em relatórios do Power BI](power-bi-report-visualizations.md).

[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

