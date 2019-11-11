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
ms.openlocfilehash: c96518bb8de7f323b51a7e1e3f34f9d9bf056c79
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875373"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: função DIVIDIR vs. operador dividir (/)

Este artigo destina-se aos modeladores de dados que definem expressões de DAX.

## <a name="background"></a>Fundo

Ao escrever uma expressão de DAX para dividir um numerador por um denominador, pode optar por utilizar a função [DIVIDIR](/dax/divide-function-dax) ou o operador dividir (/ – barra invertida).

Ao utilizar a função DIVIDIR, tem de passar as expressões de numerador e denominador. Opcionalmente, pode passar um valor que represente um resultado alternativo.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

A função DIVIDIR foi concebida para o processamento automático de casos de divisão por zero. Se não for passado um resultado alternativo e o denominador for zero ou EM BRANCO, a função irá devolver um resultado EM BRANCO. Se for passado um resultado alternativo, este será devolvido em vez de um resultado EM BRANCO.

A função DIVIDIR é conveniente porque evita que a sua expressão tenha de testar primeiro o valor do denominador. Esta função também está melhor otimizada para testar o valor do denominador do que a função [SE](/dax/if-function-dax). O ganho de desempenho é significativo, uma vez que a verificação da divisão por zero é dispendiosa. A utilização da função DIVIDIR também resulta numa expressão mais concisa e elegante.

## <a name="example"></a>Exemplo

A seguinte expressão de medida produz uma divisão segura, mas implica a utilização de quatro funções DAX.

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

Esta expressão de medida alcança o mesmo resultado, mas de forma mais eficaz e elegante.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Recomendações

Recomendamos que utilize a função DIVIDIR quando o denominador for uma expressão que _pode_ devolver zero ou um resultado EM BRANCO.

Se o denominador for um valor constante, recomendamos que utilize o operador dividir. Neste caso, o êxito da divisão estará garantido e a sua expressão irá ter um melhor desempenho, porque irá evitar testes desnecessários.

Deve ponderar se a função DIVIDIR deve devolver um valor alternativo. Para as medidas, normalmente é melhor que a função devolva um resultado EM BRANCO, uma vez que os elementos visuais de relatórios eliminam agrupamentos por predefinição quando os resumos estão EM BRANCO. Esta eliminação permite que o elemento visual se centre nos grupos em que existem dados. Quando for necessário, pode configurar o elemento visual para apresentar todos os grupos (que devolvem valores ou resultados EM BRANCO) no contexto de filtro ao ativar a opção "Mostrar Itens Sem Dados".
