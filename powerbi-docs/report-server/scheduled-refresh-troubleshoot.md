---
title: "Resolução de problemas da atualização agendada no Power BI Report Server"
description: "Este artigo aborda os recursos disponíveis para resolver problemas com a atualização agendada no Power BI Report Server."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 11/01/2017
ms.author: asaxton
ms.openlocfilehash: 815e2ff78a89b98978d4b8a5c0d21317e9f92056
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Resolução de problemas da atualização agendada no Power BI Report Server
Este artigo aborda os recursos disponíveis para resolver problemas com a atualização agendada no Power BI Report Server.

À medida que ocorrem problemas, este artigo será atualizado com informações para ajudá-lo.

## <a name="common-issues"></a>Problemas comuns
Seguem-se os problemas mais comuns ao tentar agendar a atualização de um relatório. 

### <a name="driver-related-problems"></a>Problemas relacionados com o controlador
Ligar a origens de dados diferentes pode requerer controladores de terceiros que têm de ser instalados para poder estabelecer ligação com êxito. Não só tem de instalá-los no computador em que está a utilizar o Power BI Desktop, mas também terá de assegurar que o controlador está instalado no servidor de relatórios.

O controlador pode ainda ser de 32 bits e 64 bits. Certifique-se de que instala o controlador de 64 bits, uma vez que o Power BI Report Server é de 64 bits.

Consulte o fabricante para obter detalhes sobre como instalar e configurar controladores de terceiros.

### <a name="memory-pressure"></a>Pressão da memória
Pode ocorrer pressão da memória quando os relatórios precisam de mais memória para processamento e composição. Agendar a atualização em relatórios pode exigir uma quantidade significativa de memória no computador. Sobretudo para relatórios maiores. A pressão da memória pode resultar em falhas de relatórios, bem como na potencial falha do próprio servidor de relatórios.

Se estiver a ocorrer pressão da memória de forma consistente, poderá ser útil considerar uma implementação de escalamento horizontal do servidor de relatórios para distribuir a carga de recursos. Também pode definir se um determinado servidor de relatórios é utilizado para atualização de dados com a definição `IsDataModelRefreshService` em rsreportserver.config. Com esta definição, pode definir um ou mais servidores como servidor de front-end para processar relatórios a pedido e ter outro conjunto de servidores apenas utilizado na atualização agendada.

