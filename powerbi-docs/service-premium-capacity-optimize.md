---
title: Otimizar as capacidades Premium do Microsoft Power BI
description: Descreve estratégias de otimização das capacidades Premium do Power BI.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: d2e8ede356ed015c4c35b311ca58d35366324b9a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871923"
---
# <a name="optimizing-premium-capacities"></a>Otimizar as capacidades Premium

Quando surgem problemas de desempenho da capacidade Premium, uma primeira abordagem comum é otimizar ou ajustar as suas soluções para restaurar tempos de resposta aceitáveis. A lógica consiste em evitar a compra de capacidade Premium adicional, a menos que seja justificada.

Quando é necessária capacidade Premium adicional, há duas opções descritas neste artigo:

- Aumentar verticalmente uma capacidade Premium existente
- Adicionar uma nova capacidade Premium

Por fim, as abordagens de teste e o dimensionamento da capacidade Premium concluem este artigo.

## <a name="best-practices"></a>Melhores práticas

Ao tentar obter a melhor utilização e desempenho, existem algumas melhores práticas recomendadas, incluindo:

- A utilização de áreas de trabalho em vez de áreas de trabalho pessoais.
- A separação de crítico para empresas e BI com gestão personalizada (SSBI) em diferentes capacidades.

  ![Separação de crítico para empresas e BI com gestão personalizada em diferentes capacidades](media/service-premium-capacity-optimize/separate-capacities.png)

- Se estiver a partilhar conteúdos apenas com utilizadores do Power BI Pro, talvez não seja necessário armazenar o conteúdo numa capacidade dedicada.
- Utilize capacidades dedicadas ao procurar atingir um tempo de atualização específico ou quando forem necessárias funcionalidades específicas. Por exemplo, com conjuntos de dados de grandes dimensões ou relatórios paginados.

### <a name="addressing-common-questions"></a>Resposta a perguntas comuns

A otimização de implementações do Power BI Premium é um assunto complexo que envolve uma compreensão dos requisitos de carga de trabalho, dos recursos disponíveis e da sua utilização efetiva.

Este artigo aborda sete perguntas comuns de suporte e descreve possíveis problemas e explicações, juntamente com informações sobre como identificar e resolver os problemas.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Por que motivo está a capacidade lenta e o que posso fazer?

Existem várias razões que podem contribuir para uma capacidade Premium lenta. Esta pergunta requer mais informações para esclarecer o significado de "lenta". O carregamento dos relatórios é lento? Ou não estão a ser carregados? Os elementos visuais do relatório estão a demorar a carregar ou atualizar quando os utilizadores interagem com o relatório? As atualizações estão a demorar mais tempo a concluir do que o esperado, ou do que anteriormente?

Ao compreender o motivo, pode começar a investigar. As respostas às seis perguntas seguintes vão ajudá-lo a resolver problemas mais específicos.

### <a name="what-content-is-using-up-my-capacity"></a>Que conteúdos estão a utilizar toda a minha capacidade?

Pode utilizar a aplicação **Power BI Premium Capacity Metrics** para filtrar por capacidade e analisar as métricas de desempenho do conteúdo da área de trabalho. É possível analisar as métricas de desempenho e a utilização de recursos por hora nos últimos sete dias para todos os conteúdos armazenados numa capacidade Premium. A monitorização é geralmente o primeiro passo necessário para resolver um problema geral sobre o desempenho da capacidade Premium.

As principais métricas a monitorizar incluem:

- CPU média e contagem de utilização elevada.
- Memória média e contagem de utilização elevada, e utilização da memória para conjuntos de dados, fluxos de dados e relatórios paginados específicos.
- Conjuntos de dados ativos carregados na memória.
- Durações média e máxima de consulta.
- Tempos médios de espera das consultas.
- Tempos médios de atualização de conjuntos de dados e fluxos de dados.

Na aplicação Power BI Premium Capacity Metrics, a memória ativa mostra a quantidade total de memória atribuída a um relatório que não pode ser expulso porque foi utilizado nos últimos três minutos. Um pico elevado no tempo de espera da atualização pode estar correlacionado com um conjunto de dados grande e/ou ativo.

O gráfico **Primeiros Cinco Conjuntos de Dados por Duração Média** realça os cinco principais conjuntos de dados, relatórios paginados e fluxos de dados que consomem recursos da capacidade. Os conteúdos nas listas dos primeiros cinco apresenta candidatos à investigação e possível otimização.

