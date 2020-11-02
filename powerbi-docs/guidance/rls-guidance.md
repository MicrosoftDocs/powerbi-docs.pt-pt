---
title: Orientação de segurança ao nível da linha (RLS) com o Power BI Desktop
description: Orientação para imposição da segurança ao nível da linha (RLS) nos modelos de dados com o Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 644e4499a335f18febadf33c371bd15e01499701
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349627"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Orientação de segurança ao nível da linha (RLS) com o Power BI Desktop

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Descreve as boas práticas de design para impor a segurança ao nível de linha (RLS) nos modelos de dados.

É importante compreender as _linhas da tabela_ dos filtros RLS. Estas não podem ser configuradas para restringir o acesso a objetos do modelo, incluindo tabelas, colunas ou medidas.

> [!NOTE]
> Este artigo não descreve a RLS nem como a configurar. Para obter mais informações, veja [Restringir o acesso aos dados com segurança ao nível da linha (RLS) para o Power BI Desktop](../create-reports/desktop-rls.md).
>
> Além disso, não abrange a imposição da RLS em ligações em direto para modelos alojados externamente com o Azure Analysis Services ou o SQL Server Analysis Services. Nestes casos, a RLS é imposta pelo Analysis Services. Quando o Power BI se liga com o início de sessão único (SSO), o Analysis Services aplicará a RLS (exceto se a conta tiver privilégios de administrador).

## <a name="create-roles"></a>Criar funções

É possível criar várias funções. Quando estiver a considerar as necessidades de permissões para um único utilizador do relatório, tente criar uma única função que concede todas estas permissões, em vez de um design em que o utilizador de relatório será membro de várias funções. Tal deve-se ao facto de um utilizador do relatório poder ser mapeado para várias funções, diretamente com a conta de utilizador ou indiretamente através da associação ao grupo de segurança. Os mapeamentos de várias funções podem levar a resultados inesperados.

Quando são atribuídas várias funções a um utilizador de relatório, os filtros RLS tornam-se aditivos. Ou seja, os utilizadores do relatório podem ver as linhas da tabela que representam a união desses filtros. Além disso, em alguns cenários não é possível garantir que um utilizador do relatório não vê linhas numa tabela. Assim, ao contrário das permissões aplicadas a objetos de base de dados do SQL Server (e outros modelos de permissão), o princípio “uma vez negado sempre negado” não se aplica.

Considere um modelo com duas funções: a primeira função, denominada **Trabalhadores** , restringe o acesso a todas as linhas da tabela **Folha de pagamentos** , com a seguinte expressão de regra:

```dax
FALSE()
```

> [!NOTE]
> Uma regra não devolverá linhas de tabela quando a expressão a avaliar como **falsa** .

No entanto, uma segunda função, denominada **Gestores** , permite o acesso a todas as linhas da tabela **Folha de pagamentos** , com a seguinte expressão de regra:

```dax
TRUE()
```

Tenha em atenção: caso um utilizador de relatório seja mapeado a ambas as funções, verá todas as linhas da tabela **Folha de pagamentos** .

## <a name="optimize-rls"></a>Otimizar a RLS

A RLS funciona ao aplicar automaticamente filtros a todas as consultas DAX. Estes filtros, por sua vez, podem ter um impacto negativo no desempenho da consulta. Neste caso, uma RLS eficiente resume-se a um bom design de modelo. É importante seguir a orientação de conceção do modelo, conforme discutido nos seguintes artigos:

- [Compreender o que é um esquema de estrela e qual a importância para o Power BI](star-schema.md)
- Todos os artigos de orientação das relações encontrados na [documentação de orientação do Power BI](./index.yml)

Em geral, é normalmente mais eficiente impor filtros RLS em tabelas de dimensão e não em tabelas de factos. E, dependerem de relações bem concebidas para garantir que os filtros RLS se propagam a outras tabelas do modelo. Como tal, evite utilizar a função DAX [LOOKUPVALUE](/dax/lookupvalue-function-dax) se as relações do modelo conseguirem obter o mesmo resultado.

Sempre que os filtros RLS forem impostos nas tabelas DirectQuery e existirem relações com outras tabelas DirectQuery, confirme que otimiza a base de dados de origem. Pode envolver a conceção de índices adequados ou a utilização de colunas calculadas persistentes. Para obter mais informações, veja [Orientação do modelo DirectQuery no Power BI Desktop](directquery-model-guidance.md).

### <a name="measure-rls-impact"></a>Medir o impacto da RLS

É possível medir o impacto sobre o desempenho dos filtros RLS no Power BI Desktop com o [Analisador de Desempenho](../create-reports/desktop-performance-analyzer.md). Primeiro, determine as durações das consultas dos elementos visuais do relatório quando a RLS não é aplicada. Em seguida, utilize o comando **Ver Como** no separador do friso **Modelação** para impor a RLS e determinar e comparar as durações das consultas.

## <a name="configure-role-mappings"></a>Configurar os mapeamentos das funções

