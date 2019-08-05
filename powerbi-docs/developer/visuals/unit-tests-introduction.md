---
title: Introdução aos testes de unidades
description: Como escrever testes de unidades para o projeto de elementos visuais do Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 4b16eaad9b541bf6e5d8df49ffda99d9bbd5bbf2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424545"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>Tutorial: adicionar testes de unidades para projetos de elementos visuais do Power BI

Este tutorial descreve as noções básicas da escrita de testes de unidades para os seus elementos visuais do Power BI.

Neste tutorial, vamos considerar:

* como utilizar a execução de testes karma.js e a arquitetura de teste jasmine.js;
* como utilizar o pacote powerbi-visuals-utils-testutils;
* como o conjunto de simulações e falsificações ajuda a simplificar os testes de unidades para elementos visuais do Power BI.

## <a name="prerequisites"></a>Pré-requisitos

* Tem de ter o projeto de elementos visuais do Power BI
* Ambiente Node. JS configurado

## <a name="install-and-configure-karmajs-and-jasmine"></a>Instalar e configurar karma.js e jasmine

Adicione as bibliotecas necessárias a package.json na secção `devDependencies`:

```json
"@babel/polyfill": "^7.2.5",
"@types/d3": "5.5.0",
"@types/jasmine": "2.5.37",
"@types/jasmine-jquery": "1.5.28",
"@types/jquery": "2.0.41",
"@types/karma": "3.0.0",
"@types/lodash-es": "4.17.1",
"coveralls": "3.0.2",
"istanbul-instrumenter-loader": "^3.0.1",
"jasmine": "2.5.2",
"jasmine-core": "2.5.2",
"jasmine-jquery": "2.1.1",
"jquery": "3.1.1",
"karma": "3.1.1",
"karma-chrome-launcher": "2.2.0",
"karma-coverage": "1.1.2",
"karma-coverage-istanbul-reporter": "^2.0.4",
"karma-jasmine": "2.0.1",
"karma-junit-reporter": "^1.2.0",
"karma-sourcemap-loader": "^0.3.7",
"karma-typescript": "^3.0.13",
"karma-typescript-preprocessor": "0.4.0",
"karma-webpack": "3.0.5",
"puppeteer": "1.17.0",
"style-loader": "0.23.1",
"ts-loader": "5.3.0",
"ts-node": "7.0.1",
"tslint": "^5.12.0",
"webpack": "4.26.0"
```

Veja a descrição abaixo para saber mais sobre o pacote.

Guarde `package.json` e execute na linha de comando na localização `package.json`:

```cmd
npm install
```

O gestor de pacotes instalará todos os novos pacotes adicionados a `package.json`.

Para executar testes de unidades, temos de configurar a execução de testes e a configuração `webpack`. Pode encontrar aqui o exemplo de configuração.

Exemplo de `test.webpack.config.js`:

```typescript
const path = require('path');
const webpack = require("webpack");

module.exports = {
    devtool: 'source-map',
    mode: 'development',
    optimization : {
        concatenateModules: false,
        minimize: false
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: /node_modules/
            },
            {
                test: /\.json$/,
                loader: 'json-loader'
            },
            {
                test: /\.tsx?$/i,
                enforce: 'post',
                include: /(src)/,
                exclude: /(node_modules|resources\/js\/vendor)/,
                loader: 'istanbul-instrumenter-loader',
                options: { esModules: true }
            },
            {
                test: /\.less$/,
                use: [
                    {
                        loader: 'style-loader'
                    },
                    {
                        loader: 'css-loader'
                    },
                    {
                        loader: 'less-loader',
                        options: {
                            paths: [path.resolve(__dirname, 'node_modules')]
                        }
                    }
                ]
            }
        ]
    },
    externals: {
        "powerbi-visuals-api": '{}'
    },
    resolve: {
        extensions: ['.tsx', '.ts', '.js', '.css']
    },
    output: {
        path: path.resolve(__dirname, ".tmp/test")
    },
    plugins: [
        new webpack.ProvidePlugin({
            'powerbi-visuals-api': null
        })
    ]
};
```

Exemplo de `karma.conf.ts`:

