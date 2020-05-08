---
title: Introdução à formatação de visualizações do Power BI
description: Personalizar o título, fundo e legenda da visualização
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 7ff02eb07d4b052892cc80ab4710223d8d302a9f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78893436"
---
# <a name="customize-visualization-titles-backgrounds-and-legends"></a>Personalizar os títulos, fundos e legendas das visualizações

Neste tutorial, vai aprender várias formas de personalizar as visualizações. Existem muitas opções para personalizar as visualizações. A melhor forma de saber mais sobre todas elas é explorar o painel **Formatação** (selecione o ícone de rolo de pintura). Para começar, este artigo mostra-lhe como pode personalizar um título, uma legenda, um fundo de visualização e adicionar um tema.

Não pode personalizar todas as visualizações. Veja a [lista completa](#visualization-types-that-you-can-customize) das visualizações para obter mais detalhes.


## <a name="prerequisites"></a>Pré-requisitos

- O serviço Power BI ou Power BI Desktop

- Relatório de Exemplo de Análise de Revenda

## <a name="customize-visualization-titles-in-reports"></a>Personalizar títulos de visualização em relatórios

Inicie sessão no Power BI Desktop e abra o relatório [Exemplo de Análise de Revenda](../sample-datasets.md).

> [!NOTE]
> Ao afixar uma visualização num dashboard, ela se torna um mosaico do dashboard. Também pode personalizar os próprios mosaicos com [novos títulos e subtítulos, hiperligações e redimensionar os mesmos](../service-dashboard-edit-tile.md).

1. Aceda à página **Novas Lojas** do relatório **Exemplo de Análise de Revenda**.

1. Selecione o gráfico de colunas agrupadas **Contagem de Lojas Abertas por Mês de Abertura e Cadeia**.

1. No painel **Visualizações**, selecione o ícone de rolo de pintura para apresentar as opções de formatação.

1. Selecione **Título** para expandir essa secção.

   ![Captura de ecrã do painel Formatação com o ícone de rolo de pintura destacado e uma seta para a lista pendente Título.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-format-menu.png)

1. Mova o controlo de deslize **Mosaico** para **Ativado**.

1. Para alterar o título, insira a *Contagem de lojas por mês de abertura* no campo **Texto do título**.

    ![Captura de ecrã a mostrar o painel Formatar com o texto de título introduzido.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-title.png)

1. Altere a **Cor do tipo de letra** para branco e a **Cor de fundo** para azul.    

    a. Selecione a lista suspensa e escolha uma cor em **Cores do tema**, **Cores recentes**ou **Cor personalizada**.
    
    ![Captura de ecrã das opções da Cor do tipo de letra e da Cor de fundo.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-color.png)

    b. Selecione a lista suspensa para fechar a janela de cores.


1. Aumente o tamanho do texto para **16 pt**.

1. A última personalização feita ao título do gráfico será o seu alinhamento ao centro da visualização.

    ![Captura de ecrã dos controlos de Alinhamento com a opção Centrar selecionada.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-align.png)

    Nesta fase do tutorial, o título do gráfico de colunas agrupadas deverá ter um aspeto semelhante ao seguinte:

    ![Captura de ecrã do gráfico de colunas agrupadas recém-configurado.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-table.png)

Guarde as alterações realizadas e avance para a secção seguinte.

Se precisar de reverter todas as alterações, selecione **Reverter para predefinição**, na parte inferior do painel de personalização **Título**.

![Captura de ecrã da opção Reverter para predefinição.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-revert.png)

## <a name="customize-visualization-backgrounds"></a>Personalizar planos de fundo de visualização

Com o mesmo gráfico de colunas agrupadas selecionado, expanda as opções **Fundo**.

1. Mova o controlo de deslize **Fundo** para **Ativado**.

1. Selecione a lista suspensa e escolha uma cor cinzenta.

1. Altere a **Transparência** para **74%** .

Nesta fase do tutorial, o fundo do gráfico de colunas agrupadas deverá ter um aspeto semelhante ao seguinte:

![Captura de ecrã do gráfico de colunas agrupadas com a cor de fundo atualizada.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-background.png)

Guarde as alterações realizadas e avance para a secção seguinte.

Se precisar de reverter todas as alterações, selecione **Reverter para predefinição**, na parte inferior do painel de personalização **Fundo**.

## <a name="customize-visualization-legends"></a>Personalizar legendas de visualização

1. Abra a página de relatório **Visão geral** e selecione o gráfico **Variação das Vendas Totais por MêsFiscal e Gestor Distrital**.

1. No separador **Visualização**, selecione o ícone de rolo de pintura para abrir o painel Formatação.

1. Expanda as opções de **Legenda**:

    ![Captura de ecrã a mostrar o cartão Legenda.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Mova o controlo de deslize **Legenda** para **Ativado**.

1. Mova a legenda para a esquerda da visualização.

1. Adicione um título de legenda ao alternar o **Título** para **Ativado**.

1. Introduza *Gestor* no campo **Nome da legenda**.

1. Altere a **Cor** para preto.

Guarde as alterações realizadas e avance para a secção seguinte.

Se precisar de reverter todas as alterações, selecione **Reverter para predefinição**, na parte inferior do painel de personalização **Legenda**.

## <a name="customize-colors-using-a-theme"></a>Personalizar cores com um tema

Com os temas de relatório, pode aplicar alterações de design a todo o relatório, como utilizar cores da empresa, alterar conjuntos de ícones ou aplicar uma nova formatação visual predefinida. Quando aplica um tema de relatório, todos os elementos visuais no relatório utilizam as cores e a formatação do tema selecionado.

Para aplicar um tema ao seu relatório, selecione **Mudar tema** a partir da barra de menu. Selecione um tema.  O relatório abaixo utiliza o tema **Solar**.

 
![O relatório utiliza o tema Solar com tons amarelos, laranjas e vermelhos](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Tipos de visualizações que pode personalizar

Veja a seguir uma lista de visualizações e as opções de personalização disponíveis para cada uma:

| Visualização | Title | Fundo | Legenda |
|:--- |:--- |:--- |:--- |
| Área | sim | sim |sim |
| Barras | sim | sim |sim |
| Cartão | sim | sim |n/a |
| Cartão de Linhas múltiplas | sim | sim | n/a |
| Personalizada | sim | sim | sim |
| Combinação | sim | sim | sim |
| Anel | sim | sim | sim |
| Mapa de manchas | sim | sim | sim |
| Funil | sim | sim | n/a |
| Medidor | sim | sim | n/a |
| Principal Influenciador | sim | sim | n/a |
| KPI | sim | sim | n/a |
| Linha | sim | sim | sim |
| Mapa | sim | sim | sim |
| Matriz | sim | sim | n/a |
| Circular | sim | sim | sim |
| Perguntas e Respostas | sim | sim | n/a |
| Dispersão | sim | sim | sim |
| Formas | sim | sim | sim |
| Segmentação de Dados | sim | sim | n/a |
| Tabela | sim | sim | n/a |
| Caixa de texto | não | sim | n/a |
| Treemap | sim | sim | sim |
| Cascata | sim | sim | sim |

## <a name="next-steps"></a>Próximas etapas

- [Personalizar as propriedades dos Eixos X e Y](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Getting started with color formatting and axis properties](service-getting-started-with-color-formatting-and-axis-properties.md) (Introdução às propriedades de eixo e formatação de cor)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
