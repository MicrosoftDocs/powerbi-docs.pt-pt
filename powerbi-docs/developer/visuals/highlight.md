---
title: Realce
description: Realce de seleções de pontos de dados em elementos visuais do Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424821"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Realçar pontos de dados em elementos visuais do Power BI

Por predefinição, sempre que um elemento for selecionado, a matriz `values` no objeto `dataView` será filtrada apenas para os valores selecionados. Isso fará com que todos os outros elementos visuais na página mostrem apenas os dados selecionados.

![realçar comportamento predefinido de "DataView"](./media/highlight-dataview.png)

Se definir a propriedade `supportsHighlight` no seu `capabilities.json` como `true`, receberá a matriz completa sem filtro `values`, bem como uma matriz `highlights`. A matriz `highlights` terá o mesmo comprimento que a matriz "values" e todos os valores não selecionados serão definidos como `null`. Quando esta propriedade está ativada, o elemento visual é responsável por realçar os dados adequados ao comparar a matriz `values` com a matriz `highlights`.

![realçar supportshighlight de "DataView"](./media/highlight-dataview-supports.png)

No exemplo, verá que apenas uma barra está selecionada e que é o único valor na matriz "highlights". Também é importante reparar que pode haver múltiplas seleções e realce parcial. O valor numérico correspondente nas matrizes "values" e "highlights" estarão sempre presentes, mas serão diferentes.