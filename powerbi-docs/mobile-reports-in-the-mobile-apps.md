---
title: "Explorar relatórios nas aplicações móveis do Power BI"
description: "Saiba mais sobre ver e interagir com relatórios nas aplicações móveis do Power BI no seu telemóvel ou tablet. Pode criar relatórios no serviço Power BI ou no Power BI Desktop e, em seguida, interagir com os mesmos nas aplicações móveis. "
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/23/2018
ms.author: maggies
ms.openlocfilehash: 610234a221c5ab1de976f9d554292395760efa0f
ms.sourcegitcommit: 1a5446c3136dc0787f2a1d5b8cad1113704301ba
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/24/2018
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorar relatórios nas aplicações móveis do Power BI
Aplica-se a:

| ![iPhone](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Telemóvel Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablet Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Dispositivos Windows 10](media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Telemóveis Android |Tablets Android |Dispositivos Windows 10 |

Um relatório do Power BI é uma vista interativa dos seus dados, com visuais que representam diferentes descobertas e informações obtidas por meio desses dados. Ver os relatórios nas aplicações móveis do Power BI é o terceiro passo num processo de três passos.

1. [Criar relatórios no Power BI Desktop](desktop-report-view.md). Pode mesmo [otimizar um relatório para telemóveis](mobile-apps-view-phone-report.md) no Power BI Desktop. 
2. Publique esses relatórios no serviço Power BI [(https://powerbi.com)](https://powerbi.com) ou no [Power BI Report Server](report-server/get-started.md).  
3. Em seguida, interaja com esses relatórios nas aplicações móveis do Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Abrir um relatório do Power BI na aplicação móvel
Os relatórios do Power BI são armazenados em diferentes locais na aplicação móvel, consoante o local onde os obteve. Podem estar em Aplicações, Partilhado comigo, Áreas de trabalho (incluindo A Minha Área de Trabalho) ou num servidor de relatórios. Pode vezes, percorre um dashboard relacionado para chegar a um relatório, e noutras vezes estes estão listados.

* Num dashboard, toque nas reticências (...) no canto superior direito de um mosaico > **Abrir relatório**.
  
  ![Abrir relatório](media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Nem todos os mosaicos têm a opção de abrir num relatório. Por exemplo, os mosaicos criados ao fazer uma pergunta na caixa de Perguntas e Respostas não abrem os relatórios ao tocar nos mesmos. 
  
  Num telemóvel, o relatório é aberto no modo horizontal, a menos que esteja [otimizado para visualização num telemóvel](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones).
  
  ![Relatório de telemóvel no modo horizontal](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>Ver relatórios otimizados para telemóveis
Os autores de relatórios do Power BI podem criar um esquema de relatório especificamente otimizado para telemóveis. As páginas do relatório otimizadas para telemóveis têm mais funcionalidades: por exemplo, pode pesquisar e ordenar em visuais no modo de foco, e pode aceder a [filtra o autor do relatório adicionado à página do relatório](mobile-apps-view-phone-report.md#filter-the-report-page-on-a-phone). Numa lista de relatórios, um relatório otimizado tem um ícone especial ![Ícone de relatório do telemóvel](media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png):

![Abrir o relatório no telemóvel](media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

Quando vê esse relatório num telemóvel, este é aberto numa vista vertical.

![Relatório na vista vertical](media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

 Um relatório pode ter uma mistura de páginas que estão e não estão otimizadas para telemóveis. Se for o caso, quando percorrer o relatório, a vista irá alternar entre horizontal e vertical para cada página.

Saiba mais sobre os [relatórios otimizados para a vista de telemóvel](mobile-apps-view-phone-report.md).

## <a name="use-slicers-to-filter-a-report-page"></a>Usar a segmentação para filtrar uma página de relatório
Ao estruturar um relatório no serviço Power BI [(https://powerbi.com)](https://powerbi.com), tenha em conta que, num telemóvel, não pode ver o painel Filtros, mas pode [ver segmentações numa página de relatório](power-bi-visualization-slicers.md). Adicione segmentações a um relatório para que o utilizador e os seus colegas possam utilizar para filtrar a página num telemóvel.

* Quando selecionar um valor numa segmentação na página de relatório, este filtra os outros visuais na página.
  
  ![Segmentação de relatórios](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  Nesta ilustração, a segmentação está a filtrar o gráfico de colunas para mostrar apenas valores de julho.

## <a name="cross-filter-and-highlight-a-power-bi-report-page"></a>Realizar filtragem cruzada e realçar uma página de relatório do Power BI
Quando seleciona um valor num visual, este não filtra os outros visuais. Realça os valores relacionados nos outros visuais.

* Toque num valor num visual.
  
  ![Filtros cruzados numa página](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  Tocar na coluna Grande num visual realça os valores relacionados nos outros visuais. 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>Ordenar um visual num iPad ou num tablet
* Toque no gráfico, toque nas reticências (**...**) e toque no nome do campo.
  
   ![Ordenar um visual](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* Para reverter a ordenação, toque novamente nas reticências (**...**) e, em seguida, toque novamente no mesmo nome de campo.

## <a name="drill-down-and-up-in-a-visual-on-an-ipad-or-a-tablet"></a>Desagregar e agregar num visual num iPad ou num tablet
Se um autor de relatório tiver adicionado esta capacidade a um visual, num iPad ou num tablet, pode desagregar num visual para ver os valores que constituem uma parte do mesmo. Pode [adicionar desagregações a um visual](power-bi-visualization-drill-down.md) no Power BI Desktop ou no serviço Power BI. 

> [!NOTE]
> Atualmente, a desagregação não funciona em mapas no iPad ou tablet.
> 
> 

* Toque num elemento visual. Se tiver setas para cima e para baixo nos cantos superiores ![Ícones Agregar e Desagregar](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-down.png), pode desagregá-los. Para desagregar um valor, toque na seta no canto superior direito e, em seguida, toque num valor num visual; neste caso, o balão FD-04 a azul escuro.
  
  ![Desagregar num visual](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-one.png)
* Para voltar a agregar, toque na seta para cima no canto superior esquerdo.
  
  ![Agregar](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up.png)

## <a name="go-back-to-my-workspace"></a>Regresse a A Minha Área de Trabalho
* Toque na seta junto ao nome do relatório > toque em **A Minha Área de Trabalho**.
  
  ![Voltar para cima](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-back.png)

## <a name="next-steps"></a>Passos seguintes
* [Ver e interagir com relatórios do Power BI otimizados para o seu telemóvel](mobile-apps-view-phone-report.md)
* [Criar uma versão de um relatório otimizada para telemóveis](desktop-create-phone-report.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
