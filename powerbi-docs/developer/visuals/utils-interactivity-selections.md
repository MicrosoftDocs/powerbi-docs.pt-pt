---
title: Utilitários de interatividade dos elementos visuais do Power BI
description: O artigo descreve como adicionar seleções em elementos visuais do Power BI com utilitários de interatividade
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818692"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Utilitários de interatividade dos elementos visuais do Microsoft Power BI

O InteractivityUtils é um conjunto de funções e classes para simplificar a implementação de seleção e filtragem cruzadas para os elementos visuais personalizados do Power BI.

## <a name="installation"></a>Instalação

> [!NOTE]
> Se continuar a utilizar a versão antiga do powerbi-visuals-tools (número de versão inferior a 3.X.X), instale a nova versão da ferramenta (3.X.X).

> [!IMPORTANT]
> As novas atualizações dos utilitários de interatividade apenas suportarão a versão mais recente das ferramentas. [Saiba mais sobre como atualizar o código dos elementos visuais para utilização com as ferramentas mais recentes](migrate-to-new-tools.md)

Para instalar o pacote, deve executar o seguinte comando no diretório com os elementos visuais personalizados atuais:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

Na versão 3.0 ou posterior, também precisa de instalar ```powerbi-models``` para resolver as dependências.

```bash
npm install powerbi-models --save
```

Para os utilitários de interatividade do utilizador, precisa de importar o componente necessário no código-fonte do elemento visual.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>Incluir artefactos CSS no elemento visual personalizado

Para utilizar o pacote com os elementos visuais personalizados, deve importar o seguinte ficheiro CSS para o ficheiro `your.less`:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Como resultado, terá a seguinte estrutura de ficheiros:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Deve importar os ficheiros .css como ficheiros .less porque as Ferramentas de Elementos Visuais do Power BI encapsulam as regras CSS externas.

## <a name="usage"></a>Usage

### <a name="define-interface-for-data-points"></a>Definir a interface dos pontos de dados

Geralmente, os pontos de dados contêm seleções e valores. A interface estende a interface `SelectableDataPoint`. `SelectableDataPoint` já contém propriedades:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

O primeiro passo da utilização dos utilitários de interatividade é criar uma instância de utilitários de interatividade e guardar o objeto como uma propriedade do elemento visual

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

O segundo passo é estender a classe de comportamento base:

> [!NOTE]
> BaseBehavior, introduzido na [versão 5.6.x dos utilitários de interatividade](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Se utilizar a versão antiga, crie a classe de comportamento a partir do exemplo abaixo (a classe `BaseBehavior` é igual):

Defina a interface das opções da classe de comportamento:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Defina a classe de `visual behavior`. A classe é responsável por processar os eventos do rato `click` e `contextmenu`.
Quando um utilizador clica em elementos de dados, o elemento visual chama o processador de seleção para selecionar os pontos de dados. Se o utilizador clicar no componente de fundo do elemento visual, este chama o processador de limpeza da seleção. A classe tem os métodos correspondentes: `bindClick`, `bindClearCatcher` e `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

Pode também estender a classe `BaseBehavior`:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Para processar o clique nos elementos, chame o método `on` do objeto de seleção D3 (também para elementsSelection e clearCatcherSelectionh):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Adicione o processador semelhante para o evento `contextmenu` chamar o método `showContextMenu` do gestor de seleção:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

Os utilitários de interatividade chamam os métodos `bindEvents` para atribuir funções a processadores, adicionar chamadas de `bindClick`, `bindClearCatcher` e `bindContextMenu` no método `bindEvents`:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

O método `renderSelection` é responsável pela atualização do estado visual dos elementos no gráfico.

Exemplo do método `renderSelection` de implementação:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

O último passo é a criação de uma instância de `visual behavior` e a chamada do método `bind` da instância de utilitários de interatividade:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` é o objeto de seleção D3, que representa todos os elementos selecionáveis no elemento visual.

* `select(this.target)` é o objeto de seleção D3, que representa todos os elementos DOM principais selecionáveis do elemento visual.

* As instâncias `this.categories` são pontos de dados com elementos em que a interface é `VisualDataPoint` (ou `categories: VisualDataPoint[];`)

* `this.behavior` é uma nova instância de `visual behavior`

  criada no construtor do elemento visual:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

Agora, o elemento visual está pronto para processar a seleção.

## <a name="next-steps"></a>Próximos passos

* [Leia como lidar com seleções na alternância de marcadores](bookmarks-support.md#visuals-with-selection)

* [Saiba como adicionar o menu de contexto para pontos de dados de elementos visuais](context-menu.md)

* [Saiba como utilizar o gestor de seleção para adicionar seleções nos Elementos Visuais do Power BI](selection-api.md)
