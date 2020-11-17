---
title: Introdução à formatação de visualizações de relatórios
description: Introdução à utilização das opções de formatação com visualizações de relatórios
author: msftrien
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 3e61521ec7ac518aaa374cec328639a849b21bd5
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483852"
---
# <a name="getting-started-with-the-formatting-pane"></a>Introdução ao painel de formatação

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

Se tiver permissões para editar um relatório, existem inúmeras opções de formatação disponíveis. Nos relatórios do Power BI, pode alterar a cor da série de dados, os pontos de dados e até o fundo das visualizações. Pode alterar a forma como o eixo x e o eixo y são apresentados. Pode até formatar as propriedades do tipo de letra das visualizações, das formas e dos títulos. O Power BI permite-lhe ter controlo total sobre a forma como os relatórios são apresentados.

Para começar, abra um relatório no Power BI Desktop ou no serviço Power BI. Ambos fornecem opções de formatação quase idênticas. Quando abrir um relatório no serviço Power BI, confirme que seleciona **Editar** na barra de menus. 

![barra de menus a mostrar a opção Editar](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-edit.png)

Quando estiver a editar um relatório e tiver uma visualização selecionada, é apresentado o painel **Visualizações**. Utilize este painel para alterar as visualizações. Diretamente abaixo do painel **Visualizações** estão três ícones: o ícone **Campos** (uma pilha de barras), **Formatar** (um rolo de pintura) e **Análise** (uma lupa). Na imagem abaixo, o ícone **Campos** está selecionado, indicado por uma barra amarela sob o ícone.

![Painel Visualização com o ícone Campos selecionado](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-format.png)

Quando selecionar **Formatar**, a área abaixo do ícone apresenta as personalizações disponíveis para a visualização atualmente selecionada.  

![Painel Visualização com o ícone Formatar selecionado](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-format-selected.png)

Pode personalizar muitos elementos de cada visualização. As opções disponíveis dependem do elemento visual selecionado. Algumas destas opções são:

* Legenda
* Eixo X
* Eixo Y
* Cores de dados
* Etiquetas de dados
* Total de etiquetas
* Formas
* Área de desenho
* Título
* Fundo
* Manter proporção
* Limite
* Descrições
* Cabeçalhos de elementos visuais
* Formas
* Posição    
e muito mais.


> [!NOTE]
>  
> Não verá todos estes elementos em cada tipo de visualização. A visualização que selecionar afetará as personalizações que estão disponíveis; por exemplo, não verá um eixo X se tiver selecionado um gráfico circular porque não há eixo x em gráficos circulares.

Repare também que, se não tiver nenhuma visualização selecionada, é apresentado **Filtros** em vez dos ícones, o que permite aplicar filtros a todas as visualizações na página.

A melhor forma de aprender a utilizar as Opções de formatação é experimentá-las. Pode sempre anular as alterações ou voltar à predefinição. Existe uma quantidade incrível de opções disponíveis, para além estarem constantemente a ser adicionadas novas. Não é possível descrever todas as opções de formatação num só artigo. Mas para começar, vamos descrever algumas delas. 

1. Alterar as cores utilizadas no elemento visual   
2. Aplicar um estilo    
3. Alterar as propriedades do eixo    
4. Adicionar etiquetas de dados    
1. Adicionar total de etiquetas




## <a name="working-with-colors"></a>Trabalhar com cores

Vamos percorrer os passos necessários para personalizar as cores numa visualização.

1. Selecione a visualização para ativá-la.

2. Selecione o ícone de rolo de pintura para abrir o separador Formatação. O separador Formatação apresenta todos os elementos de formatação disponíveis para o elemento visual selecionado.

    ![Gráfico com separador do painel Formatação selecionado](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-formatting.png)

3. Selecione **Cores dos Dados** para expandir as personalizações disponíveis.  

    ![Gráfico com painel Formatação aberto e a opção Cores dos dados expandida](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-data-colors.png)

4. Altere **Mostrar tudo** para Ligado e selecione cores diferentes para as colunas.

    ![Gráfico com as novas cores aplicadas a algumas colunas](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-change-colors.png)

Veja a seguir algumas sugestões úteis para trabalhar com cores. Os números na lista a seguir também são mostrados no ecrã seguinte, indicando onde estes elementos úteis podem ser acedidos ou alterados.

1. Não gosta da cor? Não há problema, basta selecionar **Reverter para predefinição** para reverter a seleção para a predefinição. 

2. Não gosta de nenhuma das mudanças de cor? Selecione **Reverter para predefinição** na parte inferior da secção **Cor dos dados** e as suas cores revertem para as predefinições. 

3. Quer uma cor que não vê na paleta? Basta selecionar **Cores personalizadas** e escolher no espectro.  

   ![Secção Cor dos dados com a paleta de cores aberta](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-color-extras.png)

