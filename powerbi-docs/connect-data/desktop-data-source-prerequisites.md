---
title: Pré-requisitos de origem de dados do Power BI
description: Pré-requisitos de origem de dados do Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 01/29/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 55e219ff5da73774adaec768b48a0aedd90c1748
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405382"
---
# <a name="power-bi-data-source-prerequisites"></a>Pré-requisitos de origem de dados do Power BI
Para cada fornecedor de dados, o Power BI suporta uma versão específica do fornecedor em objetos. Para obter mais informações sobre as origens de dados disponíveis no Power BI, veja [Origens de dados](desktop-data-sources.md). A tabela seguinte descreve estes requisitos.

| Origem de dados | Fornecedor | Versão mínima do fornecedor | Versão mínima da origem de dados | Objetos de origem dos dados suportados | Ligação para transferência |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (incorporado no .Net Framework) |.NET Framework 3.5 (apenas) |SQL Server 2005+ |Tabelas/Vistas, Funções escalares, Funções de tabela |Incluído no .NET Framework 3.5 ou superior |
| Access |Motor da Base de Dados do Microsoft Access (ACE) |ACE 2010 SP1 |Sem restrição |Tabelas/Vistas |[Ligação para transferência](./desktop-access-database-errors.md) |
| Excel (apenas ficheiros .xls) (ver nota 1) |Motor da Base de Dados do Microsoft Access (ACE) |ACE 2010 SP1 |Sem restrição |Tabelas, Folhas |[Ligação para transferência](./desktop-access-database-errors.md) |
| Oracle (ver nota 2) |ODP.NET |ODAC 11.2 Versão 5 (11.2.0.3.20) |9.x + |Tabelas/Vistas |[Ligação para transferência](./desktop-connect-oracle-database.md) |
| | System.Data.OracleClient (incorporado no .NET Framework) |.NET Framework 3.5 |9.x + |Tabelas/Vistas |Incluído no .NET Framework 3.5 ou superior |
| IBM DB2 |Cliente ADO.Net do IBM (parte do pacote de controlador do servidor de dados do IBM) |10.1 |9.1+ |Tabelas/Vistas |[Ligação para transferência](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Conector/Net |6.6.5 |5.1 |Tabelas/Vistas, Funções escalares |[Ligação para transferência](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |Fornecedor de NPGSQL ADO.NET (Enviado com o Power BI Desktop) |4.0.10 |9.4 |Tabelas/Vistas |[Ligação para transferência](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |Fornecedor de Dados .NET para Teradata |14+ |12+ |Tabelas/Vistas |[Ligação para transferência](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere do .NET 3.5 |16+ |16+ |Tabelas/Vistas |[Ligação para transferência](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Os ficheiros do Excel que tenham uma extensão .xlsx não necessitam de uma instalação de fornecedor independente.

>[!NOTE]
>Os fornecedores de Oracle também requerem o software de cliente Oracle (versão 8.1.7 ou superior).
> 
>