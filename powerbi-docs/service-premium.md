---
title: "Power BI Premium – o que é?"
description: "O Power BI Premium é capacidade dedicada para a sua organização ou equipa, oferecendo desempenho mais fiável e maiores volumes de dados sem exigir a compra de licenças por utilizador."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/05/2018
ms.author: maghan
LocalizationGroup: Premium
ms.openlocfilehash: 11cfdfdfbc4b918d00633b78ec0bdafabfe99cd6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="power-bi-premium---what-is-it"></a>Power BI Premium – o que é?
O Power BI Premium fornece recursos dedicados à execução do serviço Power BI para a sua organização ou equipa, dando-lhe um desempenho mais fiável e volumes de dados maiores. O Premium também permite uma distribuição alargada de conteúdos sem que precise de comprar licenças por utilizador para visualizadores.

Pode tirar partido do Power BI Premium ao atribuir áreas de trabalho a uma capacidade Premium. A *capacidade Premium* é um recurso dedicado para a sua organização. Para áreas de trabalho que não estejam atribuídas a uma capacidade Premium, estas estarão numa capacidade partilhada.

A *capacidade partilhada* é a experiência que já conhece no Power BI, onde as suas cargas de trabalho são executadas em recursos informáticos partilhados por outros clientes. Na capacidade partilhada, existem mais limites para utilizadores individuais, o que permite uma experiência de qualidade para todos os utilizadores.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Níveis de capacidade
Existem dois tipos de capacidade no Power BI. Capacidade partilhada e capacidade Power BI Premium. Eis uma análise às diferenças entre as mesmas.

|  | Capacidade partilhada | Capacidade Power BI Premium |
| --- | --- | --- |
| **Taxa de atualizações** |8/dia |Sem restrições |
| **Isolamento com hardware dedicado** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |
| **Distribuição Empresarial para** ***todos os utilizadores*** | | |
| Aplicações |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>1</sup> |
| API e controlos incorporados |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>2</sup> |
| **Publicar relatórios do Power BI no local** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |

*<sup>1</sup> O consumo gratuito de utilizadores em aplicações inclui a visualização de conteúdos na Web e em dispositivos móveis, a utilização das Perguntas e Respostas, Quick Insights, Cortana, exportação para CSV, Excel e PowerPoint. Precisa de uma licença Pro para outras atividades que não estão listadas como, por exemplo, criar relatórios em conjuntos de dados partilhados e Analisar no Excel. Saiba mais sobre a funcionalidade [Power BI Gratuito vs. Pro](service-free-vs-pro.md).*  
*<sup>2</sup> Melhorias futuras brevemente disponíveis no Power BI Premium após GA.*

### <a name="premium-capacity"></a>Capacidade Premium
Para começar a utilizar uma capacidade do Power BI Premium, tem de atribuir uma área de trabalho a uma capacidade. Para obter mais informações sobre como atribuir uma área de trabalho a uma capacidade premium, consulte [Gerir o Power BI Premium](service-admin-premium-manage.md).

Quando uma área de trabalho tem capacidade premium, o utilizador beneficia das vantagens do Power BI Premium.

* Atualizações agendadas: anteriormente, os utilizadores estavam limitados a 8x por dia ao agendar atualizações em modelos importados. A limitação é levantada nos conjuntos de dados em áreas de trabalho Premium. Tal não se aplica às definições de atualização de cache agendada para o DirectQuery. Estas permanecem iguais nas capacidades Premium e Partilhada.
* Isolamento com hardware dedicado: devido à natureza da capacidade partilhada, o desempenho dos seus relatórios e dashboards pode ser afetado pelas exigências de recursos de outras cargas de trabalho na capacidade, apesar das nossas salvaguardas contra esta situação. Por sua vez, o Premium dá um desempenho mais consistente e fiável às suas cargas de trabalho, ao isolá-la de cargas de trabalho não relacionadas.

Se uma aplicação tiver capacidade Premium (ou seja, se foi publicada de uma área de trabalho de aplicação que está atualmente atribuída a Premium), a aplicação publicada pode ser utilizada por qualquer utilizador na sua organização, independentemente da licença atribuída. Isto significa que mesmo os utilizadores do Power BI Gratuito podem utilizar essas aplicações publicadas.

### <a name="shared-capacity"></a>Capacidade partilhada
Por predefinição, a sua área de trabalho estará na capacidade partilhada. Tal inclui *A Minha Área de Trabalho* pessoal, juntamente com as áreas de trabalho de Aplicações. Uma capacidade partilhada é a experiência que já conhece no Power BI, onde as suas cargas de trabalho são executadas em recursos informáticos partilhados por outros clientes.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium
O Power BI Premium está disponível em configurações de nós com diferentes capacidades de núcleos virtuais. Para obter mais informações sobre ofertas e custos de SKUs específicos, consulte os [preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre o planeamento de capacidade de análise incorporada, consulte o [Documento técnico sobre Planear uma Implementação Empresarial do Power BI](https://aka.ms/pbienterprisedeploy).

* Os nós P podem ser utilizados em implementações de serviço ou incorporadas
* Os nós EM podem ser utilizados apenas em implementações incorporadas
* EM1 e EM2 
* As ligações nesta tabela só funcionam corretamente para utilizadores que são administradores globais do Office 365. Os outros utilizadores obtêm um erro 404. 

| Nó de Capacidade | Total de núcleos<br/>*(Back-end + front-end)* | Núcleos de Back-end | Núcleos de Front-end | Limites do DirectQuery/ligação em direto | Composição de páginas máxima em hora de ponta | Disponibilidade |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |.5 núcleos, 2,5 GB de RAM |.5 núcleos |3,75 por segundo |150-300 |Disponível |
| [EM2 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos virtuais |1 núcleo, 5 GB de RAM |1 núcleo |7,5 por segundo |301-600 |Disponível |
| [EM3 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos virtuais |2 núcleos, 10 GB de RAM |2 núcleos | |601-1200 |Disponível |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 núcleos virtuais |4 núcleos, 25 GB de RAM |4 núcleos |30 por segundo |1201-2400 |Disponível (também está disponível[mês a mês](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 núcleos virtuais |8 núcleos, 50 GB de RAM |8 núcleos |60 por segundo |2401-4800 |Disponível |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 núcleos virtuais |16 núcleos, 100 GB de RAM |16 núcleos |120 por segundo |4801-9600 |Disponível |

* Os núcleos de front-end são responsáveis pelo serviço Web, a gestão de documentos de relatórios e dashboards, gestão de direitos de acesso, agendamento, APIs, carregamentos e transferências e, de forma geral, por tudo o que tem a ver com a experiência de utilizador.
* Os núcleos de back-end são responsáveis pelo trabalho pesado: processamento de consultas, gestão de cache, executar servidores R, atualização de dados, processamento de linguagem natural, feeds em tempo real e composição de relatórios e imagens no servidor. Nos núcleos de back-end, está também reservada uma determinada quantidade de memória. Ter memória suficiente torna-se especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

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