```typescript
"use strict";

const webpackConfig = require("./test.webpack.config.js");
const tsconfig = require("./test.tsconfig.json");
const path = require("path");

const testRecursivePath = "test/visualTest.ts";
const srcOriginalRecursivePath = "src/**/*.ts";
const coverageFolder = "coverage";

process.env.CHROME_BIN = require("puppeteer").executablePath();

import { Config, ConfigOptions } from "karma";

module.exports = (config: Config) => {
    config.set(<ConfigOptions>{
        mode: "development",
        browserNoActivityTimeout: 100000,
        browsers: ["ChromeHeadless"], // or Chrome to use locally installed Chrome browser
        colors: true,
        frameworks: ["jasmine"],
        reporters: [
            "progress",
            "junit",
            "coverage-istanbul"
        ],
        junitReporter: {
            outputDir: path.join(__dirname, coverageFolder),
            outputFile: "TESTS-report.xml",
            useBrowserName: false
        },
        singleRun: true,
        plugins: [
            "karma-coverage",
            "karma-typescript",
            "karma-webpack",
            "karma-jasmine",
            "karma-sourcemap-loader",
            "karma-chrome-launcher",
            "karma-junit-reporter",
            "karma-coverage-istanbul-reporter"
        ],
        files: [
            "node_modules/jquery/dist/jquery.min.js",
            "node_modules/jasmine-jquery/lib/jasmine-jquery.js",
            {
                pattern: './capabilities.json',
                watched: false,
                served: true,
                included: false
            },
            testRecursivePath,
            {
                pattern: srcOriginalRecursivePath,
                included: false,
                served: true
            }
        ],
        preprocessors: {
            [testRecursivePath]: ["webpack", "coverage"]
        },
        typescriptPreprocessor: {
            options: tsconfig.compilerOptions
        },
        coverageIstanbulReporter: {
            reports: ["html", "lcovonly", "text-summary", "cobertura"],
            dir: path.join(__dirname, coverageFolder),
            'report-config': {
                html: {
                    subdir: 'html-report'
                }
            },
            combineBrowserReports: true,
            fixWebpackSourcePaths: true,
            verbose: false
        },
        coverageReporter: {
            dir: path.join(__dirname, coverageFolder),
            reporters: [
                // reporters not supporting the `file` property
                { type: 'html', subdir: 'html-report' },
                { type: 'lcov', subdir: 'lcov' },
                // reporters supporting the `file` property, use `subdir` to directly
                // output them in the `dir` directory
                { type: 'cobertura', subdir: '.', file: 'cobertura-coverage.xml' },
                { type: 'lcovonly', subdir: '.', file: 'report-lcovonly.txt' },
                { type: 'text-summary', subdir: '.', file: 'text-summary.txt' },
            ]
        },
        mime: {
            "text/x-typescript": ["ts", "tsx"]
        },
        webpack: webpackConfig,
        webpackMiddleware: {
            stats: "errors-only"
        }
    });
};
```

Pode modificar esta configuração se for necessário.

Algumas definições de `karma.conf.js`:

* A variável `recursivePathToTests` localiza o local do código de testes.

* A variável `srcRecursivePath` localiza o código JS de saída após a compilação.

* A variável `srcCssRecursivePath` localiza o CSS de saída após compilar menos ficheiros com estilos.

* A variável `srcOriginalRecursivePath` localiza o código fonte do seu elemento visual.

* A variável `coverageFolder` determina o local onde o relatório de cobertura será criado.

Algumas propriedades de configuração:

* `singleRun: true` – os testes são executados no sistema CI e é suficiente escolher uma vez.
Pode mudar para `false` para depurar os seus testes. O Karma vai continuar a executar o browser e vai permitir-lhe utilizar a consola para depurar.

* `files: [...]` – nesta matriz, pode definir ficheiros a carregar para o browser.
Normalmente, há ficheiros de origem, casos de teste, bibliotecas (jasmine, utilitários de teste). Pode adicionar outros ficheiros à lista caso seja necessário.

* `preprocessors` – nesta secção, pode configurar ações que são executadas antes da execução dos testes de unidades. Há pré-compilação de TypeScript para JS, preparação de ficheiros de mapa de origem e geração de relatório de cobertura de código. Pode desativar `coverage` para depurar os seus testes. A cobertura gera código adicional com vista à verificação do código para a cobertura de teste e complicará os testes de depuração.

