---
title: Dicas e truques para formatação com cores no Power BI
description: Dicas e truques para formatação com cores no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 09c505d114eaa951978f23061d9c79c1b6870fad
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983376"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Dicas e truques para formatação com cores no Power BI
O Power BI fornece diversas maneiras de personalizar os painéis e relatórios. Este artigo detalha uma coleção de dicas que podem tornar suas visualizações do Power BI mais convincentes, interessantes e personalizadas para suas necessidades.

As dicas a seguir são fornecidas. Há outra dica excelente? Ótimo! Envie para nós e vermos sobre adicioná-la à lista.

* Alterar a cor de um único ponto de dados
* Basear as cores de um gráfico num valor numérico
* Base da cor de pontos de dados no valor de campo
* Personalizar as cores usadas na escala de cores
* Usar escalas de cores divergentes
* Como anular no Power BI

Para fazer alterações, deve editar um relatório: selecione o **Relatório** no painel **Meu espaço de trabalho**, selecione **Editar relatório** na área do menu superior, conforme mostrado na imagem a seguir. Este exemplo utiliza o **exemplo de Recursos Humanos**.

![tela do relatório com a opção Editar relatório realçada](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

Quando o painel **Visualizações** é mostrado no lado direito do ecrã **Relatório**, está pronto para começar a personalizar.

![relatório com o painel Formatação realçado](media/service-tips-and-tricks-for-color-formatting/power-bi-formatting-pane.png)

## <a name="change-the-color-of-a-single-data-point"></a>Alterar a cor de um único ponto de dados
Às vezes deseja destacar um determinado ponto de dados. Talvez seja os números de vendas para o lançamento de um novo produto, ou pontuações de qualidade aumentadas depois de lançar um novo programa. Com o Power BI, na maioria dos tipos de elementos visuais, pode destacar um determinado ponto de dados ao alterar a sua cor.

A seguinte visualização apresenta as margens de vendas por colaborador, através de cores predefinidas. 

![gráfico de área](media/service-tips-and-tricks-for-color-formatting/power-bi-area-chart.png)

É difícil ver a área da Teresa, por isso vamos utilizar uma cor para dar mais destaque. Eis os passos:

Aumenta a secção **Cores de Dados**. O seguinte aparece.

![Área de seleção Cores de Dados em Formatação](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors.png)


Neste caso, vamos selecionar uma cor escura, mas forte, que não seja semelhante à cor utilizada para a Rita. Selecione a seta para baixo dentro da caixa de cor da Teresa, selecione **Cor Personalizada** e selecione um azul-vivo.

![seleções de cor](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_6.png)

Depois de selecionar, a área da Teresa é mais fácil de distinguir dos outros colaboradores. 

![gráfico de área, a área da Teresa está a azul-vivo](media/service-tips-and-tricks-for-color-formatting/power-bi-color.png)

Mesmo que altera os tipos de visualização, e em seguida, retornar, o Power BI lembra a sua seleção e mantém **Washington** verde.

Também pode alterar a cor de um ponto de dados para mais de um elemento de dados. A imagem a seguir, **Arizona** está vermelha, e **Washington** ainda verde.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_8.png)

Há inúmeras coisas que pode fazer com o Power BI Desktop. Na próxima secção, vamos dar uma olhada em gradientes.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Basear as cores de um gráfico num valor numérico
Os gráficos muitas vezes se beneficiam de configurar a cor com base no valor numérico de um campo. Ao fazer isso, pode mostrar um valor diferente para que é utilizado o tamanho de uma barra e mostrar dois valores num único gráfico. Ou pode utilizar isso para destacar pontos de dados acima (ou abaixo) de um determinado valor – talvez destacando lucratividade baixa.

As seções a seguir demonstram maneiras diferentes de cor de base num valor numérico.

