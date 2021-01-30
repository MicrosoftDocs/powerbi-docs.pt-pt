---
title: Origens de dados do Power BI
description: O presente artigo lista as origens de dados suportadas pelo Power BI, incluindo informações sobre o DirectQuery e o gateway de dados no local.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/14/2020
ms.openlocfilehash: def849c9a3b867f181dbc91628260cf24491e855
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087942"
---
# <a name="power-bi-data-sources"></a>Origens de dados do Power BI

A seguinte tabela apresenta as origens de dados suportadas pelo Power BI para os conjuntos de dados, incluindo informações sobre o DirectQuery e o gateway de dados no local. Para obter mais informações acerca dos fluxos de dados, veja [Ligar a origens de dados dos fluxos de dados do Power BI](../transform-model/dataflows/dataflows-configure-consume.md).

| Origem de dados | Ligar a partir do Ambiente de Trabalho | Ligar e atualizar a partir do serviço | DirectQuery/Ligação em direto | Gateway (suportado) | Gateway (necessário) | Fluxos de Dados do Power BI |
|---|---|---|---|---|---|---|---|
| Base de dados do Access | Sim | Yes | Não | Sim <sup>1</sup> | Sim | Sim |
| ActiveDirectory | Sim | Yes | No | Yes | Sim | Sim |
| Adobe Analytics | Sim | Yes | No | No | No | Não |
| Amazon Redshift | Sim | Yes | Sim | Sim | No | Sim |
| appFigures | Sim | Sim | No | No | No | Não |
| Cubos AtScale | Sim | Sim | Sim | Yes | Não | Não |
| Azure Analysis Services | Sim | Yes | Yes | Não | No | No |
| Armazenamento de Blobs do Azure | Yes | Yes | Não | Yes | No | Sim |
| Azure Cosmos DB | Sim | Yes | No | No | No | Não |
| Azure Cost Management | Sim | Yes | No | No | No | Não |
| Azure Data Explorer (kusto) | Sim | Sim | Sim | Yes | No | Sim |
| Azure Data Lake Storage Gen1 | Sim | Sim | No | Não | Não | Não |
| Azure Data Lake Storage Gen2 | Sim | Yes | No | Sim | No | Sim |
| Azure Databricks | Yes | Yes | Yes | Yes | No | Não |
| Azure DevOps | Sim | Yes | No | No | No | Não |
| Azure DevOps Server | Sim | Yes | No | Sim | Sim | No |
| Azure HDInsight (HDFS) | Sim | Yes | No | No | No | Não |
| Azure HDInsight Spark | Sim | Sim | Sim | No | No | Yes |
| Base de Dados SQL do Azure | Sim | Yes | Yes | Yes | No | Sim |
| Azure SQL Data Warehouse | Yes | Yes | Yes | Yes | No | Sim |
| Armazenamento de Tabelas do Azure | Yes | Yes | No | Sim | No | Sim |
| Conector BI | Sim | Yes | Sim | Sim | Sim | Não |
| BI360 - Budgeting & Financial Reporting | Sim | Sim | No | No | Não | Não |
| Microsoft Dataverse | Sim | Sim | Yes | Não | Não | Sim |
| Data.World - Obter Conjunto de Dados | Sim | Yes | Não | Não | No | Não |
| Denodo | Sim | Yes | Yes | Yes | Sim | Não |
| Dremio | Sim | Yes | Yes | Sim | Sim | No |
| Dynamics 365 (online) | Sim | Yes | No | No | No | Não |
| Dynamics 365 Business Central | Sim | Sim | No | No | No | Não |
| Dynamics 365 Business Central (no local) | Sim | Sim | No | No | No | Não |
| Dynamics 365 Customer Insights | Sim | Yes | No | No | No | Não |
| Dynamics NAV | Sim | Yes | Não | No | No | Não |
| Origem de Dados Emigo | Yes | Sim | No | No | No | No |
| Entersoft Business Suite | Sim | Yes | No | No | No | Não |
| Essbase | Sim | Sim | Sim | Yes | Yes | Não |
| Exasol | Sim | Sim | Sim | Yes | Yes | Não |
| Excel | Sim <sup>3</sup> | Sim <sup>3</sup> | Não | Sim <sup>3</sup> | Não <sup>4</sup> | Sim |
| Facebook | Sim | Yes | Não | No | No | Não |
| Ficheiro | Sim | Yes | No | Sim | Sim | Sim |
| Pasta | Yes | Yes | No | Sim | Sim | Sim |
| GitHub | Sim | Sim | No | No | No | Não |
| Google Analytics | Sim | Sim | No | No | No | Não |
| Google BigQuery | Sim | Yes | Yes | Yes | No | Sim |
| Hadoop File (HDFS) | Sim | Não | Não | No | No | Não |
| LLAP do Hive | Sim | Sim | Yes | Sim | No | No |
| Interactive Query do HDInsight | Sim | Yes | Sim | No | No | Não |
| IBM DB2 | Sim | Yes | Sim | Yes | No | Sim |
| IBM Informix Database | Sim | Sim | No | Sim | No | Não |
| IBM Netezza | Sim | Yes | Yes | Yes | Yes | Não |
| Impala | Sim | Yes | Yes | Yes | Sim | Sim |
| Indexima | Sim | Sim | Yes | Sim | Sim | No |
| Industrial App Store | Sim | Yes | No | No | No | No |
| Information Grid | Sim | Sim | No | No | Não | Não |
| InterSystems IRIS | Sim | Sim | Yes | Yes | Yes | Não |
| Intune Data Warehouse | Sim | Yes | Não | Não | No | Não |
| ODBC da Jethro | Sim | Yes | Sim | Yes | Sim | No |
| JSON | Yes | Yes | Não | Sim** | Não <sup>4</sup> | Sim |
| Kyligence Enterprise | Sim | Yes | Sim | Sim | Yes | No |
| MailChimp | Yes | Sim | No | No | No | No |
| Marketo | Sim | Sim | No | No | Não | Não |
| ODBC da MarkLogic | Sim | Yes | Sim | Yes | Yes | Não |
| Microsoft Azure Consumption Insights | Sim | Yes | Não | No | No | No |
| Microsoft Exchange | Sim | Yes | No | Sim | No | No |
| Microsoft Exchange Online | Sim | Yes | No | No | No | Sim |
| Segurança do Microsoft Graph | Sim | Sim | No | Yes | Não | Não |
| Mixpanel | Sim | Sim | No | No | Não | Não |
| MySQL | Sim | Yes | Não | Yes | Yes | Sim |
| OData | Sim | Sim <sup>7</sup> | Não | Yes | No | Sim |
| ODBC | Sim | Sim | No | Sim | Sim | Sim |
| OleDb | Sim | Yes | No | Sim | Yes | Não |
| Oracle | Sim | Sim | Yes | Yes | Yes | Sim |
| Paxata <sup>8</sup> | Sim | Sim | No | Yes | No | Não |
| PDF | Sim | Yes | Não | Sim | Não <sup>4</sup> | Sim |
| Planview Enterprise One - CTM | Sim | Yes | Não | No | No | Não |
| Planview Enterprise One - PRM | Sim | Sim | No | No | No | Não |
| Planview Projectplace | Sim | Yes | No | No | No | Não |
| PostgreSQL | Sim | Sim | Sim | Yes | No | Sim |
| Fluxos de dados do Power BI | Sim | Sim | No | No | No | Sim |
| Conjuntos de dados do Power BI | Sim | Yes | Yes | Não | No | Não |
| Power platform dataflows (Fluxos de dados do Power Platform) | Sim | Yes | Não | No | No | Sim |
| Script de Python | Sim | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Sim | Não |
| QubolePresto | Sim | Yes | Sim | Sim | Yes | Não |
| Quick Base | Sim | Sim | No | Sim | Sim | Não |
| QuickBooks Online | Yes | Sim | No | No | No | Não |
| Script R | Sim | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Não | Não |
| Roamler | Yes | Yes | Não | Yes | No | No |
| Objetos do Salesforce | Sim | Yes | No | No | No | Sim |
| Relatórios do Salesforce | Sim | Yes | No | No | No | Yes |
| SAP Business Warehouse Message Server | Sim | Sim | Sim | Yes | Yes | Yes |
| SAP Business Warehouse Server | Yes | Sim | Sim | Sim | Sim | Yes |
| SAP HANA | Sim | Yes | Sim | Yes | Yes | Sim |
| Pasta do SharePoint | Yes | Yes | Não | Sim | Não <sup>4</sup> | Sim |
| Lista do SharePoint | Sim | Yes | No | Sim | Não <sup>4</sup> | Sim |
| Lista do SharePoint Online | Sim | Yes | No | Sim | No | Sim |
| Smartsheet | Sim | Sim | No | No | Não | Sim |
| Snowflake | Sim | Sim | Yes | Yes | Não | Sim |
| Spark | Sim | Yes | Sim | Yes | No | Sim |
| SparkPost | Sim | Yes | Não | No | No | Não |
| SQL Server | Sim | Yes | Yes | Yes | Yes | Yes |
| SQL Server Analysis Services | Yes | Yes | Yes | Yes | Yes | Não |
| Stripe | Sim | Yes | No | No | No | Não |
| SurveyMonkey | Sim | Yes | No | Yes | No | Não |
| SweetIQ | Sim | Yes | No | No | No | Não |
| Sybase | Sim | Yes | No | Yes | Yes | Sim |
| TeamDesk | Sim | Yes | No | Yes | No | Não |
| Tenforce | Sim | Yes | No | No | No | Não |
| Teradata | Yes | Yes | Yes | Yes | Yes | Yes |
| Texto/CSV | Yes | Yes | No | Sim | Não <sup>4</sup> | Sim |
| Twilio | Sim | Yes | No | No | No | Não |
| tyGraph | Sim | Yes | No | No | No | Não |
| Vertica | Sim | Yes | Yes | Yes | Yes | Yes |
| Web | Yes | Yes | No | Sim | Sim <sup>6</sup> | Sim |
| Webtrends | Sim | Yes | No | No | No | Não |
| Workforce Dimensions | Sim | Yes | No | Yes | No | Não |
| XML | Yes | Yes | No | Sim | Não <sup>4</sup> | Sim |
| Zendesk | Sim | Yes | No | No | No | Não |
| | | | | | | | |

