---
title: Obter mais dados do Power BI
description: Este artigo aborda a forma de ativar a obtenção segmentada de conjuntos de dados de grandes dimensões dos elementos visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: b8be5b68603f818e26e7f731e4f163bc626b5053
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483702"
---
# <a name="fetch-more-data-from-power-bi"></a>Obter mais dados do Power BI

Este artigo aborda como carregar mais dados de modo a contornar o limite restritivo de um ponto de dados de 30 KB com o método `fetchMoreData`. Esta abordagem fornece dados em segmentos. Para melhorar o desempenho, pode configurar o tamanho dos segmentos para acomodar o caso de utilização.

## <a name="limitations-of-fetchmoredata"></a>Limitações do método fetchMoreData

* O tamanho da janela é limitado a um intervalo de 2 a 30 000.
* O número de linhas do total do DataView está limitado a 1 048 576 linhas.
* No modo de agregação de segmentos, o tamanho da memória do DataView é limitado a 100 MB.

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Ativar uma obtenção segmentada de conjuntos de dados grandes

Para o modo de segmento `dataview`, irá definir um tamanho de janela para `dataReductionAlgorithm` no ficheiro *capabilities.json* do elemento visual para o `dataViewMapping` necessário. A `count` determina o tamanho da janela, o que limita o número de novas linhas de dados que podem ser anexadas à `dataview` em cada atualização.

Adicione o seguinte código ao ficheiro *capabilities.json*:

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

São anexados ao `dataview` existente novos segmentos, que são depois fornecidos ao elemento visual como uma chamada `update`.

## <a name="usage-in-the-power-bi-visual"></a>Utilização no elemento visual do Power BI

No Power BI, pode utilizar `fetchMoreData` no modo de agregação de segmentos predefinido ou no modo de atualizações incrementais. 

### <a name="using-segments-aggregation-mode-default"></a>Utilizar o modo de agregação de segmentos (predefinição)

Com este modo, o DataView fornecido ao elemento visual contém os dados acumulados para todos os `fetchMoreData requests` anteriores. Portanto, espera-se que o tamanho do DataView aumente a cada atualização. Por exemplo, se for esperado um total de 100 000 linhas e o tamanho da janela estiver definido para 10 000, a primeira atualização ao DataView deve incluir 10 000 linhas, a segunda atualização ao DataView deve incluir 20 000 linhas e assim sucessivamente.

Este modo é selecionado ao chamar `fetchMoreData` com `aggregateSegments = true`.

Pode determinar se existem dados ao verificar a existência de `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Também é possível verificar se é a primeira atualização ou uma atualização subsequente, ao verificar `options.operationKind`. No seguinte código, `VisualDataChangeOperationKind.Create` refere-se ao primeiro segmento e `VisualDataChangeOperationKind.Append` aos segmentos subsequentes.

Para obter um exemplo de implementação, veja o fragmento de código abaixo:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Também pode invocar o método `fetchMoreData` de um processador de eventos de interface de utilizador, como mostrado aqui:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Como resposta à chamada do método `this.host.fetchMoreData`, o Power BI chama o método `update` do elemento visual com um novo segmento de dados.

> [!NOTE]
> Para evitar restrições da memória do cliente, de momento, o Power BI limita o total de dados obtidos a 100 MB. Pode ver que o limite foi atingido quando `fetchMoreData()` devolve `false`.

### <a name="using-incremental-updates-mode"></a>Utilizar o modo de atualizações incrementais

Com este modo, o DataView fornecido ao elemento visual contém apenas dados incrementais. Assim, o tamanho do DataView não ultrapassaria o tamanho da janela definido. Por exemplo, se for esperado um total de 101 000 linhas e o tamanho da janela estiver definido para 10 000, o elemento visual obterá 10 atualizações com um tamanho de DataView de 10 000 e uma atualização com um tamanho de DataView de 1000.

Este modo é selecionado ao chamar `fetchMoreData` com `aggregateSegments = false`.

Pode determinar se existem dados ao verificar a existência de `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Também é possível verificar se é a primeira atualização ou uma atualização subsequente, ao verificar `options.operationKind`. No seguinte código, `VisualDataChangeOperationKind.Create` refere-se ao primeiro segmento e `VisualDataChangeOperationKind.Segment` aos segmentos subsequentes.

Para obter um exemplo de implementação, veja o fragmento de código abaixo:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

Também pode invocar o método `fetchMoreData` de um processador de eventos de interface de utilizador, como mostrado aqui:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Como resposta à chamada do método `this.host.fetchMoreData`, o Power BI chama o método `update` do elemento visual com um novo segmento de dados.

> [!NOTE]
> Apesar de os dados dos DataViews entre as diferentes atualizações serem maioritariamente exclusivos, haverá alguma sobreposição entre os DataViews subsequentes.
> Para o mapeamento de dados categóricos e de tabela, espera-se que as primeiras N linhas do DataView contenham dados copiados do DataView anterior.
> N pode ser determinado por: `(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`