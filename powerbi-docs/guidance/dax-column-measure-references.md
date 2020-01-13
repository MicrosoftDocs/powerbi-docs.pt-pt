---
title: 'DAX: Referências de colunas e de medidas'
description: Orientação sobre como fazer referência a colunas em medidas nas suas expressões DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 3ca49008639f7e3e084c8d045bc911aff57b7b21
ms.sourcegitcommit: 0da17de80c9651f9f4474d1abb1bdaaade8808fb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/27/2019
ms.locfileid: "75498743"
---
# <a name="dax-column-and-measure-references"></a>DAX: Referências de colunas e de medidas

Enquanto modelador de dados, as suas expressões DAX farão referência a colunas e medidas de modelos. As colunas e medidas estão sempre associadas a tabelas de modelos, mas estas associações são diferentes. Por conseguinte, temos recomendações diferentes sobre a forma como fará referência a estas nas suas expressões.

## <a name="columns"></a>Colunas

As colunas são objetos ao nível da tabela e os nomes das colunas têm de ser únicos dentro de uma tabela. Desta forma, é possível utilizar o mesmo nome de coluna várias vezes no seu modelo desde que as colunas pertençam a tabelas diferentes. Há mais uma regra: um nome de coluna não pode ser igual ao nome de uma medida ou hierarquia existente na mesma tabela.

Regra geral, o DAX não irá impor a utilização de uma referência _completamente qualificada_ a uma coluna. Se uma referência for completamente qualificada isto significa que o nome da tabela precede o nome da coluna.

Segue-se um exemplo de uma definição de coluna calculada com recurso exclusivo a referências de nomes de colunas. As colunas **Sales** e **Cost** pertencem a uma tabela chamada **Orders**.

```dax
Profit = [Sales] - [Cost]
```

A mesma definição pode ser reescrita com referências de colunas completamente qualificadas.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Contudo, por vezes, terá de utilizar referências de colunas completamente qualificadas quando o Power BI detetar a existência de ambiguidade. Quando introduzir uma fórmula, será alertado por um sublinhado vermelho ondulado e por uma mensagem de erro. Além disso, algumas funções DAX, tais como [LOOKUPVALUE](/dax/lookupvalue-function-dax), requerem a utilização de colunas completamente qualificadas.

Recomendamos que qualifique sempre completamente as suas referências de colunas. Os motivos para tal encontram-se na secção [Recomendações](#recommendations).

## <a name="measures"></a>Medidas

As medidas são objetos ao nível do modelo. Como tal, os nomes das medidas têm de ser únicos dentro do mesmo modelo. Contudo, no painel **Campos**, os autores do relatório verão cada medida associada a uma única tabela do modelo. Esta associação é definida por motivos cosméticos, pelo que a pode configurar ao definir a propriedade **Tabela Principal** para a medida. Para obter mais informações, veja [Medidas no Power BI Desktop (Organizar as medidas)](../desktop-measures.md#organizing-your-measures).

É possível utilizar uma medida completamente qualificada nas suas expressões. O IntelliSense do DAX dará inclusivamente a sugestão. Contudo, tal não é necessário nem é uma prática recomendada. Se alterar a tabela principal para uma medida, qualquer expressão que utilize uma referência de medida completamente qualificada à tabela será quebrada. Em seguida, terá de editar cada fórmula quebrada para remover (ou atualizar) a referência de medida.

Recomendamos que nunca qualifique as suas referências de medidas. Os motivos para tal encontram-se na secção [Recomendações](#recommendations).

## <a name="recommendations"></a>Recomendações

As nossas recomendações são simples e fáceis de recordar:

- Utilize sempre referências de colunas completamente qualificadas.
- Nunca utilize referências de medidas completamente qualificadas.

Eis o porquê:

- **Entrada de fórmulas**: serão aceites expressões, uma vez que não haverá referências ambíguas para resolver. Além disso, satisfará o requisito das funções DAX que exigem referências de colunas completamente qualificadas.
- **Robustez**: as expressões continuarão a funcionar, mesmo quando alterar uma propriedade da tabela principal da medida.
- **Legibilidade**: a compreensão das expressões será rápida e fácil. Determinará rapidamente se é uma coluna ou medida com base no facto de serem ou não completamente qualificadas.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
