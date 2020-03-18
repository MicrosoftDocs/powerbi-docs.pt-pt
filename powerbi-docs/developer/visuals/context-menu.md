---
title: Capacidades e propriedades dos elementos visuais do Power BI
description: Este artigo descreve as capacidades e propriedades dos elementos visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1e2fbe3288e5dbb759a56ad1c299db2e277408b2
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380761"
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
