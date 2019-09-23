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
ms.openlocfilehash: 2ebbc277f2a269ebaf2d1bdb99f1aa800576b466
ms.sourcegitcommit: ba085b248c54e8fb1fd8eb2bb23a814e3fdd7ff6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936499"
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

[Adicionar formas estáticas, caixas de texto e imagens a um relatório](https://docs.microsoft.com/power-bi/guided-learning/visualizations?tutorial-step=11)

[Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

