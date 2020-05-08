---
title: Origens de dados de relatórios do Power BI no Power BI Report Server
description: Os relatórios do Power BI podem estabelecer ligação a diversas origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: maggies
ms.openlocfilehash: 166f72a717c99457e1d6b8e9a1f30535a9b4686f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80979851"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Origens de dados de relatórios do Power BI no Power BI Report Server
Os relatórios do Power BI podem estabelecer ligação a diversas origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados. Pode importar ou consultar dados diretamente através do DirectQuery ou de uma ligação em direto ao SQL Server Analysis Services.

Estas origens de dados são específicas para relatórios do Power BI utilizados no Power BI Report Server. Para obter informações sobre as origens de dados suportadas com relatórios paginados (.rdl), veja [Data Sources Supported by Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs) (Origens de Dados Suportadas pelo Reporting Services).

> [!IMPORTANT]
> Todas as origens de dados num relatório do Power BI Desktop têm de suportar a configuração da atualização agendada.
>  

## <a name="list-of-supported-data-sources"></a>Lista de origens de dados suportadas

Outras origens de dados podem funcionar apesar de não estarem na lista suportada.

| **Origem de Dados** | **Dados em cache** | **Atualização agendada** | **Em direto/DirectQuery** |
| --- | --- | --- | --- |
| Base de Dados do SQL Server |Yes |Yes |Yes |
| SQL Server Analysis Services |Yes |Yes |Yes |
| Base de dados SQL do Azure |Yes |Yes |Yes |
| Azure SQL Data Warehouse |Yes |Yes |Yes |
| Excel |Yes |Yes |No |
| Base de Dados do Access |Yes |Yes |No |
| Active Directory |Yes |Yes |No |
| Amazon Redshift |Yes |No |No |
| Armazenamento de Blobs do Azure |Yes |Yes |No |
| Azure Data Lake Store |Yes |No |No |
| Azure HDInsight (HDFS) |Yes |No |No |
| Azure HDInsight (Spark) |Yes |No |No |
| Armazenamento de Tabelas do Azure |Yes |Yes |No |
| Dynamics 365 (online) |Yes |No |No |
| Facebook |Yes |No |No |
| Pasta |Yes |Yes |No |
| Google Analytics |Yes |No |No |
| HDFS (Ficheiro do Hadoop) |Yes |No |No |
| Base de Dados IBM DB2 |Yes |Yes |No |
| Impala |Yes |No |No |
| JSON |Yes |Yes |No |
| Microsoft Exchange |Yes |No |No |
| Microsoft Exchange Online |Yes |No |No |
| Base de Dados MySQL |Yes |Yes |No |
| Feed OData |Yes |Yes |No |
| ODBC |Yes |Yes |No |
| OLE DB |Yes |Yes |No |
| Base de Dados Oracle |Yes |Yes |Yes |
| Base de Dados PostgreSQL |Yes |Yes |No |
| serviço Power BI |No |No |No |
| Script do R |Yes |No |No |
| Objetos do Salesforce |Yes |No |No |
| Relatórios do Salesforce |Yes |No |No |
| SAP Business Warehouse Server |Yes |Yes |Yes |
| Base de Dados do SAP HANA |Yes |Yes |Yes |
| Pasta do SharePoint (no local) |Yes |Yes |No |
| Lista do SharePoint (no local) |Yes |Yes |No |
| Lista do SharePoint Online |Yes |No |No |
| Snowflake |Yes |No |No |
| Base de Dados Sybase |Yes |Yes |No |
| Teradata |Yes |Yes |Yes |
| Texto/CSV |Yes |Yes |No |
| Vista Web |Yes |Yes |No |
| XML |Yes |Yes |No |
| appFigures (Beta) |Yes |No |No |
| Base de dados do Azure Analysis Services |Yes |No |Yes |
| Azure Cosmos DB (Beta) |Yes |No |No |
| Azure HDInsight Spark (Beta) |Yes |No |No |
| Common Data Service (Beta) |Yes |No |No |
| comScore Digital Analytix (Beta) |Yes |No |No |
| Dynamics 365 for Customer Insights (Beta) |Yes |No |No |
| Dynamics 365 for Financials (Beta) |Yes |No |No |
| GitHub (Beta) |Yes |No |No |
| Google BigQuery (Beta) |Yes |No |No |
| Base de dados IBM Informix (Beta) |Yes |No |No |
| IBM Netezza (Beta) |Yes |No |No |
| Kusto (Beta) |Yes |No |No |
| MailChimp (Beta) |Yes |No |No |
| Microsoft Azure Consumption Insights (Beta) |Yes |No |No |
| Mixpanel (Beta) |Yes |No |No |
| Planview Enterprise (Beta) |Yes |No |No |
| Projectplace (Beta) |Yes |No |No |
| QuickBooks Online (Beta) |Yes |No |No |
| Smartsheet |Yes |No |No |
| Spark (Beta) |Yes |No |No |
| SparkPost (Beta) |Yes |No |No |
| SQL Sentry (Beta) |Yes |No |No |
| Stripe (Beta) |Yes |No |No |
| SweetIQ (Beta) |Yes |No |No |
| Troux (Beta) |Yes |No |No |
| Twilio (Beta) |Yes |No |No |
| tyGraph (Beta) |Yes |No |No |
| Vertica (Beta) |Yes |No |No |
| Visual Studio Team Services (Beta) |Yes |No |No |
| Webtrends (Beta) |Yes |No |No |
| ZenDesk (Beta) |Yes |No |No |

