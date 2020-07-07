---
title: Tabela de elementos visuais e registos nos elementos visuais do Power BI Desktop
description: Utilize as funcionalidades Tabela de elementos visuais e Tabela de ponto de dados do Power BI Desktop para explorar os detalhes
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: f70876b3b8c1815576ed019f88b67296f7aec052
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238613"
---
# <a name="use-visual-table-and-data-point-table-in-power-bi-desktop"></a>Utilizar a Tabela de elementos visuais e a Tabela de ponto de dados no Power BI Desktop
No **Power BI Desktop**, pode explorar os detalhes de uma visualização e ver representações textuais dos dados subjacentes ou registos dos dados individuais do elemento visual selecionado. Estas funcionalidades são, por vezes, referidas como *clicável*, *exploração* ou *exploração de detalhes*.

Pode utilizar a **Tabela de elementos visuais** para visualizar os dados num elemento visual como uma tabela ou pode utilizar uma **Tabela de ponto de dados** para visualizar uma tabela dos dados utilizados para calcular um único ponto de dados. 

![Tabela de elementos visuais e Tabela de ponto de dados](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>A **Tabela de elementos visuais** e a **Tabela de ponto de dados** suportam apenas os seguintes tipos de visualização:
>  - Gráfico de barras
>  - Gráfico de colunas
>  - Gráfico em anel
>  - Mapa de manchas
>  - Funil
>  - Mapa
>  - Gráfico circular
>  - Treemap

## <a name="use-visual-table-in-power-bi-desktop"></a>Utilizar a Tabela de elementos visuais no Power BI Desktop

A **Tabela de elementos visuais** mostra os dados subjacentes a uma visualização. A **Tabela de elementos visuais** aparece no separador **Dados/Pormenorização**, na secção **Mostrar** do friso, quando está selecionado um elemento visual.

![Tabela de elementos visuais no friso](media/desktop-see-data-see-records/visual-table-01.png)

Também pode ver os dados ao clicar com o botão direito do rato numa visualização e, em seguida, selecionar **Mostrar Dados** no menu apresentado ou selecionar **Mais opções** (…) no canto superior direito de uma visualização e, em seguida, selecionar **Mostrar como uma tabela**.

![Mostrar Dados com o botão direito do rato](media/desktop-see-data-see-records/visual-table-02.png)&nbsp;&nbsp;![Mostrar Dados com Mais Opções](media/desktop-see-data-see-records/visual-table-03.png)

> [!NOTE]
> Tem de colocar o cursor do rato sobre um ponto de dados no elemento visual para que o menu de contexto esteja disponível.

Quando selecionar **Tabela de elementos visuais** ou **Tabela de ponto de dados**, a tela do Power BI Desktop apresenta o elemento visual e a representação textual dos dados. Na *vista horizontal*, o elemento visual é apresentado na metade superior da tela e os dados são mostrados na metade inferior. 

![vista horizontal](media/desktop-see-data-see-records/visual-table-04.png)

Pode alternar entre a vista horizontal e a *vista vertical* ao selecionar o ícone no canto superior direito da tela.

![alternar vista vertical](media/desktop-see-data-see-records/visual-table-05.png)

Para voltar ao relatório, selecione **< Voltar ao Relatório** no canto superior esquerdo da tela.

![Voltar ao Relatório](media/desktop-see-data-see-records/visual-table-06.png)

## <a name="use-data-point-table-in-power-bi-desktop"></a>Utilizar a Tabela de ponto de dados no Power BI Desktop

Também pode concentrar-se num registo de dados numa visualização e explorar os dados. Para utilizar a **Tabela de ponto de dados**, selecione uma visualização e, em seguida, **Tabela de ponto de dados** no separador **Dados/Pormenorização** na secção **Ferramentas Visuais** do friso e, em seguida, selecione um ponto de dados ou uma linha na visualização. 

![Tabela de ponto de dados no friso](media/desktop-see-data-see-records/visual-table-07.png)

> [!NOTE]
> Se o botão **Tabela de ponto de dados** no friso estiver desativado e indisponível, significa que a visualização selecionada não suporta a **Tabela de ponto de dados**.

Também pode clicar com o botão direito do rato num elemento de dados e selecionar **Tabela de ponto de dados** no menu apresentado.

![Tabela de ponto de dados com clique do botão direito do rato](media/desktop-see-data-see-records/visual-table-08.png)

Quando selecionar **Tabela de ponto de dados** para um elemento de dados, a tela do Power BI Desktop apresenta todos os dados associados ao elemento selecionado. 

![](media/desktop-see-data-see-records/visual-table-09.png)

Para voltar ao relatório, selecione **< Voltar ao Relatório** no canto superior esquerdo da tela.


> [!NOTE]
>A **Tabela de ponto de dados** tem as seguintes limitações:
> - Não pode alterar os dados na vista **Tabela de ponto de dados** e guardá-los novamente no relatório.
> - Não pode utilizar a **Tabela de ponto de dados** quando o elemento visual utiliza uma medida calculada num grupo de medidas (multidimensional).
> - Não pode utilizar a **Tabela de ponto de dados** quando estiver ligado a um modelo multidimensional (MD).

## <a name="next-steps"></a>Próximos passos
Existem todos os tipos de formatação de relatórios e funcionalidades de gestão de dados no **Power BI Desktop**. Consulte os seguintes recursos para alguns exemplos:

* [Utilizar agrupamento e discretização no Power BI Desktop](desktop-grouping-and-binning.md)
* [Utilizar linhas de grelha, ajustar à grelha, ordenação z, alinhamento e distribuição em relatórios do Power BI Desktop](desktop-gridlines-snap-to-grid.md)

