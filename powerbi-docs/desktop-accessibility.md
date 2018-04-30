---
title: Acessibilidade nos relatórios do Power BI Desktop
description: Funcionalidades e sugestões para criar relatórios do Power BI Desktop acessíveis
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
ms.date: 11/21/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a0268af4d5b6ec1e94b42735100196e11c4d119b
ms.sourcegitcommit: 312390f18b99de1123bf7a7674c6dffa8088529f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="accessibility-in-power-bi-desktop-reports"></a>Acessibilidade nos relatórios do Power BI Desktop
O **Power BI Desktop** tem funcionalidades que permitem a pessoas com incapacidades consumir e interagir mais facilmente com os relatórios do **Power BI Desktop**. Estas funcionalidades incluem a capacidade de consumir um relatório com o teclado ou um leitor de ecrã, utilizando a tabulação para colocar o foco em vários objetos numa página e a utilização cuidada de marcadores em visualizações.

![Utilizar marcadores diferentes em gráficos de área e de linhas para melhorar a acessibilidade](media/desktop-accessibility/accessibility_01.png)

> [!NOTE]
> Estas funcionalidades de acessibilidade estão disponíveis com a versão de junho de 2017 do **Power BI Desktop** e com as versões posteriores. Também estão planeadas para versões futuras funcionalidades de acessibilidade adicionais.
> 
> 

## <a name="consuming-a-power-bi-desktop-report-with-a-keyboard-or-screen-reader"></a>Consumir um relatório do Power BI Desktop com um teclado ou leitor de ecrã
A partir da versão de setembro de 2017 do **Power BI Desktop**, pode premir a tecla **?** para mostrar uma janela que descreve os atalhos do teclado da acessibilidade disponíveis no **Power BI Desktop**.

![Premir a tecla ? no Power BI Desktop para mostrar atalhos do teclado da acessibilidade](media/desktop-accessibility/accessibility_03.png)

Com as melhorias de acessibilidade, pode consumir um relatório do **Power BI Desktop** com um teclado ou um leitor de ecrã com as seguintes técnicas:

Pode mudar o foco entre os separadores de página do relatório ou os objetos de uma determinada página do relatório com as teclas **Ctrl+F6**.

* Quando o foco está nos *separadores de página do relatório*, utilize as teclas de *tabulação* ou de *seta* para mover o foco de uma página do relatório para a página seguinte. O leitor de ecrã lê o título da página do relatório e se esta está atualmente selecionada. Para carregar a página do relatório que tem o foco, utilize a tecla *Enter* ou a *Barra de Espaço*.
* Quando o foco está numa *página do relatório* carregado, utilize a tecla de *tabulação* para mudar o foco para cada objeto na página, que inclui todas as caixas de texto, imagens, formas e gráficos. O leitor de ecrã lê o tipo de objeto e uma descrição desse objeto que é fornecida pelo respetivo autor. 

Pode premir **Alt+Shift+F10** para mover o foco para um menu visual.

Pode premir **Alt+Shift+F11** para apresentar uma versão acessível da janela *Ver dados*.

![Prima Alt+Shift+F11 no Power BI Desktop para apresentar uma janela Ver Dados acessível para um elemento visual](media/desktop-accessibility/accessibility_04.png)

Estas adições de acessibilidade foram criadas para permitir que os utilizadores consumam totalmente os relatórios do **Power BI Desktop** com a navegação de um leitor de ecrã ou de um teclado.

## <a name="tips-for-creating-accessible-reports"></a>Sugestões para criar relatórios acessíveis
As sugestões seguintes podem ajudar a criar relatórios do **Power BI Desktop** que são mais acessíveis.

* Para os elementos visuais de **Linha**, **Área** e **Combinação**, bem como para os elementos visuais de **Dispersão** e **Bolhas**, ative os marcadores e utilize uma *Forma do marcador* diferente para cada linha.
  
  * Para ativar os *Marcadores*, selecione a secção **Formato** no painel **Visualizações**, expanda a secção **Formas** e, em seguida, desloque o ecrã para baixo para localizar o botão de alternar **Marcadores** e *Ativá-lo*.
  * Em seguida, selecione o nome de cada linha (ou área, se utilizar um gráfico de **Área**) na caixa pendente dessa secção **Formas**. Abaixo da caixa pendente, pode ajustar muitos aspetos do marcador utilizado para a linha selecionada, incluindo a respetiva forma, cor e tamanho.
  
  ![Utilizar marcadores diferentes em gráficos de área e de linhas para melhorar a acessibilidade](media/desktop-accessibility/accessibility_01.png)
  
  * Utilizar uma *Forma do marcador* diferente para cada linha permite que os consumidores do relatório distingam mais facilmente as linhas (ou áreas) umas das outras.
* No seguimento do ponto anterior, não dependa da cor para transmitir informações. É útil utilizar formas em linhas (marcadores, conforme descrito nos pontos anteriores).
* Selecione um *tema* que seja de alto contraste e fácil de distinguir para as pessoas daltónicas na galeria de temas e importe-o com a [funcionalidade de pré-visualização **Personalização do Tema**](desktop-report-themes.md).
* Para cada objeto num relatório, forneça *Texto Alternativo*. Se o fizer, garante que os consumidores do seu relatório compreendem o que está a tentar comunicar com um elemento visual, mesmo que não consigam ver o elemento visual, imagem, forma ou caixa de texto. Pode fornecer *Texto Alternativo* para qualquer objeto num relatório do **Power BI Desktop**. Para isso, selecione o objeto (por exemplo, um elemento visual, forma, etc.) e, no painel **Visualizações**, selecione a secção **Formato**, expanda **Geral**, desloque-se para a parte inferior e preencha a caixa de texto **Texto Alternativo**.
  
  ![É possível adicionar texto alternativo para qualquer objeto num relatório, em Visualizações > Formato > Geral > caixa Texto Alternativo](media/desktop-accessibility/accessibility_02.png)
* Certifique-se de que os seus relatórios têm contraste suficiente entre o texto e as cores de fundo.
* Utilize tamanhos e tipos de letra de texto que sejam facilmente legíveis. Um tamanho de texto pequeno, ou tipos de letra que poderão ser difíceis de ler, são inúteis para a acessibilidade.
* Inclua um título, etiquetas do eixo e etiquetas de dados em todos os elementos visuais.

## <a name="considerations-and-limitations"></a>Considerações e limitações
Existem algumas limitações e problemas conhecidos nas funcionalidades de acessibilidade, descritos na lista seguinte:

* O JAWS é suportado nos relatórios que são visualizados no **serviço Power BI**, incluindo quaisquer relatórios incorporados. O JAWS também é suportado no **Power BI Desktop**; no entanto, tem de abrir o leitor de ecrã antes de abrir qualquer ficheiro do **Power BI Desktop**, para que o leitor de ecrã funcione corretamente.

## <a name="next-steps"></a>Próximos passos
* [Utilizar Temas de Relatório no Power BI Desktop (Pré-visualização)](desktop-report-themes.md)

