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
ms.openlocfilehash: 6d51a27bc5c0f18b7f784395dedd58813bfffbc0
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380692"
---
# <a name="fetch-more-data-from-power-bi"></a>Obter mais dados do Power BI

Este artigo aborda a forma de carregar mais dados de modo a contornar o limite restritivo de um ponto de dados de 30 KB. Esta abordagem fornece dados em segmentos. Para melhorar o desempenho, pode configurar o tamanho dos segmentos para acomodar o caso de utilização.  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Ativar uma obtenção segmentada de conjuntos de dados grandes

No caso do modo de segmento `dataview`, defina um tamanho da janela do dataReductionAlgorithm no ficheiro *capabilities.json* do elemento visual para o dataViewMapping necessário. A `count` determina o tamanho da janela, o que limita o número de novas linhas de dados que podem ser anexadas à `dataview` em cada atualização.

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
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Como resposta à chamada do método `this.host.fetchMoreData`, o Power BI chama o método `update` do elemento visual com um novo segmento de dados.

> [!NOTE]
> Para evitar restrições da memória do cliente, de momento, o Power BI limita o total de dados obtidos a 100 MB. Pode ver que o limite foi atingido quando o fetchMoreData() devolve `false`.
