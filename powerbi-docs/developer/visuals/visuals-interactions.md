---
title: Interações visuais em elementos visuais do Power BI
description: Este artigo aborda a forma de verificar se os elementos visuais do Power BI devem permitir interações visuais.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1fb4f7d5950ab18a74dcacfdfef9c3ada90512c4
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378944"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Interações visuais em elementos visuais do Power BI

Os elementos visuais podem consultar o valor do sinalizador `allowInteractions`, que indica se o elemento visual deve ou não permitir interações de elementos visuais. Por exemplo, os elementos visuais são interativos durante a visualização ou edição de relatórios, mas não são interativos quando são vistos num dashboard. Essas interações são, entre outras, *clicar*, *deslocar*, *ampliar* e *selecionar*. 

> [!NOTE]
> O utilizador deve ativar as descrições em todos os cenários, seja qual for o sinalizador indicado.

O sinalizador `allowInteractions` é transmitido sob a forma de Booleano durante a inicialização do elemento visual como membro da interface IVisualHost.

O sinalizador `allowInteractions` será definido como `false` em todos os cenários do Power BI que exijam que os elementos visuais não sejam interativos (por exemplo, mosaicos de dashboard). Caso contrário (por exemplo, Relatório), `allowInteractions` é definido como `true`.

Para obter mais informações, veja o [repositório de elementos visuais do SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
