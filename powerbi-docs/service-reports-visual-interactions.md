---
title: "Alterar a forma como os elementos visuais interagem num relatório"
description: "Documentação sobre como definir interações visuais num relatório do Microsoft Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: N_xYsCbyHPw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 126bd40e98a88138a2732155f9792d65666e52c7
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interações de visualização num relatório do Power BI
Por predefinição, as visualizações numa página de relatório podem ser utilizadas para filtro cruzado e realce cruzado de outras visualizações na página.
Por exemplo, selecionar um estado numa visualização de mapa realça o gráfico de colunas e filtra o gráfico de linhas para mostrar apenas os dados que se aplicam a um estado.
Consulte [Sobre filtragem e realce](power-bi-reports-filters-and-highlighting.md).

Para alterar este comportamento padrão, utilize o controlo de **Interação Visual**. As interações visuais só estão disponíveis na [Vista de edição](service-interact-with-a-report-in-editing-view.md). Se um relatório foi partilhado consigo, não terá acesso a interações visuais.

> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são utilizados para distinguir o comportamento descrito aqui do que acontece quando utiliza o painel **Filtros** para filtrar e realçar visualizações.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Selecione a visualização para ativá-la.  
2. Ative as **Interações Visuais** ao selecionar na barra do menu principal. Tenha em atenção aos ícones de filtrar e realçar que aparecem quando paira sobre outras visualizações na página do relatório.
   
    ![](media/service-reports-visual-interactions/pbi-visual-interaction-icon.png)
3. Determine o impacto que a visualização selecionada deve ter nas outras visualizações.  
   
   * Se deve executar o filtro cruzado na outra visualização, selecione o **ícone** de filtragem![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Se deve executar o realce cruzado nessa visualização, selecione o **ícone** de realce ![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Se não tiver nenhum impacto, selecione o **ícone** de não impacto ![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).
4. Opcionalmente, repita para todas as outras visualizações na página do relatório.

### <a name="next-steps"></a>Próximos passos
[Como utilizar filtros de relatório](power-bi-how-to-report-filter.md)

[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

