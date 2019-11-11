---
title: 'DAX: Appropriate use of error functions (Utilização adequada de funções de erro)'
description: Documentação de orientação sobre quando utilizar as funções de erro DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: ae4e9081930b0f6934a557ba45afd99dd8dfc05d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875623"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Appropriate use of error functions (Utilização adequada de funções de erro)

Este artigo destina-se aos modeladores de dados que definem expressões de DAX.

## <a name="background"></a>Fundo

Ao escrever uma expressão DAX que possa gerar o erro de tempo de avaliação, pode considerar utilizar duas funções DAX úteis.

- A função [ISERROR](/dax/iserror-function-dax), que assume uma única expressão e devolverá TRUE se essa expressão resultar em erro.
- A função [IFERROR](/dax/iferror-function-dax), que assume duas expressões. Se a primeira expressão resultar em erro, será devolvido o valor da segunda expressão. Na verdade, é uma implementação mais otimizada do aninhamento da função ISERROR dentro de uma função [IF](/dax/if-function-dax).

Contudo, embora estas funções possam ser úteis e possam contribuir para escrever expressões de fácil compreensão, também podem degradar significativamente o desempenho dos cálculos. Essa degradação ocorre porque estas funções aumentam o número necessário de análises do motor de armazenamento.

Tenha em atenção que a maioria dos erros de tempo de avaliação deve-se a valores inesperados EM BRANCO ou nulos ou à conversão inválida do tipo de dados.

## <a name="recommendations"></a>Recomendações

É melhor evitar a utilização das funções ISERROR e IFERROR. Em vez disso, adote estratégias defensivas ao desenvolver o modelo e ao escrever expressões, que podem incluir o seguinte:

- **Garantir que são carregados dados de qualidade no modelo:** utilize as transformações do Power Query para remover ou substituir valores inválidos ou em falta e para definir tipos de dados corretos. Uma transformação do Power Query também pode ser utilizada para filtrar linhas quando ocorrem erros, como a conversão inválida dos dados.

    A qualidade dos dados também pode ser controlada ao definir a propriedade **Pode Ser Nulo** da coluna do modelo como Desativada, o que fará com que a atualização dos dados falhe, caso sejam encontrados valores EM BRANCO. Tenha em atenção que, se essa falha ocorrer, os dados carregados como resultado de uma atualização bem-sucedida manter-se-ão nas tabelas.
- **Utilizar a função IF:** a expressão lógica de teste da função IF pode ser utilizada para determinar se ocorrerá um resultado de erro. Tenha em atenção que, tal como as funções ISERROR e IFERROR, esta função pode resultar em análises adicionais do motor de armazenamento, mas provavelmente terá um melhor desempenho do que essas funções, já que não será necessário gerar erros.
- **Utilizar as funções de tolerância a erros:** algumas funções DAX vão testar e compensar as condições de erro. Estas funções permitem-lhe introduzir um resultado alternativo que será devolvido. A função [DIVIDIR](/dax/divide-function-dax) é um desses exemplos. Para uma orientação adicional em relação a esta função, leia o artigo [DAX: função DIVIDIR vs. operador dividir (/)](dax-divide-function-operator.md).

## <a name="example"></a>Exemplo

A seguinte expressão de medida testa se será gerado um erro. Devolverá EM BRANCO nesta instância (que é o caso quando não fornece à função IF uma expressão de valor se falso).
```dax
= IF(ISERROR([Profit] / [Sales]))
```
Esta próxima versão da expressão de medida foi melhorada com a função IFERROR em vez das funções IF e ISERROR.
```dax
= IFERROR([Profit] / [Sales], BLANK())
```
No entanto, esta versão final da expressão de medida alcança o mesmo resultado, mas de forma mais eficaz e elegante.
```dax
= DIVIDE([Profit], [Sales])
```