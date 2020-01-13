---
title: Power BI visual project structure (Estrutura de projeto de elementos visuais do Power BI)
description: O artigo descreve uma estrutura de projetos de elementos visuais
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542099"
---
# <a name="power-bi-visual-project-structure"></a>Power BI visual project structure (Estrutura de projeto de elementos visuais do Power BI)

Depois de executar o novo `<visual project name>` do pbiviz, a ferramenta cria a estrutura básica de ficheiros e pastas na pasta `<visual project name>`.

## <a name="visual-project-structure"></a>Estrutura de projetos de elementos visuais

![Estrutura de projetos de elementos visuais](./media/visual-project-structure.png)

* `.vscode` – contém as definições do projeto para VS Code. Para configurar a sua área de trabalho, edite o ficheiro `.vscode/settings.json`. Leia mais [sobre as definições do VS Code na documentação](https://code.visualstudio.com/docs/getstarted/settings)

* A pasta `assets` apenas contém o ficheiro `icon.png`. A ferramenta utiliza este ficheiro como um ícone do elemento visual no painel Visualizações do Power BI.

    ![Painel Visualizações](./media/visualization-pane-analytics-tab.png)

* A pasta `node_modules` contém todos os pacotes [instalados pelo Node Package Manager](https://docs.npmjs.com/files/folders.html).

* A pasta `src` contém o código fonte do elemento visual. Por predefinição, a ferramenta cria dois ficheiros:

  * `visual.ts` – o código fonte principal do elemento visual.

  * `settings.ts` – o código das definições para o elemento visual. As classes que se encontram no ficheiro simplificam o [trabalho com as propriedades do elemento visual](./objects-properties.md#properties).

* A pasta `style` contém o ficheiro `visual.less` com estilos para o elemento visual.

* A pasta `capabilities.json` contém as propriedades e definições principais para o elemento visual. Permite que o elemento visual declare funcionalidades, objetos, propriedades e mapeamento de vista de dados suportados.

    Leia mais [sobre as funcionalidades na documentação](./capabilities.md).

* `package-lock.json` é gerado automaticamente para qualquer operação na qual npm modifique a árvore de `node_modules` ou `package.json`.

    Leia mais [sobre o `package-lock.json` na documentação oficial do NPM](https://docs.npmjs.com/files/package-lock.json).

* `package.json` descreve o pacote do projeto. Normalmente, contém informações sobre o projeto, os seus autores, a descrição e as dependências do projeto.

    Leia mais [sobre o `package.json` na documentação oficial do NPM](https://docs.npmjs.com/files/package.json.html).

* `pbiviz.json` contém os metadados do elemento visual. Especifique os metadados do elemento visual neste ficheiro.

    Conteúdo típico do ficheiro:

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    em que

  * `name` – nome interno do elemento visual.

  * `displayName` – nome do elemento visual na interface de utilizador do Power BI.

  * `guid` – ID exclusivo do elemento visual.

  * `visualClassName` – nome da principal classe para o elemento visual. O Power BI cria a instância desta classe para começar a utilizar o elemento visual no relatório do Power BI.

  * `version` – número de versão do elemento visual.

  * `author` – contém o nome e o contacto de e-mail do autor.

  * `icon` em `assets` – caminho do ficheiro de ícone para o elemento visual.

  * `externalJS` contém caminhos para bibliotecas JS utilizadas no elemento visual.

    > [!IMPORTANT]
    > A versão mais recente da ferramenta (3.X.X ou posterior) deixou de utilizar `externalJS`.

  * `style` é o caminho dos ficheiros dos estilos.

  * `capabilities` é o caminho do ficheiro `capabilities.json`.

  * `dependencies` é o caminho do ficheiro `dependencies.json`. `dependencies.json` contém informações sobre pacotes de R utilizados em elementos visuais baseados em R.

  * `stringResources` é uma matriz de caminhos de ficheiros com localizações.

  Leia mais [sobre a localização em elementos visuais na documentação](./localization.md)

* `tsconfig.json` é o ficheiro de configuração para TypeScript.

    Leia mais [sobre a configuração de TypeScript na documentação oficial](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    O ficheiro `tsconfig.json` na secção `files` tem de conter o caminho do ficheiro *.ts no qual a classe principal do elemento visual está localizada especificada na propriedade `visualClassName` do ficheiro `pbiviz.json`.

* O ficheiro `tslint.json` contém a configuração de TSLint.

    Leia mais [sobre a configuração de TSLint na documentação oficial](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>Próximos passos

* Leia mais [sobre o conceito de elemento visual](./power-bi-visuals-concept.md) para compreender melhor a forma como o elemento visual, o utilizador e o Power BI interagem entre si.

* Comece a criar de raiz os seus próprios elementos visuais do Power BI [com o guia passo a passo](./custom-visual-develop-tutorial.md).
