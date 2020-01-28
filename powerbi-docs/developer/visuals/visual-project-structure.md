---
title: Power BI visual project structure (Estrutura de projeto de elementos visuais do Power BI)
description: Este artigo descreve a pasta e a estrutura de ficheiros de um projeto de elemento visual do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 16e7a317102602ffb4faf04da0ed2cae588a2a4d
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925519"
---
# <a name="power-bi-visual-project-structure"></a>Power BI visual project structure (Estrutura de projeto de elementos visuais do Power BI)

A melhor maneira de começar a criar um novo elemento visual do Power BI é utilizar a ferramenta [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) dos elementos visuais do Power BI.

Para criar um novo elemento visual, navegue para o diretório onde quer que o elemento visual do Power BI resida e execute o comando:

`pbiviz new <visual project name>`

Executar este comando cria uma pasta para os elementos visuais do Power BI que contém os seguintes ficheiros:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Descrição dos ficheiros e das pastas

Esta secção apresenta informações para cada ficheiro e pasta no diretório que a ferramenta **pbiciz** dos elementos visuais do Power BI cria.  

### <a name="vscode"></a>.vscode

Esta pasta contém as definições do projeto do VS Code.

Para configurar a área de trabalho, edite o ficheiro `.vscode/settings.json`.

Para obter mais informações, veja [User and Workspace Settings](https://code.visualstudio.com/docs/getstarted/settings) (Definições da Área de Trabalho e do Utilizador)

### <a name="assets"></a>recursos

Esta pasta contém o ficheiro `icon.png`.

A ferramenta dos elementos visuais do Power BI utiliza este ficheiro como o novo ícone de elemento visual do Power BI no painel de visualização do Power BI.

<!--- ![Visualization pane](./media/visualization-pane-analytics-tab.png) --->

### <a name="src"></a>src

Esta pasta contém o código fonte do elemento visual.

Nesta pasta, a ferramenta dos elementos visuais do Power BI cria os seguintes ficheiros:
* `visual.ts` – o principal código fonte do elemento visual.
* `settings.ts` – o código das definições do elemento visual. As classes no ficheiro oferecem uma interface para definir as [propriedades do elemento visual](./objects-properties.md#properties).

### <a name="style"></a>estilo

Esta pasta contém o ficheiro `visual.less`, que contém os estilos do elemento visual.

### <a name="capabilitiesjson"></a>capabilities.json

Este ficheiro contém as principais propriedades e definições (ou [capacidades](./capabilities.md)) do elemento visual. Permite que o elemento visual declare funcionalidades, objetos, propriedades e [mapeamento de vista de dados](./dataview-mappings.md). suportados.

### <a name="package-lockjson"></a>package-lock.json

Este ficheiro é gerado automaticamente para todas as operações na qual *npm* modifica a árvore `node_modules` ou o ficheiro `package.json`.

Para obter mais informações sobre este ficheiro, veja a documentação [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) oficial.

### <a name="packagejson"></a>package.json

Este ficheiro descreve o pacote do projeto. Contém informações sobre o projeto, como os autores, a descrição e as dependências do projeto.

Para obter mais informações sobre este ficheiro, veja a documentação [npm-package.json](https://docs.npmjs.com/files/package.json.html) oficial.

### <a name="pbivizjson"></a>pbiviz.json

Este ficheiro contém os metadados do elemento visual.

Para ver um exemplo de ficheiro `pbiviz.json` com comentários que descrevem as entradas de metadados, veja a secção [entradas de metadados](#metadata-entries).

### <a name="tsconfigjson"></a>tsconfig.json

Um ficheiro de configuração para [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

Este ficheiro deve conter o caminho para o ficheiro **\*.ts** no qual a classe principal do elemento visual está localizada, conforme especificado na propriedade `visualClassName` do ficheiro `pbiviz.json`.

### <a name="tslintjson"></a>tslint.json

Este ficheiro contém a [configuração TSLint](https://palantir.github.io/tslint/usage/configuration/).

## <a name="metadata-entries"></a>Entradas de metadados

Os comentários na legenda do código seguinte, no ficheiro `pbiviz.json`, descrevem as entradas de metadados.

> [!NOTE]
> * A partir da versão 3.x.x da ferramenta **pbiciz**, `externalJS` não é suportado.
> * Para suporte de localização, [adicione a localização do Power BI ao elemento visual](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Próximos passos

* Para compreender as interações entre um elemento visual, um utilizador e o Power BI, veja o [Conceito do elemento visual do Power BI](./power-bi-visuals-concept.md).

* Comece a criar de raiz os seus próprios elementos visuais do Power BI, com o [guia passo a passo](./custom-visual-develop-tutorial.md).