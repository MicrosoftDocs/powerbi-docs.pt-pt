---
title: Objetos e propriedades dos elementos visuais do Power BI
description: Este artigo descreve as propriedades personalizáveis dos elementos visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ae548abd0d579414a69b0d970213ff9d69ff2f08
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96120211"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Objetos e propriedades dos elementos visuais do Power BI

Os objetos descrevem as propriedades personalizáveis associadas a um elemento visual. Um objeto pode ter múltiplas propriedades e cada propriedade tem um tipo associado que descreve o que será a propriedade. Este artigo fornece informações sobre objetos e tipos de propriedade.

`myCustomObject` é o nome interno utilizado para fazer referência ao objeto dentro de `dataView` e `enumerateObjectInstances`.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Nome a apresentar

`displayName` é o nome que será apresentado no painel de propriedades.

## <a name="properties"></a>Properties

`properties` é um mapa das propriedades definidas pelo programador.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` é uma propriedade especial que permite que um botão ative/desative o objeto.

Por exemplo:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Tipo de propriedade

Há dois tipos de propriedade: `ValueTypeDescriptor` e `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Descritor do tipo de valor

`ValueTypeDescriptor` são, na grande maioria, tipos primitivos e normalmente utilizados como objeto estático.

Eis alguns dos elementos comuns `ValueTypeDescriptor`:

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Descritor do tipo estrutural

`StructuralTypeDescriptor` são, na grande maioria, tipos utilizados para objetos vinculados por dados.
O tipo `StructuralTypeDescriptor` mais comum é *fill*.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Propriedade "gradient"

A propriedade "gradient" não se pode definir como propriedade padrão. Em vez disso, tem de definir uma regra para substituir a propriedade do seletor de cores (tipo *fill*).

É apresentado um exemplo no seguinte código:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Preste atenção às propriedades *fill* e *fillRule*. A primeira corresponde ao seletor de cores e a segunda é a regra de substituição de "gradient" que substituirá a *propriedade fill*, `visually`, quando se cumprirem as condições da regra.

Esta ligação entre a propriedade *fill* e a regra de substituição é definida na secção `"rule"`>`"output"` da propriedade *fillRule*.

A propriedade `"Rule"`>`"InputRole"` define a função de dados que aciona a regra (condição). Neste exemplo, se a função de dados `"Gradient"` contiver dados, a regra será aplicada à propriedade `"fill"`.

No seguinte código, é apresentado um exemplo da função de dados que aciona a regra de preenchimento (`the last item`):

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>Método enumerateObjectInstances

Para utilizar objetos eficazmente, precisa de uma função no seu elemento visual personalizado chamada `enumerateObjectInstances`. Esta função preenche o painel de propriedades com objetos e também determina onde os objetos devem estar vinculados em DataView.  

Uma configuração típica assemelha-se ao seguinte.

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Properties

As propriedades em `enumerateObjectInstances` refletem as propriedades que definiu nas suas capacidades. Para obter um exemplo, vá para o final deste artigo.

### <a name="objects-selector"></a>Seletor de objetos

O seletor em `enumerateObjectInstances` determina onde cada objeto será vinculado em DataView. Há quatro opções distintas.

#### <a name="static"></a>static

Este objeto está vinculado a metadados `dataviews[index].metadata.objects`, conforme apresentado aqui.

```typescript
selector: null
```

#### <a name="columns"></a>colunas

Este objeto está vinculado a colunas com o `QueryName` correspondente.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Este objeto está vinculado ao elemento para o qual criou um `selectionID`. Neste exemplo, vamos pressupor que criámos `selectionID` para alguns pontos de dados e que estamos a explorá-los.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Scope identity

Este objeto está vinculado a valores específicos na interseção de grupos. Por exemplo, se tiver as categorias `["Jan", "Feb", "March", ...]` e as séries `["Small", "Medium", "Large"]`, poderá querer ter um objeto na interseção dos valores que correspondem a `Feb` e `Large`. Para tal, poderia obter `DataViewScopeIdentity` das duas colunas, emiti-las para a variável `identities` e utilizar esta sintaxe com o seletor.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Exemplo

O seguinte exemplo mostra a que se assemelharia objectEnumeration para um objeto customColor com uma propriedade *fill*. Queremos que este objeto esteja vinculado estaticamente a `dataViews[index].metadata.objects`, conforme apresentado:

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
