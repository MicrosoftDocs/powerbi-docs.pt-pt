---
title: Comparar o Power BI Report Server e o serviço Power BI
description: Este artigo compara as funcionalidades do Power BI Report Server e do serviço Power BI.
author: maggiesMSFT
ms.author: maggies
keywords: ''
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 01/25/2021
ms.openlocfilehash: ba0fada8ed167b9ba788f4f0d2f9ab9e900dcde4
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044293"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparar o Power BI Report Server e o serviço Power BI

O Power BI Report Server e o serviço Power BI têm muitas semelhanças e algumas diferenças importantes. Esta tabela explica cada uma delas.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Funcionalidades do Power BI Report Server e do serviço Power BI

| Funcionalidades | Power BI Report Server | Serviço Power BI | Notas |
|---------|---------|---------|---------|
| Implementação | Cloud no local ou alojada | Cloud | O Power BI Report Server poderá ser implementado em VMs do Azure (cloud alojada) se for licenciado através do Power BI Premium ou do SQL Server Enterprise com Software Assurance|
| Dados de origem | Na cloud e/ou no local | Na cloud e/ou no local |  |
| Licença | Power BI Premium ou o SQL Server EE com Software Assurance (SA) | Power BI Pro e/ou Power BI Premium | |  
| Ciclo de vida | Política de ciclo de vida moderna | Serviço totalmente gerido |  |
| Ciclo de lançamento | Três vezes por ano (janeiro, maio, setembro) | Uma vez por mês | As funcionalidades e correções mais recentes estarão disponíveis primeiro no serviço Power BI. Um rollup de funcionalidades do Power BI Desktop para o serviço incluído no Power BI Report Server em cada versão; a maioria das outras funcionalidades destinam-se apenas ao serviço Power BI. |
| Criar relatórios do Power BI no Power BI Desktop | Sim | Sim |  |
| Criar relatórios do Power BI no browser | Não | Sim |  |
| Alojar e ligar a conjuntos de dados partilhados do Power BI | Não | Sim | [Introdução aos conjuntos de dados em áreas de trabalho](../connect-data/service-datasets-across-workspaces.md) |
| Gateway necessário | Não | Sim para origens de dados no local |  |
| Transmissão em fluxo em tempo real | Não | Sim | [Transmissão em fluxo em tempo real no Power BI](../connect-data/service-real-time-streaming.md) |
| Dashboards | Não | Sim | [Dashboards no serviço Power BI](../consumer/end-user-dashboards.md) |
| Distribuir grupo de relatórios através de aplicações | Não | Sim | [Criar e publicar aplicações com dashboards e relatórios](../collaborate-share/service-create-distribute-apps.md) |
| Pacotes de conteúdos | Não | Sim | [Pacotes de conteúdos organizacionais: Introdução](../collaborate-share/service-organizational-content-pack-introduction.md) |
| Ligar a serviços como o Salesforce | Sim | Sim | [Ligue-se aos serviços que utiliza](../connect-data/service-connect-to-services.md) com pacotes de conteúdos no serviço Power BI. No Power BI Report Server, utilize conectores certificados para ligar a serviços. Veja [Origens de dados de relatórios do Power BI no Power BI Report Server](data-sources.md) para obter detalhes. |
| Perguntas e Respostas | Não | Sim | [Perguntas e Respostas no serviço Power BI e no Power BI Desktop](../create-reports/power-bi-tutorial-q-and-a.md) 
| Informações rápidas | Não | Sim | [Gerar automaticamente as informações de dados com o Power BI](../consumer/end-user-insights.md) |
| Analisar no Excel | Não | Sim | [Analyze in Excel](../collaborate-share/service-analyze-in-excel.md) 
| Relatórios paginados | Sim | Sim | [Os relatórios paginados estão disponíveis no serviço Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md) em pré-visualização numa capacidade Premium |
| Aplicações móveis do Power BI | Sim | Sim | [Descrição geral das aplicações móveis do Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ArcGIS para o Power BI | Yes | Sim | [ArcGIS para o Power BI](../visuals/power-bi-visualizations-arcgis.md) |
| Subscrições de e-mail para relatórios do Power BI | Não | Sim | [Subscrever um relatório ou dashboard](../collaborate-share/service-report-subscribe.md) para si ou para outras pessoas no serviço Power BI |
| Subscrições de e-mail para relatórios paginados | Sim | Sim | [Subscrever relatórios paginados no serviço Power BI para si e para outras pessoas](../consumer/paginated-reports-subscriptions.md)<br><br>[Email delivery in Reporting Services](/sql/reporting-services/working-with-subscriptions-web-portal) (Entrega de e-mail no Reporting Services)  |
| Alertas de dados | Não | Sim | [Alertas de dados](../create-reports/service-set-data-alerts.md) no serviço Power BI
| Segurança ao nível da linha (RLS) | Sim | Sim | Disponível no DirectQuery (origem de dados) e no Modo de importação <br><br>Segurança ao nível da linha no [serviço Power BI](../admin/service-admin-rls.md) <br><br>service-report-subscribe [Power BI Report Server](row-level-security-report-server.md) |
| Relações Muitos para muitos | Não | Sim | [Aplicar relações muitos-para-muitos](../transform-model/desktop-many-to-many-relationships.md) no Power BI Desktop |
| Pormenorização de relatórios cruzados | Não | Sim | [Utilizar a pormenorização de relatórios cruzados](../create-reports/desktop-cross-report-drill-through.md) |
| Modo de ecrã inteiro | Não | Sim | [Modo de ecrã inteiro](../consumer/end-user-focus.md) no serviço Power BI |
| Colaboração avançada do Microsoft 365 | Não | Sim | [Colaborar numa área de trabalho](../collaborate-share/service-collaborate-power-bi-workspace.md) com o Microsoft 365 |
| Scripts R e elementos visuais | Não | Sim | [Crie elementos visuais R](../create-reports/desktop-r-visuals.md) e execute scripts R no Power BI Desktop e publique-os no serviço Power BI. Não pode guardar relatórios do Power BI com scripts ou elementos visuais R no Power BI Report Server.  |
| Scripts de Python | Não | Sim | [Crie scripts de Python](../connect-data/desktop-python-scripts.md) e elementos visuais no Power BI Desktop e publique-os no serviço Power BI. Não pode guardar relatórios do Power BI com scripts de Python ou elementos visuais no Power BI Report Server. |
| Funcionalidades de pré-visualização | Não | Sim | [Optar ativamente por participar nas funcionalidades de pré-visualização](../consumer/end-user-preview-features.md) do serviço Power BI |
| Elementos Visuais do Power BI | Sim | Sim | [Elementos visuais do Power BI](../developer/visuals/power-bi-custom-visuals.md) |
| Modelos compostos | Não | Sim |
| Power BI Desktop | Versão otimizada para o Report Server, disponível para transferência com o Report Server | Versão otimizada para o Serviço Power BI, disponível na Loja Windows | [Power BI Desktop para o servidor de relatórios](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para o serviço Power BI](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Próximos passos

[Instalar o Power BI Report Server](install-report-server.md)