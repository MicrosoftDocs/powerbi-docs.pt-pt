---
title: Utilização e otimização da memória de capacidade Power BI Premium
description: Compreenda a gestão e otimização da memória de capacidade Power BI Premium.
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: powerbi
ms.component: powerbi-admin
ms.author: mblythe
ms.reviewer: mblythe
author: mgblythe
manager: kfile
ms.openlocfilehash: aee7fb94f1e132783fc2b7791f7e634c903f7aa6
ms.sourcegitcommit: 1574ecba7530e6e0ee97235251a3138fb0e4789b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40257220"
---
# <a name="power-bi-premium-capacity-resource-management-and-optimization"></a>Gestão e otimização do recurso de capacidade Power BI Premium

Este artigo descreve como o serviço Power BI Premium gere os recursos e fornece sugestões para o planeamento e otimização da sua solução.

## <a name="premium-capacity-memory-management"></a>Gestão da memória de capacidade Premium

 A memória de capacidade Premium é consumida por:

* Memória utilizada pelo conjuntos de dados carregados
* Memória utilizada pela atualização de conjuntos de dados (agendada e a pedido)
* Memória utilizada pelas consultas de relatórios

Quando um pedido é emitido em relação a um conjunto de dados publicado na sua capacidade, esse conjunto de dados é carregado na memória de armazenamento persistente (também denominado carregamento de imagem). Manter o conjunto de dados carregado na memória ajuda na resposta rápida a consultas futuras para este conjunto de dados. Além da memória necessária para manter o conjunto de dados carregado na memória, as consultas de relatório e as atualizações de conjuntos de dados também consumem memória adicional.

### <a name="dataset-memory-estimation"></a>Estimativa da memória do conjunto de dados

Ao tentar carregar um conjunto de dados para a memória, o Power BI calcula a quantidade de memória de que o conjunto de dados vai precisar para concluir o comando pedido. Os conjuntos de dados na memória tendem a ser superiores em tamanho do que quando estão guardados no disco. Durante a atualização de um conjunto de dados, a capacidade da memória requer, pelo menos, o dobro da quantidade de memória que é preciso do que quando está inativo.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Sobreconsolidar capacidade, expulsão e recarregamento de conjuntos de dados

O Power BI Premium dá-lhe a vantagem de sobreconsolidar a sua capacidade. Por exemplo, pode publicar mais conjuntos de dados do que a capacidade da memória pode suportar. Se os conjuntos de dados publicados na sua capacidade precisam de mais memória de o que é suportado na capacidade, alguns dos conjuntos de dados serão armazenados em separado num armazenamento persistente. O armazenamento persistente faz parte do armazenamento de 100 TB associado a cada uma das suas capacidades.

Então, quais são os conjuntos de dados que permanecem na memória e o que acontece aos outros conjuntos de dados? Tal como foi descrito anteriormente, quando um pedido é emitido em relação a um conjunto de dados, este é carregado para a memória (carregamento de imagem). O pedido pode ser uma consulta de relatório ou uma operação de atualização.

Uma vez que pode sobreconsolidar a capacidade, a capacidade também pode enfrentar pressão de memória. Quando a capacidade enfrenta pressão de memória (porque um novo conjunto de dados tem de ser carregado ou as consultas em certos conjuntos de dados carregados aumentam os requisitos de memória), o nó *expulsa um ou mais conjuntos de dados* que estejam a ocupar a memória da capacidade. Os conjuntos de dados que estão inativos (ou seja, em que não exista nenhuma operação de consulta/atualização em execução) são os primeiros a ser expulsos, sendo que a ordem de expulsão tem como base a "utilização menos recente" (LRU). Se os novos comandos forem emitidos para o conjunto de dados expulso, o serviço tenta recarregá-lo na memória, expulsando potencialmente outros conjuntos de dados. Este comportamento permite uma utilização mais eficiente ao permitir que a capacidade sirva muitos mais conjuntos de dados do que a sua memória consegue suportar.

