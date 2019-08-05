---
title: Fetch more data (Obter mais dados)
description: Ativar a obtenção segmentada de conjuntos de dados grandes para elementos visuais do Power BI
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425074"
---
# <a name="fetch-more-data-from-power-bi"></a>Obter mais dados do Power BI

O carregamento de mais API de dados ultrapassa o limite restritivo de 30 000 pontos de dados. Permite obter dados em segmentos. O tamanho dos segmentos é configurável para melhorar o desempenho de acordo com o caso de utilização.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Ativar a obtenção segmentada de conjuntos de dados grandes

No caso do modo de segmento `dataview`, defina um dataReductionAlgorithm tipo "window" em `capabilities.json` do elemento visual para o dataViewMapping necessário.
A `count` determinará o tamanho da janela, o que limita o número de novas linhas de dados que são anexadas a `dataview` em cada atualização.

A adicionar em capabilities.json

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

## <a name="usage-in-the-custom-visual"></a>Utilização no elemento visual personalizado

É possível determinar a indicação de que existem dados ou não podem ao verificar a existência de `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Também é possível verificar se é a primeira atualização ou a atualização subsequente ao verificar `options.operationKind`.

`VisualDataChangeOperationKind.Create` significa que é primeiro segmento e `VisualDataChangeOperationKind.Append` significa que se trata de segmentos subsequentes.

Veja o fragmento de código abaixo para obter um exemplo de implementação:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

O método `fetchMoreData` também poderia ser invocado a partir de um processador de eventos de interface de utilizador.

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

O Power BI chamará o método `update` do elemento visual com o novo segmento de dados como resposta à chamada do método `this.host.fetchMoreData`.

> [!NOTE]
> De momento, o Power BI limitará o total de dados obtidos a **100 MB** para evitar restrições da memória do cliente. Pode detetar que este limite está a ser alcançado quando fetchMoreData() devolver "false".*
