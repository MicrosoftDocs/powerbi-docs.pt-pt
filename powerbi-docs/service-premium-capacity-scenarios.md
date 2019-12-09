---
title: Cenários de capacidade do Microsoft Power BI Premium
description: Descreve cenários comuns de capacidade do Microsoft Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 9b3e06172d29f218f9234cf1f3d7e1f623495001
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74697273"
---
# <a name="premium-capacity-scenarios"></a>Cenários de capacidades Premium

Este artigo descreve cenários do mundo real onde foram implementadas capacidades premium do Power BI. Estão descritos problemas e desafios comuns, como os identificar e ajudar a resolver ao:

- [Manter conjuntos de dados atualizados](#keeping-datasets-up-to-date)
- [Identificar conjuntos de dados de resposta lenta](#identifying-slow-responding-datasets)
- [Identificar causas de conjuntos de dados de resposta esporadicamente lenta](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinar se existe memória suficiente](#determining-whether-there-is-enough-memory)
- [Determinar se existe CPU suficiente](#determining-whether-there-is-enough-cpu)

Os passos, juntamente com os exemplos do gráfico e da tabela, são da **aplicação Métricas de Capacidade do Power BI Premium**, à qual um administrador do Power BI terá acesso.

## <a name="keeping-datasets-up-to-date"></a>Manter conjuntos de dados atualizados

Neste cenário, foi acionada uma investigação quando os utilizadores reclamaram que os dados do relatório por vezes parecem ser antigos ou obsoletos.

Na aplicação, o administrador interage com o elemento visual **Atualiza**, ao ordenar os conjuntos de aplicações pelas estatísticas **Tempo de Espera Máximo**, por ordem decrescente. Este elemento visual ajuda a revelar conjuntos de dados com os tempos de espera mais longos, agrupados por nome de área de trabalho.

![Atualizações do conjunto de dados ordenadas por tempo de espera máximo decrescente, agrupadas por área de trabalho](media/service-premium-capacity-scenarios/dataset-refreshes.png)

No elemento visual **Tempos de Espera de Atualização Média por Hora**, foi observado que o pico dos tempos de espera de atualização ocorreu consistentemente em torno das 16:00 todos os dias.

![A atualização aguarda o pico periodicamente às 16:00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Existem várias explicações possíveis para estes resultados:

- Podem estar a ocorrer demasiadas tentativas de atualização em simultâneo, excedendo os limites definidos pelo nó de capacidade. Neste caso, seis atualizações simultâneas num P1 com alocação de memória predefinida.

- Os conjuntos de valores a serem atualizados podem ser muito grandes para se ajustarem à memória disponível (exigindo, pelo menos, o dobro da memória necessária para a atualização completa).
- A lógica do Power Query ineficiente pode estar a resultar num pico de utilização de memória durante a atualização do conjunto de resultados. Numa capacidade ocupada, este pico pode alcançar por vezes o limite físico, falhando a atualização e potencialmente afetando outras operações de apresentação de relatórios sobre a capacidade.
- Os conjuntos de dados consultados com frequência que precisam de permanecer na memória podem afetar a capacidade de atualização de outros conjuntos de dados devido à memória disponível limitada.

Para ajudar a investigar, o administrador do Power BI pode procurar:

- Baixa memória disponível no momento em que os dados são atualizados quando a memória disponível é inferior ao dobro do tamanho do conjunto de dados a ser atualizado.
- Os conjuntos de dados não estão a ser atualizados e não estão na memória antes da atualização, mas começaram a mostrar o tráfego interativo durante tempos de atualização pesados. Para ver os conjuntos de dados que são carregados para a memória a qualquer momento, um administrador do Power BI pode ver a área conjuntos de dados no separador **Conjuntos de dados** na aplicação. O administrador pode utilizar a função de filtro cruzado num determinado horário ao clicar numa das barras nas **Contagens de Conjuntos de Dados Carregados por Hora**. Um pico local, mostrado na imagem abaixo, indica uma hora em que vários conjuntos de dados foram carregados para a memória, o que poderia atrasar o início das atualizações agendadas.
- Ocorrem mais expulsões de conjuntos de dados quando as atualizações estão agendadas para iniciar. As expulsões podem indicar que houve pressão de memória elevada causada pelo fornecimento de muitos relatórios interativos diferentes antes do momento da atualização. O elemento visual **Expulsões do Conjunto de Dados e Consumo de Memória Por Hora** pode indicar claramente picos em expulsões.

A imagem a seguir mostra um pico local nos conjuntos de dados carregados, o que sugere que uma consulta interativa atrasou o início das atualizações. A seleção de um período de tempo no elemento visual **Contagens do Conjunto de Dados Carregados Por Hora** irá utilizar o filtro cruzado no elemento visual **Tamanhos dos Conjuntos de Dados**.

![Um pico local nos conjuntos de dados carregados sugere que uma consulta interativa atrasou o início das atualizações](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

O administrador do Power BI pode tentar resolver o problema ao seguir os passos para garantir que existe memória suficiente disponível para as atualizações de dados serem iniciadas ao:

- Contactar os proprietários do conjunto de dados e pedir-lhes para escalonar e espaçar agendamentos de atualizações.
- Reduzir a carga de consulta do conjunto de dados ao remover dashboards ou mosaicos de dashboards desnecessários, especialmente os que impõem segurança ao nível da linha.
- Acelerar as atualizações de dados ao otimizar a lógica do Power Query. Melhore a modelação de colunas ou tabelas calculadas. Reduza os tamanhos dos conjuntos de dados ou configure conjuntos de dados maiores para executar a atualização incremental de dados.

## <a name="identifying-slow-responding-datasets"></a>Identificar conjuntos de dados de resposta lenta

Neste cenário, começou uma investigação quando os utilizadores reclamaram que determinados relatórios demoravam muito tempo para abrir e, às vezes, eram interrompidos.

Na aplicação, o administrador do Power BI pode utilizar o elemento visual **Durações de Consulta** para determinar os piores conjuntos de dados de desempenho, ao ordenar os conjuntos de dados por ordem decrescente de **Duração Média**. Este elemento visual também mostra contagens da consulta do conjunto de dados, para que possa ver com que frequência os conjuntos de dados são consultados.

![Conjuntos de dados com o pior desempenho](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

O administrador pode consultar o elemento visual **Distribuição da Duração da Consulta**, que mostra uma distribuição geral do desempenho da consulta registada (<= 30 ms, 0-100 ms) no período de tempo filtrado. Geralmente, as consultas que demoram um segundo ou menos são consideradas responsivas pela maioria dos utilizadores; as consultas que demoram mais tendem a criar uma perceção de mau desempenho.

O elemento visual **Distribuição da Duração da Consulta Por Hora** permite que o administrador do Power BI identifique períodos de uma hora quando o desempenho da capacidade pode ter sido percebido como insatisfatório. Quanto maiores forem os segmentos de barras que representam durações de consulta num segundo, maior será o risco de que os utilizadores irão perceber o desempenho insatisfatório.

O elemento visual é interativo e, quando um segmento da barra é selecionado, o elemento visual da tabela **Durações da Consulta** correspondente na página do relatório é filtrado de forma cruzada para mostrar os conjuntos de dados que ele representa. Esta filtragem cruzada permite que o administrador do Power BI identifique facilmente os conjuntos de dados que estão a responder lentamente.

A imagem a seguir mostra um elemento visual filtrado por **Distribuições de Duração de Consulta Por Hora**, concentrando-se nos conjuntos de dados com pior desempenho em intervalos de uma hora. 

![O elemento visual de Distribuições de Duração de Consulta Filtrados Por Hora mostra os conjuntos de dados com pior desempenho](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Quando o conjunto de dados com pior desempenho num período específico de uma hora for identificado, o administrador do Power BI pode investigar se o baixo desempenho é causado por uma capacidade sobrecarregada ou devido a um relatório ou conjunto de dados mal concebido. O elemento visual **Tempos de Espera de Consulta** pode ser acedido, de forma a ordenar conjuntos de dados por tempo médio decrescente de espera de consulta. Se uma grande percentagem de consultas estiver a aguardar, uma procura elevada pelo conjunto de dados é provavelmente a causa de muitas esperas de consulta. Se o tempo médio de espera da consulta for significativo (> 100 ms), poderá valer a pena rever o conjunto de dados e comunicá-lo para ver se podem ser feitas otimizações. Por exemplo, menos elementos visuais em determinadas páginas de relatório ou numa otimização de expressão do DAX.

![O elemento visual Tempos de Espera da Consulta ajuda a revelar conjuntos de dados com mau desempenho](media/service-premium-capacity-scenarios/query-wait-times.png)

Há várias razões possíveis para o tempo de espera da consulta acumular nos conjuntos de dados:

- Um design de modelo de qualidade inferior, expressões de medida ou até mesmo o design do relatório – todas as circunstâncias que podem contribuir para consultas de execução prolongada que consomem altos níveis de CPU. O que força as novas consultas a aguardar até que os threads de CPU fiquem disponíveis e possam criar um efeito de comboio (como um engarrafamento de trânsito), normalmente visto durante o pico do horário comercial. A página **Esperas de Consulta** será o recurso principal para determinar se os conjuntos de dados têm tempos de espera médios de consulta.
- Um elevado número de utilizadores de capacidade simultânea (centenas a milhares) que consomem o mesmo relatório ou conjunto de dados. Até mesmo os conjuntos de dados bem desenhados podem ter um mau desempenho além de um limite de simultaneidade. O que é geralmente indicado por um único conjunto de dados, mostrando um valor consideravelmente mais alto para contagens de consulta do que outros conjuntos de valores mostram (por exemplo, 300 mil consultas para um conjunto de dados em comparação com <30 mil consultas para todos os outros conjuntos de dados). Em algum momento, a consulta espera que este conjunto de dados comece a escalonar, o que pode ser visto no elemento visual **Durações da Consulta**.
- Foram consultados muitos conjuntos de dados diferentes em simultâneo, causando thrashing, dado que os conjuntos de dados saem e entram frequentemente da memória. O que resulta num desempenho reduzido para os utilizadores quando o conjunto de dados é carregado para a memória. Para confirmar, o administrador do Power BI pode consultar o elemento visual **Expulsões do Conjunto de Dados e Consumo de Memória Por Hora**, que pode indicar que um grande número de conjuntos de dados carregados para a memória está a ser expulso repetidamente.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificar causas de conjuntos de dados de resposta esporadicamente lenta

Neste cenário, começou uma investigação quando os utilizadores descreveram que os elementos visuais do relatório às vezes eram lentos para responder ou deixavam de responder, mas noutras alturas respondiam de forma aceitável.

Na aplicação, a secção **Durações da Consulta** foi utilizada para encontrar o conjunto de dados responsável da seguinte forma:

- No elemento visual **Durações da Consulta**, o administrador filtrou o conjunto de dados por conjunto de dados (começando pelos conjuntos de dados principais consultados) e examinou as barras com filtro cruzado no elemento visual **Distribuições de Consulta Por Hora**.
- Quando uma única barra de uma hora mostrou alterações significativas na proporção entre todos os grupos de duração da consulta em relação a outras barras de uma hora para esse conjunto de dados (por exemplo, as proporções entre as cores são alteradas de forma drástica), significa que este conjunto de dados demonstrou uma alteração esporádica no desempenho.
- As barras de uma hora que mostram uma parte irregular das consultas de baixo desempenho, indicaram um intervalo de tempo em que esse conjunto de dados foi afetado por um efeito vizinho ruidoso, causado por outras atividades de conjuntos de dados.

A imagem abaixo mostra uma hora a 30 de janeiro, em que ocorreu um retrocesso significativo no desempenho de um conjunto de dados, indicado pelo tamanho do registo da duração da execução "(3,10 s)". Clicar nessa barra de uma hora revela todos os conjuntos de dados carregados para a memória durante esse tempo, surgindo possíveis conjuntos de dados que causam o efeito de vizinho ruidoso.

![Barra que mostra o pior desempenho numa grande parte](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Assim que um intervalo de tempo problemático é identificado (por exemplo, durante 30 de janeiro na imagem acima), o administrador do Power BI pode remover todos os filtros do conjunto de dados e então filtrar apenas por esse intervalo de tempo, para determinar quais foram os conjuntos de dados ativamente consultados durante esse período. O conjunto de dados responsável pelo efeito de vizinho ruidoso é geralmente o conjunto de dados mais consultado ou aquele com a duração média mais longa da consulta.

Uma solução para este problema pode ser distribuir os conjuntos de dados responsáveis em diferentes áreas de trabalho em diferentes capacidades Premium, ou em capacidade partilhada, se o tamanho do conjunto de dados, os requisitos de consumo e os padrões de atualização forem suportados.

O inverso também pode ser verdade. O administrador do Power BI pode identificar os momentos em que um desempenho de consulta de um conjunto de dados melhora drasticamente e, em seguida, procura o que desapareceu. Se determinadas informações estiverem em falta nesse ponto, pode ajudar a apontar para o problema causador.

## <a name="determining-whether-there-is-enough-memory"></a>Determinar se existe memória suficiente

Para determinar se existe memória suficiente para a capacidade concluir as suas cargas de trabalho, o administrador do Power BI pode consultar o elemento visual **Percentagens de Memória Consumidas** no separador **Conjuntos de dados** da aplicação. **Toda** representa a memória total consumida pelos conjuntos de dados carregados para a memória, independentemente de serem consultados ou processados ativamente. **Ativa** representa a memória ativa consumida pelos conjuntos de dados que estão a ser processados ativamente.

Numa capacidade em bom estado de funcionamento, o elemento visual terá esta aparência, mostrando uma lacuna entre Toda (total) e a memória Ativa:

![Uma capacidade em bom estado de funcionamento irá mostrar uma lacuna entre Toda (total) e a memória Ativa](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Numa capacidade que está a sofrer pressão de memória, o mesmo elemento visual irá mostrar claramente a convergência entre a memória ativa e a memória total, o que significa que é impossível carregar conjuntos de dados adicionais para a memória. Neste caso, o administrador do Power BI pode clicar em **Reinício da Capacidade** (em **Opções Avançadas** da área de definições da capacidade do portal de administração). Reiniciar os resultados da capacidade em todos os conjuntos de dados que são removidos da memória e permitir que eles recarreguem para a memória conforme preciso (por consultas ou atualização de dados).

![Memória **Ativa** convergente com a memória **Toda**](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Determinar se existe CPU suficiente

Em geral, a utilização média da CPU de uma capacidade deve permanecer abaixo de 80%. Exceder este valor significa que a capacidade está a aproximar-se da saturação da CPU.

Os efeitos da saturação da CPU são expressos por operações que demoram mais do que deveriam, devido à capacidade de executar muitas alternâncias de contextos de CPU, à medida que tenta processar todas as operações. Numa capacidade Premium com um número elevado de consultas em simultâneo, isto é indicado por tempos de espera de consulta altos. Uma consequência dos tempos de espera de consulta altos é a capacidade de resposta mais lenta do que o habitual. O administrador do Power BI consegue identificar facilmente quando a CPU está saturada ao ver o elemento visual **Distribuições do Tempo de Espera de Consulta Por Hora**. Os picos periódicos de contagens de tempo de espera de consulta indicam uma potencial saturação de CPU.

![Os picos periódicos de contagens de tempo de espera de consulta indicam uma potencial saturação de CPU](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Às vezes pode ser detetado um padrão semelhante em operações em segundo plano se contribuir para a saturação da CPU. Um administrador do Power BI pode procurar um pico periódico em momentos de atualização para um conjunto de dados específico, o que pode indicar a saturação da CPU no momento (provavelmente devido a outras atualizações de conjunto de dados em curso e/ou consultas interativas). Nesta instância, aceder à vista **Sistema** na aplicação pode não revelar necessariamente que a CPU está a 100%. A vista **Sistema** apresenta as médias por hora, mas a CPU pode ficar saturada de operações pesadas durante vários minutos, que aparecem como picos nos tempos de espera.

Existem mais nuances para ver o efeito da saturação da CPU. Embora o número de consultas esperado seja importante, o tempo de espera da consulta irá sempre ocorrer até certo ponto, sem causar uma degradação discernível do desempenho. Alguns conjuntos de resultados (com tempo médio de consulta mais demorado, o que indica complexidade ou tamanho) são mais propensos aos efeitos da saturação da CPU do que outros. Para identificar facilmente estes conjuntos de dados, o administrador do Power BI pode procurar por mudanças na composição de cores das barras no elemento visual **Distribuição do Tempo de Espera Por Hora**. Depois de detetarem uma barra diferente, podem procurar os conjuntos de dados que tiveram esperas de consulta durante esse tempo e ver o tempo médio de espera de consulta em comparação com a duração média da consulta. Quando estas duas métricas são da mesma magnitude e a carga de trabalho da consulta para o conjunto de dados não é trivial, é provável que o conjunto de dados seja afetado pela CPU insuficiente.

Este efeito pode ser especialmente aparente quando um conjunto de dados é consumido em pequenos picos de consultas de alta frequência por vários utilizadores (por exemplo, numa sessão de preparação), resultando na saturação da CPU durante cada pico. Neste caso, podem ser experimentados tempos de espera de consulta significativos neste conjunto de recursos, bem como o impacto noutros conjuntos de dados na capacidade (efeito de vizinho ruidoso).

Em alguns casos, os administradores do Power BI podem pedir que os proprietários do conjunto de dados criem uma carga de trabalho de consulta menos volátil ao criar um dashboard (que consultam periodicamente com qualquer atualização de conjunto de dados para mosaicos em cache) em vez de um relatório. Isto pode ajudar a evitar picos quando o dashboard é carregado. Esta solução nem sempre é possível para determinados requisitos de negócios, no entanto, pode ser uma forma eficaz para evitar a saturação da CPU, sem alterar o conjunto de dados.

## <a name="acknowledgements"></a>Agradecimentos

Este artigo foi escrito por Peter Myers, MVP de Plataforma de Dados e especialista independente de BI na [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Monitorizar as capacidades Premium com a aplicação](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Monitorizar capacidades no Portal de administração](service-admin-premium-monitor-portal.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||