---
title: Gerir capacidades Microsoft Power BI Premium
description: Descreve as tarefas de gestão para capacidades Power BI Premium.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 5e8becd877165f456793d99951544156a9314290
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881202"
---
# <a name="managing-premium-capacities"></a>Gerir as capacidades Premium

A gestão do Power BI Premium envolve a criação, a gestão e a monitorização de capacidades Premium. Este artigo fornece uma visão geral das capacidades; veja [Configurar e gerir capacidades](service-admin-premium-manage.md) para ver instruções passo a passo.

## <a name="creating-and-managing-capacities"></a>Criar e gerir capacidades

A página **Definições de Capacidade** do portal de Administração do Power BI apresenta o número de núcleos virtuais comprados e capacidades Premium disponíveis. A página permite que os administradores globais do Office 365 ou os administradores de serviço do Power BI criem capacidades Premium a partir de núcleos virtuais disponíveis ou modifiquem as capacidades Premium existentes.

Quando cria uma capacidade Premium, os administradores têm de definir:

- Nome da capacidade (exclusivo no inquilino).
- Administrador(es) de capacidade.
- Tamanho da capacidade.
- Região para residência de dados.

Pelo menos um Administrador de Capacidade tem de ser atribuído. Os utilizadores atribuídos como Administradores de Capacidade podem:

- Atribuir áreas de trabalho à capacidade.
- Gerir permissões de utilizador para adicionar mais Administradores de Capacidade ou utilizadores com permissões de atribuição (para lhes permitir que atribuam áreas de trabalho à capacidade).
- Gerir cargas de trabalho, para configurar a utilização máxima de memória para relatórios paginados e cargas de trabalho de fluxos de dados.
- Reiniciar a capacidade, para repor todas as operações devido a uma sobrecarga do sistema.

Os Administradores de Capacidade não podem aceder ao conteúdo da área de trabalho, a menos que sejam explicitamente atribuídos em permissões de área de trabalho. Também não têm acesso a todas as áreas de administração do Power BI (exceto se atribuídas explicitamente), como as métricas de utilização, os registos de auditoria ou as definições de inquilino. É importante ter em conta que os Administradores de Capacidade não dispõem de permissões para criar novas capacidades ou dimensionar as capacidades existentes. Os administradores são atribuídos consoante a capacidade, o que garante que só podem ver e gerir capacidades às quais estejam atribuídos.

O tamanho da capacidade é selecionado a partir de uma lista disponível de opções de SKU, que é restrita pelo número de núcleos virtuais disponíveis no conjunto. É possível criar várias capacidades a partir do conjunto, que podem ser originadas de uma ou mais SKUs compradas. Por exemplo, um SKU P3 (32 núcleos virtuais) poderia servir para criar três capacidades: um P2 (16 núcleos virtuais) e dois P1 (2 x 8 núcleos virtuais). O desempenho e escala melhorados podem ser obtidos com a criação de capacidades de tamanho menor, conforme descrito no artigo [Otimizar as Capacidades Premium](service-premium-capacity-optimize.md). A seguinte imagem mostra um exemplo de configuração para a organização fictícia da Contoso que consiste em cinco capacidades Premium (3 x P1 e 2 x P3), cada uma com áreas de trabalho e várias áreas de trabalho na capacidade partilhada.

