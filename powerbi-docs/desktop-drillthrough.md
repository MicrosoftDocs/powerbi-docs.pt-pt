---
title: Utilizar a pormenorização no Power BI Desktop
description: Saiba como utilizar a pormenorização para desagregar dados numa nova página de relatório no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a7b00b0cb611dd3e0921885ddaca6547fdb43fd3
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "74310901"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Utilizar a pormenorização no Power BI Desktop
Com a *pormenorização* no Power BI Desktop, pode criar uma página no relatório centrada numa entidade específica, por exemplo, um fornecedor, um cliente ou um fabricante. Selecione a pormenorização para poder utilizá-la. Para tal, clique com o botão direito do rato num ponto de dados noutras páginas de relatórios. Em seguida, pode explorar a página em destaque para obter detalhes filtrados em função desse contexto.

![Utilizar a pormenorização](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Utilizar a pormenorização
1. Para utilizar a pormenorização, crie uma página de relatório com os elementos visuais que pretende para o tipo de entidade para o qual vai fornecer pormenorização. 

    Por exemplo, imagine que pretende fornecer pormenorização para fabricantes. Neste caso, pode criar uma página de pormenorização com elementos visuais que demonstram as vendas totais, as unidades enviadas totais, as vendas por categoria, as vendas por região e assim por diante. Desta forma, quando pormenorizar nesta página, os elementos visuais serão específicos do fabricante selecionado.

2. Em seguida, na página de pormenorização, na secção **Campos** do painel **Visualizações**, arraste o campo para o qual quer ativar a pormenorização para a área **Filtros de pormenorização**.

    ![Área de pormenorização](media/desktop-drillthrough/drillthrough_02.png)

    Quando adicionar um campo à área **Filtros de pormenorização**, o Power BI Desktop irá automaticamente criar um visual de botão para *voltar*. Esse elemento visual torna-se num botão nos relatórios publicados. Os utilizadores que consomem o seu relatório no serviço Power BI utilizam este botão para voltar à página de relatório anterior.

    ![Imagem de pormenorização](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Utilizar a sua própria imagem para um botão Anterior    
 Como o botão anterior é uma imagem, pode substituir a imagem desse elemento visual por qualquer imagem desejada. O botão continuará a funcionar como um botão anterior para que os consumidores de relatórios possam voltar à página original. 

Para utilizar a sua própria imagem para um botão anterior, siga os passos seguintes:

1. No separador **Base**, selecione **Imagem**. Em seguida, localize a imagem e coloque-a na página de pormenorização.

2. Selecione a sua nova imagem na página de pormenorização. No painel **Formatar imagem**, defina o controlo de deslize **Ação** como **Ativado** e, em seguida, defina o **Tipo** como **Anterior**. A imagem funciona agora como um botão de retrocesso.

    ![Carregar imagem e definir o Tipo como Anterior](media/desktop-drillthrough/drillthrough_05.png)

    
     Agora, os utilizadores podem clicar com o botão direito do rato num ponto de dados no seu relatório e obter um menu de contexto que permite a pormenorização nessa página. 

    ![Menu de pormenorização](media/desktop-drillthrough/drillthrough_04.png)

    Quando os consumidores de relatórios escolherem a pormenorização, a página é filtrada para mostrar informações acerca do ponto de dados no qual clicaram com o botão direito do rato. Por exemplo, imaginemos que clicaram com o botão direito do rato num ponto de dados sobre a Contoso (um fabricante) e selecionaram pormenorização. A página de pormenorização que acederam é filtrada para a Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Passar todos os filtros na pormenorização

A partir da versão de maio de 2018 do Power BI Desktop, pode passar todos os filtros aplicados para a janela de pormenorização. Por exemplo, pode selecionar apenas uma determinada categoria de produtos e os elementos visuais dessa categoria e, em seguida, selecionar a pormenorização. Poderá estar interessado no aspeto que essa pormenorização teria com todos os filtros aplicados.

Para manter todos os filtros aplicados, na secção **Pormenorização** do painel **Visualizações**, defina o botão **Manter todos os filtros** como **Ativado**. 

![Manter todos os filtros](media/desktop-drillthrough/drillthrough_06.png)

Nas versões do Power BI Desktop lançadas antes de maio de 2018, o comportamento é equivalente a ter este botão **Desativado**.

Quando realiza o processo de pormenorização num elemento visual, pode ver quais os filtros aplicados como resultado do facto de o elemento visual de origem ter filtros aplicados temporariamente. Na secção **Pormenorização** do painel de **Visualização**, esses filtros transitórios são apresentados em itálico. 

![Filtros transitórios em itálico](media/desktop-drillthrough/drillthrough_07.png)

Embora pudesse fazer isto com páginas de descrições, acabaria por se tornar uma experiência estranha, uma vez que a descrição pareceria não estar a funcionar corretamente. Por esse motivo, não é recomendado fazê-lo com descrições.

## <a name="add-a-measure-to-drillthrough"></a>Adicionar uma medida à pormenorização

Além de transmitir todos os filtros para a janela de pormenorização, também pode adicionar uma medida ou uma coluna numérica resumida à área de pormenorização. Arraste o campo de pormenorização para o cartão de **Pormenorização** para o aplicar. 

![Adicionar uma medida à pormenorização](media/desktop-drillthrough/drillthrough_08.png)

Ao adicionar uma medida ou uma coluna numérica resumida, pode explorar a página quando o campo for utilizado na área *Valor* de um elemento visual.

É tudo o que precisa de saber acerca da utilização da pormenorização nos relatórios. É uma excelente forma de obter uma vista expandida das informações da entidade que selecionou para o seu filtro de pormenorização.

## <a name="next-steps"></a>Próximos passos

Poderá também estar interessado nos seguintes artigos:

* [Utilizar a pormenorização de relatório cruzado no Power BI Desktop](desktop-cross-report-drill-through.md)
* [Utilizar a segmentação de dados no Power BI Desktop](visuals/power-bi-visualization-slicers.md)

