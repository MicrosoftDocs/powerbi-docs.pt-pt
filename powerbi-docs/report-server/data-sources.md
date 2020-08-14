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
ms.openlocfilehash: 00c00ca7bbd7ad3f901c98f44a2900f332e3616a
ms.sourcegitcommit: 65822b51810a5239fea9d3d0af1fc286436c6cad
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2020
ms.locfileid: "87837618"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Origens de dados de relatórios do Power BI no Power BI Report Server
Os relatórios do Power BI podem estabelecer ligação a diversas origens de dados. Consoante a forma como os dados são utilizados, estão disponíveis diferentes origens de dados. Pode importar ou consultar dados diretamente através do DirectQuery ou de uma ligação em direto ao SQL Server Analysis Services. Algumas origens de dados são suportadas no Power BI Desktop otimizado para o Power BI Report Server, mas não são otimizadas para os relatórios do Power BI publicados no Power BI Report Server. Veja a lista seguinte para saber quais as origens de dados suportadas em ambos os locais.

Estas origens de dados são específicas para relatórios do Power BI utilizados no Power BI Report Server. Para obter informações sobre as origens de dados suportadas com relatórios paginados (.rdl), veja [Data Sources Supported by Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs) (Origens de Dados Suportadas pelo Reporting Services).

> [!IMPORTANT]
> Todas as origens de dados num relatório do Power BI Desktop têm de suportar a configuração da atualização agendada.
>  

## <a name="list-of-supported-data-sources"></a>Lista de origens de dados suportadas

| **Origem de dados** | **Dados em cache** | **Atualização agendada** | **Live/DirectQuery** |
| --- | --- | --- | --- |
| Base de Dados do SQL Server |Yes |Yes |Sim |
| SQL Server Analysis Services |Yes |Yes |Sim |
| Base de Dados SQL do Azure |Yes |Yes |Sim |
| Azure SQL Data Warehouse |Yes |Yes |Sim |
| Excel |Yes |Sim |Não |
| Base de Dados do Access |Yes |Sim |Não |
| Active Directory |Yes |Sim |Não |
| Amazon Redshift |Sim |No |Não |
| Armazenamento de Blobs do Azure |Yes |Sim |Não |
| Azure Data Lake Store |Sim |No |Não |
| Azure HDInsight (HDFS) |Sim |No |Não |
| Azure HDInsight (Spark) |Sim |No |Não |
| Armazenamento de Tabelas do Azure |Yes |Sim |Não |
| Dynamics 365 (online) |Sim |No |Não |
| Facebook |Sim |No |Não |
| Pasta |Yes |Sim |Não |
| Google Analytics |Sim |No |Não |
| Hadoop File (HDFS) |Sim |No |Não |
| Base de Dados IBM DB2 |Yes |Sim |Não |
| Impala |Sim |No |Não |
| JSON |Yes |Sim |Não |
| Microsoft Exchange |Sim |No |Não |
| Microsoft Exchange Online |Sim |No |Não |
| Base de Dados MySQL |Yes |Sim |Não |
| Feed OData |Yes |Sim |Não |
| ODBC |Yes |Sim |Não |
| OLEDB |Yes |Sim |Não |
| Base de dados Oracle |Yes |Yes |Sim |
| Base de Dados PostgreSQL |Yes |Sim |Não |
| Serviço Power BI |No |No |Não |
| Script do R |Sim |No |Não |
| Objetos do Salesforce |Sim |No |Não |
| Relatórios do Salesforce |Sim |No |Não |
| SAP Business Warehouse Server |Yes |Yes |Sim |
| Base de Dados do SAP HANA |Yes |Yes |Sim |
| Pasta do SharePoint (no local) |Yes |Sim |Não |
| Lista do SharePoint (no local) |Yes |Sim |Não |
| Lista do SharePoint Online |Sim |No |Não |
| Snowflake |Sim |No |Não |
| Base de Dados Sybase |Yes |Sim |Não |
| Teradata |Yes |Yes |Sim |
| Texto/CSV |Yes |Sim |Não |
| Web |Yes |Sim |Não |
| XML |Yes |Sim |Não |
| appFigures (Beta) |Sim |No |Não |
| Base de dados do Azure Analysis Services |Sim |Não |Sim |
| Azure Cosmos DB (Beta) |Sim |No |Não |
| Azure HDInsight Spark (Beta) |Sim |No |Não |
| Common Data Service (Beta) |Sim |No |Não |
| comScore Digital Analytix (Beta) |Sim |No |Não |
| Dynamics 365 for Customer Insights (Beta) |Sim |No |Não |
| Dynamics 365 for Financials (Beta) |Sim |No |Não |
| GitHub (Beta) |Sim |No |Não |
| Google BigQuery (Beta) |Sim |No |Não |
| Base de dados IBM Informix (Beta) |Sim |No |Não |
| IBM Netezza (Beta) |Sim |No |Não |
| Kusto (Beta) |Sim |No |Não |
| MailChimp (Beta) |Sim |No |Não |
| Microsoft Azure Consumption Insights (Beta) |Sim |No |Não |
| Mixpanel (Beta) |Sim |No |Não |
| Planview Enterprise (Beta) |Sim |No |Não |
| Projectplace (Beta) |Sim |No |Não |
| QuickBooks Online (Beta) |Sim |No |Não |
| Smartsheet |Sim |No |Não |
| Spark (Beta) |Sim |No |Não |
| SparkPost (Beta) |Sim |No |Não |
| SQL Sentry (Beta) |Sim |No |Não |
| Stripe (Beta) |Sim |No |Não |
| SweetIQ (Beta) |Sim |No |Não |
| Troux (Beta) |Sim |No |Não |
| Twilio (Beta) |Sim |No |Não |
| tyGraph (Beta) |Sim |No |Não |
| Vertica (Beta) |Sim |No |Não |
| Visual Studio Team Services (Beta) |Sim |No |Não |
| Webtrends (Beta) |Sim |No |Não |
| ZenDesk (Beta) |Sim |No |Não |

