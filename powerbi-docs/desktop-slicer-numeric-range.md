---
title: "Utilizar a segmentação de dados de intervalo numérico no Power BI Desktop"
description: "Saiba como utilizar uma segmentação de dados para restrição a intervalos numéricos no Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/05/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f6e0433e8862e2acb6f0e7a72a1293e37f2185eb
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Utilizar a segmentação de dados de intervalo numérico no Power BI Desktop
Com a **segmentação de dados de intervalo numérico**, pode aplicar todos os tipos de filtros a qualquer coluna numérica no seu modelo de dados. Pode optar por filtrar **entre** números, **menos que ou igual** a um número ou **mais que ou igual** a um número. Apesar de parecer simples, é uma forma muito poderosa de filtrar os seus dados.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_2.png)

## <a name="using-the-numeric-range-slicer"></a>Utilizar a segmentação de dados do intervalo numérico
Pode utilizar a segmentação de dados de intervalo numérico tal como qualquer outra segmentação de dados. Basta criar um visual de **segmentação de dados** para o relatório e selecionar um valor numérico para o valor **Campo**. Na imagem seguinte, o campo *UnitPrice* está selecionado.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_3.png)

Selecione o acento circunflexo no canto superior direito da **segmentação de dados de intervalo numérico** e é apresentado um menu.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_4.png)

Para intervalos numéricos, pode selecionar de entre as seguintes três seleções:

* Entre
* Menor que ou igual a
* Maior que ou igual a

Ao selecionar **Entre** no menu, é apresentado um controlo de deslize que lhe permite filtrar por valores numéricos que se enquadrem entre os números. Além de utilizar a barra do controlo de deslize, pode clicar numa das caixas e escrever os valores. Esta forma é conveniente se pretender ter uma segmentação de dados sobre números inteiros específicos, mas a granularidade de mover a barra de controlo de deslize dificultar a obtenção do número exato.

Na imagem seguinte, a página de relatório está filtrada para os valores de *UnitPrice* entre 500 e 1500.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_5.png)

Quando selecionarmos **Menor que ou igual a**, a alça esquerda (valor inferior) da barra de controlo de deslize desaparece e podemos apenas ajustar o limite superior da barra de controlo de deslize. Na imagem seguinte, definimos a barra de controlo de deslize para 497,17.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_6.png)

Por último, se selecionarmos **Maior que ou igual a**, a barra de controlo de deslize à direita (valor mais alto) desaparece, e podemos ajustar o valor inferior, conforme visto na seguinte imagem. Agora, apenas os itens com *UnitPrice* igual ou superior a 750,56 são apresentados nos visuais na página de relatório.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_7.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer-preview"></a>Ajustar para números inteiros com a segmentação de dados do intervalo numérico (Pré-visualização)

A partir do lançamento de fevereiro de 2018 do **Power BI Desktop**, a segmentação de dados do intervalo numérico será ajustada para números inteiros. Esta funcionalidade permite que a segmentação de dados se alinhe corretamente com números inteiros. O ajuste para números inteiros não se aplica a filtros decimais.


## <a name="limitations-and-considerations"></a>Limitações e considerações
As seguintes limitações e considerações aplicam-se atualmente à **segmentação de dados de intervalo numérico**

* Atualmente, o **controlo de deslize de intervalo numérico** filtra todas as linhas subjacentes nos dados, não os valores agregados. Por exemplo, se for utilizado um campo de *Valor de Vendas*, cada transação baseada no *Valor de Vendas* seria filtrada, não a soma do *Valor de Vendas* para cada ponto de dados de um visual.
* Atualmente, não funciona em Medidas
* Atualmente, a **segmentação de dados de intervalo numérico** está disponível apenas no **Power BI Desktop**. Se um relatório que utilize a **segmentação de dados de intervalo numérico** for publicado no **serviço Power BI**, o filtro continuará a ser aplicado, mas será aplicado como segmentação de dados de lista.

