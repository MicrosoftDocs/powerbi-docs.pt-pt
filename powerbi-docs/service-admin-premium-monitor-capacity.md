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
ms.date: 10/09/2018
LocalizationGroup: Premium
ms.openlocfilehash: b2627950ea51239acb19972fde3244f3bd158255
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48909228"
---
# <a name="monitor-power-bi-premium-and-power-bi-embedded-capacities"></a>Monitorizar as capacidades no Power BI Premium e no Power BI Embedded

Este artigo fornece uma descrição geral da monitorização das métricas das capacidades do Power BI Premium. Monitorizar a utilização das capacidades permite-lhe ter uma abordagem informada para gerir as suas capacidades.

Pode monitorizar a capacidade com a aplicação Métricas de Capacidade do Power BI Premium ou no portal de administração. Recomendamos a aplicação, porque fornece muitos mais detalhes, apesar deste artigo abordar as duas opções.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UgsjMbhi_Bk?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="install-the-premium-capacity-metrics-app"></a>Instalar a aplicação Métricas de Capacidade Premium

Pode ir diretamente para a [aplicação Métricas de Capacidade Premium](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) ou instalá-la tal como faz com as outras aplicações no Power BI.

1. No Power BI, clique em **Aplicações**.

    ![Ir para as Aplicações](media/service-admin-premium-monitor-capacity/apps.png)

2. No lado direito, clique em **Obter aplicações**.

3. Na categoria **Aplicações**, procure **Aplicação Métricas de Capacidade do Power BI Premium**.

4. Precisa de uma subscrição para instalar a aplicação.

Agora que instalou a aplicação, pode ver as métricas sobre as capacidades na sua organização. Vamos dar analisar algumas das métricas principais disponíveis.

## <a name="use-the-metrics-app"></a>Utilizar a aplicação de métricas

Quando abre a aplicação, é apresentado um dashboard com um resumo de todas as capacidades para as quais tem direitos de administrador.

![Dashboard da aplicação de métricas](media/service-admin-premium-monitor-capacity/app-dashboard.png)

O relatório tem três separadores, que descrevemos em mais detalhes nas seções a seguir.

* **Filtros aplicados a todas as páginas**: permite-lhe filtrar as outras páginas no relatório para uma capacidade específica.
* **Conjuntos de dados**: proporciona métricas detalhadas sobre o estado de funcionamento dos conjuntos de dados dentro das suas capacidades.
* **Sistema**: proporciona métricas gerais da capacidade, incluindo a memória e a utilização elevada da CPU. 

### <a name="filters-applied-to-all-pages-tab"></a>Separador Filtros aplicados a todas as páginas

O separador **Filtros aplicados a todas as páginas** permite-lhe selecionar uma capacidade, um conjunto de dados e um intervalo de datas nos últimos sete dias. Os filtros são aplicados, em seguida, a todos os mosaicos e páginas relevantes no relatório. Se não forem selecionados filtros, o relatório por predefinição mostrará as métricas da semana anterior para cada capacidade de que for proprietário.

![Separador Filtros](media/service-admin-premium-monitor-capacity/filters-tab.png)

### <a name="datasets-tab"></a>Separador Conjuntos de Dados

O separador **Conjuntos de dados** proporciona a maior parte das métricas na aplicação. Utilize os quatro botões na parte superior do separador para navegar para áreas diferentes: **Resumo**, **Atualizações**, **Consultas** e **Conjuntos de Dados**.

![Separador Conjuntos de Dados](media/service-admin-premium-monitor-capacity/datasets-tab.png)

#### <a name="summary-area"></a>Área de resumo

![Botão de resumo](media/service-admin-premium-monitor-capacity/summary-button.png)

A área **Resumo** mostra uma vista das suas capacidades com base em entidades, recursos de sistema e cargas de trabalho do conjunto de dados.

