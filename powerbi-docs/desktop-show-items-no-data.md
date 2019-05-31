---
title: Mostrar itens sem dados no Power BI
description: Saiba como é que o Power BI processa e apresenta itens sem dados
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/03/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: a687e42ef2963ce5e85bd1e0be72c2562afa5b6c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61370506"
---
# <a name="show-items-with-no-data-in-power-bi"></a>Mostrar itens sem dados no Power BI

O Power BI permite-lhe visualizar todos os tipos de dados de várias origens. Ao criar um elemento visual, o Power BI apenas mostra os dados relevantes para permitir gerir adequadamente a forma como os dados são apresentados e visualizados. O Power BI determina que dados são relevantes com base na configuração do elemento visual e no modelo de dados subjacente. Este artigo descreve o comportamento do Power BI ao determinar os dados relevantes, com exemplos que ilustram a forma como as determinações são feitas.

![Como ativar a funcionalidade Mostrar itens sem dados](media/desktop-show-items-no-data/show-items-no-data_02.png)

## <a name="determining-relevant-data"></a>Determinar os dados relevantes

Para começar a compreender a forma como o Power BI determina os dados cuja apresentação é relevante, consideremos uma tabela como um exemplo simples. Utilizando o modelo representado na secção de exemplos, disponível na parte final deste artigo, considere criar uma tabela com as definições abaixo:

**1. Grupos da mesma tabela:** *Product[Color] - Product[Size]*

|*Product[Color]*  |*Product[Size]*  |
|---------|---------|
|Azul     |Grande         |
|Azul     |Medium         |
|Azul     |Small         |
|Vermelho     |Grande         |

Neste exemplo, o Power BI apresenta as combinações de *[Color-Size]* que existem na tabela *[Product]* . 

Vejamos agora outra combinação:

**2. Grupos de tabelas diferentes, mas diretamente relacionadas, e uma medida:** *ProductStyle[Finish] - Product[Color] - Sum(Sales[Quantity])*

|*ProductStyle[Finish]*  |*Product[Color]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Brilhante     |Azul         |10         |
|Mate     |Azul         |15         |

Neste exemplo, o Power BI só mostra combinações que existem. Por exemplo, não apresentará (“Nenhum” + “Azul”) ou (“Mate” + “Vermelho”) porque estas combinações não existem no modelo. A condição que determina que combinações existem é o valor de *Sum(Sales[Quantity])* não estar em branco.

Vejamos um caso diferente: 

**3. Grupos de tabelas diferentes, mas diretamente relacionadas, e sem medida:** *ProductStyle[Finish] - Product[Color]*

|*ProductStyle[Finish]*  |*Product[Color]*  |
|---------|---------|
|Brilhante     |Azul         |
|Brilhante     |Vermelho         |
|Mate     |Azul         |

Uma vez que não há uma medida explícita e as duas tabelas estão diretamente relacionadas, o Power BI tenta injetar uma medida para limitar as combinações resultantes. Neste caso, o Power BI injeta a medida *CALCULATE(COUNTROWS('Product'))* , que não deve estar em branco, uma vez que *Product* é a tabela comum a ambas as tabelas.

