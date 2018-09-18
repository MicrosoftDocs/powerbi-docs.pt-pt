---
title: Alterar a forma como um gráfico é ordenado num relatório do Power BI
description: Alterar a forma como um gráfico é ordenado num relatório do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 89891ead8eda1b8de4c7be943af2a9e9e98314c5
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44726093"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Alterar a forma como um gráfico é ordenado num relatório do Power BI
Num relatório do Power BI, pode ordenar alfabeticamente a maioria das visualizações pelos nomes das categorias no gráfico ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico está ordenado por nome de loja.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

É fácil alterar a ordenação de uma categoria (nome de arquivo) para um valor (vendas por metro quadrado).

1. Selecione as reticências (...) e selecione **Ordenar por Vendas Por Metro Quadrado**.
2. Se necessário, selecione o ícone de ordenação ![](media/power-bi-report-change-sort/sorticon.png) para alterar para **Descendente**.

   ![](media/power-bi-report-change-sort/sortby.gif)

   **NOTA**: nem todos os elementos visuais podem ser ordenados.  Por exemplo, os seguintes visuais não podem ser ordenados: Treemap, Mapa, Mapa de Manchas, Dispersão, Medidor, Cartão, Cartão de Linhas Múltiplas e Cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Guardar as alterações feitas à sequência de ordenação
Os relatórios do Power BI mantêm os filtros, as segmentações de dados, a ordenação e outras alterações que fizer à vista de dados. Por isso, se sair de um relatório e regressar mais tarde, as alterações são guardadas.  Se quiser reverter as alterações para as definições do autor do relatório, selecione **Repor para predefinição** na barra de menus superior. 

![Ordenação persistente](media/power-bi-report-change-sort/power-bi-reset-to-default.png)

Se, no entanto, o botão **Repor para predefinição** for apresentado a cinzento, isso significa que o autor do relatório desativou a capacidade de guardar (fazer persistir) as suas alterações.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordenar através de outros critérios
Às vezes, deseja ordenar o seu visual através de um campo diferente ou outros critérios.  Por exemplo, talvez queira ordenar por mês (e não por ordem alfabética) ou por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  

Em alguns casos, poderá conseguir ordenar o visual da forma que pretende (por exemplo, por mês).  Se não conseguir, poderá dever-se ao facto de o conjunto de dados associado ao relatório precisar de alguns ajustes. Seguem-se várias soluções:

* No Power BI Desktop, [utilize o separador Modelação das Ferramentas de Dados para ordenar por uma coluna diferente](desktop-sort-by-column.md).
* No Excel, se for o proprietário do conjunto de dados, adicione uma nova coluna que concatene o nome e o número do mês. Em seguida, atualize ou importe novamente o conjunto de dados para ver a nova coluna na área Campos.
* No Excel, certifique-se de que as colunas numéricas estão marcadas como "número inteiro" ou "decimal" e não como "texto".

## <a name="next-steps"></a>Passos seguintes
Mais sobre [Visualizações em relatórios do Power BI](visuals/power-bi-report-visualizations.md).

[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
