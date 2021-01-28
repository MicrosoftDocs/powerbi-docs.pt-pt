---
title: Model relationships in Power BI Desktop (Relações de modelos no Power BI Desktop)
description: Introduz teoria sobre relações de modelos no Power BI Desktop
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 10/15/2019
ms.openlocfilehash: 0f9edc247401ccf72ec1a5b0aebb5b3a074a5494
ms.sourcegitcommit: 1872a167d1e4d731ad00cf8a6d951c31aa54bcce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/28/2021
ms.locfileid: "98925710"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Model relationships in Power BI Desktop (Relações de modelos no Power BI Desktop)

Este artigo destina-se aos Modeladores de dados de importação que trabalham com o Power BI Desktop. É um tópico importante de design de modelos essencial para oferecer modelos intuitivos, precisos e ideais.

Para uma discussão mais profunda sobre design de modelo ideal, incluindo relações e funções de tabela, leia o artigo [Compreender o que é um esquema de estrela e qual a importância para o Power BI](../guidance/star-schema.md).

## <a name="relationship-purpose"></a>Objetivo da relação

Em resumo, as relações do Power BI propagam filtros aplicados nas colunas de tabelas de modelo a outras tabelas de modelo. Os filtros serão propagados desde que haja um caminho de relação a seguir, o que pode envolver a propagação em várias tabelas.

