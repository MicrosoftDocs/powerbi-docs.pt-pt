---
title: Origens de dados suportadas pelo DirectQuery no Power BI
description: Obtenha uma lista das origens de dados que podem utilizar o DirectQuery.
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3630d876f3e32cbe981d7fb5bcc38d9da1a257f2
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Origens de dados suportadas pelo DirectQuery no Power BI
O **Power BI Desktop** e o **serviço Power BI** têm várias origens de dados às quais pode ligar e obter acesso aos dados. Este artigo descreve as origens de dados do Power BI que suportam o método de ligação conhecido como **DirectQuery**. Para obter mais informações sobre o DirectQuery, veja [**DirectQuery no Power BI**](desktop-directquery-about.md).

As seguintes origens de dados suportam o DirectQuery no Power BI:

* Amazon Redshift
* Azure HDInsight Spark (Beta)
* Base de Dados SQL do Azure
* SQL Data Warehouse do Azure
* Google BigQuery (Beta)
* IBM Netezza (Beta)
* Impala (versão 2.x)
* Base de dados Oracle (versão 12 e posteriores)
* SAP Business Warehouse (Beta)
* SAP HANA
* Snowflake
* Spark (Beta) (versão 0.9 e posteriores)
* SQL Server
* Base de Dados Teradata
* Vertica (Beta)

As origens de dados com **(Beta)** ou **(Pré-visualização)** após o respetivo nome estão sujeitas a alterações e não são suportadas para utilização em produção. Também poderão não ser suportadas depois de publicar um relatório para o **serviço Power BI**, o que significa que abrir um relatório publicado ou explorar o conjunto de dados pode resultar num erro.

A única diferença entre as origens de dados **(Beta)** e **(Pré-visualização)** é que as origens **(Pré-visualização)** têm de ser ativadas como uma funcionalidade de Pré-visualização antes de ficarem disponíveis para utilização. Para ativar um conector de dados **(Pré-visualização)**, no **Power BI Desktop** aceda a **Ficheiro > Opções e Definições** e em **Definições > Opções > Funcionalidades de pré-visualização**.

## <a name="on-premises-gateway-requirements"></a>Requisitos do gateway no local
A seguinte tabela especifica se um **gateway de dados no local** é necessário para ligar à origem de dados especificada, após a publicação de um relatório para o **serviço Power BI**.

| Origem | É necessário um gateway? |
| --- | --- |
| SQL Server |Sim |
| Base de Dados SQL do Azure |Não |
| SQL Data Warehouse do Azure |Não |
| SAP HANA |Sim |
| Base de Dados Oracle |Sim |
| Base de Dados Teradata |Sim |
| Amazon Redshift |Não |
| Impala (versão 2.x) |Sim |
| Snowflake (Pré-visualização) |Ainda não é suportado no **Serviço Power BI** |
| Spark (beta), versão 0.9 e posteriores |Ainda não é suportado no **Serviço Power BI** |
| Azure HDInsight Spark (Beta) |Ainda não é suportado no **Serviço Power BI** |
| IBM Netezza (Beta) |Ainda não é suportado no **Serviço Power BI** |
| SAP Buisness Warehouse (Beta) |Ainda não é suportado no **Serviço Power BI** |

## <a name="next-steps"></a>Passos seguintes
Para obter mais informações sobre o DirectQuery, consulte os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados no local](service-gateway-onprem.md)

