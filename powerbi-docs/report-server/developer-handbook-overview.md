---
title: "Descrição geral do manual de programador, Power BI Report Server"
description: "Bem-vindo ao manual de programador para o Power BI Report Server, uma localização no local para armazenar e gerir os relatórios móveis e paginados do Power BI."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 93cc5b5566816b1b9ce8295cf7c0b727b07571df
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="developer-handbook-overview-power-bi-report-server"></a>Descrição geral do manual de programador, Power BI Report Server
Bem-vindo ao manual de programador para o Power BI Report Server, uma localização no local para armazenar e gerir os relatórios móveis e paginados do Power BI.

![](media/developer-handbook-overview/admin-handbook.png)

Este manual irá realçar as opções disponíveis, como programador, para trabalhar no Power BI Report Server.

## <a name="embedding"></a>Incorporação
Para qualquer relatório do Power BI Report Server, pode incorporar numa iFrame, ao adicionar o parâmetro de cadeia de consulta `?rs:Embed=true` ao URL. Isto funciona com relatórios do Power BI, bem como outros tipos de relatório.

### <a name="report-viewer-control"></a>Controlo do Visualizador de Relatórios
Para obter relatórios paginados, pode tirar partido do Controlo do Visualizador de Relatórios. Isto permite-lhe colocar o controlo dentro do Windows .NET ou aplicação Web. Para obter mais informações, veja [Introdução ao Controlo do Visualizador de Relatórios](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

## <a name="apis"></a>APIs
Existem várias opções de API para interagir com o Power BI Report Server. Isto inclui o seguinte.

* [APIs REST](rest-api.md)
* [Acesso por URL](https://docs.microsoft.com/sql/reporting-services/url-access-ssrs)
* [Fornecedor de WMI](https://docs.microsoft.com/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Também pode utilizar a open source [Utilitários do PowerShell](https://github.com/Microsoft/ReportingServicesTools) para gerir o servidor de relatórios.

> [!NOTE]
> Os utilitários do PowerShell não suportam atualmente ficheiros do Power BI Desktop (.pbix).
> 
> 

## <a name="custom-extensions"></a>Extensões personalizadas
A biblioteca de extensões é um conjunto de classes, interfaces e tipos de valores que estão incluídos no Power BI Report Server. Esta biblioteca fornece acesso à funcionalidade do sistema e foi concebida para ser a base na qual as aplicações Microsoft .NET Framework podem ser utilizadas para expandir os componentes do Power BI Report Server.

Pode criar vários tipos de extensões.

* Extensões de processamento de dados
* Extensão de entrega
* Extensões de composição para relatórios paginados
* Extensões de segurança

Para obter mais informações, veja [Biblioteca de extensões](https://docs.microsoft.com/sql/reporting-services/extensions/reporting-services-extension-library).

## <a name="next-steps"></a>Passos seguintes
[Introdução ao Controlo do Visualizador de Relatórios](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)  
[Criar Aplicações com o Serviço Web e o .NET Framework](https://docs.microsoft.com/sql/reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework)  
[Acesso por URL](https://docs.microsoft.com/sql/reporting-services/url-access-ssrs)  
[Biblioteca de extensões](https://docs.microsoft.com/sql/reporting-services/extensions/reporting-services-extension-library)  
[Fornecedor de WMI](https://docs.microsoft.com/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

