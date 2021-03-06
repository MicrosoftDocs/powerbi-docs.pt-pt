---
title: Ativar a funcionalidade Segmentação de Dados de Sincronização em elementos visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo descreve como pode adicionar a funcionalidade Segmentação de Dados de Sincronização a elementos visuais do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: bd69e05bba3e9449f9fb6f07bd9625dfb1ea0c08
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885294"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Segmentação de Dados de Sincronização em elementos visuais do Power BI

Para suportar a funcionalidade [Segmentação de Dados de Sincronização](../../visuals/power-bi-visualization-slicers.md), o elemento visual de segmentação de dados personalizado tem de utilizar a versão 1.13.0 ou posterior da API.

Além disso, tem de ativar a opção no ficheiro *capabilities.json*, conforme mostrado no seguinte código:

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

Depois de atualizar o ficheiro *capabilities.json*, poderá ver o painel de opções **Segmentação de dados de sincronização** quando selecionar o seu elemento visual de segmentação de dados personalizado.

> [!NOTE]
> A funcionalidade Segmentação de Dados de Sincronização não suporta mais do que um campo. Se a sua segmentação de dados tiver mais do que um campo (**Categoria** ou **Medida**), a funcionalidade será desativada.

![O painel "Segmentação de dados de sincronização"](media/enable-sync-slicers/sync-slicers-panel.png)

No painel **Segmentação de dados de sincronização**, pode ver que a visibilidade e os filtros da segmentação de dados podem ser aplicados a várias páginas do relatório.