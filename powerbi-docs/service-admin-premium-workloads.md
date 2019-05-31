---
title: Como configurar cargas de trabalho no Power BI Premium
description: Saiba como configurar cargas de trabalho numa capacidade Premium do Power BI.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564864"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho numa capacidade Premium

Este artigo descreve como ativar e configurar cargas de trabalho para capacidades Premium do Power BI. Por predefinição, as capacidades só suportam as cargas de trabalho associadas à execução de consultas do Power BI. Também pode ativar e configurar cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)** , **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Predefinições de memória

As cargas de trabalho de consulta são otimizadas e limitadas por recursos determinados pelo SKU da capacidade Premium. As capacidades Premium também suportam cargas de trabalho adicionais que podem utilizar os recursos da sua capacidade. Os valores predefinidos da memória para estas cargas de trabalho são baseados nos nós de capacidade disponíveis para o seu SKU. As definições de memória máxima não são cumulativas. A memória até ao valor máximo especificado é alocada dinamicamente à IA e aos fluxos de dados, mas é alocada estaticamente aos relatórios paginados. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários de software como serviço (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N/D | N/D | padrão de 20%. mínimo de 20% | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo |
| Fluxos de Dados | N/D |20% predefinido; 12% mínimo  | 20% predefinido; 5% mínimo  | 20% predefinido; 3% mínimo | 20% predefinido; 2% mínimo  |
| Relatórios paginados | N/D |N/D | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários de plataforma como serviço (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N/D                      | padrão de 20%. mínimo de 100%                     | padrão de 20%. mínimo de 50%                     | padrão de 20%. mínimo de 20% | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo |
| Fluxos de Dados         | 40% predefinido; 40% mínimo | 24% predefinido; 24% mínimo | 20% predefinido; 12% mínimo | 20% predefinido; 5% mínimo  | 20% predefinido; 3% mínimo | 20% predefinido; 2% mínimo   |
| Relatórios paginados | N/D                      | N/D                      | N/D                     | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| | | | | | |

## <a name="workload-settings"></a>Definições de carga de trabalho

### <a name="ai-preview"></a>IA (pré-visualização)

Além da **máx. de memória** definição, a carga de trabalho de IA tem uma configuração adicional, **permitir que a utilização do Power BI Desktop**. A predefinição é **desativar**. Esta definição está reservada para utilização futura e pode não aparecer em todos os inquilinos.

### <a name="datasets-preview"></a>Conjuntos de dados (pré-visualização)

Por predefinição, a carga de trabalho de conjuntos de dados está ativada e não pode ser desativada. Esta carga de trabalho contém uma configuração adicional, **ponto final XMLA**. A predefinição é **1**, significado ativado. Esta definição especifica ligações a partir de aplicações cliente honrar a associação ao grupo de segurança definido nos níveis de área de trabalho e aplicações. Para obter mais informações, consulte [ligar a conjuntos de dados com as ferramentas e aplicativos cliente](service-premium-connect-tools.md).

### <a name="dataflows"></a>Fluxos de Dados

Para além da **máx. de memória** definição, a carga de trabalho de fluxos de dados tem uma configuração adicional, **tamanho do contentor**. Esta definição permite-lhe otimizar o desempenho de carga de trabalho do fluxo de dados para o processamento de fluxos de dados mais complexos e de computação intensiva.

Ao atualizar um fluxo de dados, a carga de trabalho do fluxo de dados gera um contentor para cada entidade no fluxo de dados. Cada contentor pode pegar a memória até o volume em especificado na definição de tamanho de contentor. É a predefinição para todos os SKUs **700 MB**. Pode querer alterar esta definição se:

- Fluxos de dados demorarem demasiado tempo a atualizar ou falha de atualização de fluxo de dados num tempo limite.
- Entidades de fluxo de dados incluem os passos de computação, por exemplo, uma associação.  

Ele do que recomendamos que utilize o [métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) aplicação para analisar o desempenho da carga de trabalho de fluxo de dados. 

Em alguns casos, aumentar o tamanho do contentor pode não melhorar o desempenho. Por exemplo, se o fluxo de dados está a receber dados apenas a partir de uma origem sem efetuar cálculos significativos, alterar o tamanho do contentor provavelmente não ajudará. Aumentar o tamanho do contentor pode ajudar se promove a carga de trabalho do fluxo de dados alocar mais memória para a entidade de operações de atualização. Dispondo de mais memória alocada, pode reduzir o tempo que demora a atualizar entidades intensamente calculadas. 

O valor do tamanho do contentor não pode exceder o máximo de memória para a carga de trabalho de fluxos de dados. Por exemplo, uma capacidade de P1 tem 25GB de memória. Se a carga de trabalho do fluxo de dados máx. de memória (%) está definido para 20%, contentor. o tamanho (MB) não pode exceder os 5000. Em todos os casos, o tamanho do contentor não pode exceder a memória máxima, mesmo que defina um valor mais alto. 

### <a name="paginated-reports-preview"></a>Relatórios paginados (pré-visualização)

Relatórios paginados permitem que o código personalizado ser executado quando a composição de um relatório. Por exemplo, alterar dinamicamente a cor do texto com base no conteúdo, o que pode demorar memória adicional. O Power BI Premium executa relatórios paginados num espaço contido dentro da capacidade. Máx. de memória especificado é utilizada *se pretende ou não* a carga de trabalho está ativa. Se alterar a definição de memória máxima da predefinição, certifique-se de que defini-lo baixa o suficiente para que ele não afeta negativamente outras cargas de trabalho.

Em alguns casos, a carga de trabalho de relatórios paginados pode se tornar indisponível. Neste caso, a carga de trabalho mostra um Estado de erro no portal de administração e os utilizadores veem tempos limite para a composição do relatório. Para atenuar este problema, desative a carga de trabalho e, em seguida, ative-a novamente.

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Maximize os recursos disponíveis da sua capacidade ao permitir cargas de trabalho apenas se forem ser utilizadas. Altere as definições de memória apenas quando tiver determinado que as predefinições não estão a cumprir os requisitos dos recursos de capacidade.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar cargas de trabalho no portal de administração do Power BI

1. Em **Definições de capacidade** > **CAPACIDADES PREMIUM**, selecione uma capacidade.

1. Em **MAIS OPÇÕES**, expanda **Cargas de trabalho**.

1. Ative uma ou mais cargas de trabalho e defina um valor para **Memória Máx**.   

    
    ![Ativar cargas de trabalho](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Clique em **Aplicar**.

### <a name="rest-api"></a>API REST

As cargas de trabalho podem ser ativadas e atribuídas a uma capacidade ao utilizar APIs REST de [Capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Monitorizar cargas de trabalho

A [aplicação Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) fornece as métricas de conjunto de dados, fluxos de dados e relatórios paginados para monitorizar as cargas de trabalho permitidas para as suas capacidades. 

## <a name="next-steps"></a>Próximos passos

[Otimizar as capacidades do Power BI Premium](service-premium-capacity-optimize.md)     
[Preparação personalizada de dados no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)