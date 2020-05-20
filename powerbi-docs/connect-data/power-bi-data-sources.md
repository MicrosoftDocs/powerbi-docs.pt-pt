---
title: Origens de dados do Power BI
description: O presente artigo lista as origens de dados suportadas pelo Power BI, incluindo informações sobre o DirectQuery e o gateway de dados no local.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/10/2020
ms.author: kfollis
ms.openlocfilehash: 2aa12ec3d55e491535d12107fc70709f9d41c3f0
ms.sourcegitcommit: 6ba7cc9afaf91229f717374bc0c12f0b8201d15e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2020
ms.locfileid: "83438091"
---
# <a name="power-bi-data-sources"></a>Origens de dados do Power BI

A seguinte tabela apresenta as origens de dados suportadas pelo Power BI para os conjuntos de dados, incluindo informações sobre o DirectQuery e o gateway de dados no local. Para obter mais informações acerca dos fluxos de dados, veja [Ligar a origens de dados dos fluxos de dados do Power BI](../transform-model/service-dataflows-data-sources.md).

> [!NOTE]
> Existem muitos conectores de dados para o Power BI Desktop que requerem o Internet Explorer 10 (ou mais recente) para autenticação. 


| Origem de dados | Ligar a partir do Ambiente de Trabalho | Ligar e atualizar a partir do serviço | DirectQuery/Ligação em direto | Gateway (suportado) | Gateway (necessário) |
|---|---|---|---|---|---|---|---|
| Base de dados do Access | Yes | Yes | No | Sim <sup>1</sup> | Yes |
| ActiveDirectory | Yes | Yes | No | Yes | Yes |
| Adobe Analytics | Yes | Yes | No | No | No |
| Amazon Redshift | Yes | Yes | Yes | Yes | No |
| appFigures | Yes | Yes | No | No | No |
| Cubos AtScale | Yes | Yes | Yes | Yes | No |
| Azure Analysis Services | Yes | Yes | Yes | Sim <sup>2</sup> | No |
| Armazenamento de Blobs do Azure | Yes | Yes | No | Yes | No |
| Azure Cosmos DB | Yes | Yes | No | No | No |
| Azure Cost Management | Yes | Yes | No | No | No |
| Azure Data Explorer (kusto) | Yes | Yes | Yes | No | No |
| Azure Data Lake Storage Gen1 | Yes | Yes | No | No | No |
| Azure Data Lake Storage Gen2 | Yes | Yes | No | Yes | No |
| Azure DevOps | Yes | Yes | No | No | No |
| Azure DevOps Server | Yes | Yes | No | Yes | Yes |
| Azure HDInsight (HDFS) | Yes | Yes | No | No | No |
| Azure HDInsight Spark | Yes | Yes | Yes | No | No |
| Base de dados SQL do Azure | Yes | Yes | Yes | Sim <sup>2</sup> | No |
| Azure SQL Data Warehouse | Yes | Yes | Yes | Sim <sup>2</sup> | No |
| Armazenamento de Tabelas do Azure | Yes | Yes | No | Yes | No |
| Conector BI | Yes | Yes | Yes | Yes | Yes |
| BI360 - Budgeting & Financial Reporting | Yes | Yes | No | No | No |
| Common Data Service | Yes | Yes | No | No | No |
| Data.World - Obter Conjunto de Dados | Yes | Yes | No | No | No |
| Denodo | Yes | Yes | Yes | Yes | Yes |
| Dremio | Yes | Yes | Yes | Yes | Yes |
| Dynamics 365 (online) | Yes | Yes | No | No | No |
| Dynamics 365 Business Central | Yes | Yes | No | No | No |
| Dynamics 365 Business Central (no local) | Yes | Yes | No | No | No |
| Dynamics 365 Customer Insights | Yes | Yes | No | No | No |
| Dynamics NAV | Yes | Yes | No | No | No |
| Origem de Dados Emigo | Yes | Yes | No | No | No |
| Entersoft Business Suite | Yes | Yes | No | No | No |
| Essbase | Yes | Yes | Yes | Yes | Yes |
| Exasol | Yes | Yes | Yes | Yes | Yes |
| Excel | Sim <sup>3</sup> | Sim <sup>3</sup> | No | Sim <sup>3</sup> | Não <sup>4</sup> |
| Facebook | Yes | Yes | No | No | No |
| File | Yes | Yes | No | Yes | Yes |
| Pasta | Yes | Yes | No | Yes | Yes |
| GitHub | Yes | Yes | No | No | No |
| Google Analytics | Yes | Yes | No | No | No |
| Google BigQuery | Yes | Yes | Sim | No | No |
| HDFS (Ficheiro do Hadoop) | Yes | No | No | No | No |
| Interactive Query do HDInsight | Yes | Yes | Yes | No | No |
| IBM DB2 | Yes | Yes | Yes | Yes | No |
| IBM Informix Database | Yes | Yes | No | Yes | No |
| IBM Netezza | Yes | Yes | Yes | Yes | Yes |
| Impala | Yes | Yes | Yes | Yes | Yes |
| Indexima | Yes | Yes | Yes | Yes | Yes |
| Industrial App Store | Yes | Yes | No | No | No |
| Information Grid | Yes | Yes | No | No | No |
| InterSystems IRIS | Yes | Yes | Yes | Yes | Yes |
| Intune Data Warehouse | Yes | Yes | No | No | No |
| ODBC da Jethro | Yes | Yes | Yes | Yes | Yes |
| JSON | Yes | Yes | No | Sim** | Não <sup>4</sup> |
| Kyligence Enterprise | Yes | Yes | Yes | Yes | Yes |
| MailChimp | Yes | Yes | No | No | No |
| Marketo | Yes | Yes | No | No | No |
| ODBC da MarkLogic | Yes | Yes | Yes | Yes | Yes |
| Microsoft Azure Consumption Insights (Informações sobre Consumo do Microsoft Azure) | Yes | Yes | No | No | No |
| Microsoft Exchange | Yes | Yes | No | Yes | No |
| Microsoft Exchange Online | Yes | Yes | No | No | No |
| Segurança do Microsoft Graph | Yes | Yes | No | Yes | No |
| Mixpanel | Yes | Yes | No | No | No |
| MySQL | Yes | Yes | No | Yes | Yes |
| OData | Yes | Yes | No | Yes | No |
| ODBC | Yes | Yes | No | Yes | Yes |
| OleDb | Yes | Yes | No | Yes | Yes |
| Oracle | Yes | Yes | Yes | Yes | Yes |
| Paxata | Yes | Yes | No | Yes | No |
| PDF | Yes | Yes | No | Yes | Não <sup>4</sup> |
| Planview Enterprise One - CTM | Yes | Yes | No | No | No |
| Planview Enterprise One - PRM | Yes | Yes | No | No | No |
| Planview Projectplace | Yes | Yes | No | No | No |
| PostgreSQL | Yes | Yes | Yes | Yes | No |
| Fluxos de dados do Power BI | Yes | Yes | No | No | No |
| Conjuntos de dados do Power BI | Yes | Yes | Yes | No | No |
| Power platform dataflows (Fluxos de dados do Power Platform) | Yes | Yes | No | No | No |
| Script de Python | Yes | Sim <sup>5</sup> | No | Sim <sup>5</sup> | Yes |
| QubolePresto | Yes | Yes | Yes | Yes | Yes |
| Quick Base | Yes | Yes | No | Yes | Yes |
| QuickBooks Online | Yes | Yes | No | No | No |
| Script do R | Yes | Sim <sup>5</sup> | No | Sim <sup>5</sup> | No |
| Roamler | Yes | Yes | No | Yes | No |
| Objetos do Salesforce | Yes | Yes | No | No | No |
| Relatórios do Salesforce | Yes | Yes | No | No | No |
| SAP Business Warehouse Message Server | Yes | Yes | Yes | Yes | Yes |
| SAP Business Warehouse Server | Yes | Yes | Yes | Yes | Yes |
| SAP HANA | Yes | Yes | Yes | Yes | Yes |
| Pasta do SharePoint | Yes | Yes | No | Yes | Não <sup>4</sup> |
| Lista do SharePoint | Yes | Yes | No | Yes | Não <sup>4</sup> |
| Lista do SharePoint Online | Yes | Yes | No | Sim <sup>2</sup> | No |
| Smartsheet | Yes | Yes | No | No | No |
| Snowflake | Yes | Yes | Yes | Yes | No |
| Spark | Yes | Yes | Yes | Yes | No |
| SparkPost | Yes | Yes | No | No | No |
| SQL Server | Yes | Yes | Yes | Yes | Yes |
| SQL Server Analysis Services | Yes | Yes | Yes | Yes | Yes |
| Stripe | Yes | Yes | No | No | No |
| SurveyMonkey | Yes | Yes | No | Yes | No |
| SweetIQ | Yes | Yes | No | No | No |
| Sybase | Yes | Yes | No | Yes | Yes |
| TeamDesk | Yes | Yes | No | Yes | No |
| Tenforce | Yes | Yes | No | No | No |
| Teradata | Yes | Yes | Yes | Yes | Yes |
| Texto/CSV | Yes | Yes | No | Yes | Não <sup>4</sup> |
| Twilio | Yes | Yes | No | No | No |
| tyGraph | Yes | Yes | No | No | No |
| Vertica | Yes | Yes | Yes | Yes | Yes |
| Vista Web | Yes | Yes | No | Yes | Sim <sup>6</sup> |
| Webtrends | Yes | Yes | No | No | No |
| Workforce Dimensions | Yes | Yes | No | Yes | No |
| XML | Yes | Yes | No | Yes | Não <sup>4</sup> |
| Zendesk | Yes | Yes | No | No | No |
| | | | | | | | |

