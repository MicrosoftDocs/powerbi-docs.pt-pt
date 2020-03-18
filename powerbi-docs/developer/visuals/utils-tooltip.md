---
title: Introdução à utilização de utilitários de descrição em elementos visuais do Power BI
description: Este artigo descreve como utilizar utilitários de descrição para simplificar a personalização das descrições dos elementos visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 67470ec405806f44fdb483e857d222ad4ff05a45
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379174"
---
# <a name="tooltip-utils"></a>Utilitários de descrição
Este artigo irá ajudá-lo a instalar, importar e utilizar utilitários de descrição. Este utilitário é útil para qualquer personalização de descrições em elementos visuais do Power BI.

## <a name="requirements"></a>Requirements
Para utilizar o pacote, deve ter o seguinte:
* [node.js](https://nodejs.org) (recomendamos a versão LTS mais recente)
* [npm](https://www.npmjs.com/) (a versão mínima suportada é a 3.0.0)
* O elemento visual personalizado criado por [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Instalação

Para instalar o pacote, deve executar o seguinte comando no diretório com os elementos visuais atuais:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Este comando instala o pacote e adiciona um pacote como dependência a ```package.json```

## <a name="usage"></a>Usage

> O Guia de Utilização descreve uma API pública do pacote. Encontrará uma descrição e alguns exemplos para cada interface pública do pacote.

Este pacote apresenta a forma de criar `TooltipServiceWrapper` e métodos para ajudar a lidar com as ações de descrição. Utiliza as interfaces de descrição `ITooltipServiceWrapper`, `TooltipEventArgs` e `TooltipEnabledDataPoint`. 

Além disso, tem métodos específicos (processadores de eventos de toque) relacionados com o desenvolvimento de aplicações móveis: `touchEndEventName`, `touchStartEventName` e `usePointerEvents`.

`TooltipServiceWrapper` apresenta a forma mais simples de manipular descrições.

Este módulo apresenta a seguinte interface e função:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Interfaces](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Eventos de toque](#touch-events)

### `createTooltipServiceWrapper`
Esta função cria uma instância de ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

```ITooltipService``` está disponível em [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Exemplo**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

Dê uma vista de olhos ao código de exemplo do elemento visual personalizado [aqui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391).

### `ITooltipServiceWrapper`
Esta interface descreve os métodos públicos de TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Este método adiciona descrições à seleção atual.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Exemplo**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

Dê uma vista de olhos ao código de exemplo do elemento visual personalizado [aqui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931).

Preste também atenção ao seguinte exemplo de personalização de descrições no elemento visual Gantt personalizado [aqui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)

### `ITooltipServiceWrapper.hide`

Este método oculta a descrição.

```typescript
hide(): void;
```

**Exemplo**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Estas interfaces são utilizadas durante a criação de TooltipServiceWrapper e da sua utilização. Também foram mencionadas em exemplos de tópicos anteriores [aqui](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Agora, os utilitários de descrição conseguem processar vários eventos de toque úteis para o desenvolvimento de aplicações móveis.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Este método devolve o nome do evento de início de toque.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Este método devolve o nome do evento de início de toque.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Este método devolve o evento touchStart atual relacionado ou não com o ponteiro.
