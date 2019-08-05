---
title: Ordenar
description: Comportamento de ordenação predefinido do Elemento Visual do Power BI.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f3d913e2bce34850dfae4c9486b2e43c78521a58
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424522"
---
# <a name="sorting-options"></a>Opções de ordenação

`Sorting` especifica o comportamento de ordenação predefinido do elemento visual.
A funcionalidade necessita de um dos parâmetros descritos abaixo:

## <a name="default-sorting"></a>Ordenação predefinida

A opção `default` é a forma mais simples. Permite a ordenação dos dados apresentados na secção "DataMappings".
Esta opção permite a ordenação de "DataMappings" pelo utilizador e a especificação da direção da ordenação.

```json
    "sorting": {
        "default": {   }
    }
```

![Opções de ordenação no menu de contexto](./media/sorting.png)

## <a name="implicit-sorting"></a>Ordenação implícita

`implicit` refere-se à ordenação com parâmetro de matriz – `clauses` que descreve a ordenação para cada função de dados.
`implicit` significa que o utilizador do elemento visual não pode alterar a ordem de ordenação.
O Power BI não apresentará opções de ordenação no menu do elemento visual. No entanto, o Power BI irá classificar os dados de acordo com as definições especificadas.

Os parâmetros `clauses` podem conter vários objetos com dois parâmetros:

- `role` – determina `DataMapping` para ordenação.

- `direction` – determina a direção da ordenação (1 = ascendente, 2 = descendente).

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

`custom` significa que a ordenação é gerida pelo programador no código do elemento visual.
