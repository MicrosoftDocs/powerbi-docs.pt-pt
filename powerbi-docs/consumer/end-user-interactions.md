---
title: Compreender como os elementos visuais interagem num relatório
description: Documentação para os utilizadores finais do Power BI que explica como os elementos visuais interagem numa página de relatório.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413161"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Forma como os elementos visuais efetuam a filtragem cruzada entre si num relatório do Power BI
Um dos recursos incríveis do Power BI é a forma como estão interligados todos os elementos visuais numa página de relatório. Se selecionar um ponto de dados num dos elementos visuais, serão alterados todos os outros elementos visuais na página que contêm esses dados, com base nessa seleção. 

![vídeo de interação dos elementos visuais](media/end-user-interactions/interactions.gif)

Por predefinição, selecionar um ponto de dados numa visualização numa página de relatório irá filtro cruzado, realce cruzado e explorar as outras visualizações na página. 

Isso pode ser útil para identificar como um valor nos seus dados contribui para outro. Por exemplo, selecionando o segmento de moderação no gráfico em anel, destaca a contribuição desse segmento para cada coluna de Total de unidades pelo gráfico de mês, e ele filtrados de gráfico de linhas no lado direito.

![imagem dos elementos visuais interagem](media/end-user-interactions/power-bi-interactions.png)

Consulte [Sobre filtragem e realce](../power-bi-reports-filters-and-highlighting.md). 

O modo exato como interagem os elementos visuais numa página é definido pelo *designer* do relatório. Os designers têm opções para ativar e desativar interações visuais e para alterar o comportamento de filtragem cruzada, realce cruzado e exploração predefinidos. 
  
> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são utilizados para distinguir o comportamento descrito aqui do que acontece quando utiliza o painel **Filtros** para filtrar e realçar visualizações.  

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- Se o relatório tiver uma visualização que suporta [desagregação](../power-bi-visualization-drill-down.md), por predefinição, exploração de uma visualização não tem qualquer impacto nas outras visualizações na página do relatório.     
- Se usar visualA para interagir com visualB, filtros de nível visual da visualA serão aplicados a visualB.

## <a name="next-steps"></a>Próximos passos
[Como utilizar filtros de relatório](../power-bi-how-to-report-filter.md)
