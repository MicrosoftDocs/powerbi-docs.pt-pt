---
title: Introdução à utilização de utilitários de teste em elementos visuais do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo descreve como utilizar utilitários de teste para simplificar simulações e métodos específicos em testes de unidades para elementos visuais do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 4b2a846f4905c4cb28fe92043cf3c71750b40f11
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888058"
---
# <a name="power-bi-visuals-test-utils"></a>Utilitários de teste de elementos visuais do Power BI

Este artigo ajuda-o a instalar, importar e utilizar os utilitários de teste de elementos visuais do Power BI. Estes utilitários de teste podem ser utilizados para testes de unidades e incluem simulações e métodos para elementos como vistas de dados, seleções e esquemas de cores.

## <a name="requirements"></a>Requisitos

Para utilizar este pacote, terá de instalar o seguinte:

* [Node.js](https://nodejs.org) (recomenda-se utilizar a versão LTS)
* [npm](https://www.npmjs.com/), versão 3.0.0 ou superior
* O pacote [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)

## <a name="installation"></a>Instalação

Para instalar os utilitários de teste e adicionar a respetiva dependência ao *package.json*, execute o seguinte comando no diretório de elementos visuais do Power BI:

```bash
npm install powerbi-visuals-utils-testutils --save
```

Seguem-se descrições e exemplos sobre a API pública de utilitários de teste.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Utilizada pelo **VisualBuilder** em testes de unidades com os métodos mais utilizados: `build`, `update` e `updateRenderTimeout`. 

O método `build` devolve uma instância criada do elemento visual.

Os métodos `enumerateObjectInstances` e `updateEnumerateObjectInstancesRenderTimeout` são necessários para verificar alterações no registo e nas opções de formatação.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Para obter mais exemplos, saiba como [escrever testes de unidades da VisualBuilderBase](./unit-tests-introduction.md#create-a-visual-instance-builder) e veja um [cenário de utilização real da VisualBuilderBase](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Utilizado pelo **TestDataViewBuilder**, este módulo fornece uma classe **CategoricalDataViewBuilder** utilizada no método `createCategoricalDataViewBuilder`. Especifica também as interfaces e os métodos necessários para trabalhar com um elemento visual **DataView** simulado em testes de unidades.

* `withValues` adiciona colunas de séries estáticas e `withGroupedValues` adiciona colunas de séries dinâmicas.

  Não aplique séries dinâmicas e estáticas em simultâneo num elemento visual **DataViewCategorical**. Só pode utilizar ambas as séries na consulta **DataViewCategorical**, em que se espera que **DataViewTransform** as divida em objetos visuais **DataViewCategorical**.

* `build` devolve o elemento visual DataView com metadados e o objeto DataViewCategorical.

  `build` devolve **Undefined** (Indefinido) se a combinação de parâmetros for inválida, como incluir séries dinâmicas e estáticas em simultâneo ao criar o elemento visual **DataView**.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Utilizado para a criação de **VisualData** em testes de unidades. Ao colocar dados em registos de campos de dados, o Power BI produz um objeto categórico **DataView** baseado nos dados. O **TestDataViewBuilder** ajuda a simular a criação do objeto categórico **DataView**.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  Segue-se uma apresentação das interfaces mais utilizadas ao criar um `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Para obter mais exemplos, saiba como [escrever testes de unidades do TestDataViewBuilder](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) e veja um [cenário de utilização real do TestDataViewBuilder](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Simulações

### <a name="mockivisualhost"></a>MockIVisualHost

Implementa o **IVisualHost** para testar elementos visuais do Power BI sem dependências externas, como a Arquitetura do Power BI.

Os métodos úteis incluem `createSelectionIdBuilder`, `createSelectionManager` e `createLocalizationManager`, e propriedades de getter.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` cria e devolve uma instância do **iVisualHost**, ou seja, do **MockIVisualHost**.
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Exemplo
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> O **MockIVisualHost** é uma implementação fictícia do **iVisualHost** e só deve ser utilizado com testes de unidades.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implementa a **IColorPalette** para testar elementos visuais do Power BI sem dependências externas, como a Arquitetura do Power BI.

A **MockIColorPalette** fornece propriedades úteis para verificar o esquema de cores ou o modo de alto contraste em testes de unidades.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` cria e devolve uma instância da **IColorPalette**, ou seja, da **MockIColorPalette**.
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Exemplo
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> A **MockIColorPalette** é uma implementação fictícia da **IColorPalette** e só deve ser utilizada com testes de unidades.

### <a name="mockiselectionid"></a>MockISelectionId

Implementa o **ISelectionId** para testar elementos visuais do Power BI sem dependências externas, como a Arquitetura do Power BI.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` cria e devolve uma instância do **ISelectionId**, ou seja, do **MockISelectionId**.
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Exemplo
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> O **MockISelectionId** é uma implementação fictícia do **ISelectionId** e só deve ser utilizado com testes de unidades.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implementa o **ISelectionIdBuilder** para testar elementos visuais do Power BI sem dependências externas, como a Arquitetura do Power BI. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` cria e devolve uma instância do **ISelectionIdBuilder**, ou seja, do **MockISelectionIdBuilder**.
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Exemplo
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> O **MockISelectionIdBuilder** é uma implementação fictícia do **ISelectionIdBuilder** e só deve ser utilizado com testes de unidades.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implementa o **ISelectionManager** para testar elementos visuais do Power BI sem dependências externas, como a Arquitetura do Power BI. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` cria e devolve uma instância do **ISelectionManager**, ou seja, do **MockISelectionManager**.
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Exemplo
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> O **MockISelectionManager** é uma implementação fictícia do **ISelectionManager** e só deve ser utilizado com testes de unidades.

### <a name="mockilocale"></a>MockILocale

  Define a região e altera-a de acordo com as suas necessidades durante o processo de teste de unidades.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` cria e devolve uma instância da **MockILocale**.
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simula o `TooltipService` e chama-o de acordo com as suas necessidades durante o processo de teste de unidades.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` cria e devolve uma instância do **MockITooltipService**.
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` cria e devolve uma instância de **MockIAllowInteractions**.
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Fornece capacidades básicas do **LocalizationManager** necessárias para testes de unidades.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` cria e devolve uma instância do **ILocalizationManager**, ou seja, do **MockILocalizationManager**.
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Exemplo
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simula a utilização do **TelemetryService**.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Criação de `MockITelemetryService`.
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simula o funcionamento do **AuthenticationService** ao fornecer um token do AAD simulado.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` cria e devolve uma instância do **IAuthenticationService**, ou seja, do **MockIAuthenticationService**.
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Permite-lhe utilizar o **ILocalVisualStorageService** com o mesmo comportamento do **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` cria e devolve uma instância do **ILocalVisualStorageService**, ou seja, do **MockIStorageService**.
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` cria e devolve uma instância do **IVisualEventService**, ou seja, do **MockIEventService**.
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utilitários

Os utilitários incluem métodos auxiliares para os testes de unidades dos elementos visuais do Power BI, incluindo auxiliares relacionados com cores, números e eventos.

- `renderTimeout` devolve o tempo limite.
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` ajuda a definir a posição fixa em testes de unidades.
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Exemplo
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Métodos auxiliares relacionados com cores

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Devolve a seguinte estrutura:

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` compara objetos **RgbColor** analisados de cadeias de entrada.
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` analisa a cor da cadeia de entrada e devolve-a na interface **RgbColor** especificada.
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Métodos auxiliares relacionados com números

- `getRandomNumbers` gera um número aleatório ao utilizar valores mínimos e máximos. Pode especificar a `exceptionList` e fornecer uma função para a alteração do resultado.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` fornece um conjunto de números aleatórios gerados pelo método `getRandomNumber`, com valores mínimos e máximos especificados.
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Métodos auxiliares relacionados com eventos
Os seguintes métodos são escritos para a simulação de eventos de páginas Web em testes de unidades.

- `clickElement` simula um clique no elemento especificado.
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` devolve um objeto **Touch** para ajudar a simular um evento de toque.
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` devolve uma lista de eventos **Touch** simulados.
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` devolve o **MouseEvent**.
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` cria e devolve o **MouseEvent**.
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>Métodos auxiliares relacionados com eventos D3

Os seguintes métodos são utilizados para simular eventos D3 em testes de unidades.

- `flushAllD3Transitions` força a conclusão de todas as transições D3.

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalmente, as transições de atraso zero são executadas após um atraso instantâneo (<10 ms), mas isso pode causar uma breve intermitência se o browser compuser a página duas vezes. Uma intermitência no fim do primeiro ciclo de eventos e outra imediatamente a seguir na primeira chamada de retorno do temporizador.
  >
  > Estas intermitências são mais percetíveis no IE e com um grande número de vistas Web, e não são recomendadas para o iOS.
  > 
  > Ao remover a fila do temporizador da cache no fim do primeiro ciclo de eventos, pode executar imediatamente quaisquer transições de atraso zero e evitar a intermitência.

Estão também incluídos os seguintes métodos:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Interfaces auxiliares
A interface e as enumerações seguintes são utilizadas na função auxiliar.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Passos seguintes

Para escrever testes de unidades para elementos visuais do Power BI baseados no webpack e realizar testes de unidades com `karma` e `jasmine`, veja, por exemplo, [Tutorial: Adicionar testes de unidades para projetos de elementos visuais do Power BI](./unit-tests-introduction.md).
