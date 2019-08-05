---
title: Descrições em elementos visuais
description: Os elementos visuais do Power BI conseguem apresentar descrições
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 286c5eef2c341ad77c351008b321992597bef292
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425649"
---
# <a name="power-bi-visuals-tooltips"></a>Descrições em elementos visuais do Power BI

Agora os elementos visuais conseguem utilizar o suporte de descrições do Power BI. As descrições do Power BI suportam as seguintes interações:

Mostrar uma descrição.
Ocultar uma descrição.
Mover uma descrição.

As descrições podem apresentar um elemento textual com um título, um valor com uma determinada cor e opacidade num conjunto especificado de coordenadas. Estes dados são fornecidos à API. O anfitrião do Power BI compõe-nos da mesma forma que compõe descrições para elementos visuais nativos.

Por exemplo, descrições no exemplo de BarChart.

![Descrições do exemplo de BarChart](./media/tooltips-in-samplebarchart.png)

A descrição acima ilustra o valor e a categoria de uma única barra. Contudo, pode ser aumentada de forma possibilitar a apresentação de múltiplos valores dentro de uma só descrição.

## <a name="handling-tooltips"></a>Processar descrições

A interface através da qual gere descrições é o "ITooltipService". Esta interface é utilizada para notificar o anfitrião de que é necessário apresentar, remover ou mover uma descrição.

```typescript
    interface ITooltipService {
        enabled(): boolean;
        show(options: TooltipShowOptions): void;
        move(options: TooltipMoveOptions): void;
        hide(options: TooltipHideOptions): void;
    }
```

O seu elemento visual terá de escutar os eventos de rato dentro do seu elemento visual e chamar os delegados `show()`, `move()` e `hide()` conforme necessário com o devido conteúdo preenchido nos objetos `Tooltip****Options`.
`TooltipShowOptions` e `TooltipHideOptions`, por sua vez, definiriam o que apresentar e o comportamento a adotar nestes eventos.
Como a chamada destes métodos envolveria eventos de utilizador, tais como eventos de toque ou movimentos do rato, seria boa ideia criar serviços de escuta para estes eventos, o que, por sua vez, invocaria os membros do `TooltipService`.
Os nossos exemplos de agregações numa classe chamada `TooltipServiceWrapper`.

### <a name="tooltipservicewrapper-class"></a>Classe TooltipServiceWrapper

A ideia básica subjacente a esta classe consiste em conter a instância do `TooltipService`, em escutar eventos de rato D3 sobre elementos relevantes e, em seguida, em chamar `show()` e `hide()` quando for necessário.
A classe contém e gere todos os estados e lógicas relevantes para estes eventos, especialmente destinados a ser utilizados com interface com o código D3 subjacente. A utilização com interface e a conversão D3 estão fora do âmbito deste documento.

Pode encontrar o exemplo de código completo no [repositório de elementos visuais do SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/981b021612d7b333adffe9f723ab27783c76fb14).

### <a name="creating-tooltipservicewrapper"></a>Criar TooltipServiceWrapper

O construtor do BarChart tem agora um membro `tooltipServiceWrapper`, que é instanciado no construtor com a instância do `tooltipService` do anfitrião.

```typescript
        private tooltipServiceWrapper: ITooltipServiceWrapper;

        this.tooltipServiceWrapper = createTooltipServiceWrapper(this.host.tooltipService, options.element);
```

A classe `TooltipServiceWrapper` contém a instância `tooltipService`, assim como o elemento D3 raiz dos parâmetros visuais e de toque.

```typescript
    class TooltipServiceWrapper implements ITooltipServiceWrapper {
        private handleTouchTimeoutId: number;
        private visualHostTooltipService: ITooltipService;
        private rootElement: Element;
        private handleTouchDelay: number;

        constructor(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay: number) {
            this.visualHostTooltipService = tooltipService;
            this.handleTouchDelay = handleTouchDelay;
            this.rootElement = rootElement;
        }
        .
        .
        .
    }
```

O único ponto de entrada para esta classe registar serviços de escuta de eventos é o método `addTooltip`.

### <a name="addtooltip-method"></a>Método addTooltip

```typescript
        public addTooltip<T>(
            selection: d3.Selection<Element>,
            getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[],
            getDataPointIdentity: (args: TooltipEventArgs<T>) => ISelectionId,
            reloadTooltipDataOnMouseMove?: boolean): void {

            if (!selection || !this.visualHostTooltipService.enabled()) {
                return;
            }
        ...
        ...
        }
```

* **selection: d3.Selection<Element>**
* Os elementos D3 sobre os quais são processadas descrições
* **getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[]**
* Delegar para preencher o conteúdo da descrição (o que apresentar) por contexto
* **getDataPointIdentity: (args: TooltipEventArgs<T>) => ISelectionId**
* Delegar para recuperar o ID do ponto de dados (não utilizado neste exemplo) 
* **reloadTooltipDataOnMouseMove?: boolean**
* Booleano que indica se os dados da descrição devem ou não ser atualizados durante um evento mouseMove (não utilizado neste exemplo)

Como pode ver, `addTooltip` sairá sem ação se `tooltipService` estiver desativado ou não houver nenhuma seleção real.

### <a name="call-of-show-method-to-display-a-tooltip"></a>Chamada do método Show para apresentar uma descrição

