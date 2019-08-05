---
title: API de Filtros de Elementos Visuais
description: Como os Elementos Visuais do Power BI podem filtrar outros elementos visuais
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425051"
---
# <a name="power-bi-visual-filters-api"></a>API de Filtros de Elementos Visuais do Power BI

A filtragem de elementos visuais permite a filtragem de dados. A principal diferença das seleções é que os outros elementos visuais serão filtrados de qualquer forma, apesar do suporte de destaque do outro elemento visual.

Para ativar a filtragem do elemento visual, o mesmo deve conter o objeto `filter` na secção `general` do conteúdo de capabilities.json.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

As interfaces de API de filtro estão disponíveis no pacote [`powerbi-models`](https://www.npmjs.com/package/powerbi-models). O pacote também contém classes para criar instâncias de filtro.

```cmd
npm install powerbi-models --save
```

Se utilizar ferramentas com versões antigas (versão inferior a 3.X.X), deve incluir `powerbi-models` no pacote do elemento visual. [Breve guia sobre como incluir o pacote](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Todos os filtros expandem a interface `IFilter`.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` – é uma coluna de tabela na origem de dados.

## <a name="basic-filter-api"></a>API de filtro básico

A interface de filtro básico é

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` – é uma enumeração com os valores "In", "NotIn", "All"

`values` – são valores da condição

Exemplo de filtro básico:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

O filtro significa "dê-me todas as linhas em que `col1` é igual a um dos valores 1, 2 ou 3".

O equivalente do SQL é

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Para criar um filtro, pode utilizar a classe BasicFilter em `powerbi-models`.

Se utilizar a versão antiga das ferramentas, deve obter uma instância dos modelos no objeto de janela por `window['powerbi-models']`:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

O elemento visual invoca o filtro com o método applyJsonFilter() na interface de anfitrião IVisualHost fornecida ao elemento visual no construtor.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>API de filtro avançado

A [API de Filtro Avançado](https://github.com/Microsoft/powerbi-models) permite consultas complexas de filtragem/seleção de pontos de dados entre elementos visuais com base em múltiplos critérios (tal como, "LessThan", "Contains", "Is", "IsBlank", entre outros).

O filtro foi apresentado na API de Elementos Visuais 1.7.0.

A API de Filtro Avançado também requer `target` com os nomes `table` e `column`. No entanto, os operadores da API de Filtro Avançado são `"And" | "Or"`. 

Além disso, o filtro utiliza condições em vez de valores com interface:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Os operadores de condição do parâmetro `operator` são `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

O equivalente do SQL é

```sql
SELECT * FROM table WHERE col1 < 0;
```

Pode encontrar o código de exemplo completo para utilizar a API de Filtro Avançado no [repositório](https://github.com/Microsoft/powerbi-visuals-sampleslicer) `Sampleslicer visual`.

## <a name="tuple-filter-api-multi-column-filter"></a>API de filtro de cadeia de identificação (filtro de múltiplas colunas)

A API de Filtro de Cadeia de Identificação foi apresentada na API de Elementos Visuais 2.3.0.

A API de filtro de cadeia de identificação é semelhante ao filtro básico, mas permite definir condições para várias colunas e tabelas.

Um filtro tem uma interface: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` é uma variedade de colunas com nomes de tabela:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  O filtro pode abordar colunas de tabelas diferentes.

`$schema` é "http://powerbi.com/product/schema#tuple"

`filterType` é `FilterType.Tuple`

`operator` apenas permite utilizar o operador `"In"`

`values` é uma variedade de cadeias de identificação de valor, em que cada cadeia de identificação representa uma combinação permitida de valores de coluna de destino 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Exemplo completo:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**A ordem dos nomes da coluna e os valores da condição são confidenciais.**

O equivalente do SQL é

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>Restaurar o Filtro JSON a partir de DataView

A partir da API 2.2, os **Filtros JSON** podem ser restaurados a partir de **VisualUpdateOptions**

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

O Power BI chama o método `update` do elemento visual quando utiliza marcadores de mudança e o elemento visual obtém o objeto `filter` correspondente.
[Leia mais sobre o suporte de marcadores](bookmarks-support.md)

### <a name="sample-json-filter"></a>Filtro JSON de Exemplo

![Captura de ecrã a mostrar o Filtro JSON](./media/json-filter.png)

### <a name="clear-json-filter"></a>Limpar o Filtro JSON

A API de filtro aceita o valor `null` do filtro como redefinido ou limpo.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
