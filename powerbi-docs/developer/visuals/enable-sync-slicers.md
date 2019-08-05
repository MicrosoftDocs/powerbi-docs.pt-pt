---
title: Ativar segmentação de dados de sincronização
description: Como adicionar a funcionalidade de segmentação de dados de sincronização para elementos visuais do Power BI
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425028"
---
# <a name="sync-slicers"></a>Segmentação de dados de sincronização

Para suportar a [segmentação de dados de sincronização](https://docs.microsoft.com/power-bi/desktop-slicers), o seu elemento visual de segmentação de dados personalizado tem de utilizar a API 1.13 ou posterior.

Também é necessário que a opção esteja ativada em `capabilities.json` (veja o exemplo abaixo).

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Após a realização das alterações em `capabilities.json`, pode ver o painel de opções da segmentação de dados de sincronização quando clicar no seu elemento visual de segmentação de dados personalizado.

> [!NOTE]
> Se a sua segmentação de dados tiver mais do que um campo (categoria ou medida), a funcionalidade será desativada porque a segmentação de dados de sincronização não suporta vários campos.

![Painel de segmentação de dados de sincronização](./media/sync-slicers-panel.png)

No painel, pode ver que a visibilidade da sua segmentação de dados e a respetiva filtragem poderão ser aplicadas a várias páginas de relatório.
