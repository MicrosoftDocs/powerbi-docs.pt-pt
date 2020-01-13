---
title: Introdução à utilização de utilitários de SVG no elemento visual do Power BI
description: Este artigo descreve como utilizar utilitários de SVG para simplificar manipulações de SVG para elementos visuais personalizados do Power BI
author: vtkalek
ms.author: asander
manager: asander
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 15398c0e8d7322e29c502f49b8c1ea0798f52afe
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2019
ms.locfileid: "75308531"
---
# <a name="svg-utils"></a>Utilitários de SVG

SVGUtils é um conjunto de funções e classes para simplificar manipulações de SVG para elementos visuais personalizados do Power BI

## <a name="installation"></a>Instalação

Para instalar o pacote, deve executar o seguinte comando no diretório com os elementos visuais atuais:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

O módulo `CssConstants` fornece a função especial e a interface para trabalhar com seletores de classe.

O módulo `powerbi.extensibility.utils.svg.CssConstants` fornece a seguinte função e interface:

## <a name="classandselector"></a>ClassAndSelector

Esta interface descreve as propriedades comuns do seletor de classe.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Esta função cria uma instância de ClassAndSelector com o nome especificado da classe.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Por exemplo:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

`manipulation` fornece algumas funções especiais para gerar cadeias para utilizar com a propriedade transform de SVG.

O módulo fornece as seguintes funções:

### <a name="translate"></a>translate

Esta função cria uma cadeia translate para utilizar com a propriedade transform de SVG.

```typescript
function translate(x: number, y: number): string;
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Esta função cria uma cadeia translateX para utilizar com a propriedade transform de SVG.

```typescript
function translateXWithPixels(x: number): string;
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Esta função cria uma cadeia translate para utilizar com a propriedade transform de SVG.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Esta função cria uma cadeia translate-rotate para utilizar com a propriedade transform de SVG.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

Esta função cria uma cadeia scale para utilizar numa propriedade transform de CSS.

```typescript
function scale(scale: number): string;
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Esta função cria uma cadeia transform-origin para utilizar numa propriedade transform-origin de CSS.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Esta função força a conclusão de todas as transições de D3.

```typescript
function flushAllD3Transitions(): void;
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Esta função analisa a cadeia transform com o valor "translate(x,y)".

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Esta função cria uma seta.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Por exemplo:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

O módulo `Rect` fornece algumas funções especiais para manipular retângulos.

O módulo fornece as seguintes funções:

### <a name="getoffset"></a>getOffset

Esta função devolve um desfasamento do retângulo.

```typescript
function getOffset(rect: IRect): IPoint;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Esta função devolve o tamanho do retângulo.

```typescript
function getSize(rect: IRect): ISize;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Esta função modifica o tamanho do retângulo.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Esta função devolve a posição direita do retângulo.

```typescript
function right(rect: IRect): number;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Esta função devolve a posição inferior do retângulo.

```typescript
function bottom(rect: IRect): number;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Esta função devolve a posição superior à esquerda do retângulo.

```typescript
function topLeft(rect: IRect): IPoint;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Esta função devolve a posição superior à direita do retângulo.

```typescript
function topRight(rect: IRect): IPoint;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Esta função devolve a posição inferior à esquerda do retângulo.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Esta função devolve a posição inferior à direita do retângulo.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Exemplo

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

Esta função cria uma cópia do retângulo.

```typescript
function clone(rect: IRect): IRect;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Esta função converte o retângulo numa cadeia.

```typescript
function toString(rect: IRect): string;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Esta função aplica um determinado desfasamento ao retângulo.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>adicionar

Esta função adiciona o primeiro retângulo ao segundo retângulo.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Esta função devolve o ponto mais próximo no retângulo para um determinado ponto.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Esta função compara retângulos e devolve true se forem iguais.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Esta função compara retângulos ao considerar a precisão dos valores.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Esta função verifica se o retângulo está vazio.

```typescript
function isEmpty(rect: IRect): boolean;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Esta função verifica se o retângulo contém o ponto.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Esta função verifica se os retângulos se intersetam.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Esta função devolve uma interseção de retângulos.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Esta função combina retângulos.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Esta função devolve um ponto central do retângulo.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Por exemplo:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>pointer

O módulo `pointer` fornece uma função especial para obter a posição do ponteiro.

O módulo fornece a seguinte função:

### <a name="getcoordinates"></a>getCoordinates

Esta função devolve a posição do ponteiro.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Por exemplo:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
