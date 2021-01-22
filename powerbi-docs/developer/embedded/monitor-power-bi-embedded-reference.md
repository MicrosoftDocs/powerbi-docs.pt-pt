---
title: Referência de dados incorporada do Power BI de monitorização
description: Material de referência importante necessário quando monitoriza o Power BI Incorporado.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: fc6b9dd4d50d665211324d1b6c05e62468fc034d
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690805"
---
# <a name="monitoring-power-bi-embedded-data-reference"></a>Referência de dados incorporada do Power BI de monitorização

Consulte [o Monitor Power BI Incorporado](monitor-power-bi-embedded.md) para obter detalhes sobre a recolha e análise de dados de monitorização para Power BI Incorporado.

## <a name="metrics"></a>Métricas

Esta secção lista todas as métricas da plataforma recolhidas automaticamente para Power BI Incorporado.  

|Tipo métrico | Fornecedor de recursos / Espaço de nomes tipo<br/> e ligação com métricas individuais |
|-------|-----|
| Capacidades | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities) |

### <a name="capacities"></a>Capacidades

Fornecedor e Tipo de Recursos: [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities)

| Name | Metric | Unidade | Descrição |
|:---|:-------|:-----|:------------|
|Memória (Gen1) |memory_metric               |Bytes        |Memória. Alcance 0-3 GB para A1, 0-5 GB para A2, 0-10 GB para A3, 0-25 GB para A4, 0-50 GB para A5 e 0-100 GB para A6. Suportado apenas para recursos Power BI Embedded Geração 1. |
|Thrashing de memória (Conjuntos de dados) (Gen1) |memory_thrashing_metric     |Percentagem      |Memória média a bater. Suportado apenas para recursos Power BI Embedded Geração 1. |
|Utilização elevada do QPU (Gen1) |qpu_high_utilization_metric |de palavras        |QPU Alta Utilização em último minuto, 1 para alta utilização QPU, caso contrário 0. Suportado apenas para recursos Power BI Embedded Geração 1. |
|Duração da consulta (Conjuntos de dados) (Gen1) |Queriaduração               |Milissegundos |Duração da consulta DAX no último intervalo. Suportado apenas para recursos Power BI Embedded Geração 1. |
|Comprimento da fila de trabalho da piscina de consulta (conjuntos de dados) (Gen1) |QueryPoolJobQueueLength     |de palavras        |Número de empregos na fila da piscina de fios de consulta. Suportado apenas para recursos Power BI Embedded Geração 1. |

## <a name="metric-dimensions"></a>Dimensões métricas

