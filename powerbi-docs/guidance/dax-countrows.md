---
title: 'DAX: COUNTROWS em vez de COUNT'
description: Documentação de orientação sobre quando utilizar as funções COUNTROWS.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 8d3baba388900a9d57d6490db13c25cb363667ba
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088517"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: COUNTROWS em vez de COUNT

Enquanto modelador de dados, por vezes poderá ter de escrever uma expressão DAX que conte linhas de tabela. A tabela pode ser uma tabela de modelo ou uma expressão que devolve uma tabela.

O seu requisito pode ser atingido de duas formas. Pode utilizar a função [COUNT](/dax/count-function-dax) para contar valores de coluna ou pode utilizar a função [COUNTROWS](/dax/countrows-function-dax) para contar linhas de tabela. Ambas as funções darão o mesmo resultado se a coluna que for alvo da contagem não contiver qualquer resultado EM BRANCO.

A seguinte definição de medida apresenta um exemplo. Esta calcula o número de valores de coluna **DataDaEncomenda**.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Se a granularidade da tabela **Sales** for de uma linha por ordem de venda e a coluna **OrderDate** não contiver resultados EM BRANCO, a medida devolverá um resultado correto.

No entanto, a seguinte definição de medida é uma solução melhor.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Existem três motivos para a segunda definição de medida ser melhor:

- É mais eficiente e, assim sendo, traduz-se num melhor desempenho.
- Não considera os resultados EM BRANCO incluídos em qualquer coluna da tabela.
- A intenção da fórmula torna-se mais clara ao ponto de ser autodescritiva.

## <a name="recommendation"></a>Recomendação

Quando tiver a intenção de contar linhas de tabela, recomendamos que utilize sempre a função COUNTROWS.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Percurso de aprendizagem: [Utilizar a DAX no Power BI Desktop](/learn/paths/dax-power-bi/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)