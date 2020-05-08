---
title: Resolver problemas com o desempenho dos relatórios no Power BI
description: Guia de resolução de problemas para diagnosticar desempenho lento dos relatórios no Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: a5230a39706ce5d6941c00386160fe10114442e1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "81527997"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Resolver problemas com o desempenho dos relatórios no Power BI

Este artigo apresenta orientações que permitem aos programadores e administradores resolver problemas de desempenho lento dos relatórios. Aplica-se aos relatórios do Power BI e aos relatórios paginados do Power BI.

Os relatórios lentos podem ser identificados pelos utilizadores dos relatórios que se deparam com o carregamento lento dos relatórios ou a atualização lenta quando interagem com a segmentação de dados ou outras funcionalidades. Quando os relatórios estão alojados numa capacidade Premium, os relatórios lentos também podem ser identificados ao monitorizar a [aplicação Power BI Premium Metrics](../service-admin-premium-monitor-capacity.md). Esta aplicação ajuda-o a monitorizar o estado de funcionamento e capacidade da sua subscrição do Power BI Premium.

## <a name="follow-flowchart-steps"></a>Siga os passos do fluxograma

Utilize o fluxograma seguinte para ajudar a compreender a causa do desempenho lento e para determinar que ação tomar.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="Imagem que mostra o fluxograma, que é totalmente descrito no texto do artigo." border="true":::

Existem seis terminadores de fluxograma, cada um deles descreve a ação a tomar:

|Terminador|Ações|
|---------|---------|
|![Terminador de fluxograma 1.](media/common/icon-01-red-30x30.png)|Gerir capacidade<br />Dimensionar capacidade |
|![Terminador de fluxograma 2.](media/common/icon-02-red-30x30.png)|Investigar a atividade da capacidade durante a utilização normal do relatório|
|![Terminador de fluxograma 3.](media/common/icon-03-red-30x30.png)|Alteração da arquitetura<br />Considerar o Azure Analysis Services<br />Verificar o gateway no local|
|![Terminador de fluxograma 4.](media/common/icon-04-red-30x30.png)|Considerar o Azure Analysis Services<br />Considerar o Power BI Premium|
|![Terminador de fluxograma 5.](media/common/icon-05-red-30x30.png)|Utilizar o Analisador de Desempenho do Power BI Desktop<br />Otimizar o relatório, o modelo ou o DAX|
|![Terminador de fluxograma 6.](media/common/icon-06-red-30x30.png)|Criar pedido de suporte|

## <a name="take-action"></a>Tomar medidas

A primeira consideração é compreender se o relatório lento está alojado numa capacidade Premium.

### <a name="premium-capacity"></a>Capacidade Premium

Quando o relatório está alojado numa capacidade Premium, utilize a **aplicação Power BI Premium Metrics** para determinar se a capacidade de alojamento do relatório excede frequentemente os recursos de capacidade. É o caso da CPU quando excede frequentemente 80% da capacidade. No caso da memória, é quando a [métrica de memória ativa](../service-premium-metrics-app.md#the-active-memory-metric) excede 50. Quando existe pressão sobre os recursos, pode estar na altura de [gerir ou dimensionar a capacidade](../service-admin-premium-manage.md) (terminador de fluxograma 1). Quando existirem recursos adequados, investigue a atividade da capacidade durante a utilização normal do relatório (terminador de fluxograma 2).

### <a name="shared-capacity"></a>Capacidade partilhada

Quando o relatório está alojado na capacidade partilhada, não é possível monitorizar o estado de funcionamento da capacidade. Terá de seguir uma abordagem de investigação diferente.

Primeiro, determine se o desempenho lento ocorre em horas específicas do dia ou do mês. Se ocorrer (e se muitos utilizadores estiverem a abrir o relatório nesses períodos), considere duas opções:

- Aumente o débito de consulta ao migrar o conjunto de dados para o [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) ou para uma capacidade Premium (terminador de fluxograma 4).
- Utilize o [Analisador de Desempenho](../desktop-performance-analyzer.md) do Power BI Desktop para saber o desempenho de cada um dos elementos do relatório, como elementos visuais e fórmulas DAX. É especialmente útil para determinar se é a consulta ou a composição de elementos visuais que está a contribuir para os problemas de desempenho (terminador de fluxograma 5).

Se determinar que não existe um padrão de data e hora, considere se o desempenho lento está isolado numa região ou geografia específica. Se assim for, será provável que a origem de dados seja remota e exista comunicação lenta da rede. Neste caso, considere:

- Alterar a arquitetura com o [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (terminador de fluxograma 3).
- Otimizar o [desempenho do gateway de dados no local](/data-integration/gateway/service-gateway-performance) (terminador de fluxograma 3).

Finalmente, se determinar que não existe um padrão de data e hora _e_ o desempenho lento ocorrer em todas as regiões, investigue se o desempenho lento ocorre em dispositivos, clientes ou browsers específicos. Se tal não ocorrer, utilize o [Analisador de Desempenho](../desktop-performance-analyzer.md) do Power BI Desktop, conforme descrito anteriormente, para otimizar o relatório ou o modelo (terminador de fluxograma 5).

Quando determinar que dispositivos, clientes ou browsers específicos contribuem para o desempenho lento, recomendamos a criação de um pedido de suporte através da [página de suporte do Power BI](https://powerbi.microsoft.com/support/) (terminador de fluxograma 6).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Documentação de orientação do Power BI](index.yml)
- [Monitorizar o desempenho dos relatórios](monitor-report-performance.md)
- [Analisador de Desempenho](../desktop-performance-analyzer.md)
- Documento técnico: [Planear uma Implementação Empresarial do Power BI](https://go.microsoft.com/fwlink/?linkid=2057861)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
