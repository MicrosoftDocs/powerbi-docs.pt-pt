---
title: Apresentar imagens numa tabela ou matriz num relatório
description: No Power BI Desktop, crie uma coluna com hiperligações para as imagens. Em seguida, no Power BI Desktop ou no serviço Power BI, adicione estas hiperligações a uma tabela, matriz, segmentação de dados ou cartão multilinhas do relatório para apresentar a imagem.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 09/11/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 4ba0042804d366ddfd80935c48246cadeadf3614
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417963"
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
