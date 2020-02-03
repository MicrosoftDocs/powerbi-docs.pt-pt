---
title: Migrar para o powerbi-visuals-tools versão 3.X
description: Introdução à nova versão do powerbi-visuals-tools
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818830"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migrar para o novo powerbi-visuals-tools versão 3.*X*

A partir da versão 3, o Power BI Visuals Tools (powerbi-visuals-tools ou `pbiviz`) utiliza o webpack para criar elementos visuais personalizados.
A nova versão oferece aos programadores muitas melhorias para a criação de elementos visuais:

- O TypeScript versão 3.*X* é utilizado por predefinição. A partir do TypeScript 1.5, a nomenclatura foi alterada. [Saiba mais acerca dos módulos TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

- Os módulos ECMAScript 6 (ES6) são suportados. Já não precisa de utilizar a [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries). Em vez disso, utilize as importações ES6.

- São suportadas as novas versões da Data-Driven Documents ([D3v5](https://d3js.org/)) e outras bibliotecas de código baseadas no módulo ES6.

- Tamanho de pacote reduzido. O webpack utiliza o [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) para eliminar código que não seja utilizado. Reduz o código JavaScript e proporciona um melhor desempenho no carregamento de elementos visuais.

- Desempenho melhorado da API.

- A biblioteca de código Globalize.js [está integrada](migrate-to-new-tools.md#remove-the- globalizejs-library) nos FormattingUtils.

- O Power BI Visuals Tools utiliza o [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) para apresentar a base de código do elemento visual.

Este artigo descreve todos os passos da migração para a nova versão do Power BI Visuals Tools.

## <a name="backward-compatibility"></a>Retrocompatibilidade

As novas ferramentas preservam as informações de retrocompatibilidade com a base de código antiga dos elementos visuais, mas podem exigir algumas alterações adicionais para carregar bibliotecas de código externas.

As bibliotecas de código que suportam sistemas de módulos são importadas como módulos do webpack. Todas as outras bibliotecas e códigos fonte dos elementos visuais estão encapsulados num módulo.

As variáveis globais, como JQuery e Lodash, que foram utilizadas no Power BI Visuals Tools estão, agora, obsoletas. Se o código antigo do seu elemento visual depender de variáveis globais, o elemento visual provavelmente não irá funcionar com as novas ferramentas.

A versão anterior do Power BI Visuals Tools exigia que definisse uma classe do elemento visual no módulo `powerbi.extensibility.visual`. Com a nova versão das ferramentas, em vez disso, tem de definir uma classe do elemento visual no ficheiro TypeScript (.ts) principal. Normalmente, esse ficheiro é o `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>Instalar o powerbi-visuals-tools

Execute este comando para instalar as novas ferramentas:

```cmd
npm install -g powerbi-visuals-tools
```

O código que se segue é do ficheiro `package.json` no [repositório do elemento visual sampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15), após o projeto de elementos visuais ter sido atualizado para funcionar com as novas ferramentas:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Instalar a API de Elementos Visuais Personalizados do Power BI

A nova versão do powerbi-visuals-tools não inclui todas as versões da API. Em vez disso, tem de instalar uma versão específica do pacote [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api). Escolha a versão do pacote que corresponda à versão da API dos seus elementos visuais personalizados do Power BI. O pacote fornece todas as definições de tipo para a API de Elementos Visuais Personalizados do Power BI.

Adicione `powerbi-visuals-api` às dependências do seu projeto ao executar este comando:

```cmd
npm install --save-dev powerbi-visuals-api
```

Além disso, remova todas as ligações para as antigas definições de tipo da API, pois o webpack inclui automaticamente todos os tipos da `powerbi-visuals-api`. As alterações correspondentes estão no [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) e no [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>Atualizar o tsconfig.json

Para utilizar módulos externos, altere a opção `out` para `outDir`. Por exemplo, utilize `"outDir": "./.tmp/build/",` em vez de `"out": "./.tmp/build/visual.js",`.

Esta alteração é necessária, uma vez que os ficheiros TypeScript serão compilados em ficheiros JavaScript de forma independente. É por isso que já não precisa de especificar o ficheiro visual.js como uma saída.

Além disso, também pode alterar a opção `target` para `ES6`, caso queira utilizar o JavaScript moderno como uma saída. Esta alteração é [opcional](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Atualizar os utilitários dos elementos visuais personalizados

Se utilizar um dos pacotes [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), atualize-os também para a versão mais recente. Para tal, execute este comando:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Por exemplo, para obter a nova versão com os módulos externos do TypeScript, execute: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Para obter um exemplo de um elemento visual que utilize todos os pacotes `powerbi-visuals-utils`, veja o [MekkoChart repository](https://github.com/Microsoft/powerbi-visuals-mekkochart) (repositório MekkoChart).

## <a name="remove-the-globalizejs-library"></a>Remover a biblioteca de código Globalize.js

A nova versão do [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) inclui a biblioteca de código Globalize.js. Portanto, não precisa de incluir esta biblioteca manualmente no projeto. Todas as localizações necessárias serão automaticamente adicionadas ao pacote final.

## <a name="configure-loading-of-external-libraries"></a>Configurar o carregamento das bibliotecas de código externas

Inclua novos ficheiros JavaScript depois das bibliotecas na matriz `externalJS` de `pbiviz.json`. Por exemplo:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importe as bibliotecas do seu código fonte. Por exemplo, para `lodash-es`, utilize esta instrução:

```JS
import * as _ from "lodash-es";
```

No exemplo anterior, `_` é a variável global da biblioteca `lodash`.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Fazer alterações nas origens dos elementos visuais

A principal alteração que tem de fazer é converter módulos internos em externos. Não pode utilizar módulos externos dentro de módulos internos.

Segue-se uma descrição detalhada das alterações a serem feitas. As modificações são descritas no contexto do exemplo de código do elemento visual personalizado Bar Chart:

1. Remova todas as definições do módulo de cada ficheiro do [código fonte](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3):

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importe as definições da API de elementos visuais personalizados do Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importe as interfaces ou classes necessárias](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) do módulo interno do `powerbi`.

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

4. [Importe a biblioteca de código D3.js](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    Pode importar apenas os módulos necessários da biblioteca de código D3:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importe os utilitários, as classes e as interfaces definidos no projeto de elementos visuais](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) para o ficheiro de origem principal:

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importar os estilos CSS

A nova versão das ferramentas permite-lhe importar os estilos `CSS` e `Less` diretamente para o código TypeScript. Agora, a [secção de estilos](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) que foi utilizada anteriormente é ignorada pelo compilador.

Para utilizar a folha de estilos, abra o ficheiro TypeScript (.ts) principal e adicione esta linha:  

```typescript
import "./../style/visual.less";
```  

Os estilos `CSS` e `Less` serão compilados automaticamente.

### <a name="externaljs-section-in-pbivizjson"></a>Secção externalJS no pbiviz.json

As ferramentas [não requerem uma lista de `externalJS` bibliotecas de código](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) para serem carregadas para o conjunto de elementos visuais, uma vez que o webpack inclui todas as bibliotecas importadas.

> [!NOTE]
> Em `pbiviz.json`, deixe a secção `externalJS` vazia.

Utilize o comando típico `npm run package` para criar o pacote de elementos visuais ou o comando `npm run start` para iniciar o servidor de programação.

## <a name="update-the-d3js-library-to-version-5"></a>Atualizar a biblioteca de código D3.js para a versão 5

Com as novas ferramentas de elementos visuais, pode começar a utilizar a nova versão da biblioteca de código D3.js. Execute estes comandos para atualizar a D3 no projeto de elementos visuais:

- `npm install --save d3@5` para instalar a nova D3.js.

- `npm install --save-dev @types/d3@5` para instalar as novas definições de tipo para a D3.js.

> [!IMPORTANT]
> A D3 versão 5 apresenta várias alterações interruptivas.

Modifique o seu código para utilizar a nova D3.js:

- A interface `d3.Selection<T>` [foi alterada](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) para `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- Não pode aplicar vários atributos através de uma única chamada para o método `attr`. Em alternativa, tem de [passar cada atributo numa chamada separada](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) para `attr`. Faça também [chamadas separadas para o método `style`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247).

- A D3.js versão 4 apresentou o novo método `merge`. Este método é frequentemente utilizado para intercalar seleções de `enter` e de `update` depois de uma operação de associação de dados. Para utilizar a D3 corretamente, [chame o método `merge`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[Saiba mais](https://github.com/d3/d3/blob/master/CHANGES.md) sobre as alterações na biblioteca de código D3.js.

## <a name="install-babel-and-core-js"></a>Instalar o Babel e o core-js

A partir da versão 3.1, as ferramentas de elementos visuais utilizam o Babel para compilar o código JavaScript moderno na antiga ECMAScript 5 (ES5) para suportar uma grande variedade de browsers.

A opção Babel está ativada por predefinição, mas tem de importar o pacote [`core-js`](https://www.npmjs.com/package/core-js) manualmente. Execute este comando para instalar o pacote:

```cmd
npm install --save core-js
```

Em seguida, importe o pacote no ponto inicial do código do elemento visual. Normalmente, esse é o ficheiro "src/visual.ts".

```JS
import "core-js/stable";
```

Saiba mais sobre o Babel [na documentação](https://babeljs.io/docs/en/).
