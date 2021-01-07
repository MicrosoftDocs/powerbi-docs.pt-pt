---
title: Saiba como os botões funcionam no serviço Power BI
description: Os botões podem ser utilizados para iniciar diversas ações, incluindo navegação no relatório, pormenorização e pormenorização entre relatórios
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/21/2020
LocalizationGroup: Reports
ms.openlocfilehash: 140ca42dc34e98133beac5fff671cf1ef244501c
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721438"
---
# <a name="buttons-in-the-power-bi-service"></a>Botões no serviço Power BI
Pode ter reparado em botões nos relatórios que recebe de colegas e questionado como utilizá-los. Alguns têm palavras, outros têm setas, outros têm gráficos e outros até têm menus pendentes. Este artigo irá ensinar-lhe a reconhecer os botões e como descobrir o que fazer com eles.

## <a name="how-to-recognize-a-button"></a>Como reconhecer um botão
Os botões numa página de relatório podem parecer-se muito com formas, imagens ou ícones. No entanto, se ocorrer uma ação quando seleciona (clica em) algum, então provavelmente é um botão.

## <a name="types-of-buttons"></a>Tipos de botões
Os criadores de relatórios adicionam botões aos relatórios para ajudar na navegação e exploração. Apenas alguns dos tipos de botão são: voltar, marcador, setas, Perguntas e Respostas, ajuda e em branco. 

### <a name="back-buttons"></a>Botões de retrocesso 
Um botão de retrocesso pode ter uma seta como ícone e, quando o seleciona, o Power BI direciona-o novamente para a página anterior.  Os botões de retrocesso são utilizados frequentemente com a pormenorização. Aqui está um exemplo de um botão de retrocesso utilizado com a pormenorização.

1. O utilizador selecionou o **Word** no gráfico de barras e está a pormenorizar para **Market basket analysis**.

    ![Captura de ecrã a mostrar o botão de pormenorização.](media/end-user-buttons/power-bi-drillthrough.png)

2. Ao selecionar **Market basket analysis**, o Power BI abre a página de relatório de *Market basket analysis* e utiliza as seleções feitas na página de origem para filtrar o que é mostrado na página de destino.

    ![Captura de ecrã a mostrar o botão Anterior.](media/end-user-buttons/power-bi-back.png)

    Está agora na página de relatório de **Market basket analysis**, que é filtrada para o **Word**. Selecione o botão de retrocesso que está etiquetado como **Voltar** para voltar à página anterior. 

## <a name="bookmark-buttons"></a>Botões de Marcador
Os *estruturadores* de relatórios geralmente incluem marcadores nos seus relatórios. Pode ver a lista de marcadores de relatório ao selecionar **Marcadores** no canto superior direito. Quando um criador de relatórios adiciona um *botão* de marcador, é apenas para proporcionar uma forma alternativa de navegar para a página do relatório que está associada a esse marcador. A página terá as definições e filtros aplicados que são capturados pelo marcador. [Saiba mais sobre os marcadores no Power BI](end-user-bookmarks.md). 

Neste exemplo, o botão tem um ícone e o nome do marcador, *Urban*. 

![captura de ecrã a mostrar o botão de marcador](media/end-user-buttons/power-bi-bookmark.png)

Ao selecionar o botão marcador, o Power BI leva-o à localização e às definições estabelecidas para esse marcador.  Neste caso, o marcador está na página de relatório *Growth opportunities* e essa página é alvo de filtragem cruzada para **Urban**.

![captura de ecrã a mostrar a página de relatório filtrada para Urban](media/end-user-buttons/power-bi-urban.png)


## <a name="drillthrough-buttons"></a>Botões de Pormenorização
Há duas maneiras de pormenorizar no serviço Power BI. A Pormenorização leva-o a uma página de relatório diferente e os dados dessa página de destino são apresentados de acordo com os filtros e seleções que fez na página de origem.

