---
title: Utilização e otimização da memória de capacidade Power BI Premium
description: Compreenda a gestão e otimização da memória de capacidade Power BI Premium.
ms.date: 10/18/2018
ms.topic: conceptual
ms.service: powerbi
ms.component: powerbi-admin
ms.author: mblythe
ms.reviewer: mblythe
author: mgblythe
manager: kfile
ms.openlocfilehash: 99c84aff932c7ce56a4aaa81d71e4583bce3e4c2
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641755"
---
# <a name="microsoft-power-bi-premium-capacity-resource-management-and-optimization"></a>Gestão e otimização de recursos de capacidade do Microsoft Power BI Premium

Este artigo descreve como o Power BI Premium gere recursos e também fornece exemplos e sugestões de resolução de problemas. Para obter uma descrição geral, veja [O que é o Power BI Premium?](service-premium.md).

## <a name="premium-capacity-memory-management"></a>Gestão da memória de capacidade Premium

 A memória de capacidade Premium é consumida por:

* Conjuntos de dados que são carregados para a memória
* Atualizações de conjuntos de dados (agendadas e a pedido)
* Consultas de relatório

Quando um pedido é emitido em relação a um conjunto de dados publicado na sua capacidade, esse conjunto de dados é carregado na memória de armazenamento persistente (também denominado carregamento de imagem). Manter o conjunto de dados carregado na memória ajuda na resposta rápida a consultas futuras para este conjunto de dados. Além da memória necessária para manter o conjunto de dados carregado na memória, as consultas de relatório e as atualizações de conjuntos de dados consomem memória adicional.

### <a name="dataset-memory-estimation"></a>Estimativa da memória do conjunto de dados

Ao tentar carregar um conjunto de dados para a memória, o Power BI calcula a quantidade de memória de que o conjunto de dados vai precisar para concluir o comando pedido. Os conjuntos de dados na memória tendem a ser superiores em tamanho do que quando estão guardados no disco. Durante a atualização de um conjunto de dados, o Power BI necessita de, pelo menos, o dobro da quantidade de memória que é preciso do que quando o conjunto de dados está inativo.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Sobreconsolidar capacidade, expulsão e recarregamento de conjuntos de dados

O Power BI Premium dá-lhe a vantagem de *sobreconsolidar* a sua capacidade. Por exemplo, pode publicar mais conjuntos de dados do que a sua capacidade pode suportar. Se os conjuntos de dados publicados precisarem de mais memória do que aquela que está disponível na capacidade, alguns dos conjuntos de dados serão armazenados em separado num armazenamento persistente. O armazenamento persistente faz parte do armazenamento de 100 TB associado a cada uma das suas capacidades.

Assim sendo, quais são os conjuntos de dados que permanecem na memória e o que acontece aos outros conjuntos de dados? Tal como foi descrito anteriormente, quando um pedido é emitido em relação a um conjunto de dados, este é carregado para a memória (carregamento de imagem). O pedido pode ser uma consulta de relatório ou uma operação de atualização. No entanto, uma vez que pode sobreconsolidar a capacidade, esta também pode sofrer pressão de memória. Quando uma capacidade sofre uma pressão de memória, o nó *expulsa* um ou mais conjuntos de dados da memória. Os conjuntos de dados que estiverem inativos (sem qualquer operação de consulta/atualização em execução) são os primeiros a serem expulsos. Em seguida, a ordem de expulsão é feita com base no critério "menos recentemente utilizado" (LRU). Se os novos comandos forem emitidos para o conjunto de dados expulso, o serviço tenta recarregá-lo na memória, expulsando potencialmente outros conjuntos de dados. Este comportamento permite uma utilização mais eficiente ao permitir que a capacidade sirva muitos mais conjuntos de dados do que a sua memória consegue suportar.

Carregar um conjunto de dados para a memória é uma operação bastante dispendiosa. Consoante o tamanho do conjunto de dados, pode demorar de alguns segundos para os conjuntos de dados pequenos, a dezenas de segundos ou até minutos para os conjuntos de dados de dimensão considerável, como os de ~10 GB. A capacidade Premium tenta minimizar o número de vezes que a capacidade precisa de ser carregada ao manter os conjuntos de dados menos utilizados recentemente na memória durante o máximo de tempo possível. Quando for precisa mais memória, têm de ser excluídos alguns conjuntos de dados e o sistema vai tentar escolher aquele que tiver o menor impacto sobre a experiência de utilizador. Quando for precisa mais memória, têm de ser excluídos alguns conjuntos de dados e o sistema vai tentar escolher aquele que tiver o menor impacto sobre a experiência de utilizador. Por exemplo, o sistema evitará expulsar conjuntos de dados que foram utilizados de forma ativa durante os últimos minutos. É provável que estes conjuntos de dados voltem a ser consultados muito em breve.

O processo de expulsão em si é uma operação rápida. Se o conjunto de dados não estiver em utilização ativa no momento da expulsão, o utilizador não poderá determinar um grande impacto resultante da expulsão. No entanto, se houverem demasiados conjuntos de dados a ser utilizados ativamente ao mesmo tempo e não existir memória suficiente para os conter a todos, poderão ocorrer várias expulsões. O excesso de conjuntos de dados ativos pode levar a uma situação de "degradação", em que os conjuntos de dados estão constantemente a ser expulsos e recarregados, sendo que os utilizadores podem constatar uma diminuição significativa nos tempos de resposta e no desempenho.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Requisito de memória de atualização do conjunto de dados a competir com um requisito de memória de conjunto de dados ativo

