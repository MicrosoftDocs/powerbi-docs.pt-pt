---
title: Alterar a forma como um gráfico é ordenado num relatório
description: Alterar a forma como um gráfico é ordenado num relatório do Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 98a91b0651e7a357f0ba0462f6ba8734c64ab162
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302731"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Alterar a forma como um gráfico é ordenado num relatório do Power BI
Num relatório do Power BI, pode ordenar alfabeticamente a maioria das visualizações pelos nomes das categorias no gráfico ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico está ordenado pela categoria **nome de loja**.

![gráfico de barras ordenado alfabeticamente pelo eixo X](media/end-user-change-sort/pbi_chartsortcategory.png)

É fácil alterar a ordenação de uma categoria (nome de arquivo) para um valor (vendas por metro quadrado).

1. Selecione as reticências (...) e selecione **Ordenar por > Vendas Por Metro Quadrado**.
2. Se necessário, selecione as reticências novamente e selecione **Ordenação descendente**.

   ![vídeo que mostra a ordem de seleção ascendente e descendente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nem todos os elementos visuais podem ser ordenados. Por exemplo, os seguintes elementos visuais não podem ser ordenados: treemap, mapa, mapa de manchas, dispersão, medidor, cartão, cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Guardar as alterações feitas à sequência de ordenação
Os relatórios do Power BI mantêm os filtros, as segmentações de dados, a ordenação e outras alterações que fizer à vista de dados. Por isso, se sair de um relatório e regressar mais tarde, as alterações são guardadas.  Se quiser reverter as alterações para as definições do designer do relatório, selecione **Repor para predefinição** na barra de menus superior. 

![Ordenação persistente](media/end-user-change-sort/power-bi-reset.png)

Se, no entanto, o botão **Repor para predefinição** for apresentado a cinzento, isso significa que o designer do relatório desativou a capacidade de guardar (fazer persistir) as suas alterações.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordenar através de outros critérios
Às vezes, deseja ordenar o seu visual através de um campo diferente ou outros critérios.  Por exemplo, talvez queira ordenar por mês (e não por ordem alfabética) ou por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  

Em alguns casos, poderá conseguir ordenar o visual da forma que pretende (por exemplo, por mês).  Se não conseguir, poderá dever-se ao facto de o conjunto de dados associado ao relatório precisar de alguns ajustes. Peça ao designer do relatório para atualizar o conjunto de dados.

## <a name="next-steps"></a>Próximos passos
Mais sobre [Visualizações em relatórios do Power BI](end-user-visualizations.md).

[Power BI - Conceitos Básicos](end-user-basic-concepts.md)
