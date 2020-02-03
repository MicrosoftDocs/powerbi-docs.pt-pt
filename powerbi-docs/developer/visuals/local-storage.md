---
title: API de Armazenamento Local em Elementos Visuais do Power BI
description: Este artigo descreve como utilizar a API de Elementos Visuais do Power BI para obter acesso a armazenamento local do browser
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 7665f0c8e3c909263f194a0fd54a54ed2a752c8c
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819106"
---
# <a name="local-storage-api"></a>Local Storage API (API de Armazenamento Local)

A API de Armazenamento Local é uma API que um elemento visual personalizado pode utilizar para pedir ao anfitrião para guardar ou carregar dados do armazenamento do dispositivo. É isolada, na medida em que existe uma separação de acesso a armazenamento entre diferentes tipos de elementos visuais.

## <a name="sample"></a>Exemplo

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

A API de Armazenamento Local não está ativada para Elementos Visuais Personalizados por predefinição. Se quiser ativá-la para o seu Elemento Visual Personalizado, envie o pedido para o Suporte de Elementos Visuais Personalizados do Power BI `pbicvsupport@microsoft.com`.  
**Tenha em atenção que o seu elemento visual deverá estar disponível no [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) e ser [certificado](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
