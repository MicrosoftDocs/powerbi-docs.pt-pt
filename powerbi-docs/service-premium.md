---
title: O que é o Microsoft Power BI Premium?
description: O Power BI Premium é capacidade dedicada para a sua organização ou equipa, oferecendo desempenho mais fiável e maiores volumes de dados sem exigir a compra de licenças por utilizador.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: f327cb95c10756f079778d20e62cba4871b95c02
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964945"
---
# <a name="what-is-microsoft-power-bi-premium"></a>O que é o Microsoft Power BI Premium?

> [!NOTE]
> Este artigo está a ser atualizado para descrever novas funcionalidades, fornecer mais detalhes e melhorar a legibilidade. Para obter as informações mais recentes, veja [Deploying and Managing Power BI Premium Capacities](whitepaper-powerbi-premium-deployment.md) (Implementar e Gerir Capacidades Premium do Power BI).

O Power BI Premium fornece recursos dedicados à execução do serviço Power BI para a sua organização. Além disso, proporciona um desempenho mais fiável e a utilização de volumes de dados maiores. O Premium também permite uma distribuição alargada de conteúdos sem que precise de comprar licenças Pro por utilizador para consumidores de conteúdos.  

## <a name="premium-capacity-and-shared-capacity"></a>Capacidade Premium e capacidade partilhada

Pode tirar partido do Power BI Premium ao atribuir áreas de trabalho a uma *capacidade Premium*. A capacidade Premium é um recurso dedicado para a sua organização. As áreas de trabalho que não estejam atribuídas a uma capacidade Premium estão numa *capacidade partilhada*. Com a capacidade partilhada, as suas cargas de trabalho são executadas em recursos informáticos partilhados por outros clientes.

A imagem seguinte mostra a relação entre a capacidade Premium e a capacidade partilhada ao utilizar a organização Contoso como exemplo.

![Ilustração do Power BI Premium](media/service-premium/premium-chart.png)

| Área | Descrição |
| --- | --- |
| **(1)** Itens numa capacidade Premium | <ul><li>Aceder às áreas de trabalho das aplicações (como membros ou administradores) e publicar aplicações requer uma licença do Power BI Pro.<li>É necessária uma licença do Power BI Pro para partilhar uma aplicação, mas não para a utilizar.<li>Todos os destinatários do dashboard podem definir alertas de dados, independentemente da licença que têm atribuída.<li>As APIs REST para incorporação utilizam uma conta de serviço com uma licença do Power BI Pro, em vez de uma conta de utilizador.</ul> |
| **(2)** A minha área de trabalho na capacidade Partilhada | <ul><li>É necessária uma licença do Power BI Pro tanto para partilhar como para utilizar uma aplicação.</ul> |
| **(3)** Áreas de trabalho de aplicação na capacidade partilhada | <ul><li>É necessária uma licença do Power BI Pro para utilizar uma aplicação.</ul>|
| | |

Na capacidade partilhada, o Power BI coloca mais limites para utilizadores individuais, o que permite uma experiência de qualidade para todos os utilizadores. Por predefinição, a sua área de trabalho está na capacidade partilhada, incluindo a sua *A Minha Área de Trabalho* pessoal e áreas de trabalho de Aplicação.

A tabela seguinte apresenta um resumo das diferenças entre a capacidade partilhada e a capacidade Premium:

|  | Capacidade partilhada | Capacidade Power BI Premium |
| --- | --- | --- |
| **Taxa de atualizações** |8/dia |48/dia |
| Isolamento com hardware dedicado |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Distribuição Empresarial para *todos os utilizadores* | | |
| Aplicações e partilha |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| API e controlos incorporados |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| Publicar relatórios do Power BI no local |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> Melhorias futuras brevemente disponíveis no Power BI Premium.



### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium

