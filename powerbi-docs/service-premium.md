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
ms.date: 09/11/2018
LocalizationGroup: Premium
ms.openlocfilehash: 0723ddb57131fed499d4ac86666b3cd6d8bcbd2d
ms.sourcegitcommit: 833cf1252807721fb1b3000487bd032bfd6c8c98
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48271814"
---
# <a name="what-is-microsoft-power-bi-premium"></a>O que é o Microsoft Power BI Premium?

O Microsoft Power BI Premium oferece recursos dedicados à execução do serviço Power BI para a sua organização ou equipa. Além disso, proporciona um desempenho mais fiável e a utilização de volumes de dados maiores. O Premium também permite uma distribuição alargada de conteúdos sem que precise de comprar licenças Pro por utilizador para visualizadores.

Pode tirar partido do Power BI Premium ao atribuir áreas de trabalho a uma *capacidade Premium*. A capacidade Premium é um recurso dedicado para a sua organização. As áreas de trabalho que não estejam atribuídas a uma capacidade Premium estão numa *capacidade partilhada*. Com a capacidade partilhada, as suas cargas de trabalho são executadas em recursos informáticos partilhados por outros clientes. 

Na capacidade partilhada, o Power BI coloca mais limites para utilizadores individuais, o que permite uma experiência de qualidade para todos os utilizadores. Por predefinição, a sua área de trabalho está na capacidade partilhada, incluindo a sua *A Minha Área de Trabalho* pessoal e áreas de trabalho de Aplicação.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Níveis de capacidade

Aqui está um resumo das diferenças entre a capacidade partilhada e a capacidade Premium.

|  | Capacidade partilhada | Capacidade Power BI Premium |
| --- | --- | --- |
| **Taxa de atualizações** |8/dia |48/dia |
| **Isolamento com hardware dedicado** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |
| **Distribuição Empresarial para** ***todos os utilizadores*** | | |
| Aplicações e partilha |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>1</sup> |
| API e controlos incorporados |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>2</sup> |
| **Publicar relatórios do Power BI no local** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |

*<sup>1</sup> Para obter mais informações, veja [Funcionalidades por tipo de licença](service-features-license-type.md).*  
*<sup>2</sup> Melhorias futuras brevemente disponíveis no Power BI Premium.*

Para começar a utilizar uma capacidade Power BI Premium, atribua uma área de trabalho a uma capacidade. Quando uma área de trabalho tem capacidade Premium, obtém:

* **Atualizações agendadas**: com a capacidade partilhada, as atualizações agendadas dos conjuntos de dados de modelos importados estão limitadas a oito vezes por dia. Para conjuntos de dados em áreas de trabalho Premium, pode agendar atualizações até 48 vezes por dia. As atualizações de cache do DirectQuery estão ainda limitadas a oito vezes por dia na capacidade Premium.

* **Isolamento com hardware dedicado**: na capacidade partilhada, exigências de recursos de outras cargas de trabalho podem afetar o desempenho dos seus relatórios e dashboards. Em contrapartida, a capacidade Premium proporciona um desempenho mais consistente e fiável às suas cargas de trabalho, ao isolá-la de cargas de trabalho não relacionadas.

Se uma aplicação tiver capacidade Premium (ou seja, se tiver sido publicada de uma área de trabalho de aplicação que está atualmente atribuída à capacidade Premium), a aplicação publicada pode ser utilizada por qualquer utilizador na sua organização, independentemente da licença atribuída.

Para saber mais sobre a atribuição de áreas de trabalho a uma capacidade Premium, veja [Manage Power BI Premium](service-admin-premium-manage.md) (Gerir o Power BI Premium).

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium

O Power BI Premium está disponível em configurações de nós com diferentes capacidades de núcleos virtuais. Para obter mais informações sobre ofertas e custos de SKUs específicos, consulte os [preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre o planeamento de capacidade de análise incorporada, consulte o [Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy).

* Os nós P podem ser utilizados em implementações de serviço ou incorporadas.

* Os nós EM podem ser utilizados apenas em implementações incorporadas. Os nós EM não têm acesso às funcionalidades premium, como a partilha de aplicações para utilizadores que não têm uma licença do Power BI Pro.

>[!NOTE]
>As ligações nesta tabela só funcionam corretamente para utilizadores que são administradores globais do Office 365. Os outros utilizadores obtêm um erro 404.

| Nó de Capacidade | Núcleos virtuais totais<br/>*(Back-end + front-end)* | Núcleos virtuais de back-end | Núcleos virtuais de front-end | Limites do DirectQuery/ligação em direto | Composição de páginas máxima em hora de ponta | Disponibilidade |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |0.5 núcleos virtuais, 2.5 GB de RAM |0,5 núcleos virtuais |3,75 por segundo |150-300 |Disponível |
| [EM2 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos virtuais |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |301-600 |Disponível |
| [EM3 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos virtuais |2 núcleos virtuais, 10 GB de RAM |2 núcleos virtuais | |601-1200 |Disponível |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 núcleos virtuais |4 núcleos virtuais, 25 GB de RAM |4 núcleos virtuais |30 por segundo |1201-2400 |Disponível (também está disponível[mês a mês](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 núcleos virtuais |8 núcleos virtuais, 50 GB de RAM |8 núcleos virtuais |60 por segundo |2401-4800 |Disponível |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 núcleos virtuais |16 núcleos virtuais, 100 GB de RAM |16 núcleos virtuais |120 por segundo |4801-9600 |Disponível |

* Os núcleos virtuais de front-end são responsáveis pelo serviço Web, a gestão de documentos de relatórios e dashboards, gestão de direitos de acesso, agendamento, APIs, carregamentos e transferências e, de forma geral, por tudo o que tem a ver com a experiência de utilizador.

* Os núcleos virtuais de back-end são responsáveis pelo trabalho pesado: processamento de consultas, gestão de cache, executar servidores R, atualização de dados, processamento de linguagem natural, feeds em tempo real e composição de relatórios e imagens no servidor. Nos núcleos virtuais de back-end, está também reservada uma determinada quantidade de memória. Ter memória suficiente torna-se especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="power-bi-report-server"></a>Power BI Report Server
O Power BI Premium também inclui a capacidade de executar o Power BI Report Server no local na sua organização. Para saber mais, veja [Get started with Power BI Report Server](report-server/get-started.md) (Introdução ao Power BI Report Server).

## <a name="next-steps"></a>Próximos passos
[Perguntas Frequentes do Power BI Premium](service-premium-faq.md)  
[Notas de versão do Power BI Premium](service-premium-release-notes.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[Gerir o Power BI Premium](service-admin-premium-manage.md)  
[Documento técnico do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy)  
[Administrar o Power BI na sua organização](service-admin-administering-power-bi-in-your-organization.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
