---
title: Origens de dados do Power BI
description: O presente artigo lista as origens de dados suportadas pelo Power BI, incluindo informações sobre o DirectQuery e o gateway de dados no local.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2020
ms.author: davidi
ms.openlocfilehash: 0bc6b844457f625d0287f2ec85f582a6ea874624
ms.sourcegitcommit: 6d3a37eb636e1b71c7dcb9d1c3a9e495b78dec97
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681865"
---
# <a name="power-bi-data-sources"></a>Origens de dados do Power BI

A seguinte tabela apresenta as origens de dados suportadas pelo Power BI para os conjuntos de dados, incluindo informações sobre o DirectQuery e o gateway de dados no local. Para obter mais informações acerca dos fluxos de dados, veja [Ligar a origens de dados dos fluxos de dados do Power BI](../transform-model/service-dataflows-data-sources.md).

> [!NOTE]
> Existem muitos conectores de dados para o Power BI Desktop que requerem o Internet Explorer 10 (ou mais recente) para autenticação. 


| Origem de dados | Ligar a partir do Ambiente de Trabalho | Ligar e atualizar a partir do serviço | DirectQuery/Ligação em direto | Gateway (suportado) | Gateway (necessário) |
|---|---|---|---|---|---|---|---|
| Base de dados do Access | Sim | Sim | Não | Sim <sup>1</sup> | Sim |
| ActiveDirectory | Sim | Sim | Não | Sim | Sim |
| Adobe Analytics | Sim | Sim | Não | Não | Não |
| Amazon Redshift | Sim | Sim | Sim | Sim | Não |
| appFigures | Sim | Sim | Não | Não | Não |
| Cubos AtScale | Sim | Sim | Sim | Sim | Não |
| Azure Analysis Services | Sim | Sim | Sim | Não | Não |
| Armazenamento de Blobs do Azure | Sim | Sim | Não | Sim | Não |
| Azure Cosmos DB | Sim | Sim | Não | Não | Não |
| Azure Cost Management | Sim | Sim | Não | Não | Não |
| Azure Data Explorer (kusto) | Sim | Sim | Sim | Não | Não |
| Azure Data Lake Storage Gen1 | Sim | Sim | Não | Não | Não |
| Azure Data Lake Storage Gen2 | Sim | Sim | Não | Sim | Não |
| Azure DevOps | Sim | Sim | Não | Não | Não |
| Azure DevOps Server | Sim | Sim | Não | Sim | Sim |
| Azure HDInsight (HDFS) | Sim | Sim | Não | Não | Não |
| Azure HDInsight Spark | Sim | Sim | Sim | Não | Não |
| Base de Dados SQL do Azure | Sim | Sim | Sim | Sim <sup>2</sup> | Não |
| Azure SQL Data Warehouse | Sim | Sim | Sim | Sim <sup>2</sup> | Não |
| Armazenamento de Tabelas do Azure | Sim | Sim | Não | Sim | Não |
| Conector BI | Sim | Sim | Sim | Sim | Sim |
| BI360 - Budgeting & Financial Reporting | Sim | Sim | Não | Não | Não |
| Common Data Service | Sim | Sim | Não | Não | Não |
| Data.World - Obter Conjunto de Dados | Sim | Sim | Não | Não | Não |
| Denodo | Sim | Sim | Sim | Sim | Sim |
| Dremio | Sim | Sim | Sim | Sim | Sim |
| Dynamics 365 (online) | Sim | Sim | Não | Não | Não |
| Dynamics 365 Business Central | Sim | Sim | Não | Não | Não |
| Dynamics 365 Business Central (no local) | Sim | Sim | Não | Não | Não |
| Dynamics 365 Customer Insights | Sim | Sim | Não | Não | Não |
| Dynamics NAV | Sim | Sim | Não | Não | Não |
| Origem de Dados Emigo | Sim | Sim | Não | Não | Não |
| Entersoft Business Suite | Sim | Sim | Não | Não | Não |
| Essbase | Sim | Sim | Sim | Sim | Sim |
| Exasol | Sim | Sim | Sim | Sim | Sim |
| Excel | Sim <sup>3</sup> | Sim <sup>3</sup> | Não | Sim <sup>3</sup> | Não <sup>4</sup> |
| Facebook | Sim | Sim | Não | Não | Não |
| Ficheiro | Sim | Sim | Não | Sim | Sim |
| Pasta | Sim | Sim | Não | Sim | Sim |
| GitHub | Sim | Sim | Não | Não | Não |
| Google Analytics | Sim | Sim | Não | Não | Não |
| Google BigQuery | Sim | Sim | Sim | Não | Não |
| Hadoop File (HDFS) | Sim | Não | Não | Não | Não |
| Interactive Query do HDInsight | Sim | Sim | Sim | Não | Não |
| IBM DB2 | Sim | Sim | Sim | Sim | Não |
| IBM Informix Database | Sim | Sim | Não | Sim | Não |
| IBM Netezza | Sim | Sim | Sim | Sim | Sim |
| Impala | Sim | Sim | Sim | Sim | Sim |
| Indexima | Sim | Sim | Sim | Sim | Sim |
| Industrial App Store | Sim | Sim | Não | Não | Não |
| Information Grid | Sim | Sim | Não | Não | Não |
| InterSystems IRIS | Sim | Sim | Sim | Sim | Sim |
| Intune Data Warehouse | Sim | Sim | Não | Não | Não |
| ODBC da Jethro | Sim | Sim | Sim | Sim | Sim |
| JSON | Sim | Sim | Não | Sim** | Não <sup>4</sup> |
| Kyligence Enterprise | Sim | Sim | Sim | Sim | Sim |
| MailChimp | Sim | Sim | Não | Não | Não |
| Marketo | Sim | Sim | Não | Não | Não |
| ODBC da MarkLogic | Sim | Sim | Sim | Sim | Sim |
| Microsoft Azure Consumption Insights | Sim | Sim | Não | Não | Não |
| Microsoft Exchange | Sim | Sim | Não | Sim | Não |
| Microsoft Exchange Online | Sim | Sim | Não | Não | Não |
| Segurança do Microsoft Graph | Sim | Sim | Não | Sim | Não |
| Mixpanel | Sim | Sim | Não | Não | Não |
| MySQL | Sim | Sim | Não | Sim | Sim |
| OData | Sim | Sim <sup>7</sup> | Não | Sim | Não |
| ODBC | Sim | Sim | Não | Sim | Sim |
| OleDb | Sim | Sim | Não | Sim | Sim |
| Oracle | Sim | Sim | Sim | Sim | Sim |
| Paxata | Sim | Sim | Não | Sim | Não |
| PDF | Sim | Sim | Não | Sim | Não <sup>4</sup> |
| Planview Enterprise One - CTM | Sim | Sim | Não | Não | Não |
| Planview Enterprise One - PRM | Sim | Sim | Não | Não | Não |
| Planview Projectplace | Sim | Sim | Não | Não | Não |
| PostgreSQL | Sim | Sim | Sim | Sim | Não |
| Fluxos de dados do Power BI | Sim | Sim | Não | Não | Não |
| Conjuntos de dados do Power BI | Sim | Sim | Sim | Não | Não |
| Power platform dataflows (Fluxos de dados do Power Platform) | Sim | Sim | Não | Não | Não |
| Script de Python | Sim | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Sim |
| QubolePresto | Sim | Sim | Sim | Sim | Sim |
| Quick Base | Sim | Sim | Não | Sim | Sim |
| QuickBooks Online | Sim | Sim | Não | Não | Não |
| Script R | Sim | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Não |
| Roamler | Sim | Sim | Não | Sim | Não |
| Objetos do Salesforce | Sim | Sim | Não | Não | Não |
| Relatórios do Salesforce | Sim | Sim | Não | Não | Não |
| SAP Business Warehouse Message Server | Sim | Sim | Sim | Sim | Sim |
| SAP Business Warehouse Server | Sim | Sim | Sim | Sim | Sim |
| SAP HANA | Sim | Sim | Sim | Sim | Sim |
| Pasta do SharePoint | Sim | Sim | Não | Sim | Não <sup>4</sup> |
| Lista do SharePoint | Sim | Sim | Não | Sim | Não <sup>4</sup> |
| Lista do SharePoint Online | Sim | Sim | Não | Sim <sup>2</sup> | Não |
| Smartsheet | Sim | Sim | Não | Não | Não |
| Snowflake | Sim | Sim | Sim | Sim | Não |
| Spark | Sim | Sim | Sim | Sim | Não |
| SparkPost | Sim | Sim | Não | Não | Não |
| SQL Server | Sim | Sim | Sim | Sim | Sim |
| SQL Server Analysis Services | Sim | Sim | Sim | Sim | Sim |
| Stripe | Sim | Sim | Não | Não | Não |
| SurveyMonkey | Sim | Sim | Não | Sim | Não |
| SweetIQ | Sim | Sim | Não | Não | Não |
| Sybase | Sim | Sim | Não | Sim | Sim |
| TeamDesk | Sim | Sim | Não | Sim | Não |
| Tenforce | Sim | Sim | Não | Não | Não |
| Teradata | Sim | Sim | Sim | Sim | Sim |
| Texto/CSV | Sim | Sim | Não | Sim | Não <sup>4</sup> |
| Twilio | Sim | Sim | Não | Não | Não |
| tyGraph | Sim | Sim | Não | Não | Não |
| Vertica | Sim | Sim | Sim | Sim | Sim |
| Web | Sim | Sim | Não | Sim | Sim <sup>6</sup> |
| Webtrends | Sim | Sim | Não | Não | Não |
| Workforce Dimensions | Sim | Sim | Não | Sim | Não |
| XML | Sim | Sim | Não | Sim | Não <sup>4</sup> |
| Zendesk | Sim | Sim | Não | Não | Não |
| | | | | | | | |

<sup>1</sup> Suportado com o [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920), instalado no mesmo computador que o gateway.

<sup>2</sup> Suportado com a mesma função M que na versão no local, o que leva a opções de Autenticação restritas (o gateway não suporta a OAuth).

<sup>3</sup> Os ficheiros de Excel 1997-2003 (.xls) necessitam do [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Necessário para a versão no local da tecnologia.

<sup>5</sup> Suportado apenas com o [gateway pessoal](service-gateway-personal-mode.md).

<sup>6</sup> Necessário para .html, .xls e Bases de Dados do Access

<sup>7</sup> O serviço Power BI não suporta feeds OData que exigem autenticação.

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

> [!Note]
> O Multi-Factor Authentication (MFA) do Microsoft Azure não é suportado. Os utilizadores que quiserem utilizar o SSO com o DirectQuery têm de ser excluídos do MFA.

## <a name="next-steps"></a>Próximos passos

[Ligar a dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)  
[Dados dinâmicos do SQL Server Analysis Services no Power BI](sql-server-analysis-services-tabular-data.md)  
[What is an on-premises data gateway?](service-gateway-onprem.md) (O que é um gateway de dados no local?)  
