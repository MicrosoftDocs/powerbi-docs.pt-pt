---
title: Tipos de Informações suportados pelo Power BI
description: Informações Rápidas e Ver informações com o Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 184aeb1f26e54bb8b8935f2f06ec6cad2e282ecf
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76537921"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Tipos de informações suportados pelo Power BI

Pode pedir ao Power BI que analise os seus dados e encontre tendências e padrões interessantes. Estas tendências e padrões são apresentados sob a forma de elementos visuais que são denominados de *Informações*. 

Para saber como utilizar as Informações, veja [Informações do Power BI](end-user-insights.md)

![um conjunto de informações](media/end-user-insight-types/power-bi-insight.png)

## <a name="how-does-insights-work"></a>Como funcionam as Informações?
O Power BI procura rapidamente vários subconjuntos do seu conjunto de dados. À medida que procura, o Power BI aplica um conjunto de algoritmos sofisticados para obter informações potencialmente interessantes. Os *consumidores* do Power BI podem executar informações em mosaicos do dashboard.

## <a name="some-terminology"></a>Alguma terminologia
O Power BI recorre a algoritmos estatísticos para descobrir informações. Os algoritmos encontram-se listados e descritos na próxima secção deste artigo. Antes de abordarmos os algoritmos, eis as definições de alguns termos que pode não conhecer. 

* **Measure** (Medida) – uma medida é um campo quantitativo (numérico) que pode ser utilizado para fazer cálculos. Os cálculos comuns são soma, média e mínimo. Por exemplo, se a nossa empresa construir e vender skates, as nossas medidas podem ser o número de skates vendidos e o lucro médio por ano.  
* **Dimension** (Dimensão) – as dimensões são dados categóricos (texto). Uma dimensão descreve uma pessoa, objeto, item, produtos, local e hora. Num conjunto de dados, as dimensões são a forma de agrupar *medidas* em categorias úteis. Para a nossa empresa de skates, algumas dimensões podem incluir a análise das vendas (uma medida) por modelo, país ou campanha de marketing.   
* **Correlation** (Correlação) – uma correlação diz-nos como os comportamentos das coisas estão relacionados.  Se os seus padrões de aumento e diminuição forem semelhantes, significa que estão positivamente correlacionados. E se os seus padrões forem opostos, significa que estão negativamente correlacionados. Por exemplo, se as vendas do nosso skate vermelho aumentarem sempre que fizermos uma campanha de marketing televisivo, então, as vendas do skate vermelho e a campanha televisiva estão positivamente correlacionadas.
* **Time series** (Série temporal) – uma série temporal é uma forma de apresentar o tempo como pontos de dados sucessivos. Esses pontos de dados podem ser incrementos tais como segundos, horas, meses ou anos.  
* **Continuous variable** (Variável contínua) – uma variável contínua pode ser qualquer valor entre os seus limites mínimos e máximos, caso contrário, é uma variável discreta. Os exemplos são a temperatura, peso, idade e hora. As variáveis contínuas podem incluir frações ou porções do valor. O número total de skates azuis vendidos é uma variável discreta, uma vez que não podemos vender metade de um skate.  

## <a name="what-types-of-insights-can-you-find"></a>Que tipos de informações é possível encontrar?
Estes são os algoritmos que o Power BI utiliza. 

### <a name="category-outliers-topbottom"></a>Valores Atípicos das Categorias (superior/inferior)
Destaca os casos em que uma ou duas categorias têm valores muito maiores do que outras categorias.  

![Exemplo de Valores atípicos das categorias](./media/end-user-insight-types/pbi-auto-insight-types-category-outliers.png)

### <a name="change-points-in-a-time-series"></a>Alterar os pontos numa série de tempo
Realça os casos em que há alterações significativas nas tendências numa série de tempo de dados.

![Exemplo de alteração dos pontos numa série de tempo](./media/end-user-insight-types/pbi-auto-insight-types-changepoint.png)

### <a name="correlation"></a>Correlação
Deteta casos em que múltiplas medidas mostram um padrão ou tendência semelhante quando desenhadas em relação a uma categoria ou um valor no conjunto de dados.

![Exemplo de Correlação](./media/end-user-insight-types/pbi-auto-insight-types-correlation.png)

### <a name="low-variance"></a>Desvio Baixo
Deteta casos em que os pontos de dados não estão longe da média.

![Exemplo de Desvio Baixo](./media/end-user-insight-types/power-bi-low-variance.png)

### <a name="majority-major-factors"></a>Maioria (Principais fatores)
Encontra casos em que a maioria de um valor total pode ser atribuída a um único fator quando dividida por outra dimensão.  

![Exemplo de principais fatores](./media/end-user-insight-types/pbi-auto-insight-types-majority.png)

### <a name="overall-trends-in-time-series"></a>Tendências gerais na série de tempo
Deteta as tendências ascendentes ou descendentes em dados de série de tempo.

![Exemplo de Tendências gerais na série de tempo](./media/end-user-insight-types/pbi-auto-insight-types-trend.png)

### <a name="seasonality-in-time-series"></a>Sazonalidade na série de tempo
Encontra padrões periódicos nos dados de série de tempo, como a sazonalidade semanal, mensal ou anual.

![Exemplo de Sazonalidade](./media/end-user-insight-types/pbi-auto-insight-types-seasonality-new.png)

### <a name="steady-share"></a>Partilha constante
Realça os casos em que há uma correlação de pai-filho entre a partilha de um valor do filho em relação ao valor geral do pai numa variável contínua.

![Exemplo de Partilha constante](./media/end-user-insight-types/pbi-auto-insight-types-steadyshare.png)

### <a name="time-series-outliers"></a>Valores atípicos de série de tempo
Para dados numa série de tempo, deteta quando há datas ou horas específicas com valores significativamente diferentes dos outros valores de data/hora.

![Exemplo de Valores atípicos de série de tempo](./media/end-user-insight-types/pbi-auto-insight-types-time-series-outliers.png)

## <a name="next-steps"></a>Próximos passos
[Informações do Power BI](end-user-insights.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

