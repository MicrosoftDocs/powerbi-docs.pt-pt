---
title: Monitorizar capacidades do Power BI Premium com o portal de administração
description: Utilize o portal de administração do Power BI para monitorizar as suas capacidades Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564898"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorizar capacidades no Portal de administração

O **estado de funcionamento** separador a **definições de capacidade** área no portal de administração fornece uma resumo sobre as cargas de trabalho ativadas e capacidade de métricas.  

![Separador de estado de funcionamento de capacidade no portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Se precisar de métricas mais abrangentes, utilize o [métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) aplicação. A aplicação fornece desagregar e filtragem, e as métricas mais detalhadas para quase todos os aspectos que afetam o desempenho de capacidade. Para obter mais informações, consulte [capacidades Premium do Monitor com a aplicação](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Métricas do sistema

Sobre o **estado de funcionamento** separador, com o nível mais alto, a utilização da CPU e utilização de memória fornecer uma vista rápida das métricas mais importantes para a capacidade. Estas métricas são cumulativas, incluindo todas as cargas de trabalho a capacidade de ativadas.

| **Métrica** | **Descrição** |
| --- | --- |
| UTILIZAÇÃO DA CPU | Utilização média de CPU, como uma percentagem do total de CPU disponível. |
| UTILIZAÇÃO DA MEMÓRIA | Média de utilização de memória em gigabytes (GB).|

## <a name="workload-metrics"></a>Métricas de carga de trabalho

Para cada carga de trabalho ativada para a capacidade. Utilização da CPU e utilização de memória são apresentados.

| **Métrica** | **Descrição** |
| --- | --- |
| UTILIZAÇÃO DA CPU | Utilização média de CPU, como uma percentagem do total de CPU disponível. |
| UTILIZAÇÃO DA MEMÓRIA | Média de utilização de memória em gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Métricas de carga de trabalho detalhados

Cada carga de trabalho tem métricas adicionais. O tipo de métricas apresentadas dependem da carga de trabalho. Para ver métricas detalhadas para cargas de trabalho, clique em expansão (seta).

![Expanda o estado de funcionamento da carga de trabalho](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Fluxos de Dados

##### <a name="dataflow-operations"></a>Operações de fluxo de dados

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem Total | o número total de atualizações de cada fluxo de dados. |
| Contagens com Êxito | Atualizações com êxito total para cada fluxo de dados.|
| Duração média (min) | a duração média da atualização do fluxo de dados, em minutos |
| Duração Máx. (min) | a duração da atualização de execução mais longa do fluxo de dados, em minutos. |
| Tempo médio de espera (min) | o atraso médio entre a hora agendada e o início da atualização do fluxo de dados, em minutos. |
| Tempo de espera de Max (min) | o tempo máximo de espera do fluxo de dados, em minutos.  |

#### <a name="datasets"></a>Conjuntos de Dados

##### <a name="refresh"></a>Atualizar

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem Total | as atualizações totais de cada conjunto de dados. |
| Contagens com Êxito | Atualizações com êxito total para cada conjunto de dados. |
| Contagem de Falhas | Total de atualizações falhou para cada conjunto de dados. |
| Taxa de êxito  | Número de atualizações com êxito, dividido pelas atualizações total para medir. Fiabilidade. |
| Duração média (min) | a duração média da atualização do conjunto de dados, em minutos.  |
| Duração Máx. (min) | a duração da atualização de execução mais longa do conjunto de dados, em minutos. |
| Tempo médio de espera (min) | o atraso médio entre a hora agendada e o início da atualização do conjunto de dados, em minutos. |
| Tempo de espera de Max (min) | o tempo máximo de espera do conjunto de dados, em minutos. |

##### <a name="query"></a>Consulta

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem Total | o número total de consultas executadas do conjunto de dados. |
| Duração Média (ms) |a duração média das consultas do conjunto de dados, em milissegundos|
| Duração Máxima (ms) |a duração das consultas de execução mais longa no conjunto de dados, em milissegundos. |
| Tempo Médio de Espera (ms) |o tempo médio de espera da consulta para o conjunto de dados, em milissegundos. |
| Tempo máx. de espera (ms) |a duração da consulta de espera mais longa no conjunto de dados, em milissegundos. |

##### <a name="eviction"></a>Expulsão

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de modelo | O número total de expulsões de conjunto de dados para esta capacidade. Quando uma capacidade sofre uma pressão de memória, o nó expulsa um ou mais conjuntos de dados da memória. Os conjuntos de dados que estiverem inativos (sem qualquer operação de consulta/atualização em execução) são os primeiros a serem expulsos. Em seguida, a ordem de expulsão é feita com base no critério "menos recentemente utilizado" (LRU). |

#### <a name="paginated-reports"></a>Relatórios Paginados

##### <a name="report-execution"></a>Execução de relatórios

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de execução  | O número de vezes que o relatório foi foi executado e visualizado por utilizadores.|

##### <a name="report-usage"></a>Relatório de utilização

| **Métrica** | **Descrição** |
| --- | --- |
| Contagens com Êxito | O número de vezes que o relatório tiver sido visto por um utilizador. |
| Contagem de Falhas |O número de vezes que o relatório tiver sido visto por um utilizador.|
| Contagem de Linhas |o número de linhas de dados no relatório. |
| Duração de obtenção de dados (ms) |o tempo médio que demora a obter os dados para o relatório, em milissegundos. As durações longas podem indicar consultas lentas ou outros problemas na origem dos dados.  |
| Duração de processamento (ms) |o tempo médio que demora a processar os dados para um relatório, em milissegundos. |
| Duração de processamento (ms) |o tempo médio que demora a compor um relatório no browser, em milissegundos. |

> [!NOTE]
> Detalhadas métricas para o **IA** carga de trabalho ainda não estão disponíveis.

## <a name="next-steps"></a>Próximos passos

Agora que tem uma noção de como monitorizar as capacidades do Power BI Premium, saiba mais sobre as capacidades de otimização.

> [!div class="nextstepaction"]
> [Otimizar as capacidades do Power BI Premium](service-premium-capacity-optimize.md)
