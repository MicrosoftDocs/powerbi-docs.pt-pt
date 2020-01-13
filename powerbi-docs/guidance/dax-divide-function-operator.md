---
title: 'DAX: função DIVIDIR vs. operador dividir (/)'
description: Documentação de orientação sobre quando se deve utilizar a função DIVIDIR de DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 7eea15d4389afaac2ac69e2f26eaa38fe84e337b
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2019
ms.locfileid: "75304172"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: função DIVIDIR vs. operador dividir (/)

Como modelador de dados, quando escreve uma expressão de DAX para dividir um numerador por um denominador, pode optar por utilizar a função [DIVIDIR](/dax/divide-function-dax) ou o operador dividir (/ – barra invertida).

Ao utilizar a função DIVIDIR, tem de passar as expressões de numerador e denominador. Opcionalmente, pode transmitir um valor que represente um _resultado alternativo_.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

A função DIVIDIR foi concebida para o processamento automático de casos de divisão por zero. Se não for passado um resultado alternativo e o denominador for zero ou EM BRANCO, a função irá devolver um resultado EM BRANCO. Quando um resultado alternativo é transmitido, é devolvido em vez de um resultado EM BRANCO.

A função DIVIDIR é conveniente porque evita que a sua expressão tenha de testar primeiro o valor do denominador. Esta função também está melhor otimizada para testar o valor do denominador do que a função [SE](/dax/if-function-dax). O ganho de desempenho é significativo, uma vez que a verificação da divisão por zero é dispendiosa. A utilização da função DIVIDIR resulta numa expressão mais concisa e elegante.

## <a name="example"></a>Exemplo

A seguinte expressão de medida produz uma divisão segura, mas implica a utilização de quatro funções DAX.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Esta expressão de medida alcança o mesmo resultado, mas de forma mais eficaz e elegante.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Recomendações

Recomendamos que utilize a função DIVIDIR quando o denominador for uma expressão que _pode_ devolver zero ou um resultado EM BRANCO.

Se o denominador for um valor constante, recomendamos que utilize o operador dividir. Neste caso, o êxito da divisão estará garantido e a sua expressão irá ter um melhor desempenho, porque irá evitar testes desnecessários.

Pondere se a função DIVIDIR deve devolver um valor alternativo. Para as medidas, normalmente é melhor que a função devolva um resultado EM BRANCO, uma vez que os elementos visuais de relatórios eliminam agrupamentos, por predefinição, quando os resumos estão EM BRANCO. Tal permite que o elemento visual concentre a atenção nos grupos em que existem dados. Quando for necessário, pode configurar o elemento visual para apresentar todos os grupos (que devolvem valores ou resultados EM BRANCO) no contexto de filtro ao ativar a opção [Mostrar itens sem dados](../desktop-show-items-no-data.md).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
