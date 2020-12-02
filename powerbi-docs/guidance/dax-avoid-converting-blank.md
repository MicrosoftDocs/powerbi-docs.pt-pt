---
title: 'DAX: Evitar converter espaços em branco em valores'
description: Documentação de orientação sobre a conversão de resultados EM BRANCO para valores
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/24/2019
ms.openlocfilehash: 20686615c58015040349138ffd49b544c5dac70a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394273"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Evitar converter espaços em branco em valores

Enquanto modelador de dados e ao escrever expressões de medida, poderá deparar-se com casos onde não é devolvido um valor significativo. Nestas instâncias, pode ter a tentação de devolver um valor, como um zero. Sugerimos que pondere cuidadosamente se este tipo de design é eficiente e prático.

Considere a seguinte definição de medida que converte explicitamente os resultados EM BRANCO para zero.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Considere outra definição de medida que também converte resultados EM BRANCO para zero.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

A função [DIVIDIR](/dax/divide-function-dax) divide a medida **Profit** pela medida **Sales**. Se o resultado for zero ou EM BRANCO, será devolvido o terceiro argumento: o resultado alternativo (opcional). Neste exemplo, uma vez que zero foi transmitido como o resultado alternativo, a medida devolverá sempre um valor.

Esta forma de criar medidas é ineficaz e resulta na criação de relatórios com fraco desempenho.

Quando adicionados ao elemento visual de um relatório, o Power BI tenta obter todos os agrupamentos no contexto do filtro. Muitas vezes, a avaliação e obtenção de uma grande quantidade de resultados de consulta provoca lentidão na apresentação de um relatório. Cada medida de exemplo pode tornar um cálculo simples numa operação morosa, o que força o Power BI a utilizar mais memória do que o necessário.

Além disso, a existência de muitos agrupamentos tende a sobrecarregar os utilizadores do seu relatório.

Vejamos o que acontece quando a medida **Profit Margin** é adicionada a um elemento visual de tabela, agrupado por cliente.

![Captura de ecrã a mostrar o Power B I Desktop com um elemento visual de tabela de dados com uma linha por cliente. Os valores de vendas EM BRANCO e os valores de Profit Margin são 0%. ](media/dax-avoid-converting-blank/table-visual-poor.png)

O elemento visual de tabela apresenta um número enorme de linhas. (Na verdade, existem 18 484 clientes no modelo e a tabela tenta apresentá-los a todos.) Repare que os clientes visíveis não obtiveram qualquer venda. No entanto, como a medida **Profit Margin** devolve sempre um valor, os mesmos são apresentados.

> [!NOTE]
> Quando existem demasiados pontos de dados a apresentar num elemento visual, o Power BI pode utilizar estratégias de redução de dados para remover ou resumir uma grande quantidade de resultados de consulta. Para obter mais informações, veja [Limites de pontos de dados e estratégias por tipo de elemento visual](../visuals/power-bi-data-points.md).

Vejamos o que acontece quando a definição da medida **Profit Margin** é melhorada. Agora, a medida apenas devolve um valor quando a medida **Sales** não está EM BRANCO (ou zero).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

Agora, o elemento visual da tabela apresenta apenas os clientes que realizaram vendas no contexto do filtro atual. A medida melhorada proporciona uma experiência mais eficiente e prática para os utilizadores do seu relatório.

![Captura de ecrã a mostrar o Power B I Desktop com um elemento visual de tabela de dados com conteúdos filtrados.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Quando for necessário, pode configurar um elemento visual para apresentar todos os agrupamentos (que devolvem valores ou resultados EM BRANCO) no contexto de filtro ao ativar a opção [Mostrar Itens Sem Dados](../create-reports/desktop-show-items-no-data.md).

## <a name="recommendation"></a>Recomendação

Recomendamos que as suas medidas devolvam resultados EM BRANCO quando não for possível devolver um valor significativo.

Esta abordagem de design é eficiente e permite que o Power BI apresente relatórios mais rapidamente. Além disso, a devolução de resultados EM BRANCO é melhor porque os elementos visuais de relatórios eliminam (por predefinição) agrupamentos quando os resumos estão EM BRANCO.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Percurso de aprendizagem: [Utilizar a DAX no Power BI Desktop](/learn/paths/dax-power-bi/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)