Como tal, o Power BI apresenta as combinações que têm entradas na tabela Product, o que exclui as combinações de *("Nenhum" + "Azul")* e *("Mate" + "Vermelho”)* .

**4. Grupos de tabelas diferentes e não relacionadas**

O modelo de exemplo não tem esta combinação. Contudo, se existissem grupos de tabelas diferentes e não relacionadas, o Power BI não conseguiria relacionar as duas colunas. O resultado seria uma união de todos os valores de cada coluna. Nesse caso, o Power BI emite um erro do tipo *associação não limitada*, uma vez que o cálculo dessas uniões na base de dados é moroso e aquelas não disponibilizam muitas informações aos utilizadores. 

![Erro mostrado para uma associação não limitada](media/desktop-show-items-no-data/show-items-no-data_01.png)


## <a name="showing-items-with-no-data"></a>Mostrar itens sem dados

A secção anterior descreveu a forma como o Power BI determina que dados são relevantes para apresentar. No entanto, poderá haver situações em que *pretende* mostrar itens sem dados. 

A funcionalidade **Mostrar itens sem dados** permite-lhe fazer precisamente o que o nome diz - incluir linhas e colunas de dados que não contêm dados de medidas (valores de medidas em branco).

Para ativar a funcionalidade **Mostrar itens sem dados**, selecione um elemento visual e, em **Campos**, clique com o botão direito do rato no campo e selecione **Mostrar itens sem dados**, no menu que aparece, conforme mostrado na imagem seguinte:

![Como ativar a funcionalidade Mostrar itens sem dados](media/desktop-show-items-no-data/show-items-no-data_02.png)


A funcionalidade **Mostrar itens sem dados** *não* tem efeito nas circunstâncias abaixo:

* Não há medidas adicionadas ao elemento visual e as colunas de agrupamento são provenientes da mesma tabela
* Os grupos não são relacionados; o Power BI não executa consultas para elementos visuais que têm grupos não relacionados
* A medida não está relacionada com nenhum dos grupos; isto deve-se ao facto de que a medida nunca vai estar em branco apenas para algumas combinações de grupos.
* Existe um filtro de medida definido pelo utilizador que exclui medidas em branco, como, por exemplo: *SalesAmount > 0*

### <a name="how-show-items-with-no-data-works"></a>Como Mostrar itens sem dados funciona

Os casos de utilização mais interessantes de **Mostrar itens sem dados** são aqueles nos quais estão presentes medidas. Vejamos uma situação em que os grupos são provenientes da mesma tabela ou podem ser relacionados através de um caminho no modelo. Por exemplo, *ProductStyle* está diretamente relacionado com *Product* e indiretamente relacionado com *Sales*, *ProductStyle* e *ProductCategory* podem ser relacionados através da tabela *Product* e assim sucessivamente.

Vejamos dois exemplos interessantes e façamos a comparação quando **Mostrar itens sem dados** está desativado e ativado. 

**1. Agrupar colunas da mesma tabela:** *Product[Color] - Product[Size] - Sum(Sales[Quantity])*

Como aparece se a funcionalidade **Mostrar itens sem dados** estiver desativada:

|*Product[Color]*  |*Product[Size]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Azul     |Medium         |15         |
|Azul     |Small         |10         |

Como aparece se a funcionalidade **Mostrar itens sem dados** estiver ativada:

|*Product[Color]*  |*Product[Size]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Azul     |Grande         |         |
|Azul     |Medium         |15         |
|Azul     |Small         |10         |
|Vermelho     |Grande         |         |

Repare como as duas combinações novas apareceram quando a funcionalidade está ativada: *Azul - Grande* e *Vermelho - Grande*. Nenhuma das entradas tem *Quantity* correspondente na tabela *Sales*. No entanto, são apresentadas na tabela *Product*.

**2. Agrupar colunas de tabelas relacionadas:** *ProductStyle[Finish] - Product[Color] - Sum(Sales[Quantity])*

Como aparece se a funcionalidade **Mostrar itens sem dados** estiver desativada:

|*ProductStyle[Finish]*  |*Product[Color]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Brilhante     |Azul         |10         |
|Mate     |Azul         |15         |

Como aparece se a funcionalidade **Mostrar itens sem dados** estiver ativada:

|*ProductStyle[Finish]*  |*Product[Color]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Brilhante     |Azul         |10         |
|Brilhante     |Vermelho         |         |
|Mate     |Azul         |15         |
|Nenhum     |         |         |

Repare como *(Brilhante - Vermelho)* e *(Nenhum, em branco)* apareceram como combinações. Eis o motivo de isso ter acontecido:
* O Power BI considerou primeiro ProductStyle[Finish] e selecionou todos os valores a apresentar, o que resultou em Brilhante, Mate e Nenhum.
* Utilizando cada um destes valores, o Power BI selecionou todas as entradas de *Product[Color]* correspondentes. 
* Uma vez que *Nenhum* não corresponde a nenhum *Product[Color]* , este valor fica em branco

É importante ter em conta que o mecanismo de seleção dos valores para as colunas depende da ordem e pode ser encarado como uma operação de *externa à esquerda* entre tabelas. Se a ordem da coluna for alterada, os resultados também mudarão.

Vejamos um exemplo da alteração da ordem e como os resultados são afetados. É igual ao item **2** nesta secção, com a ordem alterada.

**Product[Color] - ProductStyle[Finish] - Sum(Sales[Quantity])**

Como aparece se a funcionalidade **Mostrar itens sem dados** estiver ativada:

|*Product[Color]* |*ProductStyle[Finish]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Azul     |Brilhante         |10         |
|Azul     |Mate         |15         |
|Vermelho     |Brilhante         |         |

Neste caso, repare como *ProductStyle[Finish]=None* não aparece na tabela. Isto deve-se ao facto de que, neste caso, o Power BI selecionou primeiro todos os valores de *Color* na tabela *Product*. Depois, para cada cor, selecionou os valores de *Finish* correspondentes que continham dados. Uma vez que *Nenhum* não aparece em nenhuma combinação de *Color*, não é selecionado.

## <a name="example-data-model"></a>Modelo de dados de exemplo

Esta secção mostra o modelo de dados de exemplo utilizado nos exemplos deste artigo.

**Modelo**: ![Relações no modelo de dados](media/desktop-show-items-no-data/show-items-no-data_03.png)


**Dados**:

|Product[ProductId]|    Product[ProductName]|   Product[Color]| Product[Size]|  Product[CategoryId]|    Product[StyleId]|
|---------|---------|---------|---------|---------|---------|
|1  |Prod1  |Azul   |Small  |1  |1 |
|2  |Prod2  |Azul   |Medium |2  |2 |
|3  |Prod3  |Vermelho    |Grande  |1  |1 |
|4  |Prod4  |Azul   |Grande  |2  |2 |


|ProductCategory[CategoryId]|   ProductCategory[CategoryName]|
|---------|---------|
|1  |Telefone   |
|2  |Câmara |
|3  |TV |


|ProductStyle[StyleId]| ProductStyle[Finish]|   ProductStyle[Polished]|
|---------|---------|---------|
|1  |Brilhante  |Sim |
|2  |Mate  |Não |
|3  |Nenhum   |Não |


|Sales[SaleId]| Sales[ProductId]|   Sales[Date]|    Sales[Quantity]|
|---------|---------|---------|---------|
|1  |1  |1/1/2012 0:00| 10 |
|2  |2  |1/1/2013 0:00| 15 |



## <a name="next-steps"></a>Próximos passos

Este artigo descreveu como ativar a funcionalidade **Mostrar itens sem dados** no Power BI. Poderá também estar interessado nos seguintes artigos: 

* [Membro predefinido em modelos multidimensionais no Power BI](desktop-default-member-multidimensional-models.md)