> [!IMPORTANT]
> A segurança ao nível da linha configurada na origem de dados deve funcionar para determinadas ligações DirectQuery (SQL Server, Base de Dados SQL do Azure, Oracle e Teradata) e em direto ao assumir que o Kerberos está configurado corretamente no seu ambiente.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Lista de métodos de autenticação suportados para a atualização de modelos

O Power BI Report Server não suporta autenticação com base em OAuth para a atualização de modelos. Algumas origens de dados, como as bases de dados do Access ou do Excel, utilizam um passo separado como Ficheiro ou Web para ligar aos dados.

| **Origem de dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de utilizador e Palavra-passe** | **Autenticação do Windows** |
| --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |Não |Yes |Sim |
| SQL Server Analysis Services |No |Não |Yes |Sim |
| Web |Sim |Não |Yes |Sim |
| Base de Dados SQL do Azure |No |Não |Sim |Não |
| Azure SQL Data Warehouse |No |Não |Sim |Não |
| Active Directory |No |Não |Yes |Sim |
| Amazon Redshift |No |No |No |Não |
| Armazenamento de Blobs do Azure |Yes |Sim |No |Não |
| Azure Data Lake Store |No |No |No |Não |
| Azure HDInsight (HDFS) |No |No |No |Não |
| Azure HDInsight (Spark) |No |No |No |Não |
| Armazenamento de Tabelas do Azure |Não |Sim |No |Não |
| Dynamics 365 (online) |No |No |No |Não |
| Facebook |No |No |No |Não |
| Pasta |No |No |Não |Sim |
| Google Analytics |No |No |No |Não |
| Hadoop File (HDFS) |No |No |No |Não |
| Base de Dados IBM DB2 |No |Não |Yes |Sim |
| Impala |No |No |No |Não |
| Microsoft Exchange |No |No |No |Não |
| Microsoft Exchange Online |No |No |No |Não |
| Base de Dados MySQL |No |Não |Yes |Sim |
| Feed OData |Yes |Yes |Yes |Sim |
| ODBC |Sim |Não |Yes |Sim |
| OLEDB |Sim |Não |Yes |Sim |
| Base de dados Oracle |No |Não |Yes |Sim |
| Base de Dados PostgreSQL |No |Não |Sim |Não |
| Serviço Power BI |No |No |No |Não |
| Script do R |No |No |No |Não |
| Objetos do Salesforce |No |No |No |Não |
| Relatórios do Salesforce |No |No |No |Não |
| SAP Business Warehouse Server |No |Não |Sim |Não |
| Base de Dados do SAP HANA |No |Não |Yes |Sim |
| Pasta do SharePoint (no local) |Sim |No |Não |Sim |
| Lista do SharePoint (no local) |Sim |No |Não |Sim |
| Lista do SharePoint Online |No |No |No |Não |
| Snowflake |No |No |No |Não |
| Base de Dados Sybase |No |Não |Yes |Sim |
| Teradata |No |Não |Sim |Sim** |
| appFigures (Beta) |No |No |No |Não |
| Base de dados do Azure Analysis Services (Beta) |No |No |No |Não |
| Azure Cosmos DB (Beta) |No |No |No |Não |
| Azure HDInsight Spark (Beta) |No |No |No |Não |
| Common Data Service (Beta) |No |No |No |Não |
| comScore Digital Analytix (Beta) |No |No |No |Não |
| Dynamics 365 for Customer Insights (Beta) |No |No |No |Não |
| Dynamics 365 for Financials (Beta) |No |No |No |Não |
| GitHub (Beta) |No |No |No |Não |
| Google BigQuery (Beta) |No |No |No |Não |
| Base de dados IBM Informix (Beta) |No |No |No |Não |
| IBM Netezza (Beta) |No |No |No |Não |
| Kusto (Beta) |No |No |No |Não |
| MailChimp (Beta) |No |No |No |Não |
| Microsoft Azure Consumption Insights (Beta) |No |No |No |Não |
| Mixpanel (Beta) |No |No |No |Não |
| Planview Enterprise (Beta) |No |No |No |Não |
| Projectplace (Beta) |No |No |No |Não |
| QuickBooks Online (Beta) |No |No |No |Não |
| Smartsheet |No |No |No |Não |
| Spark (Beta) |No |No |No |Não |
| SparkPost (Beta) |No |No |No |Não |
| SQL Sentry (Beta) |No |No |No |Não |
| Stripe (Beta) |No |No |No |Não |
| SweetIQ (Beta) |No |No |No |Não |
| Troux (Beta) |No |No |No |Não |
| Twilio (Beta) |No |No |No |Não |
| tyGraph (Beta) |No |No |No |Não |
| Vertica (Beta) |No |No |No |Não |
| Visual Studio Team Services (Beta) |No |No |No |Não |
| Webtrends (Beta) |No |No |No |Não |
| ZenDesk (Beta) |No |No |No |Não |

