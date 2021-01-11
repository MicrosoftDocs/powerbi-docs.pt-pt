---
title: API de elementos visuais na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo descreve como utilizar a API IVisual para elementos visuais do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 7b81ecfa1b97b202b6c1ff306cf858f2ea00acde
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888541"
---
# <a name="visual-api"></a>Visual API (API de Elementos Visuais)
Todos os elementos visuais começam com uma classe que implementa a interface `IVisual`. Pode dar o nome que quiser à classe, desde que exista especificamente uma classe que implemente a interface `IVisual`.

> [!NOTE]
> O nome da classe do elemento visual deve corresponder ao que está definido no ficheiro *pbiviz.json*.

Veja a classe do elemento visual de exemplo com os seguintes métodos que devem ser implementados:

* `constructor`, um construtor padrão para inicializar o estado do elemento visual
* `update`, para atualizar os dados do elemento visual
* `enumerateObjectInstances`, para devolver objetos para povoar o painel de propriedades (opções de formatação), onde os pode modificar conforme necessário
* `destroy`, um processo de destruição padrão para limpeza

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>construtor

O construtor da classe do elemento visual é chamado quando o elemento visual é instanciado. Pode ser utilizado para todas as operações de instalação exigidas pelo elemento visual.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, uma referência ao elemento DOM que conterá o elemento visual
* `host: IVisualHost`, uma coleção de propriedades e serviços que pode ser utilizada para interagir com o sistema anfitrião do elemento visual (Power BI)

   `IVisualHost` contém os seguintes serviços:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, gera e armazena metadados para itens selecionáveis no elemento visual
   * `createSelectionManager`, cria a ponte de comunicação utilizada para notificar o sistema anfitrião do elemento visual sobre as alterações ao estado de seleção, veja [API de Seleção](./selection-api.md).
   * `createLocalizationManager`, gera um gestor para ajudar com a [Localização](./localization.md)
   * `allowInteractions: boolean`, um sinalizador booleano que indica se o elemento visual deve ou não ser interativo
   * `applyJsonFilter`, aplica tipos de filtro específicos. Veja [API de Filtro](./filter-api.md)
   * `persistProperties`, permite que os utilizadores mantenham propriedades e as guardem juntamente com a definição do elemento visual, para que estejam disponíveis no próximo recarregamento
   * `eventService`, devolve um [serviço de eventos](./event-service.md) para suportar eventos de **Composição**
   * `storageService`, devolve um serviço para ajudar a utilizar o [armazenamento local](./local-storage.md) no elemento visual
   * `authenticationService`, gera um serviço para ajudar na autenticação de utilizador
   * `tooltipService`, devolve um [serviço de descrição](./add-tooltips.md) para ajudar a utilizar descrições no elemento visual
   * `launchUrl`, ajuda a [iniciar o URL](./launch-url.md) no separador seguinte
   * `locale`, devolve uma cadeia de região. Veja [Localização](./localization.md)
   * `instanceId`, devolve uma cadeia de carateres para identificar a instância do elemento visual atual
   * `colorPalette`, devolve a colorPalette necessária para aplicar cores aos dados
   * `fetchMoreData`, suporta a utilização de mais dados do que o limite padrão (1000 linhas)
   * `switchFocusModeState`, ajuda a mudar o estado do modo de detalhe

## <a name="update"></a>update

Todos os elementos visuais devem implementar um método de atualização pública que é chamado sempre que existe uma alteração ao ambiente do sistema anfitrião ou dos dados.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, dimensões da janela viewport para compor o elemento visual
* `dataViews: DataView[]`, o objeto dataview que contém todos os dados necessários para compor o elemento visual (o elemento visual utilizará normalmente a propriedade categórica em DataView)
* `type: VisualUpdateType`, sinalizador para indicar os tipos desta atualização (**Dados** | **Redimensionar** | **ViewMode** | **Estilo** | **ResizeEnd**)
* `viewMode: ViewMode`, sinalizador para indicar o modo de visualização do elemento visual (**Ver** | **Editar** | **InFocusEdit**)
* `editMode: EditMode`, sinalizador para indicar o modo de edição do elemento visual (**Predefinição** | **Avançado**) (se os elementos visuais suportarem **AdvancedEditMode**, deverá compor os controlos da IU avançados apenas quando **editMode** estiver definido como **Avançado**. Veja [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind`, sinalizador para indicar o tipo de alteração de dados (**Criar** | **Acrescentar**)
* `jsonFilters?: IFilter[]`, coleção de filtros json aplicados
* `isInFocus?: boolean`, sinalizador para indicar se o elemento visual se encontra no modo de detalhe ou não
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Este método é chamado para todos os objetos listados nas capacidades. Com as opções (atualmente apenas o nome), poderá devolver um `VisualObjectInstanceEnumeration` com as informações sobre como apresentar esta propriedade.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, nome do objeto

## <a name="destroy-optional"></a>destruição `optional`

A função de destruição é chamada quando o elemento visual é descarregado e pode ser utilizada para tarefas de limpeza, como remover clientes de escuta dos eventos.

``` typescript
public destroy(): void
```

> [!Note]
> O Power BI geralmente não chama `destroy`, já que é mais rápido remover todo o IFrame que contém o elemento visual.