Os caminhos de relação são deterministas, o que significa que os filtros são sempre propagados da mesma forma e sem variação aleatória. No entanto, as relações podem ser desativadas ou ter o contexto de filtro modificado por cálculos de modelo que utilizam funções do DAX específicas. Para obter mais informações, leia o tópico [Funções do DAX relevantes](#relevant-dax-functions) mais adiante neste artigo.

> [!IMPORTANT]
> É importante entender que as relações de modelo não impõem a integridade dos dados. Para obter mais informações, leia o tópico [Avaliação de relação](#relationship-evaluation) mais adiante neste artigo. Este tópico explica como as relações de modelo se comportam quando existem problemas de integridade dos dados com os seus dados.

Vamos ver como as relações propagam filtros com um exemplo animado.

:::image type="content" source="media/desktop-relationships-understand/animation-filter-propagation.gif" alt-text="Exemplo animado a mostrar a propagação dos filtros de relação.":::

Neste exemplo, o modelo consiste em quatro tabelas: **Categoria**, **Produto**, **Ano** e **Vendas**. A tabela **Categoria** está relacionada com a tabela **Produto** e a tabela **Produto** está relacionada com a tabela **Vendas**. A tabela **Ano** também está relacionada com a tabela **Vendas**. Todas as relações são um para muitos (os detalhes estão descritos mais adiante neste artigo).

Uma consulta – possivelmente gerada por um elemento visual de cartão do Power BI – pede a quantidade total de vendas dos pedidos de vendas feitos para uma única categoria, **Cat-A** e, para um único ano, **AF2018**. É por este motivo que pode ver filtros aplicados nas tabelas **Categoria** e **Ano**. O filtro na tabela **Categoria** é propagado para a tabela **Produto** para isolar dois produtos atribuídos à categoria **Cat-A**. Em seguida, os filtros de tabela **Produto** propagam para a tabela **Vendas** para isolar apenas duas linhas de vendas para estes produtos. Estas duas linhas de vendas representam as vendas de produtos atribuídos à categoria **Cat-A**. A quantidade combinada das mesmas é de 14 unidades. Em simultâneo, o filtro da tabela **Ano** propaga-se para filtrar ainda mais a tabela **Vendas**, resultando apenas numa linha de vendas destinada para produtos atribuídos à categoria **Cat-A** e que foi pedida no ano **AF2018**. O valor da quantidade devolvido pela consulta é de 11 unidades. Observe que quando são aplicados vários filtros a uma tabela (como a tabela **Vendas** neste exemplo), é sempre uma operação AND, o que exige que todas as condições tenham de ser verdadeiras.

### <a name="disconnected-tables"></a>Tabelas desligadas

É raro uma tabela de modelo não estar relacionada com outra tabela de modelo. Essa tabela num design de modelo válido pode ser descrita como uma _tabela desligada_. Uma tabela desligada não se destina a propagar filtros para outras tabelas de modelo. Em vez disso, é utilizada para aceitar "entrada do utilizador" (talvez com um elemento visual de segmentação de dados), ao permitir que os cálculos de modelo utilizem o valor de entrada de forma significativa. Por exemplo, considere uma tabela desligada que é carregada com um intervalo de valores de taxa de câmbio de moeda. Desde que um filtro seja aplicado para filtrar por um valor de taxa única, o valor pode ser utilizado por uma expressão de medida para converter valores de vendas.

O parâmetro "E se" do Power BI Desktop é uma funcionalidade que cria uma tabela desligada. Para obter mais informações, leia o artigo [Criar e utilizar um parâmetro “E se” para visualizar variáveis no Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Propriedades da relação

Uma relação de modelo relaciona uma coluna numa tabela a uma coluna numa tabela diferente. (Há um caso especializado em que este requisito não é verdadeiro e isso aplica-se apenas a relações de várias colunas em modelos DirectQuery. Para obter mais informações, leia o artigo da função DAX [COMBINEVALUES](/dax/combinevalues-function-dax).)

> [!NOTE]
> Não pode relacionar uma coluna a uma coluna diferente _na mesma tabela_. Às vezes, isto é confundido com a capacidade de definir uma restrição de chave de referência de base de dados relacional que é a autorreferência de tabela. Este conceito de base de dados relacional pode ser utilizado para armazenar relações de elemento principal com subordinado (por exemplo, cada registo de colaborador está associado a um colaborador "reporta a"). A geração de uma hierarquia de modelo baseada neste tipo de relação não pode ser resolvida pela criação de relações de modelo. Para o fazer, leia o artigo [Parent and Child functions (Funções de elemento principal e subordinado)](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Cardinalidade

Cada relação de modelo deve ser definida com um tipo de cardinalidade. Existem quatro opções de tipo de cardinalidade que representam as características das colunas relacionadas "de" e "para". O lado "um" significa que a coluna contém valores únicos; o lado "muitos" significa que a coluna pode conter valores duplicados.

> [!NOTE]
> Se uma operação de atualização de dados tentar carregar valores duplicados para uma coluna do lado "um", a atualização de dados irá falhar.

As quatro opções, juntamente com as anotações abreviadas, estão descritas na seguinte lista com marcadores:

- Um para muitos (1:\*)
- Muitos para um (\*:1)
- Um para um (1:1)
- Muitos para muitos (\*:\*)

Quando cria uma relação no Power BI Desktop, o designer vai detetar e definir automaticamente o tipo de cardinalidade. O designer consulta o modelo para saber quais são as colunas que contêm valores exclusivos. Para modelos de Importação, o designer utiliza estatísticas de armazenamento interno; para modelos DirectQuery, envia consultas de criação de perfil para a origem de dados. No entanto, às vezes pode errar. Tal acontece porque as tabelas ainda devem ser carregadas com dados ou porque as colunas que espera que contenham valores duplicados contêm atualmente valores exclusivos. Seja qual for o caso, pode atualizar o tipo de cardinalidade desde que qualquer coluna do lado “um” contenha valores únicos (ou a tabela ainda não foi carregada com linhas de dados).

As opções de cardinalidade **Um para muitos** e **Muitos para um** são essencialmente as mesmas, e são também os tipos de cardinalidade mais comuns.

Ao configurar uma relação Um para muitos ou Muitos para um, deve escolher aquela que corresponde à ordem em que as colunas estão relacionadas. Considere a forma como configuraria a relação da tabela **Produto** com a tabela **Vendas** através da coluna **ProductID** encontrada em cada tabela. O tipo de cardinalidade seria _Um para muitos_, já que a coluna **ProductID** na tabela **Produto** contém valores exclusivos. Se tiver relacionado as tabelas na direção inversa, **Vendas** para **Produto**, a cardinalidade seria _Muitos para um_.

Uma relação **Um para um** significa que ambas as colunas contêm valores exclusivos. Este tipo de cardinalidade não é comum e provavelmente representa um design de modelo de qualidade inferior devido ao armazenamento de dados redundantes. Para obter mais informações sobre a utilização deste tipo de cardinalidade, veja [Documento de orientação das relações um-para-um](../guidance/relationships-one-to-one.md).

Uma relação **Muitos para muitos** significa que ambas as colunas podem conter valores duplicados. Esse tipo de cardinalidade é raramente utilizado. Normalmente, é útil ao criar requisitos de modelos complexos. Para obter orientação sobre a utilização deste tipo de cardinalidade, veja [Guia de relações muitos para muitos](../guidance/relationships-many-to-many.md).

> [!NOTE]
> O tipo de cardinalidade Muitos para muitos não é suportada atualmente para modelos desenvolvidos para o Power BI Report Server.

> [!TIP]
> Na vista de modelo do Power BI Desktop, pode interpretar o tipo de cardinalidade de uma relação ao olhar para os indicadores (1 ou \*) em ambos os lados da linha de relação. Para determinar as colunas que estão relacionadas, deve selecionar, ou passar o cursor sobre, a linha de relação para destacar as colunas.

### <a name="cross-filter-direction"></a>Direção de filtro cruzado

Cada relação de modelo deve ser definida com uma direção de filtro cruzado. A sua seleção determina as direções em que os filtros serão propagados. As opções de filtro cruzado disponíveis dependem do tipo de cardinalidade.

| Tipo de cardinalidade | Opções de filtro cruzado |
| --- | --- |
| Um para muitos (ou Muitos para um) | Único<br>Ambos |
| Um para um | Ambos |
| Muitos para muitos | Única (Tabela1 a Tabela2)<br>Única (Tabela2 a Tabela1)<br>Ambos |

A direção _única_ de filtro cruzado significa "direção única" e _Ambas_ significa "ambas as direções". Uma relação que filtra em ambas as direções é geralmente descrita como _bidirecional_.

Para relações Um para muitos, a direção do filtro cruzado é sempre do lado "um" e, opcionalmente, do lado "muitos" (bidirecional). Para relações Um para um, a direção do filtro cruzado é sempre de ambas as tabelas. Por fim, para as relações Muitos para muitos, a direção do filtro cruzado pode ser de uma das tabelas ou de ambas as tabelas. Tenha em conta que quando o tipo de cardinalidade inclui um lado "um", os filtros irão sempre propagar-se desse lado.

Quando a direção do filtro cruzado estiver definida como **Ambos**, existe uma propriedade adicional disponível. Pode aplicar a filtragem bidirecional quando forem aplicadas regras de segurança ao nível da linha (RLS). Para obter mais informações sobre a RLS, leia o artigo [Segurança ao nível da linha (RLS) com o Power BI Desktop](../create-reports/desktop-rls.md).

A modificação da direção do filtro cruzado da relação, incluindo a desativação da propagação do filtro, também pode ser feita por um cálculo de modelo. Pode ser feito com a função DAX [CROSSFILTER](/dax/crossfilter-function).

As relações bidirecionais podem afetar negativamente o desempenho. Além disso, a tentativa de configurar uma relação bidirecional pode resultar em caminhos de propagação de filtro ambíguos. Neste caso, o Power BI Desktop pode falhar ao consolidar a alteração da relação e irá alertá-lo com uma mensagem de erro. No entanto, por vezes o Power BI Desktop pode permitir que defina caminhos de relação ambíguos entre tabelas. As regras de precedência que afetam a deteção de ambiguidade e a resolução de caminho estão descritas mais adiante neste artigo no tópico [Regras de precedência](#precedence-rules).

É recomendável utilizar a filtragem bidirecional apenas conforme necessário. Para obter mais informações, veja [Documento de orientação das relações bidirecionais](../guidance/relationships-bidirectional-filtering.md).

> [!TIP]
> Na vista de modelo do Power BI Desktop, pode interpretar a direção de filtro cruzado de uma relação ao observar as pontas da seta ao longo da linha da relação. Uma única ponta de seta representa um filtro de direção única na direção da ponta de seta; uma ponta de seta dupla representa uma relação bidirecional.

### <a name="make-this-relationship-active"></a>Tornar esta relação ativa

Pode haver apenas um caminho de propagação de filtro ativo entre duas tabelas de modelo. No entanto, pode introduzir caminhos de relação adicionais, embora estas relações tenham de ser configuradas como _inativas_. As relações inativas podem ser ativadas apenas durante a avaliação de um cálculo de modelo. Pode ser feito com a função do DAX [USERELATIONSHIP](/dax/userelationship-function-dax).

Para obter mais informações, veja [Documento de orientação das relações ativas vs. inativas](../guidance/relationships-active-inactive.md).

> [!TIP]
> Na vista de modelo do Power BI Desktop, pode interpretar um estado ativo ou inativo da relação. Uma relação ativa é representada por uma linha sólida; uma relação inativa é representada como uma linha tracejada.

### <a name="assume-referential-integrity"></a>Assumir integridade referencial

A propriedade _Assumir integridade referencial_ está disponível apenas para relações Um para muitos e Um para um entre duas tabelas do modo de armazenamento do DirectQuery baseadas na mesma origem de dados. Quando ativadas, as consultas nativas enviadas para a origem de dados irão associar as duas tabelas através de uma ASSOCIAÇÃO INTERNA, em vez de uma ASSOCIAÇÃO EXTERNA. Geralmente, a ativação desta propriedade melhora o desempenho das consultas, embora dependa das especificidades da origem de dados.

Ative sempre esta propriedade quando existir uma restrição de chave de referência de base de dados entre as duas tabelas. Quando uma restrição de chave de referência não existir, ainda pode ativar a propriedade desde que tenha a certeza de que existe integridade dos dados.

> [!IMPORTANT]
> Se a integridade dos dados for comprometida, a associação interna irá eliminar linhas sem correspondência entre as tabelas. Por exemplo, considere uma tabela de **Vendas** de modelo com um valor de coluna **ProductID** que não existia na tabela de **Produto** relacionado. Filtrar a propagação da tabela de **Produto** para a tabela de **Vendas** irá eliminar as linhas de vendas de produtos desconhecidos. O que iria resultar numa subavaliação dos resultados das vendas.
>
> Para obter mais informações, veja o artigo [Definição Assumir integridade referencial no Power BI Desktop](../connect-data/desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Funções do DAX relevantes

Existem várias funções do DAX que são relevantes para relações de modelo. Cada função encontra-se descrita brevemente na seguinte lista com marcadores:

- [RELATED](/dax/related-function-dax): obtém o valor do lado "um".
- [RELATEDTABLE](/dax/relatedtable-function-dax): obtém uma tabela de linhas do lado "muitos".
- [USERELATIONSHIP](/dax/userelationship-function-dax): força a utilização de uma relação de modelo específico inativo.
- [CROSSFILTER](/dax/crossfilter-function): modifica a direção do filtro cruzado da relação (para uma ou ambas) ou desativa a propagação do filtro (nenhum).
- [COMBINEVALUES](/dax/combinevalues-function-dax): associa duas ou mais cadeias de texto numa cadeia de texto. A finalidade desta função é suportar relações de várias colunas em modelos do DirectQuery.
- [TREATAS](/dax/treatas-function): aplica o resultado de uma expressão de tabela como filtros a colunas de uma tabela não relacionada.
- [Funções de elemento principal e subordinado](/dax/parent-and-child-functions-dax): uma família de funções relacionadas que podem ser utilizadas para gerar colunas calculadas para a naturalização de uma hierarquia principal-subordinado. Estas colunas podem então ser utilizadas para criar uma hierarquia de nível fixo.

## <a name="relationship-evaluation"></a>Avaliação de relação

As relações de modelo, de uma perspetiva de avaliação, são classificadas como _regular_ ou _limitada_. Não é uma propriedade de relação configurável. Na verdade, é inferido do tipo de cardinalidade e da origem de dados das duas tabelas relacionadas. É importante entender o tipo de avaliação porque pode haver implicações de desempenho ou consequências, caso a integridade dos dados seja comprometida. Estas implicações e consequências de integridade estão descritas neste tópico.

Primeiro, é preciso conhecer alguma teoria de modelação para compreender totalmente as avaliações de relação.

Um modelo de Importação ou do DirectQuery obtém todos os seus dados da cache Vertipaq ou da base de dados de origem. Em ambas as instâncias, o Power BI consegue determinar que existe um lado "um" de uma relação.

No entanto, um modelo Composto pode ser constituído por tabelas que utilizam modos de armazenamento diferentes (Importação, DirectQuery ou Duplos) ou várias origens do DirectQuery. Cada origem, incluindo a cache do Vertipaq de Dados de importação, é considerada um _grupo de origem_. As relações de modelos podem então ser classificadas como _dentro do grupo de origem_ ou _entre vários grupos de origem_. Uma relação dentro do grupo de origem relaciona duas tabelas dentro de um grupo de origem, enquanto as relações entre vários grupos de origem relacionam tabelas de diferentes grupos de origem. Observe que as relações nos Modelos de importação ou do DirectQuery são sempre intra grupo de origem.

Vamos ver um exemplo de Modelo composto.

:::image type="content" source="media/desktop-relationships-understand/source-group-example.png" alt-text="Exemplo de um Modelo composto que consiste em dois grupos de origem.":::

Neste exemplo, o Modelo composto consiste em dois grupos de origem: um grupo de origem do Vertipaq e um grupo de origem do DirectQuery. O grupo de origem do Vertipaq contém três tabelas e o grupo de origem do DirectQuery contém duas tabelas. Existe uma relação entre grupos de origem para relacionar uma tabela no grupo de origem do Vertipaq com uma tabela no grupo de origem do DirectQuery.

### <a name="regular-relationships"></a>Relações regulares

Uma relação de modelo é _regular_ quando o motor de consulta pode determinar o lado "um" da relação. Tem a confirmação de que a coluna do lado "um" contém valores exclusivos. Todas as relações intra grupo de origem um-para-muitos são relações regulares.

No exemplo seguinte, existem duas relações regulares, ambas marcadas como **R**. As relações incluem a relação um-para-muitos contida no grupo de origem do Vertipaq e a relação um-para-muitos contida na origem do DirectQuery.

:::image type="content" source="media/desktop-relationships-understand/source-group-example-regular.png" alt-text="Exemplo de um Modelo composto que consiste em dois grupos de origem com relações regulares marcadas.":::

Para Modelos de importação, onde todos os dados são armazenados na cache do Vertipaq, é criada uma estrutura de dados para cada relação regular no momento da atualização de dados. As estruturas de dados consistem em mapeamentos indexados de todos os valores de coluna para coluna e a sua finalidade é acelerar a associação de tabelas no momento da consulta.

No momento da consulta, as relações regulares permitem que a _expansão da tabela_ ocorra. A expansão da tabela resulta na criação de uma tabela virtual, ao incluir as colunas nativas da tabela base e, em seguida, ao expandir para tabelas relacionadas. Para as tabelas Importação, é feito no motor de consulta; para as tabelas DirectQuery, é feito na consulta nativa enviada para a base de dados de origem (desde que a propriedade **Assumir integridade referencial** não esteja ativada). O motor de consulta age na tabela expandida, ao aplicar filtros e agrupar pelos valores nas colunas da tabela expandida.

> [!NOTE]
> As relações inativas também são expandidas, mesmo quando a relação não é utilizada por um cálculo. As relações bidirecionais não têm impacto na expansão da tabela.

Para relações Um para muitos, a expansão da tabela ocorre dos lados “muitos” para “um”, através da semântica ASSOCIAÇÃO EXTERNA À ESQUERDA. Quando um valor correspondente de "muitos" para o lado "um" não existir, é adicionada uma linha virtual em branco à tabela do lado "um".

A expansão de tabela também ocorre emrelações intra grupo de origem um-para-um, mas com a semântica EXTERNA COMPLETA. Desta forma, garante-se que as linhas virtuais em branco são adicionadas em ambos os lados, quando necessário.

As linhas virtuais em branco são efetivamente _Membros Desconhecidos_. Os membros desconhecidos representam violações de integridade referencial em que o valor do lado "muitos" não tem um valor do lado "um" correspondente. Idealmente, estes espaços em branco não devem existir e podem ser eliminados ao limpar ou reparar os dados de origem.

Vamos ver como a expansão da tabela funciona com um exemplo animado.

:::image type="content" source="media/desktop-relationships-understand/animation-expanded-table.gif" alt-text="Exemplo animado a mostrar a expansão da tabela.":::

Neste exemplo, o modelo consiste em três tabelas: **Categoria**, **Produto** e **Vendas**. A tabela **Categoria** está relacionada com a tabela **Produto** com uma relação de Um para muitos e a tabela **Produto** está relacionada com a tabela **Vendas** com uma relação de Um para muitos. A tabela **Categoria** contém duas linhas, a tabela **Produto** contém três linhas e as tabelas **Vendas** contêm cinco linhas. Existem valores correspondentes em ambos os lados de todas as relações, o que significa que não existem violações de integridade referencial. É revelada uma tabela expandida de tempo de consulta. A tabela consiste nas colunas das três tabelas. É efetivamente uma perspetiva desnormalizada dos dados contidos nas três tabelas. É adicionada uma nova linha à tabela **Vendas** e tem um valor de identificador de produção (9) que não tem valor um correspondente na tabela **Produto**. É uma violação de integridade referencial. Na tabela expandida, a nova linha tem valores (Em branco) para as colunas de tabela **Categoria** e **Produto**.

### <a name="limited-relationships"></a>Relações limitadas

Uma relação de modelo é _limitada_ quando não existe um lado "um" garantido. Pode acontecer por dois motivos:

- A relação utiliza um tipo de cardinalidade Muitos para muitos (mesmo se uma ou ambas as colunas tiverem valores exclusivos)
- A relação é entre grupos de origem (que só pode ocorrer em Modelos compostos)

No exemplo seguinte, existem duas relações limitadas, ambas marcadas como **L**. Ambas as relações incluem a relação muitos-para-muitos contida no grupo de origem do Vertipaq e a relação um-para-muitos entre grupos de origem.

:::image type="content" source="media/desktop-relationships-understand/source-group-example-limited.png" alt-text="Exemplo de um Modelo composto que consiste em dois grupos de origem com relações limitadas marcadas.":::

Para Modelos de importação, as estruturas de dados nunca são criadas para relações limitadas. O que significa que as associações de tabela devem ser resolvidas no momento da consulta.

A expansão da tabela nunca ocorre para relações limitadas. As associações das tabelas são alcançadas através da semântica ASSOCIAÇÃO INTERNA e, por este motivo, as linhas virtuais em branco não são adicionadas para compensar as violações de integridade referencial.

Existem restrições adicionais relacionadas com as relações limitadas:

- A função DAX RELATED não pode ser utilizada para obter os valores da coluna do lado "um"
- A imposição da RLS tem restrições de topologia

> [!NOTE]
> Na vista de modelo do Power BI Desktop, nem sempre é possível determinar se uma relação de modelo é regular ou limitada. Uma relação muitos-para-muitos será sempre limitada, já que é uma relação um-para-muitos quando é uma relação entre grupos de origem. Para determinar se é uma relação entre grupos de origem, terá de inspecionar os modos de armazenamento de tabela e as origens de dados para chegar à determinação correta.

### <a name="precedence-rules"></a>Regras de precedência

As relações bidirecionais podem introduzir vários (e, portanto, ambíguos) caminhos de propagação de filtros entre tabelas de modelo. A lista a seguir apresenta regras de precedência que o Power BI utiliza para a deteção de ambiguidade e a resolução do caminho:

1. Relações Muitos para um e Um para um, incluindo relações limitadas
2. Relações Muitos para muitos
3. Relações bidirecionais, na direção inversa (ou seja, do lado “Muitos”)

### <a name="performance-preference"></a>Preferência de desempenho

A lista a seguir ordena o desempenho da propagação do filtro, do desempenho mais rápido ao mais lento:

1. Relações um-para-muitos dentro do grupo de origem
2. Relações de cardinalidade de Muitos para muitos
3. Relações de modelo de Muitos para muitos obtidas com uma tabela intermediária e que envolve, pelo menos, uma relação bidirecional
4. Relações entre vários grupos de origem

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Compreender o que é um esquema de estrela e qual a importância para o Power BI](../guidance/star-schema.md)
- [Documento de orientação das relações um-para-um](../guidance/relationships-one-to-one.md)
- [Guia de relações muitos para muitos](../guidance/relationships-many-to-many.md)
- [Documento de orientação das relações ativas vs. inativas](../guidance/relationships-active-inactive.md)
- [Documento de orientação das relações bidirecionais](../guidance/relationships-bidirectional-filtering.md)
- [Documento de orientação da resolução de problemas de relações](../guidance/relationships-troubleshoot.md)
- Vídeo: [The Do's and Don'ts of Power BI Relationships](https://www.youtube.com/watch?v=78d6mwR8GtA) (O que deve fazer e o que não deve fazer nas Relações do Power BI)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
