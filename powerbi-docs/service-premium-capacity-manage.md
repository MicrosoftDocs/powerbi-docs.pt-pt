---
title: Gerir as capacidades do Microsoft Power BI Premium
description: Descreve as tarefas de gestão para as capacidades do Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565232"
---
# <a name="managing-premium-capacities"></a>Gerir capacidades Premium

Gerir o Power BI Premium envolve criar, gerir e monitorizar as capacidades Premium.

## <a name="creating-and-managing-capacities"></a>Criar e gerir as capacidades

O **definições de capacidade** página do portal de administração do Power BI apresenta o número de núcleos virtuais comprados e as capacidades Premium disponíveis. A página permite que os administradores globais do Office 365 ou administradores de serviço do Power BI para criar capacidades Premium a partir de núcleos virtuais disponíveis ou para modificar as capacidades de Premium existentes.

Ao criar uma capacidade Premium, os administradores são necessários para definir:

- Nome da capacidade (exclusivo no inquilino).
- Capacidade admin(s).
- Tamanho da capacidade.
- Região do residência dos dados.

Tem de ser atribuído pelo menos um administrador de capacidade. Os utilizadores atribuídos como administradores de capacidade podem:

- Atribua áreas de trabalho à capacidade.
- Gerir permissões de utilizador, para adicionar os administradores de capacidade ou utilizadores com permissões de atribuição (para que eles possam atribuir áreas de trabalho à capacidade) adicionais.
- Gerir cargas de trabalho, para configurar a utilização de memória máxima para relatórios paginados e cargas de trabalho de fluxos de dados.
- Reinicie a capacidade, para repor todas as operações devido a uma sobrecarga de system.

Os administradores de capacidade não é possível aceder a conteúdo de área de trabalho, a menos que explicitamente atribuídas permissões de área de trabalho. Eles também não tem acesso a todas as áreas de administração do Power BI (a menos que explicitamente atribuídos), como a métrica de utilização, registos de auditoria ou as definições de inquilino. Importante, os administradores de capacidade não tem permissões para criar novas capacidades ou aumentar as capacidades existentes. Os administradores são atribuídos individualmente por capacidade, garantindo que eles podem apenas ver e gerir as capacidades ao qual são atribuídos.

Tamanho da capacidade é selecionado a partir de uma lista disponível das opções de SKU, que é limitada pelo número de núcleos virtuais disponíveis no conjunto. É possível criar vários recursos do conjunto, que pode ser obtido a partir de um ou mais adquirido SKUs. Por exemplo, um SKU P3 (32 núcleos) poderiam ser usados para criar as capacidades de três: um P2 (16 núcleos) e P1 duas (2 x 8 núcleos). Melhoria do desempenho e dimensionamento podem ser conseguidos através da criação de menores tamanho as capacidades, conforme descrito no [otimizando as capacidades de Premium](service-premium-capacity-optimize.md) artigo. A imagem seguinte mostra um exemplo de configuração para a organização Contoso fictícia consiste em cinco capacidades de Premium (3 x P1 e 2 x P3) com cada áreas de trabalho de aplicação que contém e várias áreas de trabalho na capacidade partilhada.

