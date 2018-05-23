---
title: Criar relatórios otimizados para as aplicações de telemóvel do Power BI
description: Saiba como otimizar páginas de relatório no Power BI Desktop para as aplicações para telemóvel do Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/08/2017
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 58fa5214d1a5b7e7c80d199e23cfae9762a80f36
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="create-reports-optimized-for-the-power-bi-phone-apps"></a>Criar relatórios otimizados para as aplicações de telemóvel do Power BI
Quando [criar um relatório no Power BI Desktop](desktop-report-view.md), pode melhorar a experiência de utilização nas aplicações móveis para telemóveis através da criação de uma versão do relatório especificamente para o telemóvel. Pode adaptar o relatório ao telemóvel ao reorganizar e redimensionar os elementos visuais, provavelmente ao não incluir todos, para uma experiência ideal. Além disso, pode criar [visuais *reativos*](#optimize-a-visual-for-any-size) e [segmentações de dados reativas](#enhance-slicers-to-to-work-well-in-phone-reports) que sejam corretamente redimensionados para visualização num telemóvel. Também pode adicionar filtros ao relatório. Esses filtros aparecem automaticamente no relatório do telemóvel. Os leitores de relatórios podem vê-los e filtrar o relatório com os mesmos.

![Relatório otimizado num telemóvel](media/desktop-create-phone-report/07-power-bi-phone-report-portrait.png)

## <a name="lay-out-a-report-page-for-the-phone-in-power-bi-desktop"></a>Apresentar uma página de relatório para telemóvel no Power BI Desktop
Depois de [criar um relatório no Power BI Desktop](desktop-report-view.md), pode otimizá-lo para telemóveis.

1. No Power BI Desktop, selecione **Vista de Relatório** na barra de navegação esquerda.
   
    ![Ícone de Vista de Relatório](media/desktop-create-phone-report/pbi_reportviewinpbidesigner_changeview.png)
2. No separador **Ver**, selecione **Esquema de Telemóvel**.  
   
    ![Ícone de Esquema de Telemóvel](media/desktop-create-phone-report/power-bi-phone-layout-icon.png)
   
    Verá uma tela de telemóvel em branco. Todos os elementos visuais na página de relatório original estão listados no painel Visualizações à direita.
3. Para adicionar um elemento visual ao esquema de telemóvel, arraste-o do painel Visualizações para a tela do telemóvel.
   
    Os relatórios de telemóvel utilizam um esquema de grelha. À medida que arrasta os elementos visuais para a tela do telemóvel, estes ajustam-se a essa grelha.
   
    ![Arrastar e largar um elemento visual](media/desktop-create-phone-report/02_dragging_and_droping_a_vis.gif)
   
    Pode adicionar alguns ou todos os elementos visuais do relatório principal à página de relatório de telemóvel. Pode adicionar cada elemento visual apenas uma vez.
4. Pode redimensionar os elementos visuais na grelha, tal como faria para mosaicos em dashboards e dashboards móveis.
   
   > [!NOTE]
   > A grelha de relatório de telemóvel é dimensionada nos telemóveis de tamanhos diferentes, pelo que o relatório será apresentado corretamente em ecrãs pequenos e grandes.
   > 
   > 
   
   ![Redimensionar um elemento visual](media/desktop-create-phone-report/03_resizing_a_viz_to_grid.gif)

## <a name="optimize-a-visual-for-any-size"></a>Otimizar um elemento visual para qualquer tamanho
Pode definir os elementos visuais no seu dashboard ou relatório para que sejam *reativos*, para que sejam alterados dinamicamente para apresentarem a quantidade máxima de dados e informações, independentemente do tamanho do ecrã. 

À medida que o elemento visual muda de tamanho, o Power BI dá prioridade à vista de dados, por exemplo, ao remover o preenchimento e ao mover a legenda para a parte superior do elemento visual automaticamente, para que o elemento visual permaneça informativo mesmo enquanto fica mais pequeno.

![Redimensionamento de elemento visual reativo](media/desktop-create-phone-report/power-bi-responsive-visual.gif)

Escolha se quer ativar a capacidade de resposta de cada elemento visual. Leia mais sobre como [otimizar elementos visuais](desktop-create-responsive-visuals.md).

## <a name="considerations-when-creating-phone-report-layouts"></a>Considerações ao criar esquemas de relatório de telemóvel
* Para relatórios com múltiplas páginas, pode otimizar todas as páginas ou apenas algumas. 
* Se tiver definido uma cor de fundo para uma página de relatório, o relatório de telemóvel terá a mesma cor de fundo.
* Não pode modificar as definições de formatação apenas para o telemóvel. A formatação é consistente entre esquemas principais e de telemóvel. Por exemplo, os tamanhos dos tipos de letra serão idênticos.
* Para alterar um elemento visual, como alterar a formatação, o conjunto de dados, os filtros ou qualquer outro atributo, volte ao modo de criação de relatórios normal.
* O Power BI fornece títulos e nomes de página predefinidos para relatórios de telemóvel na aplicação móvel. Se tiver criado elementos visuais de texto para títulos e nomes de página no relatório, considere não os adicionar aos seus relatórios de telemóvel.     

## <a name="remove-a-visual-from-the-phone-layout"></a>Remover um elemento visual do esquema de telemóvel
* Para remover um elemento visual, clique no X na parte superior direita do elemento visual na tela do telemóvel ou selecione-o e prima **Eliminar**.
  
   A remoção do elemento visual aqui apenas o remove da tela do esquema de telemóvel. O elemento visual e o relatório original não são afetados.
  
   ![Remover um elemento visual](media/desktop-create-phone-report/05_removing_a_vis.gif)

## <a name="enhance-slicers-to-to-work-well-in-phone-reports"></a>Melhorar as segmentações de dados para um correto funcionamento nos relatórios de telemóvel
As segmentações de dados disponibilizam uma filtragem na tela dos dados de relatório. Quando conceber segmentações de dados no modo de criação de relatórios normal, pode modificar algumas definições de segmentação de dados para torná-las mais utilizáveis nos relatórios de telemóvel:

* Decida se os leitores de relatórios podem selecionar apenas um ou mais do que um item.
* Coloque uma caixa à volta da segmentação de dados para facilitar a análise do relatório.
* Torne a segmentação vertical, horizontal ou *reativa*. 

Se tornar a segmentação reativa, ao alterar o seu tamanho e forma esta mostrará mais ou menos opções. Pode aumentá-la ou diminui-la na vertical ou na horizontal. Se a diminuir muito, esta transforma-se num ícone de filtro na página do relatório. 

![Segmentação de dados reativa no Power BI](media/desktop-create-phone-report/power-bi-slicer-2-rows.png)

Leia mais sobre a [criação de segmentações de dados reativas](power-bi-slicer-filter-responsive.md).

## <a name="publish-a-phone-report"></a>Publicar um relatório de telemóvel
* Para publicar a versão para telemóvel de um relatório, pode [publicar o relatório principal do Power BI Desktop para o serviço Power BI](desktop-upload-desktop-files.md) e a versão para telemóvel publica em simultâneo.
  
    Leia mais sobre [partilhas e permissões no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md).

## <a name="view-optimized-and-unoptimized-reports-on-a-phone"></a>Ver relatórios otimizados e não otimizados num telemóvel
Em aplicações móveis em telemóveis, o Power BI deteta automaticamente os relatórios otimizados e não otimizados. Se existir um relatório otimizado para telemóvel, a aplicação de telemóvel do Power BI abre automaticamente o relatório no modo de relatório de telemóvel.

Se não existir um relatório otimizado para telemóvel, o relatório é aberto na vista horizontal não otimizada.  

Quando estiver num relatório de telemóvel, a alteração da orientação do telemóvel para horizontal abre o relatório na vista não otimizada com o esquema de relatório original, quer o relatório esteja ou não otimizado.

Se apenas otimizar algumas páginas, os leitores verão uma mensagem na vista vertical a indicar que o relatório se encontra disponível na vista horizontal.

![Página de telemóvel não otimizada](media/desktop-create-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Os leitores de relatórios podem colocar os telemóveis de lado para ver a página no modo horizontal. Leia mais sobre como [interagir com relatórios do Power BI otimizados para o seu telemóvel](mobile-apps-view-phone-report.md).

## <a name="next-steps"></a>Passos seguintes
* [Criar uma vista de telemóvel de um dashboard no Power BI](service-create-dashboard-mobile-phone-view.md)
* [Ver relatórios do Power BI otimizados para o seu telemóvel](mobile-apps-view-phone-report.md)
* [Criar elementos visuais reativos otimizados para qualquer tamanho](desktop-create-responsive-visuals.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

