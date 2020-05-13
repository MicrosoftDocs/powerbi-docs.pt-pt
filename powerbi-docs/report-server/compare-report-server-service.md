---
title: Comparar o Power BI Report Server e o serviço Power BI
description: Este artigo compara as funcionalidades do Power BI Report Server e do serviço Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 03/04/2020
ms.openlocfilehash: 18ca1b58d37fedb2c8246b91dc765168002e163e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275944"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparar o Power BI Report Server e o serviço Power BI

O Power BI Report Server e o serviço Power BI têm muitas semelhanças e algumas diferenças importantes. Esta tabela explica cada uma delas.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funcionalidades do Power BI Report Server e do serviço Power BI

| Funcionalidades | Servidor de Relatório do Power BI | Power BI Service (Serviço Power BI) | Notas |
|---------|---------|---------|---------|
| Implementação | Cloud no local ou alojada | Nuvem | O Power BI Report Server poderá ser implementado em VMs do Azure (cloud alojada) se for licenciado através do Power BI Premium ou do SQL Server Enterprise com Software Assurance|
| Dados de origem | Na cloud e/ou no local | Na cloud e/ou no local |  |
| Licença | Power BI Premium ou o SQL Server EE com Software Assurance (SA) | Power BI Pro e/ou Power BI Premium | |  
| Ciclo de vida | Política de ciclo de vida moderna | Serviço totalmente gerido |  |
| Ciclo de lançamento | Três vezes por ano (janeiro, maio, setembro) | Uma vez por mês | As funcionalidades e correções mais recentes estarão disponíveis primeiro no serviço Power BI. Um rollup de funcionalidades do Power BI Desktop para o serviço incluído no Power BI Report Server em cada versão; a maioria das outras funcionalidades destinam-se apenas ao serviço Power BI. |
| Criar relatórios do Power BI no Power BI Desktop | Yes | Yes |  |
| Criar relatórios do Power BI no browser | No | Yes |  |
| Alojar e ligar a conjuntos de dados partilhados do Power BI | No | Yes | [Introdução aos conjuntos de dados em áreas de trabalho](../connect-data/service-datasets-across-workspaces.md) |
| Gateway necessário | No | Sim para origens de dados no local |  |
| Transmissão em fluxo em tempo real | No | Yes | [Transmissão em fluxo em tempo real no Power BI](../connect-data/service-real-time-streaming.md) |
| Painéis | No | Yes | [Dashboards no serviço Power BI](../consumer/end-user-dashboards.md) |
| Distribuir grupo de relatórios através de aplicações | No | Yes | [Criar e publicar aplicações com dashboards e relatórios](../collaborate-share/service-create-distribute-apps.md) |
| Pacotes de conteúdos | No | Yes | [Pacotes de conteúdos organizacionais: introdução](../collaborate-share/service-organizational-content-pack-introduction.md) |
| Ligar a serviços como o Salesforce | Yes | Yes | [Ligue-se aos serviços que utiliza](../connect-data/service-connect-to-services.md) com pacotes de conteúdos no serviço Power BI. No Power BI Report Server, utilize conectores certificados para ligar a serviços. Veja [Origens de dados de relatórios do Power BI no Power BI Report Server](data-sources.md) para obter detalhes. |
| Perguntas e Respostas | No | Yes | [Perguntas e Respostas no serviço Power BI e no Power BI Desktop](../create-reports/power-bi-tutorial-q-and-a.md) 
| Informações rápidas | No | Yes | [Gerar automaticamente as informações de dados com o Power BI](../consumer/end-user-insights.md) |
| Analyze in Excel (Analisar no Excel) | No | Yes | [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md) 
| Relatórios paginados | Yes | Yes | [Os relatórios paginados estão disponíveis no serviço Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md) em pré-visualização numa capacidade Premium |
| Aplicativos móveis do Power BI | Yes | Yes | [Descrição geral das aplicações móveis do Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| Mapas ARC GIS | No | Yes | [Mapas ArcGIS no serviço Power BI e Power BI Desktop pela Esri](../visuals/power-bi-visualization-arcgis.md) |
| Subscrições de e-mail para relatórios do Power BI | No | Yes | [Subscrever um relatório ou dashboard](../collaborate-share/service-report-subscribe.md) para si ou para outras pessoas no serviço Power BI |
| Subscrições de e-mail para relatórios paginados | Yes | Yes | [Subscrever relatórios paginados no serviço Power BI para si e para outras pessoas](../consumer/paginated-reports-subscriptions.md)<br><br>[Email delivery in Reporting Services](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal) (Entrega de e-mail no Reporting Services)  |
| Alertas de dados | No | Yes | [Alertas de dados](../create-reports/service-set-data-alerts.md) no serviço Power BI
| Segurança ao nível da linha (RLS) | Yes | Yes | Disponível no DirectQuery (origem de dados) e no Modo de importação <br><br>Segurança ao nível da linha no [serviço Power BI](../admin/service-admin-rls.md) <br><br>service-report-subscribe [Power BI Report Server](row-level-security-report-server.md) |
| Modo de ecrã inteiro | No | Yes | [Modo de ecrã inteiro](../consumer/end-user-focus.md) no serviço Power BI |
| Colaboração avançada no Office 365 | No | Yes | [Collaborate in a workspace](../collaborate-share/service-collaborate-power-bi-workspace.md) (Colaborar numa área de trabalho) com o Office 365 |
| Visuais R | No | Yes | [Crie visuais R](../create-reports/desktop-r-visuals.md) no Power BI Desktop e publique-os no serviço Power BI. Não pode guardar relatórios do Power BI com visuais R no Power BI Report Server.  |
| Funcionalidades de pré-visualização | No | Yes | [Optar ativamente por participar nas funcionalidades de pré-visualização](../consumer/end-user-preview-features.md) do serviço Power BI |
| Power BI visuals | Yes | Yes | [Elementos visuais do Power BI](../developer/visuals/power-bi-custom-visuals.md) |
| Modelos compostos | No | Yes |
| Power BI Desktop | Versão otimizada para o Report Server, disponível para transferência com o Report Server | Versão otimizada para o Serviço Power BI, disponível na Loja Windows | [Power BI Desktop para o servidor de relatórios](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para o serviço Power BI](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Próximas etapas

[Instalar o Power BI Report Server](install-report-server.md)






