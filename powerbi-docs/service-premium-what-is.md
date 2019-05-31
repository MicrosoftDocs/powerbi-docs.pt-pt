---
title: O que é o Microsoft Power BI Premium?
description: O Power BI Premium fornece as capacidades dedicadas para a sua organização, dando-lhe um desempenho mais fiável e maiores volumes de dados, sem que precise de comprar licenças por utilizador.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/22/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e5ffa624bf69cf470aade076c80ac37028a55456
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565262"
---
# <a name="what-is-power-bi-premium"></a>O que é o Power BI Premium?

O Power BI Premium fornece recursos dedicados e aprimorados para executar o serviço Power BI para a sua organização. Por exemplo:

- Maior dimensionamento e desempenho
- Flexibilidade de licença por capacidade
- Uniformizar a gestão personalizada e enterprise BI
- Expandir o BI no local com o Power BI Report Server
- Suporte para residência de dados por região (Multi-Geo)
- Partilhar dados com qualquer pessoa sem comprar uma licença por utilizador

Este artigo não se destina a oferecer detalhes aprofundados sobre todas as funcionalidades do Power BI Premium – na verdade, ele apenas contempla a superfície. Sempre que necessário, são fornecidas hiperligações para artigos adicionais com informações mais detalhadas.

## <a name="subscriptions-and-licensing"></a>As subscrições e licenciamento

O Power BI Premium é uma subscrição do Office 365 de inquilinos disponível em duas famílias de SKU (Stock manutenção unidade):

- **EM** SKUs (EM1-EM3) para incorporar, que requerem um compromisso anual, faturados mensalmente.
- **P** SKUs (P1-P3) para recursos de incorporação e enterprise, exigindo um compromisso mensal ou anualmente, faturados mensalmente e inclui uma licença para instalar o Power BI Report Server no local.

Uma abordagem alternativa é comprar um **do Azure Power BI Embedded** subscrição, o que tem uma única **A** família SKU (A1-A6) para incorporar e capacidade de teste apenas a fins. Núcleos virtuais para criar as capacidades de entrega de todos os SKUs, mas os EM SKUs são restritos para incorporação de escala mais pequena. EM1, EM2, A1 e A2 SKUs com menos de quatro núcleos virtuais não são executadas na infraestrutura dedicada.

Embora o foco deste artigo é sobre os SKU P, muito do que é descrito também é relevante para os SKUs. Em contraste com a subscrição Premium SKUs, SKUs do Azure requerem sem compromisso de tempo e são cobradas à hora. Eles fornecem elasticidade completa, permitindo dimensionamento cópia de segurança, reduzir verticalmente, colocar em pausa, retomam e eliminam. 

