---
title: 'DAX: Utilizar SELECTEDVALUE em vez de VALUES'
description: Documentação de orientação sobre quando utilizar as funções SELECTEDVALUE.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/20/2019
ms.openlocfilehash: 1925333b935209484855dff444542a20040a0f6a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394227"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX: Utilizar SELECTEDVALUE em vez de VALUES

Enquanto modelador de dados, por vezes poderá ter de escrever uma expressão DAX que testa se uma coluna é filtrada por um valor específico.

Em versões anteriores do DAX, o cumprimento deste requisito era assegurado através de um padrão que envolvia três funções DAX. As funções são [IF](/dax/if-function-dax), [HASONEVALUE](/dax/hasonevalue-function-dax) e [VALUES](/dax/values-function-dax). A seguinte definição de medida apresenta um exemplo. Esta calcula o montante do imposto sobre vendas, mas apenas para as vendas feitas a clientes na Austrália.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

No exemplo, a função HASONEVALUE devolve o resultado TRUE apenas quando um único valor filtrar a coluna **Country-Region**. Quando o resultado é TRUE, a função VALUES é comparada com o texto literal "Austrália". Quando a função VALUES devolve o resultado TRUE, a medida **Sales** é multiplicada por 0,10 (valor que representa 10%). Se a função HASONEVALUE devolver o resultado FALSE por a coluna ter sido filtrada por mais de um valor, a primeira função IF devolve um resultado EM BRANCO.

A utilização da função HASONEVALUE é uma técnica de defesa. É obrigatória devido à possibilidade de a coluna **Country-Region** devolver múltiplos valores. Neste caso, a função VALUES devolve uma tabela com múltiplas linhas. Comparar uma tabela de múltiplas linhas a um valor escalar origina um erro.

## <a name="recommendation"></a>Recomendação

Recomendamos que utilize a função [SELECTEDVALUE](/dax/selectedvalue-function). Esta função atinge o mesmo resultado que o padrão descrito neste artigo, mas de uma forma mais eficaz e elegante.

Ao utilizar a função SELECTEDVALUE, a definição da medida de exemplo foi reescrita.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> É possível transmitir um _resultado alternativo_ para a função SELECTEDVALUE. O valor do resultado alternativo é devolvido quando não houver nenhum filtro ou existirem múltiplos filtros aplicados à coluna.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Percurso de aprendizagem: [Utilizar a DAX no Power BI Desktop](/learn/paths/dax-power-bi/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)