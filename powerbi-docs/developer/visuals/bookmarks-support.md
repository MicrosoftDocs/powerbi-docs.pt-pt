---
title: Marcadores
description: Os elementos visuais do Power BI suportam a mudança de marcadores
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425511"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Adicionar suporte de marcadores para elementos visuais do Power BI

Os marcadores de relatório do Power BI permitem captar a vista configurada de uma página de relatório, estado de seleção e estado de filtragem do elemento visual. Contudo, isso requer a realização de ações adicionais do lado dos elementos visuais personalizados para suportar o marcador e reagir corretamente às alterações.

Leia mais sobre marcadores na [documentação](https://docs.microsoft.com/power-bi/desktop-bookmarks).

## <a name="report-bookmarks-support-in-your-visual"></a>Suporte de marcadores de relatório no seu elemento visual

Se o seu elemento visual interagir com outros elementos visuais, selecionar pontos de dados ou filtrar outros elementos visuais, tem de restaurar o estado a partir das propriedades.

## <a name="how-to-add-report-bookmarks-support"></a>Como adicionar suporte de marcadores de relatório

1. Instale (ou atualize) o utilitário necessário: `powerbi-visuals-utils-interactivityutils`(https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) versão 3.0.0 ou posterior. Contém classes adicionais para manipular com a seleção do estado ou o filtro. É necessário para filtrar elementos visuais e qualquer elemento visual que utilize o `InteractivityService`.

2. Atualize a API do elemento visual para 1.11.0 para utilizar `registerOnSelectCallback` na instância do `SelectionManager`. É necessário para elementos visuais sem filtro que utilizam o `SelectionManager` simples em vez do `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Como os elementos visuais personalizados interagem com o Power BI no cenário de marcadores de relatório

Considere o seguinte exemplo: um utilizador cria vários marcadores na página de relatório com um estado de seleção diferente em cada marcador.

Primeiro, o utilizador seleciona um ponto de dados no elemento visual. O elemento visual interage com o Power BI e com outros elementos visuais ao transmitir as seleções para o anfitrião. Em seguida, o utilizador seleciona "Adicionar" no `Bookmark panel` e o Power BI guarda as seleções atuais do novo marcador.

Isto acontece repetidamente à medida que o utilizador altera a seleção e adiciona novos marcadores.
Uma vez criados, o utilizador pode alternar entre os marcadores.

Quando os utilizadores selecionam um marcador, o Power BI restaura o filtro ou estado de seleção guardado e transmite-o aos elementos visuais. Serão realçados ou filtrados outros elementos visuais de acordo com o estado armazenado no marcador. O anfitrião do Power BI é responsável pelas ações. O elemento visual é responsável por refletir corretamente o novo estado de seleção (por exemplo, por alterar a cor dos pontos de dados compostos).

O novo estado de seleção é comunicado ao elemento visual através do método `update`. O argumento `options` conterá uma propriedade especial: `options.jsonFilters`. A sua propriedade JSONFilter pode conter `Advanced Filter` e `Tuple Filter`.

O elemento visual deve restaurar valores de filtros para apresentar o estado correspondente do elemento visual do marcador selecionado.

Em alternativa, se o elemento visual só utilizar seleções, utilize a chamada da função de chamada de retorno especial registada no método `registerOnSelectCallback` do ISelectionManager.

### <a name="visuals-with-selections"></a>Elementos visuais com seleções

Se os seus elementos visuais interagirem com outros elementos visuais através de [seleções](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), tem duas formas de adicionar marcadores.

* Pode utilizar o método `FilterManager.restoreSelectionIds` se não **tiver utilizado o [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** anteriormente no seu elemento visual.

* Se o seu elemento visual já utilizar **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** para gerir seleções, deve utilizar o método `applySelectionFromFilter` na instância do `InteractivityService`.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Utilizar `ISelectionManager.registerOnSelectCallback`

Quando um utilizador clica em marcadores, o Power BI chama o método `callback` do elemento visual com seleções correspondentes. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Vamos supor que tem um ponto de dados no seu elemento visual criado no método [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

Suponhamos também que `datapoints` se assemelha ao seguinte:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Portanto, tem `visualDataPoints` como pontos de dados e uma matriz `ids` transmitida para a função `callback`.

Nesta fase, o elemento visual deverá comparar a matriz de `ISelectionId[]` com as seleções na sua matriz `visualDataPoints` e marcar os pontos de dados correspondentes como selecionados.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Depois de atualizar os pontos de dados, estes refletirão o estado de seleção atual armazenado no objeto `filter`. Em seguida, quando os pontos de dados forem compostos, o estado de seleção do elemento visual personalizado corresponderá ao estado do marcador.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>Utilizar `InteractivityService` para seleções de controlo no elemento visual

Se o seu elemento visual utilizar `InteractivityService`, não precisa de realizar ações adicionais para suportar marcadores no seu elemento visual.

O utilitário processará o estado de seleção do elemento visual quando o utilizador selecionar marcadores.

### <a name="visuals-with-filter"></a>Elementos visuais com filtro

Vamos supor que o elemento visual cria um filtro de dados por intervalo de datas. Desta forma, temos `startDate` e `endDate` como início e fim do intervalo.
O elemento visual cria um filtro avançado e chama o método `applyJsonFilter` do anfitrião para filtrar dados de acordo com as condições relevantes.
`target` é a tabela para filtrar.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Cada vez que um utilizador clica num marcador, o elemento visual personalizado obtém uma chamada `update`.

O elemento visual personalizado deve verificar o filtro no objeto.

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Se o objeto `filter` não for nulo, o elemento visual deverá restaurar as condições de filtro do objeto.

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Depois disso, o elemento visual deve alterar o seu estado interno (pontos de dados e objetos de visualização como linhas, retângulos, etc.) para refletir as condições atuais.

> [!IMPORTANT]
> No cenário dos marcadores de relatório, o elemento visual não deve chamar `applyJsonFilter` para filtrar outros elementos visuais porque estes já terão sido filtrados pelo Power BI.

O elemento visual da Segmentação de Dados de Linha Cronológica altera o seletor de intervalo para fazer corresponder os intervalos de dados.

Para obter mais informações, veja o [repositório da Segmentação de Dados de Linha Cronológica](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Estado do filtro para guardar propriedades de elementos visuais em marcadores

A propriedade `filterState` transforma parte da filtragem numa propriedade. O elemento visual pode armazenar diferentes valores em marcadores.

Para guardar o valor da propriedade como estado do filtro, a propriedade do objeto deve estar marcada como `"filterState": true` em `capabilities.json`.

Exemplo: `Timeline Slicer` armazena valores da propriedade `Granularity` no filtro. Além disso, permite alterar a granularidade atual quando o utilizador muda de marcadores.

Para obter mais informações, veja o [repositório da Segmentação de Dados de Linha Cronológica](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
