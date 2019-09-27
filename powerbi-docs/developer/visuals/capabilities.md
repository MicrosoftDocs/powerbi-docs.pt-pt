---
title: Capacidades e propriedades dos elementos visuais do Power BI
description: Este artigo descreve as capacidades e propriedades dos elementos visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8b14568eb3a9ebc75b8d94935aedc2ae07122ef4
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193672"
---
# <a name="capabilities-and-properties-of-power-bi-visuals"></a>Capacidades e propriedades dos elementos visuais do Power BI 

Pode utilizar as capacidades para fornecer informações ao anfitrião sobre o seu elemento visual. Todas as propriedades no modelo de capacidades são `optional`.

Os objetos raiz das capacidades de um elemento visual são `dataRoles`, `dataViewMappings` e por aí adiante.

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

## <a name="define-the-data-fields-that-your-visual-expects-dataroles"></a>Defina os campos de dados esperados pelo seu elemento visual: dataRoles

Para definir os campos que podem ser associados a dados, utilize `dataRoles`. `dataRoles` utiliza uma variedade de objetos `DataViewRole`, que definem todas as propriedades necessárias.

### <a name="properties"></a>Propriedades

* **name**: o nome interno deste campo de dados (tem de ser exclusivo).
* **kind**: o tipo de campo:
    * `Grouping`: os valores discretos utilizados para agrupar campos de medida.
    * `Measure`: valores de dados numéricos.
    * `GroupingOrMeasure`: valores que podem ser utilizados como um agrupamento ou medida.
* **displayName**: o nome apresentado ao utilizador no painel **Propriedades**.
* **description**: uma breve descrição do campo (opcional).
* **requiredTypes**: o tipo de dados necessário para esta função de dados. Os valores que não corresponderem serão definidos como nulos (opcional).
* **preferredTypes**: o tipo de dados preferencial para esta função de dados (opcional).

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Tipos de dados válidos em requiredTypes e preferredTypes

* **bool**: um valor booleano
* **integer**: um valor de número inteiro
* **numeric**: um valor numérico
* **text**: Um valor de texto
* **geography**: um dado geográfico

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

As funções de dados anteriores iriam criar os campos que são apresentados na seguinte imagem:

![Campos de função de dados](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped-dataviewmappings"></a>Defina como pretende que os dados sejam mapeados: dataViewMappings

Uma propriedade DataViewMapping descreve como as funções de dados se relacionam entre si e permite especificar requisitos condicionais.

A maioria dos elementos visuais fornece um mapeamento único, mas pode fornecer múltiplos dataViewMappings. Cada mapeamento válido produz uma vista de dados. 

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

Para obter mais informações, veja [Compreender o mapeamento de vista de dados em elementos visuais do Power BI](dataview-mappings.md).

## <a name="define-property-pane-options-objects"></a>Defina as opções do painel de propriedades: objetos

Os objetos descrevem as propriedades personalizáveis associadas ao elemento visual. Cada objeto pode ter múltiplas propriedades e cada propriedade tem um tipo associado. Os tipos referem qual será a propriedade. 

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

Para obter mais informações, veja [Objetos e propriedades dos elementos visuais do Power BI](objects-properties.md).

## <a name="handle-partial-highlighting-supportshighlight"></a>Processe o realce parcial: supportsHighlight

Por predefinição, este valor é definido como `false`, o que significa que os seus valores são filtrados automaticamente quando for selecionado algo na página. Esta filtragem automática, por sua vez, atualiza o seu elemento visual para apresentar apenas o valor selecionado. Se quiser apresentar os dados completos, mas realçar apenas os itens selecionados, tem de definir `supportsHighlight` como `true` no ficheiro *capabilities.json*.

Para obter mais informações, veja [Realçar pontos de dados em elementos visuais do Power BI](highlight.md).

## <a name="handle-advanced-edit-mode-advancededitmodesupport"></a>Processe o modo de edição avançado: advancedEditModeSupport

Um elemento visual pode declarar o suporte do modo de edição avançado. Por predefinição, um elemento visual não suporta o modo de edição avançado, a menos que o contrário seja indicado no ficheiro *capabilities.json*.

Para obter mais informações, veja [Modo de edição avançado em elementos visuais do Power BI](advanced-edit-mode.md).

## <a name="data-sorting-options-for-visual-sorting"></a>Opções de ordenação de dados para o elemento visual: ordenação

Um elemento visual pode definir o seu comportamento de ordenação através das suas capacidades. Por predefinição, um elemento visual não suporta a modificação da sequência de ordenação, a menos que indicado em contrário no ficheiro *capabilities.json*.

Para obter mais informações, veja [Opções de ordenação dos elementos visuais do Power BI](sort-options.md).
