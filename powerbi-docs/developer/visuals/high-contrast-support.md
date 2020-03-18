---
title: O suporte do modo de alto contraste nos elementos visuais do Power BI
description: Este artigo descreve como adicionar o suporte do modo de alto contraste a elementos visuais do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 56ebfeb8c1c52b83f5be0ca9e9db6f312986dd57
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380165"
---
# <a name="high-contrast-mode-support-in-power-bi-visuals"></a>O suporte do modo de alto contraste nos elementos visuais do Power BI

A definição de *alto contraste* do Windows facilita a visualização de texto e aplicações graças à apresentação de cores mais nítidas. Este artigo aborda a forma como adicionar o suporte do modo de alto contraste a elementos visuais do Power BI. Para obter mais informações, veja o [suporte de alto contraste no Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

Para ver uma implementação do suporte de alto contraste, aceda ao [repositório de elementos visuais do PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6).

## <a name="on-initialization"></a>Durante a inicialização

O membro de paleta de cores de `options.host` tem várias propriedades para o modo de alto contraste. Utilize essas propriedades para determinar se o modo de alto contraste está ativo e, caso esteja, escolher as cores a utilizar.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Verificar se o Power BI está no modo de alto contraste

Se `host.colorPalette.isHighContrast` for `true`, significa que o modo de alto contraste está ativo e o elemento visual deverá ser desenhado em conformidade.

### <a name="get-high-contrast-colors"></a>Obter cores de alto contraste

No modo de alto contraste, o seu elemento visual deve limitar-se às seguintes definições:

* A cor **de primeiro plano** é utilizada para desenhar todas as linhas, ícones e texto, bem como para contornar ou preencher formas.
* A cor **de fundo** é utilizada no fundo e como cor de preenchimento de formas contornadas.
* A cor de **primeiro plano – selecionada** é utilizada para indicar um elemento selecionado ou ativo.
* A cor de **hiperligação** é utilizada apenas para o texto de hiperligações.

> [!NOTE]
> Se necessitar de uma cor secundária, a cor de primeiro plano pode ser utilizada com alguma opacidade (os elementos visuais nativos do Power BI têm 40% de opacidade). Faça-o com moderação para que seja fácil ver os detalhes do elemento visual.

Durante a inicialização, pode armazenar os seguintes valores:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

Em alternativa, pode armazenar o objeto `host` durante a inicialização e aceder às propriedades de `colorPalette` relevantes durante a atualização.

## <a name="on-update"></a>Durante a atualização

As implementações específicas do suporte de alto contraste variam consoante o elemento visual e dependem dos detalhes do respetivo design gráfico. De modo a que seja fácil distinguir os detalhes importantes através de cores limitadas, o modo de alto contraste requer, normalmente, um design ligeiramente diferente do modo predefinido.

Os elementos visuais nativos do Power BI seguem estas diretrizes:

* Todos os pontos de dados utilizam a mesma cor (primeiro plano).
* Todo o texto, eixos, setas e linhas, entre outros, utilizam a cor do primeiro plano.
* As formas espessas são desenhadas como contornos com traços espessos (pelo menos dois píxeis) e preenchimento de cor de fundo.
* Caso os pontos de dados sejam relevantes, os mesmos são distinguidos com diferentes formas de marcador e as linhas de dados são distinguidas com um tracejado diferente.
* Se um elemento de dados estiver destacado, todos os outros elementos terão uma opacidade de 40%.
* No caso das segmentações de dados, os elementos de filtro ativos utilizam a cor de primeiro plano selecionada.

Por exemplo, no gráfico de barras de exemplo que se segue, todas as barras são desenhadas com um contorno de primeiro plano e um preenchimento de fundo com dois píxeis de espessura. Compare o aspeto do gráfico com as cores predefinidas e alguns temas de alto contraste:

![Gráfico de Barras de Exemplo com cores padrão](media/high-contrast-support/hc-samplebarchart-standard.png)
![Gráfico de Barras de Exemplo com o tema de cores *Escuro #2*](media/high-contrast-support/hc-samplebarchart-dark2.png)
![Gráfico de Barras de Exemplo com o tema de cores *Branco*](media/high-contrast-support/hc-samplebarchart-white.png)

A próxima secção mostra um local na função `visualTransform` que foi alterado para suportar o alto contraste. É chamado como parte da composição durante a atualização.

### <a name="before"></a>Antes de

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Depois de

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
