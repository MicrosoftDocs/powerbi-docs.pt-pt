---
title: Adicionar uma página de destino aos elementos visuais do Power BI
description: Este artigo descreve como adicionar uma página de destino a elementos visuais do Power BI.
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d15c52134fe3c8638625e50a1374867a4abed3c1
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236704"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Adicionar uma página de destino aos elementos visuais do Power BI

Com a API 2.3.0, pode adicionar uma página de destino aos elementos visuais do Power BI. Para tal, adicione `supportsLandingPage` às capacidades e defina-o como verdadeiro. Esta ação inicializa e atualiza o seu elemento visual antes de adicionar dados ao mesmo. Uma vez que o elemento visual já não mostra uma marca d'água, pode criar a sua própria página de destino para ser apresentada no elemento visual, desde que não tenha dados.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

A seguinte imagem apresenta uma página de destino de exemplo:

![captura de ecrã a mostrar a página de destino](./media/landing-page.png)
