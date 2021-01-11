---
title: API de Armazenamento Local em elementos visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo descreve como utilizar a API de Elementos Visuais do Power BI para obter acesso a armazenamento local do browser. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: abec68c5622d3dcd96746148ed7a6da4f06c8ec0
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888196"
---
# <a name="local-storage-api"></a>Local Storage API (API de Armazenamento Local)

A API de Armazenamento Local é uma API que um elemento visual personalizado pode utilizar para pedir ao anfitrião para guardar ou carregar dados do armazenamento do dispositivo. É isolada, na medida em que existe uma separação de acesso a armazenamento entre diferentes tipos de elementos visuais.

## <a name="sample"></a>Sample

Caso o elemento visual personalizado deva aumentar um contador sempre que o método de atualização for chamado, mas o valor do contador deva também ser preservado e não reiniciado cada vez que o elemento visual for iniciado:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Limitações e problemas conhecidos

A API de Armazenamento Local não está ativada para elementos visuais do Power BI por predefinição. Se quiser ativá-la para o seu elemento visual do Power BI, envie o pedido para o Suporte de elementos visuais do Power BI `pbicvsupport@microsoft.com`.  
**Tenha em atenção que o seu elemento visual deverá estar disponível no [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) e ser [certificado](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