| | **Métricas** |
| --- | --- |
| **Entidades** | * O número de capacidades de que é proprietário<br> * O número distinto de conjuntos de dados na sua capacidade<br> * O número distinto de áreas de trabalho na sua capacidade |
| **Sistema** | * A utilização média da memória em GB nos últimos sete dias<br> * O mais alto consumo de memória em GB nos últimos sete dias e a hora local em que ocorreu<br> * O número de vezes que a CPU excedeu o valor de 80% dos limiares nos últimos sete dias, dividido em registos de três minutos<br> * A maioria das vezes em que a CPU excedeu o valor de 80% nos últimos sete dias, dividido em registos de uma hora e a hora local em que ocorreram<br> * O número de vezes que a Consulta direta/Ligações em direto excederam o valor de 80% dos limiares nos últimos sete dias, dividido em registos de três minutos<br> * A maioria das vezes em que a Consulta direta/Ligações em direto excederam o valor de 80% nos últimos sete dias, dividido em registos de uma hora e a hora local em que ocorreram |
| **Cargas de Trabalho do Conjunto de Dados** | * O número total de atualizações nos últimos sete dias<br> * O número total de atualizações com êxito nos últimos sete dias<br> * O número total de atualizações com falha nos últimos sete dias<br> * O número total de atualizações com falha devido a memória esgotada<br> * A duração média da atualização é medida em minutos, o tempo necessário para concluir a operação<br> * O tempo médio de espera da atualização é medido em minutos, o desfasamento médio entre a hora agendada e o início da operação<br> * O número total de consultas executadas nos últimos sete dias<br> * O número total de consultas com êxito nos últimos sete dias<br> * O número total de consultas com falhas nos últimos sete dias<br> * A duração média da consulta é medida em minutos, o tempo necessário para concluir a operação<br> * O número total de modelos expulsos devido à pressão de memória |
|  |  |

#### <a name="refreshes-area"></a>Área de atualizações

![Botão de atualizações](media/service-admin-premium-monitor-capacity/refreshes-button.png)

A área **Atualizações** lista as atualizações concluídas, as medidas com êxito, o tempo de espera médio/máx. de atualização e a duração média/máx. da atualização segmentada por conjuntos de dados nos últimos sete dias. Os dois gráficos na parte inferior mostram as atualizações versus o consumo de memória em GB e os tempos de espera médios divididos em registos de uma hora, comunicados na hora local. Os gráficos de barras na parte superior listam os cinco conjuntos de dados principais com base no tempo médio necessário para concluir a atualização do conjunto de dados (duração da atualização) e no tempo médio de espera de atualização. Os vários picos de tempo de espera da atualização são indicativos da execução frequente da capacidade.

#### <a name="queries-area"></a>Área de consultas

![Botão de consultas](media/service-admin-premium-monitor-capacity/queries-button.png)

A área **Consultas** lista o número total de consultas executadas, o número total de consultas com contagem do tempo de espera para Consulta em direto/Consulta direta, duração média/máxima, tempo de espera médio/máximo comunicado em milissegundos dividido por conjuntos de dados, área de trabalho e registos de uma hora nos últimos sete dias. Os gráficos na parte inferior mostram as contagens de consultas, duração média (em milissegundos) e a média de tempo de espera (em milissegundos) vs. o consumo de memória em GB, dividido por registos de uma hora comunicados na hora local. Os dois gráficos principais à direita listam os cinco conjuntos de dados principais pela duração média de consulta e pelo tempo de espera necessário para concluir as consultas. Durações de consulta longas e tempos de espera longos são indicativos da capacidade de executar acessos frequentes. Também pode significar que um único conjunto de dados está a causar problemas e ainda é necessário mais investigação.

#### <a name="datasets-area"></a>Área de conjuntos de dados

![Botão de conjuntos de dados](media/service-admin-premium-monitor-capacity/datasets-button.png)

A área **Conjuntos de dados** mostra os conjuntos de dados concluídos expulsos devido à pressão de memória por hora.

### <a name="system-tab"></a>Separador Sistema

O separador **Sistema** mostra as vezes da utilização elevada da CPU (número de vezes que excedeu 80% da utilização), a utilização elevada da consulta direta/ligações em direto e o consumo de memória.

![Relatório do Sistema Premium](media/service-admin-premium-monitor-capacity/system-tab.png)

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
