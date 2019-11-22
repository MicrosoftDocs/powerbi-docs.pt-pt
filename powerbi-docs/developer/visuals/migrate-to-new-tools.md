---
title: Migrar para o powerbi-visuals-tools 3.x
description: Introdução à nova versão do powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cc554bff1cbd248ccd69a80ee47b60af981cdab1
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061828"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Migrar para o novo powerbi-visuals-tools 3.x.x

A partir da versão 3, o Power BI Visuals Tools utiliza o Webpack para criar Elementos Visuais Personalizados.
A nova versão traz muitas novas oportunidades para os programadores criarem elementos visuais:

* TypeScript v3.x.x por predefinição. A partir do TypeScript 1.5, a nomenclatura foi alterada. [Saiba mais acerca dos módulos TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

* Os módulos ES6 são suportados. Já não precisa de utilizar a [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries). Em vez disso, utilize as importações ES6.

* São suportadas as novas versões da [D3v5](https://d3js.org/) e outras bibliotecas de códigos baseadas no módulo ES6.

* Tamanho de pacote reduzido. O Webpack utiliza o [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) para eliminar códigos que não são utilizados. Reduz o código de JS e, como resultado, obtém um melhor desempenho no carregamento de elementos visuais.

* Desempenho melhorado da API.

* A biblioteca de códigos Globalize.js [está integrada](migrate-to-new-tools.md#remove-globalizejs-library) nos utilitários de formatação.

* O Tools utiliza o [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) para apresentar a base de código do elemento visual.

Todos os passos da migração para a nova versão do Power BI Visuals Tools são descritos abaixo.

## <a name="backward-compatibility"></a>Retrocompatibilidade

As novas ferramentas preservam a retrocompatibilidade com a base de código antiga dos elementos visuais, mas podem exigir algumas alterações adicionais para carregar bibliotecas de códigos externas.

As bibliotecas de códigos que suportam sistemas de módulos serão importadas como módulos do Webpack. Todas as outras bibliotecas e códigos fonte dos elementos visuais serão encapsulados num módulo.

As variáveis globais, como JQuery e Lodash, que foram utilizadas nas ferramentas pbiviz anteriores estão, agora, obsoletas. Tal significa que se o código antigo do elemento visual for reencaminhado em variáveis globais, o elemento visual poderá, neste caso, ficar danificado.

A versão anterior do Power BI Visuals Tools exigia a definição de uma classe do elemento visual no módulo `powerbi.extensibility.visual`.

## <a name="how-to-install-powerbi-visuals-tools"></a>Como instalar o powerbi-visuals-tools

O novo conjunto de ferramentas pode ser instalado através da execução do comando

```cmd
npm install -g powerbi-visuals-tools
```

Amostra do elemento visual sampleBarChart e [alterações](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) correspondentes em `package.json`:

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Como instalar a API de Elementos Visuais Personalizados do Power BI

A nova versão do powerbi-visual-tools não inclui todas as versões da API. Em vez disso, o programador deve instalar uma versão específica do pacote [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api). A versão do pacote corresponde à versão da API dos Elementos Visuais Personalizados do Power BI e fornece todas as definições de tipo para a API de Elementos Visuais do Power BI.

Adicione `powerbi-visuals-api` às dependências do projeto ao executar o comando `npm install --save-dev powerbi-visuals-api`.
Deve também remover a ligação para as antigas definições de tipo da API, uma vez que os tipos da `powerbi-visuals-api` são automaticamente incluídos via Webpack. As alterações correspondentes estão [nesta](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) linha do `package.json`.

## <a name="update-tsconfigjson"></a>Atualizar `tsconfig.json`

Para utilizar módulos externos, deve alterar a opção `out` para `outDir`.
`"outDir": "./.tmp/build/",` em vez de `"out": "./.tmp/build/visual.js",`.

Este procedimento é necessário, uma vez que os ficheiros TypeScript serão compilados em ficheiros JavaScript de forma independente. É por isso que já não precisa de especificar o ficheiro visual.js como uma saída.

E também pode alterar a opção `target` para `ES6`, caso queira utilizar o JavaScript moderno como uma saída. [É opcional](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Atualizar os utilitários dos Elementos Visuais Personalizados

Se utilizar um dos [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), também os deverá atualizar para a versão mais recente.

Execute o comando `npm install powerbi-visuals-utils-<UTILNAME> --save`. (por exemplo, `npm install powerbi-visuals-utils-dataviewutils --save`) para obter a nova versão com os módulos externos do TypeScript.

Pode encontrar um exemplo no [repositório](https://github.com/Microsoft/powerbi-visuals-mekkochart) do MekkoChart.
Este elemento visual utiliza todos os utilitários.

## <a name="remove-globalizejs-library"></a>Remover a biblioteca de códigos Globalize.js

A nova versão do [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) inclui uma biblioteca de códigos globalize.js inovadora.
Não precisa de incluir esta biblioteca manualmente no projeto.
Todas as localizações necessárias serão automaticamente adicionadas ao pacote final.

## <a name="fix-loading-external-libraries"></a>Corrigir o carregamento das bibliotecas de códigos externas

Em vez disso, inclua o novo ficheiro JS depois das bibliotecas de códigos na matriz `externalJS` do `pbiviz.json`. Por exemplo:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importe as bibliotecas de códigos na origem. Exemplo para `lodash-es`:

```JS
import * as _ from "lodash-es";
```

em que `_` é a variável global para a biblioteca de códigos `lodash`.

## <a name="changes-in-the-visuals-sources"></a>Alterações nas origens dos elementos visuais

A principal alteração é a conversão de módulos internos em módulos externos, já que não é possível utilizar módulos externos dentro de módulos internos.

Essas alterações descrevem as modificações que foram aplicadas ao Gráfico de Barras de Exemplo.

Abaixo encontram-se as descrições detalhadas das alterações:

1. Remova todas as definições de módulos de cada ficheiro do [código fonte](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importe as definições da API de elementos visuais personalizados do Power BI](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importe](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) as interfaces ou classes necessárias do módulo interno do `powerbi`.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importe](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) a biblioteca de códigos D3.js.

    ```typescript
    import * as d3 from "d3";
    ```

    Pode importar apenas os módulos da biblioteca de códigos d3 necessários.

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importe](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) os utilitários, as classes e as interfaces definidos no projeto do elemento visual para o ficheiro de origem principal

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importar os Estilos CSS

A nova versão das ferramentas permite que os programadores importem o estilo CSS, LESS diretamente para o código TypeScript.

Por isso, a [secção de estilos](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) utilizada anteriormente será ignorada pelo compilador.

Para utilizar a folha de estilos, abra o ficheiro ts principal e adicione a seguinte linha:  

```typescript
import "./../style/visual.less";
```  

Os estilos CSS, LESS serão compilados automaticamente.  

### <a name="externaljs-section-in-pbivizjson"></a>Secção externalJS no pbiviz.json

As ferramentas [não requerem](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) uma lista de `externalJS` para serem carregadas para o conjunto de elementos visuais, uma vez que o webpack inclui todas a bibliotecas de códigos importadas.

**A secção externalJS no pbivi.json deve estar vazia.**

Chame os comandos `npm run package` típicos para criar o pacote de elementos visuais ou `npm run start` para iniciar o servidor de programação.

## <a name="updating-d3js-library-to-version-5"></a>Atualizar a biblioteca de códigos D3.js para a versão 5

Com as novas ferramentas, pode começar a utilizar a nova versão da biblioteca de códigos D3.js.

Chame os comandos para atualizar a D3 no projeto do elemento visual

`npm install --save d3@5` para instalar a nova D3.js.

`npm install --save-dev @types/d3@5` para instalar as novas definições de tipo para a D3.js.

Existem várias alterações interruptivas, pelo que deve modificar o código para utilizar a nova D3.js.

1. A interface `d3.Selection<T>` [foi alterada](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) para `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. Não pode aplicar vários atributos numa única chamada do método `attr`. [Deverá passar](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) cada atributo numa chamada diferente do método `attr`. Também é [semelhante](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) para o método `style`.

3. Na D3.js v4, é introduzido o novo método de intercalação. Este método é frequentemente utilizado para intercalar seleções de introdução e de atualização depois de uma associação de dados. [Chame o método de intercalação](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) para utilizar a d3 de forma adequada.

[Saiba mais](https://github.com/d3/d3/blob/master/CHANGES.md) sobre as alterações na biblioteca de códigos D3.js.

## <a name="babel"></a>Babel

A partir da versão 3.1, as ferramentas utilizam o Babel para compilar o novo código JS moderno na antiga ES5 para suportar uma grande variedade de browsers.

Esta opção está ativada por predefinição, mas precisa de importar o pacote [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill) manualmente.

Execute o comando para instalar o pacote

`npm install --save @babel/polyfill`

e importe o pacote no ponto inicial do código do elemento visual (normalmente é o ficheiro “src/visual.ts”):

`import "@babel/polyfill";`

Saiba mais sobre o Babel [na documentação](https://babeljs.io/docs/en/).

Por fim, execute o [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) para apresentar a base de código do elemento visual.  

![Estatísticas do código de elemento visual](./media/webpack-stats.png)
