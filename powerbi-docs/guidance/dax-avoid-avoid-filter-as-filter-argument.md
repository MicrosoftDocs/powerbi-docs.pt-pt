---
title: 'DAX: Avoid using FILTER as a filter argument (Evitar utilizar FILTER como um argumento de filtro)'
description: Orientação sobre como utilizar a função FILTER como um argumento de filtro.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: abff4eafc741ea776180752147019cae3c744e2c
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90964992"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Avoid using FILTER as a filter argument (Evitar utilizar FILTER como um argumento de filtro)

Na qualidade de modelador de dados, é comum escrever expressões DAX que precisam de ser avaliadas num contexto de filtro modificado. Por exemplo, pode escrever uma definição de medida para calcular as vendas de "produtos com elevada margem de lucro". Vamos descrever este cálculo mais tarde neste artigo.

> [!NOTE]
> Este artigo é sobretudo relevante para cálculos de modelos que aplicam filtros nas tabelas de Importação.

As funções DAX [CALCULATE](/dax/calculate-function-dax) e [CALCULATETABLE](/dax/calculatetable-function-dax) são importantes e úteis. Permitem que escreva cálculos que removem ou adicionam filtros e que podem modificar caminhos de relação. Isto é conseguido ao transmitir argumentos de filtro, que tanto podem ser expressões booleanas, como expressões de tabela ou funções de filtro especiais. Neste artigo, vamos apenas abordar as expressões booleanas e as de tabela.

Considere a seguinte definição de medida, que calcula as vendas de produtos vermelhos ao utilizar uma expressão de tabela. Irá substituir os filtros que podem ser aplicados à tabela **Product** (Produto).

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

A função CALCULATE aceita uma expressão de tabela devolvida pela função DAX [FILTER](/dax/filter-function-dax), que avalia a respetiva expressão de filtro para cada linha da tabela **Product** (Produto). Obtém o resultado correto: o resultado de vendas dos produtos vermelhos. No entanto, podia ser alcançado muito mais eficazmente se fosse utilizada uma expressão booleana.

Esta é uma definição de medida melhorada, que utiliza uma expressão booleana em vez de uma expressão de tabela. A função DAX [KEEPFILTERS](/dax/keepfilters-function-dax) garante que qualquer filtro existente e aplicado à coluna **Cor** é preservado e não é substituído.

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

Recomendamos, sempre que possível, transmitir os argumentos de filtro como expressões booleanas. Isto deve-se ao facto de as tabelas de modelo de Importação serem arquivos de colunas dentro da memória. São explicitamente otimizadas para filtrar colunas eficientemente desta forma.

No entanto, as expressões booleanas têm restrições quando são utilizadas como argumentos de filtro. As expressões booleanas:

- Não podem comparar colunas
- Não podem fazer referência a uma medida
- Não podem utilizar funções CALCULATE aninhadas
- Não podem utilizar funções que analisam ou devolvem uma tabela

Isto significa que terá de utilizar expressões de tabela no caso de requisitos de filtros mais complexos.

Agora, considere uma definição de medida diferente.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

Um _produto com elevada margem de lucro_ define-se como um produto que tem um preço de lista duas vezes mais caro do que o custo padrão. Neste exemplo, a função FILTER tem de ser utilizada. Isto deve-se ao facto de a expressão de filtro ser demasiado complexa para uma expressão booleana.

Eis mais um exemplo. Desta vez, o requisito é ter de calcular as vendas, mas apenas os meses em que houve lucro.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

Neste exemplo, a função FILTER também tem de ser utilizada. Isto ocorre porque é necessário avaliar a medida **Profit** (Lucro) para eliminar os meses em que não houve lucro. Não é possível utilizar uma medida numa expressão booleana quando esta é utilizada como um argumento de filtro.

## <a name="recommendations"></a>Recomendações

Para obter o melhor desempenho, recomendamos que utilize, sempre que possível, expressões booleanas como argumentos de filtro.

Por conseguinte, a função FILTER deve ser utilizada apenas quando necessária. Pode utilizá-la para efetuar comparações de colunas complexas de filtragem. Estas comparações de coluna podem incluir:

- Medidas
- Outras colunas
- A utilização da função DAX [OR](/dax/or-function-dax) ou o operador lógico OR (||)

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- [Funções de filtro (DAX)](/dax/filter-function-dax)
- Percurso de aprendizagem: [Use DAX in Power BI Desktop](/learn/paths/dax-power-bi/) (Utilizar a DAX no Power BI Desktop)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)