---
title: Monitorizar as capacidades do Power BI Premium na sua organização
description: Utilizar o portal de administração do Power BI e a aplicação Métricas de Capacidade do Power BI Premium
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/06/2018
LocalizationGroup: Premium
ms.openlocfilehash: 4fc036bf9191d0ed56be11e69152e579cfc5102d
ms.sourcegitcommit: 883d7e76816f2696e88ae391744ac6c7b1cb59c7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51688402"
---
# <a name="monitor-power-bi-premium-and-power-bi-embedded-capacities"></a>Monitorizar as capacidades no Power BI Premium e no Power BI Embedded

Este artigo fornece uma descrição geral da monitorização das métricas das capacidades do Power BI Premium. Monitorizar a utilização das capacidades permite-lhe ter uma abordagem informada para gerir as suas capacidades.

Pode monitorizar a capacidade com a aplicação Métricas de Capacidade do Power BI Premium ou no portal de administração. Recomendamos a aplicação, porque fornece muitos mais detalhes, apesar deste artigo abordar as duas opções.

**A versão atual da aplicação é a 1.9 (lançada a 14 de novembro de 2018).**

.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UgsjMbhi_Bk?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="install-the-premium-capacity-metrics-app"></a>Instalar a aplicação Métricas de Capacidade Premium

Pode ir diretamente para a [aplicação Métricas de Capacidade Premium](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) ou instalá-la tal como faz com as outras aplicações no Power BI.

1. No Power BI, clique em **Aplicações**.

    ![Ir para as Aplicações](media/service-admin-premium-monitor-capacity/apps.png)

1. No lado direito, clique em **Obter aplicações**.

1. Na categoria **Aplicações**, procure **Aplicação Métricas de Capacidade do Power BI Premium**.

1. Precisa de uma subscrição para instalar a aplicação.

Agora que instalou a aplicação, pode ver as métricas sobre as capacidades na sua organização. Vamos dar analisar algumas das métricas principais disponíveis.

## <a name="use-the-metrics-app"></a>Utilizar a aplicação de métricas

Quando abre a aplicação, é apresentado um dashboard com um resumo de todas as capacidades para as quais tem direitos de administrador.

