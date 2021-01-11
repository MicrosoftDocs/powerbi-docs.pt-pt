---
title: Opções de ordenação dos elementos visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo aborda o comportamento de ordenação predefinido dos elementos visuais do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 0d24719b486608c283ec73f0188092a1ece3155e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889254"
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

![Opções de ordenação no menu de contexto](media/sort-options/sorting.png)

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
