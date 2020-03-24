---
title: Esquemas personalizados com conteúdo incorporado do Power BI
description: Saiba mais sobre esquemas personalizados ao incorporar conteúdo do Power BI na sua aplicação.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: reference
ms.date: 12/19/2017
ms.openlocfilehash: e114c208093c9f3401c43e9ea44502e65d6d84fd
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79493210"
---
# <a name="custom-layouts"></a>Esquemas personalizados

Utilize o esquema personalizado para incorporar um relatório com um esquema diferente do que num relatório original. Definir um novo esquema varia entre definir apenas um tamanho de página, controlar os tamanhos dos elementos visuais ou a posição e a visibilidade.

Para definir um esquema personalizado, defina um objeto de esquema personalizado e transmita-o para o objeto de definições na definição incorporada. Além disso, defina LayoutType como Personalizado. Para obter mais informações, veja [Embed Configuration Details (Detalhes da Configuração Incorporada)](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details).

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom,
            customLayout: {...}
    }
};
```

## <a name="object-definition"></a>Definição do Objeto

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`: utilize o tamanho da página para controlar o tamanho da área da tela (isto é, a área em branco do relatório).
- `displayOptions`: os valores possíveis são: FitToWidth, FitToPage ou ActualSize. Controla como dimensionar a tela para ajustar ao iframe.
- `pagesLayout`: controla o esquema de cada elemento visual. veja PagesLayout para obter mais detalhes.

## <a name="pages-layout"></a>Esquema de páginas

Definir um objeto de esquema de páginas é basicamente definir um esquema para cada página e, para cada página, define um esquema para cada elemento visual.
O PageLayout é opcional. Se não definir um esquema para uma página, será aplicado o esquema predefinido (que é guardado no relatório).

O pagesLayout é um mapa do nome de página para o objeto PageLayout. Definição:

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

O PageLayout contém um mapa de esquema visual, que mapeia cada nome do elemento visual para um objeto de esquema visual:

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>Esquema do elemento visual

Para definir um esquema do elemento visual, transmita uma nova posição e tamanho e um novo estado de visibilidade.

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`: define a nova posição do elemento visual.
- `width`, altura: define o novo tamanho do elemento visual.
- `displayState`: define a visibilidade do elemento visual.

## <a name="update-layout"></a>Atualizar o esquema

Pode utilizar o método updateSettings para atualizar o esquema do relatório em qualquer altura enquanto o relatório é carregado. Veja [Definições de Atualização](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings).

## <a name="code-example"></a>Exemplo de código

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;

var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom,
            customLayout: {
                pageSize: {
                    type: models.PageSizeType.Custom,
                    width: 1600,
                    height: 1200
                }
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};

// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');

// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);
```

## <a name="see-also"></a>Veja também

[Incorporar os dashboards, os relatórios e os mosaicos do Power BI](embed-sample-for-customers.md)   
[Pergunte à Comunidade do Power BI](https://community.powerbi.com/)