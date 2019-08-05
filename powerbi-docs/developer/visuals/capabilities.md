---
title: Capacidades
description: Capacidades e propriedades dos Elementos Visuais do Power BI
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425465"
---
# <a name="power-bi-visual-capabilities"></a>Capacidades do Elemento Visual do Power BI

As capacidades fornecem informações ao anfitrião sobre o seu elemento visual. Todas as propriedades no modelo de Capacidades são `optional`

Os objetos raiz das capacidades do elemento visual são `dataRoles`, `dataViewMappings` e por aí adiante.

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>Defina os campos de dados esperados pelo seu elemento visual – `dataRoles`

Para definir os campos que podem ser associados a dados, utilizamos `dataRoles` que utilizam uma variedade de objetos `DataViewRole`, que definem todas as propriedades necessárias.

### <a name="properties"></a>Propriedades

* **name** – o nome interno deste campo de dados (tem de ser exclusivo)
* **kind** – o tipo de campo:
    * `Grouping` – os valores discretos utilizados para o agrupamento de campos de medida
    * `Measure` – valores de dados numéricos
    * `GroupingOrMeasure` – pode ser utilizado como um agrupamento ou medida
* **displayName** – o nome apresentado ao utilizador no painel de propriedades
* **description** – uma breve descrição do campo (opcional)
* **requiredTypes** – o tipo de dados necessário para esta função de dados. Quaisquer valores que não correspondam serão definidos como nulos (opcional)
* **preferredTypes** – o tipo de dados preferencial para esta função de dados (opcional)

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Tipos de dados válidos em "requiredTypes" e "preferredTypes"

* **bool** – um valor booleano
* **integer** – um valor de número inteiro
* **numeric** – um valor numérico
* **text** – um valor de texto
* **geography** – dados geográficos

### <a name="example"></a>Exemplo

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

As funções de dados acima iriam criar os campos seguintes

![Apresentação de funções de dados](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>Defina como pretende que os dados sejam mapeados – `dataViewMappings`

Um DataViewMapping descreve como as funções de dados se relacionam entre si e permite especificar requisitos condicionais.

A maioria dos elementos visuais fornece um mapeamento único, mas pode fornecer múltiplos dataViewMappings. Cada mapeamento válido irá produzir um DataView. 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[Saiba mais sobre DataViewMappings](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>Defina as opções do painel de propriedades – `objects`

Os objetos descrevem propriedades personalizáveis associadas ao elemento visual.
Cada objeto pode ter múltiplas propriedades e cada propriedade tem um tipo associado.
Os tipos referem qual será a propriedade. Veja abaixo para obter mais informações sobre tipos.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[Saiba mais sobre objetos](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>Processe o realce parcial – `supportsHighlight`

Por predefinição, este valor é definido como falso, o que significa que os "Valores" serão filtrados automaticamente quando for selecionado algo na página, o que irá atualizar o seu elemento visual para apresentar apenas o valor selecionado. Se quiser apresentar os dados completos, mas realçar apenas os itens selecionados, tem de definir `supportsHighlight` como verdadeiro no capabilities.json.

[Saiba mais sobre o realce](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>Processe o Modo de Edição Avançado – `advancedEditModeSupport`

Um elemento visual pode declarar o suporte do Modo de Edição Avançado.
Por predefinição, um elemento visual não suporta o Modo de Edição Avançado, a menos que indicado em contrário no capabilities.json.

[Saiba mais sobre o advancedEditModeSupport](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>Opções de ordenação de dados para o elemento visual – `sorting`

Um elemento visual pode definir o seu comportamento de ordenação através das suas capacidades.
Por predefinição, um elemento visual não suporta a modificação da sequência de ordenação, a menos que indicado em contrário no capabilities.json.

[Saiba mais sobre a ordenação](sort-options.md)
