---
title: (Pré-visualização pública) de monitorização de desempenho de gateway
description: Este artigo fornece informações sobre como monitorizar o desempenho das atividades de gateway de dados no local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535373"
---
# <a name="gateway-performance-monitoring-public-preview"></a>(Pré-visualização pública) de monitorização de desempenho de gateway

Para monitorizar o desempenho, os administradores de gateway tem tradicionalmente dependia de monitorização manualmente os contadores de desempenho por meio da ferramenta Monitor de desempenho do Windows. Oferecemos agora o registo de consulta adicionais e um [o ficheiro de modelo de PBI de desempenho do Gateway](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) para visualizar os resultados. Esta funcionalidade fornece novas informações sobre a utilização do gateway e permite-lhe resolver as consultas com desempenho lentas.

> [!NOTE]
> Esta funcionalidade está atualmente disponível apenas para o gateway de dados no local no modo padrão e não para o modo pessoal.

## <a name="enable-performance-logging"></a>Ativar o registo de desempenho

Para ativar esta funcionalidade, efetue as seguintes alterações para o *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* de ficheiros a "\Program Files\On-gateway de dados locais" pasta:

1. Atualização **QueryExecutionReportOn** ao _verdadeiro_ para ativar o registo adicional para consultas executadas com o gateway. Ativar esta opção cria o relatório de execução de consulta e os ficheiros de relatório de agregação de execução de consulta.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Atualização **SystemCounterReportOn** ao _verdadeiro_ para ativar o registo adicional de memória e de contadores de CPU do sistema. Ativar esta opção cria o ficheiro de relatório de agregação de contador do sistema.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Existem outros valores no ficheiro de configuração que pode atualizar conforme necessário.

    - **ReportFilePath**: Determina o caminho em que os três ficheiros de registo são armazenados. Por predefinição, este caminho é "\Users\PBIEgwService\AppData\Local\Microsoft\On-premises dados gateway\Report" ou "Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On local dados gateway\Report", dependendo da versão de SO. Se usar uma conta de serviço para o gateway que _PBIEgwService_, substitua esta parte do caminho com o nome de conta de serviço.
    - **ReportFileCount**: Determina o número de ficheiros de registo de cada tipo de manter. O valor predefinido é 10.
    - **ReportFileSizeInBytes**: Determina o tamanho do ficheiro a manter. O valor predefinido é 104857600.
    - **QuerExecutionAggregationTimeInMinutes**: Determina o número de minutos para que as informações de execução da consulta são agregadas. O valor predefinido é 5.
    - **SystemCounterAggregationTimeInMinutes**: Determina o número de minutos para que os contadores do sistema é agregado. O valor predefinido é 5.

1. Após fazer as alterações ao ficheiro de configuração, reinicie o gateway para estes valores de configuração entrem em vigor. Agora começará a ver os ficheiros de relatório a ser gerados na localização que especificou para **ReportFilePath**.

    > [!NOTE]
    > Pode demorar até 10 minutos e ainda o período de tempo definido para **QuerExecutionAggregationTimeInMinutes** no ficheiro de configuração, até que os ficheiros comecem a aparecer na pasta.

## <a name="understand-performance-logs"></a>Compreender os registos de desempenho

Quando ativar esta funcionalidade, criamos três novos ficheiros de registo:

- O relatório de execução de consulta
- O relatório de agregação de execução de consulta
- O relatório de agregação de contador do sistema

O relatório de execução da consulta contém informações de execução de consultas detalhadas. Podemos capturar os seguintes atributos:

|Attribute |Descrição |
| ---- | ---- |
|**GatewayObjectId** |Identificador exclusivo para o gateway. |
|**RequestId** |Identificador exclusivo de um pedido de gateway. Pode ser o mesmo para várias consultas. |
|**DataSource** |Contém o tipo de origem de dados e a origem de dados. |
|**QueryTrackingId** |Identificador exclusivo de uma consulta. |  
|**QueryExecutionEndTimeUTC** |Hora quando a execução da consulta concluída. |
|**QueryExecutionDuration**(ms) |Duração de uma execução da consulta. |
|**QueryType** |Tipo de consulta - por exemplo, a consulta transmitida pode ser uma atualização/DirectQuery do Power BI ou consultas do PowerApps e Microsoft Flow. |
|**DataProcessingEndTimeUTC** |Hora de quando as atividades de processamento de dados, como no spool, obtenção de dados, compressão, processamento de dados e assim por diante concluída. |
|**DataProcessingDuration**(ms) |Duração de atividades de processamento de dados, como no spool, obtenção de dados, compressão, processamento de dados e assim por diante. |
|**Êxito** |Indica se a consulta foi concluída com êxito ou falha. |
|**ErrorMessage** |Se a consulta falhou, indica que a mensagem de erro. |
| | |

