---
title: Parte 1, Adicionar visualizações a um relatório do Power BI
description: Parte 1, Adicionar visualizações a um relatório do Power BI
author: mihart
ms.reviewer: rien
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 439807717a91a22520969a85a3991b76f8115833
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85232385"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Adicionar elementos visuais a um relatório do Power BI (parte 1)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Este artigo apresenta uma breve introdução à criação de uma visualização num relatório. Aplica-se ao serviço Power BI e ao Power BI Desktop. Para obter conteúdos mais avançados, [veja a Parte 2](power-bi-report-add-visualizations-ii.md) desta série.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial utiliza o [ficheiro PBIX de Vendas e marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).

1. Na secção superior esquerda da barra de menus do Power BI Desktop, selecione **Ficheiro** > **Abrir**
   
2. Localize a sua cópia do **ficheiro PBIX de Vendas e marketing**.

1. Abra o **ficheiro PBIX de Vendas e marketing** na vista de relatório ![Captura de ecrã a mostrar o ícone da vista de relatório.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de ecrã do separador amarelo.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.

> [!NOTE]
> Para partilhar o seu relatório com outro utilizador do Power BI, é necessário que ambos tenham licenças individuais do Power BI Pro ou que o relatório seja guardado numa capacidade Premium. Veja [partilhar relatórios](../collaborate-share/service-share-reports.md)

## <a name="add-visualizations-to-the-report"></a>Adicione visualizações ao relatório

1. Crie uma visualização selecionando um campo no painel **Campos**.

    Comece com um campo numérico, como **Vendas** > **TotalDeVendas**. O Power BI cria um gráfico de colunas com uma única coluna.

    ![Captura de ecrã de um gráfico de colunas com uma única coluna.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    Em alternativa, comece com um campo de categoria, como **Nome** ou **Produto**. O Power BI cria uma tabela e adiciona esse campo ao conjunto **Valores**.

    ![Captura de ecrã a mostrar uma tabela com quatro categorias](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    Também pode começar com um campo geográfico, como **Área Geográfica** > **Cidade**. O Power BI e o Bing Maps criam uma visualização de mapa.

    ![Captura de ecrã de uma visualização de mapa.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>Alterar o tipo de visualização

 Crie uma visualização e, em seguida, altere o respetivo tipo. 
 
 1. Selecione **Produto** > **Categoria** e, em seguida, **Produto** > **Contagem do Produto** para adicionar ambos ao conjunto **Valores**.

    ![Captura de ecrã do painel Campos com o conjunto Valores destacado.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Altere a visualização para um gráfico de colunas ao selecionar o ícone **Gráfico de colunas empilhadas**.

   ![Captura de ecrã do painel Visualizações, com o ícone Gráfico de colunas empilhadas destacado.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. Para alterar a forma como o elemento visual é ordenado, selecione **Mais ações** (...).  Utilize as opções de ordenação para alterar o sentido da ordenação (crescente ou decrescente) e alterar a coluna que está a ser utilizada para ordenar (**Ordenar por**).

   ![Captura de ecrã a mostrar o menu pendente Mais ações.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Próximos passos

 Continue para:

* [Parte 2: Adicionar visualizações a um relatório do Power BI](power-bi-report-add-visualizations-ii.md)

* [Interaja com as visualizações](../consumer/end-user-reading-view.md) no relatório.