**A utilização da autenticação LDAP com Teradata (ativada no Power BI Desktop com a linha de comandos "setx PBI_EnableTeradataLdap true") não é suportada para a atualização de modelos.

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Lista de métodos de autenticação suportados para o DirectQuery

O Power BI Report Server não suporta autenticação com base em OAuth para o DirectQuery.

| **Origem de dados** | **Autenticação Anónima** | **Autenticação da Chave** | **Nome de utilizador e Palavra-passe** | **Autenticação do Windows** | **Autenticação Integrada do Windows** |
| --- | --- | --- | --- | --- | --- |
| Base de Dados do SQL Server |No |Não |Yes |Yes |Sim |
| SQL Server Analysis Services |No |Não |Yes |Yes |Sim |
| Base de Dados SQL do Azure |No |Não |Sim |No |Não |
| Azure SQL Data Warehouse |No |Não |Sim |No |Não |
| Base de dados Oracle |No |Não |Yes |Yes |Sim |
| SAP Business Warehouse Server |No |Não |Sim |No |Não |
| Base de Dados do SAP HANA |No |Não |Yes |Sim |Sim** |
| Teradata |No |Não |Yes |Yes |Sim |

**O SAP HANA suporta o DirectQuery com Autenticação Integrada do Windows apenas quando a utiliza como base de dados relacional no ficheiro do Power BI Desktop publicado (.pbix).

## <a name="next-steps"></a>Passos seguintes

[Origens de dados para relatórios do Power BI[(../connect-data/power-bi-data-sources.md) no serviço Power BI Agora que estabeleceu ligação à origem de dados, [crie um relatório do Power BI](quickstart-create-powerbi-report.md) com os dados dessa origem de dados.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