<sup>1</sup> Suportado com o [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920), instalado no mesmo computador que o gateway.

<sup>2</sup> Suportado com a mesma função M que na versão no local, o que leva a opções de Autenticação restritas (o gateway não suporta a OAuth).

<sup>3</sup> Os ficheiros de Excel 1997-2003 (.xls) necessitam do [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Necessário para a versão no local da tecnologia.

<sup>5</sup> Suportado apenas com o [gateway pessoal](service-gateway-personal-mode.md).

<sup>6</sup> Necessário para .html, .xls e Bases de Dados do Access

## <a name="single-sign-on-sso-for-directquery-sources"></a>Início de sessão único (SSO) para origens de dados do DirectQuery

Quando a opção SSO está ativada e os utilizadores acedem aos relatórios compilados por cima da origem de dados, o Power BI envia as suas credenciais autenticadas do Azure AD nas consultas para a origem de dados subjacente. Esta operação permite que o Power BI respeite as definições de segurança que estão configuradas ao nível da origem de dados.
A opção SSO tem efeito em todos os conjuntos de dados que utilizam esta origem de dados. Não afeta o método de autenticação utilizado para os cenários de importação. As seguintes origens de dados suportam SSO para ligações através do DirectQuery:

- Base de dados SQL do Azure
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

## <a name="next-steps"></a>Próximas etapas

[Ligar a dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)  
[Dados dinâmicos do SQL Server Analysis Services no Power BI](sql-server-analysis-services-tabular-data.md)  
[What is an on-premises data gateway?](service-gateway-onprem.md) (O que é um gateway de dados no local?)  