> [!IMPORTANT]
> A segurança ao nível da linha configurada na origem de dados deve funcionar para determinadas ligações DirectQuery (SQL Server, Base de Dados SQL do Azure, Oracle e Teradata) e em direto ao assumir que o Kerberos está configurado corretamente no seu ambiente.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Lista de métodos de autenticação suportados para a atualização de modelos

O Power BI Report Server não suporta autenticação com base em OAuth para a atualização de modelos. Algumas origens de dados, como as bases de dados do Access ou do Excel, utilizam um passo separado como Ficheiro ou Web para ligar aos dados.

| **Origem de Dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de Utilizador e Palavra-passe** | **Autenticação do Windows** |
| --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |No |Yes |Yes |
| SQL Server Analysis Services |No |No |Yes |Yes |
| Vista Web |Yes |No |Yes |Yes |
| Base de dados SQL do Azure |No |No |Yes |No |
| Azure SQL Data Warehouse |No |No |Yes |No |
| Active Directory |No |No |Yes |Yes |
| Amazon Redshift |No |No |No |No |
| Armazenamento de Blobs do Azure |Yes |Yes |No |No |
| Azure Data Lake Store |No |No |No |No |
| Azure HDInsight (HDFS) |No |No |No |No |
| Azure HDInsight (Spark) |No |No |No |No |
| Armazenamento de Tabelas do Azure |No |Yes |No |No |
| Dynamics 365 (online) |No |No |No |No |
| Facebook |No |No |No |No |
| Pasta |No |No |No |Yes |
| Google Analytics |No |No |No |No |
| HDFS (Ficheiro do Hadoop) |No |No |No |No |
| Base de Dados IBM DB2 |No |No |Yes |Yes |
| Impala |No |No |No |No |
| Microsoft Exchange |No |No |No |No |
| Microsoft Exchange Online |No |No |No |No |
| Base de Dados MySQL |No |No |Yes |Yes |
| Feed OData |Yes |Yes |Yes |Yes |
| ODBC |Yes |No |Yes |Yes |
| OLE DB |Yes |No |Yes |Yes |
| Base de Dados Oracle |No |No |Yes |Yes |
| Base de Dados PostgreSQL |No |No |Yes |No |
| serviço Power BI |No |No |No |No |
| Script do R |No |No |No |No |
| Objetos do Salesforce |No |No |No |No |
| Relatórios do Salesforce |No |No |No |No |
| SAP Business Warehouse Server |No |No |Yes |No |
| Base de Dados do SAP HANA |No |No |Yes |Yes |
| Pasta do SharePoint (no local) |Yes |No |No |Yes |
| Lista do SharePoint (no local) |Yes |No |No |Yes |
| Lista do SharePoint Online |No |No |No |No |
| Snowflake |No |No |No |No |
| Base de Dados Sybase |No |No |Yes |Yes |
| Teradata |No |No |Yes |Sim** |
| appFigures (Beta) |No |No |No |No |
| Base de Dados do Azure Analysis Services (Beta) |No |No |No |No |
| Azure Cosmos DB (Beta) |No |No |No |No |
| Azure HDInsight Spark (Beta) |No |No |No |No |
| Common Data Service (Beta) |No |No |No |No |
| comScore Digital Analytix (Beta) |No |No |No |No |
| Dynamics 365 for Customer Insights (Beta) |No |No |No |No |
| Dynamics 365 for Financials (Beta) |No |No |No |No |
| GitHub (Beta) |No |No |No |No |
| Google BigQuery (Beta) |No |No |No |No |
| Base de dados IBM Informix (Beta) |No |No |No |No |
| IBM Netezza (Beta) |No |No |No |No |
| Kusto (Beta) |No |No |No |No |
| MailChimp (Beta) |No |No |No |No |
| Microsoft Azure Consumption Insights (Beta) |No |No |No |No |
| Mixpanel (Beta) |No |No |No |No |
| Planview Enterprise (Beta) |No |No |No |No |
| Projectplace (Beta) |No |No |No |No |
| QuickBooks Online (Beta) |No |No |No |No |
| Smartsheet |No |No |No |No |
| Spark (Beta) |No |No |No |No |
| SparkPost (Beta) |No |No |No |No |
| SQL Sentry (Beta) |No |No |No |No |
| Stripe (Beta) |No |No |No |No |
| SweetIQ (Beta) |No |No |No |No |
| Troux (Beta) |No |No |No |No |
| Twilio (Beta) |No |No |No |No |
| tyGraph (Beta) |No |No |No |No |
| Vertica (Beta) |No |No |No |No |
| Visual Studio Team Services (Beta) |No |No |No |No |
| Webtrends (Beta) |No |No |No |No |
| ZenDesk (Beta) |No |No |No |No |

