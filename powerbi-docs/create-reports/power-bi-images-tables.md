---
title: Apresentar imagens numa tabela ou matriz num relatório
description: No Power BI Desktop, crie uma coluna com hiperligações para as imagens. Em seguida, no Power BI Desktop ou no serviço Power BI, adicione estas hiperligações a uma tabela, matriz, segmentação de dados ou cartão multilinhas do relatório para apresentar a imagem.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 4aa10a08757b9d62d4d8c987aedbede47f936a00
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344624"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>Apresentar imagens numa tabela, matriz ou segmentação de dados num relatório

Uma boa maneira de melhorar os relatórios é através da adição de imagens. As imagens estáticas na página são boas para algumas finalidades. Mas, às vezes, precisa de imagens que se relacionem com os dados no relatório. Este tópico ensina como apresentar imagens numa tabela, numa matriz, numa segmentação de dados ou num cartão multilinhas. 

![Imagens de URL numa tabela](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>Adicionar imagens ao relatório

1. Crie uma coluna com os URLs das imagens. Veja as [Considerações](#considerations) mais adiante neste artigo para obter os requisitos.

1. Selecione essa coluna. No friso **Modelagem**, para **Categoria de dados**, selecione **URL da imagem**.

    ![Definir a Categoria de dados como o URL da imagem](media/power-bi-images-tables/power-bi-set-url-image.png)

1. Adicione a coluna a uma tabela, matriz, segmentação de dados ou cartão multilinhas.

    ![Segmentação de dados com imagens](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>Considerações

- A imagem precisa de estar num destes formatos de ficheiro: .bmp, .jpg, .jpeg, .gif, .png ou .svg
- O URL precisa de ser acessível de forma anónima, não num site que exija início de sessão, como o SharePoint. No entanto, se as imagens estiverem alojadas no SharePoint ou no OneDrive, poderá obter um código de incorporação que aponte diretamente para elas. 


## <a name="next-steps"></a>Próximas etapas

[Formatação e esquema de página](/learn/modules/visuals-in-power-bi/12-formatting)

[Conceitos básicos para designers no serviço Power BI](../fundamentals/service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)