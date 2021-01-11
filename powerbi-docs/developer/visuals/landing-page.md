---
title: Adicionar uma página de destino aos elementos visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo descreve como adicionar uma página de destino a elementos visuais do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4381ecf63c0864c4d68e48959efc14baa9d4553b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886356"
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

![captura de ecrã a mostrar a página de destino](media/landing-page/app-landing-page.png)