<sup>1</sup> Suportado com o [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920), instalado no mesmo computador que o gateway.

<sup>3</sup> Os ficheiros de Excel 1997-2003 (.xls) necessitam do [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Necessário para a versão no local da tecnologia.

<sup>5</sup> Suportado apenas com o [gateway pessoal](service-gateway-personal-mode.md).

<sup>6</sup> Necessário para .html, .xls e Bases de Dados do Access

<sup>7</sup> O serviço Power BI não suporta o método OAuth2 genérico.

<sup>8</sup> O Paxata é suportado na versão do Power BI Desktop otimizada para o Power BI Report Server. Não é suportado nos relatórios do Power BI publicados no Power BI Report Server. Veja [Origens de dados de relatórios do Power BI no Power BI Report Server](../report-server/data-sources.md) para obter a lista de origens de dados suportadas.

## <a name="considerations-and-limitations"></a>Considerações e limitações

- Muitos conectores de dados para o Power BI Desktop necessitam do Internet Explorer 10 (ou mais recente) para autenticação. 
- Algumas origens de dados estão disponíveis no Power BI Desktop otimizadas para o Power BI Report Server, mas não são suportadas quando publicadas no Power BI Report Server. Veja [Origens de dados de relatórios do Power BI no Power BI Report Server](../report-server/data-sources.md) para obter a lista de origens de dados suportadas.

## <a name="single-sign-on-sso-for-directquery-sources"></a>Início de sessão único (SSO) para origens de dados do DirectQuery

Quando a opção SSO está ativada e os utilizadores acedem aos relatórios compilados por cima da origem de dados, o Power BI envia as suas credenciais autenticadas do Azure AD nas consultas para a origem de dados subjacente. Esta operação permite que o Power BI respeite as definições de segurança que estão configuradas ao nível da origem de dados.
A opção SSO tem efeito em todos os conjuntos de dados que utilizam esta origem de dados. Não afeta o método de autenticação utilizado para os cenários de importação. As seguintes origens de dados suportam SSO para ligações através do DirectQuery:

- Base de Dados SQL do Azure
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Servidor de Mensagens SAP BW
- Snowflake
- Spark
- SQL Server
- Teradata

## <a name="next-steps"></a>Próximos passos

[Ligar a dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)  
[Dados dinâmicos do SQL Server Analysis Services no Power BI](sql-server-analysis-services-tabular-data.md)  
[What is an on-premises data gateway?](service-gateway-onprem.md) (O que é um gateway de dados no local?)  
[Origens de dados de relatórios do Power BI no Power BI Report Server](../report-server/data-sources.md)