Uma vez publicadas no Power BI, os membros devem ser mapeados para as funções dos conjuntos de dados. Apenas os proprietários dos conjuntos de dados ou os administradores das áreas de trabalho podem adicionar membros a funções. Para obter mais informações, veja [Segurança ao nível da linha (RLS) com o Power BI (Gerir a segurança no modelo)](../admin/service-admin-rls.md#manage-security-on-your-model).

Os membros podem ser contas de utilizador ou grupos de segurança. Sempre que possível, recomendamos que mapeie os grupos de segurança para funções de conjunto de dados. Envolve a associação dos membros do grupo de segurança no Azure Ative Directory. Possivelmente, delega a tarefa aos administradores de rede.

## <a name="validate-roles"></a>Validar as funções

Teste cada função para garantir que filtra corretamente o modelo. Pode testar facilmente com o comando **Ver Como** no separador do friso **Modelação** .

Quando o modelo tiver regras dinâmicas com a função DAX [USERNAME](/dax/username-function-dax), confirme que testa quanto a valores esperados _e inesperados_ . Ao incorporar o conteúdo do Power BI, especificamente com o cenário [Os dados pertencem à aplicação](../developer/embedded/embedding.md#embedding-for-your-customers), a lógica da aplicação pode transmitir qualquer valor como nome de utilizador de identidade em vigor. Sempre que possível, confirme que valores acidentais ou maliciosos resultam em filtros que não devolvem linhas.

Considere um exemplo com o Power BI Embedded, em que a aplicação passa a função de tarefa do utilizador como o nome de utilizador em vigor: “Gestor” ou “Trabalhador”. Os gestores conseguem ver todas as linhas, mas os trabalhadores só conseguem ver a linhas onde o valor da coluna **Tipo** é “Interno”.

É definida a seguinte expressão da regra:

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

O problema desta expressão de regra é que todos os valores, exceto “Trabalhador”, devolvem _todas as linhas da tabela_ . Assim, um valor acidental, como “Trbalhador”, devolverá acidentalmente todas as linhas da tabela. Portanto, é mais seguro escrever uma expressão que testa cada valor esperado. Na seguinte expressão de regra melhorada, um valor inesperado resultará na devolução de uma tabela sem linhas.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>Conceção parcial da RLS

Por vezes os cálculos precisam de valores não limitados pelos filtros RLS. Por exemplo, um relatório pode precisar de apresentar um rácio de receitas obtidas pela região de vendas do utilizador do relatório relativamente a _todas as receitas obtidas_ .

Apesar de não ser possível que uma expressão DAX substitua a RLS, de facto, nem sequer consegue determinar se a RLS está aplicada, pode utilizar uma tabela de modelo resumida. A tabela de modelo resumida é consultada para recuperar as receitas de “todas as regiões” e não é limitada pelos filtros RLS.

Vamos ver como implementar este requisito de design. Primeiro, considere o seguinte modelo de design:

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="É apresentada uma imagem do diagrama de modelo. O diagrama é descrito nos seguintes parágrafos.":::

O modelo é composto por quatro tabelas:

- A tabela **Vendedor** armazena uma linha por vendedor. Inclui a coluna **EmailAddress** , que armazena o endereço de e-mail de cada vendedor. Esta tabela está oculta.
- A tabela **Vendas** armazena uma linha por encomenda. Inclui a medida **% de Receitas de Todas as Regiões** , que se destina a devolver um rácio das receitas obtidas pela região do utilizador do relatório relativamente às receitas obtidas por todas as regiões.
- A tabela **Data** armazena uma linha por data e permite filtrar e agrupar o ano e o mês.
- **SalesRevenueSummary** é uma tabela calculada. Armazena receitas totais para cada data de encomenda. Esta tabela está oculta.

A expressão seguinte define a tabela calculada **SalesRevenueSummary** :

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> Uma [tabela de agregação](../transform-model/desktop-aggregations.md) poderia conseguir o mesmo requisito de conceção.

A seguinte regra RLS é aplicada à tabela **Vendedor** :

```dax
[EmailAddress] = USERNAME()
```

Cada uma das três relações de modelo é descrita na tabela seguinte:

|Relação|Descrição|
|---------|---------|
|![Terminador de fluxograma 1.](media/common/icon-01-red-30x30.png)|Existe uma relação de muitos para muitos entre as tabelas **Vendedor** e **Vendas** . A regra RLS filtra a coluna **EmailAddress** da tabela **Vendedor** oculta, com a função DAX [USERNAME](/dax/username-function-dax). O valor da coluna **Região** (do utilizador do relatório) propaga-se para a tabela **Vendas** .|
|![Terminador de fluxograma 2.](media/common/icon-02-red-30x30.png)|Existe uma relação de um para muitos entre as tabelas **Data** e **Vendas** .|
|![Terminador de fluxograma 3.](media/common/icon-03-red-30x30.png)|Existe uma relação de um para muitos entre as tabelas **Data** e **SalesRevenueSummary** .|

A seguinte expressão define a medida **% de Receita de Todas as Regiões** :

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> Tenha cuidado para evitar revelar informações sensíveis. Se existirem apenas duas regiões neste exemplo, será possível a um utilizador do relatório calcular as receitas para a outra região.

## <a name="avoid-using-rls"></a>Evitar utilizar a RLS

Evite utilizar a RLS, sempre que isso fizer sentido. Se tiver apenas uma pequena quantidade de regras simplistas da RLS que aplicam filtros estáticos, considere publicar vários conjuntos de dados. Nenhum dos conjuntos de dados define funções, dado que cada conjunto de dados contém dados para um público-alvo de utilizadores do relatório específico, que tem as mesmas permissões de dados. Em seguida, crie uma área de trabalho por público-alvo e atribua permissões de acesso à área de trabalho ou aplicação.

Por exemplo, uma empresa que tem apenas duas regiões de vendas decide publicar um conjunto de dados _para cada região de vendas_ para diferentes áreas de trabalho. Os conjuntos de dados não impõem a RLS. Utilizam, no entanto, [parâmetros de consulta](/power-query/power-query-query-parameters) para filtrar os dados de origem. Desta forma, o mesmo modelo é publicado em cada área de trabalho, apenas têm diferentes valores de parâmetros de conjunto de dados. Os vendedores têm acesso a apenas uma das áreas de trabalho (ou aplicações publicadas).

Existem várias vantagens associadas ao evitar a RLS:

- **Aumentar o desempenho das consultas:** pode resultar numa melhoria do desempenho devido à existência de menos filtros.
- **Modelos mais pequenos:** embora resulte em mais modelos, estes são de menor dimensão. Os modelos mais pequenos podem melhorar a reatividade de atualização dos dados e das consultas, especialmente se a capacidade de alojamento estiver a sofrer pressão a nível dos recursos. Além disso, é mais fácil manter as dimensões do modelo abaixo dos limites de dimensão impostas pela capacidade. Por fim, é mais fácil equilibrar as cargas de trabalho entre diferentes capacidades, dado que pode criar espaços de trabalho, ou mover áreas de trabalho, para diferentes capacidades.
- **Funcionalidades adicionais:** as funcionalidades do Power BI que não funcionam com a RLS, como [Publicar na Web](../collaborate-share/service-publish-to-web.md), podem ser utilizadas.

No entanto, existem desvantagens associadas ao cenário Evitar a RLS:

- **Várias áreas de trabalho:** é necessária uma área de trabalho para cada público-alvo de utilizadores do relatório. Se as aplicações forem publicadas, também significa que existe uma aplicação por público-alvo de utilizadores do relatório.
- **Duplicação de conteúdos:** devem ser criados relatórios e dashboards em cada área de trabalho, o que requer esforço e tempo adicional para a instalação e a manutenção.
- **Utilizadores com privilégios elevados:** os utilizadores com privilégios elevados, que pertencem a vários públicos-alvo de utilizadores do relatório, não conseguem ter uma vista consolidada dos dados. Terão de abrir vários relatórios (em diferentes áreas de trabalho ou aplicações).

## <a name="troubleshoot-rls"></a>Resolver problemas da RLS

Se a RLS produzir resultados inesperados, verifique a existência dos seguintes problemas:

- Existência de relações incorretas entre tabelas de modelos, em termos de mapeamento de colunas e direções de filtro.
- A propriedade de relação **Aplicar filtro de segurança em ambas as direções** não está corretamente definida. Para obter mais informações, veja [Documento de orientação das relações bidirecionais](relationships-bidirectional-filtering.md).
- As tabelas não contêm dados.
- São carregados valores incorretos nas tabelas.
- O utilizador é mapeado para várias funções.
- O modelo inclui tabelas de agregação e as regras RLS não filtram consistentemente agregações e detalhes. Para obter mais informações, veja [Utilizar agregações no Power BI Desktop (RLS para agregações)](../transform-model/desktop-aggregations.md#rls-for-aggregations).

Quando um utilizador específico não consegue ver dados, pode ser devido à UPN não estar armazenada ou ter sido introduzida incorretamente. Pode ocorrer abruptamente porque a conta de utilizador foi alterada como resultado de uma alteração de nome.

> [!TIP]
> Para efeitos de teste, adicione uma medida que devolve a função DAX [USERNAME](/dax/username-function-dax). Pode chamar-lhe algo como “Quem Sou Eu”. Em seguida, adicione a medida a um elemento visual de cartão num relatório e publique-a no Power BI.

Quando um utilizador específico consegue ver todos os dados, é possível que esteja a aceder aos relatórios diretamente a partir da área de trabalho e que seja o proprietário do conjunto de dados. A RLS só é imposta quando:

- O relatório é aberto numa aplicação.
- O relatório é aberto numa área de trabalho, e o utilizador está mapeado para a [função Visualizador](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Segurança ao nível da linha (RLS) com o Power BI](../admin/service-admin-rls.md)
- [Restringir o acesso a dados com segurança a nível da linha (RLS) para o Power BI Desktop](../create-reports/desktop-rls.md)
- [Relações de modelos no Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
