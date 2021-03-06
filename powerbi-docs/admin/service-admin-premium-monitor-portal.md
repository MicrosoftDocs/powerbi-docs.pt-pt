---
title: Monitorizar capacidades do Power BI Premium com o portal de administração
description: Utilize o portal de administração do Power BI para monitorizar as suas capacidades Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: b6f6b819b5c31f655d0c0dc43d8852cb34b5a7a2
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512062"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorizar capacidades no Portal de administração

O separador **Estado de Funcionamento** na área **Definições de capacidade** no portal de Administração fornece um resumo de métrica sobre a sua capacidade e cargas de trabalho ativadas.  

![Separador Estado de Funcionamento de Capacidade no portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Se precisar de métricas mais abrangentes, utilize a aplicação [Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md). A aplicação permite desagregar e filtrar, dando as métricas mais detalhadas para praticamente qualquer aspeto que influencia o desempenho de capacidade. Para saber mais, consulte [Monitorizar as capacidades Premium com a aplicação](service-admin-premium-monitor-capacity.md).

> [!IMPORTANT]
> Se a sua capacidade do Power BI Premium tiver uma alta utilização de recursos, resultando em problemas de fiabilidade ou desempenho, pode receber e-mails de notificação para identificar e resolver o problema. Pode ser uma forma simplificada de resolver problemas de capacidades sobrecarregadas. Para obter mais informações, veja [notificações de fiabilidade e capacidade](service-interruption-notifications.md#capacity-and-reliability-notifications).

> [!NOTE]
> O Power BI Premium lançou recentemente uma nova versão do Premium, denominada **Premium Gen2**, que está atualmente em pré-visualização. O Premium Gen2 irá simplificar a gestão de capacidades Premium e reduzirá a sobrecarga de gestão. Para obter mais informações, veja [Power BI Premium Generation 2 (pré-visualização)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="system-metrics"></a>Métricas de Sistema

No separador **Estado de Funcionamento**, no nível mais elevado, a utilização de CPU e a utilização de memória fornecem uma vista rápida das métricas mais importantes da capacidade. Estas métricas são cumulativas, incluindo todas as cargas de trabalho ativadas da capacidade.

| **Métrica** | **Descrição** |
| --- | --- |
| UTILIZAÇÃO DA CPU | Utilização média de CPU como percentagem da CPU total disponível. |
| UTILIZAÇÃO DA MEMÓRIA | Utilização de memória média em gigabytes (GB).|

## <a name="workload-metrics"></a>Métricas da carga de trabalho

Para cada carga de trabalho ativada para a capacidade. São mostradas a utilização de CPU e a utilização de memória.

| **Métrica** | **Descrição** |
| --- | --- |
| UTILIZAÇÃO DA CPU | Utilização média de CPU como percentagem da CPU total disponível. |
| UTILIZAÇÃO DA MEMÓRIA | Utilização de memória média em gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Métricas da carga de trabalho detalhadas

Cada carga de trabalho tem métricas adicionais. O tipo de métrica mostrada depende da carga de trabalho. Para ver as métricas detalhadas de uma carga de trabalho, clique na seta de expansão (para baixo).

![Expandir estado de funcionamento da carga de trabalho](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Fluxos de Dados

##### <a name="dataflow-operations"></a>Operações do Fluxo de Dados

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem Total | o número total de atualizações de cada fluxo de dados. |
| Contagens com Êxito | Número total de atualizações bem-sucedidas de cada fluxo de dados.|
| Duração Média (min) | a duração média da atualização do fluxo de dados, em minutos |
| Duração Máxima (min) | a duração da atualização de execução mais longa do fluxo de dados, em minutos. |
| Tempo Médio de Espera (min) | o atraso médio entre a hora agendada e o início da atualização do fluxo de dados, em minutos. |
| Tempo Máximo de Espera (min) | o tempo máximo de espera do fluxo de dados, em minutos.  |

#### <a name="datasets"></a>Conjuntos de Dados

##### <a name="refresh"></a>Atualizar

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem Total | as atualizações totais de cada conjunto de dados. |
| Contagens com Êxito | Número total de atualizações bem-sucedidas de cada conjunto de dados. |
| Contagem de Falhas | Número total de atualizações falhadas de cada conjunto de dados. |
| Taxa de Êxito  | O número de atualizações bem-sucedidas dividido pelo total de atualizações a medir. fiabilidade. |
| Duração Média (min) | a duração média da atualização do conjunto de dados, em minutos.  |
| Duração Máxima (min) | a duração da atualização de execução mais longa do conjunto de dados, em minutos. |
| Tempo Médio de Espera (min) | o atraso médio entre a hora agendada e o início da atualização do conjunto de dados, em minutos. |
| Tempo Máximo de Espera (min) | o tempo máximo de espera do conjunto de dados, em minutos. |

##### <a name="query"></a>Consulta

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem Total | o número total de consultas executadas do conjunto de dados. |
| Duração Média (ms) |a duração média das consultas do conjunto de dados, em milissegundos|
| Duração Máxima (ms) |a duração das consultas de execução mais longa no conjunto de dados, em milissegundos. |
| Tempo Médio de Espera (ms) |o tempo médio de espera da consulta para o conjunto de dados, em milissegundos. |
| Tempo Máximo de Espera (ms) |a duração da consulta de espera mais longa no conjunto de dados, em milissegundos. |

##### <a name="eviction"></a>Expulsão

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de Modelos | Número total de expulsões de conjunto de dados para esta capacidade. Quando uma capacidade sofre uma pressão de memória, o nó expulsa um ou mais conjuntos de dados da memória. Os conjuntos de dados que estiverem inativos (sem qualquer operação de consulta/atualização em execução) são os primeiros a serem expulsos. Em seguida, a ordem de expulsão é feita com base no critério "menos recentemente utilizado" (LRU). |

#### <a name="paginated-reports"></a>Relatórios Paginados

##### <a name="report-execution"></a>Execução do Relatório

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de Execuções  | O número de vezes que o relatório foi executado e visualizado pelos utilizadores.|

##### <a name="report-usage"></a>Utilização do Relatório

| **Métrica** | **Descrição** |
| --- | --- |
| Contagens com Êxito | O número de vezes que o relatório foi visto por um utilizador. |
| Contagem de Falhas |O número de vezes que o relatório foi visto por um utilizador.|
| Contagem de Linhas |o número de linhas de dados no relatório. |
| Duração de Obtenção de Dados (ms) |o tempo médio que demora a obter os dados para o relatório, em milissegundos. As durações longas podem indicar consultas lentas ou outros problemas na origem dos dados.  |
| Duração do Processamento (ms) |o tempo médio que demora a processar os dados para um relatório, em milissegundos. |
| Duração da Composição (ms) |o tempo médio que demora a compor um relatório no browser, em milissegundos. |

> [!NOTE]
> As métricas detalhadas da carga de trabalho **IA** ainda não estão disponíveis.

## <a name="next-steps"></a>Próximos passos

Agora que tem uma noção de como monitorizar as capacidades do Power BI Premium, saiba mais sobre as capacidades de otimização.

> [!div class="nextstepaction"]
> [Otimizar as capacidades do Power BI Premium](service-premium-capacity-optimize.md)


O Power BI introduziu o Power BI Premium Gen2 como uma oferta de pré-visualização, que melhora a experiência do Power BI Premium nos seguintes aspetos:
* Desempenho
* Licenciamento por utilizador
* Maior dimensionamento
* Métricas melhoradas
* Dimensionamento automático
* Sobrecarga de gestão reduzida

Para obter mais informações sobre o Power BI Premium Gen2, veja [Power BI Premium Generation 2 (pré-visualização)](service-premium-what-is.md#power-bi-premium-generation-2-preview).