---
title: Aplicação Métricas do Power BI Premium
description: Saiba como utilizar a aplicação Métricas do Power BI Premium para gerir e resolver problemas de capacidade Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/19/2019
LocalizationGroup: Premium
ms.openlocfilehash: ae11ec64a0bffbd3e64c0fd677a7225c2b31f521
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488689"
---
# <a name="power-bi-premium-metrics-app"></a>Aplicação Métricas do Power BI Premium

Pode utilizar a **aplicação Métricas do Power BI Premium** para gerir o estado de funcionamento e a capacidade da sua subscrição do Power BI Premium. Com a aplicação, os administradores utilizam o **Centro de estado de funcionamento da capacidade** da aplicação para ver e interagir com os indicadores que monitorizam o estado de funcionamento da capacidade premium. A aplicação Métricas consiste na página de destino, denominada **Centro de Estado de Funcionamento da Capacidade**, e em detalhes sobre três métricas importantes:

* Memória ativa
* Esperas de consultas
* Esperas de atualizações

![A aplicação Métricas do Power BI Premium](media/service-premium-metrics-app/premium-metrics-app-00.png)

As secções a seguir descrevem a página de destino e as três páginas de relatório de métricas em detalhe. 

## <a name="premium-capacity-health-center"></a>Centro de estado de funcionamento da capacidade Premium

Quando abre a **aplicação Métricas do Power BI Premium**, é-lhe apresentado o **Centro de estado de funcionamento da capacidade**, que apresenta uma visão geral do estado de funcionamento da capacidade do Power BI Premium.

![O centro de estado de funcionamento da capacidade na aplicação Métricas Premium](media/service-premium-metrics-app/premium-metrics-app-01.png)

Na página de destino, pode selecionar a capacidade do Power BI Premium que quer ver, caso a sua organização possua várias subscrições Premium. Para ver uma capacidade Premium, selecione a lista pendente perto do topo da página denominada **Selecionar uma capacidade para ver as métricas**.

Os três KPIs mostram o estado de funcionamento atual da capacidade Premium selecionada, com base nas definições aplicadas a cada um dos três KPI. 

Para ver informações específicas sobre cada KPI, selecione o botão **Explorar** na parte inferior de cada elemento visual do KPI para ver a página de detalhes. As secções seguintes descrevem cada KPI e os detalhes apresentados na página.

## <a name="the-active-memory-metric"></a>Métrica “memória ativa”

A métrica **memória ativa** faz parte da categoria *planeamento de capacidade*, que serve como indicador do bom estado de funcionamento para avaliar o consumo de utilização dos recursos da capacidade, para que assim possa ajustar a capacidade conforme necessário para planear o dimensionamento da capacidade. 

![KPI “memória ativa”](media/service-premium-metrics-app/premium-metrics-app-02.png)

A **memória ativa** é a memória utilizada para processar os conjuntos de dados que estão atualmente em utilização e que, portanto, não serão expulsos quando a memória é necessária. A métrica “memória ativa” indica se a sua capacidade consegue lidar com carga adicional ou se já se encontra perto ou acima da capacidade, a carga atual da capacidade. A memória ativa que está a ser atualmente consumida significa que se encontra disponível menos memória para suportar consultas e atualizações adicionais. 

O KPI **memória ativa** mede quantas vezes a memória ativa da capacidade ultrapassou o limiar de 70% 50 vezes (o marcador está definido como 30% nos últimos sete dias), o que indica que a capacidade se está a aproximar de um ponto no qual os utilizadores poderão começar a ter problemas de desempenho com as consultas.

O elemento visual do medidor nesta secção revela que, nos últimos sete dias a partir do momento em que o relatório foi atualizado pela última vez, a capacidade ultrapassou o limiar de 70% quatro vezes, dividida em registos horários. O valor máximo do medidor, 168, representa os últimos sete dias em horas.

Para saber os detalhes do KPI “memória ativa”, clique no botão **Explorar** para ver uma página de relatório que apresenta visualizações específicas das suas métricas detalhadas, juntamente com um guia de resolução de problemas na coluna direita da página. 

São explicados dois cenários, que podem ser apresentados na página do relatório ao selecionar **Cenário 1** ou **Cenário 2** na página. 

![Página de detalhes da memória ativa](media/service-premium-metrics-app/premium-metrics-app-03.png)

