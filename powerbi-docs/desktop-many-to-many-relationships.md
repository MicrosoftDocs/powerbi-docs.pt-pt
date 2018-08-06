---
title: Relações muitos para muitos no Power BI Desktop (Pré-visualização)
description: Utilizar relações muitos para muitos no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/31/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 40799bb2716b2f6e85405e76c2a301acef3509aa
ms.sourcegitcommit: 06f59902105c93700e71e913dff8453e221e4f82
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388761"
---
# <a name="many-to-many-relationships-in-power-bi-desktop-preview"></a>Relações muitos para muitos no Power BI Desktop (Pré-visualização)

Com a funcionalidade **Relação muitos para muitos** do **Power BI Desktop**, pode associar tabelas com uma cardinalidade de **Muitos para Muitos** e criar modelos de dados que contenham várias origens de dados de uma forma mais fácil e intuitiva. A funcionalidade **relação muitos para muitos** faz parte das capacidades de **modelos compostos** maiores do **Power BI Desktop**.

![funcionalidade muitos para muitos na caixa de diálogo Editar relação](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

A capacidade **relações muitos para muitos** no **Power BI Desktop** faz parte de uma coleção de três funcionalidades relacionadas:

* **Modelos compostos** – permite que um relatório tenha várias ligações de dados, incluindo ligações DirectQuery ou de importação, em qualquer combinação.
* **Relações muitos para muitos** – com os **modelos compostos**, pode estabelecer **relações muitos para muitos** entre tabelas, ao remover requisitos de valores exclusivos nas tabelas e ao remover soluções alternativas anteriores, como a introdução de novas tabelas apenas para estabelecer relações. 
* **Modo de armazenamento** – agora pode especificar que elementos visuais necessitam de uma consulta às origens de dados de back-end e aqueles que não o exigem serão importados mesmo se se basearem no DirectQuery, o que melhora o desempenho e reduz a carga de back-end. Anteriormente, mesmo os elementos visuais simples como as consultas iniciadas pelas segmentações eram enviadas para as origens de back-end. 

Os três recursos relacionados dos **modelos compostos** desta coleção são descritos em artigos separados:

* Os **modelos compostos** são descritos detalhadamente no artigo [Modelos compostos no Power BI Desktop (Pré-visualização)](desktop-composite-models.md).
* As **relações muitos para muitos** são descritas neste artigo.
* O **modo de armazenamento** é descrito no seu próprio artigo: [Modo de armazenamento no Power BI Desktop (Pré-visualização)](desktop-storage-mode.md).

## <a name="enabling-the-many-to-many-relationships-preview-feature"></a>Ativar a funcionalidade de pré-visualização de relações muitos para muitos

A funcionalidade **relações muitos para muitos** faz parte das capacidades dos **modelos compostos** e está em Pré-visualização. Deve ser ativada no **Power BI Desktop**. Para ativar os **modelos compostos**, selecione **Ficheiro > Opções e Definições > Opções > Funcionalidades de Pré-visualização** e, em seguida, selecione a caixa de verificação **modelos compostos**.

![ativar as funcionalidades de pré-visualização](media/desktop-composite-models/composite-models_02.png)

Terá de reiniciar o **Power BI Desktop** para que a funcionalidade seja ativada.

![reinício necessário para que as alterações entrem em vigor](media/desktop-composite-models/composite-models_03.png)


## <a name="what-many-to-many-relationships-solves"></a>O que solucionam as relações muitos para muitos

Antes da disponibilidade das **relações muitos para muitos**, quando se definia uma relação entre duas tabelas no Power BI, pelo menos, uma das colunas envolvidas na relação tinha de conter valores exclusivos. No entanto, em muitas circunstâncias, nenhuma coluna na tabela continha valores exclusivos. 

Por exemplo, duas tabelas podem ter uma coluna que contenha o *País*, mas os valores do *País* não serem exclusivos em nenhuma das tabelas. Para associar essas tabelas, era necessário criar uma solução alternativa como a que introduzia tabelas adicionais no modelo que continha os valores exclusivos necessários. A funcionalidade **relações muitos para muitos** fornece uma abordagem alternativa, que permite que essas tabelas sejam associadas diretamente, através de uma relação com uma cardinalidade de **Muitos para muitos**.  

## <a name="using-many-to-many-relationships"></a>Utilizar relações muitos para muitos

Ao definir uma relação entre duas tabelas no Power BI, tem de definir a cardinalidade da relação. Por exemplo, a relação entre *Vendas por Produto* e *Produto* (através da utilização de colunas *Vendas por Produto[Código do Produto]* e *Produto[Código do Produto]*) seria definida como **Muitos para 1**, dado que existem muitas vendas para cada produto e a coluna na tabela *Produto* *(Código do Produto)* é exclusiva. Ao definir a cardinalidade de uma relação como **Muitos para 1**, **1 para Muitos** ou **1-1**, o Power BI executa a validação para garantir que a cardinalidade selecionada corresponde aos dados reais.

Por exemplo, vejamos o modelo simples na imagem seguinte.

![vista da relação](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Em seguida, imagine que a tabela *Produto* continha apenas duas linhas.

![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imagine também que a tabela *Vendas* tem apenas quatro linhas, que inclui *Vendas* de um produto **C** que não existe na tabela *Produto* (devido a um erro de integridade referencial).

![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Um elemento visual que apresentasse *Nome do Produto* e *Preço* (da tabela *Produto*), juntamente com o total de *Qtd* para cada produto (da tabela *Vendas por Produto*) seria apresentado como na seguinte imagem: 

![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Como pode ver na imagem anterior, há uma linha no elemento visual com um *Nome do Produto* em branco, associada às vendas do produto *C*. Esta linha em branco representa o seguinte:

* Todas as linhas na tabela *Vendas por Produto* para as quais não há nenhuma linha correspondente na tabela *Produto* – existe um problema de integridade referencial, tal como podemos ver no produto *C* neste exemplo.

* Todas as linhas da tabela *Vendas por Produto* para a qual a coluna de chave de referência tem valor Nulo. 

Por esses motivos, em ambos os casos a linha em branco representa as vendas em que o *Nome do Produto* e o *Preço* são desconhecidos.

No entanto, por vezes acontece que as tabelas são unidas por duas colunas, mas nenhuma das colunas é exclusiva. Por exemplo, considere as duas tabelas seguintes:

* A tabela *Vendas* contém os dados de vendas por *Estado*, cada linha com o valor das vendas do tipo de venda nesse estado (incluindo os estados CA, WA e TX) 

    ![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* A tabela *Dados por Cidade* contém os dados por cidades, incluindo a população e o estado (incluindo os estados CA, WA e Nova Iorque)

    ![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Embora haja uma coluna para *Estado* em ambas as tabelas e, é razoável pretender comunicar as *Vendas* totais por *Estado*, juntamente com a população total de cada estado, existe um problema: a coluna *Estado* não é exclusiva em nenhuma das tabelas. 

## <a name="the-prior-workaround"></a>Solução alternativa anterior

Nas versões do **Power BI Desktop** anteriores à versão de julho de 2018, não era possível criar uma relação diretamente entre estas tabelas. Uma solução alternativa comum para esse problema era fazer o seguinte:

* Criar uma terceira tabela com apenas os IDs exclusivos de *Estado*. Esta poderia ser uma tabela calculada (definida com o DAX) ou uma tabela definida com uma consulta definida no **Editor de Consultas**, que poderia conter os IDs exclusivos retirados de uma das tabelas ou do conjunto completo da junção.

* Relacionar as duas tabelas originais com essa nova tabela, através de relações **Muitos para 1*.

Esta tabela alternativa poderia ficar visível ou ser ocultada de modo a não aparecer na lista de campos. No último caso, as relações**Muitos para 1** normalmente seriam definidas para filtrar em ambas as direções, de modo que o campo *Estado* de qualquer tabela poderia ser utilizado, com subsequente propagação de filtragem cruzada para a outra tabela. Essa abordagem de solução alternativa é ilustrada na imagem seguinte da **Vista da relação**.

![vista da relação](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Um elemento visual a mostrar *Estado* (da tabela *Dados por Cidade*), juntamente com a *População* total e as *Vendas* totais seria apresentado da seguinte forma.

![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

Tenha em atenção que devido à utilização da tabela *Dados por Cidade* nesta solução alternativa, apenas os *Estados* na tabela são listados (assim, TX é excluído). Além disso, ao contrário do que acontece nas relações **Muitos para 1**, enquanto a linha total inclui todas as *Vendas* (incluindo as do TX), os detalhes não incluem uma linha em branco a abranger as linhas sem correspondência. Da mesma forma, não haveria nenhuma linha em branco a abranger as *Vendas* para as quais há um valor nulo em *Estado*.

Se a *Cidade* também fosse adicionada a esse elemento visual, sempre que a população por *Cidade* fosse conhecida, as *Vendas* mostradas por *Cidade* repetiriam simplesmente as *Vendas* do *Estado* correspondente (tal como normalmente acontece quando se faz o agrupamento numa coluna que não está relacionada com nenhuma medida de agregação), conforme mostrado na imagem seguinte.

![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Se a nova tabela *Vendas* fosse definida como a junção de todos os *Estados* nesta solução alternativa e ficasse visível na lista de campos, o mesmo elemento visual que mostra *Estado* (na nova tabela), juntamente com a *População* total e as *Vendas* totais, seria apresentado da seguinte forma.

![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Nesse caso e conforme mostrado no elemento visual, seriam incluídos *TX* (com as *Vendas*, mas população desconhecida) e *Nova Iorque* (com população conhecida, mas sem *Vendas*). 

Como pode ver, esta solução alternativa não era a ideal e acarretava muitos problemas. Com a criação da **relação muitos para muitos**, estes problemas foram resolvidos, conforme descrito na secção seguinte.

## <a name="using-many-to-many-relationships-instead-of-the-workaround"></a>Utilizar relações muitos para muitos, em vez da solução alternativa

Nas versões do **Power BI Desktop** posteriores a julho de 2018, pode relacionar diretamente as tabelas descritas na secção anterior, sem a necessidade de recorrer a tais soluções alternativas. Agora, é possível definir a cardinalidade de uma relação como **Muitos para Muitos**, o que indica que nenhuma das tabelas contém valores exclusivos. Para tais relações, pode ainda controlar que tabela filtra a outra tabela ou pode ter um filtro bidirecional em que ambas as tabelas se filtram mutuamente.  

> [!NOTE]
> A capacidade de criar relações **Muitos para Muitos** está em Pré-visualização e enquanto tal, não é possível publicar modelos com relações **Muitos para Muitos** no serviço Power BI. 

No **Power BI Desktop**, a cardinalidade predefinida é **Muitos para Muitos** quando se determina que nenhuma destas tabelas contém valores exclusivos para as colunas na relação. Nesses casos, é apresentado um aviso para confirmar que pretende essa definição de relação, em vez de obter o efeito não intencional de um problema de dados. 

Por exemplo, ao criar uma relação diretamente entre *Dados por Cidade* e *Vendas*, onde os Filtros devem fluir de *Dados por Cidade* para *Vendas*, a caixa de diálogo de relação será apresentada como na imagem seguinte.

![caixa de diálogo Editar relação](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

A **Vista de Relações** resultante iria conter a relação direta **Muitos para muitos** entre as duas tabelas. O aspeto na lista **Campos** e o comportamento subsequente quando os elementos visuais são criados são iguais a empregar a solução alternativa descrita na secção anterior, onde a tabela extra (com os diferentes *Estados*) não fica visível. Por exemplo, tal como na seção anterior, que descreve a solução alternativa, um elemento visual que mostre os *Estados* juntamente com a população total e as vendas totais seria apresentado da seguinte forma.

![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Por isso, as principais diferenças entre as relações **Muitos para Muitos** e as relações **Muitos para 1** mais habituais são as seguintes.

* Os valores mostrados não incluem uma representação das linhas em branco para as linhas sem correspondência na outra tabela, nem das linhas em que a coluna utilizada na relação na outra tabela têm valor nulo.
* Não é possível utilizar a função *RELATED()* (porque mais do que uma linha pode estar relacionada)
* A utilização da função *ALL()* numa tabela não removerá os filtros aplicados a outras tabelas relacionadas com a mesma, através de uma relação **Muitos para Muitos**. Por exemplo, uma medida definida como a seguinte no exemplo anterior não removeria os filtros das colunas na tabela *Dados por Cidade* relacionada:

    ![exemplo de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Como tal, um elemento visual que mostre *Estado*, *Vendas* e *Vendas totais* resultaria no seguinte:

    ![elemento visual da tabela](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Por este motivo, deve ter cuidado para garantir que esses cálculos com *ALL(\<Table >)*, como a *% do total geral*, devolvem os resultados pretendidos. 


## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações nesta versão das **relações muitos para muitos** e dos **modelos compostos**.

As seguintes origens multidimensionais não podem ser utilizadas com **modelos compostos**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI

Ao ligar-se a essas origens multidimensionais através do DirectQuery, também não poderá ligar-se à outra origem do DirectQuery nem combinar com dados importados.

As limitações existentes da utilização do DirectQuery ainda se aplicam ao utilizar as **relações muitos para muitos**. Muitas destas limitações são agora por tabela, de acordo com o **modo de armazenamento** da tabela. Por exemplo, uma coluna calculada numa tabela importada pode referir-se a outras tabelas, mas uma coluna calculada numa tabela DirectQuery está restrita a referir-se apenas às colunas na mesma tabela. As outras limitações aplicar-se-ão ao modelo como um todo se qualquer uma das tabelas no modelo for DirectQuery. Por exemplo, as funcionalidades **QuickInsights** e **Perguntas e Respostas** não estarão disponíveis nos modelos se qualquer uma das tabelas dentro dos mesmos tiverem um **modo de armazenamento** do DirectQuery. 

## <a name="next-steps"></a>Próximos passos

Os artigos seguintes descrevem de forma mais detalhada os modelos compostos e o DirectQuery.

* [Modelos Compostos no Power BI Desktop (Pré-visualização)](desktop-composite-models.md)
* [Modo de Armazenamento no Power BI Desktop (Pré-visualização)](desktop-storage-mode.md)

Artigos do DirectQuery:

* [Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery no Power BI](desktop-directquery-data-sources.md)