Os conjuntos de dados podem ser atualizados de forma agendada ou a pedido pelos utilizadores. Conforme foi descrito anteriormente, a memória necessária para as atualizações completas tem, no mínimo, o dobro do tamanho da memória dos conjuntos de dados carregados e inativos. Antes do início da atualização, calcula-se um requisito de memória de atualização. Se o requisito de memória total for superior à memória disponível na capacidade, alguns conjuntos de dados são expulsos. Mais uma vez, a expulsão é baseada num critério LRU.

Se a memória necessária não estiver disponível, apesar de expulsão, a atualização é colocada na fila para ser repetida. O serviço repete até ser bem-sucedido ou até ser iniciada uma nova ação de atualização.

Se uma consulta interativa for emitida para qualquer conjunto de dados na capacidade e não existir memória disponível suficiente devido a uma atualização em curso, esse pedido falha e tem de ser repetido pelo utilizador.

## <a name="cpu-resource-management-in-premium-capacity"></a>Gestão de recursos da CPU na capacidade Premium

Existem dois principais consumidores de recursos da CPU:

* Consultas de relatórios
* Atualização (processamento)

### <a name="queries-from-reports"></a>Consultas de relatórios

As consultas de relatórios consomem recursos da CPU na sua capacidade. Os relatórios com consultas ineficazes ou com muitos utilizadores em simultâneo podem consumir uma grande quantidade de recursos da CPU. A sua capacidade existente poderá não ser suficiente para processar a carga.

### <a name="refresh-parallelization-policy"></a>Política de paralelização de atualização

A memória não é o único recurso que pode restringir a atualização de um conjunto de dados. O número de núcleos virtuais num servidor também pode ser um fator. Devido a cada operação de atualização exigir um determinado número de núcleos virtuais, há um limite para as atualizações que podem ser executadas em paralelo. O limite por SKU está indicado em detalhe na tabela seguinte. As atualizações adicionais que excedam estes limites são colocadas em fila de espera.

 | SKU | Núcleos virtuais de back-end | Paralelismo de atualização do modelo |
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
> Se as atualizações estiverem atrasadas, verifique o número de atualizações paralelas suportado pela sua capacidade.

## <a name="example-scenarios"></a>Cenários de exemplo

Eis alguns cenários comuns e as medidas tomadas pelo serviço:

**Vinte atualizações agendadas submetidas ao mesmo tempo**. O Power BI tenta iniciar as primeiras *x* atualizações ao mesmo tempo. O valor para *x* é determinado pela política de paralelização de atualização dessa SKU. Se o Power BI não conseguir obter memória suficiente ao expulsar conjuntos de dados inativos (conjuntos de dados não utilizados recentemente), nem todas as *x* atualizações serão iniciadas ao mesmo tempo. Qualquer atualização que não consiga ser iniciada é colocada na fila até que seja possível.

**Duas atualizações em execução ao mesmo tempo e só há memória suficiente para concluir apenas uma**. É iniciada aquela que pode ser concluída. A outra é repetida mais tarde.

**Grande quantidade de conjuntos de dados a serem consultados enquanto vários conjuntos de dados estão a ser atualizados**. Se não houver memória suficiente disponível, o Power BI tenta parar as atualizações ativas para dar prioridade a consultas interativas. Esta medida diminui o desempenho da atualização.

**Conjunto de dados que requer demasiada memória para ser atualizado com o tamanho atual da capacidade**. A atualização falha. Não ocorrem tentativas para obter mais memória por meio de expulsão.

**Atualizar um único conjunto de dados que possui um pico de pedidos grande na memória**. Se o pico de pedidos for maior do que a quantidade de memória que pode ser obtida ao expulsar conjuntos de dados inativos, a atualização é repetida mais tarde quando existir memória suficiente para processar o pico de pedidos.

**A consulta é executada para um conjunto de dados que não consegue obter memória suficiente ao expulsar todos os conjuntos de dados inativos e atualiza**. Essa consulta falha. Para estes tipos de requisitos de carga de trabalho, deve ser comprada uma capacidade superior.

## <a name="troubleshooting-and-testing"></a>Resolução de problemas e testes

Se os relatórios estiverem lentos ou não responderem, comece por testar apenas um utilizador no relatório. Em seguida, comece a aumentar a carga de utilizadores em simultâneo para encontrar o limite. Em muitos casos, a otimização de consultas DAX pode alterar significativamente o desempenho dos seus relatórios. A otimização de consultas também aumenta o número de utilizadores em simultâneo que são suportados pela sua capacidade. [Monitorize a sua capacidade](service-admin-premium-monitor-capacity.md) para identificar potenciais problemas de desempenho.

Utilize a capacidade Power BI Embedded no Azure para testar SKUs diferentes e determine o melhor SKU Premium para a carga de trabalho esperada. O SKU A4 do Power BI Embedded é igual ao P1, A5 = P2 e A6 = P3. No Azure, pode alternar facilmente entre os SKUs ao aumentar e reduzir verticalmente no portal do Azure. Quando encontrar o SKU que funciona melhor para a sua carga de trabalho e tiver terminado os testes, pode eliminar o SKU.

Em certos casos, a abertura de um ficheiro do Power BI Desktop (.pbix) do modelo no computador e a verificação do consumo de memória e da CPU é uma ação bastante esclarecedora do problema. Este procedimento não ajuda em modelos muito grandes, mas, para alguns modelos mais pequenos, tente abrir, atualizar e consultar o modelo a partir do seu computador. Verifique o tamanho do modelo, a memória e a CPU consumida quando abrir o modelo. Experimente atualizar e consultar. Utilize o gestor de tarefas para verificar o consumo da memória e da CPU relativo ao ficheiro local. Por vezes, essas métricas no seu computador podem indicar que essa capacidade premium inferior, como P1/P2, pode não funcionar para a sua solução.

## <a name="next-steps"></a>Próximos passos

[Gerir as capacidades no Power BI Premium e no Power BI Embedded](service-admin-premium-manage.md)