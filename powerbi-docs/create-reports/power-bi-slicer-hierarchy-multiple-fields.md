---
title: Adicionar vários campos a uma segmentação de dados de hierarquia
description: Saiba como criar uma segmentação de dados de hierarquia com vários campos numa hierarquia.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Create reports
ms.openlocfilehash: abed7e9f6da352d5461868e6371ffefb814eb3ff
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597638"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Adicionar vários campos a uma segmentação de dados de hierarquia

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Se quiser filtrar vários campos relacionados numa única segmentação de dados, poderá fazê-lo ao criar uma *segmentação de dados de hierarquia*. Pode criar segmentações de dados de hierarquia no Power BI Desktop ou no serviço Power BI.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Captura de ecrã da Segmentação de dados de hierarquia no Power BI.":::

Quando adiciona vários campos à segmentação de dados, será apresentada por predefinição uma seta ou *divisa* junto aos itens que podem ser expandidos para mostrar os itens no próximo nível.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Captura de ecrã do menu pendente Segmentação de dados de hierarquia no Power BI.":::
 
 
Quando seleciona um ou mais elementos subordinados de um item, vê um círculo semi-selecionado para o item de nível superior.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Captura de ecrã da Segmentação de dados de hierarquia de seleção única no Power BI.":::

## <a name="format-the-slicer"></a>Formatar a segmentação de dados

O comportamento da segmentação de dados não mudou. Também pode modelar a segmentação de dados como quiser. Por exemplo, pode defini-la como modo de seleção única. Também pode alternar entre uma lista e um menu pendente. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Captura de ecrã da Segmentação de dados de hierarquia formatada como segmentação de dados de menu pendente.":::

Também pode realizar as seguintes alterações de formatação.

### <a name="change-the-title"></a>Alterar o título

Também pode editar o título para qualquer segmentação de dados, mas é especialmente útil para as segmentações de dados de hierarquia. Por predefinição, o nome de uma segmentação de dados de hierarquia é uma lista dos nomes de campo na hierarquia.

Neste exemplo, o título da segmentação de dados lista os três campos na hierarquia: Tipo, Plataforma e Nome.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="Captura de ecrã da segmentação de dados de hierarquia com os campos Tipo, Plataforma e Nome.":::

Para alterar o nome, selecione a segmentação de dados e, em seguida, selecione o painel **Formato**. Em **Cabeçalho da segmentação de dados**, veja o nome atual da segmentação de dados na caixa **Texto do título**.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="Captura de ecrã do painel Formatar com o título atual.":::

Selecione o texto e adicione um novo nome.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="Captura de ecrã do novo título da segmentação de dados de hierarquia.":::


### <a name="change-the-expandcollapse-icon"></a>Alterar o ícone de expandir/fechar

As segmentações de dados de hierarquia têm outras opções de formatação. Pode alterar o ícone de expandir/fechar da seta predefinida para um sinal de adição/subtração ou um acento circunflexo.

1. Selecione a segmentação de dados e, em seguida, selecione **Formatar**.
1. Expanda **Itens** e selecione **Ícone de expandir/fechar**.
1. Escolha entre **Divisas**, **Mais/menos** ou **Acento circunflexo**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Captura de ecrã Selecionar um ícone de expandir/fechar para a segmentação de dados de hierarquia.":::
 
### <a name="change-the-indentation"></a>Alterar o avanço

Se o espaço for apertado no relatório, poderá querer reduzir o avanço dos itens subordinados. Por predefinição, o avanço é de 15 pixéis, mas pode aumentar ou diminuir. 

1. Selecione a segmentação de dados e, em seguida, selecione **Formatar**.
1. Expanda **Itens**, em seguida, arraste **Avanço de esquema gradual** mais ou menos. Também pode simplesmente escrever um número na caixa.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Captura de ecrã Definir o avanço da segmentação de dados de hierarquia.":::
    
## <a name="limitations-and-considerations"></a>Limitações e considerações

- Para modelos tabulares, esta funcionalidade requer o SQL Server Analysis Services 2017 ou posterior.
- Para modelos multidimensionais, esta funcionalidade ter o SQL Server Analysis Services 2019 CU5 ou posterior com o SuperDAXMD ativado. Leia mais sobre o [SuperDAXMD](/analysis-services/multidimensional-models/dax-for-multidimensional-models#superdaxmd).

## <a name="next-steps"></a>Próximos passos

- [Segmentação de Dados no Power BI](../visuals/power-bi-visualization-slicers.md)
- Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
