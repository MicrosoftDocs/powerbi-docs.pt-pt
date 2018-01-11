---
title: Tipos de Quick Insights suportados pelo Power BI
description: Quick Insights com o Power BI.
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/03/2017
ms.author: mihart
ms.openlocfilehash: 13f5614cf121b17d8ae4dff9653f5789372f7f49
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="types-of-quick-insights-supported-by-power-bi"></a>Tipos de Quick Insights suportados pelo Power BI
## <a name="how-does-quick-insights-work"></a>Como funciona o Quick Insights?
O Power BI procura rapidamente diferentes subconjuntos do conjunto de dados enquanto aplica um grupo de algoritmos sofisticados para detetar informações potencialmente interessantes. O Power BI analisa o máximo de um conjunto de dados possível num período de tempo atribuído.

Pode executar informações rápidas em relação a um conjunto de dados ou mosaico (Informações Relacionadas).   

## <a name="what-types-of-quick-insights-can-we-find"></a>Que tipos de Informações Rápidas é possível encontrar?
Estes são alguns dos algoritmos que usamos:

## <a name="category-outliers-topbottom"></a>Valores Atípicos das Categorias (superior/inferior)
Realça os casos em que, para uma medida no modelo, um ou dois membros de uma dimensão têm valores muito mais altos do que outros membros da dimensão.  

![](media/service-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Alterar os pontos numa série de tempo
Realça os casos em que há alterações significativas nas tendências numa série de tempo de dados.

![](media/service-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Correlação
Deteta os casos em que várias medidas mostram uma correlação entre si quando representadas numa dimensão no conjunto de dados.

![](media/service-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Desvio Baixo
Deteta casos em que os pontos de dados não estão longe da média.

![](media/service-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Maioria (Principais fatores)
Encontra casos em que a maioria de um valor total pode ser atribuída a um único fator quando dividida por outra dimensão.  

![](media/service-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Tendências gerais na série de tempo
Deteta as tendências ascendentes ou descendentes em dados de série de tempo.

![](media/service-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Sazonalidade na série de tempo
Encontra padrões periódicos nos dados de série de tempo, como a sazonalidade semanal, mensal ou anual.

![](media/service-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Partilha constante
Realça os casos em que há uma correlação de pai-filho entre a partilha de um valor do filho em relação ao valor geral do pai numa variável contínua.

![](media/service-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Valores atípicos de série de tempo
Para dados numa série de tempo, deteta quando há datas ou horas específicas com valores significativamente diferentes dos outros valores de data/hora.

![](media/service-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Próximos passos
[Power BI Quick Insights](service-insights.md)

Se é proprietário de um conjunto de dados, [otimize-o para as Informações Rápidas](service-insights-optimize.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

