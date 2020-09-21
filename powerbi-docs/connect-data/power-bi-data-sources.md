---
title: Origens de dados do Power BI
description: O presente artigo lista as origens de dados suportadas pelo Power BI, incluindo informações sobre o DirectQuery e o gateway de dados no local.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/11/2020
ms.author: davidi
ms.openlocfilehash: 926569e783dad7a97b91e2e5c1752401d21d6612
ms.sourcegitcommit: 376ea86f69545444f975378cbf63e54c2f75faa3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2020
ms.locfileid: "90084059"
---
# <a name="power-bi-data-sources"></a>Origens de dados do Power BI

A seguinte tabela apresenta as origens de dados suportadas pelo Power BI para os conjuntos de dados, incluindo informações sobre o DirectQuery e o gateway de dados no local. Para obter mais informações acerca dos fluxos de dados, veja [Ligar a origens de dados dos fluxos de dados do Power BI](../transform-model/service-dataflows-data-sources.md).

| Origem de dados | Ligar a partir do Ambiente de Trabalho | Ligar e atualizar a partir do serviço | DirectQuery/Ligação em direto | Gateway (suportado) | Gateway (necessário) |
|---|---|---|---|---|---|---|---|
| Base de dados do Access | Sim | Sim | Não | Sim <sup>1</sup> | Sim |
| ActiveDirectory | Sim | Sim | No | Yes | Sim |
| Adobe Analytics | Sim | Sim | No | Não | Não |
| Amazon Redshift | Sim | Sim | Sim | Sim | Não |
| appFigures | Sim | Sim | No | Não | Não |
| Cubos AtScale | Sim | Sim | Sim | Sim | Não |
| Azure Analysis Services | Sim | Sim | Sim | No | Não |
| Armazenamento de Blobs do Azure | Yes | Sim | No | Yes | Não |
| Azure Cosmos DB | Sim | Sim | No | Não | Não |
| Azure Cost Management | Sim | Sim | No | Não | Não |
| Azure Data Explorer (kusto) | Sim | Sim | Sim | Sim | Não |
| Azure Data Lake Storage Gen1 | Sim | Sim | No | Não | Não |
| Azure Data Lake Storage Gen2 | Sim | Sim | No | Yes | Não |
| Azure DevOps | Sim | Sim | No | Não | Não |
| Azure DevOps Server | Sim | Sim | No | Yes | Sim |
| Azure HDInsight (HDFS) | Sim | Sim | No | Não | Não |
| Azure HDInsight Spark | Sim | Sim | Sim | No | Não |
| Base de Dados SQL do Azure | Yes | Sim | Sim | Sim <sup>2</sup> | Não |
| Azure SQL Data Warehouse | Yes | Sim | Sim | Sim <sup>2</sup> | Não |
| Armazenamento de Tabelas do Azure | Yes | Sim | No | Yes | Não |
| Conector BI | Sim | Sim | Sim | Sim | Sim |
| BI360 - Budgeting & Financial Reporting | Sim | Sim | No | Não | Não |
| Common Data Service | Sim | Sim | No | Não | Não |
| Data.World - Obter Conjunto de Dados | Sim | Sim | No | Não | Não |
| Denodo | Sim | Sim | Sim | Sim | Sim |
| Dremio | Sim | Sim | Sim | Sim | Sim |
| Dynamics 365 (online) | Sim | Sim | No | Não | Não |
| Dynamics 365 Business Central | Sim | Sim | No | Não | Não |
| Dynamics 365 Business Central (no local) | Sim | Sim | No | Não | Não |
| Dynamics 365 Customer Insights | Sim | Sim | No | Não | Não |
| Dynamics NAV | Sim | Sim | No | Não | Não |
| Origem de Dados Emigo | Sim | Sim | No | Não | Não |
| Entersoft Business Suite | Sim | Sim | No | Não | Não |
| Essbase | Sim | Sim | Sim | Sim | Sim |
| Exasol | Sim | Sim | Sim | Sim | Sim |
| Excel | Sim <sup>3</sup> | Sim <sup>3</sup> | Não | Sim <sup>3</sup> | Não <sup>4</sup> |
| Facebook | Sim | Sim | No | Não | Não |
| Ficheiro | Sim | Sim | No | Yes | Sim |
| Pasta | Yes | Sim | No | Yes | Sim |
| GitHub | Sim | Sim | No | Não | Não |
| Google Analytics | Sim | Sim | No | Não | Não |
| Google BigQuery | Sim | Sim | Sim | No | Não |
| Hadoop File (HDFS) | Sim | No | Não | Não | Não |
| Interactive Query do HDInsight | Sim | Sim | Sim | No | Não |
| IBM DB2 | Sim | Sim | Sim | Sim | Não |
| IBM Informix Database | Sim | Sim | No | Yes | Não |
| IBM Netezza | Sim | Sim | Sim | Sim | Sim |
| Impala | Sim | Sim | Sim | Sim | Sim |
| Indexima | Sim | Sim | Sim | Sim | Sim |
| Industrial App Store | Sim | Sim | No | Não | Não |
| Information Grid | Sim | Sim | No | Não | Não |
| InterSystems IRIS | Sim | Sim | Sim | Sim | Sim |
| Intune Data Warehouse | Sim | Sim | No | Não | Não |
| ODBC da Jethro | Sim | Sim | Sim | Sim | Sim |
| JSON | Yes | Sim | Não | Sim** | Não <sup>4</sup> |
| Kyligence Enterprise | Sim | Sim | Sim | Sim | Sim |
| MailChimp | Sim | Sim | No | Não | Não |
| Marketo | Sim | Sim | No | Não | Não |
| ODBC da MarkLogic | Sim | Sim | Sim | Sim | Sim |
| Microsoft Azure Consumption Insights | Sim | Sim | No | Não | Não |
| Microsoft Exchange | Sim | Sim | No | Yes | No |
| Microsoft Exchange Online | Sim | Sim | No | Não | Não |
| Segurança do Microsoft Graph | Sim | Sim | No | Yes | Não |
| Mixpanel | Sim | Sim | No | Não | Não |
| MySQL | Sim | Sim | No | Yes | Sim |
| OData | Sim | Sim <sup>7</sup> | Não | Yes | Não |
| ODBC | Yes | Sim | No | Yes | Sim |
| OleDb | Sim | Sim | No | Yes | Sim |
| Oracle | Sim | Sim | Sim | Sim | Sim |
| Paxata <sup>8</sup> | Sim | Sim | No | Yes | Não |
| PDF | Sim | Sim | No | Sim | Não <sup>4</sup> |
| Planview Enterprise One - CTM | Sim | Sim | No | Não | Não |
| Planview Enterprise One - PRM | Sim | Sim | No | Não | Não |
| Planview Projectplace | Sim | Sim | No | Não | Não |
| PostgreSQL | Sim | Sim | Sim | Sim | Não |
| Fluxos de dados do Power BI | Sim | Sim | No | Não | Não |
| Conjuntos de dados do Power BI | Sim | Sim | Sim | No | Não |
| Power platform dataflows (Fluxos de dados do Power Platform) | Sim | Sim | No | Não | Não |
| Script de Python | Sim | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Sim |
| QubolePresto | Sim | Sim | Sim | Sim | Sim |
| Quick Base | Sim | Sim | No | Yes | Sim |
| QuickBooks Online | Sim | Sim | No | Não | Não |
| Script R | Sim | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Não |
| Roamler | Sim | Sim | No | Yes | No |
| Objetos do Salesforce | Sim | Sim | No | Não | Não |
| Relatórios do Salesforce | Sim | Sim | No | Não | Não |
| SAP Business Warehouse Message Server | Sim | Sim | Sim | Sim | Sim |
| SAP Business Warehouse Server | Sim | Sim | Sim | Sim | Sim |
| SAP HANA | Sim | Sim | Sim | Sim | Sim |
| Pasta do SharePoint | Sim | Sim | No | Sim | Não <sup>4</sup> |
| Lista do SharePoint | Sim | Sim | No | Sim | Não <sup>4</sup> |
| Lista do SharePoint Online | Sim | Sim | Não | Sim <sup>2</sup> | Não |
| Smartsheet | Sim | Sim | No | Não | Não |
| Snowflake | Sim | Sim | Sim | Sim | Não |
| Spark | Sim | Sim | Sim | Sim | Não |
| SparkPost | Sim | Sim | No | Não | Não |
| SQL Server | Sim | Sim | Sim | Sim | Sim |
| SQL Server Analysis Services | Yes | Sim | Sim | Sim | Sim |
| Stripe | Sim | Sim | No | Não | Não |
| SurveyMonkey | Sim | Sim | No | Yes | Não |
| SweetIQ | Sim | Sim | No | Não | Não |
| Sybase | Sim | Sim | No | Yes | Sim |
| TeamDesk | Sim | Sim | No | Yes | Não |
| Tenforce | Sim | Sim | No | Não | Não |
| Teradata | Yes | Sim | Sim | Sim | Sim |
| Texto/CSV | Yes | Sim | No | Sim | Não <sup>4</sup> |
| Twilio | Sim | Sim | No | Não | Não |
| tyGraph | Sim | Sim | No | Não | Não |
| Vertica | Sim | Sim | Sim | Sim | Sim |
| Web | Yes | Sim | No | Sim | Sim <sup>6</sup> |
| Webtrends | Sim | Sim | No | Não | Não |
| Workforce Dimensions | Sim | Sim | No | Yes | Não |
| XML | Yes | Sim | No | Sim | Não <sup>4</sup> |
| Zendesk | Sim | Sim | No | Não | Não |
| | | | | | | | |

