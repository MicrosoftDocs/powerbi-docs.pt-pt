---
title: Origens de dados de relatórios do Power BI no Power BI Report Server
description: Os relatórios do Power BI podem estabelecer ligação a diversas origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 08/04/2020
ms.author: maggies
ms.openlocfilehash: 08294e1320e603131beb0ca332b0f85ee51ea8bb
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937568"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Origens de dados de relatórios do Power BI no Power BI Report Server
Os relatórios do Power BI podem estabelecer ligação a diversas origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados. Pode importar ou consultar dados diretamente através do DirectQuery ou de uma ligação em direto ao SQL Server Analysis Services. Algumas origens de dados estão disponíveis no Power BI Desktop otimizadas para o Power BI Report Server, mas não são suportadas quando publicadas no Power BI Report Server.

Estas origens de dados são específicas para relatórios do Power BI utilizados no Power BI Report Server. Para obter informações sobre as origens de dados suportadas com relatórios paginados (.rdl), veja [Data Sources Supported by Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs) (Origens de Dados Suportadas pelo Reporting Services).

> [!IMPORTANT]
> Todas as origens de dados num relatório do Power BI Desktop têm de suportar a configuração da atualização agendada.
>  

## <a name="list-of-supported-data-sources"></a>Lista de origens de dados suportadas

| **Origem de dados** | **Dados em cache** | **Atualização agendada** | **Live/DirectQuery** |
| --- | --- | --- | --- |
| Base de Dados do SQL Server |Yes |Yes |Yes |
| SQL Server Analysis Services |Sim |Yes |Yes |
| Base de Dados SQL do Azure |Sim |Yes |Yes |
| Azure SQL Data Warehouse |Sim |Yes |Yes |
| Excel |Yes |Yes |Não |
| Base de Dados do Access |Yes |Yes |Não |
| Active Directory |Yes |Yes |Não |
| Amazon Redshift |Sim |Não |No |
| Armazenamento de Blobs do Azure |Sim |Yes |Não |
| Azure Data Lake Store |Sim |Não |No |
| Azure HDInsight (HDFS) |Sim |Não |No |
| Azure HDInsight (Spark) |Sim |Não |No |
| Armazenamento de Tabelas do Azure |Sim |Yes |Não |
| Dynamics 365 (online) |Sim |Não |No |
| Facebook |Sim |Não |No |
| Pasta |Sim |Yes |Não |
| Google Analytics |Sim |Não |No |
| Hadoop File (HDFS) |Sim |Não |No |
| Base de Dados IBM DB2 |Yes |Yes |Não |
| Impala |Sim |Não |No |
| JSON |Sim |Yes |Não |
| Microsoft Exchange |Sim |Não |No |
| Microsoft Exchange Online |Sim |Não |No |
| Base de Dados MySQL |Yes |Yes |Não |
| Feed OData |Yes |Yes |Não |
| ODBC |Sim |Yes |Não |
| OLEDB |Sim |Yes |Não |
| Base de dados Oracle |Yes |Yes |Yes |
| Base de Dados PostgreSQL |Yes |Yes |Não |
| Serviço Power BI |No |No |No |
| Script do R |Sim |Não |No |
| Objetos do Salesforce |Sim |Não |No |
| Relatórios do Salesforce |Sim |Não |No |
| SAP Business Warehouse Server |Yes |Yes |Yes |
| Base de Dados do SAP HANA |Yes |Yes |Yes |
| Pasta do SharePoint (no local) |Sim |Yes |Não |
| Lista do SharePoint (no local) |Sim |Yes |Não |
| Lista do SharePoint Online |Sim |Não |No |
| Snowflake |Sim |Não |No |
| Base de Dados Sybase |Yes |Yes |Não |
| Teradata |Sim |Yes |Yes |
| Texto/CSV |Sim |Yes |Não |
| Web |Sim |Yes |Não |
| XML |Sim |Yes |Não |
| appFigures (Beta) |Sim |Não |No |
| Base de dados do Azure Analysis Services |Sim |Não |Sim |
| Azure Cosmos DB (Beta) |Sim |Não |No |
| Azure HDInsight Spark (Beta) |Sim |Não |No |
| Common Data Service (Beta) |Sim |Não |No |
| comScore Digital Analytix (Beta) |Sim |Não |No |
| Dynamics 365 for Customer Insights (Beta) |Sim |Não |No |
| Dynamics 365 for Financials (Beta) |Sim |Não |No |
| GitHub (Beta) |Sim |Não |No |
| Google BigQuery (Beta) |Sim |Não |No |
| Base de dados IBM Informix (Beta) |Sim |Não |No |
| IBM Netezza (Beta) |Sim |Não |No |
| Kusto (Beta) |Sim |Não |No |
| MailChimp (Beta) |Sim |Não |No |
| Microsoft Azure Consumption Insights (Beta) |Sim |Não |No |
| Mixpanel (Beta) |Sim |Não |No |
| Planview Enterprise (Beta) |Sim |Não |No |
| Projectplace (Beta) |Sim |Não |No |
| QuickBooks Online (Beta) |Sim |Não |No |
| Smartsheet |Sim |Não |No |
| Spark (Beta) |Sim |Não |No |
| SparkPost (Beta) |Sim |Não |No |
| SQL Sentry (Beta) |Sim |Não |No |
| Stripe (Beta) |Sim |Não |No |
| SweetIQ (Beta) |Sim |Não |No |
| Troux (Beta) |Sim |Não |No |
| Twilio (Beta) |Sim |Não |No |
| tyGraph (Beta) |Sim |Não |No |
| Vertica (Beta) |Sim |Não |No |
| Visual Studio Team Services (Beta) |Sim |Não |No |
| Webtrends (Beta) |Sim |Não |No |
| ZenDesk (Beta) |Sim |Não |No |

