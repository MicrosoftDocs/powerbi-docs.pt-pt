---
title: Eventos de composição nos elementos visuais do Power BI
description: Os elementos visuais do Power BI podem notificar o Power BI de que estão prontos para exportar para o PowerPoint ou PDF.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: c54aaa92f3463ce1102866c8d3b69532c8b25cf7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380255"
---
# <a name="render-events-in-power-bi-visuals"></a>Eventos de composição nos elementos visuais do Power BI

A nova API consiste em três métodos (`started`, `finished` ou `failed`) que devem ser chamados durante a composição.

Quando a composição é iniciada, o código do elemento visual do Power BI chama o método `renderingStarted` para indicar que o processo de composição começou.

Se a composição for concluída com êxito, o código do elemento visual do Power BI chama imediatamente o método `renderingFinished` e notifica os serviços de escuta (principalmente, *exportar para PDF* e *exportar para o PowerPoint*) de que a imagem do elemento visual está pronta para ser exportada.

Se ocorrer um problema durante o processo, o elemento visual do Power BI será impedido de ser composto com êxito. De modo a notificar os serviços de escuta que o processo de composição não foi concluído, o código do elemento visual do Power BI deverá chamar o método `renderingFailed`. Este método também fornece uma cadeia de carateres opcional para justificar a falha.

## <a name="usage"></a>Usage

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Exemplo: o elemento visual não apresenta qualquer animação

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Exemplo: o elemento visual apresenta animações

Se o elemento visual tiver animações ou funções assíncronas a compor, o método `renderingFinished` deverá ser chamado após a animação ou dentro da função assíncrona.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Eventos de composição para a certificação de elementos visuais

O suporte dos eventos de composição por parte do elemento visual é um dos requisitos da certificação de elementos visuais. Para obter mais informações, veja os [requisitos de certificação](power-bi-custom-visuals-certified.md#certification-requirements).