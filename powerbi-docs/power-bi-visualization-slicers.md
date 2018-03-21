---
title: "Segmentações de dados no Power BI (Tutorial)"
description: "Tutorial: segmentações no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/05/2018
ms.author: v-thepet
LocalizationGroup: Visualizations
ms.openlocfilehash: cfa4c0f17c67a036b7d01744da1b5247345c493a
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2018
---
# <a name="slicers-in-power-bi-tutorial"></a>Segmentações de dados no Power BI (Tutorial)
Um RP de Vendas quer ver várias métricas de todo o departamento e de cada Gestor Regional individual. Pode criar um relatório separado para cada gestor ou utilizar uma segmentação de dados. Uma segmentação de dados restringe a parte do conjunto de dados apresentada noutras visualizações num relatório. As segmentações são uma maneira alternativa de filtragem.

Este tutorial utiliza o [Exemplo de Análise de Revenda](sample-retail-analysis.md) gratuito para o ajudar a criar e a formatar uma segmentação de dados e a utilizá-la para filtrar um relatório. Divirta-se a descobrir maneiras de formatar e utilizar as segmentações de dados. 

![segmentação de dados](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Quando usar uma segmentação
As segmentações de dados são uma ótima escolha quando quer:

* Apresentar os filtros mais utilizados ou importantes na tela do relatório para facilitar o acesso.
* Facilitar a apresentação do estado atual filtrado sem ter de abrir uma lista pendente. 
* Filtrar por colunas desnecessárias e ocultas nas tabelas de dados.
* Criar relatórios mais objetivos ao colocar as segmentações de dados junto aos elementos visuais importantes.

As segmentações de dados do Power BI têm as seguintes limitações:

- As segmentações de dados não suportam campos de texto.
- As segmentações de dados não podem ser afixadas a um dashboard.
- A desagregação não é suportada para segmentações de dados.
- As segmentações de dados não suportam filtros ao nível dos elementos visuais.

## <a name="create-a-slicer"></a>Criar uma segmentação

Este tutorial utiliza uma segmentação de dados de lista. Os tipos de dados numéricos e de data/hora podem ter segmentações de dados de intervalo. Veja [Utilizar a segmentação de dados de intervalo numérico no Power BI Desktop](desktop-slicer-numeric-range.md) ou o seguinte vídeo para obter mais informações sobre a criação e utilização de segmentações de dados de intervalo.
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>

1. No Power BI Desktop ou serviço Power BI, abra o [Exemplo de Análise de Revenda](sample-retail-analysis.md) na [Vista de Edição](service-interact-with-a-report-in-editing-view.md) e [adicione uma nova página de relatório](power-bi-report-add-page.md).
2. No painel Campos, em District, selecione **District Manager** para criar uma nova visualização.
    
    ![novo gráfico](media/power-bi-visualization-slicers/1-new-vis.png)
    
3. Selecione o ícone da **Segmentação de Dados** ![ícone da segmentação de dados](media/power-bi-visualization-slicers/slicer-icon.png) no painel Visualizações para converter a nova visualização numa segmentação de dados. 
    
    ![converter em segmentação de dados](media/power-bi-visualization-slicers/2-slicer.png)

Também pode selecionar o ícone da Segmentação de Dados para criar uma nova segmentação de dados e, em seguida, selecionar ou arrastar um campo de dados para a caixa Campos para a povoar.

>[!TIP]
>Pode ordenar os itens de segmentações de dados de lista pelos valores de dados. Para ordenar os itens da segmentação de dados por ordem alfabética invertida, selecione as reticências (…) no canto superior direito da segmentação de dados e selecione **Ordenar Por District Manager**. A predefinição é a ordem alfabética ascendente, mas pode alternar entre a ordem ascendente e descendente. 

## <a name="format-the-slicer"></a>Formatar a segmentação de dados
Aplique formatação visual à segmentação de dados District Manager.
1. Com a segmentação de dados selecionada, no painel Visualizações, selecione o ícone Formato ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) para mostrar os controlos de formatação. 
    
    ![formatação](media/power-bi-visualization-slicers/3-format.png)
    
