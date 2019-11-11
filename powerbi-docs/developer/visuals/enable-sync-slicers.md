---
title: Ativar a funcionalidade Segmentação de Dados de Sincronização em elementos visuais do Power BI
description: Este artigo descreve como pode adicionar a funcionalidade Segmentação de Dados de Sincronização a elementos visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 055878988a197b80a8e4842a6567966f75af2ce5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880150"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Segmentação de Dados de Sincronização em elementos visuais do Power BI

Para suportar a funcionalidade [Segmentação de Dados de Sincronização](https://docs.microsoft.com/power-bi/desktop-slicers), o seu elemento visual de segmentação de dados personalizado tem de utilizar a versão de API 1.13 ou posterior.

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

![O painel "Segmentação de dados de sincronização"](./media/sync-slicers-panel.png)

No painel **Segmentação de dados de sincronização**, pode ver que a visibilidade e os filtros da segmentação de dados podem ser aplicados a várias páginas do relatório.
