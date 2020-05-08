---
title: Relações muitos-para-muitos no Power BI Desktop
description: Utilizar relações com uma cardinalidade de muitos-para-muitos no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7452879e47cd4b058fcdb3e08f0ded35a85da1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761071"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Aplicar relações muitos para muitos no Power BI Desktop

Com as *relações com uma cardinalidade de muitos para muitos* no Power BI Desktop, pode associar tabelas com uma cardinalidade de *muitos para muitos*. Pode criar modelos de dados que contêm duas ou mais origens de dados mais facilmente e de forma intuitiva. As *relações com uma cardinalidade de muitos para muitos* fazem parte das capacidades de *modelos compostos* maiores do Power BI Desktop.

![Relação muitos para muitos no painel "Editar relação", Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Uma *relação com uma cardinalidade de muitos para muitos* no Power BI Desktop é composta por uma de três funcionalidades relacionadas:

* **Modelos compostos**: Um *modelo composto* permite que um relatório tenha duas ou mais ligações de dados, incluindo ligações DirectQuery ou de Importação, em qualquer combinação. Para obter mais informações, veja [Utilizar modelos compostos no Power BI Desktop](desktop-composite-models.md).

* **Relações com uma cardinalidade de muitos-para-muitos**: com os modelos compostos, pode estabelecer *relações com uma cardinalidade de muitos para muitos* entre tabelas. Esta abordagem remove os requisitos de valores exclusivos nas tabelas. Esta operação também remove soluções anteriores como, por exemplo, apresentar novas tabelas apenas para estabelecer relações. A funcionalidade é descrita mais detalhadamente neste artigo.

* **Modo de armazenamento**: agora pode especificar que elementos visuais precisam de uma consulta às origens de dados de back-end. Os elementos visuais que não precisam de uma consulta são importados, mesmo que sejam baseados no DirectQuery. Esta funcionalidade ajuda a melhorar o desempenho e a reduzir a carga de back-end. Anteriormente, até os elementos visuais simples, como as segmentações de dados, iniciavam consultas que eram enviadas para origens de back-end. Para obter mais informações, veja [Modo de armazenamento no Power BI Desktop](desktop-storage-mode.md).

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>O que uma relação com uma cardinalidade de muitos para muitos resolve

Antes de as *relações com uma cardinalidade de muitos para muitos* serem disponibilizadas, a relação entre duas tabelas era definida no Power BI. Pelo menos uma das colunas da tabela envolvidas na relação tinha de conter valores exclusivos. Muitas vezes, no entanto, nenhuma coluna continha valores exclusivos.

Por exemplo, duas tabelas podiam ter uma coluna identificada como País. No entanto, os valores do País não eram exclusivos em nenhuma tabela. Para associar essas tabelas, era preciso criar uma solução alternativa. Uma solução alternativa poderia ser a introdução de tabelas adicionais com os valores exclusivos necessários. Com as *relações com uma cardinalidade de muitos para muitos*, pode associar essas tabelas diretamente se utilizar uma relação com uma cardinalidade de *muitos para muitos*.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Utilizar relações com uma cardinalidade de muitos para muitos

Ao definir uma relação entre duas tabelas no Power BI, tem de definir a cardinalidade da relação. Por exemplo, a relação entre Vendas por Produto e Produto&mdash;através da utilização de colunas Vendas por Produto[Código do Produto] e Produto[Código do Produto]&mdash;seria definida como *Muitos para 1*. Definimos a relação dessa forma porque existem muitas vendas para cada produto e a coluna na tabela Produto (Código do Produto) é exclusiva. Quando define uma cardinalidade da relação como *Muitos para 1*, *1 para Muitos* ou *1 para 1*, o Power BI executa a validação para que a cardinalidade selecionada corresponda aos dados reais.

Por exemplo, vejamos o modelo simples nesta imagem:

![Tabela ProductSales e Product, vista Relação, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Agora, imagine que a tabela **Produto** apresenta apenas duas linhas, conforme mostrado:

![Elemento visual da tabela Product com duas linhas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imagine também que a tabela Vendas tem apenas quatro linhas, incluindo uma linha para um produto C. Devido a um erro de integridade referencial, a linha de produto C não existe na tabela **Product**.

![Elemento visual da tabela Vendas com quatro linhas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

O **ProductName** e o **Price** (da tabela **Product**), juntamente com o total de **Qty** para cada produto (da tabela ProductSales) seriam apresentados da seguinte forma:

![Elemento visual a apresentar o nome do produto, o preço e a quantidade, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Como pode ver na imagem anterior, uma linha **ProductName** em branco está associada às vendas do produto C. Esta linha em branco representa o seguinte:

* Todas as linhas na tabela **Vendas por Produto** para as quais não existe qualquer linha correspondente na tabela **Produto**. Existe um problema de integridade referencial, como podemos ver para o produto C neste exemplo.

* Todas as linhas da tabela **Vendas por Produto** para a qual a coluna de chave de referência tem valor nulo.

Por esses motivos, a linha em branco em ambos os casos representa as vendas em que o **Nome do Produto** e o **Preço** são desconhecidos.

Por vezes, as tabelas são associadas por duas colunas, mas nenhuma das colunas é exclusiva. Por exemplo, considere estas duas tabelas:

* A tabela **Vendas** apresenta dados de vendas por **Estado** e cada linha contém o valor de vendas para o tipo de venda nesse estado. Os estados incluem CA, WA e TX.

    ![Tabela Vendas a apresentar as vendas por estado, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* A tabela **CityData** apresenta dados de cidades, incluindo a população e o estado (tal como os estados CA, WA e Nova Iorque).

    ![Tabela Sales a apresentar a cidade, o estado e a população, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Uma coluna para **State** está agora em ambas as tabelas. É razoável querer reportar o total de vendas por estado e a população total de cada estado. No entanto, existe um problema: a coluna **State** não é exclusiva em nenhuma tabela.

## <a name="the-previous-workaround"></a>A solução anterior

Antes do lançamento de julho de 2018 do Power BI Desktop, não podia criar uma relação direta entre estas tabelas. Uma solução comum consistia em:

* Criar uma terceira tabela que contivesse apenas os IDs de Estado exclusivos. A tabela podia ser qualquer ou todas as opções seguintes:
  * Uma tabela calculada (definida com a linguagem DAX [Data Analysis Expressions]).
  * Uma tabela com base numa consulta definida no Editor de Consultas, que podia apresentar os IDs exclusivos desenhados a partir de uma das tabelas.
  * O conjunto completo combinado.

* Em seguida, relacionar as duas tabelas originais com essa nova tabela, através de relações *Muitos para 1* comuns.

Pode deixar a tabela da solução alternativa visível ou pode ocultá-la, de modo a que não apareça na lista **Campos**. Se ocultasse a tabela, as relações *Muitos para 1* seriam normalmente definidas para filtrar em ambas as direções e podia utilizar o campo Estado a partir de qualquer tabela. A filtragem cruzada posterior seria propagada para a outra tabela. Essa abordagem é mostrada na imagem seguinte:

![Tabela State ocultada, vista Relação, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Um elemento visual a mostrar **Estado** (da tabela **Dados por Cidade**), juntamente com a **População** total e as **Vendas** totais seria apresentado da seguinte forma:

![Tabelas State, Population e Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Devido à utilização do estado da tabela **CityData** nesta solução alternativa, apenas os estados nessa tabela são listados e, por isso, TX é excluído. Além disso, ao contrário das relações *Muitos para 1*, apesar de a linha total incluir todas as **Vendas** (incluindo as de TX), os detalhes não incluem uma linha em branco a abranger as linhas sem correspondência. Da mesma forma, nenhuma linha em branco abrangeria as **Sales** para as quais há um valor nulo em **State**.

Suponha que também adiciona a Cidade a esse elemento visual. Embora a população por Cidade seja conhecida, as **Sales** apresentadas para Cidade simplesmente repetem as **Sales** correspondentes ao **State**. Este cenário ocorre normalmente quando o agrupamento de colunas não está relacionado com alguma medida agregada, como mostrado aqui:

![População e vendas por estado e cidade, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Digamos que define a nova tabela Vendas como a combinação de todos os Estados aqui e vamos torná-la visível na lista **Fields**. O mesmo elemento visual apresentaria **State** (na nova tabela), a **Population** total e as **Sales** totais:

![Elemento visual de estado, população e vendas, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Como pode ver, TX&mdash;com dados de **Sales**, mas dados de *Population* desconhecidos&mdash;e Nova Iorque&mdash;com dados de **Population** conhecidos, mas sem dados de **Sales**&mdash;seria incluído. Esta solução não é ideal e tem muitos problemas. Para relações com uma cardinalidade de muitos para muitos, os problemas resultantes foram resolvidos, conforme descrito na secção seguinte.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Utilizar uma relação com uma cardinalidade de muitos para muitos em vez da solução alternativa

Com a versão de julho de 2018 do Power BI Desktop, pode relacionar diretamente tabelas, como aquelas que descrevemos anteriormente, sem ter de recorrer a soluções semelhantes. Já é possível definir a cardinalidade da relação para *muitos para muitos*. Esta definição indica que nenhuma das tabelas contém valores exclusivos. Para tais relações, ainda pode controlar que tabela filtra a outra tabela. Em alternativa, pode aplicar a filtragem bidirecional, em que cada tabela filtra a outra.

No Power BI Desktop, a cardinalidade predefinida é *muitos para muitos* quando se determina que nenhuma das tabelas contém valores exclusivos para as colunas na relação. Nestes casos, uma mensagem de aviso confirma que pretende definir uma relação, e a alteração não é o efeito indesejado de um problema de dados.

Por exemplo, quando cria uma relação diretamente entre CityData e Sales&mdash;em que os filtros devem fluir de CityData para Sales&mdash;, o Power BI Desktop apresenta a caixa de diálogo **Editar relação**:

![Caixa de diálogo Editar relação, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

A vista **Relação** resultante iria apresentar a relação direta muitos para muitos entre as duas tabelas. O aspeto das tabelas na lista **Fields** e o comportamento posterior quando os elementos visuais são criados são semelhantes a quando aplicamos a solução alternativa. Na solução alternativa, a tabela adicional que apresenta os dados de Estado distintos não fica visível. Conforme descrito anteriormente, um elemento visual que mostra dados de **State**, **Population** e **Sales** seria apresentado:

![Tabelas State, Population e Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

As principais diferenças entre as *relações com uma cardinalidade de muitos-para-muitos* e as relações *muitos-para-um* mais habituais são as seguintes:

* Os valores mostrados não incluem uma linha em branco que representa linhas sem correspondência na outra tabela. De igual modo, os valores não representam linhas em que a coluna utilizada na relação na outra tabela é nula.
* Não é possível utilizar a função `RELATED()`, porque mais do que uma linha pode estar relacionada.
* Utilizar a função `ALL()` numa tabela não remove os filtros que são aplicados a outras tabelas relacionadas através de uma relação muitos para muitos. No exemplo anterior, uma medida que é definida conforme mostrado aqui não removeria filtros em colunas na tabela Dados por Cidade relacionada:

    ![Exemplo de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Como tal, um elemento visual que mostre dados de **State**, **Sales** e **Sales total** resultaria neste gráfico:

    ![Elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Com as diferenças anteriores em mente, confirme que os cálculos que utilizam `ALL(<Table>)`, tal como *% of grand total*, estão a devolver os resultados pretendidos.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações nesta versão das *relações com uma cardinalidade de muitos-para-muitos* e dos modelos compostos.

As seguintes origens do Live Connect (multidimensionais) não podem ser utilizadas com modelos compostos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI
* Azure Analysis Services

Quando se liga a estas origens multidimensionais através do DirectQuery, não se pode ligar a outra origem do DirectQuery nem combiná-las com dados importados.

As limitações existentes da utilização do DirectQuery ainda se aplicam ao utilizar as *relações com uma cardinalidade de muitos-para-muitos*. Muitas limitações são agora por tabela, de acordo com o modo de armazenamento da tabela. Por exemplo, uma coluna calculada numa tabela importada pode referir-se a outras tabelas, mas uma coluna calculada numa tabela DirectQuery ainda pode referir-se apenas às colunas na mesma tabela. As outras limitações aplicam-se ao modelo como um todo se qualquer uma das tabelas no modelo for DirectQuery. Por exemplo, as funcionalidades QuickInsights e Perguntas e Respostas não estarão disponíveis nos modelos se qualquer uma das tabelas dentro dos mesmos tiver um modo de armazenamento do DirectQuery.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre os modelos compostos e o DirectQuery, veja os artigos seguintes:
* [Utilizar modelos compostos no Power BI Desktop](desktop-composite-models.md)
* [Modo de armazenamento no Power BI Desktop](desktop-storage-mode.md)
* [Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados do Power BI](power-bi-data-sources.md)
