---
title: Ver dados e registos nos elementos visuais do Power BI Desktop
description: Utilize as funcionalidades Ver Dados e Ver Registos do Power BI Desktop para explorar detalhes
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
ms.date: 02/22/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: c44a5140fe40217aac170abb0b351197803b6299
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Utilizar Ver Dados e Ver Registos no Power BI Desktop
No **Power BI Desktop**, pode explorar os detalhes de qualquer elemento visual e ver uma representação textual dos dados ou de elementos de dados individuais de um elemento visual selecionado. Estas funcionalidades são, por vezes, referidas como *clicável*, *exploração* ou *exploração de detalhes*.

Pode utilizar **Ver Registos** para ver as linhas subjacentes de um elemento de dados selecionado a partir de um elemento visual ou utilizar **Ver Dados** para ver uma versão textual dos valores utilizados no elemento visual. Existem algumas limitações de utilização de **Ver Dados** e **Ver Registos**, as quais são debatidas no final deste artigo.

![](media/desktop-see-data-see-records/see-data-see-records_1.png)

## <a name="using-see-data-in-power-bi-desktop"></a>Utilizar Ver Dados no Power BI Desktop
O botão **Ver Dados** está localizado no separador **Dados/Pormenorização** na secção **Ferramentas Visuais** do friso.

![](media/desktop-see-data-see-records/see-data-see-records_2.png)

Também pode **Ver Dados** ao clicar com o botão direito do rato num elemento visual e ao selecionar **Ver Dados** no menu apresentado.

![](media/desktop-see-data-see-records/see-data-see-records_3.png)

> [!NOTE]
> Tem de colocar o cursor do rato sobre um ponto de dados no elemento visual para que o menu de contexto esteja disponível.
> 
> 

Quando selecionar **Ver Dados**, o **Power BI Desktop** centra-se no elemento visual e nos dados selecionados e dedica o espaço da tela à apresentação do elemento visual e à representação textual dos dados. O elemento visual é apresentado na metade superior da tela e os dados são mostrados na metade inferior, conforme indicado na imagem seguinte. Esta é a vista *horizontal*.

![](media/desktop-see-data-see-records/see-data-see-records_4.png)

Também pode mudar para uma *vista vertical* (ou novamente para a *vista horizontal*) ao selecionar o ícone no canto superior direito.

![](media/desktop-see-data-see-records/see-data-see-records_5.png)

Para voltar ao relatório, selecione **< Voltar ao Relatório** no canto superior esquerdo da tela.

![](media/desktop-see-data-see-records/see-data-see-records_6.png)

## <a name="using-see-records-in-power-bi-desktop"></a>Utilizar Ver Registos no Power BI Desktop
Também pode concentrar-se num elemento de dados num elemento visual e explorar os respetivos dados. Depois de selecionar um elemento visual, existem duas formas de utilizar **Ver Registos**; pode ativar o botão **Ver Registos** no friso **Dados/Pormenorização** e, em seguida, clicar num elemento de dados ou clicar com o botão direito do rato num elemento de dados e selecionar **Ver Registos** no menu apresentado.

![](media/desktop-see-data-see-records/see-data-see-records_7.png)

> [!NOTE]
> Se o elemento visual selecionado não suportar **Ver Registos**, o botão aparece desativado no friso.
> 
> 

Depois de selecionar **Ver Registos**, o **Power BI Desktop** concentra-se nesse elemento de dados individual e dedica a área da tela à apresentação dos dados desse elemento, conforme mostrado na imagem seguinte.

![](media/desktop-see-data-see-records/see-data-see-records_8.png)

> [!NOTE]
> Não pode guardar as alterações dos dados visualizados (ou modificados por utilizadores) em **Ver Registos** num relatório.

Para voltar ao relatório, selecione o botão **Voltar ao Relatório** no canto superior esquerdo da tela.

## <a name="limitations"></a>Limitações
Existem algumas limitações a ter em consideração quando utilizar **Ver Dados** ou **Ver Registos**:

* Apenas são suportados os seguintes tipos de elemento visual:
  * **Barra**
  * **Coluna**
  * **Mapa**
  * **Mapa de Árvore**
  * **Mapa de Manchas**
  * **Circular**
  * **Anel**
  * **Funil**
* Não pode utilizar **Ver Registos** quando o elemento visual utiliza uma medida calculada
* Não pode utilizar **Ver Registos** quando estiver ligado a um modelo multidimensional (MD)

## <a name="next-steps"></a>Próximos passos
Existem todos os tipos de formatação de relatórios e funcionalidades de gestão de dados no **Power BI Desktop**. Consulte os seguintes recursos para alguns exemplos:

* [Utilizar agrupamento e discretização no Power BI Desktop](desktop-grouping-and-binning.md)
* [Utilizar linhas de grelha, ajustar à grelha, ordenação z, alinhamento e distribuição em relatórios do Power BI Desktop](desktop-gridlines-snap-to-grid.md)

