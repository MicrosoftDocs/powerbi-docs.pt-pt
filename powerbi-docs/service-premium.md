---
title: O que é o Microsoft Power BI Premium?
description: O Power BI Premium é capacidade dedicada para a sua organização ou equipa, oferecendo desempenho mais fiável e maiores volumes de dados sem exigir a compra de licenças por utilizador.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/21/2018
LocalizationGroup: Premium
ms.openlocfilehash: 451727d473b59afd362e4f31e8aef634d2168f83
ms.sourcegitcommit: 1e4fee6d1f4b7803ea285eb879c8d5a4f7ea8b85
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51717637"
---
# <a name="what-is-microsoft-power-bi-premium"></a>O que é o Microsoft Power BI Premium?

O Microsoft Power BI Premium oferece recursos dedicados à execução do serviço Power BI para a sua organização. Além disso, proporciona um desempenho mais fiável e a utilização de volumes de dados maiores. O Premium também permite uma distribuição alargada de conteúdos sem que precise de comprar licenças Pro por utilizador para consumidores de conteúdos. Para obter informações sobre compras, veja [Como comprar o Power BI Premium](service-admin-premium-purchase.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

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

A tabela seguinte fornece um resumo das diferenças entre a capacidade partilhada e a capacidade Premium.

|  | Capacidade partilhada | Capacidade do Power BI Premium |
| --- | --- | --- |
| **Taxa de atualizações** |8/dia |48/dia |
| **Isolamento com hardware dedicado** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |
| **Distribuição Empresarial para** _**todos os utilizadores**_ | | |
| Aplicações e partilha |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>1</sup> |
| API e controlos incorporados |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>2</sup> |
| **Publicar relatórios do Power BI no local** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |
| | | |

*<sup>1</sup> Para obter mais informações, veja [Funcionalidades por tipo de licença](service-features-license-type.md).*  
*<sup>2</sup> Melhorias futuras brevemente disponíveis no Power BI Premium.*

Para saber mais sobre a atribuição de áreas de trabalho a uma capacidade Premium, veja [Manage Power BI Premium](service-admin-premium-manage.md) (Gerir o Power BI Premium).

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium

O Power BI Premium está disponível em configurações de nós com diferentes capacidades de núcleos virtuais. Para obter mais informações sobre ofertas e custos de SKUs específicos, veja os [preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre o planeamento de capacidade de análise incorporada, veja o [Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy). Em resumo:

* Os nós P podem ser utilizados em implementações de serviço ou incorporadas.

* Os nós EM podem ser utilizados apenas em implementações incorporadas. Os nós EM não têm acesso às funcionalidades premium, como a partilha de aplicações para utilizadores que não têm uma licença do Power BI Pro.

>[!NOTE]
>As ligações nesta tabela só funcionam corretamente para utilizadores que tenham a função de Administrador Global do Office 365. Os outros utilizadores obtêm um erro 404.

| Nó de Capacidade | Núcleos virtuais totais<br/>*(Back-end + front-end)* | Núcleos virtuais de back-end | Núcleos virtuais de front-end | Limites do DirectQuery/ligação em direto | Composição de páginas máxima em hora de ponta | Disponibilidade |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |0.5 núcleos virtuais, 2.5 GB de RAM |0,5 núcleos virtuais |3,75 por segundo |150-300 |Disponível |
| [EM2 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos virtuais |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |301-600 |Disponível |
| [EM3 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos virtuais |2 núcleos virtuais, 10 GB de RAM |2 núcleos virtuais | |601-1200 |Disponível |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 núcleos virtuais |4 núcleos virtuais, 25 GB de RAM |4 núcleos virtuais |30 por segundo |1201-2400 |Disponível (também está disponível[mês a mês](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 núcleos virtuais |8 núcleos virtuais, 50 GB de RAM |8 núcleos virtuais |60 por segundo |2401-4800 |Disponível |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 núcleos virtuais |16 núcleos virtuais, 100 GB de RAM |16 núcleos virtuais |120 por segundo |4801-9600 |Disponível |
| | | | | | | |

* Os núcleos virtuais de front-end são responsáveis pelo serviço Web, a gestão de documentos de relatórios e dashboards, gestão de direitos de acesso, agendamento, APIs, carregamentos e transferências e, de forma geral, por tudo o que tem a ver com a experiência de utilizador.

* Os núcleos virtuais de back-end são responsáveis pelo trabalho pesado: processamento de consultas, gestão de cache, executar servidores R, atualização de dados, processamento de linguagem natural, feeds em tempo real e composição de relatórios e imagens no servidor. Nos núcleos virtuais de back-end, está também reservada uma determinada quantidade de memória. Ter memória suficiente torna-se especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="workloads-in-premium-capacity"></a>Cargas de trabalho na capacidade Premium

Considere uma carga de trabalho no Power BI como um dos muitos serviços que pode expor aos utilizadores. Por predefinição, as capacidades do **Power BI Premium** e do **Power BI Embedded** suportam apenas a carga de trabalho associada à execução de consultas do Power BI na cloud.

Agora, oferecemos suporte de pré-visualização para duas cargas de trabalho adicionais: **Relatórios paginados** e **Fluxos de dados**. Pode ativar estas cargas de trabalho no portal de administração do Power BI ou através da API REST do Power BI. Também pode definir o máximo de memória que cada carga de trabalho pode consumir, para que possa controlar como as diferentes cargas de trabalho se afetam mutuamente. Para obter mais informações, veja [Configurar as cargas de trabalho](service-admin-premium-manage.md#configure-workloads).

### <a name="default-memory-settings"></a>Predefinições de memória

As seguintes tabelas mostram os valores da memória predefinidos e mínimos, com base nos diferentes [nós de capacidade](#premium-capacity-nodes) disponíveis. A memória é alocada dinamicamente aos fluxos de dados, mas é alocada estaticamente aos relatórios paginados. Para obter mais informações, veja a secção seguinte [Considerações sobre relatórios paginados](#considerations-for-paginated-reports).

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários de software como serviço (SaaS)

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Relatórios paginados | N/D | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| Fluxos de dados | 20% predefinido; 8% mínimo  | 20% predefinido; 4% mínimo  | 20% predefinido; 2% mínimo | 20% predefinido; 1% mínimo  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários de plataforma como serviço (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Relatórios paginados | N/D                      | N/D                      | N/D                     | 20% predefinido; 10% mínimo | 20% predefinido; 5% mínimo | 20% predefinido; 2,5% mínimo |
| Fluxos de dados         | 27% predefinido; 27% mínimo | 20% predefinido; 16% mínimo | 20% predefinido; 8% mínimo | 20% predefinido; 4% mínimo  | 20% predefinido; 2% mínimo | 20% predefinido; 1% mínimo   |

### <a name="considerations-for-paginated-reports"></a>Considerações sobre relatórios paginados

Se utilizar a carga de trabalho Relatórios paginados, tenha em atenção os seguintes pontos.

* **Alocação de memória em relatórios paginados**: os relatórios paginados permitem-lhe executar o seu próprio código ao compor um relatório (por exemplo, alterar dinamicamente a cor do texto com base nos conteúdos). Devido a este facto, protegemos a capacidade do Power BI Premium ao executar relatórios paginados num espaço contido dentro da capacidade. Atribuímos a memória máxima que especificar a este espaço, independentemente de a carga de trabalho estar ou não ativa. Se utilizar fluxos de dados ou relatórios do Power BI na mesma capacidade, certifique-se de que define a memória suficientemente baixa para relatórios paginados de modo a não afetar as outras cargas de trabalho de forma negativa.

* **Os relatórios paginados não estão disponíveis**: em circunstâncias raras, a carga de trabalho Relatórios paginados pode ficar indisponível. Neste caso, a carga de trabalho apresenta um estado de erro no portal de administração e os utilizadores veem tempos limite para a composição do relatório. Para mitigar este problema, desative a carga de trabalho e, em seguida, ative-a novamente.

## <a name="power-bi-report-server"></a>Power BI Report Server

O Power BI Premium também inclui a capacidade de executar o Power BI Report Server no local na sua organização. Para saber mais, veja [Get started with Power BI Report Server](report-server/get-started.md) (Introdução ao Power BI Report Server).

## <a name="next-steps"></a>Passos seguintes

[Perguntas Frequentes do Power BI Premium](service-premium-faq.md)
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)
[Gerir o Power BI Premium](service-admin-premium-manage.md)
[Microsoft Power BI Premium whitepaper](https://aka.ms/pbipremiumwhitepaper)
 (Documento técnico do Microsoft Power BI Premium) [Planning a Power BI Enterprise Deployment whitepaper (Documento técnico Planear uma Implementação Empresarial do Power BI) ](https://aka.ms/pbienterprisedeploy)
[Administrar o Power BI na sua organização](service-admin-administering-power-bi-in-your-organization.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