2. Clique nas setas de menu pendente junto a cada categoria para mostrar e editar as opções. 

### <a name="general-options"></a>Secção de opções Geral
1. Selecione vermelho em **Cor do contorno** e altere a **Espessura do contorno** para "2". Quando ativado, isto define a cor e a espessura dos contornos ou sublinhados do cabeçalho e do item. 
2. Em Orientação, a opção Vertical é a predefinição, o que cria uma segmentação de dados de lista na vertical com caixas de seleção antes dos itens. Selecione **Horizontal** para produzir uma segmentação de dados com os itens organizados horizontalmente. A orientação horizontal permite várias disposições de texto, botões ou mosaicos, consoante o tamanho e a forma da segmentação de dados e a formatação dos itens. 
    
    ![horizontal](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Ative o esquema **Reativo**, que altera o tamanho e a disposição dos itens da segmentação de dados horizontal para que correspondam ao tamanho e à forma da segmentação de dados. Se for muito pequena, a segmentação de dados torna-se um ícone de filtro. 
    
    ![reativo](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >As alterações do esquema Reativo poderão substituir a formatação de um cabeçalho ou item específico que definiu. 
    
4. Defina a posição e o tamanho da segmentação de dados com precisão numérica, em **Posição X**, **Posição Y**, **Largura**, e **Altura** ou mova e redimensione a segmentação de dados diretamente na tela, para produzir diferentes tamanhos e disposições dos itens, como uma linha horizontal de botões. 

    ![botões na horizontal](media/power-bi-visualization-slicers/6-buttons.png)

Veja [Criar uma segmentação de dados reativa que pode redimensionar no Power BI](power-bi-slicer-filter-responsive.md) para saber mais sobre a orientação horizontal e a formatação reativa.

### <a name="selection-controls-options"></a>Secção de opções Controlos de Seleção
1. A opção Mostrar a opção "Selecionar Tudo" está Inativa por predefinição. Selecione para que fique no modo **Ativa** para adicionar um item Selecionar Tudo à segmentação que seleciona ou desseleciona todos os itens ao clicar no mesmo. Quando todos os itens estiverem selecionados, ao clicar num deles desseleciona esta opção, o que permite criar um filtro do tipo "não é". 
    
    ![selecionar tudo](media/power-bi-visualization-slicers/7-select-all.png)
    
2. A opção Seleção Única está Ativa por predefinição. Clicar num item seleciona-o e manter premida a tecla Ctrl ao clicar permite selecionar vários itens. Mude a opção Seleção Única para **Inativa** para poder selecionar vários itens sem manter premida a tecla Ctrl. Ao clicar num item novamente desseleciona esta opção. 

### <a name="header-options"></a>Secção de opções Cabeçalho
A opção Cabeçalho está Ativa por predefinição, sendo que mostra o nome do campo de dados na parte superior da segmentação de dados. 
1. Formate o texto do cabeçalho para tornar a **Cor do tipo de letra** vermelha, o **Tamanho do texto** 14 e a **Família de tipos de letra** Arial Black. 
2. Em Contorno, selecione **Inferior apenas** para produzir um sublinhado com o tamanho e a cor que definiu na secção de opções Geral. 

### <a name="item-options"></a>Secção de opções Item
1. Formate o texto e o fundo do item para tornar a **Cor do tipo de letra** preta, o **Fundo** vermelho claro, o **Tamanho do texto** 10 e a **Família de tipos de letra** Arial. 
2. Em Contorno, selecione **Moldura** para desenhar um limite à volta de cada item com o tamanho e a cor que definiu na secção de opções Geral. 
    
    ![formatado](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Com a Orientação Horizontal, os itens desselecionados mostram as cores de texto e fundo escolhidas, enquanto os itens selecionados utilizam a predefinição do sistema (normalmente fundos pretos com texto branco). 
    >- Com a Orientação Vertical, os itens mostram sempre as cores definidas e as caixas de seleção ficam sempre em preto quando são selecionadas. 

### <a name="other-formatting-options"></a>Outras opções de formatação
As outras opções de formatação estão desativadas por predefinição. Quando estão **Ativas**: 
- **Título:** adiciona e formata um título (além de e independente do cabeçalho) à parte superior da segmentação de dados. 
- **Fundo:** adiciona uma cor de fundo a toda a segmentação de dados e define a transparência.
- **Manter proporção:** mantém a forma da segmentação de dados se esta for redimensionada.
- **Limite:** adiciona um limite de um pixel à volta da segmentação e define a respetiva cor. (Este limite da segmentação de dados é separado das definições de Contorno Geral e não é afetado pelas mesmas.) 

## <a name="sync-and-use-the-slicer-on-other-pages"></a>Sincronizar e utilizar a segmentação de dados noutras páginas
A partir da atualização de fevereiro de 2018 do Power BI, pode sincronizar uma segmentação de dados e utilizá-la em qualquer uma ou em todas as páginas de um relatório. 
1. Com a segmentação de dados District Manager selecionada, no menu Ver, selecione **Segmentação de dados de sincronização** no Power BI Desktop ou ative o **painel Segmentação de dados de sincronização** no serviço Power BI. É apresentado o painel Segmentação de dados de sincronização. 
    
    ![segmentação de dados de sincronização](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
2. Na primeira coluna, selecione **Overview** e todas as outras páginas com as quais pretende sincronizar a segmentação de dados ou clique em **Adicionar a todos** para fazer com que a segmentação de dados seja sincronizada com todas as páginas do relatório.  
3. Na coluna seguinte, selecione **Overview** e todas as outras páginas nas quais pretende que a segmentação de dados seja visível. 
4. Mude para a página **Overview** e repare na segmentação de dados e os respetivos efeitos nos elementos visuais da outra página. 
    - Selecione e desselecione itens diferentes e repare que os outros elementos visuais na página são alterados de acordo com as mesmas. A seleção de itens em qualquer página reflete-se em todas as páginas sincronizadas.
    - Altere o tamanho, a forma, a posição e/ou a formatação da segmentação de dados na página Overview. A formatação da segmentação de dados nas outras páginas sincronizadas não é alterada. 

### <a name="control-which-page-visuals-are-affected-by-the-slicer"></a>Controlar que elementos visuais da página são afetados pela segmentação de dados
Por predefinição, uma segmentação de dados numa página de um relatório afeta todas as outras visualizações nessa página. Utilize as **Interações visuais** para impedir que algumas visualizações da página sejam afetadas.

1. Na página **Overview**, com a segmentação de dados selecionada:
    - No Power BI Desktop, clique no menu Formato em Ferramentas Visuais**Editar interações**.
    - No serviço Power BI, clique no menu pendente **Interações visuais** na barra de menus e ative a opção **Editar interações**. 
    
    Os controlos de filtro são apresentados acima de todos os outros elementos visuais na página. ![controlos de filtro](media/power-bi-visualization-slicers/filter-controls.png)
    
2. Selecione o ícone **Nenhum** por cima de um elemento visual para fazer com que a segmentação de dados pare de o filtrar. Selecione o ícone **Filtrar** para fazer com que a segmentação de dados comece novamente a filtrar o elemento visual. 

Veja [Interações visuais num relatório do Power BI](service-reports-visual-interactions.md) para obter mais informações sobre a edição de interações.

## <a name="next-steps"></a>Passos seguintes
[Experimente. É gratuito!](https://powerbi.com/)

Tem ideias sobre como melhorar o Power BI? [Submeter uma ideia](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

[Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

