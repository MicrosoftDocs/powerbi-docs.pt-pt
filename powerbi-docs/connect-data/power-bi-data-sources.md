---
title: Origens de dados do Power BI
description: O presente artigo lista as origens de dados suportadas pelo Power BI, incluindo informações sobre o DirectQuery e o gateway de dados no local.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 11/17/2020
ms.openlocfilehash: 18b7e55d409dc6562fab7cf1f36b83e7edac994b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392870"
---
# <a name="power-bi-data-sources"></a>Origens de dados do Power BI

A seguinte tabela apresenta as origens de dados suportadas pelo Power BI para os conjuntos de dados, incluindo informações sobre o DirectQuery e o gateway de dados no local. Para obter mais informações acerca dos fluxos de dados, veja [Ligar a origens de dados dos fluxos de dados do Power BI](../transform-model/dataflows/dataflows-configure-consume.md).

| Origem de dados | Ligar a partir do Ambiente de Trabalho | Ligar e atualizar a partir do serviço | DirectQuery/Ligação em direto | Gateway (suportado) | Gateway (necessário) | Fluxos de Dados do Power BI |
|---|---|---|---|---|---|---|---|
| Base de dados do Access | Sim | Sim | Não | Sim <sup>1</sup> | Sim | Sim |
| ActiveDirectory | Sim | Yes | Não | Sim | Sim | Sim |
| Adobe Analytics | Sim | Sim | Não | Não | Não | Não |
| Amazon Redshift | Sim | Sim | Sim | Sim | No | Sim |
| appFigures | Sim | Sim | Não | Não | Não | Não |
| Cubos AtScale | Sim | Sim | Sim | Sim | Não | Não |
| Azure Analysis Services | Sim | Sim | Yes | Não | Não | Não |
| Armazenamento de Blobs do Azure | Sim | Sim | Não | Sim | Não | Sim |
| Azure Cosmos DB | Sim | Sim | Não | Não | Não | Não |
| Azure Cost Management | Sim | Sim | Não | Não | No | Não |
| Azure Data Explorer (kusto) | Sim | Sim | Sim | Sim | Não | Sim |
| Azure Data Lake Storage Gen1 | Sim | Sim | No | Não | Não | Não |
| Azure Data Lake Storage Gen2 | Sim | Sim | Não | Sim | Não | Sim |
| Azure DevOps | Sim | Sim | Não | Não | Não | Não |
| Azure DevOps Server | Sim | Sim | Não | Yes | Sim | Não |
| Azure HDInsight (HDFS) | Sim | Sim | Não | Não | Não | Não |
| Azure HDInsight Spark | Sim | Yes | Sim | No | Não | Sim |
| Base de Dados SQL do Azure | Sim | Sim | Sim | Sim | Não | Sim |
| Azure SQL Data Warehouse | Sim | Sim | Sim | Sim | Não | Sim |
| Armazenamento de Tabelas do Azure | Sim | Sim | Não | Sim | Não | Sim |
| Conector BI | Sim | Sim | Sim | Sim | Sim | Não |
| BI360 - Budgeting & Financial Reporting | Sim | Sim | Não | Não | Não | Não |
| Common Data Service | Sim | Sim | Não | No | Não | Sim |
| Data.World - Obter Conjunto de Dados | Sim | Sim | No | Não | Não | Não |
| Denodo | Sim | Sim | Sim | Sim | Sim | Não |
| Dremio | Sim | Sim | Sim | Sim | Sim | Não |
| Dynamics 365 (online) | Sim | Sim | Não | Não | Não | No |
| Dynamics 365 Business Central | Sim | Sim | Não | Não | No | Não |
| Dynamics 365 Business Central (no local) | Sim | Sim | Não | Não | Não | Não |
| Dynamics 365 Customer Insights | Sim | Sim | Não | Não | Não | Não |
| Dynamics NAV | Sim | Sim | Não | Não | Não | Não |
| Origem de Dados Emigo | Sim | Sim | Não | Não | Não | Não |
| Entersoft Business Suite | Yes | Sim | Não | Não | Não | No |
| Essbase | Sim | Sim | Sim | Sim | Sim | Não |
| Exasol | Sim | Sim | Sim | Sim | Sim | Não |
| Excel | Sim <sup>3</sup> | Sim <sup>3</sup> | Não | Sim <sup>3</sup> | Não <sup>4</sup> | Sim |
| Facebook | Sim | Sim | Não | Não | Não | Não |
| Ficheiro | Sim | Sim | Não | Sim | Sim | Sim |
| Pasta | Sim | Sim | Não | Sim | Sim | Sim |
| GitHub | Sim | Sim | Não | Não | Não | Não |
| Google Analytics | Sim | Sim | Não | Não | Não | Não |
| Google BigQuery | Sim | Sim | Sim | Yes | Não | Sim |
| Hadoop File (HDFS) | Sim | No | Não | Não | Não | Não |
| LLAP do Hive | Sim | Sim | Sim | Yes | Não | Não |
| Interactive Query do HDInsight | Sim | Sim | Sim | No | Não | Não |
| IBM DB2 | Sim | Sim | Yes | Sim | Não | Sim |
| IBM Informix Database | Sim | Yes | No | Sim | No | Não |
| IBM Netezza | Sim | Sim | Sim | Sim | Sim | Não |
| Impala | Sim | Sim | Sim | Sim | Sim | Sim |
| Indexima | Sim | Sim | Yes | Yes | Yes | Não |
| Industrial App Store | Sim | Sim | Não | Não | Não | No |
| Information Grid | Sim | Sim | No | No | No | Não |
| InterSystems IRIS | Sim | Sim | Yes | Yes | Yes | Não |
| Intune Data Warehouse | Sim | Sim | No | No | No | Não |
| ODBC da Jethro | Sim | Sim | Yes | Yes | Yes | No |
| JSON | Sim | Yes | Não | Sim** | Não <sup>4</sup> | Sim |
| Kyligence Enterprise | Yes | Sim | Yes | Yes | Yes | No |
| MailChimp | Sim | Sim | Não | Não | No | Não |
| Marketo | Sim | Sim | No | No | No | Não |
| ODBC da MarkLogic | Sim | Sim | Yes | Yes | Yes | Não |
| Microsoft Azure Consumption Insights | Sim | Sim | Não | No | Não | Não |
| Microsoft Exchange | Sim | Sim | Não | Yes | Não | No |
| Microsoft Exchange Online | Sim | Sim | Não | No | Não | Sim |
| Segurança do Microsoft Graph | Sim | Sim | Não | Yes | Não | Não |
| Mixpanel | Sim | Sim | Não | No | No | Não |
| MySQL | Sim | Yes | Não | Sim | Yes | Sim |
| OData | Sim | Sim <sup>7</sup> | Não | Sim | No | Sim |
| ODBC | Sim | Sim | Não | Sim | Sim | Sim |
| OleDb | Sim | Sim | No | Sim | Sim | Não |
| Oracle | Sim | Sim | Yes | Sim | Yes | Sim |
| Paxata <sup>8</sup> | Sim | Sim | Não | Sim | No | Não |
| PDF | Sim | Sim | No | Sim | Não <sup>4</sup> | Sim |
| Planview Enterprise One - CTM | Sim | Sim | Não | Não | Não | Não |
| Planview Enterprise One - PRM | Sim | Sim | Não | Não | Não | Não |
| Planview Projectplace | Sim | Sim | No | No | Não | Não |
| PostgreSQL | Sim | Sim | Yes | Yes | Não | Sim |
| Fluxos de dados do Power BI | Sim | Sim | No | No | Não | Sim |
| Conjuntos de dados do Power BI | Sim | Sim | Yes | Não | Não | Não |
| Power platform dataflows (Fluxos de dados do Power Platform) | Sim | Yes | Não | No | No | Sim |
| Script de Python | Sim | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Sim | Não |
| QubolePresto | Sim | Sim | Yes | Sim | Sim | Não |
| Quick Base | Sim | Sim | Não | Yes | Yes | Não |
| QuickBooks Online | Sim | Yes | Não | No | Não | Não |
| Script R | Yes | Sim <sup>5</sup> | Não | Sim <sup>5</sup> | Não | Não |
| Roamler | Sim | Sim | Não | Yes | Não | No |
| Objetos do Salesforce | Sim | Yes | Não | Não | Não | Sim |
| Relatórios do Salesforce | Sim | Sim | No | No | No | Sim |
| SAP Business Warehouse Message Server | Sim | Sim | Sim | Sim | Sim | Yes |
| SAP Business Warehouse Server | Sim | Sim | Sim | Sim | Sim | Sim |
| SAP HANA | Yes | Sim | Yes | Sim | Yes | Sim |
| Pasta do SharePoint | Sim | Sim | Não | Sim | Não <sup>4</sup> | Sim |
| Lista do SharePoint | Sim | Sim | Não | Sim | Não <sup>4</sup> | Sim |
| Lista do SharePoint Online | Sim | Sim | Não | Yes | Não | Sim |
| Smartsheet | Sim | Sim | No | No | No | Sim |
| Snowflake | Sim | Sim | Sim | Sim | Não | Sim |
| Spark | Sim | Sim | Yes | Yes | Não | Sim |
| SparkPost | Sim | Sim | No | No | No | Não |
| SQL Server | Sim | Sim | Sim | Sim | Sim | Yes |
| SQL Server Analysis Services | Sim | Sim | Yes | Yes | Yes | Não |
| Stripe | Sim | Sim | Não | No | Não | Não |
| SurveyMonkey | Sim | Sim | Não | Yes | Não | Não |
| SweetIQ | Sim | Sim | Não | No | No | Não |
| Sybase | Sim | Sim | Não | Sim | Yes | Sim |
| TeamDesk | Sim | Sim | Não | Yes | Não | Não |
| Tenforce | Sim | Sim | No | No | No | Não |
| Teradata | Sim | Sim | Yes | Sim | Yes | Sim |
| Texto/CSV | Sim | Sim | Não | Sim | Não <sup>4</sup> | Sim |
| Twilio | Sim | Sim | Não | Não | Não | Não |
| tyGraph | Sim | Sim | No | No | No | Não |
| Vertica | Sim | Sim | Yes | Sim | Yes | Sim |
| Web | Sim | Sim | Não | Sim | Sim <sup>6</sup> | Sim |
| Webtrends | Sim | Sim | Não | No | Não | Não |
| Workforce Dimensions | Sim | Sim | Não | Sim | No | Não |
| XML | Sim | Sim | Não | Sim | Não <sup>4</sup> | Sim |
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
