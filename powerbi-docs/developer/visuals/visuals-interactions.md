---
title: Visuals interactions (Interações de elementos visuais)
description: Como verificar se o elemento visual do Power BI deve permitir interações de elementos visuais
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424499"
---
# <a name="visuals-interactions"></a>Visuals interactions (Interações de elementos visuais)

Os elementos visuais podem consultar o valor do sinalizador "allowInteractions", que indica se o elemento visual deve ou não permitir interações de elementos visuais.
Por exemplo, os elementos visuais são interativos durante a visualização ou edição de relatórios, mas não são interativos quando são vistos num dashboard.
Essas interações são, entre outras, clicar, deslocar, ampliar e selecionar.
Tenha em atenção que as descrições devem estar ativadas em todos os cenários independentemente deste sinalizador.

O sinalizador "allowInteractions" é transmitido sob a forma de booleano durante a inicialização do elemento visual como membro da interface IVisualHost.

O sinalizador "allowInteractions" será definido como falso em todos os cenários do Power BI que exijam que os elementos visuais não sejam interativos (por exemplo, mosaicos de dashboard).
Caso contrário (por exemplo, relatório), "allowInteractions" estará definido como verdadeiro.

Para obter mais informações, veja o [repositório de elementos visuais do SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

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