Os guias de resolução de problemas, associados a cada cenário, fornecem explicações detalhadas sobre o que significam as métricas, para que possa compreender melhor o estado da capacidade e o que pode ser feito para mitigar quaisquer problemas. 

Estes dois cenários são descritos nas secções seguintes.

### <a name="scenario-one---current-load-is-too-high"></a>Cenário um – a carga atual é demasiado elevada 

Para determinar se existe memória suficiente para a capacidade concluir as cargas de trabalho, consulte o primeiro elemento visual na página: **A: Percentagens de Memória Consumida** , que apresenta a memória consumida pelos conjuntos de dados que estão a ser ativamente processados e assim não podem ser expulsos.

O limiar de alarme, que é a linha pontilhada a vermelho, marca incidentes de consumo de memória de 90%.

O limiar de aviso, que é a linha pontilhada a amarelo, marca incidentes de consumo de memória de 70%. 

A linha pontilhada a preto indica a tendência de utilização da memória, com base na atual utilização da memória da capacidade ao longo da linha cronológica do gráfico.

Muitas ocorrências de memória ativa acima do limiar de alarme (linha pontilhada a vermelho) e tendência de memória (linha pontilhada a preto) indicam pressão da capacidade de memória, que possivelmente impede que conjuntos de dados adicionais sejam carregados na memória durante esse período. 

Quando vê estes casos, deve analisar atentamente os outros gráficos na página para melhor determinar o quê e o porquê de tanta memória estar a ser consumida com tanta frequência e como otimizar e balancear a carga ou se necessário aumentar verticalmente a capacidade. 

O segundo elemento visual na página, **B: Conjuntos de dados ativos carregados por hora**, apresenta as contagens do número máximo de conjuntos de dados que foram carregados na memória, em registos horários. 

O terceiro elemento visual, **C: Porque é que os conjuntos de dados estão na memória**, é uma tabela que lista o conjunto de dados por nome de área de trabalho, nome do conjunto de dados, tamanho não comprimido de conjuntos de dados na memória e explica o motivo pelo qual está carregado na memória (por exemplo, está a ser atualizado, consultado ou ambos).

#### <a name="diagnosing-scenario-one"></a>Diagnosticar o cenário um

Uma utilização da memória ativa elevada consistente pode resultar em forçar conjuntos de dados que estão a ser ativamente utilizados a serem expulsos ou pode impedir que novos conjuntos de dados sejam carregados. Os seguintes passos podem ajudá-lo a diagnosticar problemas

