---
title: Otimizar as capacidades do Microsoft Power BI Premium
description: Descreve as estratégias de otimização para as capacidades do Power BI Premium.
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
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565343"
---
# <a name="optimizing-premium-capacities"></a>Otimizar as capacidades Premium

Quando surgem problemas de desempenho de capacidade Premium, uma abordagem de primeiro comum é otimizar ou otimizar as suas soluções para restaurar os tempos de resposta aceitável. A lógica era evitar a aquisição de capacidade de Premium adicional, a menos que justificada.

Quando a capacidade de Premium adicional é necessária, existem duas opções descritas neste artigo:

- Aumentar verticalmente uma capacidade Premium existente
- Adicionar uma nova capacidade Premium

Por fim, testes abordagens e dimensionamento de capacidade de Premium concluir este artigo.

## <a name="best-practices"></a>Melhores práticas

Ao tentar obter o melhor utilização e desempenho, existem algumas melhores práticas recomendadas, incluindo:

- Utilização de áreas de trabalho de aplicação em vez de áreas de trabalho pessoais.
- Separar crítico para a empresa e de BI de autoatendimento (SSBI) em diferentes capacidades.

  ![Separar crítico para a empresa e de BI de Self-Service em diferentes capacidades](media/service-premium-capacity-optimize/separate-capacities.png)

- Se a partilha de conteúdo apenas com utilizadores do Power BI Pro, poderão existir sem a necessidade de armazenar o conteúdo numa capacidade dedicada.
- Utilize as capacidades dedicadas ao analisar para conseguir um tempo de atualização específico ou quando são necessárias funcionalidades específicas. Por exemplo, com grandes conjuntos de dados ou relatórios paginados.

### <a name="addressing-common-questions"></a>Responder a questões comuns

Otimizar as implementações do Power BI Premium é um assunto complexo que envolvem uma compreensão dos requisitos de carga de trabalho, recursos disponíveis e seu uso Efetivo.

Este artigo aborda sete perguntas de suporte comuns, que descreve os possíveis problemas e explicações e informações sobre como identificar e a resolvê-los.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Por que é a capacidade lenta e que posso fazer?

Existem muitos motivos pelos quais podem contribuir para uma capacidade Premium lenta. Essa questão requer mais informações para compreender o que se entende por lenta. São relatórios lento a carregar? Ou falham ao carregar? Elementos visuais do relatório são lentas carregar ou atualizar quando os utilizadores interagem com o relatório? São atualizadas a demorar mais tempo a concluir que o esperado ou anteriormente experimentado?

Tendo obtido um entendimento do motivo, pode, em seguida, começar a investigar. As respostas às seguintes seis perguntas ajuda-o a resolver mais problemas específicos.

### <a name="what-content-is-using-up-my-capacity"></a>O conteúdo que está a utilizar a minha capacidade?

Pode utilizar o **métricas de capacidade do Power BI Premium** aplicação para filtrar por capacidade e reveja as métricas de desempenho para o conteúdo da área de trabalho. É possível rever a utilização de recursos e as métricas de desempenho por hora nos últimos sete dias para todos os conteúdos armazenados dentro de uma capacidade Premium. Monitorização, muitas vezes, é o primeiro passo a tomar quando uma preocupação geral sobre o desempenho de capacidade de Premium de resolução de problemas.

As principais métricas para monitorizar incluem:

- Média da CPU e a contagem de alta utilização.
- Média de memória e a contagem de alta utilização e a utilização de memória para conjuntos de dados específicos, fluxos de dados e relatórios paginados.
- Active Directory conjuntos de dados carregados na memória.
- Durações de consulta máxima e média.
- Tempos de espera médio de consulta.
- Conjunto de dados de média e fluxo de dados são atualizados vezes.

A aplicação de métricas de capacidade do Power BI Premium, memória Active Directory mostra a quantidade total de memória devida a um relatório que não pode ser expulsas por ter estado em utilização nos últimos três minutos. Um pico alta no tempo de espera da atualização pode ser correlacionado com um conjunto de dados grandes e/ou Active Directory.