O relatório de agregação de execução de consulta contém informações de consulta agregadas para um intervalo de tempo por **GatewayObjectId**, **DataSource**, **êxito**e **QueryType**. O valor predefinido é de 5 minutos, mas pode ajustá-la, conforme descrito abaixo. Podemos capturar os seguintes atributos:

|Attribute |Descrição |
| ---- | ---- |
|**GatewayObjectId** |Identificador exclusivo para o gateway. |
|**AggregationStartTimeUTC** |Início da janela de tempo para os quais os atributos de consulta foram agregados. |
|**AggregationEndTimeUTC** |Fim da janela de tempo para que consulta os atributos foram agregados. |
|**DataSource** |Contém o tipo de origem de dados e a origem de dados. |
|**Êxito** |Indica se a consulta foi concluída com êxito ou falha. |
|**AverageQueryExecutionDuration**(ms) |Média de tempo de execução de consulta para a janela de tempo de agregação. |
|**MaxQueryExecutionDuration**(ms) |Tempo de execução máxima de consulta para a janela de tempo de agregação. |
|**MinQueryExecutionDuration**(ms) |Tempo de execução de consulta mínimo para a janela de tempo de agregação. |
|**QueryType** |Tipo de consulta - por exemplo, a consulta transmitida pode ser uma atualização/DirectQuery do Power BI ou consultas do PowerApps e Microsoft Flow. |
|**AverageDataProcessingDuration**(ms) |Tempo médio para atividades de processamento de dados, como no spool, a obtenção de dados, a compressão, processamento de dados, e assim por diante para a janela de tempo de agregação. |
|**MaxDataProcessingDuration**(ms) |Tempo máximo para as atividades de processamento de dados, como no spool, obtenção de dados, compressão, processamento de dados e assim por diante para a janela de tempo de agregação. |
|**MinDataProcessingDuration**(ms) |Tempo mínimo para atividades de processamento de dados, como no spool, obtenção de dados, compressão, processamento de dados e assim por diante para a janela de tempo de agregação. |
|**Contagem** |Número de consultas. |
| | |

O relatório de agregação de contador de sistema contém valores agregados para um intervalo de tempo do contador de sistema. O valor predefinido é de 5 minutos, mas pode ajustá-la, conforme descrito abaixo. Podemos capturar os seguintes atributos:

|Attribute |Descrição |
| ---- | ---- |
|**GatewayObjectId** |Identificador exclusivo para o gateway. |
|**AggregationStartTimeUTC** |Início da janela de tempo para os quais contadores do sistema tem sido agregados. |
|**AggregationEndTimeUTC** |Fim da janela de tempo para o sistema tem sido agregados contadores. |
|**CounterName** |Contadores do sistema, incluindo a memória e utilização da CPU pelo gateway, mashup e geral pela máquina que aloja o gateway. |
|**Max** |Valor máximo para o contador de sistema para a janela de tempo de agregação. |
|**Min** |Valor mínimo para o contador de sistema para a janela de tempo de agregação. |
|**Média** |Valor médio para o contador de sistema para a janela de tempo de agregação. |
| | |

## <a name="visualize-gateway-performance"></a>Visualizar o desempenho do gateway

Agora, pode visualizar os dados que estão nos ficheiros de registo.

1. Transfira o [modelo de PBI de desempenho do Gateway](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) e abri-lo com o Power BI desktop.

1. Na caixa de diálogo que se abre, verifique se o caminho da pasta corresponde ao valor na **ReportFilePath**.

    ![Pop-up para o caminho da pasta](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Selecione **carga**, e o ficheiro de modelo começa a carregar os dados a partir dos seus ficheiros de registo. Todos os elementos visuais, em seguida, devem ser preenchidos com os dados nos relatórios.

1. Opcionalmente, guarde este ficheiro como um PBIX e publicá-lo ao seu serviço para as atualizações automáticas.

Além disso, pode personalizar este ficheiro de modelo para se adequar às suas necessidades. Para obter mais informações sobre modelos do Power BI, consulte esta [mensagem de blogue do Microsoft Power BI](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).