Não gostou da alteração que acabou de criar? Utilize **CTRL+Z** para anular, tal como está habituado a fazer.

## <a name="applying-a-style-to-a-table"></a>Aplicar um estilo a uma tabela
Algumas visualizações de Power BI têm uma opção **Estilo**. Com um único clique, é aplicado um conjunto completo de opções de formatação à visualização, tudo de uma vez. 

1. Selecione uma tabela ou matriz para a tornar ativa.   
1. Abra o painel Formatação e selecione **Estilo**.

   ![Selecionar Estilo no separador Formatação](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-style.png)


1. Selecione um estilo na lista pendente. 

   ![Mesma tabela com a opção Linhas coloridas com cabeçalho a negrito aplicada](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-style-flashy.png)

Mesmo após aplicar um Estilo, pode continuar a formatar as propriedades, incluindo a cor, dessa visualização.


## <a name="changing-axis-properties"></a>Alterar as propriedades dos eixos

Geralmente é útil modificar o eixo X ou Y. Semelhante ao trabalho com cores, pode modificar um eixo ao selecionar o ícone de seta para baixo à esquerda do eixo que deseja alterar, como mostrado na imagem a seguir.  
![Painel Formatar com uma seta para o cartão do eixo Y](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-y-axis.png)

No exemplo abaixo, formatamos o eixo Y ao:
- mover as etiquetas para o lado direito da visualização

- alterar o valor inicial para zero.

- alterar a cor do tipo de letra da etiqueta para preto

- aumentar o tamanho do tipo de letra para 12

- adicionar um título ao eixo Y


    ![mesmo gráfico de colunas com muita formatação no eixo Y](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-axis-changes.png)

Pode remover completamente as etiquetas do eixo ao ativar/desativar o botão de opção ao lado do **Eixo X** ou **Eixo Y**. Também pode optar por ativar ou desativar os títulos dos eixos ao selecionar o botão de opção junto a **Título**.  



## <a name="adding-data-labels"></a>Adicionar etiquetas de dados    

Vamos adicionar etiquetas de dados a um gráfico de área. 

Veja a seguir a foto do *antes*. 

![gráfico de área não formatado](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-area-chart.png)


E esta é a foto do *depois*.

![gráfico de área formatado](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-data-labels.png)

Selecionamos a visualização para a tornar ativa e abrimos o separador Formatação.  Selecionamos **Etiquetas de dados** e Ativar. Em seguida, aumentámos o tipo de letra para 12, alterámos a família de tipos de letra para Arial Black, definimos **Mostrar fundo** como Ativado e a cor de fundo como branco com uma transparência de 5%.

Estas são apenas algumas das tarefas de formatação possíveis. Abra um relatório no Modo de edição e divirta-se a explorar o painel Formatação para criar visualizações apelativas e informativas.

## <a name="adding-total-labels"></a>Adicionar o total de etiquetas    

Um último exemplo de formatação antes de começar a explorar por sua conta.  Vamos adicionar o total de etiquetas a um gráfico de colunas empilhadas. O total de etiquetas está disponível para gráficos empilhados, gráficos de combinação e gráficos de área.

Quando ativa o total de etiquetas, o Power BI apresenta uma agregação ou o total dos dados. Vejamos um exemplo. 

Aqui, temos um gráfico de colunas empilhadas com etiquetas de dados a mostrar o valor de cada parte de cada pilha completa.  Esta é a vista predefinida. 

![gráfico de colunas com etiquetas de dados](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-column-charts.png)


Ao abrir o elemento visual na Vista de edição, pode alterar a apresentação das etiquetas de dados e do total de etiquetas. Selecione o elemento visual para torná-lo ativo e abra o painel Formatting (Formatação). Desloque-se para baixo, até **Etiquetas de dados** e **Total de etiquetas**. A opção **Etiquetas de dados** está ativada e a opção **Total de etiquetas** está desativada. 

![gráfico de colunas não formatado](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-total-label.png)

Desative a opção **Etiquetas de dados** e ative a opção **Total de etiquetas**. O Power BI apresenta agora a agregação de cada coluna.    
![gráfico de colunas formatado](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-totals.png)

Estas são apenas algumas das tarefas de formatação possíveis. Abra um relatório no Modo de edição e divirta-se a explorar o painel Formatação para criar visualizações apelativas e informativas.


## <a name="next-steps"></a>Próximos passos
Para obter mais informações, veja o seguinte artigo: 

* [Partilhar relatórios](../collaborate-share/service-share-reports.md)

* [Sugestões e truques para formatação de cor no Power BI](service-tips-and-tricks-for-color-formatting.md)  
* [Formatação condicional em tabelas](../create-reports/desktop-conditional-table-formatting.md)

