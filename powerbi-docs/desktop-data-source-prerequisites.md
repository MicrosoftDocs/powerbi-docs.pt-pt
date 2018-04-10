---
title: Pré-requisitos de origem de dados do Power BI
description: Pré-requisitos de origem de dados do Power BI
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 282526e18777e623725859adc84475525dcf25ba
ms.sourcegitcommit: ae4d771b883b654358a6a94dd784ea9bdf3d3aa3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="power-bi-data-source-prerequisites"></a>Pré-requisitos de Origem de Dados do Power BI
Para cada fornecedor de dados, o Power BI suporta uma versão específica do fornecedor em objetos. Para obter mais informações sobre as origens de dados disponíveis, consulte [Origens de Dados](desktop-data-sources.md). A tabela seguinte descreve estes requisitos.

| Origem de dados | Fornecedor | Versão mínima do fornecedor | Versão mínima da origem de dados | Objetos de origem dos dados suportados | Ligação para transferência |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (incorporado no .Net Framework) |.NET Framework 3.5 (apenas) |SQL Server 2005+ |Tabelas/Vistas, Funções escalares, Funções de tabela |Incluído no .NET Framework 3.5 ou superior |
| Access |Motor da Base de Dados do Microsoft Access (ACE) |ACE 2010 SP1 |Sem restrição |Tabelas/Vistas |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (apenas ficheiros .xls) (ver nota 1) |Motor da Base de Dados do Microsoft Access (ACE) |ACE 2010 SP1 |Sem restrição |Tabelas, Folhas |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (ver nota 2) |ODP.NET |ODAC 11.2 Versão 5 (11.2.0.3.20) |9.x + |Tabelas/Vistas |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (incorporado no .NET Framework) |.NET Framework 3.5 |9.x + |Tabelas/Vistas |Incluído no .NET Framework 3.5 ou superior |
| IBM DB2 |Cliente ADO.Net do IBM (parte do pacote de controlador do servidor de dados do IBM) |10.1 |9.1+ |Tabelas/Vistas |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Conector/Net |6.6.5 |5.1 |Tabelas/Vistas, Funções escalares |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |Fornecedor de NPGSQL ADO.NET |2.0.12 |7.4 |Tabelas/Vistas |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |Fornecedor de Dados .NET para Teradata |14+ |12+ |Tabelas/Vistas |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere do .NET 3.5 |16+ |16+ |Tabelas/Vistas |[Ligação para transferência](http://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Os ficheiros do Excel que tenham uma extensão .xlsx não necessitam de uma instalação de fornecedor independente.

>[!NOTE]
>Os fornecedores de Oracle também requerem o software de cliente Oracle (versão 8.1.7 ou superior).
> 
> 