![Um exemplo de configuração para a organização fictícia de Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Uma capacidade Premium pode ser atribuída a uma região diferente da região base do inquilino do Power BI, conhecido como multi-geo. Multi-geo proporciona controle administrativo sobre quais centros de dados dentro de regiões geográficas definidas, o conteúdo do Power BI reside. A lógica para uma implementação de multi-geo é normalmente para empresariais ou conformidade do Governo, em vez de desempenho e dimensionamento. Relatório e o carregamento do dashboard ainda envolve a pedidos para a região base para os metadados. Para obter mais informações, consulte [Multi-Geo suporte do Power BI Premium](service-admin-premium-multi-geo.md).

Os administradores de serviço do Power BI e os administradores globais do Office 365, podem modificar capacidades Premium. Especificamente, pode:

- Altere o tamanho da capacidade para aumentar verticalmente ou reduzir verticalmente recursos.
- Adicionar ou remover os administradores de capacidade.
- Adicionar ou remover utilizadores que têm permissões de atribuição.
- Adicionar ou remover as cargas de trabalho adicionais.
- Alterar as regiões.

São necessárias permissões de atribuição para atribuir uma área de trabalho a uma capacidade Premium específica. As permissões podem ser concedidas a toda a organização, utilizadores específicos ou grupos.

Por predefinição, as capacidades Premium suportam cargas de trabalho associadas à execução de consultas do Power BI. Capacidades Premium também suportam cargas de trabalho adicionais: **(Os serviços cognitivos) de IA**, **relatórios paginados**, e **fluxos de dados**. Cada carga de trabalho necessita de configurar a memória máxima (como percentagem do total de memória disponível), que pode ser utilizada pela carga de trabalho. É importante compreender que a aumentar as alocações de memória máximo pode afetar o número de modelos de Active Directory que pode ser alojada e a taxa de transferência de atualizações. 

Memória é atribuída dinamicamente ao fluxos de dados, mas é atribuída estaticamente para relatórios paginados. O motivo para alocar estaticamente a memória máxima é que os relatórios paginados são executadas dentro de um espaço contido seguro da capacidade. Deve ter cuidado ao definição paginados memória de relatórios, pois reduz a memória disponível para carregar os modelos. Para obter mais informações, consulte a [predefinições de memória](service-admin-premium-workloads.md#default-memory-settings).

A eliminar uma capacidade Premium, é possível e não resultará na eliminação do seus espaços de trabalho e o conteúdo. Em vez disso, move todas as áreas de trabalho atribuídas para capacidade partilhada. Quando a capacidade de Premium foi criada numa região diferente, a área de trabalho é movida para uma capacidade partilhada da região principal.

### <a name="assigning-workspaces-to-capacities"></a>Atribuir áreas de trabalho para as capacidades

Áreas de trabalho podem ser atribuídas a uma capacidade Premium no portal de administração do Power BI ou, para uma área de trabalho de aplicação, no **área de trabalho** painel.

Os administradores de capacidade, bem como os administradores globais do Office 365 ou administradores de serviço do Power BI, podem efetuar em massa atribuir áreas de trabalho no portal de administração do Power BI. Em massa atribuída pode aplicar a:

- **Áreas de trabalho por utilizadores** -todas as áreas de trabalho pertencentes esses utilizadores, incluindo espaços de trabalho pessoas, são atribuídas à capacidade Premium. Isto incluirá a reatribuição de áreas de trabalho quando já estão atribuídos a uma capacidade Premium diferente. Além disso, os utilizadores também recebem permissões de atribuição de área de trabalho.

- **Áreas de trabalho específicas**
- **Áreas de trabalho do toda a organização** -todas as áreas de trabalho, incluindo espaços de trabalho pessoas, são atribuídas à capacidade Premium. Todos os utilizadores atuais e futuros são atribuídos as permissões de atribuição de área de trabalho. Essa abordagem não é recomendada. Uma abordagem mais direcionada é preferencial.

Uma área de trabalho pode ser adicionada a uma capacidade Premium ao utilizar o **área de trabalho** painel fornecendo ao usuário é um administrador de área de trabalho e tem as permissões de atribuição.

![Utilizar o painel da área de trabalho para atribuir uma área de trabalho a uma capacidade Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Os administradores de área de trabalho podem remover uma área de trabalho a partir de uma capacidade (para capacidade partilhada) sem a necessidade de permissão de atribuição. Remover áreas de trabalho de capacidades dedicadas com eficiência, a área de trabalho pois realoca para capacidade partilhada. Tenha em atenção que a remoção de uma área de trabalho da capacidade Premium pode ter conseqüências negativas, resultando, por exemplo, no conteúdo partilhado se tornar indisponível para o Power BI gratuito licenciado utilizadores ou a suspensão de atualização agendada, quando eles excedem as concessões suportadas por capacidades partilhadas.

No serviço Power BI, uma área de trabalho atribuída a uma capacidade Premium é facilmente identificada por terem o ícone de diamante adorns o nome de área de trabalho.

![Identificar uma área de trabalho atribuída a uma capacidade Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>As capacidades de monitorização

Monitorização de capacidades Premium fornece aos administradores uma compreensão de como as capacidades estão a funcionar. As capacidades podem ser monitorizadas com o portal de administrador do Power BI ou o **métricas de capacidade do Power BI Premium** aplicação (Power BI).

### <a name="power-bi-admin-portal"></a>Portal de administração do Power BI

No portal de administração, para cada capacidade, o **estado de funcionamento** separador fornece métricas de resumidas para a capacidade e cada carga de trabalho ativada. As métricas apresentam uma média nos últimos sete dias.  

Ao nível da capacidade, as métricas são cumulativas de todas as cargas de trabalho ativadas. são fornecidas as métricas seguintes:

- **UTILIZAÇÃO da CPU** -fornece a utilização média da CPU como uma percentagem do total de CPU disponível para a capacidade.  
- **UTILIZAÇÃO da memória** -fornece a média utilização de memória (em GB) como um total de memória disponível para a capacidade. 

Para cada carga de trabalho ativada, utilização da CPU e utilização de memória são fornecidos, bem como várias métricas específicas da carga de trabalho. Por exemplo, para a carga de trabalho do fluxo de dados **Contagem Total** mostra total de atualizações para cada fluxo de dados, e **duração média** mostra a duração média de atualização para o fluxo de dados.

![Separador de estado de funcionamento de capacidade no portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Para saber mais sobre todas as métricas disponíveis para cada carga de trabalho, consulte [monitorizar as capacidades no portal de administração](service-admin-premium-monitor-portal.md).

As capacidades de monitorização no portal de administração do Power BI foram concebidas para fornecer um resumo rápido das métricas de capacidade de chave. Para obter mais monitorização, é recomendado que utilize o **métricas de capacidade do Power BI Premium** aplicação.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium aplicação de métricas de capacidade

O [aplicação de métricas de capacidade do Power BI Premium](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) é uma aplicação do Power BI disponíveis para os administradores de capacidade e é instalado como qualquer outra aplicação do Power BI. Ele contém um dashboard e relatório.

![Power BI Premium aplicação de métricas de capacidade](media/service-premium-capacity-manage/capacity-metrics-app.png)

Quando a aplicação for aberta, o dashboard é carregado para apresentar vários mosaicos expressar uma exibição agregada ao longo de todas as suas capacidades de que o utilizador é um administrador de capacidade. O esquema do dashboard inclui cinco seções principais:

- **Descrição geral** -versão da aplicação, o número de capacidades e áreas de trabalho
- **Resumo do sistema** -as métricas de memória e CPU
- **Resumo de conjunto de dados** - número de conjuntos de dados, DQ/LC, atualização e métricas de consulta
- **Resumo de fluxo de dados** - número de fluxos de dados e métricas de conjunto de dados
- **Paginados resumo do relatório** - atualizar e ver métricas

O relatório subjacente, os mosaicos do dashboard foram afixados a partir do qual, pode ser acedido ao clicar em qualquer mosaico de dashboard. Ele fornece uma perspectiva mais detalhada de cada uma das seções de dashboard e oferece suporte à filtragem interativo. 

Filtragem pode ser conseguida através da definição de segmentações de dados por intervalo de datas, a capacidade, a área de trabalho e carga de trabalho (relatório, conjunto de dados, fluxo de dados) e, ao selecionar elementos no relatório, os elementos visuais cruzar filtrar a página de relatório. Filtragem cruzada é uma técnica avançada para restringir os períodos de tempo específico, as capacidades, áreas de trabalho, os conjuntos de dados, etc. e pode ser muito útil ao realizar a análise da causa raiz.

Para obter informações detalhadas sobre as métricas de dashboard e relatório na aplicação, consulte [capacidades Premium do Monitor com a aplicação](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretando métricas

As métricas devem ser monitorizadas para estabelecer uma compreensão de linha de base da atividade de carga de trabalho e de utilização de recursos. Se a capacidade se torna lenta, é importante compreender as métricas para monitorizar e as conclusões pode fazer.

O ideal é que consultas devem ser concluído dentro de um segundo para proporcionar experiências de reativas para utilizadores de relatórios e ativar um maior débito de consulta. Geralmente é uma preocupação menor quando processos em segundo plano - incluindo atualizações - tempos mais longos para concluir.

Em geral, os relatórios lentos podem ser uma indicação de uma capacidade de excesso de aquecimento.... Quando relatórios falhem ao carregar, esta é uma indicação de uma capacidade de excesso exaltada. Em qualquer situação, a causa raiz pode ser atribuíveis vários fatores, incluindo:

- **Consultas falhadas** certamente indicar pressão de memória e que não foi possível carregar um modelo na memória. O serviço Power BI irá tentar carregar um modelo para 30 segundos antes de falhar.

- **Tempos de espera de consulta excessiva** pode ser devido a vários motivos:
  - A necessidade do serviço Power BI para o primeiro expulsar o modelo (s) e, em seguida, carregar o modelo to-be-consultados (Lembre-se que superior taxas de expulsão de conjunto de dados autónomos não são uma indicação de estresse de capacidade, a menos que acompanhado por muito tempo consulta tempos de espera que indicam a degradação de memória).
  - Carga do modelo vezes (especialmente a espera para carregar um modelo de grandes na memória).
  - Consultas de execução longa.
  - Demasiadas ligações de LC\DQ (exceder os limites de capacidade).
  - Saturação de CPU.
  - Designs de relatório complexos com um número excessivo de elementos visuais numa página (Lembre-se que cada elemento visual é uma consulta).

- **Durações de consulta longo** pode indicar que os designs de modelo não são otimizados, especialmente quando vários conjuntos de dados não estão ativos numa capacidade e apenas um conjunto de dados é produzir longa durações de consulta. Isso sugere que a capacidade é suficientemente resourced e de que o conjunto de dados na pergunta é apenas lenta ou abaixo do ideal. Consultas de longa execução pode ser problemático, como eles podem bloquear o acesso aos recursos necessários por outros processos.
- **Atualizar longos tempos de espera** indica memória insuficiente devido a vários modelos de Active Directory a consumir memória ou que uma atualização problemática está a bloquear o outro é atualizada (exceder atualização paralela limites).

Uma explicação mais detalhada de como utilizar as métricas é abordada o [capacidades Premium otimizar](service-premium-capacity-optimize.md) artigo.

## <a name="acknowledgements"></a>Confirmações

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e especialista no Power BI independente com [soluções totalmente](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Otimizar as capacidades Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurar cargas de trabalho numa capacidade Premium](service-admin-premium-workloads.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||
