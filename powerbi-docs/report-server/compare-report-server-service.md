---
title: Comparar o Power BI Report Server e o serviço Power BI
description: Este artigo compara as funcionalidades do Power BI Report Server e do serviço Power BI.
services: powerbi
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.component: powerbi-report-server
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
manager: kfile
ms.custom: mvc
ms.openlocfilehash: d0a3e2870edc8b18cb982c33582c7578aa67f2c3
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33813904"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparar o Power BI Report Server e o serviço Power BI

O Power BI Report Server e o serviço Power BI tem bastantes semelhanças e algumas diferenças fundamentais. Esta tabela explica cada uma delas.

| Funcionalidades | Power BI Report Server | Power BI Service (Serviço Power BI) | Notas
|---------|---------|---------|---------|
| Implementação | Cloud no local ou alojada | Cloud | O Power BI Report Server pode ser implementado em VMs do Azure (cloud alojada) se for licenciado através do Power BI Premium
| Dados de origem | Na cloud e/ou no local | Na cloud e/ou no local |  
| Licença | Power BI Premium ou o SQL Server EE com SA | Power BI Pro e/ou Power BI Premium |  
| Ciclo de vida | Política de ciclo de vida moderna | Serviço totalmente gerido |  
| Ciclo de lançamento | A cada 4 meses | Uma vez por mês | As funcionalidades e correções mais recentes estarão disponíveis primeiro no serviço Power BI. A maioria das funcionalidade principais estarão disponíveis no Power BI Report Server nos próximos lançamentos; algumas funcionalidades destinam-se apenas ao serviço Power BI.
| Criar relatórios do Power BI no Power BI Desktop | Sim | Sim |  
| Criar relatórios do Power BI no browser | Não | Sim |  
| Gateway necessário | Não | Sim para origens de dados no local |  
| Transmissão em fluxo em tempo real | Não | Sim | [Transmissão em fluxo em tempo real no Power BI](../service-real-time-streaming.md)
| Dashboards | Não | Sim | [Dashboards no serviço Power BI](../service-dashboards.md) 
| Distribuir grupo de relatórios através de aplicações | Não | Sim | [Criar e publicar aplicações com dashboards e relatórios](../service-create-distribute-apps.md) 
| Pacotes de conteúdos | Não | Sim | [Pacotes de conteúdos organizacionais: introdução](../service-organizational-content-pack-introduction.md) 
| Ligar a serviços como o Salesforce | Não | Sim | [Ligar aos serviços que utiliza](../service-connect-to-services.md) com o serviço Power BI
| Perguntas e Respostas | Não | Sim | [Perguntas e Respostas no serviço Power BI e no Power BI Desktop](../power-bi-q-and-a.md) 
| Informações rápidas | Não | Sim | [Gerar automaticamente as informações de dados com o Power BI](../service-insights.md) 
| Analisar no Excel | Não | Sim | [Analyze in Excel](../service-analyze-in-excel.md) 
| Relatórios paginados | Sim | Não | Os relatórios paginados não estão disponíveis no serviço Power BI, mas pode [afixar itens de relatórios paginados a dashboards do Power BI](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)
| Aplicações móveis do Power BI | Sim | Sim | [Descrição geral das aplicações móveis do Power BI](../mobile-apps-for-mobile-devices.md) 
| Mapas ARC GIS | Não | Sim | [Mapas ArcGIS no serviço Power BI e Power BI Desktop pela Esri](../power-bi-visualization-arcgis.md)
| Subscrições de e-mail para relatórios do Power BI | Não | Sim | [Subscrever um relatório ou dashboard](../service-report-subscribe.md) no serviço Power BI 
| Subscrições de e-mail para relatórios paginados | Sim | Não | [Entrega de e-mail no Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| Alertas de dados | Não | Sim | [Alertas de dados](../service-set-data-alerts.md) no serviço Power BI
| Segurança ao nível da linha | Apenas através da origem de dados no modo DirectQuery | Disponível no DirectQuery (origem de dados) e no Modo de importação | [Segurança ao nível da linha (RLS)](../service-admin-rls.md) com o Power BI 
| Modo de ecrã inteiro | Não | Sim | [Modo de ecrã inteiro](../service-fullscreen-mode.md) no serviço Power BI 
| Colaboração avançada no Office 365 | Não | Sim | [Colaborar na área de trabalho de uma aplicação](../service-collaborate-power-bi-workspace.md) com o Office 365 
| Visuais R | Não | Sim | [Criar elementos visuais R](../service-r-visuals.md) no serviço Power BI  
| Funcionalidades de pré-visualização | Não | Sim | [Optar ativamente por participar nas funcionalidades de pré-visualização](../service-preview-features.md) do serviço Power BI 
| Elementos visuais personalizados | Sim | Sim | [Elementos visuais personalizados no Power BI](../power-bi-custom-visuals.md) 
| Power BI Desktop | Versão otimizada para o Report Server, disponível para transferência com o Report Server | Versão otimizada para o Serviço Power BI, disponível na Loja Windows | [Power BI Desktop para o servidor de relatórios](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para o serviço Power BI](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>Próximos passos
[Instalar o Power BI Report Server](install-report-server.md)  


