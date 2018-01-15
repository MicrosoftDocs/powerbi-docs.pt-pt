---
title: "Ver relatórios do Power BI otimizados para o seu telemóvel"
description: "Saiba mais sobre a interação com as páginas de relatórios otimizadas para visualização nas aplicações móveis do Power BI."
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
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 54a1b81cc4281db7a622668ba205c1c57d5e396d
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Ver relatórios do Power BI otimizados para o seu telemóvel
Quando criar um relatório do Power BI no Power BI Desktop, também pode criar uma versão desse [relatório otimizada para visualização numa aplicação do Power BI no telemóvel](desktop-create-phone-report.md).

Depois, quando abrir um relatório do Power BI num telemóvel, o Power BI deteta se o relatório foi otimizado para telemóveis e abre automaticamente o relatório otimizado na vista vertical.

![Relatório no modo vertical](media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Se não existir um relatório otimizado para telemóvel, o relatório será aberto na mesma, mas nas vistas horizontais não otimizadas. Mesmo num relatório otimizado para telemóveis, se colocar o telemóvel de lado, o relatório será aberto na vista não otimizada com o esquema de relatório otimizado. Se apenas algumas páginas forem otimizadas, irá ver uma mensagem na vista vertical a indicar que o relatório se encontra disponível na vista horizontal.

![Página de relatório não otimizada](media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Todas as restantes funcionalidades de relatórios do Power BI continuam a funcionar em relatórios otimizados para telemóveis. Saiba mais sobre o que pode fazer em:

* [Relatórios em iPhones](mobile-reports-in-the-mobile-apps.md). 
* [Relatórios em telemóveis Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-an-iphone"></a>Filtrar a página de relatórios num iPhone
Se um relatório otimizado para telemóvel tiver filtros definidos, quando vir o relatório num iPhone, pode utilizar esses filtros. 

1. Toque no ícone de filtro ![Ícone de filtro no telemóvel](media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) na parte inferior da página. 
2. Utilize a filtragem básica ou avançada para ver os resultados em que está interessado.
   
    ![Filtro avançado de relatórios do Power BI no telemóvel](media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Realce cruzado de visuais
O realce cruzado de visuais em relatórios no telemóvel funciona da mesma forma que no serviço Power BI e nos relatórios em telemóveis na vista horizontal: quando selecionar dados num visual, são realçados dados relacionados noutros visuais dessa página.

Saiba mais sobre [filtrar e realçar no Power BI](power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Selecionar visuais
Nos relatórios no telemóvel, ao selecionar um visual, o relatório no telemóvel realça esse visual e foca-se no mesmo, neutralizando os gestos de tela.

Com o visual selecionado, pode fazer coisas como deslocar-se no visual. Para desmarcar um visual, basta tocar em qualquer lugar fora da área visual.

## <a name="open-visuals-in-focus-mode"></a>Abrir visuais no modo de detalhe
Os relatório no telemóvel disponibilizam também um modo de detalhe, para que possa obter uma vista mais alargada de um único visual e explorar o visual e o relatório.

* No relatório de telemóvel, toque nas reticências (**...**) no canto superior direito de um visual > **Expandir para o modo de detalhe**.
  
    ![Expandir para o modo de detalhe](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

O que for feito no modo de detalhe é aplicado à tela de relatório e vice-versa, para uma experiência de exploração integrada. Por exemplo, se realçar um valor no visual e, em seguida, regressar ao relatório completo, o relatório como um todo será filtrado para o valor que realçou no visual.

Algumas ações só são possíveis no modo de detalhe, devido às limitações de tamanho de ecrã:

* **Desagregar** as informações mostradas num visual. Saiba mais sobre [desagregar e agregar](mobile-apps-view-phone-report.md#drill-down-in-a-visual) num relatório de telemóvel, mais abaixo.
* **Ordene** os valores num visual.
* **Reverter**: limpar passos de exploração que efetuou num visual e reverter para a definição estabelecida quando o relatório foi criado.
  
    Para limpar toda a exploração de um visual, toque nas reticências (**...**) > **Reverter**.
  
    ![Reverter](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Pode reverter a nível de relatório, limpar toda a exploração de todos os visuais ou, a nível visual, limpar toda a exploração do visual específico selecionado.   

## <a name="drill-down-in-a-visual"></a>Desagregar num visual
Se os níveis de hierarquia estiverem definidos num visual, pode desagregar até às informações detalhadas mostradas num visual e, em seguida, voltar para cima. Pode [adicionar desagregações a um visual](power-bi-visualization-drill-down.md) no serviço Power BI ou no Power BI Desktop. A desagregação só funciona em relatórios do Power BI otimizados para telemóveis quando os vir num telemóvel. 

1. Num relatório num telemóvel, toque nas reticências (**...**) no canto superior direito > **Expandir para o modo de detalhe**.
   
    ![Expandir para o modo de detalhe](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Neste exemplo, as barras mostram os valores de estados.
2. Toque no ícone Explorar ![Ícone Explorar](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) no canto inferior esquerdo.
   
    ![Modo Explorar](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Toque em **Mostrar nível seguinte** ou em **Expandir para o nível seguinte**.
   
    ![Expandir para o nível seguinte](media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Agora, as barras mostram os valores das cidades.
   
    ![Níveis expandidos](media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Se tocar na seta no canto superior esquerdo, irá regressar ao relatório de telemóvel com os valores ainda expandidos ao nível inferior.
   
    ![Ainda expandido ao nível inferior](media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Para regressar ao nível original, toque nas reticências (**...**) novamente > **Reverter**.
   
    ![Reverter](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="next-steps"></a>Passos seguintes
* [Criar relatórios otimizados para aplicações para telemóvel do Power BI](desktop-create-phone-report.md)
* [Criar uma vista de telemóvel de um dashboard no Power BI](service-create-dashboard-mobile-phone-view.md)
* [Criar visuais responsivos otimizados para qualquer tamanho](desktop-create-responsive-visuals.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

