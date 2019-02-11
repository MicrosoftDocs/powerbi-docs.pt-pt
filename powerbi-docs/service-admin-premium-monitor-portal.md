---
title: Monitorizar capacidades do Power BI Premium com o portal de administração
description: Utilize o portal de administração do Power BI para monitorizar as suas capacidades Premium.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 59097c07719e4bb8db188e8a86db377076aea7a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794105"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorizar capacidades no Portal de administração

Este artigo explica a forma como pode utilizar a área Definições de capacidade no Portal de Administração para obter uma vista rápida do desempenho da sua capacidade.  Para obter as métricas mais detalhadas sobre a sua capacidade, o melhor é utilizar a aplicação [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md).

## <a name="capacity-metrics"></a>Métricas de capacidade

A área **Definições de capacidade** do portal de administração fornece quatro medidores que indicam as cargas colocadas e os recursos utilizados pela sua capacidade nos últimos sete dias. Estes quatro mosaicos trabalham numa janela de tempo por hora, que indica quantas horas nos últimos sete dias a métrica correspondente foi superior a 80%. Esta métrica indica uma degradação potencial para a experiência do utilizador final.

![Utilização nos 7 dias](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrica** | **Descrição** |
| --- | --- |
| CPU |Número de vezes que a CPU excedeu os 80% de utilização. |
| Degradação de Memória |Representa a pressão de memória nos seus núcleos de back-end. Especificamente, esta é uma métrica da frequência com que os conjuntos de dados são limpos da memória devido à pressão de memória resultante da utilização de múltiplos conjuntos de dados. |
| Utilização de Memória |Utilização de memória média, representada em gigabytes (GB). |
| DQ/s | Número de vezes que a contagem de DirectQueries e Ligações em Direto excedeu os 80% de limite. <br>  O número total de consultas do DirectQuery e de ligação em direto por segundo é limitado. Os limites são 30/s para P1, 60/s para P2 e 120/s para P3.  O número de consultas do DirectQuery e de ligação em direto contam para a limitação indicada acima. Por exemplo, se tiver 15 DirectQueries e 15 ligações em direto num segundo, atingiu a limitação<br> Isto aplica-se igualmente às ligações no local e na cloud. |
|  |  |

As métricas refletem a utilização ao longo da semana anterior.  Se quiser consultar uma vista mais detalhada das métricas, pode fazê-lo ao clicar num dos mosaicos de resumo.  Isto permite-lhe ter acesso a gráficos detalhados para cada uma das métricas da sua capacidade premium. O gráfico seguinte mostra os detalhes da métrica de CPU.

![Gráfico de utilização detalhado da CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Estes gráficos são resumidos à hora para a semana anterior e podem ajudar a isolar alturas em que tenham ocorrido eventos especificamente relacionados com o desempenho na sua capacidade premium.

Também pode exportar os dados subjacentes a qualquer uma das métricas para um ficheiro .csv.  Esta exportação irá fornecer-lhe informações detalhadas em intervalos de três minutos para cada dia da semana anterior.

## <a name="next-steps"></a>Próximos passos

Agora que tem uma noção de como monitorizar as capacidades do Power BI Premium, saiba mais sobre as capacidades de otimização.

> [!div class="nextstepaction"]
> [Gestão e otimização do recurso de capacidades do Power BI Premium](service-premium-understand-how-it-works.md)
