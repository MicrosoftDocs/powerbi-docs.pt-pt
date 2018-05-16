---
title: Ordenação por coluna no Power BI Desktop
description: Ordenação por coluna no Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: monitoring
qualitydate: 05/01/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: acd621a1763e29fc66a017294cc4d63008900a4f
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/04/2018
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Ordenação por coluna no Power BI Desktop
No **Power BI Desktop** e no **serviço Power BI**, pode alterar o aspeto de um elemento visual ao ordená-lo por campos de dados diferentes. Ao alterar a forma como ordena um elemento visual, pode destacar as informações que pretende transmitir e certificar-se de que o elemento visual reflete qualquer tendência (ou ênfase) que pretende transmitir.

Se está a utilizar dados numéricos (como volume de vendas) ou dados de texto (como nomes de estado), pode ordenar as visualizações como pretender e dar o aspeto que desejar.  O **Power BI** oferece bastante flexibilidade para ordenação e menus rápidos para utilização. Em qualquer elemento visual, selecione o menu de reticências (…) e **Ordenar Por** e, em seguida, selecione o campo em que pretende ordenar, conforme mostrado na imagem seguinte.

![](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="more-depth-and-an-example"></a>Mais profundidade e um exemplo
Vamos analisar um exemplo que tem mais profundidade e ver como funciona no **Power BI Desktop**.

A visualização seguinte lista os principais 15 estados em termos de meteorologia (a maioria dos dias de sol, classificados de 1 a 50, sendo 1 os dias com mais sol). Eis como se parece a visualização antes de fazer qualquer ordenação.

![](media/desktop-sort-by-column/sortbycolumn_1.png)

O elemento visual está atualmente ordenado por **Custo de vida** - podemos dizê-lo ao corresponder a cor das barras descendentes à legenda, mas há uma forma melhor de determinar a coluna de ordenação atual: a caixa de diálogo **Ordenar por**, disponível no menu de reticências (…) no canto superior direito do elemento visual. Quando selecionamos as reticências, vemos o seguinte:

![](media/desktop-sort-by-column/sortbycolumn_2.png)

Existem alguns itens a reparar no menu que aparece quando seleciona as reticências:

* A barra amarela junto ao **Custo de vida** e o facto de que o **Custo de vida** está em negrito
* O pequeno ícone junto às palavras **Ordenar por**, que mostra **Z/A** (Z acima de A) e uma seta para baixo.

Vamos analisar cada um deles independentemente nas próximas duas secções.

## <a name="selecting-which-column-to-use-for-sorting"></a>Selecionar as colunas a utilizar para ordenação
Reparou na barra amarela junto ao **Custo de vida** no menu **Ordenar por**, que indicou que o elemento visual estava a utilizar a coluna **Custo de vida** para ordenar o elemento visual. Ordenar por outra coluna é fácil - basta selecionar as reticências para mostrar o menu **Ordenar por** e, em seguida, selecionar outra coluna. É tão simples quanto isso.

Na imagem seguinte, selecionámos **Bem-estar da comunidade** como a coluna pela qual pretendemos ordenar. Essa coluna é uma das linhas do elemento visual, em vez de uma das barras. Eis como se parece depois de selecionar-mos **Bem-estar da comunidade**.

![](media/desktop-sort-by-column/sortbycolumn_3.png)

Repare como o elemento visual foi alterado. Os valores estão agora ordenados do valor mais alto do "Bem-estar da comunidade" (neste caso RI para Rhode Island) para esses estados incluídos neste elemento visual, até ao AZ (para Arizona), que tem o valor mais baixo. Lembre-se que o gráfico geral ainda inclui apenas os 15 estados com os dias mais solarengos - ordenámos apenas com base na outra coluna incluída no elemento visual.

Mas e se queremos ordenar de forma ascendente, em vez de descendente? A secção seguinte mostra como é tão simples.

## <a name="selecting-the-sort-order---smallest-to-largest-largest-to-smallest"></a>Selecionar a sequência de ordenação - da mais pequena para a maior, da maior para a mais pequena
Quando examinamos mais de perto no menu **Ordenar Por** na imagem anterior, vemos que o ícone junto a **Ordenar Por** mostra **Z/A** (Z acima de A). Veja:

![](media/desktop-sort-by-column/sortbycolumn_4.png)

Quando é apresentado **Z/A**, significa que o visual está a ser ordenado pela coluna selecionada, do valor maior para o mais pequeno. Pretende alterar esta ordem? Não há problema - basta tocar ou clicar no ícone **Z/A** e ele altera a sequência de ordenação para **A/Z** e ordena o elemento visual (com base na coluna selecionada) do valor mais pequeno para o maior.

Aqui está o nosso mesmo elemento visual, desta vez depois de tocar no ícone **Z/A** no menu **Ordenar Por** para alterar a ordenação. Tenha em atenção que AZ (Arizona) é agora o primeiro estado listado e RI (Rhode Island) é o último - a ordenação oposta à anterior.

![](media/desktop-sort-by-column/sortbycolumn_5.png)

Pode ordenar por qualquer coluna incluída no elemento visual - podemos selecionar facilmente a Meteorologia como a coluna pela qual queremos ordenar e selecionar **Z/A** no menu **Ordenar Por**, para mostrar os estados com mais sol em primeiro lugar (valor mais alto - Meteorologia equivale a dias de sol neste modelo de dados) e ainda manter outras colunas no elemento visual, no entanto, elas aplicam-se a esse estado. Eis como se parece o elemento visual com essas definições.

![](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Ordenação utiliza botão de Ordenar Por Coluna
Existe outra forma para ordenar os dados, que é através do botão **Ordenar por Coluna** no friso **Modelação**.

![](media/desktop-sort-by-column/sortbycolumn_8.png)

Esta abordagem para ordenação exige que selecione uma coluna no painel **Campos** e, em seguida, selecione o botão **Ordenar por Coluna**, para escolher como (por qual coluna) pretende ordenar o elemento visual. Tem de selecionar a coluna (campo) que pretende ordenar a partir do painel **Campos**, para ativar o botão **Ordenar por Coluna** - caso contrário, o botão está inativo.

Vamos ver um exemplo comum: tem dados de cada dia da semana e pretende ordenar com base na ordem cronológica. Os passos seguintes mostram-lhe como pode fazê-lo.

1. Em primeiro lugar, tenha em atenção que quando o elemento visual está selecionado, mas não está selecionada nenhuma coluna no painel **Campos**, o botão **Ordenar por Coluna** está inativo (cinzento).
   
   ![](media/desktop-sort-by-column/sortbycolumn_9a.png)
2. Quando selecionamos a coluna pela qual pretendemos ordenar, no painel **Campos**, o botão **Ordenar por Coluna** fica ativo.
   
   ![](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Agora, com o elemento visual selecionado, podemos selecionar *Dia da Semana*, em vez da predefinição (*Nome do Dia*), e o elemento visual ordena agora pela ordem que queremos: por dia da semana.
   
   ![](media/desktop-sort-by-column/sortbycolumn_11.png)

E já está! Lembre-se de que tem de selecionar uma coluna no painel **Campos** para o botão **Ordenar por Coluna** ficar ativo.

## <a name="getting-back-to-default-column-for-sorting"></a>Voltar à coluna predefinida para ordenação
Pode ordenar por qualquer coluna que pretender, mas por vezes poderá querer que o elemento visual regresse à coluna de ordenação predefinida. Sem problemas. Para um elemento visual que tem uma coluna de ordenação selecionada (uma coluna de ordenação selecionada tem uma barra amarela ao lado no menu **Ordenar Por**, conforme aprendemos), basta abrir o menu **Ordenar Por** e selecionar essa coluna novamente, e a visualização regressa à respetiva coluna de ordenação predefinida.

Por exemplo, aqui está o nosso gráfico anterior:

![](media/desktop-sort-by-column/sortbycolumn_6.png)

Quando regressamos ao menu e selecionamos **Meteorologia** novamente, o elemento visual tem como predefinição ser ordenado por ordem alfabética por **Código de Estado**, conforme mostrado na imagem seguinte.

![](media/desktop-sort-by-column/sortbycolumn_7.png)

Com tantas opções para ordenar os elementos visuais, é tão simples criar o gráfico ou a imagem que pretende.

