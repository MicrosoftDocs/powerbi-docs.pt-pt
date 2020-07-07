---
title: Adicionar vários campos a uma segmentação de dados de hierarquia
description: Saiba como criar uma segmentação de dados de hierarquia com vários campos numa hierarquia.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/11/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2b9c4a8f4695f8d701eba535180194d29dd8bdec
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238185"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Adicionar vários campos a uma segmentação de dados de hierarquia

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Se quiser filtrar vários campos relacionados numa única segmentação de dados, poderá fazê-lo ao criar uma *segmentação de dados de hierarquia*. Pode criar segmentações de dados de hierarquia no Power BI Desktop ou no serviço Power BI.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Segmentação de dados de hierarquia no Power BI":::

Quando adiciona vários campos à segmentação de dados, será apresentada por predefinição uma seta ou *divisa* junto aos itens que podem ser expandidos para mostrar os itens no próximo nível.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Menu pendente de segmentação de dados de hierarquia no Power BI":::
 
 
Quando seleciona um ou mais elementos subordinados de um item, vê um círculo semi-selecionado para o item de nível superior.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Segmentação de dados de hierarquia de seleção única no Power BI":::

## <a name="format-the-slicer"></a>Formatar a segmentação de dados

O comportamento da segmentação de dados não mudou. Também pode modelar a segmentação de dados como quiser. Por exemplo, pode defini-la como modo de seleção única. Também pode alternar entre uma lista e um menu pendente. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Segmentação de dados de hierarquia formatada como segmentação de dados de menu pendente":::

### <a name="change-the-expandcollapse-icon"></a>Alterar o ícone de expandir/fechar

As segmentações de dados de hierarquia têm outras opções de formatação. Pode alterar o ícone de expandir/fechar da seta predefinida para um sinal de adição/subtração ou um acento circunflexo.

1. Selecione a segmentação de dados e, em seguida, selecione **Formatar**.
1. Expanda **Itens** e selecione **Ícone de expandir/fechar**.
1. Escolha entre **Divisas**, **Mais/menos** ou **Acento circunflexo**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Selecionar um ícone de expandir/fechar para a segmentação de dados de hierarquia":::
 
### <a name="change-the-indentation"></a>Alterar o avanço

Se o espaço for apertado no relatório, poderá querer reduzir o avanço dos itens subordinados. Por predefinição, o avanço é de 15 pixéis, mas pode aumentar ou diminuir. 

1. Selecione a segmentação de dados e, em seguida, selecione **Formatar**.
1. Expanda **Itens**, em seguida, arraste **Avanço de esquema gradual** mais ou menos. Também pode simplesmente escrever um número na caixa.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Definir o avanço da segmentação de dados de hierarquia":::

## <a name="next-steps"></a>Próximos passos

- [Segmentação de Dados no Power BI](../visuals/power-bi-visualization-slicers.md)
- Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)