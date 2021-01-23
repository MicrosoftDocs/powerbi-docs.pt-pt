---
title: Monitorizar o Power BI Embedded
description: Comece aqui para aprender a monitorizar o Power BI Incorporado.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: 1b8ebbd7913bc5763f9f4dd8576fbc4783e8d531
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690791"
---
# <a name="monitor-power-bi-embedded"></a>Monitorizar o Power BI Embedded

Quando você tem aplicações críticas e processos de negócio contando com recursos Azure, você quer monitorizar esses recursos para sua disponibilidade, desempenho e funcionamento. Este artigo descreve os dados de monitorização gerados pelo Power BI Embedded e como pode utilizar as funcionalidades do Azure Monitor para analisar e alertar estes dados.

## <a name="monitor-overview"></a>Visão geral do monitor

A **página geral** no portal Azure para cada instância Power BI *Incorporada,* inclui as seguintes informações:

* **Grupo de recursos** - O [grupo de recursos](/azure/azure-resource-manager/management/overview#resource-groups) a que a instância pertence
* **Estado** - O estado da sua instância embutida em Power BI
* **Localização** - A localização da sua instância embutida em Power BI
* **Nome do recurso** - O nome da sua instância Power BI Incorporado
* **SKU** - O SKU o seu exemplo incorporado power BI está a usar
* **Nome de subscrição** - Nome de subscrição incorporado do Power BI
* **ID de subscrição** - O seu ID de subscrição de instância incorporado power BI

## <a name="what-is-azure-monitor"></a>O que é o Azure Monitor?

*Power BI Incorporado* cria dados de monitorização usando [o Azure Monitor,](/azure/azure-monitor/overview)que é um serviço completo de monitorização de pilhas em Azure que fornece um conjunto completo de funcionalidades para monitorizar os seus recursos Azure, além de recursos em outras nuvens e no local.

Comece com o artigo [Monitorar recursos Azure com Azure Monitor,](/azure/azure-monitor/insights/monitor-azure-resource)que descreve os seguintes conceitos:

- O que é o Azure Monitor?
- Custos associados à monitorização
- Dados de monitorização recolhidos em Azure
- Recolha de dados configurado
- Ferramentas padrão em Azure para analisar e alertar sobre os dados de monitorização

As secções seguintes baseiam-se neste artigo, descrevendo os dados específicos recolhidos para o Power BI Incorporado e fornecendo exemplos para configurar a recolha de dados e analisar estes dados com ferramentas Azure.

## <a name="monitoring-data"></a>Monitorizar dados

Power BI Incorporado recolhe os mesmos tipos de dados de monitorização que outros recursos Azure que são descritos na [monitorização de dados a partir de recursos Azure](/azure/azure-monitor/insights/monitor-azure-resource#monitoring-data-from-Azure-resources).

Consulte [a referência de dados incorporada do Power *Bi* de Monitorização](monitor-power-bi-embedded-reference.md) para obter informações detalhadas sobre as métricas e métricas de registos criadas pela Power BI Embedded.

## <a name="collection-and-routing"></a>Recolha e encaminhamento

As métricas da plataforma e o registo de Atividade são recolhidos e armazenados automaticamente, mas podem ser encaminhados para outros locais utilizando uma definição de diagnóstico.  

Os Registos de Recursos não são recolhidos e armazenados até criar uma definição de diagnóstico e encaminhá-los para um ou mais locais.

Consulte [Criar definição de diagnóstico para recolher registos e métricas da plataforma em Azure](/azure/azure-monitor/platform/diagnostic-settings) para o processo detalhado para criar uma definição de diagnóstico utilizando o portal Azure, CLI ou PowerShell. Quando cria uma definição de diagnóstico, especifica quais as categorias de registos a recolher. As categorias de *Power BI Embedded* estão listadas na referência de [dados de monitorização embutidas em Power BI](monitor-power-bi-embedded-reference.md#resource-logs).

### <a name="using-powershell-to-enable-diagnostics"></a>Utilizar o PowerShell para ativar o diagnóstico

Para ativar métricas e diagnósticos de início de sessão utilizando o PowerShell, utilize os comandos listados abaixo. Para saber mais sobre a utilização do PowerShell para permitir diagnósticos, consulte [Criar e configurar um espaço de trabalho Log Analytics no Azure Monitor utilizando o PowerShell](/azure/azure-monitor/platform/powershell-workspace-configuration).

* Para ativar o armazenamento dos registos de diagnóstico numa conta de armazenamento, utilize este comando:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    O ID da conta de armazenamento é o ID do recurso da conta de armazenamento para onde pretende enviar os registos.

* Para ativar a transmissão dos registos de diagnóstico para um hub de eventos, utilize este comando:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* O ID da regra do Azure Service Bus é uma cadeia de caracteres com este formato:

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* Para ativar o envio de registos de diagnóstico para uma área de trabalho do Log Analytics, utilize este comando:

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* Para obter o ID do recurso da área de trabalho do Log Analytics, utilize o seguinte comando:

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

Pode combinar estes parâmetros para ativar várias opções de saída.

As métricas e registos que pode recolher são discutidos nas seguintes secções.

## <a name="analyzing-metrics"></a>Análise de métricas

Pode analisar métricas para *Power BI Incorporado* com métricas de outros serviços Azure usando métricas exploradores abrindo **métricas** a partir do menu **Azure Monitor.** Consulte [o Azure Metrics Explorer](/azure/azure-monitor/platform/metrics-getting-started) para obter detalhes sobre a utilização desta ferramenta.

Para obter uma lista das métricas da plataforma recolhidas para Power BI Incorporado, consulte [métricas de referência de dados *incorporadas em Power Desembutos de Energia de* Monitorização](monitor-power-bi-embedded-reference.md#metrics)  

Para referência, pode ver uma lista de [todas as métricas de recursos suportadas no Azure Monitor](/azure/azure-monitor/platform/metrics-supported).

## <a name="analyzing-logs"></a>Análise de registos

Os dados em Registos monitores Azure são armazenados em tabelas onde cada mesa tem o seu próprio conjunto de propriedades únicas.  

Todos os registos de recursos no Azure Monitor têm os mesmos campos seguidos por campos específicos de serviço. O esquema comum é delineado no [esquema de registo de recursos do Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-schema#top-level-resource-logs-schema) O esquema de registos de recursos incorporados power BI encontra-se na Referência de [Dados Incorporados Power BI](monitor-power-bi-embedded-reference.md#schemas).

O [registo de Atividades](/azure/azure-monitor/platform/activity-log) é um Azure de login de plataforma que fornece informações sobre eventos de nível de subscrição. Pode vê-lo de forma independente ou encaminhá-lo para Registos do Monitor Azure, onde pode fazer consultas muito mais complexas usando o Log Analytics.  

Para obter uma lista dos tipos de registos de recursos recolhidos para Power BI Incorporado, consulte [a referência de dados incorporada ao Power BI de monitorização,](monitor-power-bi-embedded-reference.md#resource-logs) consulte a referência de dados incorporada ao Power BI de monitorização  

Para obter uma lista das tabelas utilizadas pelos Registos do Monitor Azure e consultada por Log Analytics, consulte [a referência de dados incorporada ao Power BI de monitorização](monitor-power-bi-embedded-reference.md#azure-monitor-logs-tables)  

### <a name="sample-kusto-queries"></a>Experimente consultas kusto

> [!IMPORTANT]
> Quando seleciona **Logs** do menu Power BI Embedded, o Log Analytics é aberto com o âmbito de consulta definido para o recurso atual Power BI Incorporado. Isto significa que as consultas de registo só incluirão dados desse recurso. Se pretender executar uma consulta que inclua dados de outros recursos ou dados incorporados do Power BI de outros serviços Azure, selecione **Logs** do menu **Azure Monitor.** Consulte [o âmbito de consulta de registo e o intervalo de tempo no Azure Monitor Log Analytics](/azure/azure-monitor/log-query/scope/) para obter mais detalhes.

Abaixo estão exemplos de consulta para monitorizar o Power BI Incorporado.

* Esta é uma consulta que é completada em menos de cinco minutos (300.000 milissegundos).

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```
* Identificar os nomes de capacidade.

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```

## <a name="alerts"></a>Alertas

Os alertas do Azure Monitor notificam-no proativamente quando forem encontradas condições importantes nos seus dados de monitorização. Permitem identificar e resolver problemas no seu sistema antes que os seus clientes os percebam. Pode definir alertas em [métricas,](/azure/azure-monitor/platform/alerts-metric-overview) [registos](/azure/azure-monitor/platform/alerts-unified-log)e no registo de [atividades](/azure/azure-monitor/platform/activity-log-alerts).

## <a name="next-steps"></a>Próximas etapas

Pode saber mais sobre o registo de diagnóstico de recursos do Azure.

>[!div class="nextstepaction"]
>[Referência de dados incorporada do Power BI de monitorização](monitor-power-bi-embedded-reference.md)

>[!div class="nextstepaction"]
>[Monitorizar os recursos do Azure com o Azure Monitor](/azure/azure-monitor/insights/monitor-azure-resource)