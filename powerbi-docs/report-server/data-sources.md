---
title: Origens de dados de relatórios do Power BI no Power BI Report Server
description: Os relatórios do Power BI podem ligar-se a diferentes origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados.
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/21/2018
ms.author: maghan
ms.openlocfilehash: 3777c58bae36d6115b51b64e0422529fe390a13c
ms.sourcegitcommit: 1fe3ababba34c4e7aea08adb347ec5430e0b38e4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Origens de dados de relatórios do Power BI no Power BI Report Server
Os relatórios do Power BI podem ligar-se a diferentes origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados. Pode importar ou consultar dados diretamente através do DirectQuery ou de uma ligação em direto ao SQL Server Analysis Services.

Estas origens de dados são específicas para relatórios do Power BI utilizados no Power BI Report Server. Para obter informações sobre origens de dados suportadas com relatórios paginados, veja [Origens de Dados Suportadas pelo Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Todas as origens de dados num relatório do Power BI Desktop têm de ser suportadas para configurar a atualização agendada.
> 
> 

## <a name="list-of-supported-data-sources"></a>Lista de origens de dados suportadas

Outras origens de dados podem funcionar apesar de não estarem na lista suportada.

| **Origem de dados** | **Dados em cache** | **Atualização agendada** | **Em direto/DirectQuery** |
| --- | --- | --- | --- |
| Base de Dados do SQL Server |Sim |Sim |Sim |
| SQL Server Analysis Services |Sim |Sim |Sim |
| Base de dados SQL do Azure |Sim |Sim |Sim |
| Azure SQL Data Warehouse |Sim |Sim |Sim |
| Excel |Sim |Sim |Não |
| Base de Dados do Access |Sim |Sim |Não |
| Active Directory |Sim |Sim |Não |
| Amazon Redshift |Sim |Não |Não |
| Armazenamento de Blobs do Azure |Sim |Sim |Não |
| Azure Data Lake Store |Sim |Não |Não |
| Azure HDInsight (HDFS) |Sim |Não |No |
| Azure HDInsight (Spark) |Sim |Sim |Não |
| Armazenamento de Tabelas do Azure |Sim |Sim |Não |
| Dynamics 365 (online) |Sim |Não |Não |
| Facebook |Sim |Não |Não |
| Pasta |Sim |Sim |Não |
| Google Analytics |Sim |Não |Não |
| Hadoop File (HDFS) |Sim |Não |Não |
| Base de Dados IBM DB2 |Sim |Sim |Não |
| Impala |Sim |Não |Não |
| JSON |Sim |Sim |Não |
| Microsoft Exchange |Sim |Não |Não |
| Microsoft Exchange Online |Sim |Não |Não |
| Base de Dados MySQL |Sim |Sim |Não |
| Feed OData |Sim |Sim |Não |
| ODBC |Sim |Sim |Não |
| OLE DB |Sim |Sim |Não |
| Base de Dados Oracle |Sim |Sim |Sim |
| Base de Dados PostgreSQL |Sim |Sim |Não |
| Serviço Power BI |Não |Não |Não |
| Script do R |Sim |Não |Não |
| Objetos do Salesforce |Sim |Não |Não |
| Relatórios do Salesforce |Sim |Não |Não |
| SAP Business Warehouse Server |Sim |Sim |Sim |
| Base de Dados do SAP HANA |Sim |Sim |Sim |
| Pasta do SharePoint (no local) |Sim |Sim |Não |
| Lista do SharePoint (no local) |Sim |Sim |Não |
| Lista do SharePoint Online |Sim |Não |Não |
| Snowflake |Sim |Não |Não |
| Base de Dados Sybase |Sim |Sim |Não |
| Base de Dados Teradata |Sim |Sim |Sim |
| Texto/CSV |Sim |Sim |Não |
| Web |Sim |Sim |Não |
| XML |Sim |Sim |Não |
| appFigures (Beta) |Sim |Não |Não |
| Base de Dados do Azure Analysis Services (Beta) |Sim |Não |Não |
| Azure Cosmos DB (Beta) |Sim |Não |Não |
| Azure HDInsight Spark (Beta) |Sim |Não |Não |
| Common Data Service (Beta) |Sim |Não |Não |
| comScore Digital Analytix (Beta) |Sim |Não |Não |
| Dynamics 365 for Customer Insights (Beta) |Sim |Não |Não |
| Dynamics 365 for Financials (Beta) |Sim |Não |Não |
| GitHub (Beta) |Sim |Não |Não |
| Google BigQuery (Beta) |Sim |Não |Não |
| Base de dados IBM Informix (Beta) |Sim |Não |Não |
| IBM Netezza (Beta) |Sim |Não |Não |
| Kusto (Beta) |Sim |Não |Não |
| MailChimp (Beta) |Sim |Não |Não |
| Microsoft Azure Consumption Insights (Beta) |Sim |Não |Não |
| Mixpanel (Beta) |Sim |Não |Não |
| Planview Enterprise (Beta) |Sim |Não |Não |
| Projectplace (Beta) |Sim |Não |Não |
| QuickBooks Online (Beta) |Sim |Não |Não |
| Smartsheet |Sim |Não |Não |
| Spark (Beta) |Sim |Não |Não |
| SparkPost (Beta) |Sim |Não |Não |
| SQL Sentry (Beta) |Sim |Não |Não |
| Stripe (Beta) |Sim |Não |Não |
| SweetIQ (Beta) |Sim |Não |Não |
| Troux (Beta) |Sim |Não |Não |
| Twilio (Beta) |Sim |Não |Não |
| tyGraph (Beta) |Sim |Não |Não |
| Vertica (Beta) |Sim |Não |Não |
| Visual Studio Team Services (Beta) |Sim |Não |Não |
| Webtrends (Beta) |Sim |Não |Não |
| ZenDesk (Beta) |Sim |Não |Não |

> [!IMPORTANT]
> A segurança ao nível da linha configurada na origem de dados deve funcionar para determinadas ligações DirectQuery (SQL Server, Base de Dados SQL do Azure, Oracle e Teradata) e em direto ao assumir que o Kerberos está configurado corretamente no seu ambiente.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Lista de métodos de autenticação suportados para a atualização de modelos

O Power BI Report Server não suporta autenticação com base em OAuth para a atualização de modelos. Algumas origens de dados, como as bases de dados do Access ou do Excel, utilizam um passo separado como Ficheiro ou Web para ligar aos dados.

| **Origem de dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de Utilizador e Palavra-passe** | **Autenticação do Windows** |
| --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |No |Sim |Sim |
| SQL Server Analysis Services |No |No |Sim |Sim |
| Web |Sim |Não |Sim |Sim |
| Base de Dados SQL do Azure |No |No |Sim |No |
| SQL Data Warehouse do Azure |No |No |Sim |Não |
| Active Directory |No |No |Sim |Sim |
| Amazon Redshift |No |Não |Não |Não |
| Armazenamento de Blobs do Azure |Sim |Sim |Não |No |
| Azure Data Lake Store |No |Não |Não |Não |
| Azure HDInsight (HDFS) |No |Não |Não |No |
| Azure HDInsight (Spark) |Sim |Sim |Não |No |
| Armazenamento de Tabelas do Azure |No |Sim |Não |No |
| Dynamics 365 (online) |No |Não |Não |Não |
| Facebook |No |Não |Não |Não |
| Pasta |No |Não |No |Sim |
| Google Analytics |No |Não |Não |Não |
| HDFS (Ficheiro do Hadoop) |No |Não |Não |Não |
| Base de Dados IBM DB2 |No |No |Sim |Sim |
| Impala |No |Não |Não |No |
| Microsoft Exchange |No |Não |Não |Não |
| Microsoft Exchange Online |No |Não |Não |Não |
| Base de Dados MySQL |No |No |Sim |Sim |
| Feed OData |Sim |Sim |Sim |Sim |
| ODBC |Sim |Não |Sim |Sim |
| OLEDB |Sim |Não |Sim |Sim |
| Base de Dados Oracle |No |No |Sim |Sim |
| Base de Dados PostgreSQL |No |No |Sim |Não |
| Serviço Power BI |Não |Não |Não |Não |
| Script do R |No |Não |Não |Não |
| Objetos do Salesforce |No |Não |Não |Não |
| Relatórios do Salesforce |No |Não |Não |Não |
| SAP Business Warehouse Server |No |No |Sim |No |
| Base de Dados do SAP HANA |No |No |Sim |Sim |
| Pasta do SharePoint (no local) |Sim |Não |No |Sim |
| Lista do SharePoint (no local) |Sim |Não |No |Sim |
| Lista do SharePoint Online |No |Não |Não |Não |
| Snowflake |No |Não |Não |Não |
| Base de Dados Sybase |No |No |Sim |Sim |
| Base de Dados Teradata |No |No |Sim |Sim |
| appFigures (Beta) |No |Não |Não |Não |
| Base de Dados do Azure Analysis Services (Beta) |No |Não |Não |Não |
| Azure Cosmos DB (Beta) |No |Não |Não |Não |
| Azure HDInsight Spark (Beta) |No |Não |Não |Não |
| Common Data Service (Beta) |No |Não |Não |Não |
| comScore Digital Analytix (Beta) |No |Não |Não |Não |
| Dynamics 365 for Customer Insights (Beta) |No |Não |Não |Não |
| Dynamics 365 for Financials (Beta) |No |Não |Não |Não |
| GitHub (Beta) |No |Não |Não |Não |
| Google BigQuery (Beta) |No |Não |Não |Não |
| Base de dados IBM Informix (Beta) |No |Não |Não |Não |
| IBM Netezza (Beta) |No |Não |Não |Não |
| Kusto (Beta) |No |Não |Não |Não |
| MailChimp (Beta) |No |Não |Não |Não |
| Microsoft Azure Consumption Insights (Beta) |No |Não |Não |Não |
| Mixpanel (Beta) |No |Não |Não |Não |
| Planview Enterprise (Beta) |No |Não |Não |Não |
| Projectplace (Beta) |No |Não |Não |Não |
| QuickBooks Online (Beta) |No |Não |Não |Não |
| Smartsheet |No |Não |Não |Não |
| Spark (Beta) |No |Não |Não |Não |
| SparkPost (Beta) |No |Não |Não |Não |
| SQL Sentry (Beta) |No |Não |Não |Não |
| Stripe (Beta) |No |Não |Não |Não |
| SweetIQ (Beta) |No |Não |Não |Não |
| Troux (Beta) |No |Não |Não |Não |
| Twilio (Beta) |No |Não |Não |Não |
| tyGraph (Beta) |No |Não |Não |Não |
| Vertica (Beta) |No |Não |Não |Não |
| Visual Studio Team Services (Beta) |No |Não |Não |Não |
| Webtrends (Beta) |No |Não |Não |Não |
| ZenDesk (Beta) |No |Não |Não |No |

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lista de métodos de autenticação suportados para o DirectQuery

O Power BI Report Server não suporta autenticação com base em OAuth para o DirectQuery.

| **Origem de dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de Utilizador e Palavra-passe** | **Autenticação do Windows** | **Autenticação Integrada do Windows** |
| --- | --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |No |Sim |Sim |Sim |
| SQL Server Analysis Services |No |No |Sim |Sim |Sim |
| Base de Dados SQL do Azure |No |No |Sim |Não |No |
| SQL Data Warehouse do Azure |No |No |Sim |Não |No |
| Base de Dados Oracle |No |No |Sim |Sim |Sim |
| SAP Business Warehouse Server |No |No |Sim |Não |Sim |
| Base de Dados do SAP HANA |No |No |Sim |Sim |Não |
| Base de Dados Teradata |No |No |Sim |Sim |Sim |


## <a name="next-steps"></a>Próximos passos
Agora que a origem de dados está selecionada, [crie um relatório](quickstart-create-powerbi-report.md) com os dados dessa origem de dados.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

