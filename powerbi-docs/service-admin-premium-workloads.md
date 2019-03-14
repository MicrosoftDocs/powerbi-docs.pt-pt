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
ms.date: 03/11/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0baab138ee98d2ec96bc9f47e6e727525a57ed3e
ms.sourcegitcommit: f176ba9d52d50d93f264eca21bb3fd987dbf934b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57757252"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho numa capacidade Premium

Este artigo descreve como ativar e configurar cargas de trabalho para capacidades Premium do Power BI. Por predefinição, as capacidades só suportam as cargas de trabalho associadas à execução de consultas do Power BI. As cargas de trabalho de consulta são otimizadas e limitadas por recursos determinados pelo SKU da capacidade Premium. As capacidades Premium também suportam cargas de trabalho adicionais que utilizam recursos de capacidades.

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Pode ativar e configurar cargas de trabalho adicionais para IA, [Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) e [Relatórios paginados](paginated-reports-save-to-power-bi-service.md). Os valores predefinidos da memória para estas cargas de trabalho são baseados nos nós de capacidade disponíveis para o seu SKU. As definições de memória máxima não são cumulativas. A memória até ao valor máximo especificado é alocada dinamicamente à IA e aos fluxos de dados, mas é alocada estaticamente aos relatórios paginados. 

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


## <a name="next-steps"></a>Próximos passos

[Gestão e otimização do recurso de capacidades do Power BI Premium](service-premium-understand-how-it-works.md)   
[Preparação personalizada de dados no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)