---
title: Criar pequenos múltiplos em Power BI (pré-visualização)
description: Pequenos múltiplos, ou treliça, dividem um visual em várias versões de si mesmo, apresentadas lado a lado, com os seus dados divididos nestas versões por uma dimensão escolhida.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: bc1f890e588227f9d0dc30202474a8f77f93fc38
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617451"
---
# <a name="create-small-multiples-in-power-bi-preview"></a>Criar pequenos múltiplos em Power BI (pré-visualização)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Pequenos múltiplos, ou treliça, divide um visual em várias versões de si mesmo. As versões são apresentadas lado a lado, com dados divididos nestas versões por uma dimensão escolhida. Por exemplo, um pequeno múltiplo poderia dividir um gráfico de colunas "vendas por categoria" através de linhas de produtos ou regiões. Nesta pré-visualização, os múltiplos pequenos têm um pequeno conjunto de capacidades, com mais lançamentos posteriores.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Screenshot de pequenos múltiplos para categoria e região.":::

## <a name="enable-the-preview-feature"></a>Ativar a funcionalidade de pré-visualização

No menu **Ficheiro,** selecione **Opções e definições**  >  **Opções**  >  **Pré-visualizar funcionalidades** e selecione a caixa de verificação **Small multiples.**

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-enable-preview.png" alt-text="Ativar a pré-visualização de pequenos múltiplos.":::

Reinicie o ambiente de trabalho power BI e está pronto para experimentar múltiplos pequenos.

## <a name="create-small-multiples"></a>Criar pequenos múltiplos

Atualmente, pode criar pequenos múltiplos na barra, coluna, linha e gráficos de área. 

Para começar, crie um dos visuais acima e escolha um campo ao longo do qual gostaria de dividir os seus dados. Arraste esse campo para o **poço small multiples** na secção Fields do painel visualizações. O seu gráfico divide×se numa grelha de 2×2, com os dados divididos ao longo da sua dimensão escolhida. A grelha enche-se com os pequenos gráficos múltiplos. São ordenados pela sua ordem de ordem escolhida, da esquerda para a direita, e de cima para baixo.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-two-by-two-grid.png" alt-text="Pequenos múltiplos numa grelha de dois por dois.":::

Os eixos estão sincronizados. Há um eixo Y à esquerda de cada linha, e um eixo X na parte inferior de cada coluna.

Agora que criou pequenos múltiplos, veja como [interage com pequenos múltiplos no Power BI (pré-visualização)](power-bi-visualization-small-multiples-interact.md).

## <a name="format-a-small-multiples-visual"></a>Formato um pequeno multiples visual

Algumas novas opções no painel de formatação permitem-lhe controlar o aspeto e a sensação da grelha.

### <a name="change-the-grid-dimensions"></a>Alterar as dimensões da grelha

Pode alterar as dimensões da grelha na placa de layout Grid:

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-grid-layout-card.png" alt-text="Pequena placa de layout de grelha múltipla.":::

O padrão é uma grelha de 2×2 de pequenos múltiplos, mas pode ajustar o número de linhas e colunas até 6×6. Quaisquer múltiplos que não encaixem na carga da grelha enquanto deslizas para baixo.


### <a name="adjust-the-small-multiples-titles"></a>Ajuste os pequenos títulos de múltiplos

Tal como acontece com outros títulos visuais, pode ajustar o estilo e a posição dos pequenos títulos múltiplos na carta **de títulos múltiplos Small.**

## <a name="preview-limitations"></a>Limitações de pré-visualização

Enquanto a funcionalidade está em pré-visualização, estamos constantemente a trabalhar para garantir que interage bem com o resto das nossas funcionalidades. Aqui estão algumas limitações atuais.

### <a name="fields-pane"></a>Painel Campos

- Data e outras hierarquias contínuas: Digamos que tem um gráfico visual como um gráfico de linha com uma hierarquia de data no eixo X. Quando se faz pequenos múltiplos a partir dele, o Power BI converte esse eixo de um eixo contínuo para um eixo categórico.
- Mostrar itens sem dados: A opção ainda existe, mas o comportamento pode não se alinhar com as suas expectativas.

### <a name="visual-interactions"></a>Interações visuais

- Desloque-se para carregar mais sobre o eixo Categórico: Em visuais padrão com muitas categorias no eixo, quando desloca até ao fim do eixo, o visual carrega mais categorias. Atualmente, um pequeno multiples visual não carrega mais categorias.
- Ordenar pequenos múltiplos por medida: Classificar em múltiplos pequenos é uma nova funcionalidade. Pode estar à espera de classificar os seus pequenos múltiplos por uma medida. Atualmente, só pode classificar os seus múltiplos pela ordem natural do campo.
- Clique direito/menu de contexto -> Analisar: desativado por enquanto.
- Clique à direita/menu de contexto -> Resumir: desativado por enquanto.
- Selecionando vários pontos de dados com seleção retangular: desativado por enquanto.
- Zoom do eixo: desativado por enquanto.
- Acessibilidade: Pode ajustar a navegação de teclados e leituras de ecrã para melhor suportar a nova camada "grid" que os pequenos múltiplos trazem aos visuais. Falta algum comportamento, como a navegação de teclado através da barra de deslocamento do eixo categórico.

### <a name="formatting-options"></a>Opções de formatação

**Geral**

- Toggle responsivo: a opção ainda existe, mas o comportamento pode não se alinhar com as suas expectativas. Uma vez que muitas acomodações móveis estão ligadas a este toggle, a experiência móvel também espelha de perto a experiência que encontra no Power BI Desktop e no serviço Power BI.
- Amostragem de alta densidade: para gráficos de linha, o toggle de amostragem de alta densidade ainda existe, mas não é atualmente suportado por pequenos múltiplos.

**Eixo**

- Rótulos concatenatos: deficientes por enquanto.

**Total de etiquetas**

- Total de etiquetas para gráficos empilhados: desativados por enquanto.

**Deslizador de zoom**

- Deslizadores de zoom: desativado por enquanto.

**Analytics pane (Painel de análise)** 

- Linhas de tendência: desativada por enquanto.
- Previsão: desativado por enquanto.

Formatação dinâmica para etiquetas de destaque: atualmente não suportada.
Disponibilidade de serviço

## <a name="authoring-in-the-power-bi-service"></a>Autoria no serviço Power BI

A autoria de pequenos múltiplos na web não é suportada enquanto a funcionalidade estiver em pré-visualização. Pode ver um relatório com um pequeno multiples visual, e até mesmo formatar o visual. Mas não é possível converter um visual padrão para um pequeno visual de múltiplos no serviço Power BI. Um visual tem que ter já um campo no campo de múltiplos pequenos bem, ou os pequenos múltiplos bem não vão aparecer para esse visual.

## <a name="share-your-feedback"></a>Partilhe os seus comentários

Deixe-nos saber os seus pensamentos sobre os pequenos múltiplos visuais:

- [Comunidade do Power BI](https://community.powerbi.com/)
- [Página de Ideias de Bi de Energia](https://ideas.powerbi.com/ideas/) 

## <a name="next-steps"></a>Passos seguintes

[Interaja com pequenos múltiplos em Power BI (pré-visualização)](power-bi-visualization-small-multiples-interact.md)