Carregar um conjunto de dados para a memória é uma operação bastante dispendiosa. Consoante o tamanho do conjunto de dados, pode demorar de alguns segundos para os conjuntos de dados pequenos, a dezenas de segundos ou até minutos para os conjuntos de dados grandes, como os de ~10 GB. A capacidade Premium tenta minimizar o número de vezes que a capacidade precisa de ser carregada ao manter os conjuntos de dados menos utilizados recentemente na memória durante o máximo de tempo possível. Quando for precisa mais memória, têm de ser excluídos alguns conjuntos de dados e o sistema vai tentar escolher aquele que tiver o menor impacto sobre a experiência de utilizador. Quando for precisa mais memória, têm de ser excluídos alguns conjuntos de dados e o sistema vai tentar escolher aquele que tiver o menor impacto sobre a experiência de utilizador. Por exemplo, o sistema evitará expulsar conjuntos de dados que foram utilizados ativamente nos últimos minutos, porque é provável que voltem a ser consultados muito em breve.

O processo de expulsão em si é uma operação rápida. Se o conjunto de dados não estiver em utilização ativa no momento da expulsão, o utilizador não poderá determinar um grande impacto resultante da expulsão. No entanto, se demasiados conjuntos de dados estiverem em utilização ativa ao mesmo tempo e não existir memória suficiente para os conter a todos, poderão ocorrer bastantes expulsões. Tal pode levar a uma situação de “degradação”, em que os conjuntos de dados estão constantemente a ser expulsos e recarregados, sendo que os utilizadores podem constatar uma diminuição significativa nos tempos de resposta e no desempenho.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Requisito de memória de atualização do conjunto de dados a competir com um requisito de memória de conjunto de dados ativo

Os conjuntos de dados podem ser atualizados de forma agendada ou a pedido pelos utilizadores. Conforme foi descrito anteriormente, a memória necessária para as atualizações completas tem, no mínimo, o dobro do tamanho da memória dos conjuntos de dados carregados e inativos. Antes do início da atualização, calcula-se um requisito de memória de atualização. Se o requisito de memória total for superior à memória disponível na capacidade, alguns conjuntos de dados são expulsos. Os candidatos à expulsão são escolhidos pela ordem de conjuntos de dados menos utilizados recentemente, ou seja, o serviço tenta manter o maior número possível de conjuntos de dados utilizados recentemente na memória.

Se a memória necessária não estiver disponível, apesar de expulsão, a atualização é colocada na fila para ser repetida. O serviço repete até ser bem-sucedido ou até ser iniciada uma nova ação de atualização.

Se uma consulta interativa for emitida para qualquer conjunto de dados na capacidade e não existir memória disponível suficiente devido a uma atualização em curso, esse pedido falha e tem de ser repetido pelo utilizador.

## <a name="cpu-resource-management-in-premium-capacity"></a>Gestão de recursos da CPU na capacidade Premium

Existem dois principais consumidores de recursos da CPU:

- Consultas de relatórios
- Atualização (processamento)

### <a name="queries-from-reports"></a>Consultas de relatórios

As consultas de relatórios consomem recursos da CPU da sua capacidade. Se o seu relatório tiver algumas consultas que são ineficazes ou se tiver muitos utilizadores em simultâneo, podem consumir uma grande quantidade de recursos da CPU e a capacidade existente pode não ser suficiente para processar a carga.

### <a name="refresh-parallelization-policy"></a>Política de paralelização de atualização

A memória não é o único recurso que pode restringir a atualização de conjuntos de dados. O número de núcleos virtuais num servidor também pode ser um fator. Uma vez que cada operação de atualização exige um determinado número de núcleos virtuais, há um limite para as atualizações que podem ser executadas em paralelo. O limite por SKU está indicado em detalhe na tabela seguinte. As atualizações adicionais que excedam estes limites são colocados em fila de espera.

 | SKU  | Núcleos virtuais de back-end  | Paralelismo de atualização do modelo   |
 | --- | --- | --- |
 | A1  | 0,5  | 1  |
 | A2  | 1  | 2  |
 | A3  | 2  | 3  |
 | A4  | 4  | 6  |
 | A5  | 8  | 12  |
 | A6  | 16  | 24  |
 | EM1  | 0,5  | 1  |
 | EM2  | 1  | 2  |
 | EM3  | 2  | 3  |
 | P1  | 4  | 6  |
 | P2  | 8  | 12  |
 | P3  | 16  | 24  |
 | P4  | 32  | 48  |
 | P5  | 64  | 96  |

 > [!TIP]
