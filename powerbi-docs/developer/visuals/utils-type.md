---
title: Introdução à utilização de utilitários de tipo em elementos visuais do Power BI
description: Este artigo descreve como pode utilizar utilitários de SVG para aumentar os tipos básicos de elementos visuais do Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 5a3cfb7ea9c9f398193b45652aa43c6b83c8f70b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378001"
---
# <a name="type-utils"></a>Utilitários de escrita

TypeUtils é um conjunto de funções e classes que visa aumentar os tipos básicos de elementos visuais do Power BI.

## <a name="installation"></a>Instalação

Para instalar o pacote, deve executar o seguinte comando no diretório com os elementos visuais personalizados atuais:

npm install powerbi-visuals-utils-typeutils --save Este comando instala o pacote e adiciona um pacote sob a forma de dependência ao seu package.json

## <a name="double"></a>Double

`Double` permite manipular a precisão dos números.

O módulo fornece as seguintes funções:

### <a name="pow10"></a>pow10

Esta função devolve uma potência de 10.

```typescript
function pow10(exp: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Esta função devolve um logaritmo de base 10 do número.

```typescript
function log10(val: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Esta função devolve uma potência de 10 que representa a precisão do número.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Esta função verifica se um delta entre dois números é menor que a precisão fornecida.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Esta função verifica se o primeiro valor é menor que o segundo valor.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Esta função verifica se o primeiro valor é menor ou igual ao segundo valor.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Esta função verifica se o primeiro valor é maior que o segundo valor.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Esta função verifica se o primeiro valor é maior ou igual ao segundo valor.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Esta função arredonda o número por defeito com a precisão fornecida.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Esta função arredonda o número por excesso (`ceils`) com a precisão fornecida.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Esta função arredonda o número por defeito para a precisão fornecida.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Esta função arredonda o número por excesso (`ceils`) para a precisão fornecida.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Esta função arredonda o número para a precisão fornecida.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Esta função devolve um número que se encontra entre mín. e máx.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Esta função arredonda o número.

```typescript
function round(x: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Esta função remove as casas decimais.

```typescript
function removeDecimalNoise(value: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Esta função verifica se o número é inteiro.

```typescript
function isInteger(value: number): boolean;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Esta função incrementa o número pelo número fornecido e devolve o número arredondado.

```typescript
function toIncrement(value: number, increment: number): number;
```

Por exemplo:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototype

`Prototype` permite herdar objetos.

O módulo fornece as seguintes funções:

## <a name="inherit"></a>inherit

Esta função devolve um objeto novo com o objeto fornecido como seu protótipo.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Por exemplo:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Esta função devolve um objeto novo com o objeto fornecido como seu protótipo se, e apenas se, o protótipo não tiver sido definido.

```typescript
function inheritSingle<T>(obj: T): T;
```

Por exemplo:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` permite converter píxeis em pontos e vice-versa.

O módulo fornece as seguintes funções:

## <a name="tostring"></a>toString

Esta função converte o valor de píxeis numa cadeia.

```typescript
function toString(px: number): string;
```

Por exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Esta função converte o valor de pontos fornecido no valor de píxeis e devolve a interpretação da cadeia.

```typescript
function fromPoint(pt: number): string;
```

Por exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Esta função converte o valor de pontos fornecido no valor de píxeis.

```typescript
function fromPointToPixel(pt: number): number;
```

Por exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Esta função converte o valor de píxeis fornecido no valor de pontos.

```typescript
function toPoint(px: number): number;
```

Por exemplo:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
