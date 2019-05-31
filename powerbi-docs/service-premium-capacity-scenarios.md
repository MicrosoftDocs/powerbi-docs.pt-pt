---
title: Cenários de capacidade do Microsoft Power BI Premium
description: Descreve os cenários comuns de capacidade do Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565367"
---
# <a name="premium-capacity-scenarios"></a>Cenários de capacidade Premium

Este artigo descreve cenários reais em que as capacidades do Power BI premium foram implementadas. Problemas comuns e os desafios são descritos, também como identificar problemas e ajudar a resolvê-los:

- [Manter os conjuntos de dados atualizados](#keeping-datasets-up-to-date)
- [Resposta lenta a conjuntos de dados de identificação](#identifying-slow-responding-datasets)
- [Identificar as causas para esporadicamente lento de resposta conjuntos de dados](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinar se existe memória suficiente](#determining-whether-there-is-enough-memory)
- [Determinar se existe suficiente CPU](#determining-whether-there-is-enough-cpu)

Os passos, junto com exemplos de gráfico e tabela são do **aplicação de métricas de capacidade do Power BI Premium** que têm acesso a um administrador do Power BI.

## <a name="keeping-datasets-up-to-date"></a>Manter os conjuntos de dados atualizados

Neste cenário, uma investigação foi acionada quando os usuários reclamam que os dados de relatório apareceram, às vezes, ser antigo ou "obsoleto".

Na aplicação, o administrador interage com o **atualiza** elemento visual, conjuntos de dados de classificação a **de tempo de espera máximo** estatísticas por ordem descendente. Este elemento visual ajuda a revelar os conjuntos de dados com os tempos de espera mais longo, agrupados por nome de área de trabalho.

![Atualizações de conjunto de dados ordenadas por tempo de espera máximo, agrupado por área de trabalho de descendentes](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Na **por hora média atualizar aguardar vezes** visual, tenha em atenção que os tempos de espera da atualização picos consistentemente cerca de 4 horas por dia.

![Atualização aguarda pico periodicamente às 16:00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Há várias explicações possíveis para esses resultados:

- Demasiadas tentativas de atualização podem ocorrer ao mesmo tempo, a exceder os limites definidos pelo nó de capacidade. Neste caso, seis atualizações simultâneas num P1 com alocação de memória padrão.

- Conjuntos de dados seja atualizado podem ser demasiado grandes para caber na memória disponível (o que requer, pelo menos, 2 x a memória necessária para atualização completa).
- Lógica ineficiente do Power Query pode ser resultando num pico de utilização de memória durante a atualização do conjunto de dados. Numa capacidade de ocupado, esse pico ocasionalmente pode atingir o limite, a atualização a falhar e potencialmente afetar outras operações de vista de relatório na capacidade físico.
- Conjuntos de dados consultados com frequência que precisam para se manter na memória podem afetar a capacidade de outros conjuntos de dados de atualização devido a memória disponível limitada.

Para ajudar a investigar, o administrador do Power BI pode procurar:

- Falta de memória disponível no momento de dados é atualizada quando a memória disponível é menor do que 2 vezes o tamanho do conjunto de dados para ser atualizado.
- Conjuntos de dados não sejam atualizados e não na memória antes de atualizar, ainda começou a aparecer tráfego interativo durante as horas de atualização pesada. Para ver que conjuntos de dados são carregados na memória em qualquer momento, um administrador do Power BI pode ver a área de conjuntos de dados do **conjuntos de dados** separador na aplicação. O administrador pode, em seguida, filtro cruzado para um determinado momento clicando em uma das barras no **por hora carregado conjunto de dados contagens**. Um pico local, mostrado na imagem abaixo, indica uma hora quando vários conjuntos de dados foram carregados na memória, o que poderia causar um atraso de início de atualizações agendadas.
- Expulsões de conjunto de dados maior tirar colocam quando as atualizações de dados são agendadas para ser inicializados. Expulsões podem indicar há pressão de memória elevada foi causada pelo uso de muitos relatórios interativos diferentes antes da data de atualização. O **Expulsões de conjunto de dados por hora e o consumo de memória** visual pode indicam claramente picos na expulsões.

A imagem seguinte mostra um pico de local em conjuntos de dados carregados, que sugere consultas interativas início com atraso de atualizações. Selecionar um período de tempo no **por hora carregado conjunto de dados contagens** visual irá filtro cruzado a **tamanhos de conjunto de dados** visual.

![Um pico local em conjuntos de dados carregados sugere início atrasado de consulta interativo de atualizações](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

O administrador do Power BI pode tentar resolver o problema efetuando os passos para se certificar de que a memória suficiente está disponível para atualizações de dados começar por:

- Entrar em contato com o conjunto de dados proprietários e solicitar para escalonar e os dados do espaço atualizar agendas.
- Reduzir o conjunto de dados de carregamento de consulta ao remover dashboards desnecessários ou dashboard mosaicos, especialmente aquelas que impor segurança ao nível da linha.
- Acelerar as atualizações de dados ao otimizar a lógica do Power Query. Melhore a Modelagem de tabelas ou colunas calculadas. Reduza os tamanhos de conjunto de dados ou configurar conjuntos de dados maiores para efetuar a atualização de dados incrementais.

## <a name="identifying-slow-responding-datasets"></a>Resposta lenta a conjuntos de dados de identificação

Neste cenário, uma investigação começou quando os usuários reclamam que determinados relatórios demorou demasiado tempo a abrir e às vezes seria bloqueado.

Na aplicação, o administrador do Power BI pode utilizar o **durações de consulta** visual para determinar os conjuntos de dados de pior desempenho a ordenação de conjuntos de dados por descendentes **duração média**. Este elemento visual também mostra conjunto de dados de contagens de consultas, para que possa ver a frequência com que os conjuntos de dados são consultados.

![Conjuntos de dados de pior desempenho](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

O administrador pode consultar o **distribuição de duração de consulta** visual, que mostra uma distribuição geral de desempenho de consultas agrupados (< = 30ms, 0-100 MS) para o período de tempo filtrado. Em geral, as consultas que demoram um segundo ou menos são considerados responsiva pela maioria dos usuários; consultas que demoram mais tempo tendem a criar uma percepção de desempenho ruim.

O **distribuição de duração de consulta por hora** visual permite ao administrador do Power BI identificar períodos de uma hora quando o desempenho de capacidade pode ter sido percebido tão ruim. Quanto maior for a barra de segmentos essa consulta representam durações num segundo, quanto maior o risco de que os usuários passarão a fraco desempenho.

O elemento visual é interativo e, quando um segmento da barra de está selecionado, o correspondente **durações de consulta** visual na página do relatório de tabela é um filtro para mostrar os conjuntos de dados representa. Esta filtragem cruzada permite que o administrador do Power BI para o identificar facilmente que os conjuntos de dados estão a responder lentamente.

A imagem seguinte mostra um elemento visual filtrado pela **distribuições de duração de consulta por hora**, concentrando-se nos conjuntos de dados de pior desempenho nos registos de uma hora. 

![Filtrado por hora distribuições de duração de consulta visual mostra o pior realização de conjuntos de dados](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Depois do conjunto de dados de desempenho fraco num intervalo de tempo específico de uma hora for identificado, o administrador do Power BI pode investigar se fraco desempenho é causado por uma capacidade sobrecarregada ou devido a um projetado o conjunto de dados ou relatório. Eles podem referir-se para o **tempos de espera de consultas** visual e conjuntos de dados de ordenação descendente de tempo de espera médio de consulta. Se está à espera que uma grande porcentagem de consultas, uma procura elevada para o conjunto de dados é, provavelmente, a causa de esperas de consulta demasiados. Se a consulta de média de tempo de espera é substancial (> 100 ms), poderá ser útil rever o conjunto de dados e o relatório para ver se as otimizações podem ser feitas. Por exemplo, elementos visuais de menos com páginas de relatório ou um recurso de otimização de expressão DAX.

![O elemento visual de tempos de espera de consultas ajuda a revelar com mau desempenho de conjuntos de dados](media/service-premium-capacity-scenarios/query-wait-times.png)

Existem vários motivos possíveis para acumulação de tempo de espera de consulta em conjuntos de dados:

- Um design de modelo inferior ao ideal, expressões de medida ou até mesmo design de relatórios - todas as circunstâncias que podem contribuir para consultas que consomem altos níveis de CPU de longa execução. Isso força novas consultas a aguardar até que os threads de CPU se tornarem disponíveis e podem criar um efeito de comboio (confusão de processamento de tráfego), normalmente observado durante o horário de pico. O **esperas de consulta** página vai ser o principal recurso para determinar se os conjuntos de dados tem tempos de espera médio de consulta elevado.
- Um elevado número de utilizadores de capacidade em simultâneo (centenas a milhares) consumir o mesmo relatório ou conjunto de dados. Ainda bem projetados de conjuntos de dados podem efetuar incorretamente para além de um limiar de simultaneidade. Isso normalmente é indicado por um único conjunto de dados que mostra um valor substancialmente mais alto para a conta de consulta que outros show de conjuntos de dados (por exemplo, de 300 mil consultas para um conjunto de dados em comparação com < 30 mil consultas para todos os outros conjuntos de dados). Em algum ponto as esperas de consulta para este conjunto de dados será iniciado escalonar, que pode ser visto na **durações de consulta** visual.
- Muitos diferentes conjuntos de dados consultados ao mesmo tempo, causar degradação como conjuntos de dados com frequência ciclo dentro e fora de memória. Isso resulta em utilizadores com um desempenho lento quando o conjunto de dados é carregado na memória. Para confirmar, o administrador do Power BI pode referir-se para o **Expulsões de conjunto de dados por hora e o consumo de memória** visual, que pode indicar que um elevado número de conjuntos de dados carregados na memória estão a ser repetidamente expulso.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificar as causas para esporadicamente lento de resposta conjuntos de dados

Neste cenário, uma investigação começou quando os utilizadores descrito que elementos visuais do relatório às vezes demoravam responder ou podem deixar de responder, mas outras vezes foram aceitável pela capacidade de resposta.

Na aplicação, o **durações de consulta** seção foi usada para localizar o conjunto de dados culpado da seguinte forma:

- Na **durações de consulta** visual administrador filtrado de conjunto de dados por conjunto de dados (começando em conjuntos de dados principais consultados) e examinado as barras filtradas cruzadas no **por hora de consulta de distribuições** visual.
- Quando uma única barra de uma hora mostrou alterações significativas no rácio entre todos os grupos de duração de consulta vs. outras barras de uma hora para esse conjunto de dados (por exemplo, as taxas entre as cores altera drasticamente), significa que este conjunto de dados demonstrou uma alteração de esporádica no desempenho.
- As barras de uma hora, que mostra uma parte irregular de consultas com desempenho ruins, indicado um intervalo de tempo em que esse conjunto de dados foi afetado por um efeito de vizinhos ruidosos, causado por atividades de outros conjuntos de dados.

A imagem abaixo mostra uma hora no dia 30 de Janeiro, em que ocorreu uma infeliz significativo no desempenho de um conjunto de dados, indicado pelo tamanho do "(3,10s]"execução bucket de duração. Clicando nessa barra de uma hora revela a todos os conjuntos de dados carregados na memória durante esse tempo, através de conjuntos de dados possíveis, fazendo com que o efeito de vizinhos ruidosos.

![Barra mostrando o pior desempenho por uma grande parte](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Depois de um intervalo de tempo problemático é identificado (por exemplo, durante 30 de Janeiro na imagem acima) administrador do Power BI pode remover todos os filtros de conjunto de dados, em seguida, filtrar apenas por esse período de tempo para determinar quais conjuntos de dados foram consultados ativamente durante este período. O conjunto de dados de culpado para o efeito de vizinhos ruidosos normalmente é o conjunto de dados consultado superior ou um com o maior duração média da consulta.

Uma solução para esse problema pode ser distribuir o culpado conjuntos de dados ao longo de áreas de trabalho diferentes em diferentes capacidades Premium, ou na capacidade partilhada, se o tamanho do conjunto de dados, requisitos de consumo e dados de padrões de atualização são suportados.

O inverso poderá ser verdadeiro também. O administrador do Power BI pode identificar quando um conjunto de dados de desempenho de consulta melhora drasticamente e, em seguida, procure o que desapareceu. Se determinadas informações estão em falta nesse ponto, que pode ajudar a apontar para o problema que.

## <a name="determining-whether-there-is-enough-memory"></a>Determinar se existe memória suficiente

Para determinar se existe memória suficiente para a capacidade de concluir as suas cargas de trabalho, o administrador do Power BI pode referir-se para o **percentagens de memória consumida** visual no **conjuntos de dados** separador da aplicação. **Todos os** (total) de memória representa a memória utilizada pelas conjuntos de dados carregados na memória, independentemente se estão ativamente consultados ou processados. **Active Directory** memória representa a memória utilizada pelas conjuntos de dados que estão a ser processados ativamente.

Numa capacidade de bom estado de funcionamento o elemento visual terá um aspeto semelhante esta, que mostra uma lacuna entre todos os (total) e a memória do Active Directory:

![Uma capacidade de bom estado de funcionamento mostrará uma lacuna entre todos os (total) e a memória do Active Directory](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Numa capacidade de ter a pressão de memória, o mesmo elemento visual mostrará claramente memória Active Directory e a memória total convergir, que significa que não é possível carregar conjuntos de dados adicionais na memória, em seguida. Neste caso, o administrador do Power BI pode clicar em **capacidade reinicie** (no **opções avançadas** da área de definições de capacidade do portal de administração). Reiniciar os resultados de capacidade em todos os conjuntos de dados que está a ser liberadas da memória e permitindo-lhes recarregar na memória conforme necessário (por atualização de dados ou de consultas).

![* * Ativo * * memória a ser convergido com * * * * de todos os memória](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Determinar se existe suficiente CPU

Em geral, a utilização de CPU média de uma capacidade deve permanecer inferior a 80%. Exceder este valor significa que a capacidade está a aproximar-se o saturação de CPU.

Efeitos de saturação de CPU são expressos por operações a demorar mais tempo do que deveriam, devido a capacidade de executar muitos comutadores de contextos de CPU, como ele tenta processar todas as operações. Numa capacidade Premium com um elevado número de consultas em simultâneo, isso é indicado por tempos de espera de consulta elevado. Uma conseqüência de tempos de espera de consulta elevado é a capacidade de resposta mais lenta do que o habitual. O administrador do Power BI possa identificar facilmente quando a CPU está saturada visualizando os **distribuições de tempo de espera por hora consulta** visual. Contagens indicam potencial saturação de CPU de tempo de espera de picos periódicos da consulta.

![Contagens indicam potencial saturação de CPU de tempo de espera de picos periódicos da consulta](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Um padrão semelhante às vezes, pode ser detetado no operações em segundo plano, se eles contribuem para a saturação de CPU. Um administrador do Power BI, pode procurar um pico periódico em horas de atualização para um conjunto de dados específico, o que pode indicar a saturação de CPU no momento (provavelmente devido a outras atualizações de conjunto de dados em curso e/ou consultas interativas). Neste caso, referir-se para o **sistema** vista na aplicação pode não necessariamente revelar que a CPU está a 100%. O **sistema** vista apresenta médias por hora, mas a CPU pode se tornar saturada durante vários minutos de operações pesadas, que aparece como picos em tempos de espera.

Existem nuances mais a ver o efeito de saturação de CPU. Embora o número de consultas que aguardam seja importante, o tempo de espera de consulta será sempre acontece até certo ponto sem causar degradação do desempenho discernable. Alguns conjuntos de dados (com mais demorado tempo médio de consulta, que indica o tamanho ou complexidade) são mais propensos aos efeitos de saturação de CPU do que outras. Para identificar facilmente estes conjuntos de dados, o administrador do Power BI pode procurar alterações da composição de cores das barras no **distribuição de tempo de espera por hora** visual. Depois de detetar uma barra de exceção, podem procurar os conjuntos de dados que tinha esperas de consulta durante esse período e também observar o tempo de espera de média de consulta em comparação comparado a duração de consulta média. Quando essas duas métricas são da mesma magnitude e a carga de trabalho de consulta para o conjunto de dados não é simples, é provável que o conjunto de dados é afetado por CPU insuficiente.

Esse efeito de mensagens em fila pode ser especialmente evidente quando um conjunto de dados é consumido em curtos picos de elevada frequência consultas por vários utilizadores (por exemplo, numa sessão de treinamento), resultando em saturação de CPU durante cada rajada. Neste caso, podem encontrar tempos de espera significativo consulta neste conjunto de dados, bem como a afetar outros conjuntos de dados na capacidade (efeito de vizinhos ruidosos).

Em alguns casos, os administradores do Power BI podem solicitar que os proprietários de conjunto de dados, criar um menor carga de trabalho de consulta volátil através da criação de um dashboard (atualizar as consultas periodicamente com qualquer conjunto de dados para os mosaicos em cache), em vez de um relatório. Isso pode ajudar a evitar picos, quando o dashboard é carregado. Esta solução pode não será sempre possível devido a requisitos empresariais, mas pode ter um método eficaz para evitar a saturação de CPU, sem ter que fazer a alteração para o conjunto de dados.

## <a name="acknowledgements"></a>Confirmações

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e especialista no Power BI independente com [soluções totalmente](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Monitorizar capacidades Premium com a aplicação](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Capacidades de monitorização no portal de administração](service-admin-premium-monitor-portal.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||