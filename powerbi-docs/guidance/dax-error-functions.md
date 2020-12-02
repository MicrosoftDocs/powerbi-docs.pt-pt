---
title: 'DAX: Appropriate use of error functions (Utilização adequada de funções de erro)'
description: Documentação de orientação sobre quando utilizar as funções de erro DAX.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: fd071fad18580074ce42c990db7f048ce2ad8c2d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394043"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Appropriate use of error functions (Utilização adequada de funções de erro)

Como modelador de dados, ao escrever uma expressão DAX passível de originar um erro de tempo de avaliação, pode considerar a utilização de duas funções DAX úteis.

- A função [ISERROR](/dax/iserror-function-dax), que assume uma única expressão e devolve o valor TRUE se essa expressão resultar em erro.
- A função [IFERROR](/dax/iferror-function-dax), que assume duas expressões. Se a primeira expressão resultar em erro, será devolvido o valor da segunda expressão. Na verdade, é uma implementação mais otimizada do aninhamento da função ISERROR dentro de uma função [IF](/dax/if-function-dax).

Contudo, embora estas funções possam ser úteis e possam contribuir para escrever expressões de fácil compreensão, também podem degradar significativamente o desempenho dos cálculos. Essa degradação pode ocorrer, porque estas funções aumentam o número necessário de análises do motor de armazenamento.

A maioria dos erros de tempo de avaliação deve-se a valores inesperados EM BRANCO ou nulos ou à conversão inválida do tipo de dados.

## <a name="recommendations"></a>Recomendações

É melhor evitar a utilização das funções ISERROR e IFERROR. Em vez disso, adote estratégias defensivas ao desenvolver o modelo e ao escrever expressões, Essas estratégias incluem:

- **Garantir que são carregados dados de qualidade no modelo:** utilize as transformações do Power Query para remover ou substituir valores inválidos ou em falta e para definir tipos de dados corretos. Uma transformação do Power Query também pode ser utilizada para filtrar linhas quando ocorrem erros, como a conversão inválida dos dados.

    A qualidade dos dados também pode ser controlada ao definir a propriedade **Pode Ser Nulo** da coluna do modelo como Desativada, o que fará com que a atualização dos dados falhe, caso sejam encontrados valores EM BRANCO. Se essa falha ocorrer, os dados carregados como resultado de uma atualização bem-sucedida manter-se-ão nas tabelas.
- **Utilizar a função IF:** a expressão lógica de teste da função IF pode determinar a ocorrência de um resultado de erro. Tenha em atenção que, tal como as funções ISERROR e IFERROR, esta função pode resultar em análises adicionais do motor de armazenamento, mas provavelmente terá um melhor desempenho do que essas funções, já que não será necessário gerar erros.
- **Utilizar as funções de tolerância a erros:** algumas funções DAX vão testar e compensar as condições de erro. Estas funções permitem-lhe introduzir um resultado alternativo que será devolvido. A função [DIVIDIR](/dax/divide-function-dax) é um desses exemplos. Para uma orientação adicional em relação a esta função, leia o artigo [DAX: função DIVIDIR vs. operador dividir (/)](dax-divide-function-operator.md).

## <a name="example"></a>Exemplo

A seguinte expressão de medida testa se será gerado um erro. Devolverá EM BRANCO nesta instância (que é o caso quando não fornece à função IF uma expressão de valor se falso).

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

Esta próxima versão da expressão de medida foi melhorada com a função IFERROR em vez das funções IF e ISERROR.

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

No entanto, esta versão final da expressão de medida alcança o mesmo resultado, mas de forma mais eficaz e elegante.

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)

- Percurso de aprendizagem: [Utilizar a DAX no Power BI Desktop](/learn/paths/dax-power-bi/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)