![Dashboard da aplicação de métricas](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Clique no dashboard para ir para o relatório subjacente. O relatório tem seis separadores, que descrevemos em mais detalhes nas seções a seguir.

* **Filtros**: permite-lhe filtrar as outras páginas no relatório para uma capacidade específica.

* **Conjuntos de dados**: métricas detalhadas sobre o estado de funcionamento dos conjuntos de dados do Power BI nas suas capacidades.

* **Relatórios paginados**: métricas detalhadas sobre o estado de funcionamento dos relatórios paginados nas suas capacidades.

* **Fluxos de dados**: métricas de atualização detalhadas dos fluxos de dados nas suas capacidades.

* **Sistema**: métricas gerais da capacidade, incluindo a memória e a utilização elevada da CPU.

* **Nomes a Apresentar e IDs**: nomes, IDs e proprietários das capacidades, áreas de trabalho e cargas de trabalho.

### <a name="filters-tab"></a>Separador Filtros

O separador **Filtros** permite-lhe selecionar uma capacidade, um intervalo de datas e outras opções. Os filtros são aplicados, em seguida, a todos os mosaicos e páginas relevantes no relatório. Se não forem selecionados filtros, o relatório por predefinição mostrará as métricas da semana anterior para cada capacidade de que for proprietário.

![Separador Filtros](media/service-admin-premium-monitor-capacity/filters-tab.png)

* **(A)** Selecione **Conjuntos de Dados**, **Relatórios Paginados** ou **Fluxos de Dados** para definir filtros para cada carga de trabalho.

* **(B)** O nome e **(C)** as informações são atualizados com base no que selecionar em **(A)**, o que lhe permite filtrar uma carga de trabalho por nome. Por exemplo, na imagem acima, está selecionado **Fluxos de Dados**, a mostrar **Nome dos Fluxos de Dados** e **Informações dos Fluxos de Dados**.

* **(D)** Informações de capacidade, que indica se os conjuntos de dados, os relatórios paginados ou os fluxos de dados estão ativados para uma capacidade.

### <a name="datasets-tab"></a>Separador Conjuntos de Dados

Utilize os botões na parte superior do separador **Conjuntos de Dados** para navegar para áreas diferentes: **Resumo**, **Atualizações**, **Durações das Consultas**, **Esperas das Consultas** e **Conjuntos de Dados**.

![Separador Conjuntos de Dados](media/service-admin-premium-monitor-capacity/datasets-tab.png)

#### <a name="summary-area"></a>Área de resumo

A área **Resumo** mostra uma vista das suas capacidades com base em entidades, recursos de sistema e cargas de trabalho do conjunto de dados. Mostra as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Entidades** | * O número de capacidades de que é proprietário<br> * O número distinto de conjuntos de dados na sua capacidade<br> * O número distinto de áreas de trabalho na sua capacidade |
| **Sistema** | * A utilização média da memória em GB nos últimos sete dias<br> * O mais alto consumo de memória em GB nos últimos sete dias e a hora local em que ocorreu<br> * O número de vezes que a CPU excedeu o valor de 80% dos limiares nos últimos sete dias, dividido em registos de três minutos<br> * A maioria das vezes em que a CPU excedeu o valor de 80% nos últimos sete dias, dividido em registos de uma hora e a hora local em que ocorreram<br> * O número de vezes que a Consulta direta/Ligações em direto excederam o valor de 80% dos limiares nos últimos sete dias, dividido em registos de três minutos<br> * A maioria das vezes em que a Consulta direta/Ligações em direto excederam o valor de 80% nos últimos sete dias, dividido em registos de uma hora e a hora local em que ocorreram |
| **Cargas de Trabalho do Conjunto de Dados** | * O número total de atualizações nos últimos sete dias<br> * O número total de atualizações com êxito nos últimos sete dias<br> * O número total de atualizações com falha nos últimos sete dias<br> * O número total de atualizações com falha devido a memória esgotada<br> * A duração média da atualização é o tempo necessário para concluir a operação, em minutos<br> * O tempo médio de espera da atualização é o desfasamento médio entre a hora agendada e o início da operação, em minutos<br> * O número total de consultas executadas nos últimos sete dias<br> * O número total de consultas com êxito nos últimos sete dias<br> * O número total de consultas com falhas nos últimos sete dias<br> * A duração média das consultas é o tempo necessário para concluir a operação, em minutos<br> * O número total de modelos expulsos devido à pressão de memória<br> * Tamanho médio dos conjuntos de dados <br> * Contagem média de conjuntos de dados carregados para a memória |
|  |  |

#### <a name="refreshes-area"></a>Área de atualizações

A área **Atualizações** contém as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Fiabilidade das atualizações** | * Contagem Total: as atualizações totais para cada conjunto de dados<br> * Fiabilidade: a percentagem de atualizações que foi concluída para cada conjunto de dados<br> * Tempo Médio de Espera: o desfasamento médio entre a hora agendada e o início da atualização do conjunto de dados, em minutos<br> * Tempo Máximo de Espera: o tempo máximo de espera do conjunto de dados, em minutos <br> * Duração Média: a duração média da atualização do conjunto de dados, em minutos<br> * Duração Máxima: a duração da atualização de execução mais longa do conjunto de dados, em minutos |
| **Primeiros Cinco Conjuntos de Dados por Média de Duração da Atualização** | * Os cinco conjuntos de dados com a duração média mais longa de atualização, em minutos |
| **Primeiros Cinco Conjuntos de Dados por Média de Tempo de Espera** | * Os cinco conjuntos de dados com o tempo médio de espera de atualização mais longo, em minutos |
| **Média dos Tempos de Espera das Atualizações por Hora** | * O tempo médio de espera de atualização, dividido em registos de uma hora, comunicado na hora local. Os vários picos com tempo de espera da atualização são indicativos da execução frequente da capacidade. |
| **Contagem de Atualizações e Consumo de Memória por Hora** | * Êxitos, falhas e consumo de memória, dividido em registos de uma hora, comunicado na hora local |
|  |  |

#### <a name="query-durations-area"></a>Área Durações de Consulta

A área **Durações das Consultas** contém as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Durações das Consultas** | * Os dados nesta secção são segmentados por conjuntos de dados, área de trabalho e registos por hora dos últimos sete dias<br> * Total: o número total de consultas executadas para o conjunto de dados<br> * Média: a duração média das consultas para o conjunto de dados, em milissegundos<br> * Máx.: a duração das consultas de execução mais longa no conjunto de dados, em milissegundos|
| **Distribuição da Duração das Consultas** | * O histograma da duração das consultas é registado por durações das consultas (em milissegundos) nas seguintes categorias: intervalos de <= 30 ms, 30-100 ms, 100-300 ms, 300 ms-1 s, 1-3 s, 3-10 s, 10-30 s e > 30 s. Durações de consulta longas e tempos de espera longos são indicativos da capacidade de executar acessos frequentes. Também pode significar que um único conjunto de dados está a causar problemas e ainda é necessário mais investigação. |
| **Primeiros Cinco Conjuntos de Dados por Duração Média** | * Os cinco conjuntos de dados com a duração das consultas média mais longa, em milissegundos |
| **Consulta Direta/Ligações em Direto (> 80% de Utilização)** | * As vezes que uma consulta direta ou uma ligação em direto excedeu 80% de utilização da CPU, dividido em registos de uma hora, comunicadas na hora local |
| **Distribuições da Duração das Consultas por Hora** | * As contagens de consultas e a duração média (em milissegundos) em comparação com o consumo de memória em GB, dividido em registos de uma hora, comunicado na hora local |
|  |  |

#### <a name="query-waits-area"></a>Área Esperas de Consulta

A área **Esperas das Consultas** contém as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Tempos de Espera das Consultas** | * Os dados nesta secção são segmentados por conjuntos de dados, área de trabalho e registos por hora dos últimos sete dias<br> * Total: o número total de consultas executadas para o conjunto de dados<br> * Contagem de espera: o número de consultas no conjunto de dados que aguardou por recursos do sistema antes de iniciar execução <br> * Média: a duração média do tempo de espera para o conjunto de dados, em milissegundos<br> * Máx.: a duração da consulta de espera mais longa no conjunto de dados, em milissegundos|
| **Distribuição do Tempo de Espera** | * O histograma das durações das consultas é registado por durações das consultas (em milissegundos) nas seguintes categorias: intervalos de <= 50 ms, 50-100 ms, 100-200 ms, 200-400 ms, 400 ms-1 s, 1-5 s e > 5 s |
| **Primeiros Cinco Conjuntos de Dados por Média de Tempo de Espera** | * Os cinco conjuntos de dados com o maior tempo de espera médio para iniciar a execução de uma consulta, em milissegundos |
| **Contagens e Tempos de Espera das Consultas por Hora** | * As contagens de esperas das consultas e o tempo médio de espera (em milissegundos) em comparação com o consumo de memória em GB, dividido em registos de uma hora comunicados na hora local |
|  |  |

#### <a name="datasets-area"></a>Área de conjuntos de dados

A área **Conjuntos de Dados** contém as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Contagens da Expulsão de Conjuntos de Dados** | * Total: o número total de *expulsões* de conjunto de dados para cada capacidade. Quando uma capacidade sofre uma pressão de memória, o nó expulsa um ou mais conjuntos de dados da memória. Os conjuntos de dados que estiverem inativos (sem qualquer operação de consulta/atualização em execução) são os primeiros a serem expulsos. Em seguida, a ordem de expulsão é feita com base no critério "menos recentemente utilizado" (LRU).|
| **Expulsões de Conjuntos de Dados por Hora e Consumo de Memória** | * Expulsões de conjuntos de dados em comparação com o consumo de memória em GB, dividido em registos de uma hora, comunicado na hora local |
| **Contagens de Conjuntos de Dados Carregados por Hora** | * Número de conjuntos de dados carregados para a memória em comparação com o consumo de memória em GB, dividido em registos de uma hora, comunicado na hora local |
| **Tamanhos dos Dados**  | * Tamanho máx.: o tamanho máximo do conjunto de dados em MB para o período apresentado |
|  |  |

### <a name="paginated-reports-tab"></a>Separador Relatórios paginados

O separador **Relatórios paginados** mostra as métricas detalhadas sobre o estado de funcionamento dos relatórios paginados nas suas capacidades.

![Separador Relatórios paginados](media/service-admin-premium-monitor-capacity/paginated-reports-tab.png)

O separador **Relatórios paginados** contém as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Utilização global** | * Total de Visualizações: o número de vezes que o relatório foi visto por um utilizador<br> * Contagem de Linhas: o número de linhas de dados no relatório<br> * Obtenção (média): o tempo médio que demora a obter os dados para o relatório, em milissegundos. As durações longas podem indicar consultas lentas ou outros problemas na origem dos dados. <br> * Processamento (média): a quantidade média de tempo que demora a processar dados para um relatório, em milissegundos<br>* Composição (média): a quantidade média de tempo que demora a compor um relatório no browser, em milissegundos<br> * Tempo total: o tempo necessário para todas as fases do relatório, em milissegundos|
| **Primeiros Cinco Relatórios por Tempo Médio de Obtenção de Dados** | * Os cinco relatórios com o tempo médio de obtenção de dados mais longo, em milissegundos |
| **Primeiros Cinco Relatórios por Tempo Médio de Processamento dos Relatórios** | * Os cinco relatórios com o tempo médio de processamento de relatório mais longo, em milissegundos |
| **Durações por Hora** | * O tempo de obtenção em comparação com o de processamento e de composição de dados, dividido em registos de uma hora, comunicado na hora local |
| **Resultados por Hora** | * Êxitos, falhas e consumo de memória, dividido em registos de uma hora, comunicado na hora local |
|  |  |

### <a name="dataflows-tab"></a>Separador Fluxo de dados

O separador **Fluxo de dados** mostra as métricas detalhadas das atualizações dos fluxos de dados nas suas capacidades.

![Separador Fluxo de dados](media/service-admin-premium-monitor-capacity/dataflows-tab.png)

A área **Fluxos de dados** contém as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Atualização** | * Total: as atualizações totais para cada fluxo de dados<br> * Fiabilidade: a percentagem de atualizações que foi concluída para cada fluxo de dados<br> * Tempo Médio Espera: o desfasamento médio entre a hora agendada e o início da atualização do fluxo de dados, em minutos<br> * Tempo Máximo Espera: o tempo máximo de espera do fluxo de dados, em minutos <br> * Duração Média: a duração média da atualização do fluxo de dados, em minutos<br> * Duração Máxima: a duração da atualização de execução mais longa do fluxo de dados, em minutos |
| **Primeiros Cinco Fluxos de Dados por Média de Duração da Atualização** | * Os cinco fluxos de dados com a duração média mais longa de atualização, em minutos |
| **Principais 5 fluxos de dados por Tempo Médio de Espera** | * Os cinco fluxos de dados com o tempo médio de espera mais longo, em minutos |
| **Média dos Tempos de Espera das Atualizações por Hora** | * O tempo médio de espera de atualização, dividido em registos de uma hora, comunicado na hora local. Os vários picos com tempo de espera da atualização são indicativos da execução frequente da capacidade. |
| **Contagem de Atualizações e Consumo de Memória por Hora** | * Êxitos, falhas e consumo de memória, dividido em registos de uma hora, comunicado na hora local |
|  |  |

### <a name="system-tab"></a>Separador Sistema

O separador **Sistema** mostra o consumo de CPU e de memória em todas as capacidades e cargas de trabalho.

![Separador Sistema](media/service-admin-premium-monitor-capacity/system-tab.png)

O separador **Sistema** contém as métricas seguintes.

| **Secção Relatório** | **Métricas** |
| --- | --- |
| **Métricas de CPU (> 80% de utilização)** | * O número de vezes que a CPU excedeu o valor de 80% dos limiares nos últimos sete dias, dividido em registos de três minutos |
| **Consumo de memória** | * O consumo de memória nos últimos sete dias, dividido em registos de três minutos |
|  |  |

### <a name="display-names-and-ids-tab"></a>Separador Nomes a Apresentar e IDs

O separador **Nomes a Apresentar e IDs** contém os nomes, os IDs e os proprietários das capacidades, áreas de trabalho e cargas de trabalho.

## <a name="monitor-power-bi-embedded-capacity"></a>Monitorizar a capacidade do Power BI Embedded

Também pode utilizar a aplicação Métricas de Capacidade do Power BI Premium para monitorizar as capacidades *SKU A* no Power BI Embedded. Essas capacidades serão apresentadas no relatório, desde que seja administrador da capacidade. No entanto, a atualização do relatório falhará a menos que conceda determinadas permissões ao Power BI relativamente aos SKUs A:

1. Abra a capacidade no portal do Azure.

1. Clique em **Controlo de acesso (IAM)** e adicione a aplicação “Power BI Premium” à função de leitor. Se não conseguir encontrar a aplicação pelo nome, poderá também adicioná-la pelo seu ID de cliente: cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Permissões do Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Pode monitorizar a utilização das capacidades do Power BI Embedded na aplicação ou no portal do Azure, mas não no portal de administração do Power BI.

## <a name="basic-monitoring-in-the-admin-portal"></a>Monitorização básica no portal de administração

A área **Definições de capacidade** do portal de administração fornece quatro medidores que indicam as cargas colocadas e os recursos utilizados pela sua capacidade nos últimos sete dias. Estes quatro mosaicos trabalham numa janela de tempo por hora, que indica quantas horas nos últimos sete dias a métrica correspondente foi superior a 80%. Esta métrica indica uma degradação potencial para a experiência do utilizador final.

![Utilização nos 7 dias](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrica** | **Descrição** |
| --- | --- |
| CPU |Número de vezes que a CPU excedeu os 80% de utilização. |
| Degradação de Memória |Representa a pressão de memória nos seus núcleos de back-end. Especificamente, esta é uma métrica da frequência com que os conjuntos de dados são limpos da memória devido à pressão de memória resultante da utilização de múltiplos conjuntos de dados. |
| Utilização de Memória |Utilização de memória média, representada em gigabytes (GB). |
| DQ/s | Número de vezes que a contagem de DirectQueries e Ligações em Direto excedeu os 80% de limite. <br> * Limitamos o número total de consultas DirectQuery e de ligações em direto por segundo.* Os limites são 30/s para P1, 60/s para P2 e 120/s para P3. * A contagem de DirectQueries e consultas de ligação em direto contam para a limitação indicada acima. Por exemplo, se tiver 15 DirectQueries e 15 ligações em direto num segundo, atingiu a limitação<br>* Isto aplica-se igualmente às ligações no local e na nuvem. |
|  |  |

As métricas refletem a utilização ao longo da semana anterior.  Se quiser consultar uma vista mais detalhada das métricas, pode fazê-lo ao clicar num dos mosaicos de resumo.  Isto permite-lhe ter acesso a gráficos detalhados para cada uma das métricas da sua capacidade premium. O gráfico seguinte mostra os detalhes da métrica de CPU.

![Gráfico de utilização detalhado da CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Estes gráficos são resumidos à hora para a semana anterior e podem ajudar a isolar alturas em que tenham ocorrido eventos especificamente relacionados com o desempenho na sua capacidade premium.

Também pode exportar os dados subjacentes a qualquer uma das métricas para um ficheiro .csv.  Esta exportação irá fornecer-lhe informações detalhadas em intervalos de três minutos para cada dia da semana anterior.

## <a name="next-steps"></a>Próximos passos

Agora que tem uma noção de como monitorizar as capacidades do Power BI Premium, saiba mais sobre as capacidades de otimização.

> [!div class="nextstepaction"]
> [Gestão e otimização do recurso de capacidades do Power BI Premium](service-premium-understand-how-it-works.md)
