---
title: Utilizar botões no Power BI
description: Os botões no Power BI Desktop permitem-lhe criar relatórios e dashboards que têm um comportamento semelhante às aplicações, o que aumenta a interação com os utilizadores
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/04/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7858c76703feb53ebb74bec998ecbebcba3994cc
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/06/2018
---
# <a name="using-buttons-in-power-bi"></a>Utilizar botões no Power BI
A utilização de **botões** no Power BI permite-lhe criar relatórios e dashboards que têm um comportamento semelhante às aplicações e, deste modo, poderá criar um ambiente apelativo onde os utilizadores podem pairar o rato, clicar e ter uma maior interação com os conteúdos do Power BI. Pode adicionar botões a relatórios no **Power BI Desktop** e partilhar ou publicar esses relatórios no serviço Power BI para criar dashboards que proporcionam aos utilizadores um comportamento semelhante às aplicações.

![Botões no Power BI](media/desktop-buttons/desktop-buttons_01.png)

Os botões que criar no **Power BI Desktop** estão disponíveis para utilização em relatórios ou dashboards publicados no **serviço Power BI**.

## <a name="creating-buttons-in-reports"></a>Criação de botões em relatórios
Para criar um botão num relatório do **Power BI Desktop**, no friso **Página Principal**, selecione **Botões** e será apresentado um menu pendente, onde poderá selecionar o botão pretendido a partir de uma coleção de opções, conforme indicado na imagem seguinte. 

![Adicionar um controlo de botão no Power BI Desktop](media/desktop-buttons/desktop-buttons_02.png)

Quando cria um botão e o seleciona na tela do relatório, o painel **Visualizações** apresenta-lhe as várias formas através das quais pode personalizar o botão para que este se ajuste às suas necessidades. Por exemplo, pode ativar ou desativar o **Texto do Botão** ao ativar o controlo de deslize nesse cartão do painel **Visualizações**. Também pode alterar o ícone e o preenchimento do botão, o título e a ação efetuada quando os utilizadores clicam no botão num relatório ou dashboard, entre outras propriedades.

![Formatar um botão no Power BI Desktop](media/desktop-buttons/desktop-buttons_03.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Definir as propriedades de botão para predefinição (inativo), ao pairar com o rato ou quando selecionado

Os botões no Power BI têm três estados: predefinição (a forma como são apresentados quando o rato não está a pairar sobre eles ou quando não estão selecionados), ao pairar com o rato ou quando selecionados (mais conhecido como *clicar*). Muitos dos cartões no painel **Visualizações** podem ser modificados individualmente com base nestes três estados, o que lhe dá uma grande flexibilidade para personalizar os seus botões.

Os seguintes cartões no painel **Visualizações** permitem-lhe ajustar a formatação ou o comportamento de um botão com base nos seus três estados:

* Texto do Botão
* Ícone
* Contorno
* Preenchimento

Para selecionar a forma como um botão deve ser apresentado em cada estado, expanda um desses cartões e selecione a lista pendente apresentada na parte superior do cartão. Na imagem seguinte, pode ver o cartão **Contorno** expandido, com a lista pendente selecionada para apresentar os três estados:

![Os três estados de um botão no Power BI Desktop](media/desktop-buttons/desktop-buttons_04.png)


## <a name="select-the-action-for-a-button"></a>Selecionar a ação para um botão

Pode selecionar qual a ação efetuada quando o utilizador seleciona um botão no Power BI. Pode aceder às opções para ações do botão a partir do cartão **Ação** no painel **Visualizações**.

![Ação para um botão no Power BI](media/desktop-buttons/desktop-buttons_05.png)

As opções para ações do botão são:

* Anterior
* Marcador
* Perguntas e Respostas

A seleção **Anterior** leva o utilizador para a página anterior do relatório. Isto é especialmente útil para páginas de desagregação.

A seleção **Marcador** apresenta a página do relatório associada a um marcador que está definido para o relatório atual. Pode [obter mais informações sobre marcadores no Power BI](desktop-bookmarks.md). 

A seleção **Perguntas e Respostas** na lista pendente apresenta uma janela do **Q&A Explorer**. 

Alguns botões terão uma ação predefinida selecionada automaticamente. Por exemplo, o botão **Perguntas e Respostas** seleciona automaticamente **Perguntas e Respostas** como a ação predefinida. Pode saber mais sobre o **Q&A Explorer** ao consultar [esta mensagem do blogue](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

Pode experimentar ou testar os botões que criar para o seu relatório ao utilizar *Ctrl+Clique* no botão que pretende utilizar. 

## <a name="next-steps"></a>Passos seguintes
Para obter mais informações sobre funcionalidades semelhantes ou como interagir com botões, veja os artigos seguintes:

* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)
* [Apresentar um mosaico do dashboard ou um elemento visual do relatório no modo de detalhe](service-focus-mode.md)
* [Utilizar marcadores para partilhar informações e criar histórias no Power BI](desktop-bookmarks.md)

