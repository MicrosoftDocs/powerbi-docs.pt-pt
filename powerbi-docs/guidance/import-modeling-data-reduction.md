---
title: Técnicas de redução de dados para modelos de importação
description: Conheça diferentes técnicas para ajudar a reduzir os dados carregados em modelos de importação.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/05/2019
ms.author: v-pemyer
ms.openlocfilehash: c61a21f400de009815ecb685f989b1cdafbcdb22
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875614"
---
# <a name="data-reduction-techniques-for-import-modeling"></a>Técnicas de redução de dados para modelos de importação

Este artigo destina-se aos modeladores de dados do Power BI Desktop que criam modelos de importação. Descreve diferentes técnicas para ajudar a reduzir os dados carregados em modelos de importação.

Os modelos de importação são carregados com dados que são comprimidos, otimizados e depois armazenados para um disco pelo motor de armazenamento VertiPaq. Quando os dados de origem são carregados para a memória, é possível observar uma compressão de 10x e é razoável esperar que 10 GB de dados de origem possam ser comprimidos para cerca de 1 GB. Além disso, quando os dados persistem num disco, é possível alcançar uma redução adicional de 20%.

Apesar da eficácia do motor de armazenamento VertiPaq,é importante que faça todos os possíveis para minimizar os dados a carregar nos seus modelos. Esta recomendação é particularmente importante para grandes modelos ou modelos que se irão tornar maiores ao longo do tempo. Eis quatro motivos para esta recomendação:

