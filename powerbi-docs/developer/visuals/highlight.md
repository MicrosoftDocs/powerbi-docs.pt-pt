---
title: Realce
description: Realce de seleções de pontos de dados em elementos visuais do Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4ff2187dc99d4e790b08c11f55a37e31e85693ad
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193978"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Realçar pontos de dados em elementos visuais do Power BI

Por predefinição, sempre que um elemento for selecionado, a matriz `values` no objeto `dataView` será filtrada apenas para os valores selecionados. Isso fará com que todos os outros elementos visuais na página mostrem apenas os dados selecionados.

![realçar comportamento predefinido de "DataView"](./media/highlight-dataview.png)

Se definir a propriedade `supportsHighlight` no seu `capabilities.json` como `true`, receberá a matriz completa sem filtro `values`, bem como uma matriz `highlights`. A matriz `highlights` terá o mesmo comprimento que a matriz "values" e todos os valores não selecionados serão definidos como `null`. Quando esta propriedade está ativada, o elemento visual é responsável por realçar os dados adequados ao comparar a matriz `values` com a matriz `highlights`.

![realçar supportshighlight de "DataView"](./media/highlight-dataview-supports.png)

No exemplo, verá que apenas uma barra está selecionada e que é o único valor na matriz "highlights". Também é importante reparar que pode haver múltiplas seleções e realce parcial. O valor numérico correspondente nas matrizes "values" e "highlights" estarão sempre presentes, mas serão diferentes.