O **Top 5 por duração média** gráfico destaca os cinco principais conjuntos de dados, relatórios paginados e consumir recursos de capacidade de fluxos de dados. Conteúdo nos cinco primeiros listas é candidatos para a otimização de investigação e possíveis.

### <a name="why-are-reports-slow"></a>Por que motivo são relatórios lento?

As tabelas seguintes mostram os possíveis problemas e formas de identificar e manipulá-las.

#### <a name="insufficient-capacity-resources"></a>Recursos de capacidade insuficiente

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| Memória total Active Directory (modelo não pode ser expulsas porque está a ser utilizado nos últimos três minutos).<br><br> Vários picos elevados na consulta Aguarde vezes.<br><br> Vários picos elevados na atualização Aguarde vezes. | Monitorizar as métricas de memória \[ [1](#endnote-1)\]e contagens de expulsão \[ [2](#endnote-2)\]. | Diminuir o tamanho do modelo ou converter para o modo DirectQuery. Consulte a [otimizar modelos](#optimizing-models) secção deste artigo.<br><br> Aumentar verticalmente a capacidade.<br><br> Atribua o conteúdo a uma capacidade diferente. |

#### <a name="inefficient-report-designs"></a>Designs de relatório ineficiente

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| Páginas de relatório contém demasiados elementos visuais (filtragem interativo pode acionar, pelo menos, uma consulta por elemento visual).<br><br> Os elementos visuais recuperar mais dados que o necessário. | Reveja os designs de relatório.<br><br> Entrevista utilizadores de relatórios para compreender a forma como interagem com os relatórios.<br><br> Monitorizar as métricas de consulta do conjunto de dados \[ [3](#endnote-3)\]. | Relatórios de reformulação com elementos visuais menos por página. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Conjunto de dados é lento, especialmente quando relatórios anteriormente efetuou bem

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| Cada vez maiores volumes de dados de importação.<br><br> Lógica de cálculo complexo ou ineficaz, incluindo funções RLS.<br><br> Modelo não totalmente otimizado.<br><br> (DQ/LC) Latência de gateway.<br><br> Lentos DQ origem consulta tempos de resposta. | Reveja os designs de modelo.<br><br> Monitorizar os contadores de desempenho do gateway. | Consulte a [otimizar modelos](#optimizing-models) secção deste artigo. |

#### <a name="high-concurrent-report-usage"></a>Utilização elevada de relatório em simultâneo

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| Tempos de espera de consulta elevado.<br><br> Saturação de CPU.<br><br> Limites de conexão de DQ/LC foi excedidos. | Monitorizar a utilização da CPU \[ [4](#endnote-4)\], tempos de espera de consulta e a utilização de DQ/LC \[ [5](#endnote-5) \] métricas + durações de consulta. Se a flutuar, pode indicar problemas de simultaneidade. | A capacidade de aumentar verticalmente, ou o atribuir o conteúdo a uma capacidade diferente.<br><br> Relatórios de reformulação com elementos visuais menos por página. |

**Notas:**    
<a name="endnote-1"></a>\[1\] média de utilização de memória (GB) e o mais alto consumo de memória (GB).   
<a name="endnote-2"></a>\[2\] Expulsões de conjunto de dados.   
<a name="endnote-3"></a>\[3\] consultas de conjunto de dados, duração de consulta de conjunto de dados de média (ms), conjunto de dados aguardar contagem e a média do conjunto de dados de tempo de espera (ms).   
<a name="endnote-4"></a>\[4\] contagem de utilização elevada da CPU e de tempo de CPU de maior utilização (últimos sete dias).   
<a name="endnote-5"></a>\[5\] DQ/LC elevada contagem de utilização e a hora DQ/LC de maior utilização (últimos sete dias).   

### <a name="why-are-reports-not-loading"></a>Por que motivo são relatórios não está carregando?

Quando não carregar relatórios, é um início de sessão-se de que a capacidade não tem memória suficiente e é excessivamente exaltada. Isto pode ocorrer quando todos os modelos de carregá-lo são ativamente a ser consultados e por isso, não podem ser expulsas e quaisquer operações de atualização foram colocadas em pausa ou atrasadas. O serviço Power BI irá tentar carregar o conjunto de dados durante 30 segundos e o utilizador com elegância é notificado da falha com uma sugestão para tentar novamente em breve.

Não existe atualmente não existem métricas para monitorizar a existência de falhas de carregamento de relatório. Pode identificar o potencial para este problema, a memória do sistema de monitorização, especificamente mais altos de utilização e de tempo de maior utilização. Expulsões de conjunto de dados de alta e longo conjunto de dados tempo de espera médio de atualização poderiam sugerir que este problema está a ocorrer.

Se isto acontecer muito ocasionalmente, isso pode não ser considerado um problema de prioridade. Utilizadores de relatórios são informados de que o serviço está ocupado e que deve repetir após um curto período de tempo. Se isto acontecer com muita frequência, pode ser resolvido o problema, aumente verticalmente a capacidade de Premium ou ao atribuir o conteúdo a uma capacidade diferente.

Os administradores de capacidade (e os administradores de serviço do Power BI) pode monitorizar o **falhas nas consultas** métrica para determinar quando isso acontece. Eles também podem reiniciar a capacidade, repor todas as operações em caso de sobrecarga de system.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Por que as atualizações não começam numa agenda?

Horas de início da atualização agendada não são garantidas. Lembre-se de que o serviço Power BI sempre priorizar operações interativas sobre operações em segundo plano. A atualização é uma operação em segundo plano que pode ocorrer quando duas condições são cumpridas:

- Não existe memória suficiente
- O número de atualizações em simultâneo suportados para a capacidade de Premium não seja excedido

Quando as condições não forem cumpridas, a atualização é colocada na fila até que as condições são favoráveis.

Para uma atualização completa, lembre-se que, pelo menos, duas vezes o tamanho de memória atual do conjunto de dados é necessária. Se não está disponível memória suficiente, a atualização não é possível começar até que a expulsão de modelo liberta memória – Isto significa atrasos até que um ou mais conjuntos de dados torna-se inativo e podem ser expulso.

Lembre-se de que o número suportado de atualizações em simultâneo máximos é definido como 1,5 vezes os back-end núcleos virtuais, arredondados.

Uma atualização agendada irão falhar quando não é possível começar a antes da próxima atualização agendada começar. Uma atualização a pedido acionada manualmente a partir da interface do Usuário irá tentar executar até três vezes antes de falhar.

Os administradores de capacidade (e os administradores de serviço do Power BI) pode monitorizar o **média de atualização de tempo de espera (minutos)** métrica para determinar a latência média entre a hora agendada e o início da operação.

Embora não normalmente uma prioridade administrativa, para influenciar no tempo de dados for atualizado, certifique-se de que o está disponível memória suficiente. Isso pode envolver a isolar os conjuntos de dados para as capacidades com recursos suficientes conhecidos. Também é possível que os administradores podem coordenar com os proprietários de conjunto de dados para ajudar a escalonar ou reduzir os tempos de atualização de dados agendada para minimizar as colisões. Tenha em atenção que não é possível que um administrador para ver a fila de atualização, ou para recuperar as agendas de conjunto de dados.

### <a name="why-are-refreshes-slow"></a>Por que são atualizações lento?

As atualizações podem ser lentas - ou percebida lento (como os endereços de pergunta comum anterior).

Quando a atualização de fato estiver lenta, pode ser devido a vários motivos:

- CPU insuficiente (atualização pode ser muito intensiva da CPU).
- Memória insuficiente, resultando em atualização de colocar em pausa (que requer a atualização para começar de novo quando as condições são favoráveis para recommence).
- Motivos de não-capacidade, incluindo a capacidade de resposta de sistema de origem de dados, de latência de rede, de permissões inválidas ou de débito do gateway.
- Volume de dados - um bom motivo para configurar incremental atualiza, tal como explicado abaixo.

Os administradores de capacidade (e os administradores de serviço do Power BI) pode monitorizar o **duração média de atualização (minutos)** métrica para determinar um parâmetro de comparação para comparação ao longo do tempo e o **média de atualização de tempo de espera (minutos)** métricas para determinar a latência média entre média de atraso entre a hora agendada e o início da operação.

A atualização incremental pode reduzir significativamente o período de atualização de dados, especialmente para tabelas de modelos grandes. Existem quatro benefícios associados com atualização incremental:

- **As atualizações são mais rápidas** - apenas um subconjunto de uma tabela precisa a utilização de CPU e memória de carregamento, redução e paralelismo pode ser superior ao atualizar várias partições.
- **Apenas quando necessário, elas ocorrem** -políticas de atualização Incremental podem ser configuradas para carregar apenas quando os dados foram alterados.
- **As atualizações são mais confiáveis** -ligações em execução mais curtas para sistemas de origem de dados voláteis são menos suscetíveis a desativação.
- **Modelos de permanecerem corte** -políticas de atualização Incremental podem ser configuradas para remover automaticamente o histórico para além de uma janela deslizante de tempo.

Para obter mais informações, consulte [Incremental atualizar no Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Por que motivo são dados atualiza não concluir?

Quando a atualização de dados começa, mas não for concluída, pode ser devido a vários motivos:

- Memória insuficiente, mesmo que haja apenas um modelo na capacidade Premium, ou seja, o tamanho do modelo é muito grande.
- Motivos de não-capacidade, incluindo a desativação de sistema de origem de dados, permissões inválidas ou erros de gateway.

Os administradores de capacidade (e os administradores de serviço do Power BI) pode monitorizar o **atualizar falhas devido a memória esgotada** métrica.

## <a name="optimizing-models"></a>Otimizar modelos

Design do modelo ideal é crucial para o fornecimento de uma solução eficiente e dimensionável. No entanto, está além do escopo deste artigo fornece uma discussão completa. Em vez disso, esta secção irá fornecer áreas-chave para consideração aquando da otimização dos modelos.

### <a name="optimizing-power-bi-hosted-models"></a>Otimização de energia de BI alojado modelos

Otimizar modelos alojados numa capacidade Premium pode ser alcançado em camadas de datasource(s) e modelo.

Considere as possibilidades de otimização para um modelo de importação:

![Possibilidades de otimização para um modelo de importação](media/service-premium-capacity-optimize/import-model-optimizations.png)

Na camada de origem de dados:

- Origens de dados relacional podem ser otimizadas para garantir que a atualização mais rápida possível ao previamente integrando dados, aplicar índices apropriados, definindo as partições de tabela que se alinham para períodos de atualização incremental e ao materializar os cálculos (em vez de calculados tabelas e colunas de modelo) ou adicionar lógica de cálculo a vistas.
- Origens de dados não relacionais podem ser previamente integradas com repositórios relacionais.
- Certifique-se de que os gateways têm recursos suficientes, preferencialmente, em máquinas dedicadas, com largura de banda de rede suficiente e próximos as origens de dados.

Na camada do modelo:

- Designs de consulta do Power Query podem minimizar ou remover transformações complexas e especialmente aquelas que origens de dados diferentes (armazéns de dados atingir esse objetivo durante o estágio de Extract-Transform-Load) de intercalação. Além disso, garantir que essa origem de dados apropriada níveis de privacidade são definidas, isso pode evitar a necessidade de Power BI carregar os resultados completos para produzir um resultado combinado em consultas.
- A estrutura do modelo determina os dados para carregar e tem um impacto direto sobre o tamanho do modelo. Ele pode ser projetado para evitar o carregamento de dados desnecessários, removendo as colunas, remover as linhas (especialmente histórico de dados) ou com o carregamento de dados resumidos (às custas de carregar dados detalhados). Redução do tamanho dramática pode ser realizada removendo colunas de cardinalidade elevada (especialmente colunas de texto) que não armazenar ou comprimir de forma muito eficiente.
- Desempenho de consulta do modelo pode ser melhorado através da configuração de relações de direção única, exceto se houver uma razão convincente para permitir a filtragem bidirecional. Considere também utilizar o [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) função em vez de filtragem bidirecional.
- Tabelas de agregação podem conseguir consulta rápida respostas carregando previamente resumidos dados, no entanto, isso aumentará o tamanho do modelo e resultado em tempos mais longos de atualização. Em geral, as tabelas de agregação devem ser reservadas para modelos grandes ou designs de modelo composto.
- As tabelas calculadas e colunas aumentam o tamanho do modelo e resultam em períodos de atualização. Um tamanho mais pequeno de armazenamento e a hora de atualização mais rápida em geral, podem ser obtidos quando os dados são materializados ou calculados na origem de dados. Se não for possível, usar colunas personalizadas do Power Query pode oferecer a compressão de armazenamento aperfeiçoados.
- Pode haver oportunidade de otimizar as expressões de DAX para medidas e regras RLS, talvez reescrever a lógica para evitar caras fórmulas
- A atualização incremental drasticamente pode reduzir o tempo de atualização e poupar memória e CPU. A atualização incremental também pode ser configurada para remover o histórico de dados mantendo os tamanhos de modelos compactação.
- Um modelo poderia ser recriado como dois modelos quando existem padrões de consulta diferentes e em conflito. Por exemplo, alguns relatórios agregados de alto nível presentes ao longo de todos os histórico e pode toleram a latência de 24 horas. Outros relatórios estão preocupados com os dados de hoje e precisam de acesso granular para transações individuais. Em vez de design de um único modelo para atender a todos os relatórios, criar dois modelos otimizados para cada requisito.

Considere as possibilidades de otimização para um modelo de DirectQuery. Como o modelo de problemas de pedidos de consulta à origem de dados subjacente, otimização de origem de dados é fundamental para o fornecimento de consultas de modelo de capacidade de resposta.

 ![Possibilidades de otimização para um modelo de DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Na camada de origem de dados:

- A origem de dados pode ser otimizada para garantir que o mais rápido possível consultar o integrando previamente dados (que não é possíveis na camada de modelo), aplicar os índices apropriados, a definição de partições de tabela, materializar resumidos dados (com exibições indexadas), e minimizar a quantidade de cálculo. A melhor experiência é obtida quando as consultas de pass-through precisam apenas filtrar e efetuar as junções internas entre indexada tabelas ou vistas.
- Certifique-se de que os gateways têm recursos suficientes, preferencialmente, em máquinas dedicadas, com largura de banda de rede suficiente e próximos à origem de dados.

Na camada do modelo:

- Consulta do Power Query designs de preferência, não devem ser aplicada nenhuma transformação - caso contrário, tente manter as transformações reduzido ao mínimo.
- Desempenho de consulta do modelo pode ser melhorado através da configuração de relações de direção única, exceto se houver uma razão convincente para permitir a filtragem bidirecional. Além disso, as relações de modelo devem ser configuradas para assumir integridade referencial é imposta (quando for este o caso) e irá resultar em consultas de origem de dados com associações internas mais eficientes (em vez das associações externas).
- Evite criar colunas personalizadas de consulta de Power Query ou coluna calculada do modelo - materializar isso com a origem de dados, sempre que possível.
- Pode haver uma oportunidade para otimizar as expressões de DAX para medidas e regras RLS, talvez reescrever a lógica para evitar fórmulas caras.

Considere as possibilidades de otimização para um modelo composto. Lembre-se de que um modelo composto permite uma combinação de importação e DirectQuery tabelas.

![Possibilidades de otimização para um modelo composto](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Em geral, a otimização para modelos de importação e DirectQuery aplicam-se às tabelas de modelo composto que utilizam esses modos de armazenamento.
- Normalmente, o nosso objetivo chegar a um design equilibrado através da configuração de tabelas de tipo de dimensão (que representa as entidades de negócios) como duplo modo e o tipo de fato as tabelas de armazenamento (tabelas, muitas vezes, grandes, que representam fatos operacionais) como o modo de armazenamento do DirectQuery. Modo de armazenamento dupla significa ambos importar e modos de armazenamento do DirectQuery e isso permite que o serviço Power BI determinar o modo de armazenamento mais eficiente a utilizar ao gerar uma consulta nativa de pass-through.
- Certifique-se de que os gateways têm recursos suficientes, preferencialmente, em máquinas dedicadas, com largura de banda de rede suficiente e próximos as origens de dados
- Tabelas de agregações configurado como modo de armazenamento de importação pode fornecer melhorias de desempenho de consulta expressiva quando usada para resumir as tabelas de fatos-tipo de modo de armazenamento de DirectQuery. Neste caso, as tabelas de agregação irão aumentar o tamanho do modelo e aumentar o tempo de atualização e, muitas vezes, este é um compromisso aceitável para consultas mais rápidas.

### <a name="optimizing-externally-hosted-models"></a>Otimizando externamente alojado modelos

Muitas possibilidades de otimização discutidas a [Otimizando o Power BI alojado modelos](#optimizing-power-bi-hosted-models) seção também se aplicam a modelos desenvolvidos com o Azure Analysis Services e o SQL Server Analysis Services. Limpar exceções são determinadas funcionalidades que não são atualmente suportadas, incluindo modelos compostos e tabelas de agregação.

Uma consideração adicional para conjuntos de dados hospedados externamente é a base de dados de alojamento em relação ao serviço Power BI. Para o Azure Analysis Services, isso significa a criar o recurso do Azure na mesma região que o inquilino do Power BI (região). Para o SQL Server Analysis Services, para o IaaS, isso significa que aloja a VM na mesma região e no local, significa assegurar uma configuração do gateway eficiente.

Como uma exceção, talvez seja interessante observar que as bases de dados do Azure Analysis Services e bancos de dados em tabela do SQL Server Analysis Services exigem que os seus modelos de ser totalmente carregados na memória e que permanecem lá em todos os tempos de oferecem suporte à consulta. Como o serviço Power BI, tem de haver memória suficiente para atualizar se o modelo tem de permanecer online durante a atualização. Ao contrário do serviço Power BI, não há conceito que os modelos são automaticamente desatualizados dentro e fora de memória, de acordo com utilização. Por conseguinte, o Power BI Premium, oferece uma abordagem mais eficiente para maximizar a consultar o modelo com o uso de memória inferior.

## <a name="capacity-planning"></a>Planejamento de capacidade

O tamanho de uma capacidade Premium determina a memória disponível e recursos de processador e limites impostos na capacidade. O número de capacidades Premium também é uma consideração, como criação de vários Premium capacidades podem ajudar a isolar cargas de trabalho entre si. Tenha em atenção que o armazenamento é 100 TB por nó de capacidade, e é provável que seja mais do que suficiente para qualquer carga de trabalho.

Determinar o tamanho e número de capacidades Premium pode ser desafiante, especialmente para as capacidades iniciais que cria. A primeira etapa ao dimensionamento de capacidade é compreender a carga de trabalho média que representa o uso diário esperado. É importante compreender que nem todas as cargas de trabalho são iguais. Por exemplo, - numa extremidade num espetro - 100 utilizadores em simultâneo, aceder a uma página de relatório único que contém um único elemento visual é facilmente realizáveis. Ainda - no outro extremo do espectro - 100 utilizadores em simultâneo, aceder a 100 relatórios diferentes, cada um com 100 elementos visuais na página do relatório, será muito diferentes demandas de recursos com capacidade de fazer.

Os administradores de capacidade, por conseguinte, terá de considerar vários fatores específicos para o seu ambiente, o conteúdo e a utilização esperada. O substituir objetivo é maximizar a utilização de capacidade, ao mesmo tempo, os tempos de consulta consistente, tempos de espera aceitável e taxas de expulsão. Fatores para consideração podem incluir:

- **Modelar dados de tamanho e características** -modelos de importação tem de ser totalmente carregados na memória para permitir que a consulta ou atualizar. LC/DQ conjuntos de dados podem exigir tempo significativa do processador e, possivelmente, significativa da memória para avaliar medidas complexas ou regras da RLS. Memória e o tamanho de processador e o débito de consulta de LC/DQ estão restritos pelo tamanho da capacidade.
- **Modelos de Active Directory em simultâneo** -a consulta em simultâneo dos modelos diferentes de importação irá fornecer melhor desempenho e capacidade de resposta quando eles permanecem na memória. Deverá existir memória suficiente para alojar todos os modelos intensamente consultados, com memória adicional para permitir a sua atualização.
- **Atualização do modelo de importação** -o tipo de atualização (completo ou incremental), a duração e a complexidade de consultas do Power Query e lógica de tabela/coluna calculada podem causar impacto na memória e a utilização de processador especialmente. Atualizações em simultâneo estão restritos pelo tamanho de capacidade (1,5 x backend núcleos virtuais, arredondados).
- **Consultas em simultâneo** -muitas consultas em simultâneo podem resultar em relatórios sem resposta quando processador ou LC/DQ ligações excede o limite de capacidade. Isso é especialmente relevante para as páginas de relatório que incluem muitos elementos visuais.
- **Fluxos de dados e relatórios paginados** -a capacidade pode ser configurada para suportar fluxos de dados e relatórios paginados, com cada um a solicitar uma configurável percentagem máxima de memória de capacidade. Memória é atribuída dinamicamente ao fluxos de dados, mas é atribuída estaticamente para relatórios paginados.

Além desses fatores, os administradores de capacidade pode considerar a criação de vários recursos. Vários recursos de permitem o isolamento de cargas de trabalho e podem ser configurados para se certificar de cargas de trabalho de prioridade têm a garantia de recursos. Por exemplo, as capacidades de duas podem ser criadas para separar cargas de trabalho críticas de self-service a cargas de trabalho de BI (SSBI). A capacidade de crítico para a empresa pode ser utilizada para isolar grandes modelos empresariais, fornecendo recursos garantidos, com acesso concedido apenas para o departamento de TI de criação. A capacidade SSBI pode ser utilizada para alojar um crescente número de modelos mais pequenos, com acesso concedido aos analistas de negócios. A capacidade SSBI às vezes, poderá ter esperas de consulta ou atualização que estão tolerável.

Ao longo do tempo, os administradores de capacidade pode balancear as áreas de trabalho em capacidades ao mover o conteúdo entre áreas de trabalho ou áreas de trabalho entre as capacidades e ao aumentando ou reduzindo, as capacidades. Em geral, para modelos de host maior do que um aumento vertical e para uma simultaneidade mais elevada aumentar horizontalmente.

Lembre-se de que a compra de uma licença fornece ao inquilino núcleos virtuais. A compra de um **P3** subscrição pode ser utilizada para criar uma ou, até quatro capacidades de Premium, ou seja, 1 x P3, ou 2 x P2 ou 4 x P1. Além disso, antes de upsizing uma capacidade de P2 a uma capacidade de P3, consideração puder ser dado ao dividir os núcleos virtuais para criar dois P1 capacidades.

## <a name="testing-approaches"></a>Abordagens de teste

Depois de decidir o tamanho de capacidade, o teste pode ser efetuado através da criação de um ambiente controlado. É uma opção económica e prática criar uma capacidade do Azure (A SKUs), observar que uma capacidade de P1 é o mesmo tamanho que uma capacidade de A4, com o P2 e P3 capacidades do mesmo tamanho que as capacidades das séries A5 e A6, respectivamente. As capacidades do Azure podem ser criadas rapidamente e são faturadas à hora. Então, depois de testes são concluídos, eles podem ser facilmente eliminados para parar a acumulação de custos.

O conteúdo de teste pode ser adicionado para as áreas de trabalho criadas na capacidade do Azure e, em seguida, como um único utilizador pode executar relatórios para gerar uma carga de trabalho realista e representativa de consultas. Se existirem modelos de importação, uma atualização para cada modelo deve ser efetuada também. Ferramentas de monitorização, em seguida, podem ser utilizada para rever todas as métricas para compreender a utilização de recursos.

É importante que os testes são reproduzidos. Testes devem ser executados várias vezes e devem fornecer aproximadamente o mesmo resultado a cada vez. Uma média desses resultados pode ser utilizada para extrapolar e estimar uma carga de trabalho sob condições de produção verdadeiro.

Para gerar um teste de carga, considere a desenvolver uma aplicativo para simular uma carga de trabalho realista de teste de carga. As especificações de como fazer isso estão fora do escopo deste artigo. Para obter mais informações, incluindo um exemplo de código, consulte a [carregar testes aplicações do Power BI com o teste de carga do Visual Studio](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webinar.

## <a name="acknowledgements"></a>Confirmações

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e especialista no Power BI independente com [soluções totalmente](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Cenários de capacidade Premium](service-premium-capacity-scenarios.md)   
  
Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||