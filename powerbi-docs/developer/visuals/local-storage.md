---
title: API de Armazenamento Local em Elementos Visuais do Power BI
description: Este artigo descreve como utilizar a API de Elementos Visuais do Power BI para obter acesso a armazenamento local do browser
author: uve
ms.author: v-grniki
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: 3b6746b611a41ddfb471008f5aefa4f7dc391456
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73433082"
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
