---
title: Rendering events (Eventos de composição)
description: Os elementos visuais do Power BI podem notificar o Power BI de que estão prontos para exportar para o Power Point/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425097"
---
# <a name="event-service"></a>Serviço de eventos

A nova API consiste em três métodos (iniciada, concluída ou com falhas) que devem ser chamados durante a composição.

Quando a composição é iniciada, o código do elemento visual personalizado chama o método renderingStarted para indicar que o processo de composição começou.

Se a composição for concluída com sucesso, o código do elemento visual personalizado chamará imediatamente o método `renderingFinished` e notificará os serviços de escuta **(principalmente "exportar para PDF" e "exportar para o PowerPoint"** ) de que a imagem do elemento visual está pronta.

Caso tenha ocorrido um problema durante o processo de composição que impeça que o elemento visual personalizado seja concluído com sucesso, o código do elemento visual personalizado deverá chamar o método `renderingFailed` e notificar o serviço de escuta de que o processo de composição não foi concluído. Este método também fornece uma cadeia de carateres opcional para a causa da falha.

## <a name="usage"></a>Utilização

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Exemplo simples. O elemento visual não tem animações na composição

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

### <a name="sample-the-visual-with-animation"></a>Exemplo. O elemento visual tem uma animação

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
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Eventos de composição para a certificação de elementos visuais

O suporte dos eventos de composição por parte do elemento visual é um dos requisitos da certificação de elementos visuais. Leia mais sobre [requisitos de certificação](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements).
