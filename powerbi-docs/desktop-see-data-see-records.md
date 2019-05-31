---
title: Ver dados e registos nos elementos visuais do Power BI Desktop
description: Utilize as funcionalidades Ver Dados e Ver Registos do Power BI Desktop para explorar detalhes
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 6e425f146228d0139b9eec914a44ed5dc732fe98
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514773"
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Utilizar Ver Dados e Ver Registos no Power BI Desktop
No **Power BI Desktop**, pode explorar os detalhes de uma visualização e ver representações textuais dos dados subjacentes ou registos dos dados individuais do elemento visual selecionado. Estas funcionalidades são, por vezes, referidas como *clicável*, *exploração* ou *exploração de detalhes*.

Pode utilizar **Ver Dados** para ver uma versão textual dos valores utilizados na visualização ou utilizar**Ver Registos** para ver todos os dados selecionados para um registo ou ponto de dados selecionado. 

![Utilizar Ver Dados e Ver Registos](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>As opções **Ver Dados** e **Ver Registos** suportam apenas os seguintes tipos de visualização:
>  - Gráfico de barras
>  - Gráfico de colunas
>  - Gráfico em anel
>  - Mapa de manchas
>  - Funil
>  - Mapa
>  - Gráfico circular
>  - Treemap

## <a name="use-see-data-in-power-bi-desktop"></a>Utilizar Ver Dados no Power BI Desktop

**Ver Dados** mostra os dados subjacentes a uma visualização. **Ver Dados** aparece no separador **Dados/Pormenorização** na secção **Ferramentas Visuais** do friso quando está selecionada uma visualização.

![Ver Dados no friso](media/desktop-see-data-see-records/see-data1.png)

Também pode ver os dados ao clicar com o botão direito do rato numa visualização e, em seguida, selecionar **Mostrar Dados** no menu apresentado; ou ao selecionar as reticências de **Mais opções** (…) no canto superior direito de uma visualização e, em seguida, selecionar **Mostrar Dados**.

![Mostrar Dados com o botão direito do rato](media/desktop-see-data-see-records/see-data2.png)&nbsp;&nbsp;![Mostrar Dados com Mais Opções](media/desktop-see-data-see-records/see-data3.png)

> [!NOTE]
> Tem de colocar o cursor do rato sobre um ponto de dados no elemento visual para que o menu de contexto esteja disponível.

Quando selecionar **Ver Dados** ou **Mostrar Dados**, a tela do Power BI Desktop apresenta o elemento visual e a representação textual dos dados. Na *vista horizontal*, o elemento visual é apresentado na metade superior da tela e os dados são mostrados na metade inferior. 

![vista horizontal](media/desktop-see-data-see-records/see-data4a.png)

Pode alternar entre a vista horizontal e a *vista vertical* ao selecionar o ícone no canto superior direito da tela.

![alternar vista vertical](media/desktop-see-data-see-records/see-data4.png)

Para voltar ao relatório, selecione **< Voltar ao Relatório** no canto superior esquerdo da tela.

![Voltar ao Relatório](media/desktop-see-data-see-records/see-data5.png)

## <a name="use-see-records-in-power-bi-desktop"></a>Utilizar Ver Registos no Power BI Desktop

Também pode concentrar-se num registo de dados numa visualização e explorar os dados. Para utilizar **Ver Registos**, selecione uma visualização e, em seguida, **Ver Registos** no separador **Dados/Pormenorização** na secção **Ferramentas Visuais** do friso e, em seguida, selecione um ponto de dados ou uma linha na visualização. 

![Ver Registos no friso](media/desktop-see-data-see-records/see-record1.png)

> [!NOTE]
> Se o botão **Ver Registos** no friso estiver desativado e indisponível, significa que a visualização selecionada não suporta a opção **Ver Registos**.

Também pode clicar com o botão direito do rato num elemento de dados e selecionar **Ver Registos** no menu apresentado.

![Ver Registos com o botão direito do rato](media/desktop-see-data-see-records/see-record2.png)

Quando selecionar **Ver Registos** para um elemento de dados, a tela do Power BI Desktop apresenta todos os dados associados ao elemento selecionado. 

![](media/desktop-see-data-see-records/see-record3.png)

Para voltar ao relatório, selecione **< Voltar ao Relatório** no canto superior esquerdo da tela.

![](media/desktop-see-data-see-records/see-record4.png)

> [!NOTE]
>**Ver Registos** tem as seguintes limitações:
> - Não pode alterar os dados na vista **Ver Registos** e guardá-los novamente no relatório.
> - Não pode utilizar **Ver Registos** quando o elemento visual utiliza uma medida calculada.
> - Não pode utilizar **Ver Registos** quando estiver ligado a um modelo multidimensional (MD).

## <a name="next-steps"></a>Próximos passos
Existem todos os tipos de formatação de relatórios e funcionalidades de gestão de dados no **Power BI Desktop**. Consulte os seguintes recursos para alguns exemplos:

* [Utilizar agrupamento e discretização no Power BI Desktop](desktop-grouping-and-binning.md)
* [Utilizar linhas de grelha, ajustar à grelha, ordenação z, alinhamento e distribuição em relatórios do Power BI Desktop](desktop-gridlines-snap-to-grid.md)

