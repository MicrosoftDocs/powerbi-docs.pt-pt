---
title: API de Armazenamento Local em Elementos Visuais do Power BI
description: Este artigo descreve como utilizar a API de Elementos Visuais do Power BI para obter acesso a armazenamento local do browser
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879890"
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

A API de Armazenamento Local não está ativada para Elementos Visuais Personalizados por predefinição. Se quiser ativá-la para o seu Elemento Visual Personalizado, envie o pedido para o Suporte de Elementos Visuais Personalizados do Power BI `pbicvsupport@microsoft.com`
