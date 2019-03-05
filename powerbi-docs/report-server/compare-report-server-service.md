---
title: Comparar o Power BI Report Server e o serviço Power BI
description: Este artigo compara as funcionalidades do Power BI Report Server e do serviço Power BI.
keywords: ''
author: markingmyname
ms.author: maghan
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.date: 02/06/2019
ms.openlocfilehash: ba10e13062e4071e5afcc5d395836c96ed1401fd
ms.sourcegitcommit: e9c45d6d983e8cd4cb5af938f838968db35be0ee
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57327924"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparar o Power BI Report Server e o serviço Power BI

O Power BI Report Server e o serviço Power BI têm muitas semelhanças e algumas diferenças importantes. Esta tabela explica cada uma delas.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funcionalidades do Power BI Report Server e do serviço Power BI

| Funcionalidades | Power BI Report Server | Serviço Power BI | Notas |
|---------|---------|---------|---------|
| Implementação | Cloud no local ou alojada | Cloud | O Power BI Report Server pode ser implementado em VMs do Azure (cloud alojada) se for licenciado através do Power BI Premium |
| Dados de origem | Na cloud e/ou no local | Na cloud e/ou no local |  |
| Licença | Power BI Premium ou o SQL Server EE com SA | Power BI Pro e/ou Power BI Premium | |  
| Ciclo de vida | Política de ciclo de vida moderna | Serviço totalmente gerido |  |
| Ciclo de lançamento | A cada 4 meses | Uma vez por mês | As funcionalidades e correções mais recentes estarão disponíveis primeiro no serviço Power BI. A maioria das funcionalidade principais estarão disponíveis no Power BI Report Server nos próximos lançamentos; algumas funcionalidades destinam-se apenas ao serviço Power BI. |
| Criar relatórios do Power BI no Power BI Desktop | Sim | Sim |  |
| Criar relatórios do Power BI no browser | Não | Sim |  |
| Gateway necessário | Não | Sim para origens de dados no local |  |
| Transmissão em fluxo em tempo real | Não | Sim | [Transmissão em fluxo em tempo real no Power BI](../service-real-time-streaming.md) |
| Dashboards | Não | Sim | [Dashboards no serviço Power BI](../consumer/end-user-dashboards.md) |
| Distribuir grupo de relatórios através de aplicações | Não | Sim | [Criar e publicar aplicações com dashboards e relatórios](../service-create-distribute-apps.md) |
| Pacotes de conteúdos | Não | Sim | [Pacotes de conteúdos organizacionais: Introdução](../service-organizational-content-pack-introduction.md) |
| Ligar a serviços como o Salesforce | Sim | Sim | [Ligue-se aos serviços que utiliza](../service-connect-to-services.md) com pacotes de conteúdos no serviço Power BI. No Power BI Report Server, utilize conectores certificados para ligar a serviços. Veja [Origens de dados de relatórios do Power BI no Power BI Report Server](data-sources.md) para obter detalhes. |
| Perguntas e Respostas | Não | Sim | [Perguntas e Respostas no serviço Power BI e no Power BI Desktop](../consumer/end-user-q-and-a.md) 
| Informações rápidas | Não | Sim | [Gerar automaticamente as informações de dados com o Power BI](../consumer/end-user-insights.md) |
| Analisar no Excel | Não | Sim | [Analyze in Excel](../service-analyze-in-excel.md) 
| Relatórios paginados | Sim | Sim | [Os relatórios paginados estão disponíveis no serviço Power BI](../paginated-reports-report-builder-power-bi.md) em pré-visualização numa capacidade Premium |
| Aplicações móveis do Power BI | Sim | Sim | [Descrição geral das aplicações móveis do Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| Mapas ARC GIS | Não | Sim | [Mapas ArcGIS no serviço Power BI e Power BI Desktop pela Esri](../visuals/power-bi-visualization-arcgis.md) |
| Subscrições de e-mail para relatórios do Power BI | Não | Sim | [Subscrever um relatório ou dashboard](../service-report-subscribe.md) para si ou para outras pessoas no serviço Power BI |
| Subscrições de e-mail para relatórios paginados | Sim | Não | [Entrega de e-mail no Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  |
| Alertas de dados | Não | Sim | [Alertas de dados](../service-set-data-alerts.md) no serviço Power BI
| Segurança ao nível da linha (RLS) | Sim | Sim | Disponível no DirectQuery (origem de dados) e no Modo de importação <br>Segurança ao nível da linha no [serviço Power BI](../service-admin-rls.md) <br>service-report-subscribe [Power BI Report Server](row-level-security-report-server.md) |
| Modo de ecrã inteiro | Não | Sim | [Modo de ecrã inteiro](../consumer/end-user-focus.md) no serviço Power BI |
| Colaboração avançada no Office 365 | Não | Sim | [Colaborar na área de trabalho de uma aplicação](../service-collaborate-power-bi-workspace.md) com o Office 365 |
| Visuais R | Não | Sim | [Crie visuais R](../desktop-r-visuals.md) no Power BI Desktop e publique-os no serviço Power BI. Não pode guardar relatórios do Power BI com visuais R no Power BI Report Server.  |
| Funcionalidades de pré-visualização | Não | Sim | [Optar ativamente por participar nas funcionalidades de pré-visualização](../consumer/end-user-preview-features.md) do serviço Power BI |
| Elementos visuais personalizados | Sim | Sim | [Elementos visuais personalizados no Power BI](../power-bi-custom-visuals.md) |
| Power BI Desktop | Versão otimizada para o Report Server, disponível para transferência com o Report Server | Versão otimizada para o Serviço Power BI, disponível na Loja Windows | [Power BI Desktop para o servidor de relatórios](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para o serviço Power BI](http://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Próximos passos

[Instalar o Power BI Report Server](install-report-server.md)  