## <a name="base-the-color-of-data-points-on-a-value"></a>Base da cor de pontos de dados num valor
Para alterar a cor com base num valor, arraste o campo que deseja basear a cor para a área **Saturação de Cor** no painel **Campo**. A imagem a seguir, **Lucro antes do imposto** foi arrastada para **Saturação de Cor**. Como podemos ver que, embora **Velo** tenha mais **Vendas Brutas** (uma coluna for maior), **Amarilla** tem uma maior **Lucro antes do imposto** (sua coluna tem mais de saturação de cor).

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_9.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>Personalizar as cores usadas na escala de cores
Pode personalizar as cores usadas na escala de cores. Expanda as **Cores de dados** e verá um gradiente de cores usado para visualizar seus dados. Por predefinição, o valor mais baixo nos seus dados é mapeado para a cor menos saturada e o valor mais alto para a cor mais saturada.

O intervalo de cores é mostrado na barra de gradiente que mostra o espectro entre os valores de cor **mínimo** e **máximo**, com a cor de valoro **mínimo** à esquerda, e **máximo** valor de cor para a direita.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_10.png)

Para alterar o dimensionamento para utilizar um intervalo diferente de cores, selecione a lista suspensa ao lado da cor **mínimo** ou **máximo**, e selecione uma cor. A imagem a seguir mostra a cor **Máxima** alterada para preto e a barra de gradientes mostra o novo espectro de cores entre **Mínimo** e **Máximo**.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

Também pode alterar a forma como os valores mapeiam essas cores. Na imagem a seguir, as cores **mínimo** e **máximo** são definidas como laranja e verde, respectivamente.

Nesta primeira imagem, veja como as barras no gráfico refletem o gradiente mostrado na barra; o valor mais alto é verde, o mais baixo é laranja e cada barra é colorida com um tom do espectro entre verde e laranja.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Agora, vejamos o que acontece se podemos fornecer valores numéricos nas caixas **mínimo** e **máximo** , que estão abaixo do valor dos seletores de cor **mínimo** e **máximo** (mostrados na imagem a seguir). Vamos definir o **Mínimo** para 20 000 000 e o **Máximo** para 20 000 001.

Ao definir esses valores, gradiente não é mais aplicado a valores no gráfico que estão abaixo do **mínimo** ou acima do **máximo**; qualquer barra com um valor acima do valor **máximo** é verde e qualquer barra com um valor baixo do **mínimo** fica em vermelho.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Usar escalas de cores divergentes
Às vezes, seus dados podem ter uma escala divergente naturalmente. Por exemplo, um intervalo de temperatura tem um centro natural em congelamento de ponto e uma pontuação de rentabilidade tem um ponto intermediário natural (zero).

Para utilizar escalas de cores divergentes, deslize o controle deslizante **Divergente** para **Ativado**. Quando **Divergente** estiver ativado, um seletor de cores adicionais e caixa de valor, ambos com o nome **Centro**, mostrado conforme a imagem a seguir.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

Quando o controle deslizante **Divergente** estiver ativo, pode definir as cores **mínimo**, **máximo** e **centro** separadamente. Na imagem a seguir, **Centro** está definido como um, então barras com valores acima de uma são uma gradiente tonalidade de verde e barras abaixo são tons de vermelho.

## <a name="how-to-undo-in-power-bi"></a>Como anular no Power BI
Como muitos outros serviços da Microsoft e o software, o Power BI fornece uma maneira fácil para desfazer o último comando. Por exemplo, vamos dizer que altera a cor de um ponto de dados ou uma série de pontos de dados, e não gosta de cor quando ele for mostrado na visualização. Não se lembra exatamente da cor anterior, mas sabe que deseja voltar àquela cor!

Para **Desfazer** a última ação ou as últimas ações, o que precisa de fazer é:

- Escreva CTRL + Z

## <a name="feedback"></a>Comentários
Tem uma dica que gostaria de partilhar? Envie-nos e vamos ver sobre adicionar à lista.

>[!NOTE]
>Essas personalizações de cor e eixo disponíveis quando o ícone **Formato** é selecionado também estão disponíveis no Power BI Desktop.

## <a name="next-steps"></a>Próximos passos
[Getting started with color formatting and axis properties](service-getting-started-with-color-formatting-and-axis-properties.md) (Introdução às propriedades de eixo e formatação de cor)

