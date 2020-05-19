---
title: Adicionar cores aos elementos visuais do Power BI
description: Este artigo descreve como adicionar cores aos elementos visuais do Power BI e como lidar com pontos de dados de um elemento visual com cor.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3f3574545d82ac11c762b7011afdc49cbe855224
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141156"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Adicionar cores aos elementos visuais do Power BI

Este artigo descreve como adicionar cores aos elementos visuais e como lidar com pontos de dados de um elemento visual com cor.

`IVisualHost` expõe a cor como um dos serviços.
O código de exemplo neste artigo modifica o [elemento visual SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
Para obter o código-fonte, veja [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

Para começar a criar elementos visuais, veja [Desenvolver um elemento visual do Power BI](custom-visual-develop-tutorial.md).

## <a name="add-color-to-data-points"></a>Adicionar cor aos pontos de dados

Cada ponto de dados é representado por uma cor diferente.
Adicione cor à interface `BarChartDataPoint`, como no exemplo a seguir:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Utilizar o serviço de paleta de cores

O serviço `colorPalette` faz a gestão das cores utilizadas no elemento visual.
Existe uma instância do serviço disponível em `IVisualHost`.

Defina-o no método `update`.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Atribuir cor aos pontos de dados

Em seguida, especifique `dataPoints`.
Neste exemplo, cada um dos `dataPoints` inclui o valor, a categoria e a cor.
`dataPoints` também pode incluir outras propriedades.

Em `SampleBarChart`, o método `visualTransform` encapsula o cálculo `dataPoints`.
Este método faz parte do viewmodel do Gráfico de Barras.
Como o método itera através do cálculo `dataPoints` em `visualTransform`, é o local ideal para atribuir cores, como no código seguinte:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Em seguida, aplique os dados de `dataPoints` na seleção [d3](https://d3js.org/) `barSelection` dentro do método `update`:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre os elementos visuais do Power BI, veja [Capacidades e propriedades dos elementos visuais do Power BI](capabilities.md).

Para saber mais sobre o desenvolvimento de elementos visuais do Power BI, veja [Como depurar elementos visuais do Power BI](visuals-how-to-debug.md) e [Resolver problemas com os elementos visuais do Power BI](power-bi-custom-visuals-troubleshoot.md).