1. Observe o gráfico *A: Percentagens de consumo de memória*

    **a.** Se o Gráfico A mostrar que o limiar de alarme (90%) é ultrapassado muitas vezes e/ou durante horas consecutivas, significa que a sua capacidade está a esgotar-se na memória com demasiada frequência. No gráfico abaixo, podemos ver que o limiar de alerta (70%) foi ultrapassado quatro vezes.

    ![Gráfico A, percentagens de consumo de memória](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** O gráfico denominado *B: Conjuntos de dados ativos carregados por hora* apresenta o número máximo de conjuntos de dados únicos carregados na memória em registos horários. Selecionar uma barra no elemento visual filtrará de forma cruzada os motivos pelos quais os conjuntos de dados estão no elemento visual da memória.  

    ![Gráfico B, memória consumida por hora](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** Consulte a tabela **Por que os conjuntos de dados estão na memória** para ver uma lista dos conjuntos de dados que foram carregados na memória. Ordene por *Tamanho do Conjunto de Dados (MB)* para realçar os conjuntos de dados que ocupam a maioria da memória. As operações de capacidades são classificadas como *interativas* ou *de segundo plano*. As operações interativas incluem compor consultas e responder a interações de utilizadores (filtrar, consultar Perguntas e Respostas, etc.). O total de consultas e o total de atualizações permitem saber se existem operações em segundo plano (atualizações) ou interativas (pedidos) pesadas no conjunto de dados. É importante compreender que as operações interativas têm sempre prioridade sobre as operações de segundo plano para garantir a melhor experiência de utilizador possível. Se existirem recursos insuficientes, as operações em segundo plano serão adicionadas a uma fila e processadas quando os recursos ficarem livres. As operações em segundo plano, como as atualizações de conjuntos de dados e funções de IA, podem ser interrompidas a meio do processo pelo serviço Power BI e adicionadas a uma fila.
    
    ![Tabela C, lista de conjuntos de dados](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Soluções para o cenário um

Pode realizar os seguintes passos para solucionar os problemas associados ao cenário um:

1. **Aumentar verticalmente a capacidade** – aumentar verticalmente a capacidade para o próximo SKU disponibilizará o dobro da memória que tem com o SKU atual e permitirá, assim, aliviar qualquer pressão sobre a memória que a capacidade possa estar a enfrentar.

2. **Mover conjuntos de dados para outra capacidade** – se tiver outra capacidade que tenha mais memória disponível, poderá mover a área de trabalho que contém conjuntos de dados de maiores dimensões para essa capacidade.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Cenário dois – a carga futura vai exceder os limites

Para determinar se existe memória suficiente para a capacidade concluir as cargas de trabalho, pode ver o elemento visual **A: Percentagens de Consumo de Memória** no topo da página, que representa a memória consumida pelos conjuntos de dados que estão a ser ativamente processados e que não podem ser expulsos. A linha pontilhada a preto realça as tendências. Numa capacidade a sofrer de pressão de memória, o mesmo elemento visual vai claramente mostrar a tendência crescente da memória (linha pontilhada a preto), o que significa que é possível, nesse momento, impedir o carregamento de conjuntos de dados adicionais na memória. A linha de tendência, a linha tracejada a preto, mostra a tendência de crescimento com base em sete dias de dados. 

![Página de detalhes da memória ativa](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosticar o cenário dois

Para diagnosticar o cenário dois, determine se a linha de tendência está a apresentar uma tendência ascendente para os limiares de alerta ou de alarme. 

1. Considere o **Gráfico A:**

    ![Gráfico de memória consumida](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Se o gráfico mostrar uma inclinação ascendente, tal indicará que o consumo de memória aumentou ao longo dos últimos sete dias.

    **b.** Assuma o crescimento ascendente e preveja quando a linha de tendência cruzará o limiar de aviso (linha tracejada a amarelo).

    **c.** Continue a verificar a linha de tendência, pelo menos de dois em dois dias, para ver se a tendência continua.

#### <a name="remedies-for-scenario-two"></a>Soluções para o cenário dois

Pode realizar os seguintes passos para solucionar os problemas associados ao cenário dois:

1. **Aumentar verticalmente a capacidade** – aumentar verticalmente a capacidade para o próximo SKU disponibilizará o dobro da memória que tem com o SKU atual e permitirá, assim, aliviar qualquer pressão sobre a memória que a capacidade possa estar a enfrentar.

2. **Mover conjuntos de dados para outra capacidade** – se tiver outra capacidade que tenha mais memória disponível, poderá mover a área de trabalho que contém conjuntos de dados de maiores dimensões para essa capacidade.


## <a name="the-query-waits-metric"></a>Métrica “espera de consultas”

A categoria **Consultas** indica se os utilizadores reportaram elementos visuais com resposta lenta ou que deixaram de responder. A **Espera de consultas** é o tempo que a consulta demora a iniciar a execução a partir do momento que foi acionada. Este KPI mede se 25% ou mais das consultas da capacidade selecionada estão a demorar 100 milissegundos ou mais a serem executadas. A espera de consultas ocorre quando não existe CPU suficiente disponível para executar todas as consultas pendentes. 

![Medidor de espera de consultas](media/service-premium-metrics-app/premium-metrics-app-09.png)

O medidor neste elemento visual mostra que nos últimos sete dias a partir da hora em que o relatório foi atualizado pela última vez, 17,32% das consultas aguardaram mais de 100 milissegundos. 

Para saber detalhes sobre o KPI Espera de consultas, clique no botão **Explorar** para apresentar uma página de relatório com visualização das métricas relevantes e um guia de resolução de problemas na coluna direita da página. O guia de resolução de problemas possui dois cenários, cada um deles fornece explicações detalhadas da métrica, do estado da capacidade e o que pode fazer para mitigar o problema.

Vamos discutir cada cenário de espera de consultas, um de cada vez, nas secções a seguir.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Cenário um – consultas de execução prolongada consomem CPU

No primeiro cenário, as consultas de execução prolongada estão a ocupar demasiada CPU. 

Pode investigar se o mau desempenho do relatório é provocado por uma capacidade sobrecarregada ou devido a um conjunto de dados ou relatório mal concebido. Existem várias razões pelas quais uma consulta pode ser executada durante um longo período, um período longo é definido como um período em que a execução demora mais de 10 segundos. A complexidade e o tamanho dos conjuntos de dados, assim como a complexidade das consultas são apenas alguns exemplos do que pode provocar uma consulta de execução prolongada. 

Na página do relatório, são apresentados os seguintes elementos visuais: 

* A tabela superior intitulada **A: Tempos de espera elevados** lista os conjuntos de dados com consultas que estão em espera. 
* **B: Distribuição dos tempos de espera elevados por hora** mostra a distribuição dos tempos de espera elevados. 
* O gráfico denominado **C: Contagens de consultas de execução prolongada por hora** apresenta a contagem das consultas de execução prolongada que foram executadas, divididas em registos por hora.
* O último elemento visual, tabela **D: Consultas de execução prolongada**, lista as consultas de execução prolongada e as estatísticas das mesmas.

![Página de detalhes de espera de consultas](media/service-premium-metrics-app/premium-metrics-app-10.png)

Existem passos que pode fazer para diagnosticar e resolver problemas com os tempos de espera de consultas, descritos a seguir.

#### <a name="diagnosing-scenario-one"></a>Diagnosticar o cenário um

Em primeiro lugar, pode determinar se as consultas de execução prolongada estão a ocorrer quando as consultas estão em espera. 

![Tabela de tempos de espera elevados](media/service-premium-metrics-app/premium-metrics-app-11.png)

Observe o **Gráfico B**, que apresenta a contagem de consultas que esperam durante mais de 100 ms. Selecione uma das colunas que mostra um número elevado de esperas.

![Distribuição do tempo de espera elevado](media/service-premium-metrics-app/premium-metrics-app-12.png)

Quando clica numa coluna com tempos de espera elevados, o **Gráfico C** é filtrado para mostrar a contagem de consultas de execução prolongada que foram executadas durante esse período, apresentadas na imagem a seguir:

![Contagem de consultas prolongadas por hora](media/service-premium-metrics-app/premium-metrics-app-13.png)

Adicionalmente, o **Gráfico D** também é filtrado para mostrar as consultas de execução prolongada durante o período de tempo selecionado.

![Consultas de execução prolongada](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Soluções para o cenário um

Estes são os passos que pode fazer para resolver os problemas do cenário um:

1. **Executar PerfAnalyzer para otimizar relatórios e conjuntos de dados** - o analisador de desempenho dos relatórios mostrará o efeito de cada interação numa página, incluindo quanto tempo cada elemento visual demora a atualizar e onde o tempo é gasto.

2. **Aumentar verticalmente a capacidade** – aumentar verticalmente a capacidade para o SKU seguinte disponibilizará o dobro da quantidade de CPU e permitirá, assim, aliviar qualquer pressão sobre a CPU que possa estar a aumentar o tempo de execução das consultas.

3. **Mover conjuntos de dados para outra capacidade** – se tiver outra capacidade que tenha mais CPU disponível, poderá mover as áreas de trabalho que contêm os conjuntos de dados que contêm as consultas que estão à espera da outra capacidade.

### <a name="scenario-two---too-many-queries"></a>Cenário dois – demasiadas consultas

No cenário dois, existem demasiadas consultas em execução.

Quando o número de consultas a executar excede os limites da capacidade, as consultas são colocadas numa fila até que os recursos estejam disponíveis para as executar. Se o tamanho da fila se tornar demasiado longo, as consultas nessa fila poderão demorar mais de 100 milissegundos.

![Cenário dois](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>Diagnosticar o cenário dois

Na **Tabela A**, selecione um conjunto de dados que tenha uma elevada percentagem de tempo de espera.

![tabela de tempos de espera elevados](media/service-premium-metrics-app/premium-metrics-app-16.png)

Após selecionar um conjunto de dados com um tempo de espera elevado, o **Gráfico B** é filtrado para apresentar as distribuições de tempo de espera das consultas nesse conjunto de dados, ao longo dos últimos sete dias. Em seguida, selecione uma das colunas no **Gráfico B**.

![gráfico de distribuição de tempos de espera elevados por hora](media/service-premium-metrics-app/premium-metrics-app-17.png)

O **Gráfico C** é, em seguida, filtrado para mostrar o comprimento da fila no momento selecionado no Gráfico B.

![comprimento da fila de consultas por hora](media/service-premium-metrics-app/premium-metrics-app-18.png)

Se o comprimento da fila ultrapassar o limiar de 20, será provável que as consultas no conjunto de dados selecionado sejam atrasadas, devido a tentativas de executar demasiadas consultas ao mesmo tempo.

![Execução da tabela de consultas](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>Soluções para o cenário dois

Pode realizar os seguintes passos para solucionar os problemas associados ao cenário dois:

1. **Aumentar verticalmente a capacidade** – aumentar verticalmente a capacidade para o próximo SKU disponibilizará o dobro da memória que tem com o SKU atual e permitirá, assim, aliviar qualquer pressão sobre a memória que a capacidade possa estar a enfrentar.

2. **Mover conjuntos de dados para outra capacidade** – se tiver outra capacidade que tenha mais memória disponível, poderá mover a área de trabalho que contém conjuntos de dados de maiores dimensões para essa capacidade.


## <a name="the-refresh-waits-metric"></a>Métrica “esperas de atualizações”

A métrica **Esperas de atualizações** fornece informações sobre quando os utilizadores podem estar a receber dados de relatório antigos ou obsoletos. As **Esperas de atualizações** são o período de tempo que uma determinada atualização de dados esperou até iniciar a execução, desde o momento em que foi acionada mediante pedido ou agendada para execução. Este KPI mede se 10% ou mais dos pedidos de atualizações pendentes estão a aguardar há 10 minutos ou mais. A espera ocorre, normalmente, quando a memória ou CPU é insuficiente.

![Medidor de esperas de atualizações](media/service-premium-metrics-app/premium-metrics-app-20.png)

Este medidor mostra que nos últimos sete dias a partir da última atualização do relatório de atualizações, 3,18% das atualizações aguardaram mais de 10 minutos. 

Para obter detalhes sobre o KPI **Esperas de atualizações**, clique no botão **Explorar**, que apresentará uma página com métricas e um guia de resolução de problemas na coluna direita da página de relatório. O guia fornece explicações detalhadas sobre as métricas na página e ajuda-o a compreender o estado da capacidade e o que pode fazer para mitigar quaisquer problemas.

![Explorar as métricas “esperas de atualizações”](media/service-premium-metrics-app/premium-metrics-app-21.png)

São explicados dois cenários, que podem ser apresentados na página do relatório selecionando Cenário 1 ou Cenário 2 na página. Vamos discutir cada cenário, um de cada vez, nas secções a seguir.

### <a name="scenario-one---not-enough-memory"></a>Cenário um – memória insuficiente

No cenário um, não existe memória suficiente para carregar o conjunto de dados. Existem duas situações que resultam na limitação de uma atualização durante as condições de memória baixa:

1. Não existe memória suficiente para carregar o conjunto de dados.
2. A atualização foi cancelada devido a uma operação com prioridade superior. 

A prioridade do carregamento dos conjuntos de dados é a seguinte:

1. Consulta interativa
2. Atualização a pedido
3. Atualização agendada

Se não existir memória suficiente para carregar um conjunto de dados para uma consulta interativa, as atualizações agendadas serão interrompidas e os conjuntos de dados descarregados até que fique disponível memória suficiente. Se tal não libertar memória suficiente, as atualizações a pedido serão interrompidas e os conjuntos de dados serão descarregados.

#### <a name="diagnosing-scenario-one"></a>Diagnosticar o cenário um

Para diagnosticar o cenário um, determine primeiro se a limitação se deve a memória insuficiente. Os passos para o fazer são os seguintes.

1.    Selecione o conjunto no qual está interessado na **Tabela A** ao clicar no mesmo: 

    ![Tabela A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Quando um conjunto de dados é selecionado na **Tabela A**, a **Tabela B** é filtrada para apresentar quando a espera ocorreu.

    ![Gráfico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. E seguida, o **Gráfico C** é filtrado para mostrar qualquer limitação, explicada no passo seguinte. 

2. Observe os resultados no **Gráfico C**, que agora se encontra filtrado. Se o gráfico mostrar que ocorreu uma limitação por falta de memória no momento em que o conjunto de dados estava em espera, significa que o conjunto de dados estava em espera devido a condições de memória baixa.

    ![Gráfico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Por fim, marque o **Gráfico D**, que mostra os tipos de atualizações que estão a ocorrer, agendadas versus a pedido. Qualquer atualização a pedido que ocorra ao mesmo tempo pode ser a causa da limitação.

    ![Gráfico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Soluções para o cenário um

Pode realizar os seguintes passos para solucionar os problemas associados ao cenário um:

1. **Aumentar verticalmente a capacidade** – aumentar verticalmente a capacidade para o próximo SKU disponibilizará o dobro da memória do que tem com o SKU atual e permitirá, assim, aliviar qualquer pressão sobre a memória e sobre a CPU que a capacidade possa estar a enfrentar.

2. **Mover conjuntos de dados para outra capacidade** – se os tempos de espera estiverem a ser provocados por pressão de memória e se tiver outra capacidade que possua mais memória disponível, poderá mover as áreas de trabalho que contêm os conjuntos de dados que estão em espera para a outra capacidade.

3. **Distribuir as atualizações agendadas** – distribuir as atualizações ajudará a evitar o excesso de atualizações que tentam ser executadas em simultâneo.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Cenário dois – CPU insuficiente para atualização

No segundo cenário, não existe CPU suficiente disponível para executar a atualização. 

Para capacidades dedicadas, o Power BI limita o número de atualizações que podem acontecer em simultâneo. Este número é igual ao número de cores de back-end x 1,5. Por exemplo, uma capacidade dedicada P1, que tem quatro cores de back-end, pode executar 6 atualizações em simultâneo. Uma vez atingido o número máximo de atualizações em simultâneo, as outras atualizações vão esperar até que a execução de uma atualização termine.

![Cenário dois para atualização](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosticar o cenário dois

Para diagnosticar o cenário dois, determine primeiro se a limitação se deve a ter alcançado a simultaneidade máxima para as atualizações. Os passos para o fazer são os seguintes.

1.    Selecione o conjunto no qual está interessado na **Tabela A** ao clicar no mesmo: 

    ![Tabela A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Quando um conjunto de dados é selecionado na **Tabela A**, a **Tabela B** é filtrada para apresentar quando a espera ocorreu.

    ![Gráfico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. E seguida, o **Gráfico C** é filtrado para mostrar qualquer limitação, explicada no passo seguinte. 

2. Observe os resultados no **Gráfico C**, que agora se encontra filtrado. Se o gráfico mostrar que a *simultaneidade máxima* ocorreu nos momentos em que o conjunto de dados estava em espera, significa que o conjunto de dados estava em espera devido à CPU disponível ser insuficiente.

    ![Gráfico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Por fim, marque o **Gráfico D**, que mostra os tipos de atualizações que estão a ocorrer, agendadas versus a pedido. Qualquer atualização a pedido que ocorra ao mesmo tempo pode ser a causa da limitação.

    ![Gráfico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>Soluções para o cenário dois

1. **Aumentar verticalmente a capacidade** – aumentar verticalmente a capacidade para o próximo SKU disponibilizará o dobro da memória que tem com o SKU atual e o dobro do número de atualizações em simultâneo e permitirá, assim, aliviar qualquer pressão sobre a memória e sobre a CPU que a capacidade possa estar a enfrentar.

2. **Mover conjuntos de dados para outra capacidade** - se os tempos de espera estiverem a ser provocados por ter alcançado a simultaneidade máxima e se tiver outra capacidade que tenha simultaneidade disponível pode mover as áreas de trabalho que contêm os conjuntos de dados que estão à espera da outra capacidade.

3. **Distribuir as atualizações agendadas** – distribuir as atualizações ajudará a evitar o excesso de atualizações que tentam ser executadas em simultâneo.



## <a name="next-steps"></a>Próximos passos

* [O que é o Power BI Premium?](service-premium-what-is.md)
* [Notas de versão do Power BI Premium](service-premium-release-notes.md)
* [Documento técnico do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy)
* [Ativação da Versão de Avaliação Pro alargada](service-extended-pro-trial.md)
* [FAQ do Power BI Embedded](developer/embedded/embedded-faq.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)