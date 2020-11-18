---
title: 'Tutorial: Criar um elemento visual baseado no React para o Power BI'
description: Este tutorial mostra como criar um elemento visual do Power BI com o React. Apresenta um valor num círculo. O tamanho adaptável e as definições permitem personalizá-lo.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 03/30/2020
ms.openlocfilehash: d8e7b5dca207aef1a4f119bf324662dbcaa1bbab
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94513327"
---
# <a name="tutorial-create-a-react-based-visual"></a>Tutorial: Criar um elemento visual baseado no React

Este tutorial explica como criar um elemento visual do Power BI com o [React](https://reactjs.org/). O elemento visual apresenta um valor num círculo. O elemento visual tem um tamanho adaptável e definições para o personalizar. Com as informações neste artigo, pode criar os seus próprios elementos visuais do Power BI com o React.

![Elemento visual ColoredCircleCard do Power BI](./media/create-react-visual/powerbi-visuals-colored-circle-card.png)

Neste tutorial, vai aprender a:

> [!div class="checklist"]
>
> * Configurar o ambiente de desenvolvimento
> * Criar um elemento visual com o React
> * Configurar as capacidades do elemento visual
> * Compor dados a partir do Power BI
> * Redimensionar o elemento visual
> * Tornar o elemento visual personalizável

## <a name="prerequisites"></a>Pré-requisitos

* Uma conta do **Power BI Pro**. [Inscreva-se numa avaliação gratuita](https://powerbi.microsoft.com/pricing/) antes de começar.
* [Visual Studio Code](https://www.visualstudio.com/).
* Versão 4 ou posterior do [Windows PowerShell](/powershell/scripting/install/installing-windows-powershell) para utilizadores do Windows OU o [Terminal](https://macpaw.com/how-to/use-terminal-on-mac) para utilizadores do OSX.
* Um ambiente, conforme descrito em [Configurar o seu ambiente para desenvolver um elemento visual do Power BI](environment-setup.md).

## <a name="getting-started"></a>Introdução

Para começar, crie um elemento visual mínimo do Power BI com `pbiviz`. Para obter mais informações sobre os projetos e a estrutura dos projetos, veja [Estrutura de projeto de elementos visuais do Power BI](visual-project-structure.md). Para obter o código fonte completo deste elemento visual, veja [Elemento Visual de Cartão Circular do React](https://github.com/Microsoft/powerbi-visuals-circlecard-react).

Pode clonar ou transferir o código fonte completo do elemento visual a partir do [GitHub](https://github.com/Microsoft/powerbi-visuals-circlecard-react).

1. Abra o PowerShell e execute o seguinte comando:

   ```powershell
   pbiviz new ReactCircleCard
   ```

   O comando cria uma pasta chamada *ReactCircleCard*.

1. Altere os diretórios para essa pasta e abra o Visual Studio Code.

   ```powershell
   cd ./ReactCircleCard
   code .
   ```

1. Inicie o servidor de programação do elemento visual.

   ```powershell
   pbiviz start
   ```

   ![Atualizar o elemento visual do React](./media/create-react-visual/update-react-visual.png)

Este elemento visual básico representa o número de atualizações. Vamos transformá-lo num cartão circular no passo seguinte.

## <a name="change-the-visual-to-a-circle-card"></a>Alterar o elemento visual para um cartão circular

Este elemento visual básico representa o número de atualizações. Em seguida, transforme-o num cartão circular, que representa uma medida e o título.

1. Execute o seguinte comando para instalar as dependências necessárias:

   ```powershell
   npm i react react-dom
   ```

1. Execute o seguinte comando para instalar o React 16 e as versões correspondentes de `react-dom` e digitações:

   ```powershell
   npm i @types/react @types/react-dom
   ```

1. Crie uma classe de componente do React. No Visual Studio Code, selecione **Ficheiro** > **Novo Ficheiro**. Copie o seguinte código para o ficheiro.

    ```typescript
    import * as React from "react";

    export class ReactCircleCard extends React.Component<{}>{
        render(){
            return (
                <div className="circleCard">
                    Hello, React!
                </div>
            )
        }
    }

    export default ReactCircleCard;
    ```

1. Selecione **Guardar Como**. Aceda ao diretório *src*. Introduza o nome *component*. Em **Guardar com o tipo**, selecione **TypeScript React**.

1. Abra *src/visual.ts*. Substitua o código atual pelo seguinte código:

    ```typescript
    "use strict";
    import powerbi from "powerbi-visuals-api";

    import DataView = powerbi.DataView;
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
    import IVisual = powerbi.extensibility.visual.IVisual;

    import "./../style/visual.less";

    export class Visual implements IVisual {

        constructor(options: VisualConstructorOptions) {

        }

        public update(options: VisualUpdateOptions) {

        }
    }
    ```

1. Importe as dependências do React e o componente que acabou de adicionar.

    ```typescript
    import * as React from "react";
    import * as ReactDOM from "react-dom";
    ...
    import ReactCircleCard from "./component";
    ```

   As predefinições TypeScript do Power BI não aceitam os ficheiros *tsx* do React. O Visual Studio Code realça `component` como erro.

1. Abra o ficheiro *tsconfig.json* e adicione duas linhas ao início do item `compilerOptions`.

    ```json
    {
      "compilerOptions": {
        "jsx": "react",
        "types": ["react", "react-dom"],
        //...
      }
    }
    ```

   O erro em `component` deverá ter desaparecido.

   Para compor o componente, adicione o elemento HTML de destino. Este elemento é `HTMLElement` em `VisualConstructorOptions`, que é transmitido ao construtor.

1. Modifique a classe `Visual`, como no seguinte código:

    ```typescript
      private target: HTMLElement;
      private reactRoot: React.ComponentElement<any, any>;

      constructor(options: VisualConstructorOptions) {
          this.reactRoot = React.createElement(ReactCircleCard, {});
          this.target = options.element;

          ReactDOM.render(this.reactRoot, this.target);
      }
    ```

1. Guarde as alterações e execute o código existente com este comando:

    ```bash
    pbiviz start
    ```

   > [!NOTE]
   > Se tiver executado `pbiviz` anteriormente, terá de o reiniciar para aplicar as alterações em *tsconfig.json*.

  ![mensagem hello React no elemento visual](./media/create-react-visual/hello-react-message-visual.png)

## <a name="configure-capabilities"></a>Configurar as capacidades

Pode configurar as capacidades do elemento visual.

1. Abra `capabilities.json`. Remova o objeto `Category Data` de `dataRoles`. `ReactCircleCard` apresenta um único valor, por isso só precisamos de `Measure Data`. A chave `dataRoles` tem agora o seguinte aspeto:

    ```json
    "dataRoles": [
        {
            "displayName": "Measure Data",
            "name": "measure",
            "kind": "Measure"
        }
    ],
    ```

1. Remova todo o conteúdo da chave `objects`. Vai preenchê-la mais tarde.

    ```json
        "objects": {},
    ```

1. Copie o seguinte código da propriedade `dataViewMappings`. O valor de `max: 1` significa que apenas pode ser submetida uma única coluna de medida.

    ```json
        "dataViewMappings": [
            {
                "conditions": [
                    {
                        "measure": {
                            "max": 1
                        }
                    }
                ],
                "single": {
                    "role": "measure"
                }
            }
        ]
    ```

Agora, pode introduzir os dados do painel `Fields` nas definições do elemento visual.

![Medir Dados no Power BI](./media/create-react-visual/measure-data-powerbi-react-visual.png)

## <a name="receive-properties-from-power-bi"></a>Receber propriedades do Power BI

Pode compor os dados com o React. O componente pode apresentar os dados a partir do seu próprio estado.

1. Modifique *src/component.tsx*.

    ```javascript
    export interface State {
        textLabel: string,
        textValue: string
    }

    export const initialState: State = {
        textLabel: "",
        textValue: ""
    }

    export class ReactCircleCard extends React.Component<{}, State>{
        constructor(props: any){
            super(props);
            this.state = initialState;
        }

        render(){
            const { textLabel, textValue } = this.state;

            return (
                <div className="circleCard">
                    <p>
                        {textLabel}
                        <br/>
                        <em>{textValue}</em>
                    </p>
                </div>
            )
        }
    }
    ```

1. Adicione estilos para a nova marcação ao editar *styles/visual.less*.

    ```css
    .circleCard {
        position: relative;
        box-sizing: border-box;
        border: 1px solid #000;
        border-radius: 50%;
        width: 200px;
        height: 200px;
    }

    p {
        text-align: center;
        line-height: 30px;
        font-size: 20px;
        font-weight: bold;

        position: relative;
        top: -30px;
        margin: 50% 0 0 0;
    }
    ```

1. Os elementos visuais recebem os dados atuais como um argumento do método `update`. Abra *src/visual.ts* e adicione código a `ReactCircleCard.update`.

    ```typescript
    //...
    import { ReactCircleCard, initialState } from "./component";
    //...

    export class Visual implements IVisual {
        //...
        public update(options: VisualUpdateOptions) {

            if(options.dataViews && options.dataViews[0]){
                const dataView: DataView = options.dataViews[0];

                ReactCircleCard.update({
                    textLabel: dataView.metadata.columns[0].displayName,
                    textValue: dataView.single.value.toString()
                });
            } else {
                this.clear();
            }
        }

        private clear() {
            ReactCircleCard.update(initialState);
        }
    }
    ```

    O código seleciona `textLabel` e `textValue` a partir de `DataView` e, se os dados existirem, atualizará o estado do componente.

1. Para enviar atualizações para a instância do componente, insira o seguinte código na classe `ReactCircleCard`:

    ```typescript
        private static updateCallback: (data: object) => void = null;

        public static update(newState: State) {
            if(typeof ReactCircleCard.updateCallback === 'function'){
                ReactCircleCard.updateCallback(newState);
            }
        }

        public state: State = initialState;

        public componentWillMount() {
            ReactCircleCard.updateCallback = (newState: State): void => { this.setState(newState); };
        }

        public componentWillUnmount() {
            ReactCircleCard.updateCallback = null;
        }
    ```

1. Teste o elemento visual. Verifique se `pbiviz start` foi executado e guarde todos os ficheiros. Atualize o elemento visual.

   ![Valor apresentado no círculo no elemento visual do React](./media/create-react-visual/value-display-circle-powerbi-react.png)

## <a name="make-component-resizable"></a>Tornar o componente redimensionável

Nesta secção, vai tornar o componente redimensionável. Atualmente, o componente tem largura e altura fixas.

Obtenha o tamanho atual da janela viewport do elemento visual a partir do objeto `options`.

1. Abra *src/visual.ts*. Importe a interface `IViewport` e adicione a propriedade `viewport` à classe `visual`.

    ```typescript
    import IViewport = powerbi.IViewport;

    //...

    export class Visual implements IVisual {
        private viewport: IViewport;
        //...
    }
    ```

1. Adicione o seguinte código ao método `update` de `visual`.

    ```typescript
      if (options.dataViews && options.dataViews[0]) {
          const dataView: DataView = options.dataViews[0];

          this.viewport = options.viewport;
          const { width, height } = this.viewport;
          const size = Math.min(width, height);

          ReactCircleCard.update({
              size,
              //...
          });
      }
    ```

1. Adicione propriedades à interface `State` em *src/component.tsx*.

    ```typescript
    export interface State {
        //...
        size: number
    }

    const initialState: State = {
        //...
        size: 200
    }
    ```

1. Faça as seguintes alterações no método `render` em *src/component.tsx*:

    ```typescript
        render() {
            const { textLabel, textValue, size } = this.state;

            const style: React.CSSProperties = { width: size, height: size };

            return (
                <div className="circleCard" style={style}>
                    {/* ... */}
                </div>
            )
        }
    ```

1. Substitua as regras `width` e `height` em *style/visual.less* por `min-width` e `min-height`.

    ```css
        min-width: 200px;
        min-height: 200px;
    ```

Agora, pode redimensionar a janela viewport. O diâmetro do círculo corresponde ao tamanho mínimo, como largura ou altura.

## <a name="make-your-power-bi-visual-customizable"></a>Tornar o elemento visual do Power BI personalizável

Nesta secção, vai tornar o elemento visual personalizável.

1. Abra *capabilities.json*. Adicione as seguintes definições à propriedade `objects`.

    ```json
    //...
        "objects": {
            "circle": {
                "displayName": "Circle",
                "properties": {
                    "circleColor": {
                        "displayName": "Color",
                        "description": "The fill color of the circle.",
                        "type": {
                            "fill": {
                                "solid": {
                                    "color": true
                                }
                            }
                        }
                    },
                    "circleThickness": {
                        "displayName": "Thickness",
                        "description": "The circle thickness.",
                        "type": {
                            "numeric": true
                        }
                    }
                }
            }
        },
    //...
    ```

1. Substitua o código existente em *src/settings.ts* pelo seguinte código:

    ```typescript
    "use strict";

    import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";
    import DataViewObjectsParser = dataViewObjectsParser.DataViewObjectsParser;

    export class CircleSettings {
        public circleColor: string = "white";
        public circleThickness: number = 2;
    }

    export class VisualSettings extends DataViewObjectsParser {
        public circle: CircleSettings = new CircleSettings();
    }
    ```

1. Adicione estas instruções `import` na parte superior de *src/visual.ts*:

    ```typescript
    import VisualObjectInstance = powerbi.VisualObjectInstance;
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions;
    import VisualObjectInstanceEnumerationObject = powerbi.VisualObjectInstanceEnumerationObject;

    import { VisualSettings } from "./settings";

    ```

1. Adicione o método `enumerateObjectInstances` a *src/visual.ts*. Este método é utilizado para aplicar as definições visuais.

    ```typescript
    export class Visual implements IVisual {
        private settings: VisualSettings;

        //...

        public enumerateObjectInstances(
            options: EnumerateVisualObjectInstancesOptions
        ): VisualObjectInstance[] | VisualObjectInstanceEnumerationObject {

            return VisualSettings.enumerateObjectInstances(this.settings || VisualSettings.getDefault(), options);
        }
    }
    ```

1. Adicione código para que o objeto `dataView` possa agora receber as definições.

    ```typescript
        public update(options: VisualUpdateOptions) {

            if(options.dataViews && options.dataViews[0]){
                //...
                this.settings = VisualSettings.parse(dataView) as VisualSettings;
                const object = this.settings.circle;

                ReactCircleCard.update({
                    borderWidth: object && object.circleThickness ? object.circleThickness : undefined,
                    background: object && object.circleColor ? object.circleColor : undefined,
                    //...
                });
            }
        }
    }
    ```

1. Aplique as alterações correspondentes a *src/component.tsx*, primeiro ao adicionar estes valores a `State`:

    ```typescript
    export interface State {
        //...
        background?: string,
        borderWidth?: number
    }
    ```

1. Em seguida, adicione o seguinte código ao método `render`:

    ```typescript
        const { /*...*/ background, borderWidth } = this.state;

        const style: React.CSSProperties = { /*...*/ background, borderWidth };
    ```

    ![Elemento visual ColoredCircleCard final do Power BI](./media/create-react-visual/powerbi-visuals-colored-circle-card.png)

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o desenvolvimento do Power BI, veja [Diretrizes de elementos visuais do Power BI](guidelines-powerbi-visuals.md) e [Elementos visuais no Power BI](power-bi-visuals-concept.md).