**A utilização da autenticação LDAP com Teradata (ativada no Power BI Desktop com a linha de comandos "setx PBI_EnableTeradataLdap true") não é suportada para a atualização de modelos.

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lista de métodos de autenticação suportados para o DirectQuery

O Power BI Report Server não suporta autenticação com base em OAuth para o DirectQuery.

| **Origem de Dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de Utilizador e Palavra-passe** | **Autenticação do Windows** | **Autenticação Integrada do Windows** |
| --- | --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |No |Yes |Yes |Yes |
| SQL Server Analysis Services |No |No |Yes |Yes |Yes |
| Base de dados SQL do Azure |No |No |Yes |No |No |
| Azure SQL Data Warehouse |No |No |Yes |No |No |
| Base de Dados Oracle |No |No |Yes |Yes |Yes |
| SAP Business Warehouse Server |No |No |Yes |No |No |
| Base de Dados do SAP HANA |No |No |Yes |Yes |Sim** |
| Teradata |No |No |Yes |Yes |Yes |

**O SAP HANA suporta o DirectQuery com Autenticação Integrada do Windows apenas quando a utiliza como base de dados relacional no ficheiro do Power BI Desktop publicado (.pbix).

## <a name="next-steps"></a>Próximas etapas
Agora que estabeleceu ligação à origem de dados, [crie um relatório do Power BI](quickstart-create-powerbi-report.md) com os dados dessa origem de dados.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