O Power BI Premium está disponível em configurações de nós com diferentes capacidades de núcleos virtuais. Para obter mais informações sobre ofertas e custos de SKUs específicos, veja os [preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre o planeamento de capacidade de análise incorporada, consulte o [Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy). Em resumo:

* Os nós P podem ser utilizados em implementações de serviço ou incorporadas.

* Os nós EM podem ser utilizados apenas em implementações incorporadas. Os nós EM não têm acesso às funcionalidades premium, como a partilha de aplicações para utilizadores que não têm uma licença do Power BI Pro.

| Nó de Capacidade | Núcleos virtuais totais<br/>*(Back-end + front-end)*  | Núcleos Virtuais de Back-end <sup>[1](#fn1)</sup> | Núcleos Virtuais de Front-end <sup>[2](#fn2)</sup> | Limites do DirectQuery/ligação em direto | Máx. de atualizações em simultâneo |
| --- | --- | --- | --- | --- | --- |
| EM1 (mês a mês) |1 núcleo virtual |0.5 núcleos virtuais, 2.5 GB de RAM |0,5 núcleos virtuais |3,75 por segundo |  1 |
| EM2 (mês a mês) |2 núcleos virtuais |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |  2 |
| EM3 (mês a mês) |4 núcleos virtuais |2 núcleos virtuais, 10 GB de RAM |2 núcleos virtuais | 15 | 3 |
| P1 |8 núcleos virtuais |4 núcleos virtuais, 25 GB de RAM |4 núcleos virtuais |30 por segundo | 6 |
| P2 |16 núcleos virtuais |8 núcleos virtuais, 50 GB de RAM |8 núcleos virtuais |60 por segundo | 12 |
| P3 |32 núcleos virtuais |16 núcleos virtuais, 100 GB de RAM |16 núcleos virtuais |120 por segundo | 24 |
| | | | | | |

<a name="fn1">1</a>: Os núcleos virtuais de front-end são responsáveis pelo serviço Web. Por exemplo,são responsáveis pela gestão de documentos de relatórios e dashboards, gestão de direitos de acesso, agendamento, APIs, carregamentos e transferências e, de forma geral, por tudo o que tem a ver com a experiência de utilizador. 

<a name="fn2">2</a>: Os núcleos virtuais de back-end são responsáveis pelo trabalho pesado, como processamento de consultas, gestão de cache, execução de servidores R, atualização de dados, processamento de linguagem natural, feeds em tempo real e composição de relatórios e imagens no servidor. Nos núcleos virtuais de back-end, está também reservada uma determinada quantidade de memória. Ter memória suficiente torna-se especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="workloads-in-premium-capacity"></a>Cargas de trabalho na capacidade Premium

Por predefinição, as funcionalidades do Power BI Premium e do Power BI Embedded suportam apenas a carga de trabalho associada à execução de consultas do Power BI na cloud. O Premium também suporta cargas de trabalho adicionais para **IA**, **Fluxos de dados** e **Relatórios paginados**. Antes destas cargas de trabalho poderem utilizar os recursos da sua capacidade, têm de ser ativadas no portal de administração do Power BI ou através da API REST do Power BI. Cada carga de trabalho tem predefinições para a quantidade máxima de memória que cada uma pode consumir. No entanto, pode configurar diferentes definições de consumo de memória para determinar de que forma as cargas de trabalho se afetam entre si e consomem os recursos de capacidade. Para saber mais, veja [Configurar cargas de trabalho](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI Report Server

O Power BI Premium também inclui a capacidade de executar o Power BI Report Server no local na sua organização. Para saber mais, veja [Get started with Power BI Report Server](report-server/get-started.md) (Introdução ao Power BI Report Server).

## <a name="next-steps"></a>Próximos passos

[Deploying and Managing Power BI Premium Capacities](whitepaper-powerbi-premium-deployment.md)  (Implementar e Gerir Capacidades do Power BI Premium)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)   
[Perguntas Frequentes do Power BI Premium](service-premium-faq.md)   



Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
