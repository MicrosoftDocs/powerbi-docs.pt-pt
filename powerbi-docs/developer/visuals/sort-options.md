---
title: Opções de ordenação dos elementos visuais do Power BI
description: Este artigo aborda o comportamento de ordenação predefinido dos elementos visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: a360f619428a01c4e7a30481374d042b8e368682
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193911"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Opções de ordenação dos elementos visuais do Power BI

Este artigo descreve como é que as opções de *ordenação* especificam o comportamento de ordenação predefinido dos elementos visuais do Power BI. 

A capacidade de ordenação requer um dos seguintes parâmetros.

## <a name="default-sorting"></a>Ordenação predefinida

A opção `default` é a forma mais simples. Permite a ordenação dos dados apresentados na secção "DataMappings". A opção permite a ordenação dos mapas de dados pelo utilizador e especifica a direção da ordenação.

```json
    "sorting": {
        "default": {   }
    }
```

![Opções de ordenação no menu de contexto](./media/sorting.png)

## <a name="implicit-sorting"></a>Ordenação implícita

A ordenação implícita refere-se à ordenação com o parâmetro de matriz `clauses`, que descreve a ordenação para cada função de dados. `implicit` significa que o utilizador do elemento visual não pode alterar a ordem de ordenação. O Power BI não apresenta opções de ordenação no menu do elemento visual. No entanto, o Power BI classifica os dados de acordo com as definições especificadas.

Os parâmetros `clauses` podem conter vários objetos com dois parâmetros:

- `role`: determina `DataMapping` para ordenação
- `direction`: determina a direção da ordenação (1 = Ascendente, 2 = Descendente)

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Ordenação personalizada

A ordenação personalizada significa que a ordenação é gerida pelo programador no código do elemento visual.
