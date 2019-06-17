---
title: Origens de dados suportadas pelo DirectQuery no Power BI
description: Obtenha uma lista das origens de dados que podem utilizar o DirectQuery.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/31/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: a06a37e89f7984ab227d54ee5b06550a6ae3e4d6
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448282"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Origens de dados suportadas pelo DirectQuery no Power BI

O **Power BI Desktop** e o **serviço Power BI** têm várias origens de dados às quais pode ligar e obter acesso aos dados. Este artigo descreve as origens de dados do Power BI que suportam o método de ligação conhecido como **DirectQuery**. Para obter mais informações sobre o DirectQuery, veja [**DirectQuery no Power BI**](desktop-directquery-about.md).

As seguintes origens de dados suportam o DirectQuery no Power BI:

* Amazon Redshift
* AtScale (Beta)
* Azure HDInsight Spark
* [Base de Dados SQL do Azure](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Google BigQuery
* Interactive Query do HDInsight
* Base de dados DB2 da IBM
* IBM Netezza
* Impala (versão 2.x)
* Base de dados Oracle (versão 12 e posteriores)
* Oracle Essbase
* SAP Business Warehouse Application Server
* SAP Business Warehouse Message Server
* SAP HANA
* Snowflake
* Spark (versão 0.9 e posteriores)
* SQL Server
* Base de Dados Teradata
* Vertica

As origens de dados com **(Beta)** ou **(Pré-visualização)** após o respetivo nome estão sujeitas a alterações e não são suportadas para utilização em produção. Também poderão não ser suportadas depois de publicar um relatório para o **serviço Power BI**, o que significa que abrir um relatório publicado ou explorar o conjunto de dados pode resultar num erro.

A única diferença entre as origens de dados **(Beta)** e **(Pré-visualização)** é que as origens **(Pré-visualização)** têm de ser ativadas como uma funcionalidade de Pré-visualização antes de ficarem disponíveis para utilização. Para ativar um conector de dados **(Pré-visualização)** , no **Power BI Desktop** aceda a **Ficheiro > Opções e Definições > Opções** e, em seguida, selecione **Funcionalidades de pré-visualização**.

> [!NOTE]
> As consultas de DirectQuery para o SQL Server exigem autenticação com credenciais atuais do Windows ou credenciais de bases de dados para estabelecer acesso. Não são suportadas credenciais alternativas.
>

## <a name="on-premises-gateway-requirements"></a>Requisitos do gateway no local
A seguinte tabela especifica se um **Gateway de dados no local** é necessário para ligar à origem de dados especificada, após a publicação de um relatório para o **serviço Power BI**.

| Origem | É necessário um gateway? |
| --- | --- |
| Amazon Redshift |Não |
| Azure HDInsight Spark (Beta) |Não |
| Base de Dados SQL do Azure |Não |
| SQL Data Warehouse do Azure |Não |
| Google BigQuery |Não |
| IBM Netezza |Sim |
| Impala (versão 2.x) |Sim |
| Base de Dados Oracle |Sim |
| SAP Business Warehouse Application Server |Sim |
| SAP Business Warehouse Message Server |Ainda não é suportado no **Serviço Power BI** |
| SAP HANA |Sim |
| Snowflake |Sim |
| Spark (beta), versão 0.9 e posteriores |Sim |
| SQL Server |Sim |
| Base de Dados Teradata |Sim |

## <a name="single-sign-on-sso-for-directquery-sources"></a>Início de sessão único (SSO) para origens de dados do DirectQuery

Quando a opção SSO está ativada e os utilizadores acedem aos relatórios compilados por cima da origem de dados, o Power BI envia as suas credenciais autenticadas do Azure AD nas consultas para a origem de dados subjacente. Esta operação permite que o Power BI respeite as definições de segurança que estão configuradas ao nível da origem de dados.

A opção SSO tem efeito em todos os conjuntos de dados que utilizam esta origem de dados. Não afeta o método de autenticação utilizado para os cenários de importação. As seguintes origens de dados suportam SSO para ligações através do DirectQuery:

- Base de Dados SQL do Azure
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> O Multi-Factor Authentication (MFA) do Microsoft Azure não é suportado. Os utilizadores que quiserem utilizar o SSO com o DirectQuery têm de ser excluídos do MFA.

## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre o DirectQuery, consulte os seguintes recursos:

* [DirectQuery no Power BI](desktop-directquery-about.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway de dados no local](service-gateway-onprem.md)

