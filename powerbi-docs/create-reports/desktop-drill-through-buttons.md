---
title: Criar um botão de exploração no Power BI
description: Pode adicionar botões de exploração em relatórios do Power BI que fazem com que os seus relatórios se comportem como aplicações e aprofundam a cativação dos utilizadores.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d3cb3c8093446d4417a59c5f64ab6b85a765e3c8
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83301523"
---
# <a name="create-a-drill-through-button-in-power-bi-preview"></a>Criar um botão de exploração no Power BI (pré-visualização)

Quando cria um botão no Power BI, pode selecionar a ação **Explorar (Pré-visualização)** . Este tipo de ação cria um botão que explora uma página em destaque para obter detalhes filtrados para um contexto específico.

Um botão de exploração pode ser útil se quiser aumentar a capacidade de deteção de cenários de exploração importantes nos seus relatórios.

Neste exemplo, após o utilizador selecionar a barra do Word no gráfico, é ativado o botão **Ver detalhes**.

![Botão Ver detalhes](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Quando o utilizador seleciona o botão **Ver detalhes**, explora a página Market Basket Analysis. Como pode ver no elemento visual à esquerda, a página de exploração está agora filtrada para o Word.

![Elemento visual filtrado](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Configurar um botão de exploração

Para configurar um botão de exploração, primeiro tem de [configurar uma página de exploração válida](desktop-drillthrough.md) no seu relatório. Em seguida, tem de criar um botão com o tipo de ação **Explorar** e selecionar a página de exploração como **Destino**.

Como o botão de exploração tem dois estados (quando a exploração está ativa e quando a exploração está inativa), verá que existem duas opções de descrição.

![Configurar o botão de exploração](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Se deixar as caixas das descrições em branco, o Power BI irá gerar descrições automaticamente. Essas descrições são baseadas no destino e nos campos de exploração.

Segue-se um exemplo da descrição gerada automaticamente quando o botão está inativo:

"Para explorar Market Basket Analysis (a página de destino), selecione um ponto de dados único a partir de Product (o campo de exploração)."

![Descrição gerada automaticamente inativa](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Segue-se um exemplo da descrição gerada automaticamente quando o botão está ativo:

"Clique para explorar Market Basket Analysis (a página de destino)."

![Descrição gerada automaticamente ativa](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

No entanto, se quiser fornecer descrições personalizadas, pode inserir uma cadeia estática. Ainda não suportamos a formatação condicional de descrições.

Pode utilizar a formatação condicional para alterar o texto do botão com base no valor selecionado de um campo. Para fazê-lo, tem de criar uma medida que tenha como resultado a cadeia pretendida, com base na função DAX SELECTEDVALUE.

Segue-se uma medida de exemplo que devolve "Ver detalhes de produto" se um único valor de Product NÃO for selecionado; caso contrário, devolve "Ver detalhes de [Product selecionado]":

```
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0), "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Assim que criar esta medida, selecione a opção **Formatação condicional** para o texto do botão:

![Selecionar a opção Formatação condicional](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Em seguida, selecione a medida que criou para o texto do botão:

![Valor com base no campo](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Quando um único produto for selecionado, o texto do botão será:

"Ver detalhes de Word"

![Quando um único valor for selecionado](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Quando não há produtos selecionados ou mais de um produto é selecionado, o botão é desativado e o texto do botão será:

"Ver detalhes de produto"

![Quando múltiplos valores forem selecionados](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="pass-filter-context"></a>Transmitir o contexto do filtro

O botão funciona como a exploração normal, pelo que também pode transmitir filtros em campos adicionais ao efetuar a filtragem cruzada dos elementos visuais que contêm o campo de exploração. Por exemplo, ao utilizar **Ctrl** + **clique** e a filtragem cruzada, pode transmitir múltiplos filtros em Store para a página de exploração, visto que as suas seleções efetuam a filtragem cruzada do elemento visual que contém Product, o campo de exploração:

![Transmitir o contexto do filtro](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

Quando seleciona o botão de exploração, vê filtros em Store e Product a serem transmitidos para a página de destino:

![Filtros nesta página](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Contexto de filtro ambíguo

Como o botão de exploração não está associado a um único elemento visual, se a sua seleção for ambígua, o botão será desativado.

Neste exemplo, o botão está inativo porque os dois elementos visuais contêm uma única seleção em Product. Há ambiguidade em relação ao ponto de dados de um elemento visual ao qual se associa a ação de exploração:

![Contexto de filtro ambíguo](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="limitations"></a>Limitações

- Este botão não permite múltiplos destinos com um único botão.
- Este botão só suporta explorações no mesmo relatório, ou seja, não suporta a exploração de relatórios cruzados.
- A formatação de estado desativada para o botão está associada às classes de cores no tema do seu relatório. Saiba mais sobre as [classes de cores](desktop-report-themes.md#setting-structural-colors).
- A ação de exploração funciona com todos os elementos visuais incorporados e *alguns* elementos visuais importados do AppSource. No entanto, não é garantido que funcione com *todos* os elementos visuais importados do AppSource.

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre funcionalidades semelhantes ou como interagir com botões, veja os artigos seguintes:

* [Criar botões](desktop-buttons.md)
* [Utilizar a exploração em relatórios do Power BI](desktop-drillthrough.md)
* [Utilizar marcadores para partilhar informações e criar histórias no Power BI](desktop-bookmarks.md)

