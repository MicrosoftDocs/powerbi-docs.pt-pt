---
title: A API de Filtros de Elementos Visuais do Power BI na análise incorporada do Power BI para obter melhores informações de BI incorporadas
description: Este artigo aborda como os elementos visuais do Power BI podem filtrar outros elementos visuais. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: c03c64c2835ff8bf0b0f1ad3bd555da94aaf3126
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888748"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>API de Filtros de Elementos Visuais nos Elementos Visuais do Power BI

A API de Filtros de Elementos Visuais permite-lhe filtrar dados em elementos visuais do Power BI. A principal diferença das outras seleções é que os outros elementos visuais serão filtrados de qualquer forma, apesar do suporte de destaque do outro elemento visual.

Para ativar a filtragem do elemento visual, o mesmo deve conter o objeto `filter` na secção `general` do código *capabilities.json*.

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

As interfaces da API de Filtros de Elementos Visuais estão disponíveis no pacote [powerbi-models](https://www.npmjs.com/package/powerbi-models). O pacote também contém classes para criar instâncias de filtro.

```cmd
npm install powerbi-models --save
```

Se utilizar uma versão mais antiga (anterior a 3.X.X) das ferramentas, deve incluir `powerbi-models` no pacote de elementos visuais. Para obter mais informações, veja o breve guia [Adicionar a API de Filtro Avançado ao elemento visual](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md).

Todos os filtros expandem a interface `IFilter`, conforme apresentado no seguinte código:

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Onde:
* `target` é a coluna de tabela na origem de dados.

## <a name="the-basic-filter-api"></a>API de Filtro Básico

A interface de filtro básico é apresentada no seguinte código:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Onde:
* `operator` é uma enumeração com os valores *In*, *NotIn* e *All*.
* `values` são valores da condição.

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

O filtro significa "Dê-me todas as linhas em que `col1` é igual ao valor 1, 2 ou 3".

O equivalente do SQL é:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Para criar um filtro, pode utilizar a classe BasicFilter em `powerbi-models`.

Se utilizar uma versão mais antiga da ferramenta, deverá obter uma instância de modelos no objeto de janela ao utilizar `window['powerbi-models']`, conforme apresentado no seguinte código:

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

## <a name="the-advanced-filter-api"></a>API de Filtro Avançado

A [API de Filtro Avançado](https://github.com/Microsoft/powerbi-models) permite consultas complexas de filtragem e seleção de pontos de dados entre elementos visuais com base em múltiplos critérios (tal como, *LessThan*, *Contains*, *Is*, *IsBlank*, entre outros).

O filtro foi apresentado na API de Elementos Visuais 1.7.0.

A API de Filtro Avançado também requer `target` com os nomes `table` e `column`. No entanto, os operadores da API de Filtro Avançado são *And* e *Or*. 

Além disso, o filtro utiliza condições em vez de valores com a interface:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Os operadores de condição do parâmetro `operator` são *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* e "IsNotBlank"

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

O equivalente do SQL é:

```sql
SELECT * FROM table WHERE col1 < 0;
```

Para obter o código de exemplo completo para utilizar a API de Filtro Avançado, aceda ao [repositório de elementos visuais do Sampleslicer](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="the-tuple-filter-api-multi-column-filter"></a>API de Filtro de Cadeia de Identificação (filtro de múltiplas colunas)

A API de Filtro de Cadeia de Identificação foi apresentada na API de Elementos Visuais 2.3.0. É semelhante à API de Filtro Básico, mas permite definir condições para várias colunas e tabelas.

A interface de filtro é apresentada no seguinte código: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Onde:
* `target` é uma variedade de colunas com nomes de tabela:

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  O filtro pode abordar colunas de várias tabelas.

* `$schema` é https://powerbi.com/product/schema#tuple.

* `filterType` é *FilterType.Tuple*.

* `operator` só pode ser utilizado no operador *In*.

* `values` é uma variedade de cadeias de identificação de valor e cada cadeia de identificação representa uma combinação permitida de valores de coluna de destino. 

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
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "https://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> A ordem dos nomes da coluna e valores da condição é sensível.

O equivalente do SQL é:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>Restaurar o filtro JSON a partir da vista de dados

A partir da versão 2.2.0 da API, pode restaurar o filtro JSON a partir de *VisualUpdateOptions*, conforme apresentado no seguinte código:

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

Quando muda de marcadores, o Power BI chama o método `update` do elemento visual e o elemento visual obtém o objeto `filter` correspondente. Para obter mais informações, veja [Adicionar suporte de marcadores para elementos visuais do Power BI](bookmarks-support.md).

### <a name="sample-json-filter"></a>Filtro JSON de exemplo

Algum código de filtro JSON de exemplo é apresentado na seguinte imagem:

![Código de filtro JSON](media/filter-api/json-filter.png)

### <a name="clear-the-json-filter"></a>Limpar o filtro JSON

A API de Filtro aceita o valor `null` do filtro como *redefinido* ou *limpo*.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