> Se as atualizações se estiverem a atrasar, verifique o número de atualizações paralelas suportado pela sua capacidade.

## <a name="example-scenarios"></a>Cenários de exemplo

Seguem-se descrições de alguns cenários comuns e as medidas tomadas pelo serviço:

 **Vinte atualizações agendadas submetidas todas ao mesmo tempo** – o Power BI tenta iniciar as primeiras *x* atualizações ao mesmo tempo. O valor para *x* é determinado pela política de paralelização de atualização dessa SKU. Se o Power BI não conseguir obter memória suficiente ao expulsar conjuntos de dados inativos (conjuntos de dados não utilizados recentemente), nem todas as *x* atualizações serão iniciadas ao mesmo tempo. Qualquer atualização que não se possa iniciar é colocada na fila até poder.

 **Duas atualizações em execução ao mesmo tempo e há memória suficiente para concluir apenas uma** – a que pode ser concluída é iniciada. A outra é repetida mais tarde.

 **Grande número de conjuntos de dados a ser consultado enquanto vários conjuntos de dados estão a ser atualizados** – se não estiver disponível memória suficiente, o Power BI tenta parar as atualizações ativas para dar prioridade às consultas interativas. Esta medida diminui o desempenho da atualização.

 **Conjunto de dados que requer demasiada memória para ser atualizado com o tamanho atual da capacidade** – a atualização vai falhar. Não ocorrem tentativas para obter mais memória por meio de expulsão.

 **Atualizar um conjunto de dados único que possui um pico de pedidos grande na memória** – se o pico de pedidos for maior do que a quantidade de memória que pode ser obtida ao expulsar conjuntos de dados inativos, a atualização é repetida mais tarde quando existir memória suficiente para processar o pico de pedidos.

 **A consulta é executada para um conjunto de dados que não consegue obter memória suficiente ao expulsar todos os conjuntos de dados inativos e atualiza** – essas consultas falham. Para estes tipos de requisitos de carga de trabalho, deve ser comprada uma capacidade superior.

## <a name="troubleshooting-and-testing"></a>Resolução de problemas e testes

Se os relatórios estiverem lentos ou não responderem, comece por testar apenas um utilizador no relatório. Em seguida, comece a aumentar a carga de utilizadores em simultâneo para encontrar o limite. Em muitos casos, a otimização do DAX (consultas de relatório) pode alterar significativamente o desempenho dos relatórios (e aumentar o número de utilizadores em simultâneo suportados pela sua capacidade).

Utilize a capacidade Power BI Embedded no Azure para testar SKUs diferentes e determine o melhor SKU Premium para a carga de trabalho esperada. O SKU A4 do Power BI Embedded é igual ao P1, A5 = P2 e A6 = P3. No Azure, pode alternar facilmente entre os SKUs ao aumentar e reduzir verticalmente no portal do Azure. Quando encontrar o SKU que funciona melhor para a sua carga de trabalho e tiver terminado os testes, pode eliminar o SKU.

Em certos casos, a abertura de um ficheiro PBIX do modelo no computador e a verificação do consumo de memória e de CPU é uma ação bastante esclarecedora do problema. Este procedimento não ajuda em modelos muito grandes, mas, para alguns modelos mais pequenos, tente abrir, atualizar e consultar o modelo a partir do seu computador. Verifique o tamanho do modelo, a memória e a CPU consumida quando abrir o modelo. Experimente atualizar e consultar. Utilize o Gestor de tarefas para verificar o consumo da Memória e da CPU relativo ao ficheiro PBIX local). Por vezes, essas métricas no seu computador podem indicar que essa capacidade premium inferior, como P1/P2, pode não funcionar para a sua solução.
