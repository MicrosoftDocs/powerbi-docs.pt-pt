---
title: Origens de dados de relatórios do Power BI no Power BI Report Server
description: Os relatórios do Power BI podem estabelecer ligação a diversas origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maghan
ms.openlocfilehash: 0f06d5c3742ea5187ff41f6f8974c8a81e5d1d33
ms.sourcegitcommit: dcde910817720c05880ffe24755034f916c9b890
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2018
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Origens de dados de relatórios do Power BI no Power BI Report Server
Os relatórios do Power BI podem estabelecer ligação a diversas origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados. Pode importar ou consultar dados diretamente através do DirectQuery ou de uma ligação em direto ao SQL Server Analysis Services.

Estas origens de dados são específicas para relatórios do Power BI utilizados no Power BI Report Server. Para obter informações sobre as origens de dados suportadas com relatórios paginados (.rdl), veja [Data Sources Supported by Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs) (Origens de Dados Suportadas pelo Reporting Services).

> [!IMPORTANT]
> Todas as origens de dados num relatório do Power BI Desktop têm de suportar a configuração da atualização agendada.
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
| Azure HDInsight (HDFS) |Sim |Não |Não |
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
| Base de dados do Azure Analysis Services |Sim |Não |Sim |
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
| Base de Dados do SQL Server |Não |Não |Sim |Sim |
| SQL Server Analysis Services |Não |Não |Sim |Sim |
| Vista Web |Sim |Não |Sim |Sim |
| Base de Dados SQL do Azure |Não |Não |Sim |Não |
| SQL Data Warehouse do Azure |Não |Não |Sim |Não |
| Active Directory |Não |Não |Sim |Sim |
| Amazon Redshift |Não |Não |Não |Não |
| Armazenamento de Blobs do Azure |Sim |Sim |Não |Não |
| Azure Data Lake Store |Não |Não |Não |Não |
| Azure HDInsight (HDFS) |Não |Não |Não |Não |
| Azure HDInsight (Spark) |Sim |Sim |Não |Não |
| Armazenamento de Tabelas do Azure |Não |Sim |Não |Não |
| Dynamics 365 (online) |Não |Não |Não |Não |
| Facebook |Não |Não |Não |Não |
| Pasta |Não |Não |Não |Sim |
| Google Analytics |Não |Não |Não |Não |
| HDFS (Ficheiro do Hadoop) |Não |Não |Não |Não |
| Base de Dados IBM DB2 |Não |Não |Sim |Sim |
| Impala |Não |Não |Não |Não |
| Microsoft Exchange |Não |Não |Não |Não |
| Microsoft Exchange Online |Não |Não |Não |Não |
| Base de Dados MySQL |Não |Não |Sim |Sim |
| Feed OData |Sim |Sim |Sim |Sim |
| ODBC |Sim |Não |Sim |Sim |
| OLEDB |Sim |Não |Sim |Sim |
| Base de Dados Oracle |Não |Não |Sim |Sim |
| Base de Dados PostgreSQL |Não |Não |Sim |Não |
| Serviço Power BI |Não |Não |Não |Não |
| Script do R |Não |Não |Não |Não |
| Objetos do Salesforce |Não |Não |Não |Não |
| Relatórios do Salesforce |Não |Não |Não |Não |
| SAP Business Warehouse Server |Não |Não |Sim |Não |
| Base de Dados do SAP HANA |Não |Não |Sim |Sim |
| Pasta do SharePoint (no local) |Sim |Não |Não |Sim |
| Lista do SharePoint (no local) |Sim |Não |Não |Sim |
| Lista do SharePoint Online |Não |Não |Não |Não |
| Snowflake |Não |Não |Não |Não |
| Base de Dados Sybase |Não |Não |Sim |Sim |
| Base de Dados Teradata |Não |Não |Sim |Sim |
| appFigures (Beta) |Não |Não |Não |Não |
| Base de Dados do Azure Analysis Services (Beta) |Não |Não |Não |Não |
| Azure Cosmos DB (Beta) |Não |Não |Não |Não |
| Azure HDInsight Spark (Beta) |Não |Não |Não |Não |
| Common Data Service (Beta) |Não |Não |Não |Não |
| comScore Digital Analytix (Beta) |Não |Não |Não |Não |
| Dynamics 365 for Customer Insights (Beta) |Não |Não |Não |Não |
| Dynamics 365 for Financials (Beta) |Não |Não |Não |Não |
| GitHub (Beta) |Não |Não |Não |Não |
| Google BigQuery (Beta) |Não |Não |Não |Não |
| Base de dados IBM Informix (Beta) |Não |Não |Não |Não |
| IBM Netezza (Beta) |Não |Não |Não |Não |
| Kusto (Beta) |Não |Não |Não |Não |
| MailChimp (Beta) |Não |Não |Não |Não |
| Microsoft Azure Consumption Insights (Beta) |Não |Não |Não |Não |
| Mixpanel (Beta) |Não |Não |Não |Não |
| Planview Enterprise (Beta) |Não |Não |Não |Não |
| Projectplace (Beta) |Não |Não |Não |Não |
| QuickBooks Online (Beta) |Não |Não |Não |Não |
| Smartsheet |Não |Não |Não |Não |
| Spark (Beta) |Não |Não |Não |Não |
| SparkPost (Beta) |Não |Não |Não |Não |
| SQL Sentry (Beta) |Não |Não |Não |Não |
| Stripe (Beta) |Não |Não |Não |Não |
| SweetIQ (Beta) |Não |Não |Não |Não |
| Troux (Beta) |Não |Não |Não |Não |
| Twilio (Beta) |Não |Não |Não |Não |
| tyGraph (Beta) |Não |Não |Não |Não |
| Vertica (Beta) |Não |Não |Não |Não |
| Visual Studio Team Services (Beta) |Não |Não |Não |Não |
| Webtrends (Beta) |Não |Não |Não |Não |
| ZenDesk (Beta) |Não |Não |Não |Não |

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lista de métodos de autenticação suportados para o DirectQuery

O Power BI Report Server não suporta autenticação com base em OAuth para o DirectQuery.

| **Origem de dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de Utilizador e Palavra-passe** | **Autenticação do Windows** | **Autenticação Integrada do Windows** |
| --- | --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |Não |Não |Sim |Sim |Sim |
| SQL Server Analysis Services |Não |Não |Sim |Sim |Sim |
| Base de Dados SQL do Azure |Não |Não |Sim |Não |Não |
| SQL Data Warehouse do Azure |Não |Não |Sim |Não |Não |
| Base de Dados Oracle |Não |Não |Sim |Sim |Sim |
| SAP Business Warehouse Server |Não |Não |Sim |Não |Sim |
| Base de Dados do SAP HANA |Não |Não |Sim |Sim |Não |
| Base de Dados Teradata |Não |Não |Sim |Sim |Sim |


## <a name="next-steps"></a>Próximos passos
Agora que estabeleceu ligação à origem de dados, [crie um relatório do Power BI](quickstart-create-powerbi-report.md) com os dados dessa origem de dados.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