Uma forma de utilizar a pormenorização num relatório é clicar com o botão direito do rato num ponto de dados num elemento visual, selecionar **Pormenorizar** e escolher o destino. Este método é descrito acima, na secção intitulada **Botões de retrocesso**. No entanto, por vezes os criadores de relatórios utilizam um *botão* de pormenorização, para tornar a ação mais óbvia e chamar a atenção para informações importantes.  

Os botões de pormenorização podem ter mais do que um pré‑requisito. A não ser que cumpra todos os pré‑requisitos, o botão não irá funcionar. Vejamos um exemplo.

Aqui está um botão de pormenorização que nos irá levar à página *Store details*. Pairar o cursor sobre o botão revela uma descrição que nos informa de que precisamos de selecionar tanto uma loja como um produto. Até selecionarmos um de cada, o botão permanece inativo.

![Captura de ecrã a mostrar o botão de pormenorização com a descrição visível.](media/end-user-buttons/power-bi-drill-two-selections.png)

Agora que selecionámos um produto (**Word**), e uma loja (**Leo**), o botão muda de cor para nos informar que agora está ativo.

![Captura de ecrã a mostrar o botão de pormenorização para Detalhes da loja.](media/end-user-buttons/power-bi-select-both.png)

A seleção do botão de pormenorização leva-nos à página de relatório *Store*. A página *Store* é filtrada para as nossas seleções de **Word** e **Leo**.

![Captura de ecrã a mostrar a página de relatórios das lojas.](media/end-user-buttons/power-bi-store.png)

Os botões de pormenorização também podem ter menus pendentes que lhe oferecem uma seleção de destinos. Depois de ter feito as seleções na página do relatório de origem, selecione a página de relatório de destino para a pormenorização. No exemplo abaixo, estamos a mudar a nossa seleção para pormenorizar até chegar à página de relatório *Detalhes do mercado*. 

![captura de ecrã a mostrar o menu pendente da pormenorização com múltiplos destinos](media/end-user-buttons/power-bi-destination.png)

## <a name="page-navigation"></a>Navegação entre páginas

Os botões de navegação entre páginas levam‑no a uma página diferente no mesmo relatório. Muitas vezes, os criadores de relatórios criam botões de navegação para contar uma história ou para o guiar através das informações do relatório. No exemplo abaixo, o estruturador de relatórios adicionou em cada página um botão que o leva de volta à primeira página do relatório, a página de resumo de nível superior. Este botão de navegação entre páginas é útil porque há muitas páginas neste relatório.

![Captura de ecrã a mostrar o botão de navegação entre páginas denominado Team scorecard.](media/end-user-buttons/power-bi-nav-button.png)


## <a name="qa-buttons"></a>Botões de Perguntas e Respostas 
A seleção de um botão de Perguntas e Respostas abre a janela do Explorador de Perguntas e Respostas do Power BI. A janela de Perguntas e Respostas aparece acima da página do relatório e pode ser fechada ao selecionar o X. [Saiba mais sobre Perguntas e Respostas](end-user-q-and-a.md)

![Captura de ecrã a mostrar a janela do Explorador de Perguntas e Respostas do Power BI com o texto Faça uma pergunta sobre os seus dados.](media/end-user-buttons/power-bi-qna.png)

## <a name="web-url"></a>URL da Web
Os botões de URL da Web abrem uma nova janela do browser. Os estruturadores de relatórios podem adicionar este tipo de botão como uma origem de referência, para ligar ao site corporativo ou a uma página de ajuda, ou mesmo como uma ligação a um relatório ou dashboard diferente. No exemplo abaixo, o botão URL da Web permite transferir o ficheiro de origem do relatório. 

Uma vez que a página é aberta numa janela separada, feche a janela ou selecione o separador Power BI para voltar ao relatório do Power BI.

![captura de ecrã a mostrar o botão Transferir PBIX e a nova janela do browser com a ligação para transferência](media/end-user-buttons/power-bi-url.png)

## <a name="next-steps"></a>Próximos passos
[Marcadores](end-user-bookmarks.md)    
[Agregar, desagregar](end-user-drill.md)