### <a name="why-are-reports-slow"></a>Por que motivo estão os relatórios lentos?

As tabelas seguintes mostram possíveis problemas e maneiras de identificá-los e tratá-los.

#### <a name="insufficient-capacity-resources"></a>Recursos de capacidade insuficientes

| Explicações Possíveis | Como Identificar | Como Resolver |
| --- | --- | --- |
| Memória ativa total elevada (o modelo não pode ser expulso porque foi utilizado nos últimos três minutos).<br><br> Múltiplos picos elevados nos tempos de espera da consulta.<br><br> Múltiplos picos elevados nos tempos de espera da atualização. | Monitorize as métricas de memória \[[1](#endnote-1)\] e as contagens da exclusão \[[2](#endnote-2)\]. | Diminua o tamanho do modelo ou converta para o modo DirectQuery. Veja a secção [Otimização de modelos](#optimizing-models) neste artigo.<br><br> Aumente verticalmente a capacidade.<br><br> Atribua o conteúdo a uma capacidade diferente. |

#### <a name="inefficient-report-designs"></a>Designs de relatório ineficientes

| Explicações Possíveis | Como Identificar | Como Resolver |
| --- | --- | --- |
| As páginas do relatório contêm demasiados elementos visuais (a filtragem interativa pode desencadear, pelo menos, uma consulta por elemento visual).<br><br> Os elementos visuais obtêm mais dados do que os necessários. | Analise os designs de relatório.<br><br> Fale com os utilizadores dos relatórios para compreender de que forma interagem com os mesmos.<br><br> Monitorize as métricas de consulta de conjuntos de dados \[[3](#endnote-3)\]. | Recrie relatórios com menos elementos visuais por página. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>O conjunto de dados está lento, especialmente em relatórios que tiveram um bom desempenho no passado

| Explicações Possíveis | Como Identificar | Como Resolver |
| --- | --- | --- |
| Volumes cada vez maiores de dados de importação.<br><br> Lógica de cálculo complexa ou ineficiente, incluindo funções de RLS.<br><br> Modelo não totalmente otimizado.<br><br> (DQ/LC) Latência do gateway.<br><br> Tempos de resposta de consulta da origem do DQ lentos. | Analise os designs de modelo.<br><br> Monitorize os contadores de desempenho de gateways. | Veja a secção [Otimização de modelos](#optimizing-models) neste artigo. |

#### <a name="high-concurrent-report-usage"></a>Utilização simultânea de relatórios elevada

| Explicações Possíveis | Como Identificar | Como Resolver |
| --- | --- | --- |
| Tempos de espera das consultas elevados.<br><br> Saturação da CPU.<br><br> Limites de ligação DQ/LC excedidos. | Monitorize as métricas de utilização da CPU \[[4](#endnote-4)\], os tempos de espera das consultas e a utilização do DQ/LC \[[5](#endnote-5)\] + durações das consultas. Uma oscilação pode indicar problemas de simultaneidade. | Aumente verticalmente a capacidade ou atribua o conteúdo a uma capacidade diferente.<br><br> Recrie relatórios com menos elementos visuais por página. |

**Notas:**    
<a name="endnote-1"></a>\[1\] Utilização Média da Memória (GB) e Consumo de Memória Mais Elevado (GB).   
<a name="endnote-2"></a>\[2\] Expulsões de conjuntos de dados.   
<a name="endnote-3"></a>\[3\] Consultas de Conjuntos de Dados, Duração Média de Consulta do Conjunto de Dados (ms), Contagem de Espera do Conjunto de Dados e Tempo de Espera Médio do Conjunto de Dados (ms).   
<a name="endnote-4"></a>\[4\] Contagem de Utilização Elevada da CPU e Tempo de Utilização Mais Elevada da CPU (últimos sete dias).   
<a name="endnote-5"></a>\[5\] Contagem de Utilização Elevada do DQ/LC e Tempo de Utilização Mais Elevada do DQ/LC (últimos sete dias).   

### <a name="why-are-reports-not-loading"></a>Por que motivo é que os relatórios não estão a carregar?

Quando os relatórios não são carregados, é um sinal evidente de que a capacidade não tem memória suficiente e está a ser excessivamente utilizada. Isto pode ocorrer quando todos os modelos carregados estão a ser consultados ativamente e, portanto, não podem ser expulsos e todas as operações de atualização foram interrompidas ou atrasadas. O serviço Power BI tentará carregar o conjunto de dados durante 30 segundos e o utilizador será notificado normalmente sobre a falha com uma sugestão para tentar novamente em breve.

Atualmente, não existe nenhuma métrica para monitorizar falhas de carregamento de relatórios. Pode identificar o potencial deste problema ao monitorizar a memória do sistema, especificamente, a maior utilização e o tempo de maior utilização. Expulsões de conjuntos de dados elevadas e um tempo de espera médio de atualização de conjuntos de dados longo podem sugerir que este problema está a ocorrer.

Se isto ocorrer apenas ocasionalmente, pode não ser considerado um problema de prioridade. Os utilizadores de relatórios são informados de que o serviço está ocupado e que devem tentar novamente após um curto período. Se isto ocorrer com muita frequência, o problema poderá ser resolvido ao expandir a capacidade Premium ou atribuir o conteúdo a uma capacidade diferente.

Os Administradores de Capacidade (e os administradores do serviço Power BI) podem monitorizar a métrica **Falhas de Consulta** para determinar quando isto acontece. Podem também reiniciar a capacidade, ao repor todas as operações em caso de sobrecarga do sistema.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Por que motivo é que as atualizações não são iniciadas na devida altura?

As horas de início da atualização agendada não são garantidas. Lembre-se de que o serviço Power BI irá sempre priorizar operações interativas acima de operações em segundo plano. A atualização é uma operação em segundo plano que pode ocorrer quando duas condições estão reunidas:

- Há memória suficiente
- O número de atualizações simultâneas suportadas para a capacidade Premium não é excedido

Se as condições não forem reunidas, a atualização será colocada em fila de espera até que as condições sejam favoráveis.

Para uma atualização completa, lembre-se de que é necessário, pelo menos, o dobro do tamanho da memória do conjunto de dados atual. Se não estiver disponível memória suficiente, a atualização não poderá ser iniciada até que a expulsão do modelo liberte memória – isto significa atrasos até que um ou mais conjuntos de dados se tornem inativos e possam ser expulsos.

Lembre-se de que o número suportado de atualizações simultâneas máximas é definido como 1,5 vezes os núcleos virtuais de back-end, arredondados.

Uma atualização agendada irá falhar quando não for possível iniciar antes do início da atualização agendada seguinte. Uma atualização a pedido acionada manualmente a partir da IU irá tentar executar até três vezes antes de falhar.

Os Administradores de Capacidade (e os administradores do serviço Power BI) podem monitorizar a métrica **Tempo Médio de Espera de Atualização (minutos)** para determinar o atraso médio entre a hora agendada e o início da operação.

Embora não seja normalmente uma prioridade administrativa, para conseguir atualizações de dados atempadas, certifique-se de que está disponível memória suficiente. Isto pode envolver o isolamento de conjuntos de dados para capacidades com recursos suficientes conhecidos. Também é possível que os administradores possam coordenar com os proprietários dos conjuntos de dados para ajudar a escalonar ou reduzir os tempos de atualização de dados agendados de modo a minimizar colisões. Tenha em atenção que não é possível que um administrador veja a fila de atualização ou obtenha as agendas de conjuntos de dados.

### <a name="why-are-refreshes-slow"></a>Por que motivo é que as atualizações estão lentas?

As atualizações podem ser lentas ou observadas como lentas (como aborda a pergunta comum anterior).

Quando a atualização é, de facto, lenta, pode ser devido a vários motivos:

- CPU insuficiente (a atualização pode utilizar a CPU de forma intensiva).
- Memória insuficiente, o que resulta na pausa da atualização (que exige que a atualização seja reiniciada quando as condições forem favoráveis para tal).
- Motivos não relacionados com capacidade, incluindo a capacidade de resposta do sistema da origem de dados, a latência de rede, as permissões inválidas ou o débito do gateway.
- Volume de dados – um bom motivo para configurar a atualização incremental, conforme mencionado abaixo.

Os Administradores de Capacidade (e os administradores do serviço Power BI) podem monitorizar a métrica **Duração Média de Atualização (minutos)** para determinar uma referência para comparação ao longo do tempo e as métricas **Tempo Médio de Espera de Atualização (minutos)** para determinar o atraso médio entre a hora agendada e o início da operação.

A atualização incremental pode reduzir significativamente a duração da atualização de dados, especialmente para grandes tabelas de modelos. Existem quatro benefícios associados à atualização incremental:

- **As atualizações são mais rápidas** – apenas um subconjunto de uma tabela precisa de ser carregado, ao reduzir a utilização da CPU e da memória e o paralelismo pode ser superior ao atualizar várias partições.
- **As atualizações ocorrem apenas quando necessário** – as políticas de atualização incremental podem ser configuradas para carregar apenas quando os dados forem alterados.
- **As atualizações são mais fiáveis** – as ligações de execução mais curtas para os sistemas de origem de dados voláteis são menos suscetíveis à interrupção da ligação.
- **Os modelos permanecem reduzidos** – as políticas de atualização incremental podem ser configuradas para remover automaticamente o histórico além de uma janela deslizante de tempo.

Para saber mais, veja [Atualização incremental no Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Por que motivo é que as atualizações de dados não estão a ser concluídas?

Quando a atualização de dados começa, mas não é concluída, tal pode dever-se a vários motivos:

- Memória insuficiente, mesmo que exista apenas um modelo na capacidade Premium, ou seja, o tamanho do modelo é muito grande.
- Motivos não relacionados com capacidade, incluindo a interrupção da ligação do sistema da origem de dados, as permissões inválidas ou o erro do gateway.

Os Administradores de Capacidade (e os administradores do serviço Power BI) podem monitorizar a métrica **Falhas de Atualização devido a Memória Insuficiente**.

## <a name="optimizing-models"></a>Otimizar modelos

O design de modelo ideal é crucial para a entrega de uma solução eficiente e dimensionável. No entanto, está fora do âmbito deste artigo fornecer uma análise completa. Em vez disso, esta secção vai fornecer as principais áreas a considerar ao otimizar modelos.

### <a name="optimizing-power-bi-hosted-models"></a>Otimizar modelos alojados no Power BI

A otimização de modelos alojados numa capacidade Premium pode ser obtida nas camadas de origem(ns) de dados e modelos.

Considere as possibilidades de otimização de um modelo de importação:

![Possibilidades de otimização de um modelo de importação](media/service-premium-capacity-optimize/import-model-optimizations.png)

Na camada de origem de dados:

- As origens de dados relacionais podem ser otimizadas para garantir a atualização mais rápida possível através da pré-integração dos dados, ao aplicar os índices apropriados, definir as partições de tabela que se alinham com os períodos de atualização incremental e materializar os cálculos (no lugar de tabelas e colunas calculadas do modelo) ou adicionar lógica de cálculo a visualizações.
- As origens de dados não relacionais podem ser previamente integradas em arquivos relacionais.
- Certifique-se de que os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em grande proximidade das origens de dados.

Na camada de modelo:

- Os designs de consulta do Power Query podem minimizar ou remover transformações complexas e, especialmente, aquelas que unem diferentes origens de dados (os armazéns de dados atingem-no durante a fase de extração, transformação e carregamento). Além disso, garantir que os níveis de privacidade adequados da origem de dados estão definidos, pode evitar a necessidade de o Power BI carregar resultados completos para produzir um resultado combinado entre consultas.
- A estrutura do modelo determina os dados a carregar e tem um impacto direto no tamanho do modelo. Pode ser concebido para evitar o carregamento de dados desnecessários ao remover colunas, linhas (especialmente dados históricos) ou carregar dados resumidos (às custas de carregar dados detalhados). A redução drástica de tamanho pode ser efetuada ao remover colunas de alta cardinalidade (especialmente colunas de texto) que não são armazenadas ou compactadas com muita eficiência.
- O desempenho de consulta de modelo pode ser melhorado ao configurar relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Considere também utilizar a função [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function), em vez da filtragem bidirecional.
- As tabelas de agregação podem obter respostas de consulta rápidas ao carregar dados previamente resumidos, no entanto, isto vai aumentar o tamanho do modelo e resultar em tempos de atualização mais longos. Geralmente, as tabelas de agregação devem ser reservadas para modelos muito grandes ou designs de modelo composto.
- As tabelas e colunas calculadas aumentam o tamanho do modelo e resultam em tempos de atualização mais longos. Geralmente, um tamanho de armazenamento menor e um tempo de atualização mais rápido podem ser obtidos quando os dados são materializados ou calculados na origem de dados. Se tal não for possível, utilizar as colunas personalizadas do Power Query pode oferecer uma compactação de armazenamento melhorada.
- Pode haver oportunidade de ajustar expressões DAX para medidas e regras de RLS, talvez ao reescrever a lógica para evitar fórmulas caras
- A atualização incremental pode reduzir drasticamente o tempo de atualização e conservar a memória e a CPU. A atualização incremental também pode ser configurada para remover os dados históricos enquanto mantém os tamanhos de modelo reduzidos.
- Um modelo pode ser reestruturado como dois modelos quando existem padrões de consulta diferentes e em conflito. Por exemplo, alguns relatórios apresentam agregações de alto nível sobre todo o histórico e podem tolerar uma latência de 24 horas. Outros relatórios dizem respeito aos dados de hoje e precisam de acesso granular a transações individuais. Em vez de criar um único modelo para satisfazer todos os relatórios, crie dois modelos otimizados para cada requisito.

Considere as possibilidades de otimização para um modelo do DirectQuery. Como o modelo emite pedidos de consulta para a origem de dados subjacente, a otimização da origem de dados é essencial para fornecer consultas de modelo reativas.

 ![Possibilidades de otimização para um modelo do DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Na camada de origem de dados:

- A origem de dados pode ser otimizada para garantir a consulta mais rápida possível através da integração antecipada dos dados (o que não é possível na camada do modelo), aplicação dos índices apropriados, definição de partições de tabela, materialização de dados resumidos (com vistas indexadas) e minimização da quantidade de cálculos. A melhor experiência é obtida quando as consultas pass-through precisam apenas de filtrar e executar associações internas entre tabelas ou vistas indexadas.
- Certifique-se de que os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em grande proximidade da origem de dados.

Na camada de modelo:

- Os designs de consulta do Power Query não devem, de preferência, aplicar transformações – caso contrário, tente manter as transformações num mínimo absoluto.
- O desempenho de consulta de modelo pode ser melhorado ao configurar relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Além disso, as relações de modelo devem ser configuradas para assumir que a integridade referencial é imposta (quando for esse o caso) e resultará em consultas de origem de dados através da utilização de associações internas mais eficientes (em vez de associações externas).
- Evite criar colunas personalizadas de consulta ou coluna calculada do modelo do Power Query – materialize-as na origem de dados, quando possível.
- Pode haver oportunidade de ajustar expressões DAX para medidas e regras de RLS, talvez ao reescrever a lógica para evitar fórmulas caras.

Considere as possibilidades de otimização de um modelo composto. Não se esqueça que um modelo composto permite uma combinação de tabelas de importação e do DirectQuery.

![Possibilidades de otimização para um modelo composto](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Geralmente, a otimização de modelos de importação e do DirectQuery aplica-se a tabelas de modelo composto que utilizam estes modos de armazenamento.
- Normalmente, procure obter um design equilibrado ao configurar tabelas de dimensão (que representam entidades empresariais) como o modo de armazenamento duplo e tabelas de factos (muitas vezes, tabelas grandes, que representam factos operacionais) como o modo de armazenamento DirectQuery. O modo de armazenamento duplo significa ambos os modos de armazenamento de importação e DirectQuery, e isto permite que o serviço Power BI determine o modo de armazenamento mais eficiente a ser utilizado ao gerar uma consulta nativa para pass-through.
- Certifique-se de que os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em grande proximidade das origens de dados.
- As tabelas de agregações configuradas como modo de armazenamento de importação podem fornecer melhorias consideráveis no desempenho de consulta quando utilizadas para resumir tabelas de factos do modo de armazenamento DirectQuery. Neste caso, as tabelas de agregação vão aumentar o tamanho do modelo e o tempo de atualização. Esta é, muitas vezes, uma troca aceitável para obter consultas mais rápidas.

### <a name="optimizing-externally-hosted-models"></a>Otimizar modelos alojados externamente

Muitas das possibilidades de otimização analisadas na secção [Otimizar modelos alojados no Power BI](#optimizing-power-bi-hosted-models) aplicam-se também a modelos desenvolvidos com o Azure Analysis Services e o SQL Server Analysis Services. As exceções claras são determinadas funcionalidades que não são atualmente suportadas, incluindo modelos compostos e tabelas de agregação.

Uma consideração adicional para conjuntos de dados alojados externamente é o alojamento da base de dados em relação ao serviço Power BI. Para o Azure Analysis Services, isto significa criar o recurso do Azure na mesma região que o inquilino do Power BI (região de residência). Para o SQL Server Analysis Services, para IaaS, isto significa alojar a VM na mesma região e, para o local, isto significa garantir uma configuração de gateway eficiente.

Além disso, pode ser interessante observar que as bases de dados do Azure Analysis Services e as bases de dados tabulares do SQL Server Analysis Services exigem que os seus modelos sejam carregados totalmente na memória e que permaneçam ali sempre para dar suporte à consulta. Assim como o serviço Power BI, tem de haver memória suficiente para atualizar, caso o modelo tenha de permanecer online durante a atualização. Ao contrário do serviço Power BI, não existe o conceito de que os modelos sejam automaticamente colocados e retirados da memória de acordo com a utilização. Desse modo, o Power BI Premium oferece uma abordagem mais eficiente para maximizar a consulta de modelos com menor utilização da memória.

## <a name="capacity-planning"></a>Planeamento de capacidade

O tamanho de uma capacidade Premium determina a sua memória disponível e os limites e recursos de processamento impostos sobre a capacidade. O número de capacidades Premium também é algo a considerar, uma vez que a criação de várias capacidades Premium pode ajudar a isolar as cargas de trabalho umas das outras. Observe que o armazenamento é de 100 TB por nó de capacidade e isto será provavelmente mais do que suficiente para qualquer carga de trabalho.

Determinar o tamanho e o número das capacidades Premium pode ser desafiante, especialmente para as capacidades iniciais que criar. A primeira etapa do dimensionamento da capacidade consiste em compreender a carga de trabalho média que representa a utilização diária esperada. É importante compreender que nem todas as cargas de trabalho são iguais. Por exemplo, por um lado, o acesso simultâneo de 100 utilizadores a uma única página de relatório que contém um único elemento visual é facilmente alcançável. Porém, por outro lado, o acesso simultâneo de 100 utilizadores a 100 relatórios diferentes, cada um com 100 elementos visuais na página de relatório, tem exigências muito diferentes dos recursos de capacidade.

Portanto, os Administradores de Capacidade terão de considerar muitos fatores específicos ao seu ambiente, conteúdos e utilização esperada. O objetivo prioritário consiste em maximizar a utilização da capacidade e, ao mesmo tempo, fornecer tempos de consulta consistentes, tempos de espera aceitáveis e taxas de expulsão. Os fatores a considerar podem incluir:

- **Características de dados e tamanho do modelo** – os modelos de importação devem ser totalmente carregados na memória para permitir a consulta ou atualização. Os conjuntos de dados de LC/DQ podem exigir um tempo de processamento significativo e, possivelmente, uma quantidade de memória substancial para avaliar medidas complexas ou regras de RLS. O tamanho da memória e do processador, bem como o débito de consultas de LC/DQ são restritos pelo tamanho da capacidade.
- **Modelos ativos simultâneos** – a consulta simultânea de diferentes modelos de importação irá proporcionar uma melhor capacidade de resposta e desempenho quando os mesmos permanecem na memória. Deve existir memória suficiente para alojar todos os modelos de consulta intensa, com memória adicional para permitir a sua atualização.
- **Atualização de modelos de importação** – o tipo de atualização (completa ou incremental), a duração e a complexidade das consultas do Power Query, e a lógica de tabela/coluna calculada podem afetar a memória e, principalmente, a utilização do processador. As atualizações simultâneas são restritas pelo tamanho da capacidade (1,5 x núcleos virtuais de back-end, arredondado).
- **Consultas simultâneas** – muitas consultas simultâneas podem resultar em relatórios sem resposta quando as ligações de processador ou LC/DQ excedem o limite da capacidade. Isto adequa-se especialmente a páginas de relatório que incluem muitos elementos visuais.
- **Fluxos de dados e relatórios paginados** – a capacidade pode ser configurada para dar suporte a fluxos de dados e relatórios paginados, cada um a exigir uma percentagem máxima configurável de memória da capacidade. A memória é alocada aos fluxos de dados de forma dinâmica, mas é alocada aos relatórios paginados de forma estática.

Além destes fatores, os Administradores de Capacidade podem considerar a criação de múltiplas capacidades. Múltiplas capacidades permitem o isolamento de cargas de trabalho e podem ser configuradas para garantir que as cargas de trabalho prioritárias têm recursos garantidos. Por exemplo, podem ser criadas duas capacidades para separar cargas de trabalho críticas para empresas de cargas de trabalho de BI de gestão personalizada (SSBI). A capacidade crítica para empresas pode ser utilizada para isolar grandes modelos corporativos, ao fornecer-lhes recursos garantidos, com o acesso de criação concedido apenas ao departamento de TI. A capacidade do SSBI pode ser utilizada para alojar um número cada vez maior de modelos menores, com acesso concedido a analistas empresariais. A capacidade SSBI pode, por vezes, apresentar esperas de consulta ou atualização toleráveis.

Ao longo do tempo, os Administradores de Capacidade podem equilibrar as áreas de trabalho entre capacidades, ao moverem os conteúdos entre áreas de trabalho ou áreas de trabalho entre capacidades e ao aumentar ou reduzir as capacidades verticalmente. Geralmente, para alojar modelos maiores, deve aumentar verticalmente e para uma simultaneidade maior, deve aumentar horizontalmente.

Lembre-se de que a compra de uma licença fornece ao inquilino núcleos virtuais. A compra de uma subscrição **P3** pode ser utilizada para criar uma ou até quatro capacidades Premium, ou seja, 1 x P3 ou 2 x P2 ou 4 x P1. Além disso, antes de aumentar uma capacidade P2 para uma capacidade P3, considere dividir os núcleos virtuais para criar duas capacidades P1.

## <a name="testing-approaches"></a>Abordagens de teste

Quando o tamanho da capacidade estiver decidido, o teste pode ser executado ao criar um ambiente controlado. Uma opção prática e económica é criar uma capacidade do Azure (SKUs A), sabendo que uma capacidade P1 tem o mesmo tamanho que uma capacidade A4 e que as capacidades P2 e P3 têm o mesmo tamanho que as capacidades A5 e A6, respetivamente. As capacidades do Azure podem ser criadas rapidamente e são cobradas à hora. Assim, quando o teste for concluído, podem ser facilmente eliminadas para suspender a acumulação de custos.

Os conteúdos do teste podem ser adicionados às áreas de trabalho criadas na capacidade do Azure e, em seguida, um utilizador pode executar relatórios para gerar uma carga de trabalho de consultas realista e representativa. Se existirem modelos de importação, deve ser também efetuada uma atualização para cada modelo. As ferramentas de monitorização podem ser utilizadas para analisar todas as métricas para entender a utilização de recursos.

É importante que os testes sejam repetíveis. Os testes devem ser executados várias vezes e devem fornecer sempre resultados praticamente idênticos. Uma média destes resultados pode ser utilizada para extrapolar e estimar uma carga de trabalho em condições de produção verdadeiras.

Se já tiver uma capacidade e os relatórios para os quais pretende efetuar o teste de carga, utilize a [ferramenta de geração de carga do PowerShell](https://aka.ms/PowerBILoadTestingTool) para gerar rapidamente um teste de carga. A ferramenta permite-lhe calcular o número de instâncias de cada relatório que a sua capacidade consegue executar numa hora. Pode utilizar a ferramenta para avaliar a aptidão da capacidade para compor relatórios individuais ou compor vários relatórios diferentes em paralelo. Para obter mais informações, veja o vídeo [Microsoft Power BI: Capacidade Premium](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Para gerar um teste mais complexo, considere desenvolver uma aplicação de teste de carga que simule uma carga de trabalho realista. Para obter mais informações, veja o webinar [Load Testing Power BI Applications with Visual Studio Load Test](https://powerbi.microsoft.com/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/) (Teste de carga de Aplicações do Power BI com o Teste de Carga do Visual Studio).

## <a name="acknowledgements"></a>Agradecimentos

Este artigo foi escrito por Peter Myers, MVP de Plataforma de Dados e especialista independente de BI na [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Cenários de capacidades Premium](service-premium-capacity-scenarios.md)   
  
Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||