Em seguida, `addTooltip` escuta o evento `mouseover` D3.

```typescript
        ...
        ...
        selection.on("mouseover.tooltip", () => {
            // Ignore mouseover while handling touch events
            if (!this.canDisplayTooltip(d3.event))
                return;

            let tooltipEventArgs = this.makeTooltipEventArgs<T>(rootNode, true, false);
            if (!tooltipEventArgs)
                return;

            let tooltipInfo = getTooltipInfoDelegate(tooltipEventArgs);
            if (tooltipInfo == null)
                return;

            let selectionId = getDataPointIdentity(tooltipEventArgs);

            this.visualHostTooltipService.show({
                coordinates: tooltipEventArgs.coordinates,
                isTouchEvent: false,
                dataItems: tooltipInfo,
                identities: selectionId ? [selectionId] : [],
            });
        });
```

* **makeTooltipEventArgs**
* Extrai o contexto dos elementos D3 selecionados para um ToolTipEventArgs. Também calculará as coordenadas.
* **getTooltipInfoDelegate**
* Em seguida, cria o conteúdo da descrição a partir de ToolTipEventArgs. É uma chamada de retorno para a classe BarChart, dado ser a lógica do elemento visual. É o conteúdo de texto que será efetivamente apresentado na descrição.
* **getDataPointIdentity**
* Não utilizado neste exemplo
* **this.visualHostTooltipService.show**
* A chamada para apresentar a descrição.  

É possível encontrar processamento adicional no exemplo dos eventos `mouseout` e `mousemove`.

Para obter mais informações, veja o [repositório de elementos visuais do SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/981b021612d7b333adffe9f723ab27783c76fb14).

### <a name="populating-the-tooltip-content-by-gettooltipdata-method"></a>Preencher o conteúdo da descrição através do método getTooltipData

O `BarChart` foi adicionado com um membro `getTooltipData` que simplesmente extrai a categoria, o valor e a cor do ponto de dados para um elemento VisualTooltipDataItem[].

```typescript
        private static getTooltipData(value: any): VisualTooltipDataItem[] {
            return [{
                displayName: value.category,
                value: value.value.toString(),
                color: value.color,
                header: 'ToolTip Title'
            }];
        }
```

Na implementação acima, o membro `header` é constante, mas pode ser utilizado para implementações mais complexas que exigem valores dinâmicos. Pode preencher `VisualTooltipDataItem[]` com mais do que um elemento, o que adicionará múltiplas linhas à descrição. Pode ser útil em elementos visuais, tais como gráficos de barras empilhadas, nos quais a descrição poderá apresentar dados de mais do que um único ponto de dados.

### <a name="calling-addtooltip-method"></a>Chamar o método addTooltip

O último passo consiste em chamar `addTooltip` quando os dados reais podem mudar. Esta chamada ocorreria no método `BarChart.update()`. Desta forma, é efetuada uma chamada para monitorizar a seleção de todos os elementos da "barra" e transmite-se apenas `BarChart.getTooltipData()`, conforme mencionado acima.

```typescript
        this.tooltipServiceWrapper.addTooltip(this.barContainer.selectAll('.bar'),
            (tooltipEvent: TooltipEventArgs<number>) => BarChart.getTooltipData(tooltipEvent.data),
            (tooltipEvent: TooltipEventArgs<number>) => null);
```

## <a name="adding-report-page-tooltips"></a>Adicionar descrições da página de relatório

Para adicionar suporte de descrições da página de relatório, a maioria das alterações estará localizada em capabilities.json.

Abaixo encontra-se um exemplo de esquema.

```json
{
    "tooltips": {
        "supportedTypes": {
            "default": true,
            "canvas": true
        },
        "roles": [
            "tooltips"
        ]
    }
}
```

É possível proceder à definição das descrições da página de relatório no painel Formatação.

![Descrição da página de relatório](media/report-page-tooltip.png)

`supportedTypes` é a configuração das descrições suportada pelo elemento visual e refletida no conjunto de campos. `default` especifica se o enlace de descrições "automático" através do campo de dados é suportado. "canvas" especifica se as descrições da página de relatório são suportadas.

`roles` é opcional. Quando está definido, indica as funções de dados que estarão vinculadas à opção de descrição selecionada no conjunto de campos.

Para obter mais informações, veja as diretrizes de utilização das Descrições da Página de Relatório [Descrições da Página de Relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#tooltips).

Para apresentar a descrição da página de relatório, aquando da chamada de `ITooltipService.Show(options: TooltipShowOptions)` ou `ITooltipService.Move(options: TooltipMoveOptions)`, o anfitrião do Power BI consumirá selectionId (propriedade `identities` do argumento `options` acima). SelectionId deverá representar os dados selecionados (categoria, série, etc.), relativos ao item sobre o qual pairou o cursor do rato, a serem obtidos pela descrição.

Exemplo do envio de selectionId para chamadas de apresentação de descrições:

```typescript
    this.tooltipServiceWrapper.addTooltip(this.barContainer.selectAll('.bar'),
        (tooltipEvent: TooltipEventArgs<number>) => BarChart.getTooltipData(tooltipEvent.data),
        (tooltipEvent: TooltipEventArgs<number>) => tooltipEvent.data.selectionID);
```
