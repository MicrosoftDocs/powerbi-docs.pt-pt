---
title: "Tipos de Informações suportados pelo Power BI"
description: "Informações Rápidas e Ver informações com o Power BI."
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
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: c295eea46e6e8d182147f877548a385ce4602bad
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="types-of-insights-supported-by-power-bi"></a>Tipos de informações suportados pelo Power BI
## <a name="how-does-insights-work"></a>Como funcionam as Informações?
O Power BI procura rapidamente diferentes subconjuntos do conjunto de dados enquanto aplica um grupo de algoritmos sofisticados para detetar informações potencialmente interessantes. O Power BI analisa o máximo de um conjunto de dados possível num período de tempo atribuído.

Pode executar as informações para um conjunto de dados ou um mosaico do dashboard.   

## <a name="what-types-of-insights-can-we-find"></a>Que tipos de informações é possível encontrar?
Estes são alguns dos algoritmos que usamos:

## <a name="category-outliers-topbottom"></a>Valores Atípicos das Categorias (superior/inferior)
Realça os casos em que, para uma medida no modelo, um ou dois membros de uma dimensão têm valores muito mais altos do que outros membros da dimensão.  

![Exemplo de Valores atípicos das categorias](media/service-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Alterar os pontos numa série de tempo
Realça os casos em que há alterações significativas nas tendências numa série de tempo de dados.

![Exemplo de alteração dos pontos numa série de tempo](media/service-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Correlação
Deteta os casos em que várias medidas mostram uma correlação entre si quando representadas numa dimensão no conjunto de dados.

![Exemplo de Correlação](media/service-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Desvio Baixo
Deteta casos em que os pontos de dados não estão longe da média.

![Exemplo de Desvio Baixo](media/service-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Maioria (Principais fatores)
Encontra casos em que a maioria de um valor total pode ser atribuída a um único fator quando dividida por outra dimensão.  

![Exemplo de Principais fatores](media/service-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Tendências gerais na série de tempo
Deteta as tendências ascendentes ou descendentes em dados de série de tempo.

![Exemplo de Tendências gerais na série de tempo](media/service-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Sazonalidade na série de tempo
Encontra padrões periódicos nos dados de série de tempo, como a sazonalidade semanal, mensal ou anual.

![Exemplo de Sazonalidade](media/service-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Partilha constante
Realça os casos em que há uma correlação de pai-filho entre a partilha de um valor do filho em relação ao valor geral do pai numa variável contínua.

![Exemplo de Partilha constante](media/service-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Valores atípicos de série de tempo
Para dados numa série de tempo, deteta quando há datas ou horas específicas com valores significativamente diferentes dos outros valores de data/hora.

![Exemplo de Valores atípicos de série de tempo](media/service-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Próximos passos
[Informações do Power BI](service-insights.md)

Se for o proprietário de um conjunto de dados, [otimize-o para as informações](service-insights-optimize.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

