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
ms.openlocfilehash: 49a1f02e5aa327c2704b6c2d789934a43b760ad0
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68962017"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho numa capacidade Premium

Este artigo descreve como ativar e configurar cargas de trabalho para capacidades Premium do Power BI. Por predefinição, as capacidades só suportam as cargas de trabalho associadas à execução de consultas do Power BI. Também pode ativar e configurar cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)**, **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports-save-to-power-bi-service.md)**.

## <a name="default-memory-settings"></a>Predefinições de memória

As cargas de trabalho de consulta são otimizadas e limitadas por recursos determinados pelo SKU da capacidade Premium. As capacidades Premium também suportam cargas de trabalho adicionais que podem utilizar os recursos da sua capacidade. Os valores predefinidos da memória para estas cargas de trabalho são baseados nos nós de capacidade disponíveis para o seu SKU. As definições de memória máxima não são cumulativas. A memória até ao valor máximo especificado é alocada dinamicamente à IA e aos fluxos de dados, mas é alocada estaticamente aos relatórios paginados.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários de software como serviço (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| IA | N/D | N/D | 20% predefinido; 20% mínimo | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo |
| Fluxos de Dados | N/D |20% predefinido; 12% mínimo  | 20% predefinido; 5% mínimo  | 20% predefinido; 3% mínimo | 20% predefinido; 2% mínimo  |
| Relatórios paginados | N/D |N/D | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários de plataforma como serviço (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| IA | N/D                      | 20% predefinido; 100% mínimo                     | 20% predefinido; 50% mínimo                     | 20% predefinido; 20% mínimo | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo |
| Fluxos de Dados         | 40% predefinido; 40% mínimo | 24% predefinido; 24% mínimo | 20% predefinido; 12% mínimo | 20% predefinido; 5% mínimo  | 20% predefinido; 3% mínimo | 20% predefinido; 2% mínimo   |
| Relatórios paginados | N/D                      | N/D                      | N/D                     | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| | | | | | |

## <a name="workload-settings"></a>Definições das cargas de trabalho

### <a name="ai-preview"></a>IA (Pré-visualização)

Além da definição **Memória Máxima**, a carga de trabalho de IA tem uma definição adicional, **Permitir a utilização a partir do Power BI Desktop**. A predefinição é **Inativa**. Esta definição é reservada para utilização futura e poderá não ser apresentada em todos os inquilinos.

### <a name="datasets-preview"></a>Conjuntos de dados (Pré-visualização)

Por predefinição, a carga de trabalho Conjuntos de dados está ativada e não pode ser desativada. Esta carga de trabalho contém uma definição adicional para o _ponto final de XMLA_ e um conjunto de definições relacionadas com o desempenho. Esta definição do **Ponto Final de XMLA** especifica que as ligações das aplicações cliente são feitas de acordo com a associação de grupo de segurança definida aos níveis da área de trabalho e da aplicação. Para saber mais, veja [Ligar a conjuntos de dados com ferramentas e aplicações cliente](service-premium-connect-tools.md).

As definições relacionadas com o desempenho estão descritas na tabela seguinte.

| Nome da Definição | Descrição | Utilização |
|---------------------------------|----------------------------------------|----------------------------------------|
| **Contagem Máxima do Conjunto de Linhas Intermediárias** | O número máximo de linhas intermediárias devolvido pelo DirectQuery. O valor predefinido é 1000000 e o intervalo de valores permitido é entre 100000 e 2147483647 | Controlar o impacto de relatórios mal concebidos ou que exijam bastantes recursos. |
| **Tamanho Máximo do Conjunto de Dados Offline (GB)** | O tamanho máximo do conjunto de dados offline na memória. Este valor corresponde ao tamanho comprimido em disco. O valor predefinido é determinado pelo SKU e o intervalo permitido é entre 0,1 – 10 GB | Impedir que os criadores de relatórios publiquem um grande conjunto de dados que possa afetar negativamente a capacidade. |
| **Contagem Máxima do Conjunto de Linhas de Resultados** | Define o número máximo de linhas devolvidas numa consulta DAX. O valor predefinido é -1 (sem limite) e o intervalo de valores permitido é entre 100000 e 2147483647 | Controlar o impacto de relatórios mal concebidos ou que exijam bastantes recursos. |
| **Limite de Memória de Consulta (%)** | Aplica-se apenas a medidas e consultas DAX. Especificado em % e restringe a quantidade de memória que pode ser utilizada pelos resultados temporários durante uma consulta. | Controlar o impacto de relatórios mal concebidos ou que exijam bastantes recursos. |
| **Tempo Limite de Consulta (segundos)** | Um número inteiro que define o tempo limite, em segundos, para as consultas. A predefinição é 3600 segundos (ou 60 minutos). O valor Zero (0) especifica que nenhuma consulta irá atingir o tempo limite. | Manter um melhor controlo sobre consultas de execução longa. |
|  |  |  |

### <a name="dataflows"></a>Fluxos de Dados

Além da definição **Memória Máxima**, a carga de trabalho Fluxos de dados tem uma definição adicional, **Tamanho do contentor**. Esta definição permite-lhe otimizar o desempenho da carga de trabalho Fluxos de dados para processar fluxos de dados mais complexos que exijam mais recursos de computação.

Ao atualizar um fluxo de dados, a carga de trabalho Fluxo de dados gera um contentor para cada entidade no fluxo de dados. Cada contentor pode ocupar memória até ao volume especificado na definição Tamanho do contentor. A predefinição para todos os SKUs é **700 MB**. É aconselhável alterar esta definição se:

- Os fluxos de dados demorarem muito tempo a atualizarem ou se a atualização do fluxo de dados falhar e atingir o tempo limite.
- As entidades do fluxo de dados incluírem passos de computação, por exemplo, uma associação.  

É recomendável utilizar a aplicação [Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) para analisar o desempenho da carga de trabalho Fluxo de dados. 

Em alguns casos, aumentar o tamanho do contentor pode não melhorar o desempenho. Por exemplo, se o fluxo de dados de dados estiver a obter dados a partir de uma única origem sem efetuar cálculos significativos, é provável que o aumento do tamanho do contentor não resolva o problema. Aumentar o tamanho do contentor pode ajudar se permitir alocar mais memória na carga de trabalho Fluxo de dados para as operações de atualização de entidades. Ao alocar mais memória, pode reduzir o tempo necessário para atualizar entidades que exijam muitos recursos de computação.

O valor em Tamanho do Contentor não pode exceder a memória máxima da carga de trabalho Fluxo de dados. Por exemplo, uma capacidade P1 tem 25 GB de memória. Se a Memória Máxima (%) da carga de trabalho Fluxo de dados (%) estiver definida para 20%, o Tamanho do Contentor (MB) não poderá exceder 5000. Em todos os casos, o Tamanho do Contentor não pode exceder a Memória Máxima, mesmo que defina um valor mais alto.

### <a name="paginated-reports-preview"></a>Relatórios paginados (Pré-visualização)

Os relatórios paginados permitem a execução de código personalizado na composição do relatório. Por exemplo, alterar dinamicamente a cor do texto com base nos conteúdos, que pode ocupar memória adicional. O Power BI Premium executa relatórios paginados num espaço contido dentro da capacidade. A Memória Máxima especificada é utilizada, *independentemente* de a carga de trabalho estar ou não ativa. Se alterar a definição Memória Máxima da predefinição, certifique-se de que a define para um valor inferior o suficiente para não afetar negativamente outras cargas de trabalho.

Em alguns casos, a carga de trabalho Relatórios Paginados pode ficar indisponível. Neste caso, a carga de trabalho apresenta um estado de erro no Portal de administração e os utilizadores veem tempos limite para a composição do relatório. Para mitigar este problema, desative a carga de trabalho e, em seguida, ative-a novamente.

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Maximize os recursos disponíveis da sua capacidade ao permitir cargas de trabalho apenas se forem ser utilizadas. Altere as definições de memória e outras definições apenas quando tiver determinado que as predefinições não estão a cumprir os requisitos dos recursos de capacidade.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar cargas de trabalho no portal de administração do Power BI

1. Em **Definições de capacidade** > **CAPACIDADES PREMIUM**, selecione uma capacidade.

1. Em **MAIS OPÇÕES**, expanda **Cargas de trabalho**.

1. Ative uma ou mais cargas de trabalho e defina um valor para **Memória Máxima** e outras definições.

1. Selecione **Aplicar**.

### <a name="rest-api"></a>API REST

As cargas de trabalho podem ser ativadas e atribuídas a uma capacidade ao utilizar APIs REST de [Capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Monitorizar cargas de trabalho

A [aplicação Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) fornece as métricas de conjunto de dados, fluxos de dados e relatórios paginados para monitorizar as cargas de trabalho permitidas para as suas capacidades. 

## <a name="next-steps"></a>Próximos passos

[Otimizar as capacidades do Power BI Premium](service-premium-capacity-optimize.md)     
[Preparação personalizada de dados no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)