Para obter mais informações sobre as dimensões métricas, consulte [métricas multidimensionais.](/azure/azure-monitor/platform/data-platform-metrics#multi-dimensional-metrics)

Power BI Incorporado não tem métricas que contenham dimensões.

## <a name="resource-logs"></a>Registos do recurso

Esta secção lista os tipos de registos de recursos que pode recolher para Power BI Incorporado.

Para referência, consulte uma lista de todos os tipos de categorias de registos de [recursos suportados no Azure Monitor](/azure/azure-monitor/platform/resource-logs-schema).

Esta secção lista todos os tipos de categoria de registo de recursos recolhidos para Power BI Embedded.  

|Tipo de registo de recursos | Fornecedor de recursos / Espaço de nomes tipo<br/> e ligação com métricas individuais |
|-------|-----|
| Capacidades | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/resource-logs-categories#microsoftpowerbidedicatedcapacities) |

## <a name="azure-monitor-logs-tables"></a>Tabelas de registos do monitor Azure

Esta secção refere-se a todas as tabelas Azure Monitor Logs Kusto relevantes para o Power BI Incorporado e disponíveis para consulta por Log Analytics.

|Tipo de Recurso | Notas |
|-------|-----|
| [Power BI Embedded](/azure/azure-monitor/reference/tables/tables-resourcetype#power-bi-embedded) |Veja uma lista de tabelas abaixo |

### <a name="power-bi-embedded"></a>Power BI Embedded

| Tabela |  Descrição |
|:---------|:-------------|------------------|
| [AzureActivity](/azure/azure-monitor/reference/tables/azureactivity) | Entradas a partir do registo de Atividades Azure que fornecem informações sobre quaisquer eventos de nível de subscrição ou de grupo de gestão que ocorreram em Azure.    |                             |                                                   | 
| [AzureDiagnostics](/azure/azure-monitor/reference/tables/azurediagnostics)   | Armazena registos de recursos para serviços Azure que utilizam o modo Azure Diagnostics. Os registos de recursos descrevem o funcionamento interno dos recursos da Azure. |
| [AzureMetrics](/azure/azure-monitor/reference/tables/azuremetrics)   | Dados métricos emitidos pelos serviços da Azure que medem a sua saúde e desempenho. |

Para obter uma referência de todos os registos do Monitor Azure / Tabelas de Azure Monitor Analytics, consulte a referência da [tabela de registo do monitor Azure](/azure/azure-monitor/reference/tables/tables-resourcetype).

## <a name="activity-log"></a>Registo de atividades

Pode selecionar as categorias **Motor** e/ou **AllMetrics**.

### <a name="engine"></a>Motor

A categoria do motor instrui o recurso para registar os eventos listados abaixo. Para cada evento, existem propriedades.

|     Nome do Evento     |     Descrição do Evento     |
|----------------------------|----------------------------------------------------------------------------------|
|    Início de Sessão de Auditoria    |    Regista todas as ligações novas dos eventos de motor desde o início do rastreio.    |
|    Inicialização de Sessão    |    Regista todos os eventos de inicialização da sessão desde o início do rastreio.    |
|    Início da Consulta Vertipaq    |    Regista todos os eventos de início da consulta SE VertiPaq desde o início do rastreio.    |
|    Início da Consulta    |    Regista todos os eventos de início da consulta desde o início do rastreio.    |
|    Fim da Consulta    |    Regista todos os eventos de fim da consulta desde o início do rastreio.    |
|    Fim da Consulta Vertipaq    |    Regista todos os eventos de fim da consulta SE VertiPaq desde o início do rastreio.    |
|    Fim de Sessão de Auditoria    |    Regista todos os eventos de ligação interrompida do motor desde o início do rastreio.    |
|    Error    |    Regista todos eventos de erro do motor desde o início do rastreio.    |

#### <a name="event-example"></a>Exemplo do evento

A tabela abaixo mostra um exemplo de evento.

| Nome da Propriedade | Exemplo de Fim da Consulta Vertipaq | Descrição da Propriedade |
|---|---|---|
| EventClass | XM_SEQUERY_END | A Classe de Evento é utilizada para categorizar os eventos. |
| EventSubclass | 0 | A Subclasse de Evento fornece informações adicionais sobre cada classe de evento. (por exemplo, 0: Análise VertiPaq) |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | ID da atividade raiz. |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | Hora em que o evento começou, quando disponível. |
| StartTime | 2018-04-06T18:30:11.9137358Z | Hora em que o evento começou, quando disponível. |
| JobID | 0 | ID da Tarefa em curso. |
| ObjectID | 464 | ID do Objeto |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | Hora em que o evento terminou. |
| Duração | 0 | Período de tempo (em milissegundos) despendido pelo evento. |
| SessionType | User | Tipo de sessão (a entidade que causou a operação). |
| ProgressTotal | 0 | Progresso total. |
| IntegerData | 0 | Dados de números inteiros. |
| Gravidade | 0 | Nível de gravidade de uma exceção. |
| Com êxito | 1 | 1 = êxito. 0 = falha (por exemplo, 1 significa que uma verificação de permissões foi efetuada com êxito e 0 significa que essa verificação falhou). |
| Error | 0 | Número do erro de um evento específico. |
| ConnectionID | 3 | ID de ligação exclusivo. |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | ID do conjunto de dados no qual a instrução do utilizador está em execução. |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | GUID de Sessão. |
| SPID | 180 | ID de processo do servidor. Este ID identifica de forma exclusiva uma sessão de utilizador. Corresponde diretamente ao GUID de sessão utilizado pelo XML/A. |
| ClientProcessID | nulo | O ID de processo da aplicação cliente. |
| ApplicationName | nulo | Nome da aplicação cliente que criou a ligação ao servidor. |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | O nome do recurso de capacidades do Power BI Embedded. |

### <a name="allmetrics"></a>AllMetrics

Ao marcar a opção **AllMetrics**, são registados os dados de todas as métricas que pode utilizar com um recurso do Power BI Embedded.

A tabela que se segue lista as operações relacionadas com o Power BI Embedded que podem ser criadas no registo de Atividade.

## <a name="schemas"></a>Esquemas

Power BI Incorporado utiliza o **esquema dedicado power BI.**

## <a name="next-steps"></a>Próximos passos

>[!div class="nextstepaction"]
>[Monitor Azure Power BI Incorporado](monitor-power-bi-embedded.md)

>[!div class="nextstepaction"]
>[Registo de diagnóstico de recursos do Azure](/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

>[!div class="nextstepaction"]
>[Set-AzureRmDiagnosticSetting](/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)