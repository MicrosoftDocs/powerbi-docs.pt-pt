---
title: Adicionar um menu de contexto a um elemento visual do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Saiba como adicionar um menu de contexto a um elemento visual do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1c19ba94588628e002cdb9e65f59bd4182020e1c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888702"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Adicionar menu de contexto ao Elemento Visual do Power BI

Pode utilizar `selectionManager.showContextMenu()` com parâmetros `selectionId` e uma posição (como um objeto `{x:, y:}`) para que o Power BI apresente um menu de contexto para o elemento visual.

> [!IMPORTANT]
> O `selectionManager.showContextMenu()` foi apresentado na API de Elementos Visuais 2.2.0.

Normalmente, é adicionado como um evento de clique com o botão direito do rato (ou um premir longo em dispositivos de toque). O Menu de Contexto foi adicionado ao BarChart de amostra para referência:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