> [!IMPORTANT]
> A segurança ao nível da linha configurada na origem de dados deve funcionar para determinadas ligações DirectQuery (SQL Server, Base de Dados SQL do Azure, Oracle e Teradata) e em direto ao assumir que o Kerberos está configurado corretamente no seu ambiente.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Lista de métodos de autenticação suportados para a atualização de modelos

O Power BI Report Server não suporta autenticação com base em OAuth para a atualização de modelos. Algumas origens de dados, como as bases de dados do Access ou do Excel, utilizam um passo separado como Ficheiro ou Web para ligar aos dados.

| **Origem de dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de utilizador e Palavra-passe** | **Autenticação do Windows** |
| --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |No |Sim |Yes |
| SQL Server Analysis Services |No |No |Sim |Yes |
| Web |Sim |Não |Sim |Yes |
| Base de Dados SQL do Azure |No |No |Sim |Não |
| Azure SQL Data Warehouse |No |No |Sim |Não |
| Active Directory |No |No |Sim |Yes |
| Amazon Redshift |No |No |No |No |
| Armazenamento de Blobs do Azure |Sim |Yes |Não |No |
| Azure Data Lake Store |No |No |No |No |
| Azure HDInsight (HDFS) |No |No |No |No |
| Azure HDInsight (Spark) |No |No |No |No |
| Armazenamento de Tabelas do Azure |Não |Sim |Não |No |
| Dynamics 365 (online) |No |No |No |No |
| Facebook |No |No |No |No |
| Pasta |No |No |No |Sim |
| Google Analytics |No |No |No |No |
| Hadoop File (HDFS) |No |No |No |No |
| Base de Dados IBM DB2 |No |No |Sim |Yes |
| Impala |No |No |No |No |
| Microsoft Exchange |No |No |No |No |
| Microsoft Exchange Online |No |No |No |No |
| Base de Dados MySQL |No |No |Sim |Yes |
| Feed OData |Yes |Yes |Yes |Yes |
| ODBC |Sim |Não |Sim |Yes |
| OLEDB |Sim |Não |Sim |Yes |
| Base de dados Oracle |No |No |Sim |Yes |
| Base de Dados PostgreSQL |No |No |Sim |Não |
| Serviço Power BI |No |No |No |No |
| Script do R |No |No |No |No |
| Objetos do Salesforce |No |No |No |No |
| Relatórios do Salesforce |No |No |No |No |
| SAP Business Warehouse Server |No |No |Sim |Não |
| Base de Dados do SAP HANA |No |No |Sim |Yes |
| Pasta do SharePoint (no local) |Sim |Não |No |Sim |
| Lista do SharePoint (no local) |Sim |Não |No |Sim |
| Lista do SharePoint Online |No |No |No |No |
| Snowflake |No |No |No |No |
| Base de Dados Sybase |No |No |Sim |Yes |
| Teradata |No |No |Sim |Sim** |
| appFigures (Beta) |No |No |No |No |
| Base de dados do Azure Analysis Services (Beta) |No |No |No |No |
| Azure Cosmos DB (Beta) |No |No |No |No |
| Azure HDInsight Spark (Beta) |No |No |No |No |
| Common Data Service (Beta) |No |No |No |No |
| comScore Digital Analytix (Beta) |No |No |No |No |
| Dynamics 365 for Customer Insights (Beta) |No |No |No |No |
| Dynamics 365 for Financials (Beta) |No |No |No |No |
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

| **Origem de dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de utilizador e Palavra-passe** | **Autenticação do Windows** | **Autenticação Integrada do Windows** |
| --- | --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |No |Sim |Yes |Yes |
| SQL Server Analysis Services |No |No |Sim |Yes |Yes |
| Base de Dados SQL do Azure |No |No |Sim |Não |No |
| Azure SQL Data Warehouse |No |No |Sim |Não |No |
| Base de dados Oracle |No |No |Sim |Yes |Yes |
| SAP Business Warehouse Server |No |No |Sim |Não |No |
| Base de Dados do SAP HANA |No |No |Sim |Yes |Sim** |
| Teradata |No |No |Sim |Yes |Yes |

**O SAP HANA suporta o DirectQuery com Autenticação Integrada do Windows apenas quando a utiliza como base de dados relacional no ficheiro do Power BI Desktop publicado (.pbix).

## <a name="next-steps"></a>Passos seguintes

[Origens de dados dos relatórios do Power BI](../connect-data/power-bi-data-sources.md) no serviço Power BI

Agora que estabeleceu ligação à origem de dados, [crie um relatório do Power BI](quickstart-create-powerbi-report.md) com os dados dessa origem de dados.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