<sup>1</sup> Suportado com o [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920), instalado no mesmo computador que o gateway.

<sup>2</sup> Suportado com a mesma função M que na versão no local, o que leva a opções de Autenticação restritas (o gateway não suporta a OAuth).

<sup>3</sup> Os ficheiros de Excel 1997-2003 (.xls) necessitam do [fornecedor ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Necessário para a versão no local da tecnologia.

<sup>5</sup> Suportado apenas com o [gateway pessoal](service-gateway-personal-mode.md).

<sup>6</sup> Necessário para .html, .xls e Bases de Dados do Access

<sup>7</sup> O serviço Power BI não suporta feeds OData que exigem autenticação.

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

> [!Note]
> O Multi-Factor Authentication (MFA) do Microsoft Azure não é suportado. Os utilizadores que quiserem utilizar o SSO com o DirectQuery têm de ser excluídos do MFA.

## <a name="next-steps"></a>Próximos passos

[Ligar a dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)  
[Dados dinâmicos do SQL Server Analysis Services no Power BI](sql-server-analysis-services-tabular-data.md)  
[What is an on-premises data gateway?](service-gateway-onprem.md) (O que é um gateway de dados no local?)  
[Origens de dados de relatórios do Power BI no Power BI Report Server](../report-server/data-sources.md)