Para obter informações sobre como monitorizar uma instância do Analysis Services, veja [Monitorizar uma Instância do Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Para obter informações sobre as definições de memória no Analysis Services, veja [Propriedades de Memória](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties).

### <a name="kerberos-configuration"></a>Configuração do Kerberos
Ligar a uma origem de dados com as credenciais do Windows pode requerer a configuração da delegação restrita do Kerberos para efetuar uma ligação com êxito. Para obter mais informações sobre como configurar a delegação restrita do Kerberos, veja [Configurar o Kerberos para utilizar relatórios do Power BI](configure-kerberos-powerbi-reports.md).

## <a name="known-issues"></a>Problemas conhecidos
Serão listadas aqui informações sobre problemas conhecidos que forem disponibilizadas.

## <a name="configuration-settings"></a>Definições de configuração
As seguintes definições podem ser utilizadas para afetar a atualização agendada. As definições estipuladas no SQL Server Management Studio (SSMS) aplicam-se a todos os servidores de relatórios numa implementação de escalamento horizontal. As definições configuradas em rsreportserver.config destinam-se ao servidor específico em que estão estipuladas.

**Definições no SSMS:**

| Definição | Descrição |
| --- | --- |
| EnablePowerBIReportEmbeddedModels |Ativa ou desativa a capacidade de utilizar dados importados nos relatórios. Os valores válidos são True ou False. |
| MaxFileSizeMb |O tamanho máximo de ficheiro para os relatórios carregados. A predefinição é 1000 MB (1 GB). O valor máximo é 2000 MB (2GB). |
| ModelCleanupCycleMinutes |Define a frequência de verificação do modelo para expulsá-lo da memória. A predefinição é 15 minutos. |
| ModelExpirationMinutes |Define o intervalo de tempo até o modelo expirar com base na última utilização e expulsão. A predefinição é 60 minutos. |
| ScheduleRefreshTimeoutMinutes |Define o intervalo de tempo que a atualização de dados pode demorar para um modo. A predefinição é 120 minutos. Não existe um limite superior. |

**Definições em rsreportserver.config:**

```
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Ferramentas para resolução de problemas
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Registos relevantes para a atualização agendada de relatórios do Power BI
Os ficheiros de registo que contêm informações sobre a atualização agendada são registos RSPowerBI_. Estão localizados na pasta LogFiles da localização de instalação do servidor de relatórios. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Condição de erro**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Atualização com êxito***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Credenciais incorretas**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Ativar Registo Verboso
A ativação do registo verboso, no Power BI Report Server, é efetuada da mesma forma que no SQL Server Reporting Services.

1. Abra `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. Em `<system.diagnostics>`, altere **DefaultTraceSwitch** para **4**.
3. Em `<RStrace>`, altere **Components** para **all:4**. 

### <a name="executionlog"></a>ExecutionLog
Sempre que um relatório do Power BI é composto, ou é executado um plano de atualização de agendamento, são adicionadas novas entradas ao Registo de Execução na base de dados. Estas entradas estão disponíveis na vista **ExecutionLog3** na base de dados do catálogo do servidor de relatórios.

As entradas do registo de execução para relatórios do Power BI diferem das entradas para outros tipos de relatório.

* As colunas TimeRendering são sempre 0. A composição de relatórios do Power BI ocorre no browser e não no servidor.
* Existem dois Tipos de Pedido e ações de itens subsequentes:
  * **Interactive**: sempre que um relatório está a ser visualizado.
    * **ASModelStream**: quando o modelo de dados é transmitido para o Analysis Services a partir do catálogo.
    * **ConceptualSchema**: quando o utilizador clica para visualizar o relatório.
    * **QueryData**: sempre que os dados estão a ser pedidos a partir do cliente.
  * **Refresh Cache**: sempre que um plano de atualização de agendamento foi executado.
    * **ASModelStream**: sempre que o modelo de dados é transmitido para o Analysis Services a partir do catálogo.
    * **DataRefresh**: sempre que os dados estão a ser atualizados a partir de uma ou mais origens de dados.
    * **SaveToCatalog**: sempre que o modelo de dados está a ser guardado novamente no catálogo.

## <a name="analysis-services"></a>Analysis Services
Por vezes, pode querer modificar o Analysis Services para diagnosticar problemas ou ajustar os limites de memória.

> [!IMPORTANT]
> Estas definições serão repostas sempre que atualizar o servidor de relatórios. Lembre-se de manter uma cópia das alterações e voltar a aplicá-las, se for necessário.
> 
> 

### <a name="install-location"></a>Localização de instalação
A localização predefinida para o Power BI Report Server e o Analysis Services é a seguinte.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Configurar as definições do Analysis Services (msmdsrv.ini)
No diretório `<install directory>\PBIRS\ASEngine`, encontrará o ficheiro *msmdsrv.ini*, que pode utilizar para controlar as diferentes definições do Analysis Services. Quando abrir este ficheiro, notará imediatamente que não tem todas as definições que esperava no ficheiro msmdsrv.ini. 

Isto acontece porque o processo do Analysis Services real executado pelo Power BI Report Server é iniciado em `<install directory>\PBIRS\ASEngine\workspaces`. Nessa pasta, verá o ficheiro *msmdsrv.ini* completo a que está habituado. É importante não modificar o ficheiro na pasta de áreas de trabalho, uma vez que é reescrito sempre que o processo do Analysis Services é iniciado. Se quiser controlar uma definição, faça-o ao modificar o ficheiro msmdsrv.ini no diretório `<install directory>\PBIRS\ASEngine`.

As definições seguintes são sempre que o processo do Analysis Services é iniciado. Quaisquer alterações efetuadas serão ignoradas.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Criação de perfis do processo do Analysis Services local
É possível executar um rastreio do SQL Profiler no processo do Analysis Services local para efeitos de diagnóstico. Para ligar à instância do Analysis Services local, faça o seguinte.

O SQL Server Profiler Trace está incluído na [transferência do SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

1. Inicie o **SQL Server Profiler** como administrador.
2. Selecione o botão **New Trace** (Novo Rastreio).
3. Na caixa de diálogo **Connect to server** (Ligar ao servidor), selecione **Analysis Services** e introduza **localhost:5132** no nome do servidor.
4. Na caixa de diálogo **Trace properties** (Propriedades de rastreio), selecione os eventos que quer capturar e selecione **Run** (Executar).

## <a name="lock-pages-in-memory-windows-privilege"></a>Privilégio do Windows Bloquear Páginas na Memória
Se considerar que não consegue compor um relatório do Power BI, pode ajudar atribuir o privilégio **Bloquear páginas na memória** à conta de serviços que está a executar o Power BI Report Server. Para obter mais informações sobre como configurar o privilégio **Bloquear páginas na memória**, veja os [privilégios do Windows atribuídos à conta de serviços do Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

