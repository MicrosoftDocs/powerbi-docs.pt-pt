---
title: Utilitários de interações visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: O artigo descreve como adicionar seleções em elementos visuais do Power BI com utilitários de interatividade. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: 533cf90ed9192a8d9e595cdea6320207b841b559
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887782"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Utilitários de interatividade dos elementos visuais do Power BI

Os utilitários de interatividade (`InteractivityUtils`) são um conjunto de funções e classes que pode ser utilizado para simplificar a implementação de seleção e filtragem cruzadas.

> [!NOTE]
> As novas atualizações dos utilitários de interatividade apenas suportam a versão mais recente das ferramentas (3.x.x e superior).

## <a name="installation"></a>Instalação

1. Para instalar o pacote, execute o seguinte comando no diretório com o atual projeto visual do Power BI.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Se estiver a utilizar a versão 3.0 ou posterior da ferramenta, instale os `powerbi-models` para resolver as dependências.

    ```bash
    npm install powerbi-models --save
    ```

3. Para utilizar os utilitários de interatividade, importe o componente necessário no código-fonte do elemento visual do Power BI.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Incluir ficheiros CSS

Para utilizar o pacote com o elemento visual do Power BI, importe o seguinte ficheiro CSS para o ficheiro `.less`.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importe o ficheiro CSS como ficheiro `.less`, pois a ferramenta de elementos visuais do Power BI encapsula as regras CSS externas.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>Propriedades SelectableDataPoint

Geralmente, os pontos de dados contêm seleções e valores. A interface expande a interface `SelectableDataPoint`.

`SelectableDataPoint` já contém propriedades conforme descrito abaixo.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Definir uma interface dos pontos de dados

1. Crie uma instância dos utilitários de interatividade e guarde o objeto como propriedade do elemento visual.

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

2. Expanda a classe de comportamento base.

    > [!NOTE]
    > A classe `BaseBehavior` foi introduzida na [versão 5.6.x dos utilitários de interatividade](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Se estiver a utilizar uma versão mais antiga, crie uma classe de comportamento a partir do exemplo abaixo.

3. Defina a interface das opções da classe de comportamento.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Defina a classe de `visual behavior`. Em alternativa, expanda a classe `BaseBehavior`.

    **Definir uma classe para `visual behavior`**

    A classe é responsável por processar os eventos do rato `click` `contextmenu`.

    Quando um utilizador clica nos elementos de dados, o elemento visual chama o processador de seleção para selecionar os pontos de dados. Se o utilizador clicar no componente de fundo do elemento visual, este chama o processador de limpeza da seleção.

    A classe tem os seguintes métodos correspondentes:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
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

    **Expandir a classe `BaseBehavior`**

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

5. Para processar os cliques nos elementos, chame o método *do objeto de seleção* d3`on`, o que também se aplica a `elementsSelection` e `clearCatcherSelection`.

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

6. Adicione um processador semelhante para o evento `contextmenu`, para chamar o método `showContextMenu` do gestor de seleção.

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

7. Para atribuir funções a processadores, os utilitários de interatividade chamam o método `bindEvents`. Adicione as seguintes chamadas ao método `bindEvents`:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

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

8. O método `renderSelection` é responsável pela atualização do estado visual dos elementos no gráfico. Veja a seguir um exemplo de implementação de `renderSelection`.

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

9. O último passo é a criação de uma instância de `visual behavior` e a chamada do método `bind` da instância de utilitários de interatividade.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` é o objeto de seleção *d3*, que representa todos os elementos selecionáveis dos elementos visuais.
    * `select(this.target)` é o objeto de seleção *d3*, que representa todos os elementos DOM principais dos elementos visuais.
    * As instâncias `this.categories` são pontos de dados com elementos em que a interface é `VisualDataPoint` ou `categories: VisualDataPoint[];`.
    * `this.behavior` é uma nova instância de `visual behavior` criada no construtor do elemento visual, conforme mostrado abaixo.

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
## <a name="next-steps"></a>Passos seguintes

* [Saiba como processar seleções em mudanças de marcadores](bookmarks-support.md#visuals-with-selection)

* [Saiba como adicionar o menu de contexto para pontos de dados de elementos visuais](context-menu.md)

* [Saiba como utilizar o gestor de seleção para adicionar seleções nos Elementos Visuais do Power BI](selection-api.md)
