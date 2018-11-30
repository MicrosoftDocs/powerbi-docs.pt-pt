---
title: Compreender a forma como os elementos visuais interagem num relatório (para os consumidores de relatórios)
description: Documentação para os utilizadores finais do Power BI que explica como os elementos visuais interagem numa página de relatório.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c87f99b768f52fe7f6b565c47ed7e434b167a046
ms.sourcegitcommit: dc8b8a2cf2dcc96ccb46159802ebd9342a7fa840
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49112067"
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interações de visualização num relatório do Power BI
Um dos recursos incríveis do Power BI é a forma como estão interligados todos os elementos visuais numa página de relatório. Se selecionar um ponto de dados num dos elementos visuais, serão alterados todos os outros elementos visuais na página que contêm esses dados, com base nessa seleção. 

![vídeo de interação dos elementos visuais](media/end-user-interactions/interactions.gif)

Por predefinição, as visualizações numa página de relatório podem ser utilizadas para filtro cruzado, realce cruzado e exploração de outras visualizações na página. Por exemplo, selecionar um estado numa visualização de mapa pode realçar o gráfico de colunas e filtra o gráfico de linhas para mostrar apenas os dados que se aplicam a um estado.

Consulte [Sobre filtragem e realce](../power-bi-reports-filters-and-highlighting.md). Se tiver uma visualização que suporte a [exploração](../power-bi-visualization-drill-down.md) por predefinição, a exploração de uma visualização não tem impacto nas outras visualizações na página de relatório. 

O modo exato como interagem os elementos visuais numa página é definido pelo *designer* do relatório. Os designers têm opções para ativar e desativar interações visuais e para alterar o comportamento de filtragem cruzada, realce cruzado e exploração predefinidos.
  
> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são utilizados para distinguir o comportamento descrito aqui do que acontece quando utiliza o painel **Filtros** para filtrar e realçar visualizações.  

### <a name="next-steps"></a>Próximos passos
[Como utilizar filtros de relatório](../power-bi-how-to-report-filter.md)