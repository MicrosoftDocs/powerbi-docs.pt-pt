---
title: Compreender como os elementos visuais interagem num relatório
description: Documentação para os utilizadores finais do Power BI que explica como os elementos visuais interagem numa página de relatório.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: b95df5c32d9058e4480d7af5e226a971ba581144
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256283"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Forma como os elementos visuais efetuam a filtragem cruzada entre si num relatório do Power BI
Um dos recursos incríveis do Power BI é a forma como estão interligados todos os elementos visuais numa página de relatório. Se selecionar um ponto de dados num dos elementos visuais, serão alterados todos os outros elementos visuais na página que contêm esses dados, com base nessa seleção. 

![vídeo de interação dos elementos visuais](media/end-user-interactions/interactions.gif)

Por predefinição, selecionar um ponto de dados numa visualização numa página de relatório irá executar a filtragem cruzada, realçar de forma cruzada e explorar as outras visualizações na página. 

Isto pode ser útil para identificar como é que um valor nos seus dados contribui para outro. Por exemplo, selecionar o segmento Moderação no gráfico em anel realça a contribuição desse segmento para cada coluna no gráfico Total de Unidades por Mês e filtra o gráfico de linhas à direita.

![Imagem de interação dos elementos visuais](media/end-user-interactions/power-bi-interactions.png)

Consulte [Sobre filtragem e realce](../power-bi-reports-filters-and-highlighting.md). 

O modo exato como interagem os elementos visuais numa página é definido pelo *designer* do relatório. Os designers têm opções para ativar e desativar interações visuais e para alterar o comportamento de filtragem cruzada, realce cruzado e exploração predefinidos. 
  
> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são utilizados para distinguir o comportamento descrito aqui do que acontece quando utiliza o painel **Filtros** para filtrar e realçar visualizações.  

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- Se o seu relatório tiver uma visualização que suporte a [exploração](../power-bi-visualization-drill-down.md) por predefinição, a exploração de uma visualização não tem impacto nas outras visualizações na página de relatório.     
- Se utilizar o elemento visual A para interagir com o elemento visual B, os filtros ao nível do elemento visual A serão aplicados ao elemento visual B.

## <a name="next-steps"></a>Próximos passos
[Como utilizar filtros de relatório](../power-bi-how-to-report-filter.md)
