---
title: Interaja com pequenos múltiplos em Power BI (pré-visualização)
description: Este artigo explica como interagir com pequenos múltiplos, ou treliça.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 6d700d4a4bb7453f7630c76c5a3f265ee022e02a
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617441"
---
# <a name="interact-with-small-multiples-in-power-bi-preview"></a>Interaja com pequenos múltiplos em Power BI (pré-visualização)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Pequenos múltiplos, ou treliça, divide um visual em várias versões de si mesmo. Este artigo explica como tirar o máximo partido da interação com eles.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Screenshot de pequenos múltiplos para categoria e região.":::

Quer criar pequenos múltiplos? Ver [Criar pequenos múltiplos em Power BI (pré-visualização)](power-bi-visualization-small-multiples.md).

## <a name="scroll-in-a-small-multiple"></a>Percorra num pequeno múltiplo

Pequenos múltiplos podem conter mais gráficos individuais que podem caber na grelha. Em caso afirmativo, pode deslocar-se para baixo para ver o resto das suas categorias.

Para um eixo X categórico com muitas categorias, você também vê uma barra de deslocal para cada cópia desse eixo. Rolar sobre o eixo move-os todos juntos. Se estiver a utilizar uma roda de deslocação, segure Shift para deslocar os eixos categóricos.

## <a name="select-data-to-cross-highlight"></a>Selecione dados para o cruzamento

Pode selecionar diferentes subconjuntos de dados selecionando diferentes partes do visual.

### <a name="select-data-points"></a>Selecione pontos de dados

Passe sobre o ponto de dados de um múltiplo para mostrar a ponta da ferramenta nesse múltiplo. Você também vê uma linha guia no eixo X para gráficos de linha. Selecione esse ponto de dados para realçar outros visuais tanto pelo valor do eixo como pela categoria de pequeno múltiplo, e diminua os outros múltiplos.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-data-point.png" alt-text="Selecione um ponto de dados num pequeno múltiplo.":::

### <a name="select-a-categorical-axis-value"></a>Selecione um valor de eixo categórico

Selecione uma etiqueta de categoria para realçar outros visuais por esse valor do eixo.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-category-axis.png" alt-text="Selecione um eixo de categoria num pequeno múltiplo.":::

### <a name="select-a-title"></a>Selecione um título

Selecione o título de um múltiplo para cruzar outros visuais pela categoria nesse sub-cabeça.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-title.png" alt-text="Selecione um título num pequeno múltiplo.":::

### <a name="legend"></a>Legenda

Selecione uma categoria de lenda para cruzar outros visuais e cruzar outros múltiplos.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-legend.png" alt-text="Selecione um item na legenda num pequeno múltiplo.":::


## <a name="sort"></a>Ordenar

Com a nova funcionalidade de tipo, pode classificar vários aspetos de um visual ao mesmo tempo. Ordenar pela categoria, e também pelo eixo em cada múltiplo. 

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-sort.png" alt-text="Serdene os múltiplos pequenos.":::

## <a name="next-steps"></a>Passos seguintes

[Criar pequenos múltiplos em Power BI (pré-visualização)](power-bi-visualization-small-multiples.md)