![Um exemplo de configuração para a organização fictícia Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Uma capacidade Premium pode ser atribuída a uma região que não seja a região base do inquilino do Power BI, conhecida como multi-geo. A multi-geo fornece controlo administrativo sobre quais datacenters em regiões geográficas definidas em que o seu conteúdo de Power BI reside. A lógica para uma implementação multi-geo é normalmente para conformidade corporativa ou governamental, em vez de desempenho e dimensionamento. O carregamento de relatórios e dashboards ainda envolve pedidos de metadados à região base. Para saber mais, veja [Suporte da Multi-Geo para o Power BI Premium](service-admin-premium-multi-geo.md).

Os administradores de serviço do Power BI e os Administradores Globais do Office 365 podem modificar as capacidades Premium. Especificamente, podem:

- Alterar o tamanho da capacidade para aumentar ou reduzir a dimensão dos recursos.
- Adicionar ou remover Administradores de Capacidade.
- Adicionar ou remover utilizadores que têm permissões de atribuição.
- Adicionar ou remover cargas de trabalho adicionais.
- Alterar regiões.

São obrigatórias permissões de atribuição para atribuir uma área de trabalho a uma capacidade Premium específica. As permissões podem ser concedidas a toda a organização, utilizadores específicos ou grupos.

Por predefinição, as capacidades Premium suportam cargas de trabalho associadas à execução de consultas do Power BI. As capacidades Premium também suportam cargas de trabalho adicionais: **IA (Serviços Cognitivos)** , **Relatórios Paginados** e **Fluxos de dados**. Cada carga de trabalho exige a configuração da memória máxima (como uma percentagem da memória total disponível) que pode ser utilizada pela carga de trabalho. É importante compreender que o aumento das alocações de memória máxima pode influenciar o número de modelos ativos que podem ser alojados e o débito de atualizações. 

A memória é alocada aos fluxos de dados de forma dinâmica, mas é alocada aos relatórios paginados de forma estática. O motivo da alocação estática da memória máxima é que os relatórios paginados são executados num espaço independente protegido da capacidade. Deve ter atenção ao definir a memória de relatórios paginados, pois tal reduz a memória disponível para o carregamento de modelos. Para saber mais, veja [Definições de memória predefinidas](service-admin-premium-workloads.md#default-memory-settings).

A eliminação de uma capacidade Premium é possível e não resultará na eliminação das respetivas áreas de trabalho e conteúdo. Em vez disso, move quaisquer áreas de trabalho atribuídas para a capacidade partilhada. Quando a capacidade Premium foi criada numa região diferente, a área de trabalho é movida para a capacidade partilhada da região base.

### <a name="assigning-workspaces-to-capacities"></a>Atribuir áreas de trabalho a capacidades

As áreas de trabalho podem ser atribuídas a uma capacidade Premium no Portal de administração do Power BI ou, para uma área de trabalho, no painel **Área de trabalho**.

Os Administradores de Capacidade, bem como os Administradores Globais do Office 365 ou os administradores de serviço do Power BI, podem atribuir áreas de trabalho em massa no portal de Administração do Power BI. A atribuição em massa pode aplicar-se a:

- **Áreas de trabalho por utilizadores** – Todas as áreas de trabalho pertencentes a esses utilizadores, incluindo áreas de trabalho pessoais, são atribuídas à capacidade Premium. Tal incluirá a reatribuição de áreas de trabalho quando já estiverem atribuídas a uma capacidade Premium diferente. Além disso, os utilizadores também recebem permissões de atribuição de áreas de trabalho.

- **Áreas de trabalho específicas**
- **Áreas de trabalho de toda a organização** – Todas as áreas de trabalho, incluindo áreas de trabalho pessoais, são atribuídas à capacidade Premium. Todos os utilizadores atuais e futuros também recebem permissões de atribuição de áreas de trabalho. Esta abordagem não é recomendada. É preferível uma abordagem mais direcionada.

Uma área de trabalho pode ser adicionada a uma capacidade Premium com o painel **Área de Trabalho**, desde que o utilizador seja um administrador de área de trabalho e tenha permissões de atribuição.

![Utilizar o painel Área de trabalho para atribuir uma área de trabalho a uma capacidade Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Os administradores de áreas de trabalho podem remover uma área de trabalho de uma capacidade (para capacidade partilhada) sem ser preciso uma permissão de atribuição. A remoção de áreas de trabalho de capacidades dedicadas realoca efetivamente a área de trabalho para a capacidade partilhada. Observe que a remoção de uma área de trabalho de uma capacidade Premium pode ter consequências negativas que resultam, por exemplo, em conteúdo partilhado que fica indisponível para os utilizadores com uma licença Gratuita do Power BI ou na suspensão da atualização agendada quando excedem as permissões suportadas pelas capacidades partilhadas.

No serviço Power BI, uma área de trabalho atribuída a uma capacidade Premium é facilmente identificada pelo ícone de losango que adorna o nome da área de trabalho.

![Identificar uma área de trabalho atribuída a uma capacidade Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Monitorização de capacidades

A monitorização das capacidades Premium indica aos administradores o desempenho das capacidades. As capacidades podem ser monitorizadas com o Portal de Administração do Power BI ou com a aplicação **Métricas de Capacidade do Power BI Premium** (Power BI).

### <a name="power-bi-admin-portal"></a>Portal de administração do Power BI

No portal de Administração, para cada capacidade, o separador **Estado de Funcionamento** fornece métricas de resumo da capacidade e de cada carga de trabalho ativada. As métricas mostram uma média ao longo dos últimos sete dias.  

Ao nível da capacidade, as métricas são cumulativas de todas as cargas de trabalho ativadas. São fornecidas as seguintes métricas:

- **UTILIZAÇÃO DA CPU** – Fornece a utilização média da CPU como uma percentagem da CPU total disponível para a capacidade.  
- **UTILIZAÇÃO DE MEMÓRIA** - Fornece a utilização média da memória (em GB) como um total de memória disponível para a capacidade. 

Para cada carga de trabalho ativada, a utilização da CPU e a utilização da memória são fornecidas, bem como uma série de métricas específicas de carga de trabalho. Por exemplo, para a carga de trabalho de Fluxo de dados, a **Contagem Total** mostra o total de atualizações de cada fluxo de dados e a **Duração Média** mostra a duração média da atualização para o fluxo de trabalho.

![Separador Estado de Funcionamento de Capacidade no portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Para saber mais sobre todas as métricas disponíveis para cada carga de trabalho, veja [Monitor capacities in the Admin portal](service-admin-premium-monitor-portal.md) (Monitorizar capacidades no Portal de administração).

As capacidades de monitorização no portal de Administração do Power BI são concebidas para fornecer um resumo rápido das principais métricas de capacidade. Para uma monitorização mais detalhada, recomendamos a utilização da aplicação **Power BI Premium Capacity Metrics**.

### <a name="power-bi-premium-capacity-metrics-app"></a>Aplicação de Métricas de Capacidade do Power BI Premium

A aplicação [Power BI Premium Capacity Metrics](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) é uma aplicação do Power BI disponível para administradores de capacidade e é instalada como qualquer outra aplicação do Power BI. Contém um dashboard e um relatório.

![Aplicação de Métricas de Capacidade do Power BI Premium](media/service-premium-capacity-manage/capacity-metrics-app.png)

Quando a aplicação se abre, o dashboard é carregado para apresentar vários mosaicos que exprimem uma vista agregada sobre todas as capacidades das quais o utilizador é um Administrador de Capacidade. O esquema do dashboard inclui cinco secções principais:

- **Visão Geral** – Versão da aplicação, número de capacidades e áreas de trabalho
- **Resumo do Sistema** – Métricas de memória e CPU
- **Resumo de Conjunto de Dados** – Número de conjuntos de dados, métricas de DQ/LC, de atualizações e de consultas
- **Resumo do Fluxo de Dados** – Número de fluxos de dados e métricas de conjuntos de dados
- **Resumo do Relatório Paginado** – Métricas de atualizações e de vistas

O relatório subjacente, a partir do qual os mosaicos do dashboard foram afixados, pode ser acedido ao clicar em qualquer mosaico do dashboard. Fornece uma perspetiva mais detalhada de cada uma das secções do dashboard e dá suporte à filtragem interativa. 

A filtragem pode ser obtida ao definir segmentações por intervalo de datas, capacidade, área de trabalho e carga de trabalho (relatório, conjunto de dados, fluxo de dados) e ao selecionar elementos em elementos visuais de relatórios para filtrar de forma cruzada a página do relatório. A filtragem cruzada é uma técnica poderosa para restringir períodos de tempo, capacidades, áreas de trabalho, conjuntos de valores, etc. específicos e pode ser muito útil quando se executa uma análise da causa raiz.

Para obter informações detalhadas sobre as métricas de relatório e de dashboard na aplicação, veja [Monitorizar as capacidades Premium com a aplicação](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretar as métricas

As métricas devem ser monitorizadas para estabelecer uma compreensão base da utilização de recursos e da atividade de cargas de trabalho. Se a capacidade se tornar lenta, é importante compreender quais métricas deve monitorizar e as conclusões que pode tirar.

Idealmente, as consultas devem estar concluídas num segundo para proporcionar experiências reativas aos utilizadores de relatórios e permitir um maior débito de consultas. Normalmente, não é preocupante quando processos em segundo plano, incluindo atualizações, demoram mais tempo a serem concluídos.

Em geral, os relatórios lentos podem ser uma indicação de uma capacidade sobrecarregada. Quando os relatórios não podem ser carregados, é uma indicação de uma capacidade sobrecarregada. Em qualquer situação, a causa raiz pode ser atribuível a vários fatores, incluindo:

- As **consultas falhadas** indicam certamente a pressão da memória e que um modelo não pôde ser carregado na memória. O serviço Power BI tentará carregar um modelo durante 30 segundos antes de falhar.

- Os **tempos de espera de consulta excessivos** podem dever-se a vários motivos:
  - A necessidade de o serviço Power BI remover primeiro modelo(s) e, em seguida, carregar o modelo a ser consultado (lembre-se de que as taxas de expulsão de conjuntos de dados mais altas em si não são uma indicação de sobrecarga de capacidade, a menos que sejam acompanhadas por tempos de espera de consulta longos que indiquem uma degradação da memória).
  - Tempos de carregamento de modelos (especialmente a espera para carregar um modelo grande para a memória).
  - Consultas de execução prolongada.
  - Demasiadas ligações LC\DQ (que excedem os limites de capacidade).
  - Saturação da CPU.
  - Designs de relatório complexos com um número excessivo de elementos visuais numa página (lembre-se de que cada elemento visual é uma consulta).

- As **durações de consulta longas** podem indicar que os designs de modelo não são otimizados, especialmente quando vários conjuntos de dados estão ativos numa capacidade e apenas um conjunto de dados está a produzir durações de consulta longas. Tal sugere que a capacidade tem recursos suficientes e que o conjunto de dados em questão esteja abaixo do ideal ou seja apenas lento. As consultas de execução prolongada podem ser problemáticas, pois podem bloquear o acesso aos recursos exigidos por outros processos.
- Os **tempos de espera de atualização longos** indicam memória insuficiente devido a muitos modelos ativos que consumem memória ou que uma atualização problemática está a bloquear outras atualizações (excedendo os limites de atualização paralela).

Uma explicação mais detalhada de como usar as métricas é abordada no artigo [Otimizar as capacidades Premium](service-premium-capacity-optimize.md).

## <a name="acknowledgements"></a>Agradecimentos

Este artigo foi escrito por Peter Myers, MVP de Plataforma de Dados e especialista independente de BI na [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Otimizar as capacidades Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurar cargas de trabalho numa capacidade Premium](service-admin-premium-workloads.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

