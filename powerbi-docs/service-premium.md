---
title: Power BI Premium – o que é?
description: O Power BI Premium é capacidade dedicada para a sua organização ou equipa, oferecendo desempenho mais fiável e maiores volumes de dados sem exigir a compra de licenças por utilizador.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2018
ms.author: mblythe
LocalizationGroup: Premium
ms.openlocfilehash: 15b64b917fed56e9d9ab6be2023060378324c794
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "36944566"
---
# <a name="power-bi-premium---what-is-it"></a>Power BI Premium – o que é?
O Power BI Premium fornece recursos dedicados à execução do serviço Power BI para a sua organização ou equipa, dando-lhe um desempenho mais fiável e volumes de dados maiores. O Premium também permite uma distribuição alargada de conteúdos sem que precise de comprar licenças por utilizador para visualizadores.

Pode tirar partido do Power BI Premium ao atribuir áreas de trabalho a uma capacidade Premium. A *capacidade Premium* é um recurso dedicado para a sua organização. Para áreas de trabalho que não estejam atribuídas a uma capacidade Premium, estas estarão numa capacidade partilhada.

A *capacidade partilhada* é a experiência que já conhece no Power BI, onde as suas cargas de trabalho são executadas em recursos informáticos partilhados por outros clientes. Na capacidade partilhada, existem mais limites para utilizadores individuais, o que permite uma experiência de qualidade para todos os utilizadores.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Níveis de capacidade
Existem dois tipos de capacidade no Power BI. Capacidade partilhada e capacidade do Power BI Premium. Eis uma análise às diferenças entre as mesmas.

|  | Capacidade partilhada | Capacidade do Power BI Premium |
| --- | --- | --- |
| **Taxa de atualizações** |8/dia |Sem restrições |
| **Isolamento com hardware dedicado** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |
| **Distribuição Empresarial para** ***todos os utilizadores*** | | |
| Aplicações e partilha |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>1</sup> |
| API e controlos incorporados |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>2</sup> |
| **Publicar relatórios do Power BI no local** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |

*<sup>1</sup> Para obter mais informações, veja [Capacidades dos utilizadores com as funcionalidades do Power BI Pro e do Power BI Premium](service-free-vs-pro.md).*  
*<sup>2</sup> Melhorias futuras brevemente disponíveis no Power BI Premium após GA.*

### <a name="premium-capacity"></a>Capacidade Premium
Para começar a utilizar uma capacidade do Power BI Premium, tem de atribuir uma área de trabalho a uma capacidade. Para obter mais informações sobre como atribuir uma área de trabalho a uma capacidade premium, consulte [Gerir o Power BI Premium](service-admin-premium-manage.md).

Quando uma área de trabalho tem capacidade premium, o utilizador beneficia das vantagens do Power BI Premium.

* Atualizações agendadas: anteriormente, os utilizadores estavam limitados a 8x por dia ao agendar atualizações em modelos importados. A limitação é levantada nos conjuntos de dados em áreas de trabalho Premium. Tal não se aplica às definições de atualização de cache agendada para o DirectQuery. Estas permanecem iguais nas capacidades Premium e Partilhada.
* Isolamento com hardware dedicado: devido à natureza da capacidade partilhada, o desempenho dos seus relatórios e dashboards pode ser afetado pelas exigências de recursos de outras cargas de trabalho na capacidade, apesar das nossas salvaguardas contra esta situação. Por sua vez, o Premium dá um desempenho mais consistente e fiável às suas cargas de trabalho, ao isolá-la de cargas de trabalho não relacionadas.

Se uma aplicação tiver capacidade Premium (ou seja, se foi publicada de uma área de trabalho de aplicação que está atualmente atribuída a Premium), a aplicação publicada pode ser utilizada por qualquer utilizador na sua organização, independentemente da licença atribuída.

### <a name="shared-capacity"></a>Capacidade partilhada
Por predefinição, a sua área de trabalho estará na capacidade partilhada. Tal inclui *A Minha Área de Trabalho* pessoal, juntamente com as áreas de trabalho de Aplicações. Uma capacidade partilhada é a experiência que já conhece no Power BI, onde as suas cargas de trabalho são executadas em recursos informáticos partilhados por outros clientes.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium
O Power BI Premium está disponível em configurações de nós com diferentes capacidades de núcleos virtuais. Para obter mais informações sobre ofertas e custos de SKUs específicos, consulte os [preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre o planeamento de capacidade de análise incorporada, consulte o [Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy).

* Os nós P podem ser utilizados em implementações de serviço ou incorporadas.
* Os nós EM podem ser utilizados apenas em implementações incorporadas. Os nós EM não têm acesso às funcionalidades premium, como a partilha de aplicações para utilizadores que não têm uma licença do Power BI Pro.

>[!NOTE]
>As ligações nesta tabela só funcionam corretamente para utilizadores que são administradores globais do Office 365. Os outros utilizadores obtêm um erro 404. 

| Nó de Capacidade | Núcleos virtuais totais<br/>*(Back-end + front-end)* | Núcleos virtuais de back-end | Núcleos virtuais de front-end | Limites do DirectQuery/ligação em direto | Composição de páginas máxima em hora de ponta | Disponibilidade |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |0,5 núcleos virtuais, 2,5 GB de RAM |0,5 núcleos virtuais |3,75 por segundo |150-300 |Disponível |
| [EM2 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos virtuais |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |301-600 |Disponível |
| [EM3 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos virtuais |2 núcleos virtuais, 10 GB de RAM |2 núcleos virtuais | |601-1200 |Disponível |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 núcleos virtuais |4 núcleos virtuais, 25 GB de RAM |4 núcleos virtuais |30 por segundo |1201-2400 |Disponível (também está disponível[mês a mês](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 núcleos virtuais |8 núcleos virtuais, 50 GB de RAM |8 núcleos virtuais |60 por segundo |2401-4800 |Disponível |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 núcleos virtuais |16 núcleos virtuais, 100 GB de RAM |16 núcleos virtuais |120 por segundo |4801-9600 |Disponível |

* Os núcleos virtuais de front-end são responsáveis pelo serviço Web, a gestão de documentos de relatórios e dashboards, gestão de direitos de acesso, agendamento, APIs, carregamentos e transferências e, de forma geral, por tudo o que tem a ver com a experiência de utilizador.
* Os núcleos virtuais de back-end são responsáveis pelo trabalho pesado: processamento de consultas, gestão de cache, executar servidores R, atualização de dados, processamento de linguagem natural, feeds em tempo real e composição de relatórios e imagens no servidor. Nos núcleos virtuais de back-end, está também reservada uma determinada quantidade de memória. Ter memória suficiente torna-se especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="power-bi-report-server"></a>Power BI Report Server
O Power BI Premium inclui o direito a executar o Power BI Report Server no local. Para mais informações, consulte [Introdução ao Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Próximos passos
[Perguntas Frequentes do Power BI Premium](service-premium-faq.md)  
[Notas de versão do Power BI Premium](service-premium-release-notes.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[Gerir o Power BI Premium](service-admin-premium-manage.md)  
[Documento técnico do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy)  
[Administrar o Power BI na sua organização](service-admin-administering-power-bi-in-your-organization.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

