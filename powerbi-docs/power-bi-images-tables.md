---
title: Apresentar imagens numa tabela ou matriz num relatório
description: No Power BI Desktop, crie uma coluna com hiperligações para as imagens. Em seguida, no Power BI Desktop ou no serviço Power BI, adicione estas hiperligações a uma tabela, matriz, segmentação de dados ou cartão multilinhas do relatório para apresentar a imagem.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: cbb04057c8065e998068dd6520539c830a659f72
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715563"
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


## <a name="next-steps"></a>Próximos passos

[Formatação e esquema de página](/learn/modules/visuals-in-power-bi/12-formatting)

[Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

