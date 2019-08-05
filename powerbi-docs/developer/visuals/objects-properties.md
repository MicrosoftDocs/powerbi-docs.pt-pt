---
title: Objeto e propriedades
description: Propriedades personalizáveis dos elementos visuais do Power BI
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424614"
---
# <a name="object-and-properties"></a>Objeto e propriedades

Os objetos descrevem propriedades personalizáveis associadas ao elemento visual.
Cada objeto pode ter múltiplas propriedades e cada propriedade tem um tipo associado.
Os tipos referem qual será a propriedade. Veja abaixo para obter mais informações sobre tipos.

`myCustomObject` é o nome interno utilizado para fazer referência ao objeto dentro de `dataView` e `enumerateObjectInstances`.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Nome a Apresentar

`displayName` é o nome que será apresentado no painel de propriedades.

## <a name="properties"></a>Propriedades

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
Eis alguns dos `ValueTypeDescriptor` comuns.

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Descritor do tipo estrutural

`StructuralTypeDescriptor` são maioritariamente utilizados para objetos vinculados por dados.
"Fill" é o `StructuralTypeDescriptor` mais comum.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Propriedade "gradient"

A propriedade "gradient" é uma propriedade que não se pode definir como propriedade padrão. Em vez disso, tem de definir uma regra para substituir a propriedade do selecionador de cores (tipo "fill").
Veja o exemplo abaixo.

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

Preste atenção às propriedades `"fill"` e `"fillRule"`. A primeira corresponde ao selecionador de cores e a segunda é a regra de substituição de "gradient" que substituirá `visually` a propriedade "fill" quando se cumprirem as condições da regra.

Esta ligação entre a propriedade "fill" e a regra de substituição é definida na secção `"rule"`->`"output"` da propriedade `"fillRule"`.

`"Rule"`->`"InputRole"` define a função de dados que aciona a regra (condição). Neste exemplo, se a função de dados `"Gradient"` contiver dados, a regra será aplicada para a propriedade `"fill"`.

Abaixo, pode ver um exemplo da função de dados que aciona a regra de preenchimento (`the last item`).

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

## <a name="enumerateobjectinstances-method"></a>Método `enumerateObjectInstances`

Para utilizar objetos eficazmente, precisará de uma função no seu elemento visual personalizado chamada `enumerateObjectInstances`. Esta função preencherá o painel de propriedades com objetos e também determinará onde os objetos devem estar vinculados em DataView.  

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

### <a name="properties"></a>Propriedades

As propriedades em `enumerateObjectInstances` refletirão as propriedades que definiu nas suas capacidades. Veja o exemplo situado na parte inferior da página.

### <a name="objects-selector"></a>Seletor de objetos

O seletor em `enumerateObjectInstances` determina onde cada objeto será vinculado em DataView. Há quatro opções distintas.

#### <a name="static"></a>static

Este objeto estará vinculado aos metadados `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>colunas

Este objeto estará vinculado a colunas com o `QueryName` correspondente.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Este objeto estará vinculado ao elemento para o qual criamos um `selectionID`. Neste exemplo, vamos pressupor que criámos `selectionID` para alguns dataPoints e que estamos a explorá-los.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Scope identity

Este objeto estará vinculado a valores específicos na interseção de grupos. Por exemplo, se eu tiver as categorias `["Jan", "Feb", "March", ...]` e as séries `["Small", "Medium", "Large"]`, poderei querer ter um objeto na interseção dos valores que correspondem a `Feb` e `Large`. Para tal, poderia obter `DataViewScopeIdentity` das duas colunas, emiti-las para a variável `identities` e utilizar esta sintaxe com o seletor.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Exemplo

Neste exemplo, mostramos a que se assemelharia objectEnumeration para um objeto customColor com uma propriedade `fill`. Queremos que este objeto esteja vinculado estaticamente a `dataViews[index].metadata.objects`.

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
