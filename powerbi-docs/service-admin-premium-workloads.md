---
title: Como configurar cargas de trabalho no Power BI Premium
description: Saiba como configurar cargas de trabalho numa capacidade Premium do Power BI.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: e22b598b81f34e80431d0def93d52f7301c500d4
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964646"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho numa capacidade Premium

Este artigo descreve como ativar e configurar cargas de trabalho para capacidades Premium do Power BI. Por predefinição, as capacidades só suportam as cargas de trabalho associadas à execução de consultas do Power BI. Também pode ativar e configurar cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)**, **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports-save-to-power-bi-service.md)**.

## <a name="default-memory-settings"></a>Predefinições de memória

As cargas de trabalho de consulta são otimizadas e limitadas por recursos determinados pelo SKU da capacidade Premium. As capacidades Premium também suportam cargas de trabalho adicionais que podem utilizar os recursos da sua capacidade. Os valores predefinidos da memória para estas cargas de trabalho são baseados nos nós de capacidade disponíveis para o seu SKU. As definições de memória máxima não são cumulativas. A memória até ao valor máximo especificado é alocada dinamicamente à IA e aos fluxos de dados, mas é alocada estaticamente aos relatórios paginados. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários de software como serviço (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| IA (Serviços Cognitivos) | 20% predefinido; TBD mínimo| 20% predefinido; TBD mínimo | 20% predefinido; TBD mínimo | 20% predefinido; TBD mínimo | 20% predefinido; TBD mínimo |
| Fluxos de Dados | N/D |20% predefinido; 12% mínimo  | 20% predefinido; 5% mínimo  | 20% predefinido; 3% mínimo | 20% predefinido; 2% mínimo  |
| Relatórios paginados | N/D |N/D | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários de plataforma como serviço (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| IA (Serviços Cognitivos) | N/D                      | 20% predefinido; TBD mínimo                      | 20% predefinido; TBD mínimo                     | 20% predefinido; TBD mínimo | 20% predefinido; TBD mínimo | 20% predefinido; TBD mínimo |
| Fluxos de Dados         | 40% predefinido; 40% mínimo | 24% predefinido; 24% mínimo | 20% predefinido; 12% mínimo | 20% predefinido; 5% mínimo  | 20% predefinido; 3% mínimo | 20% predefinido; 2% mínimo   |
| Relatórios paginados | N/D                      | N/D                      | N/D                     | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| | | | | | |

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Maximize os recursos disponíveis da sua capacidade ao permitir cargas de trabalho apenas se forem ser utilizadas. Altere as definições de memória apenas quando tiver determinado que as predefinições não estão a cumprir os requisitos dos recursos de capacidade.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar cargas de trabalho no portal de administração do Power BI

1. Em **Definições de capacidade** > **CAPACIDADES PREMIUM**, selecione uma capacidade.

1. Em **MAIS OPÇÕES**, expanda **Cargas de trabalho**.

1. Ative uma ou mais cargas de trabalho e defina um valor para **Memória Máx**.   

    
    ![Ativar cargas de trabalho](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Clique em **Aplicar**.

> [!NOTE]
> Se ativar a carga de trabalho de relatórios paginados, os relatórios paginados permitirão executar o seu próprio código ao compor um relatório (por exemplo, alterar dinamicamente a cor do texto com base nos conteúdos). O Power BI Premium executa relatórios paginados num espaço contido dentro da capacidade. A memória máxima que especificar para este espaço é utilizada, independentemente de a carga de trabalho estar ou não ativa. Se utilizar fluxos de dados ou relatórios do Power BI na mesma capacidade, certifique-se de que define a memória suficientemente baixa para relatórios paginados de modo a não afetar as outras cargas de trabalho de forma negativa. Em circunstâncias raras, a carga de trabalho Relatórios paginados pode ficar indisponível. Neste caso, a carga de trabalho apresenta um estado de erro no portal de administração e os utilizadores veem tempos limite para a composição do relatório. Para mitigar este problema, desative a carga de trabalho e, em seguida, ative-a novamente.

### <a name="rest-api"></a>API REST

As cargas de trabalho podem ser ativadas e atribuídas a uma capacidade ao utilizar APIs REST de [Capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Monitorizar cargas de trabalho

A [aplicação Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) fornece as métricas de conjunto de dados, fluxos de dados e relatórios paginados para monitorizar as cargas de trabalho permitidas para as suas capacidades. 

## <a name="next-steps"></a>Próximos passos

[Gestão e otimização do recurso de capacidades do Power BI Premium](service-premium-understand-how-it-works.md)   
[Preparação personalizada de dados no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)