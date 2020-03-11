---
title: Use cascading parameters in paginated reports (Utilizar parâmetros em cascata em relatórios paginados)
description: Orientação para conceber relatórios paginados com parâmetros em cascata.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 90f501b257313c48cbef13517747ff83cd9ea9d1
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920770"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Use cascading parameters in paginated reports (Utilizar parâmetros em cascata em relatórios paginados)

O presente artigo destina-se a si, na qualidade de autor de relatório que cria [relatórios paginados](../paginated-reports/paginated-reports-report-builder-power-bi.md) do Power BI. Fornece cenários para a criação de parâmetros em cascata. Os parâmetros em cascata são parâmetros do relatório com dependências. Quando um utilizador do relatório seleciona um valor (ou valores) de parâmetro, este será utilizado para definir os valores disponíveis para outro parâmetro.

> [!NOTE]
> Neste artigo, não abordamos a introdução aos parâmetros em cascata nem como os configurar. Se não estiver totalmente familiarizado com os parâmetros em cascata, recomendamos que leia primeiro [Add Cascading Parameters to a Report (Report Builder and SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs) (Adicionar Parâmetros em Cascata a um Relatório (Report Builder e SSRS)).

## <a name="design-scenarios"></a>Cenários de design

Existem dois cenários de design para utilizar os parâmetros em cascata e podem ser utilizados de forma eficaz para:

- Filtrar _grandes conjuntos_ de itens
- Apresentar itens _relevantes_

### <a name="example-database"></a>Base de dados de exemplo

Os exemplos apresentados neste artigo baseiam-se na Base de Dados SQL do Azure. A base de dados regista as operações de vendas e contém várias tabelas que armazenam revendedores, produtos e notas de vendas.

Uma tabela denominada **Revendedor** armazena um registo de cada revendedor e contém vários milhares de registos. A tabela **Revendedor** possui estas colunas:

- CódigoRevendedor (número inteiro)
- NomeRevendedor
- País/Região
- Estado/Província
- Cidade
- PostalCode

Existe também uma tabela denominada **Vendas**. Esta tabela armazena os registos das notas de vendas e tem uma relação de chave de referência com a tabela **Revendedor**, na coluna **CódigoRevendedor**.

### <a name="example-requirement"></a>Requisito de exemplo

Existe um requisito para desenvolver um relatório Perfil de Revendedor. O relatório deve ser concebido para apresentar informações de um único revendedor. Não é apropriado que o utilizador do relatório introduza um código de revendedor, pois raramente o memoriza.

## <a name="filter-large-sets-of-items"></a>Filtrar grandes conjuntos de itens

Vamos observar três exemplos para o ajudar a limitar os grandes conjuntos de itens disponíveis, como revendedores. São:

- [Filtrar por colunas relacionadas](#filter-by-related-columns)
- [Filtrar por coluna de agrupamento](#filter-by-a-grouping-column)
- [Filtrar por padrão de pesquisa](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtrar por colunas relacionadas

Neste exemplo, o utilizador do relatório interage com cinco parâmetros de relatório. O utilizador deve selecionar o país/região, o estado/província, a cidade e o código postal. Em seguida, um parâmetro final lista os revendedores que residem nessa localização geográfica.

![A imagem mostra cinco parâmetros de relatório: País/região, Estado/província, Cidade, Código Postal e Revendedor. Os primeiros quatro têm valores definidos e a lista Revendedor é filtrada para apenas quatro itens.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

Veja a seguir como pode desenvolver os parâmetros em cascata:

1. Crie os cinco parâmetros de relatório, ordenados pela sequência correta.
2. Crie o conjunto de dados **País/Região**, que obtém diferentes valores de país/região, com a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Crie o conjunto de dados **Estado/Província**, que obtém diferentes valores de estado/província para país/região selecionado, com a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Crie o conjunto de dados **Cidade**, que obtém diferentes valores de cidade para país/região e estado/província selecionados, com a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Continue este padrão para criar o conjunto de dados **CódigoPostal**.
6. Crie o conjunto de dados **Revendedor** para obter todos os revendedores referentes aos valores geográficos selecionados, com a seguinte instrução de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Para cada conjunto de dados, exceto o primeiro, mapeie os parâmetros de consulta para os parâmetros de relatório correspondentes.

> [!NOTE]
> Todos os parâmetros de consulta (com o símbolo @ como prefixo) apresentados nestes exemplos podem ser incorporados em instruções SELECT ou passados para os procedimentos armazenados.
>
> Normalmente, os procedimentos armazenados são uma melhor abordagem de conceção. Tal deve-se ao facto de os planos de consulta estarem armazenados em cache para uma execução mais rápida, além de permitirem criar uma lógica mais sofisticada, quando necessário. No entanto, não são atualmente suportados para origens de dados relacionais de gateway, o que significa SQL Server, Oracle e Teradata.
>
> Por último, deve sempre garantir que existem índices adequados para suportar uma obtenção de dados eficiente. Caso contrário, os parâmetros de relatório podem ser preenchidos lentamente e a base de dados pode ficar sobrecarregada. Para obter mais informações sobre a indexação do SQL Server, veja [SQL Server Index Architecture and Design Guide](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017) (Guia de Arquitetura e Design dos Índices do SQL Server).

### <a name="filter-by-a-grouping-column"></a>Filtrar por uma coluna de agrupamento

Neste exemplo, o utilizador do relatório interage com o parâmetro de relatório para selecionar a primeira letra do revendedor. Em seguida, um segundo parâmetro lista os revendedores quando o nome começa com a letra selecionada.

![A imagem mostra dois parâmetros de relatório: Grupo e Revendedor. O primeiro valor do parâmetro está definido como a letra A e a lista Revendedor é filtrada para os muitos itens que começam com essa letra.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

Veja a seguir como pode desenvolver os parâmetros em cascata:

1. Crie os parâmetros de relatório **GrupoRelatório** e **Revendedor**, ordenados pela sequência correta.
2. Crie o conjunto de dados **GrupoRelatório** para obter as primeiras letras utilizadas por todos os revendedores, com a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Crie o conjunto de dados **Revendedor** para obter todos os revendedores que começam com a letra selecionada, com a instrução de consulta que se segue:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Mapeie o parâmetro de consulta do conjunto de dados **Revendedor** para o parâmetro de relatório correspondente.

É mais eficiente adicionar uma coluna de agrupamento à tabela **Revendedor**. Quando indexada e se for persistente, proporcionará o melhor resultado. Para obter mais informações, veja [Specify Computed Columns in a Table](/sql/relational-databases/tables/specify-computed-columns-in-a-table) (Especificar Colunas Calculadas numa Tabela).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Esta técnica pode proporcionar ainda maior potencial. Considere o seguinte script que adiciona uma nova coluna de agrupamento para filtrar os revendedores por _grupos de letras predefinidos_. Também cria um índice para recuperar de forma eficaz os dados exigidos pelos parâmetros de relatório.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtrar por padrão de pesquisa

Neste exemplo, o utilizador do relatório interage com o parâmetro de relatório para introduzir um padrão de pesquisa. Em seguida, um segundo parâmetro lista os revendedores quando o nome contém um padrão.

![A imagem mostra dois parâmetros de relatório: Pesquisa e Revendedor. O primeiro valor do parâmetro está definido como o texto “vermelho” e a lista Revendedor é filtrada para diversos itens que contêm esse texto.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

Veja a seguir como pode desenvolver os parâmetros em cascata:

1. Crie os parâmetros de relatório **Pesquisa** e **Revendedor**, ordenados pela sequência correta.
2. Crie o conjunto de dados **Revendedor** para obter todos os revendedores que contêm o texto selecionado, com a seguinte instrução de consulta:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Mapeie o parâmetro de consulta do conjunto de dados **Revendedor** para o parâmetro de relatório correspondente.

> [!TIP]
> Pode melhorar este design para proporcionar mais controlo aos utilizadores do relatório. Permite que os utilizadores definam os seus próprios valores de correspondência de padrão. Por exemplo, o valor da pesquisa “vermelho%” filtrará os revendedores com nomes que _começam_ com os caracteres “vermelho”.
>
> Para obter mais informações, veja [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character).

Veja a seguir como pode deixar que os utilizadores do relatório definam o seu próprio padrão.

```sql
WHERE
  [ResellerName] LIKE @Search
```

No entanto, muitos profissionais que não utilizam bases de dados desconhecem a utilização do caráter universal de percentagem (%). Em vez disso, estão familiarizados com o caráter de asterisco (*). Ao modificar a cláusula WHERE, pode deixá-los utilizar este caráter.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Apresentar itens relevantes

Neste cenário, pode utilizar dados de factos para limitar os valores disponíveis. Serão apresentados aos utilizadores do relatório itens onde a atividade foi registada.

Neste exemplo, o utilizador do relatório interage com três parâmetros de relatório. Os dois primeiros definem um intervalo de datas das notas de vendas. Em seguida, o terceiro parâmetro lista os revendedores onde as encomendas foram criadas durante esse período de tempo.

![A imagem mostra três parâmetros de relatório: Data de Início da Encomenda, Data de Fim da Encomenda e Revendedor. Os dois parâmetros de data são definidos para o mês de janeiro de 2020, e a lista Revendedores é filtrada para muitos itens que representam revendedores que fizeram encomendas durante este mês.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

Veja a seguir como pode desenvolver os parâmetros em cascata:

1. Crie os parâmetros de relatório **DataInícioEncomenda**, **DataFimEncomenda** e **Revendedor**, ordenados na sequência correta.
2. Criar o conjunto de dados **Revendedor** para obter todos os revendedores que criaram pedidos nesse período de datas, com a seguinte instrução de consulta:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Recomendações

Recomendamos que, sempre que possível, crie os relatórios com parâmetros em cascata. Porque:

- Proporciona experiências intuitivas e úteis aos utilizadores do relatório
- São eficientes, porque recuperam conjuntos de valores disponíveis menores

Confirme que otimiza as origens de dados ao:

- Utilizar procedimentos armazenados, sempre que possível
- Adicionar índices adequados para uma obtenção de dados eficiente
- Materializar os valores de coluna (e até linhas) para evitar dispendiosas avaliações de tempo de consulta

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Parâmetros de relatórios no Report Builder do Power BI](../paginated-reports/report-builder-parameters.md)
- [Add Cascading Parameters to a Report (Report Builder and SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs) (Adicionar Parâmetros em Cascata a um Relatório (Report Builder e SSRS))
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)
