---
title: 'DAX: utilizar variáveis para melhorar fórmulas'
description: Orientação sobre a utilização de variáveis em expressões DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: f352cbbd7c42aa54ae876e73c0ed821eccda59c8
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700714"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: utilizar variáveis para melhorar fórmulas

Como modelador de dados, pode ser desafiante escrever e depurar alguns cálculos DAX. É comum que os requisitos de cálculo complexos envolvam escrever expressões complexas ou compostas. As expressões compostas podem envolver a utilização de muitas funções aninhadas e, possivelmente, a reutilização da lógica de expressão.

Utilizar variáveis nas fórmulas DAX ajuda a escrever cálculos complexos e eficientes. As variáveis podem:

- [Melhorar o desempenho](#improve-performance)
- [Melhorar a legibilidade](#improve-readability)
- [Simplificar a depuração](#simplify-debugging)
- [Reduzir a complexidade](#reduce-complexity)

Neste artigo, iremos demonstrar as três primeiras vantagens ao utilizar uma medida de exemplo para o crescimento de vendas de ano a ano (YoY). (A fórmula de crescimento de vendas de ano a ano é: vendas do período _menos vendas para o mesmo período do ano passado, _dividido por_ vendas para o mesmo período do ano passado.)

Vamos começar com a seguinte definição de medida.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

A medida produz o resultado correto, mas agora vamos ver como pode ser melhorado.

## <a name="improve-performance"></a>Melhorar o desempenho

Tenha em atenção que a fórmula repete a expressão que calcula "mesmo período do ano passado". Esta fórmula é ineficiente, pois exige que o Power BI avalie a mesma expressão duas vezes. A definição da medida pode tornar-se mais eficiente com uma variável.

A seguinte definição de medida representa uma melhoria. Utiliza uma expressão para atribuir o resultado "mesmo período do ano passado" a uma variável chamada **SalesPriorYear**. A variável é utilizada duas vezes na expressão RETURN.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

A medida continua a produzir o resultado correto e fá-lo em cerca de metade do tempo de consulta.

## <a name="improve-readability"></a>Melhorar a legibilidade

Na definição de medida anterior, veja como a escolha do nome da variável torna a expressão RETURN mais simples de compreender. A expressão é curta e descritiva.

## <a name="simplify-debugging"></a>Simplificar a depuração

As variáveis também podem ajudar a depurar uma fórmula. Para testar uma expressão atribuída a uma variável, reescreva temporariamente a expressão RETURN para gerar a variável.

A seguinte definição de medida devolve apenas a variável **SalesPriorYear**. Veja como comenta a expressão RETURN pretendida. Esta técnica permite reverter facilmente quando a depuração for concluída.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Reduzir a complexidade

Em versões anteriores do DAX, as variáveis ainda não eram suportadas. As expressões complexas que apresentavam novos contextos de filtro eram necessárias para utilizar as funções [EARLIER](/dax/earlier-function-dax) ou [EARLIEST](/dax/earliest-function-dax) do DAX para fazer referência a contextos de filtro externos. Infelizmente, os modeladores de dados consideram estas funções difíceis de compreender e utilizar.

As variáveis são sempre avaliadas fora dos filtros que a expressão RETURN aplica. Por este motivo, quando utiliza uma variável num contexto de filtro modificado, obtém o mesmo resultado que a função EARLIEST. A utilização das funções EARLIER ou EARLIEST pode ser evitada. Significa que agora pode escrever fórmulas que são menos complexas e mais fáceis de compreender.

Considere a seguinte definição de coluna calculada adicionada à tabela **Subcategory**. Esta avalia uma classificação de cada subcategoria de produto com base nos valores da coluna **Subcategory Sales**.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

A função EARLIER é utilizada para fazer referência ao valor da coluna **Subcategory Sales**_no contexto de linha atual_.

A definição de coluna calculada pode ser melhorada ao utilizar uma variável em vez da função EARLIER. A variável **CurrentSubcategorySales** armazena o valor da coluna **Subcategory Sales**_no contexto de linha atual_ e a expressão RETURN utiliza-a num contexto de filtro modificado.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- Função [VAR](/dax/var-dax) (DAX)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
