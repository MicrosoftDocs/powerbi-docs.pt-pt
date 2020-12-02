---
title: Documentação de orientação dos modelos compostos no Power BI Desktop
description: Documentação de orientação para desenvolver Modelos compostos.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/24/2019
ms.openlocfilehash: 53c0af04a76d4cf8cfacd49002434ecbc246fbe8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394388"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Documentação de orientação dos modelos compostos no Power BI Desktop

Este artigo destina-se aos modeladores de dados que criam Modelos compostos no Power BI. Descreve casos práticos dos Modelos compostos e oferece orientação para a conceção. Especificamente, esta documentação de orientação serve para o ajudar a determinar se um Modelo composto é apropriado para a solução. Se for apropriado, este artigo também o vai ajudar a conceber um modelo ideal.

> [!NOTE]
> A introdução aos Modelos compostos não é abordada neste artigo. Se não estiver completamente familiarizado com os Modelos compostos, recomendamos que leia primeiro o artigo [Utilizar modelos compostos no Power BI Desktop](../transform-model/desktop-composite-models.md).
>
> Dado que os Modelos compostos consistem em, pelo menos, uma origem de dados do DirectQuery, também é importante que tenha uma compreensão completa das [relações de modelos](../transform-model/desktop-relationships-understand.md), dos [modelos do DirectQuery](../connect-data/desktop-directquery-about.md) e da [documentação de orientação sobre a conceção de modelos do DirectQuery](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Casos práticos dos modelos compostos

Sempre que possível, é melhor desenvolver um modelo no modo Importação. Este modo oferece uma maior flexibilidade a nível de conceção e o melhor desempenho.

No entanto, os desafios relacionados com grandes volumes de dados ou com a comunicação de dados quase em tempo real não podem ser resolvidos através dos Modelos de importação. Em qualquer um destes casos, pode considerar um modelo do DirectQuery, desde que os dados estejam armazenados numa origem de dados individual, [suportada pelo modo DirectQuery](../connect-data/power-bi-data-sources.md).

Adicionalmente, pode considerar o desenvolvimento de um Modelo composto nas seguintes situações.

- O modelo pode ser um modelo do DirectQuery, mas quer aumentar o desempenho. Nos Modelos compostos, o desempenho pode ser melhorado ao configurar o armazenamento adequado para cada tabela. Também pode adicionar [agregações](../transform-model/desktop-aggregations.md). Ambas as otimizações são discutidas neste artigo.
- Quer combinar um modelo do DirectQuery com dados adicionais, que devem ser importados para o modelo. Os dados importados podem ser carregados de uma origem de dados diferente ou de tabelas calculadas.
- Quer combinar duas ou mais origens de dados do DirectQuery num único modelo.

> [!NOTE]
> Os Modelos compostos não podem combinar origens de dados da Ligação em Direto nem origens de dados da base de dados de análise do DirectQuery. As origens de dados da Ligação em Direto incluem [modelos alojados externamente](../connect-data/service-datasets-understand.md#external-hosted-models) e conjuntos de dados do Power BI. As origens de dados da base de dados de análise do DirectQuery incluem o SAP Business Warehouse e o SAP HANA.

## <a name="optimize-model-design"></a>Otimizar o design de modelos

Pode otimizar os Modelos compostos através da configuração dos [modos de armazenamento](../transform-model/desktop-storage-mode.md) das tabelas e da adição de [agregações](../transform-model/desktop-aggregations.md).

### <a name="table-storage-mode"></a>Modo de armazenamento de tabelas

Nos Modelos compostos, pode configurar o modo de armazenamento de cada tabela (exceto tabelas calculadas):

- **DirectQuery**: recomendamos que defina este modo para tabelas que representem grandes volumes de dados ou que precisem de apresentar resultados quase em tempo real. Os dados nunca serão importados para estas tabelas. Normalmente, estas tabelas serão tabelas de factos, ou seja, tabelas utilizadas para resumos.
- **Importação**: recomendamos que defina este modo para tabelas de dimensão, ou seja, tabelas utilizadas para filtragem e agrupamento. De facto, é a única opção para tabelas baseadas em origem de dados não suportadas pelo modo DirectQuery. As tabelas calculadas são sempre tabelas de Importação.
- **Dual**: recomendamos que defina este modo para as tabelas de dimensão, quando existe a possibilidade de que estas sejam consultadas em conjunto com as tabelas de factos do DirectQuery da mesma origem de dados.

Existem vários cenários possíveis quando o Power BI consulta um Modelo composto:

- **Consulta apenas a(s) tabela(s) de Importação ou Dual**: todos os dados são recuperados da cache de modelos. Proporcionará o desempenho mais rápido possível. Este cenário é comum para tabelas de dimensão consultadas através de filtros ou elementos visuais de segmentação.
- **Consulta a(s) tabela(s) Dual ou a(s) tabela(s) do DirectQuery a partir da mesma origem de dados**: todos os dados são recuperados através do envio de uma ou mais consultas nativas para a origem de dados DirectQuery. Proporcionará o desempenho mais rápido possível, especialmente quando existem índices adequados nas tabelas de origem de dados. Este cenário é comum para consultas relacionadas com tabelas de dimensão Dual e tabelas de fatos do DirectQuery. Estas consultas são _intra ilha_ e todas as relações um-para-um ou um-para-muitos são avaliadas como [relações regulares](../transform-model/desktop-relationships-understand.md#regular-relationships).
- **Todas as outras consultas**: estas consultas envolvem relações entre ilhas. Tal deve-se a uma tabela de Importação estar relacionada com uma tabela do DirectQuery ou uma tabela Dual estar relacionada com uma tabela do DirectQuery de uma origem de dados diferente e, neste caso, comporta-se como uma tabela de Importação. Todas as relações são avaliadas como [relações limitadas](../transform-model/desktop-relationships-understand.md#limited-relationships). Significa também que os agrupamentos aplicados a tabelas que não são DirectQuery devem ser enviadas para a origem de dados do DirectQuery como uma tabela virtual. Neste caso, a consulta nativa pode não ser eficiente, especialmente para grandes conjuntos de agrupamentos. E, pode expor dados confidenciais na consulta nativa.

Em resumo, recomendamos que:

- Considere cuidadosamente se um Modelo composto é a solução certa, embora permita a integração ao nível de modelo de diferentes origens de dados, também introduz complexidades de design com possíveis consequências
- Defina o modo de armazenamento como **DirectQuery** quando uma tabela é uma tabela de factos que armazena grandes volumes de dados ou caso precise de fornecer resultados quase em tempo real
- Defina o modo de armazenamento como **Dual** quando é uma tabela de dimensão e que será consultada juntamente com as tabelas de factos do **DirectQuery** com base na mesma origem de dados
- Configure as frequências de atualização adequadas para manter a cache de modelos das tabelas Dual (e quaisquer tabelas calculadas dependentes) em sincronia com a(s) base(s) de dados da origem de dados
- Garanta a integridade dos dados entre origens de dados (incluindo a cache de modelos). As relações limitadas eliminam linhas quando os valores de coluna relacionados não correspondem
- Otimize as origens de dados do DirectQuery com índices apropriados para uniões, filtragens e agrupamentos eficientes
- Não carregue dados confidenciais para as tabelas de Importação ou Dual se existir risco de interceção das consultas nativas. para obter mais informações, veja [Utilizar modelos compostos no Power BI Desktop (Implicações de segurança)](../transform-model/desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>Agregações

Pode adicionar agregações às tabelas do DirectQuery no Modelo composto. As agregações são colocadas em cache no modelo e, como tal, comportam-se como tabelas de Importação (embora não possam ser utilizadas como tabelas de modelos). O objetivo delas é melhorar o desempenho para obter consultas de “agregação superior”. Para obter mais informações, consulte [Agregações no Power BI Desktop](../transform-model/desktop-aggregations.md).

Recomendamos que as tabelas de agregação sigam uma regra básica: a sua contagem de linhas deve, pelo menos, ter um fator 10 vezes inferior à tabela subjacente. Por exemplo, se uma tabela subjacente armazenar mil milhões de linhas, a tabela de agregação não deverá exceder os 100 milhões de linhas. Esta regra garante que existe um ganho de desempenho adequado em relação ao custo de criação e manutenção da tabela de agregação.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Utilizar modelos compostos no Power BI Desktop](../transform-model/desktop-composite-models.md)
- [Relações de modelos no Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [Modelos do DirectQuery no Power BI Desktop](../connect-data/desktop-directquery-about.md)
- [Utilização do DirectQuery no Power BI Desktop](../connect-data/desktop-use-directquery.md)
- [DirectQuery model troubleshooting in Power BI Desktop](../connect-data/desktop-directquery-troubleshoot.md) (Resolver problemas com o modelo DirectQuery no Power BI Desktop)
- [Origens de dados do Power BI](../connect-data/power-bi-data-sources.md)
- [Modo de armazenamento no Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Agregações no Power BI Desktop](../transform-model/desktop-aggregations.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)