É de de Power BI Embedded do Azure em grande parte do escopo deste artigo, mas ele é descrito no [abordagens do teste](service-premium-capacity-optimize.md#testing-approaches) secção do artigo de capacidades Premium otimizar como uma opção económica e prática para testar e avaliar cargas de trabalho. Para saber mais sobre os SKUs do Azure, veja [documentação do Azure Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Compra

As subscrições do Power BI Premium são compradas por administradores no Centro de administração do Microsoft 365. Especificamente, apenas os administradores globais do Office 365 ou os administradores de faturação pode comprar SKUs. Se forem comprados, o inquilino recebe um número correspondente de núcleos virtuais para atribuir a capacidades, conhecidas como *agrupamento de núcleos virtuais*. Por exemplo, a compra de uma P3 SKU fornece ao inquilino 32 núcleos. Para obter mais informações, consulte [como comprar o Power BI Premium](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Capacidades dedicadas

Com o Power BI Premium, obtém *dedicado capacidades*. Em contraste com uma capacidade partilhada, onde as cargas de trabalho executado em recursos informáticos partilhados com outros clientes, uma capacidade dedicada é para utilização exclusiva por uma organização. É isolada com recursos dedicados de computacionais que apresentam um desempenho fiável e consistente para o conteúdo alojado. 

Áreas de trabalho residem dentro de capacidades. Cada utilizador do Power BI tem uma área de trabalho pessoal, conhecida como **minha área de trabalho**. Áreas de trabalho adicionais podem ser criadas para permitir a colaboração e a implantação, e eles são conhecidos como **áreas de trabalho de aplicação**. Por predefinição, áreas de trabalho, incluindo espaços de trabalho pessoas, são criadas na capacidade partilhada. Quando tem capacidades Premium, áreas de trabalho de minhas áreas de trabalho e de aplicações podem ser atribuídas a capacidades Premium.

### <a name="capacity-nodes"></a>Nós de capacidade

Conforme descrito no [licenciamento e assinaturas](#subscriptions-and-licensing) secção, há duas famílias de SKU do Power BI Premium: **EM** e **P**. Todos os SKUs de Premium de Power BI estão disponíveis como capacidade *nós*, cada um representando uma quantidade de conjunto de recursos que consiste de processador, memória e armazenamento. Além de recursos, cada SKU tem limites operacionais no número de ligações de DirectQuery e ligação em direto por segundo e o número de modelo paralelo é atualizada.

Processamento é obtido por um determinado número de núcleos virtuais, dividido igualmente entre o back-end e front-end.

**Núcleos de back-end** são responsáveis pela funcionalidade do Power BI principal, incluindo processamento de consultas, gestão de cache, executar os serviços R, atualização de modelo, processamento de linguagem natural (perguntas e respostas) e composição do lado do servidor de relatórios e imagens. Núcleos de back-end são atribuídos uma quantidade fixa de memória que é principalmente utilizado para modelos de host, conjuntos de dados também conhecido como Active Directory.

**Núcleos de front-end** são responsáveis por web service relatórios e dashboards, gestão de documentos, gestão de direitos de acesso, agendamento, APIs, carrega e transfere, em geral para todas as informações relacionadas ao usuário experiências e.

Armazenamento é definido como **100 TB por nó de capacidade**.

Os recursos e os limites de cada SKU Premium (e tamanho de maneira equivalente A SKU) estão descritas na tabela a seguir:

| Nós de capacidade | Núcleos virtuais totais | Núcleos virtuais de back-end | RAM (GB) | Núcleos virtuais de front-end | DirectQuery/ligação em direto (por seg) | Paralelismo de atualização do modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="capacity-workloads"></a>Cargas de trabalho de capacidade

Cargas de trabalho de capacidade são disponibilizados aos utilizadores de serviços. Por predefinição, Premium e capacidades do Azure suportam apenas uma conjunto de dados carga de trabalho associada à execução de consultas do Power BI. Não é possível desativar a carga de trabalho do conjunto de dados. Cargas de trabalho adicionais podem ser ativadas para [IA (os serviços cognitivos)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium), e [relatórios paginados](paginated-reports-save-to-power-bi-service.md). Estas cargas de trabalho são suportadas nas assinaturas Premium apenas. 

Cada carga de trabalho adicional permite configurar a memória máxima (como percentagem do total de memória disponível), que pode ser utilizada pela carga de trabalho. Valores predefinidos para a memória máxima são determinados pelo SKU. Pode maximizar os recursos disponíveis de sua capacidade ao permitir que apenas essas cargas de trabalho adicionais quando são usadas. E pode alterar as definições apenas ao determinar as definições predefinidas não estão a cumprir os requisitos de recursos de capacidade de memória. Cargas de trabalho podem ser habilitadas e configuradas para os administradores de capacidade por capacidade utilizando **definições de capacidade** no [portal de administração](service-admin-portal.md) ou utilizando o [APIs de REST de capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).  

![Ativar cargas de trabalho](media/service-admin-premium-workloads/admin-portal-workloads.png)

Para obter mais informações, consulte [configurar cargas de trabalho numa capacidade Premium](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Como a função de capacidades

AT todo o tempo, o serviço Power BI faz o melhor uso de recursos de capacidade, ao mesmo tempo não exceder os limites de imposto na capacidade.

Operações de capacidade são classificadas como *interativo* ou *em segundo plano*. Operações interativas incluem o processamento de pedidos e responder a interações de utilizador (filtragem, consultar as perguntas e respostas, etc.). Em geral, consulta do modelo de importação é memória com muitos recursos, enquanto a consulta de modelos do DirectQuery e ligação em direto é intensiva da CPU. Operações em segundo plano incluem o fluxo de dados e importar as atualizações de modelo e colocação em cache de consulta de dashboard.

É importante compreender que operações interativas estão sempre priorizadas em relação de operações em segundo plano para garantir a experiência de utilizador melhor possível. Se existirem recursos suficientes, operações em segundo plano são adicionadas a uma fila para processamento quando libertam de recursos. Operações de segundo plano, como atualizações de conjunto de dados, podem ser parado meio do processo pelo serviço do Power BI e adicionada a uma fila.

Modelos de importação tem de ser totalmente carregados na memória, de modo a podem ser consultadas ou atualizadas. O serviço Power BI gerencia a memória utilização utilizando algoritmos para garantir o máximo proveito da memória disponível sofisticados e pode provocar excesso ao consolidar a capacidade: Enquanto é possível para uma capacidade armazenar a importação de muitos modelos (até 100 TB por capacidade Premium), quando o respetivo armazenamento de disco combinado excede a memória suportada (e memória adicional é necessária para consulta e atualização), em seguida, não podem todos ser carregados na memória em ao mesmo tempo.

Modelos de importação, portanto, são carregados no e removidos da memória, de acordo com utilização. Um modelo de importação é carregado quando é consultada (operação interativa) e ainda não na memória, ou quando está a ser atualizado (operação de fundo).

A remoção de um modelo de memória é conhecida como *expulsão*. É uma operação que Power BI pode realizar rapidamente, dependendo do tamanho dos modelos. Se a capacidade não está a experienciar qualquer pressão de memória, os modelos são simplesmente carregados na memória e permanecem lá. No entanto, quando a memória insuficiente está disponível para carregar um modelo, o serviço Power BI primeiro precisará para libertar memória. Isso libera memória através da deteção de modelos que se tornaram Inativos por procurar modelos, que não foram utilizados nos últimos três minutos \[ [1](#endnote-1)\]e, em seguida, expulsá-los. Se não existirem não existem modelos Inativos para expulsar, o serviço Power BI procura modelos carregados para operações em segundo plano expulsar. Um último recurso, após 30 segundos de tentativas falhadas \[ [1](#endnote-1)\], está a falhar a operação interativa. Neste caso, o utilizador de relatórios é notificado da falha com uma sugestão para tentar novamente em breve. Em alguns casos, os modelos podem ser baixados da memória devido a operações de serviço.

É importante ressaltar que expulsão de conjunto de dados é um comportamento normal e esperado. Esforça-se para maximizar a utilização da memória pelo carregamento e o descarregamento modelos cujos tamanhos combinados podem exceder a memória disponível. É por design e completamente transparente para os utilizadores de relatório. As taxas de expulsão alta não significa necessariamente que a capacidade é isolá resourced. Eles podem, no entanto, se tornar uma preocupação se sofrer uma capacidade de resposta de consulta ou atualização devido a taxas de expulsão elevada.

As atualizações de modelos de importação são sempre elevado consumo de memória como modelos têm de ser carregados na memória. Memória adicional é necessária para processamento. Uma atualização completa pode utilizar aproximadamente dobra a quantidade de memória, o modelo precisa. Isto garante que o modelo pode ser consultado durante o processamento, uma vez que as consultas são enviadas para o modelo existente, até que a atualização foi concluída e estão disponíveis novos dados de modelo. Atualização incremental exigirá menos memória e foi possível concluir com mais rapidez e, por isso, pode reduzir substancialmente pressão nos recursos de capacidade. As atualizações também podem ser intensiva da CPU para modelos, especialmente aqueles com transformações complexas do Power Query ou tabelas/colunas calculadas que são complexas ou baseiam-se em tabelas grandes.

As atualizações, como consultas, exigem que o modelo ser carregado na memória. Se existir memória insuficiente, o serviço Power BI tentará Inativos modelos expulsar e, se não for possível (como todos os modelos são Active Directory), a tarefa de atualização é colocada na fila. As atualizações são normalmente intensiva da CPU, ainda mais assim que as consultas. Por esse motivo, existem limites no número de atualizações em simultâneo, definido como 1,5 vezes o número de back-end núcleos virtuais, arredondados por excesso de capacidade. Se existirem demasiadas atualizações em simultâneo, uma atualização agendada será colocado em fila. Quando estas situações ocorrerem, demora mais tempo para a atualização concluir. A pedido é atualizada, como as acionada por um pedido de utilizador ou uma chamada à API tentará três vezes \[ [1](#endnote-1)\]. Se ainda não tenha recursos suficientes, a atualização, em seguida, irá falhar.

Notas de secção:   
<a name="endnote-1"></a>\[1\] sujeitas a alterações.

### <a name="regional-support"></a>Suporte regional

Quando criar uma nova capacidade, os administradores globais do Office 365 e administradores de serviço do Power BI pode especificar uma região em que áreas de trabalho atribuídas à capacidade irá residir. Isso é conhecido como **Multi-Geo**. Com Multi-Geo, organizações podem satisfazer os requisitos de residência de dados mediante a implementação de conteúdo para os datacenters numa região específica, mesmo se for diferente da região em que reside a subscrição do Office 365. Para obter mais informações, consulte [Multi-Geo suporte do Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Gestão de capacidade

Gerir capacidades Premium envolve criar ou eliminar as capacidades, atribuir administradores, atribuir áreas de trabalho, a configuração de cargas de trabalho, monitorização e fazendo ajustes para otimizar o desempenho de capacidade. 

Os administradores globais do Office 365 e administradores de serviço do Power BI podem criar capacidades Premium a partir de núcleos virtuais disponíveis ou modificar as capacidades de Premium existentes. Quando é criada uma capacidade, o tamanho de capacidade e a região geográfica são especificados e, é atribuído a capacidade, pelo menos, um administrador. 

Quando as capacidades são criadas, a maioria das tarefas administrativas são concluídas na [do portal de administração](service-admin-portal.md).

![Portal de administração](media/service-premium-what-is/premium-admin-portal.png)

Os administradores de capacidade podem atribuir áreas de trabalho à capacidade, gerir permissões de utilizador e atribuir outros administradores. Os administradores de capacidade também podem configurar cargas de trabalho, ajustar as alocações de memória e se necessário, reinicie uma capacidade, repor as operações em caso de uma sobrecarga de capacidade.

![Portal de administração](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Os administradores de capacidade também podem tornar-se de que uma capacidade está a funcionar sem problemas. Pode monitorizar o direito de estado de funcionamento de capacidade no portal de administração ou com a aplicação de métricas de capacidade Premium.

Para saber mais sobre as capacidades de criação, atribuição de administradores e atribuir áreas de trabalho, veja [capacidades Premium gerir](service-premium-capacity-manage.md). Para saber mais sobre as funções, veja [funções de administrador relativo ao Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Monitorização

Monitorização de capacidades Premium fornece aos administradores uma compreensão de como as capacidades estão a funcionar. As capacidades podem ser monitorizadas com o portal de administração e o [aplicação de métricas de capacidade do Power BI Premium](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

A monitorização no portal do fornece uma vista rápida com métricas de alto nível com a indicação de cargas colocadas e os recursos utilizados pela sua capacidade, média, nos últimos sete dias. 

![Portal de administração](media/service-premium-what-is/premium-admin-portal-health.png)

O **métricas de capacidade do Power BI Premium** aplicação fornece as informações mais detalhadas sobre o desempenho das suas capacidades. A aplicação fornece um dashboard de alto nível e relatórios mais detalhados.

![Dashboard da aplicação de métricas](media/service-admin-premium-monitor-capacity/app-dashboard.png)

A partir do dashboard da aplicação pode clicar numa célula de métrica para abrir um relatório aprofundado. Os relatórios fornecem métricas detalhadas e capacidade de filtragem de desagregação nas informações mais importantes que precisam manter as suas capacidades de funcionar sem problemas.

![Contagens indicam potencial saturação de CPU de tempo de espera de picos periódicos da consulta](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Para saber mais sobre as capacidades de monitorização, veja [monitorização no portal de administração do Power BI](service-admin-premium-monitor-portal.md) e [monitorização com a aplicação de métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Otimizar as capacidades

A melhor utilização das suas capacidades é essencial para garantir o desempenho a utilizadores get e esteja tirando o máximo valor pelo seu investimento de Premium. Ao monitorizar as métricas-chave, os administradores podem determinar a melhor maneira para resolver afunilamentos e tome as medidas necessárias. Para obter mais informações, consulte [capacidades Premium otimizar](service-premium-capacity-optimize.md) e [cenários de capacidade de Premium](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>Capacidades de REST APIs

As APIs de REST do Power BI inclui uma coleção de [APIs de capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities). Com as APIs, os administradores por meio de programação podem gerir muitos aspectos das suas capacidades Premium, incluindo ativar e desativar a cargas de trabalho, a atribuição de áreas de trabalho a uma capacidade e muito mais.

## <a name="large-datasets"></a>Grandes conjuntos de dados

Dependendo do SKU, o Power BI Premium suporta carregar arquivos de modelo do Power BI Desktop (. pbix) até um máximo de **10GB** de tamanho. Quando carregado, o modelo, em seguida, pode ser publicado para uma área de trabalho atribuída a uma capacidade Premium. O conjunto de dados, em seguida, pode ser atualizado para até **12 GB** de tamanho.

### <a name="size-considerations"></a>Considerações de tamanho

Modelos grandes podem exigir com muitos recursos. Deve ter, pelo menos, um SKU P1 para os modelos superiores a 1 GB. Embora a publicação de modelos grandes áreas de trabalho alicerçado A SKUs até A3 poderia trabalho, atualizá-las não são será.

A seguinte tabela descreve os SKUs recomendados para vários tamanhos de ficheiro .pbix:

   |SKU  |Tamanho do ficheiro .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4 e P5    | até 10 GB   |

O SKU A4 do Power BI Embedded é igual ao SKU P1, A5 = P2 e A6 = P3. Tenha em atenção que a publicação de modelos grandes em SKUs A e EM poderá devolver erros que não são específicos ao erro de limitação do tamanho dos modelos na capacidade partilhada. É provável que os erros de atualização de modelos grandes em SKUs A e EM indiquem limites de tempo excedidos como a causa. 

Os ficheiros. pbix representam dados num *altamente comprimido estado*. Provavelmente, os dados serão expandidos várias vezes quando forem carregados na memória. A partir daí, poderão ser expandidos mais algumas vezes durante a atualização de dados.

Atualização agendada de grandes conjuntos de dados pode demorar muito tempo e muitos recursos. É importante não agende demasiadas Atualizações sobrepostas. É recomendável [atualização incremental](service-premium-incremental-refresh.md) estiver configurado, uma vez que é mais rápida e confiável e consome menos recursos.

A carga de grandes conjuntos de dados de relatórios inicial pode demorar muito tempo, se já tiverem passado algum tempo desde a última vez que o conjunto de dados foi utilizado. Uma barra de carregamento para relatórios de carregamento mais demorado apresenta o progresso do carregamento.

Enquanto a memória por consulta e restrições de tempo serem muito superiores na capacidade Premium, recomenda-se que usar filtros e segmentações de dados para limitar os elementos visuais para apresentar apenas o que é necessário.

## <a name="incremental-refresh"></a>Atualização incremental

A atualização incremental fornece uma parte integral de ter e manutenção de grandes conjuntos de dados no Power BI Premium. A atualização incremental tem muitas vantagens, por exemplo, as atualizações são mais rápidas porque apenas os dados que tenha alterado tem de ser atualizados. As atualizações são mais confiáveis porque não é necessário manter as ligações longa para origens de dados voláteis. Consumo de recursos é reduzido porque menos atualização dos dados reduz o consumo geral de memória e outros recursos. Políticas de atualização incremental são definidas na **Power BI Desktop**e aplicadas quando publicado para uma área de trabalho uma capacidade Premium. 

![Detalhes de atualização](media/service-premium-incremental-refresh/refresh-details.png)

Para obter mais informações, consulte [Incremental atualizar no Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Relatórios paginados

Relatórios paginados, suportados no P1-P3 e A4_A6 SKUs, baseiam-se na tecnologia de linguagem RDL (Report Definition Language) no SQL Server Reporting Services. Porém, com base na tecnologia RDL, não é o mesmo que o Power BI Report Server, que é uma plataforma de relatórios que pode ser baixada, que pode instalar no local, também é incluído com o Power BI Premium. Relatórios paginados são formatados para se ajustarem a uma página que pode ser impressos ou partilhada. Dados são apresentados numa tabela, mesmo que a tabela abrange várias páginas. Ao utilizar gratuitamente [ **Power BI Report Builder** ](https://go.microsoft.com/fwlink/?linkid=2086513) aplicativo de área de trabalho do Windows, o autor de utilizadores paginado relatórios e publique-os para o serviço.

No Power BI Premium, os relatórios de Paginated são uma carga de trabalho que tem de estar ativada para uma capacidade com o portal de administração. Os administradores de capacidade podem ativar e, em seguida, especifique a quantidade de memória como uma percentagem geral da capacidade recursos de memória. Ao contrário de outros tipos de cargas de trabalho, o escalão Premium é executado relatórios paginados num espaço contido dentro da capacidade. O máximo de memória especificado para este espaço é utilizado se a carga de trabalho é Active Directory ou não. A predefinição é 20%. 

Para obter mais informações, consulte [relatórios no Power BI Premium paginados](paginated-reports-report-builder-power-bi.md). Para saber mais sobre como ativar a carga de trabalho de relatórios de Paginated, veja [configurar cargas de trabalho](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI Report Server
 
Incluído com o com o Power BI Premium, o Power BI Report Server é um *locais* servidor de relatórios com um portal web. Pode criar sua BI ambiente no local e distribuir relatórios por trás da firewall da sua organização. Servidor de relatórios concede aos utilizadores acesso interativa e avançada e capacidades de relatórios de enterprise do SQL Server Reporting Services. Os utilizadores podem explorar dados visuais e descobrir rapidamente padrões para melhor, tomar decisões mais rápidas. Servidor de relatórios fornece governação em seus próprios termos. Se e quando chegar a hora, o Power BI Report Server facilita a migrar para a cloud, em que sua organização pode tirar partido de todas as funcionalidades do Power BI Premium.

Para obter mais informações, consulte [Power BI Report Server](report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Partilha de conteúdo ilimitado

Com o Premium, qualquer pessoa, quer estejam dentro ou fora da sua organização pode ver conteúdo do Power BI, incluindo relatórios paginados e interativos sem comprar licenças individuais. 

![Partilha de conteúdos](media/service-premium-what-is/premium-sharing.png)

Premium permite uma distribuição alargada de conteúdos por utilizadores Pro sem a necessidade de licenças do Pro para destinatários que ver o conteúdo. Licenças Pro são necessárias para os criadores de conteúdo. Os criadores de ligar a origens de dados, dados de modelo e criar relatórios e dashboards que são empacotadas como aplicativos de área de trabalho. 

Para obter mais informações, consulte [licenciamento do Power BI](service-admin-licensing-organization.md).

## <a name="tool-connectivity-preview"></a>Conectividade de ferramenta (pré-visualização)

Nos bastidores, a empresa comprovada da Microsoft **motor Vertipaq de serviços de análise** capacita a conjuntos de dados do Power BI. O Analysis Services fornece a capacidade de programação e aplicação de cliente e a ferramenta de suportam através das APIs que suportam o protocolo XMLA de padrão aberto e de bibliotecas de cliente. Atualmente, suportam conjuntos de dados do Power BI Premium *só de leitura* operações da Microsoft e aplicações de cliente de terceiros e ferramentas através de **pontos de extremidade XMLA**. 

Ferramentas da Microsoft, como o SQL Server Management Studio e SQL Server Profiler e aplicações de terceiros como o DAX Studio e aplicativos de visualização de dados, podem ligar e consultar conjuntos de dados Premium ao utilizar eventos XMLA, DAX, MDX, DMVs e rastreio. 

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)

Para obter mais informações, consulte [ligar a conjuntos de dados com as ferramentas e aplicativos cliente](service-premium-connect-tools.md).

## <a name="acknowledgements"></a>Confirmações

Peter Myers, MVP de plataforma de dados e especialista no Power BI independente com [soluções totalmente](https://www.bitwisesolutions.com.au/), e o Microsoft Power BI Customer Advisory Team (CAT) são os maiores contribuinte a este artigo.

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Gerir capacidades Premium](service-premium-capacity-manage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||