- Os tamanhos de modelo maiores podem não ser suportados pela sua capacidade. A capacidade partilhada pode alojar modelos com um tamanho máximo de 1 GB, enquanto as capacidades Premium podem alojar modelos com um tamanho máximo de 13 GB. Para obter mais informações, leia o artigo [Suporte do Power BI Premium para grandes conjuntos de dados](../service-premium-large-datasets.md).
- Os tamanhos de modelo mais pequenos reduzem a disputa de recursos de capacidade, especialmente da memória. Esta situação permite o carregamento de mais modelos em simultâneo e por maiores períodos de tempo, o que resulta em taxas de expulsão mais baixas. Para obter mais informações, leia o tópico [Funcionamento das Capacidades](../whitepaper-powerbi-premium-deployment.md#how-capacities-function) do documento técnico [Implementação do Power BI Premium](../whitepaper-powerbi-premium-deployment.md).
- Os modelos mais pequenos alcançam uma atualização de dados mais rápida, o que resulta em menores taxas de latência, num maior débito de atualização dos conjuntos de dados e em menos pressão sobre o sistema de origem e os recursos de capacidade.
- As contagens de linhas de tabela mais pequenas podem levar a avaliações de cálculos mais rápidas, o que pode proporcionar um melhor desempenho das consultas em geral.

Este artigo aborda oito técnicas de redução de dados diferentes. Incluem-se:

- [Remover colunas desnecessárias](#remove-unnecessary-columns)
- [Remover linhas desnecessárias](#remove-unnecessary-rows)
- [Agrupar por e resumir](#group-by-and-summarize)
- [Otimizar os tipos de dados de colunas](#optimize-column-data-types)
- [Preferir as colunas personalizadas](#preference-for-custom-columns)
- [Desativar o carregamento de consultas do Power Query](#disable-power-query-query-load)
- [Desativar data/hora automáticas](#disable-auto-datetime)
- [Mudar para o Modo misto](#switch-to-mixed-mode)

## <a name="remove-unnecessary-columns"></a>Remover colunas desnecessárias

As colunas de tabela de modelo servem para dois fins principais:

- **Criação de relatórios**, para conseguir estruturas de relatórios que filtram, agrupam e resumem os dados de modelo adequadamente
- **Estruturação de modelos**, ao suportar relações de modelos, cálculos de modelos, funções de segurança e até mesmo a formatação de cor dos dados

As colunas que não servem para estes fins irão provavelmente ser removidas. A remoção de colunas também se denomina _filtragem vertical_.

Recomendamos que crie modelos que tenham exatamente o número certo de colunas, com base nos requisitos de criação de relatórios conhecidos. Estes requisitos podem sofrer alterações ao longo do tempo, mas tenha em atenção que é mais fácil adicionar colunas posteriormente do que removê-las posteriormente. A remoção de colunas pode danificar os relatórios ou a estrutura dos modelos.

## <a name="remove-unnecessary-rows"></a>Remover linhas desnecessárias

As tabelas de modelos devem ser carregadas com o menor número de linhas possível. Pode fazê-lo ao carregar conjuntos de linhas filtrados em tabelas de modelos por duas razões diferentes: para filtrar por entidade ou pelo tempo. A remoção de linhas também se denomina _filtragem horizontal_.

A **filtragem por entidade** implica o carregamento de um subconjunto de dados de origem no modelo. Por exemplo, em vez de ocorrer o carregamento de factos de vendas de todas as regiões, ocorre o carregamento de factos de apenas uma região. Esta abordagem de criação irá resultar em muitos modelos inferiores e também pode eliminar a necessidade de definir a segurança ao nível da linha (mas irá exigir a concessão de permissões de conjuntos de dados específicas no serviço Power BI e a criação de relatórios "duplicados" que ligam a cada conjunto de dados). Pode tirar partido da utilização de parâmetros do Power Query e Ficheiros de modelos do Power BI para simplificar a gestão e a publicação. Para obter mais informações, leia a mensagem de blogue [Deep Dive into Query Parameters and Power BI Templates](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) (Aprofundar Conhecimentos sobre os Parâmetros de Consulta e os Modelos do Power BI).

A **filtragem pelo tempo** implica a limitação da quantidade do _histórico de dados_ carregada nas tabelas de factos (e a limitação das linhas de datas carregadas nas tabelas de datas de modelo). Sugerimos que não carregue automaticamente todo o histórico disponível, a menos que este carregamento seja um requisito de criação de relatórios conhecido. Será útil compreender que os filtros do Power Query baseados no tempo podem ser parametrizados e até mesmo definidos para utilizarem períodos de tempo relativos (em relação à data de atualização, por exemplo, os últimos cinco anos). Além disso, tenha em atenção que as alterações retrospetivas aos filtros de tempo não irão danificar os relatórios. Apenas irão resultar numa menor (ou maior) quantidade de histórico de dados disponível nos relatórios.

## <a name="group-by-and-summarize"></a>Agrupar por e resumir

A técnica mais eficaz para reduzir o tamanho de um modelo é, provavelmente, o carregamento de dados pré-resumidos. Esta técnica pode ser utilizada para aumentar a capacidade das tabelas de factos. No entanto, há uma clara contrapartida: a perda de detalhes.

Por exemplo, uma tabela de factos de vendas de origem armazena uma linha por linha de ordem. É possível alcançar uma redução de dados significativa ao resumir todas as métricas de vendas e agrupar por data, cliente e produto. É possível alcançar uma redução de dados ainda mais significativa ao agrupar por data _ao nível do mês_. Esta estratégia pode levar a uma possível redução de 99% no tamanho do modelo. No entanto, a criação de relatórios a nível do dia ou a nível de ordem individual já não é possível. A decisão de resumir dados de factos implica sempre contrapartidas. Esta contrapartida pode ser mitigada por um Design de modelo misto. Esta opção será abordada posteriormente no tópico [Mudar para o Modo misto](#switch-to-mixed-mode).

## <a name="optimize-column-data-types"></a>Otimizar os tipos de dados de colunas

O motor de armazenamento VertiPaq utiliza estruturas de dados separadas para cada coluna. Por predefinição, estas estruturas de dados alcançam as melhores otimizações para dados de colunas numéricos, que utilizam a codificação de valores. No entanto, o texto e outros dados não numéricos utilizam a codificação de hashes. Esta particularidade exige que o motor de armazenamento atribua um identificador numérico a cada valor de texto único contido na coluna. Assim, é o identificador numérico que é armazenado posteriormente na estrutura de dados, exigindo uma pesquisa de hashes durante o armazenamento e a realização de consultas.

Em algumas instâncias específicas, pode converter os dados de texto de origem em valores numéricos. Por exemplo, um número de ordem de venda pode ser consistentemente antecedido por um valor de texto (por exemplo, "SO123456"). O prefixo pode ser removido e o valor de número de ordem pode ser convertido num número inteiro. No caso das tabelas grandes, esta possibilidade pode resultar numa redução de dados significativa, particularmente quando a coluna contém valores de cardinalidade únicos ou elevados.

Neste exemplo, recomendamos que defina a propriedade Resumo Predefinido da coluna para "Não Resumir". Esta ação irá ajudar a minimizar o resumo inadequado dos valores de número de ordem.

## <a name="preference-for-custom-columns"></a>Preferir as colunas personalizadas

O motor de armazenamento VertiPaq armazena as colunas calculadas de modelo (definidas na fórmula DAX) tal como as colunas normais com origem no Power Query. No entanto, as estruturas de dados são armazenadas de forma ligeiramente diferente e, normalmente, têm uma compressão menos eficaz. Além disso, são criadas assim que todas as tabelas do Power Query são carregadas, o que pode resultar num maior tempo de atualização de dados. Portanto, é menos eficaz adicionar colunas de tabelas como colunas _calculadas_ do que como colunas _calculadas_ do Power Query (definidas em M).

É preferível criar colunas personalizadas no Power Query. Quando a origem é uma base de dados, pode alcançar uma maior eficácia de carregamento de duas formas. O cálculo pode ser definido na instrução SQL (através da linguagem nativa de consultas do fornecedor) ou materializado como uma coluna na origem de dados.

Contudo, em alguns casos, as colunas calculadas de modelo podem ser a melhor opção. Um destes casos é quando a fórmula implica a avaliação de medidas ou exige funcionalidades de modelação específicas apenas suportadas em funções de DAX. Para obter mais informações sobre exemplos como este, veja o artigo [Understanding functions for parent-child hierarchies in DAX](/dax/understanding-functions-for-parent-child-hierarchies-in-dax) (Compreender as funções de hierarquias principal-subordinado em DAX).

## <a name="disable-power-query-query-load"></a>Desativar o carregamento de consultas do Power Query

As consultas do Power Query que se destinam a suportar a integração de dados com outras consultas não devem ser carregadas no modelo. Para evitar o carregamento da consulta no modelo, tenha o cuidado de garantir que desativa o carregamento de consultas nestes casos.

![Desativar o carregamento de uma consulta do Power Query](media/import-modeling-data-reduction/power-query-disable-query-load.png)

## <a name="disable-auto-datetime"></a>Desativar data/hora automáticas

O Power BI Desktop inclui uma opção intitulada _Data/hora automáticas_. Quando estiver ativada, cria uma tabela de data/hora automáticas oculta para que as colunas de data suportem autores de relatórios ao configurar filtros, agrupar e desagregar em função de períodos temporais no calendário. As tabelas ocultas são de facto tabelas calculadas que aumentam o tamanho do modelo. Para obter orientações sobre como utilizar esta opção, consulte o artigo [Orientações sobre data/hora automáticas no Power BI Desktop](../desktop-auto-date-time.md).

## <a name="switch-to-mixed-mode"></a>Mudar para o Modo misto

No Power BI Desktop, um design de Modo misto produz um Modelo composto. Resumidamente, permite-lhe determinar o modo de armazenamento _de cada tabela_. Assim, cada tabela pode ter a sua propriedade de Modo de Armazenamento definida como Importar ou DirectQuery (outra opção é Duplo).

Uma técnica eficaz para reduzir o tamanho do modelo é definir a propriedade Modo de Armazenamento de tabelas de factos maiores para DirectQuery. Tenha em atenção que esta abordagem de criação pode funcionar bem em conjunto com a estratégia abordada no anterior tópico [Agrupar por e resumir](#group-by-and-summarize). Por exemplo, os dados de vendas resumidos podem ser utilizados para alcançar relatórios resumidos com elevado desempenho. Uma página de pormenorização pode apresentar as vendas granulares de contextos de filtros específicos e diminuir estes contextos, apresentando todas as ordens de venda dentro do contexto. Neste exemplo, a página de pormenorização iria incluir elementos visuais com base numa tabela do DirectQuery para obter os dados de ordens de venda.

No entanto, há muitas implicações de segurança e desempenho relacionadas com os Modelos compostos. Para obter mais informações, leia o artigo [Utilizar modelos compostos no Power BI Desktop](../desktop-composite-models.md).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre a criação de Modelos de importação do Power BI, veja os seguintes artigos:

- [Utilizar modelos compostos no Power BI Desktop](../desktop-composite-models.md)
- [Modo de armazenamento no Power BI Desktop](../desktop-storage-mode.md)
