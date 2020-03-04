---
title: Guia de otimização para o Power BI
description: Guia de otimização do Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 0f29b70a42375be945d206672116219b7d5a3b48
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77610001"
---
# <a name="optimization-guide-for-power-bi"></a>Guia de otimização para o Power BI

Este artigo apresenta orientações que permitem aos programadores e administradores produzir e manter soluções do Power BI otimizadas. Pode otimizar a sua solução em diferentes camadas da arquitetura. As camadas incluem:

- As origens de dados
- O modelo de dados
- As visualizações, incluindo os dashboards, os relatórios do Power BI ou os relatórios paginados do Power BI
- O ambiente, incluindo as capacidades, os gateways de dados e a rede

## <a name="optimizing-the-data-model"></a>Otimizar o modelo de dados

O modelo de dados suporta toda a experiência de visualização. Os modelos de dados são hospedados externa ou internamente e são referidos como _conjuntos de dados_ no Power BI. É importante compreender as opções e escolher o tipo de conjunto de dados apropriado para a sua solução. Existem três modos de conjuntos de dados: Importação, DirectQuery e Composto. Para obter mais informações, veja [Conjuntos de dados no serviço Power BI](../service-datasets-understand.md) e [Modos dos conjuntos de dados no serviço Power BI](../service-dataset-modes-understand.md).

Para obter orientações específicas sobre o modo de conjunto de dados, veja:

- [Técnicas de redução de dados para modelos de importação](import-modeling-data-reduction.md)
- [Orientação do modelo do DirectQuery no Power BI Desktop](directquery-model-guidance.md)
- [Documentação de orientação dos modelos compostos no Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Otimizar as visualizações

As visualizações do Power BI podem ser dashboards, relatórios do Power BI ou relatórios paginados do Power BI. Cada uma destas visualizações tem arquiteturas diferentes e, assim, cada uma tem as suas próprias orientações. 

### <a name="dashboards"></a>Dashboards

É importante compreender que o Power BI mantém uma cache para os mosaicos do dashboard, exceto para os mosaicos de relatórios dinâmicos e para os mosaicos de transmissão em fluxo. Para obter mais informações, veja [Atualização dos dados no Power BI (Atualização de mosaico)](../refresh-data.md#tile-refresh). Se o conjunto de dados impuser a [segurança ao nível da linha (RLS)](../service-admin-rls.md) dinâmica, confirme que compreende as implicações no desempenho, dado que os mosaicos serão colocados em cache numa base por utilizador.

Quando afixa mosaicos de relatório dinâmico a um dashboard, estes não são processados a partir da cache de consulta. Em vez disso, comportam-se como relatórios e tornam as consultas aos cores de back-end rápidas.

Como o nome indica, obter os dados da cache permite um desempenho melhor e mais consistente do que depender da origem de dados. Uma forma de tirar partido desta funcionalidade é definir os dashboards como a página de destino principal dos seus utilizadores. Afixe os elementos visuais mais utilizados e pedidos aos dashboards. Desta forma, os dashboards tornam-se numa valiosa “primeira linha de defesa” e proporcionam consistência no desempenho com uma carga menor na capacidade. Os utilizadores podem clicar num relatório para analisar os detalhes.

No caso dos conjuntos de dados de ligação em direto e DirectQuery, a cache é atualizada periodicamente através de consultas à origem de dados. Por predefinição, ocorre a cada hora, embora possa configurar uma frequência diferente nas definições dos conjuntos de dados. Cada atualização da cache enviará consultas para a origem de dados subjacente para atualizar a cache. O número de consultas geradas depende do número de elementos visuais afixados aos dashboards que dependem da respetiva origem de dados. Tenha em atenção que, se a segurança ao nível da linha estiver ativada, as consultas são geradas para cada contexto de segurança diferente. Por exemplo, considere que existem duas funções diferentes que categorizam os utilizadores e que têm duas vistas diferentes dos dados. Durante a atualização da cache de consulta, o Power BI gera dois conjuntos de consultas.

### <a name="power-bi-reports"></a>Relatórios do Power BI

Existem várias recomendações para otimizar os designs de relatório do Power BI.

> [!NOTE]
> Quando os relatórios se baseiam num conjunto de dados DirectQuery, para obter otimizações de designs de relatório adicionais, veja [Orientação do modelo DirectQuery no Power BI Desktop (Otimizar os designs de relatório)](directquery-model-guidance.md#optimize-report-designs).

#### <a name="apply-the-most-restrictive-filters"></a>Aplicar filtros mais restritivos

Quanto maior for o volume de dados que um elemento visual tem de apresentar, mais lento será o carregamento. Embora este princípio pareça óbvio, pode ser fácil esquecê-lo. Por exemplo, digamos que tem um conjunto de dados grande. Além do conjunto de dados, pode criar um relatório com uma tabela. Os utilizadores finais podem utilizar as segmentações na página para aceder às linhas que querem, normalmente, só estão interessados em algumas dezenas de linhas.

Um erro comum é deixar a vista predefinida da tabela não filtrada, ou seja, com mais de 100 milhões de linhas. Os dados destas linhas são carregados para a memória e descomprimidos a cada atualização. Este processamento cria elevadas exigências em termos de memória. Solução: utilize o filtro “Top N” para reduzir o número máximo de itens apresentados na tabela. Pode definir um número máximo de itens muito superior ao que os utilizadores necessitam, por exemplo 10 000. Como resultado, a experiência do utilizador final não é alterada, mas a utilização da memória baixa consideravelmente E, o mais importante, o desempenho melhora.

Aconselhamos uma abordagem de design semelhante à apresentada acima para todos os elementos visuais no relatório. Faça a pergunta: "Será que são precisos todos os dados neste elemento visual? Existe alguma forma de filtrar o volume de dados apresentados no elemento visual de modo a que tenha um impacto mínimo na experiência do utilizador final?" Tenha em atenção que as tabelas, em particular, podem utilizar muita memória.

#### <a name="limit-visuals-on-report-pages"></a>Limitar os elementos visuais nas páginas de relatórios

O princípio apresentado acima aplica-se também ao número de elementos visuais adicionados a uma página de relatório. Recomendamos vivamente que limite o número de elementos visuais numa determinada página de relatório de forma a ter apenas os necessários. As [páginas de pormenorização](report-drillthrough.md) e as [descrições de páginas de relatório](report-page-tooltips.md) são úteis para proporcionar detalhes adicionais sem acrescentar mais elementos visuais à página.

#### <a name="evaluate-custom-visual-performance"></a>Avaliar o desempenho dos elementos visuais personalizados

Certifique se de que testa os seus elementos visuais personalizados com cuidado para garantir um desempenho elevado. Os elementos visuais personalizados mal otimizados podem afetar negativamente o desempenho de todo o relatório.

### <a name="power-bi-paginated-reports"></a>Relatórios paginados do Power BI

Os designs de relatórios paginados do Power BI podem ser otimizados ao aplicar as melhores práticas de design à obtenção de dados do relatório. Para obter mais informações, veja [Orientação para a obtenção de dados para relatórios paginados](report-paginated-data-retrieval.md).

Adicionalmente, confirme que tem memória suficiente alocada à [carga de trabalho de relatórios paginados](../service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>Otimizar o ambiente

Pode otimizar o ambiente do Power BI ao configurar as definições de capacidade, dimensionar os gateways de dados e reduzir a latência da rede.

### <a name="capacity-settings"></a>Definições de capacidade

Com as capacidades dedicadas, disponíveis com o Power BI Premium (SKUs P) ou o Power BI Embedded (SKUs A, A4 a A6), pode gerir as definições de capacidade. Para obter mais informações, veja [Gerir capacidades Premium](../service-premium-capacity-manage.md). Para obter orientação sobre como otimizar a capacidade, veja [Otimizar as capacidades Premium](../service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Dimensionamento do gateway

É necessário um gateway sempre que o Power BI precise de aceder a dados que não estejam diretamente acessíveis através da Internet. Pode instalar o [gateway de dados no local](../service-gateway-onprem.md) num servidor no local ou numa Infraestrutura como Serviço (IaaS) alojada na VM.

Para compreender as cargas de trabalho do gateway e as recomendações de dimensionamento, veja [Dimensionamento do gateway de dados no local](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Latência de rede

A latência de rede pode ter um impacto no desempenho do relatório ao aumentar o tempo necessário para os pedidos chegarem ao serviço Power BI e para as respostas serem devolvidas. Os inquilinos no Power BI são atribuídos a uma região específica.

> [!TIP]
> Para determinar a localização do seu inquilino, veja [Onde está localizado o meu inquilino do Power BI?](../service-admin-where-is-my-tenant-located.md)

Quando os utilizadores de um inquilino acedem ao serviço Power BI, os respetivos pedidos são sempre encaminhados para esta região. À medida que os pedidos chegam ao serviço Power BI, o serviço poderá enviar pedidos adicionais, por exemplo, para a origem de dados subjacente ou para um gateway de dados, que também estão sujeitos à latência de rede.

As ferramentas como o [Azure Speed Test](https://azurespeedtest.azurewebsites.net/) podem fornecer um indicador da latência de rede entre o cliente e a região do Azure. No geral, para minimizar o impacto da latência de rede, tente manter as origens de dados, os gateways e o seu cluster do Power BI o mais próximo possível. Preferencialmente, a residirem na mesma região. Se a latência de rede for um problema, experimente colocar os gateways e as origens de dados mais perto do cluster do Power BI ao colocá-los em máquinas virtuais alojadas na cloud.

## <a name="monitoring-performance"></a>Monitorizar o desempenho

Pode monitorizar o desempenho para identificar estrangulamentos. As consultas lentas ou os elementos visuais de relatório devem ser alvo de otimizações contínuas. A monitorização pode ser feita no momento de criação no Power BI Desktop ou nas cargas de trabalho de produção nas capacidades do Power BI Premium. Para obter mais informações, veja [Monitorizar o desempenho dos relatórios no Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Documentação de orientação do Power BI](index.yml)
- [Monitorizar o desempenho dos relatórios](monitor-report-performance.md)
- Documento técnico: [Planear uma Implementação Empresarial do Power BI](https://go.microsoft.com/fwlink/?linkid=2057861)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