**Descrição de todas as configurações que pode encontrar na [documentação](https://karma-runner.github.io/1.0/config/configuration-file.html) de karma.js**

Para simplificar a utilização, pode adicionar o comando de teste em `scripts`.

```json
{
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "typings":"node node_modules/typings/dist/bin.js i",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "pretest": "pbiviz package --resources --no-minify --no-pbiviz --no-plugin",
        "test": "karma start"
    }
    ...
}
```

Está pronto para começar a escrever os seus testes de unidades.

## <a name="simple-unit-test-for-check-dom-element-of-the-visual"></a>Teste de unidades simples para verificar o elemento DOM do elemento visual

Para testar o elemento visual, temos de criar uma instância do elemento visual.

### <a name="creating-visual-instance-builder"></a>Criar o construtor de instâncias de elementos visuais

Adicione o ficheiro `visualBuilder.ts` à pasta `test` com o seguinte código.

```typescript
import {
    VisualBuilderBase
} from "powerbi-visuals-utils-testutils";

import {
    BarChart as VisualClass
} from "../src/visual";

import  powerbi from "powerbi-visuals-api";
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class BarChartBuilder extends VisualBuilderBase<VisualClass> {
    constructor(width: number, height: number) {
        super(width, height);
    }

    protected build(options: VisualConstructorOptions) {
        return new VisualClass(options);
    }

    public get mainElement() {
        return this.element.children("svg.barChart");
    }
}
```

Há um método `build` para criar uma instância do seu elemento visual. `mainElement` é um método Get que devolve uma instância do elemento DOM "raiz" no seu elemento visual. O getter é opcional, mas facilita a escrita do teste de unidades.

Temos, assim, o construtor de uma instância de elemento visual. Vamos escrever o caso de teste. Será um caso de teste para verificar os elementos SVG criados quando o seu elemento visual for apresentado.

### <a name="creating-typescript-file-to-write-test-cases"></a>Criar o ficheiro TypeScript para escrever casos de teste

Adicione o ficheiro `visualTest.ts` para casos de teste com estes códigos:

```typescript
import powerbi from "powerbi-visuals-api";

import { BarChartBuilder } from "./VisualBuilder";

import {
    BarChart as VisualClass
} from "../src/visual";

import VisualBuilder = powerbi.extensibility.visual.test.BarChartBuilder;

describe("BarChart", () => {
    let visualBuilder: VisualBuilder;
    let dataView: DataView;

    beforeEach(() => {
        visualBuilder = new VisualBuilder(500, 500);
    });

    it("root DOM element is created", () => {
        expect(visualBuilder.mainElement).toBeInDOM();
    });
});
```

Há chamadas de vários métodos.

* O método [`describe`](https://jasmine.github.io/api/2.6/global.html#describe) descreve o caso de teste. Num contexto de arquitetura jasmine geralmente chamado de conjunto ou grupo de especificações.

* O método `beforeEach` será chamado antes de cada chamada do método `it`, que foi definido dentro do método [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach).

* `it` define uma única especificação. O método [`it`](https://jasmine.github.io/api/2.6/global.html#it) deve conter uma ou mais `expectations`.

* O método [`expect`](https://jasmine.github.io/api/2.6/global.html#expect) cria a expectativa para uma especificação. Uma especificação será bem-sucedida se todas as expectativas forem aprovadas sem falhas.

* `toBeInDOM` é um dos métodos de correspondência. Pode saber mais sobre isto na [documentação](https://jasmine.github.io/api/2.6/matchers.html) da arquitetura jasmine.

**Leia mais sobre a arquitetura jasmine na [documentação](https://jasmine.github.io/) oficial.**

Em seguida, pode executar o teste de unidades ao escrever um comando na ferramenta de linha de comandos.

Esse teste verifica se o elemento SVG raiz dos elementos visuais é criado.

### <a name="launch-unit-tests"></a>Iniciar testes de unidades

Para executar o teste de unidades, pode escrever este comando na ferramenta de linha de comandos.

```cmd
npm run test
```

`karma.js` executa o browser Chrome e executará o caso de teste.

![KarmaJS iniciado no Chrome](./media/karmajs-chrome.png)

> [!NOTE]
> É necessário instalar o Google Chrome localmente.

Na linha de comandos, obterá a seguinte saída:

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 12:24:30.850:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 12:24:31.059:INFO [launcher]: Starting browser Chrome
23 05 2017 12:24:33.160:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#2meR6hjXFmsE_fjiAAAA with id 5875251
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.194 secs / 0.011 secs)

=============================== Coverage summary ===============================
Statements   : 27.43% ( 65/237 )
Branches     : 19.84% ( 25/126 )
Functions    : 43.86% ( 25/57 )
Lines        : 20.85% ( 44/211 )
================================================================================
```

### <a name="how-to-add-static-data-for-unit-tests"></a>Como adicionar dados estáticos para testes de unidades

Crie o ficheiro `visualData.ts` na pasta `test`. Utilize estes códigos:

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;

import {
    testDataViewBuilder,
    getRandomNumbers
} from "powerbi-visuals-utils-testutils";

export class SampleBarChartDataBuilder extends TestDataViewBuilder {
    public static CategoryColumn: string = "category";
    public static MeasureColumn: string = "measure";

    public constructor() {
        super();
        ...
    }

    public getDataView(columnNames?: string[]): DataView {
        let dateView: any = this.createCategoricalDataViewBuilder([
            ...
        ],
        [
            ...
        ], columnNames).build();

        // there's client side computed maxValue
        let maxLocal = 0;
        this.valuesMeasure.forEach((item) => {
                if (item > maxLocal) {
                    maxLocal = item;
                }
        });
        (<any>dataView).categorical.values[0].maxLocal = maxLocal;
    }
}
```

A classe `SampleBarChartDataBuilder` expande `TestDataViewBuilder` e implementa o método abstrato `getDataView`.

Quando coloca dados em registos de campos de dados, o Power BI produz um objeto de `dataview` categórico baseado nos seus dados.

![Registos de campos](./media/fields-buckets.png)

Nos testes de unidades, não tem as funções nucleares do Power BI para o reproduzir. Contudo, tem de mapear os seus dados estáticos ao `dataview` categórico. A classe `TestDataViewBuilder` irá ajudá-lo.

[Leia mais sobre o DataViewMapping](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md)

No método `getDataView`, basta chamar o método `createCategoricalDataViewBuilder` com os seus dados.

Em [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) do elemento visual `sampleBarChart`, temos o objeto dataRoles e o objeto dataViewMapping.

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": "Measure"
    }
],
"dataViewMappings": [
    {
        "conditions": [
            {
                "category": {
                    "max": 1
                },
                "measure": {
                    "max": 1
                }
            }
        ],
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "select": [
                    {
                        "bind": {
                            "to": "measure"
                        }
                    }
                ]
            }
        }
    }
],
```

Para gerar o mesmo mapeamento, tem de definir os seguintes parâmetros para o método `createCategoricalDataViewBuilder`.

```typescript
([
    {
        source: {
            displayName: "Category",
            queryName: SampleBarChartData.ColumnCategory,
            type: ValueType.fromDescriptor({ text: true }),
            roles: {
                Category: true
            },
        },
        values: this.valuesCategory
    }
],
[
    {
        source: {
            displayName: "Measure",
            isMeasure: true,
            queryName: SampleBarChartData.MeasureColumn,
            type: ValueType.fromDescriptor({ numeric: true }),
            roles: {
                Measure: true
            },
        },
        values: this.valuesMeasure
    },
], columnNames)
```

Em que a matriz de categorias `this.valuesCategory` é:

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

E a matriz de medida `this.valuesMeasure` para cada categoria é: Por exemplo:

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

Agora, pode utilizar a classe `SampleBarChartDataBuilder` no seu teste de unidades.

A classe `ValueType` foi definida no pacote `powerbi-visuals-utils-testutils`. Além disso, o método `createCategoricalDataViewBuilder` necessita da biblioteca `lodash`.

Adicione estes pacotes a dependências.

Em `package.json` na secção `devDependencies`

```json
"lodash-es": "4.17.1",
"powerbi-visuals-utils-testutils": "2.2.0"
```

Chame

```cmd
npm install
```

para instalar a biblioteca `lodash-es`.

Agora pode executar novamente o teste de unidades. Deverá obter esta saída

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 16:19:58.346:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 16:19:58.394:INFO [launcher]: Starting browser Chrome
23 05 2017 16:19:59.873:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#NcNTAGH9hWfGMCuEAAAA with id 3551106
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (1.266 secs / 1.052 secs)

=============================== Coverage summary ===============================
Statements   : 56.72% ( 135/238 )
Branches     : 32.54% ( 41/126 )
Functions    : 66.67% ( 38/57 )
Lines        : 52.83% ( 112/212 )
================================================================================
```

Além disso, deverá ver o browser Chrome iniciado com o seu elemento visual.

![UT inicia no Chrome](./media/karmajs-chrome-ut-runned.png)

Repare que o resumo da cobertura aumentou. Abra `coverage\index.html` para saber mais sobre a cobertura do código atual

![Índice de cobertura UT](./media/code-coverage-index.png)

Ou no âmbito da pasta `src`

![Cobertura da pasta src](./media/code-coverage-src-folder.png)

No âmbito do ficheiro, pode ver o código fonte. Os utilitários `Coverage` marcariam o fundo da linha a vermelho se um código não fosse executado durante a execução dos testes de unidades.

![Cobertura do código do ficheiro visual.ts](./media/code-coverage-visual-src.png)

> [!IMPORTANT]
> Contudo, a cobertura do código não significa que tenha boa cobertura de funcionalidade do elemento visual. Um teste de unidades simples proporcionou mais de 96% da cobertura em `src\visual.ts`.

## <a name="next-steps"></a>Próximos passos

Quando o seu elemento visual estiver pronto, pode enviá-lo para publicação.

[Leia mais sobre como publicar elementos visuais no AppSource](../office-store.md)
