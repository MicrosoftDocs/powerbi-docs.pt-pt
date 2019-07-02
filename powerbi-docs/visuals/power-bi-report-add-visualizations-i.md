---
title: Parte 1, Adicionar visualizações a um relatório do Power BI
description: Parte 1, Adicionar visualizações a um relatório do Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299287"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Parte 1, Adicionar visualizações a um relatório do Power BI

Este artigo apresenta uma breve introdução à criação de uma visualização num relatório. Aplica-se ao serviço Power BI e ao Power BI Desktop. Para obter conteúdos mais avançados, [veja a Parte 2](power-bi-report-add-visualizations-ii.md) desta série. Veja a Amanda a demonstrar algumas formas diferentes de criar, editar e formatar visuais a tela de relatórios. Em seguida, experimente utilizando o [exemplo Vendas e Marketing](../sample-datasets.md) para criar os seus próprios relatórios.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Abra um relatório e adicione uma nova página

1. Abra um [relatório na Vista de Edição](../service-interact-with-a-report-in-editing-view.md).

    Este tutorial utiliza o [exemplo de Vendas e Marketing](../sample-datasets.md).

1. Se o painel **Campos** não estiver visível, selecione o ícone de seta para o abrir.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Adicione uma página em branco ao relatório.

## <a name="add-visualizations-to-the-report"></a>Adicione visualizações ao relatório

1. Crie uma visualização selecionando um campo no painel **Campos**.

    Comece com um campo numérico, como **FactosDeVendas** > **Vendas $** . O Power BI cria um gráfico de colunas com uma única coluna.

    ![Captura de ecrã de um gráfico de colunas com uma única coluna.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    Em alternativa, comece com um campo de categoria, como **Nome** ou **Produto**. O Power BI cria uma tabela e adiciona esse campo ao conjunto **Valores**.

    ![GIF de uma pessoa a selecionar Produto e, em seguida, a categoria para criar uma tabela.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    Também pode começar com um campo geográfico, como **Área Geográfica** > **Cidade**. O Power BI e o Bing Maps criam uma visualização de mapa.

    ![Captura de ecrã de uma visualização de mapa.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Crie uma visualização e, em seguida, altere o respetivo tipo. Selecione **Produto** > **Categoria** e, em seguida, **Produto** > **Contagem do Produto** para adicionar ambos ao conjunto **Valores**.

   ![Captura de ecrã do painel Campos com o conjunto Valores destacado.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Altere a visualização para um gráfico de colunas ao selecionar o ícone **Gráfico de colunas empilhadas**.

   ![Captura de ecrã do painel Visualizações, com o ícone Gráfico de colunas empilhadas destacado.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. Quando criar visualizações no relatório, pode [afixá-las ao dashboard](../service-dashboard-pin-tile-from-report.md). Para afixar a visualização, selecione o ícone afixar ![Captura de ecrã do ícone afixar](media/power-bi-report-add-visualizations-i/pinnooutline.png).

   ![Captura de ecrã de uma visualização do gráfico de colunas com o ícone afixar destacado.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Próximos passos

 Continue para:

* [Parte 2: Adicionar visualizações a um relatório do Power BI](power-bi-report-add-visualizations-ii.md)

* [Interaja com as visualizações](../consumer/end-user-reading-view.md) no relatório.

* [Faça mais com visualizações](power-bi-report-visualizations.md).

* [Guarde o relatório](../service-report-save.md).
