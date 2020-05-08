---
title: Descrição geral dos marcadores nos relatórios do serviço Power BI
description: Tópico de descrição geral da documentação para marcadores no serviço Power BI.
author: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 7d1e355f2c28679f5c2101d250a9fc2d5c99a2bd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79205648"
---
# <a name="what-are-bookmarks"></a>O que são marcadores?

[!INCLUDE[consumer-appliesto-ynnm](../includes/consumer-appliesto-ynnm.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Os marcadores capturam a vista atualmente configurada de uma página de relatório, incluindo filtros, segmentações e o estado dos elementos visuais. Ao selecionar um marcador, o Power BI permite-lhe voltar a essa vista. Existem dois tipos de marcadores: os criados por si e os criados por *designers* de relatórios. Qualquer utilizador do Power BI pode criar marcadores pessoais. No entanto, a capacidade de utilizar marcadores criados por outros exige uma licença Power BI Pro ou Premium. [Qual é a minha licença?](end-user-license.md)

## <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Utilizar marcadores para partilhar informações e criar histórias no Power BI 
Os marcadores podem ser utilizados de várias formas. Suponhamos que descobre informações interessantes e que quer preservá-las – crie um marcador para que possa voltar às mesmas mais tarde. Se precisar de sair e quiser preservar o seu trabalho atual, crie um marcador. Pode até fazer com que um marcador seja a sua vista predefinida do relatório para que, sempre que regressar, essa vista da página do relatório seja aberta em primeiro lugar. 

Também pode criar uma coleção de marcadores, dispô-los pela ordem que quiser e, posteriormente, seguir cada marcador numa apresentação para realçar uma série de informações que contam uma história.  

![Mostrar o Painel de Marcadores ao selecioná-lo no friso.](media/end-user-bookmarks/power-bi-select-bookmark.png)

## <a name="open-bookmarks"></a>Abrir marcadores
Para abrir o painel Marcadores, selecione **Marcadores** > **Mostrar mais marcadores** na barra de menus. Para regressar à vista publicada original do relatório, selecione **Repor para predefinição**.

### <a name="report-bookmarks"></a>Marcadores de relatório
Se o *designer* de relatórios tiver incluído marcadores de relatório, irá encontrá-los no título **Marcadores de relatório**. Esta página de relatórios tem dois marcadores, B1 e B2. 

> [!NOTE]
> Irá precisar do Power BI Pro ou Premium para ver relatórios partilhados. 

![Mostrar Marcadores de relatório.](media/end-user-bookmarks/power-bi-report.png)

Selecione um marcador para mudar para essa vista de relatório. 

![Vídeo a mostrar a seleção de marcadores de relatório.](media/end-user-bookmarks/power-bi-bookmarks.gif)

### <a name="personal-bookmarks"></a>Marcadores pessoais

Quando criar um marcador, os elementos seguintes são guardados com o marcador:

* Página atual
* Vistas
* Segmentação de Dados, incluindo o tipo de segmentação de dados (por exemplo, lista pendente ou lista) e o estado da segmentação de dados
* Estado da seleção do elemento visual (por exemplo, os filtros de realce cruzado)
* Sequência de ordenação
* Localização de agregação
* Visibilidade (de um objeto, através do painel **Seleção**)
* Os modos de detalhe ou **Em Destaque** de qualquer objeto visível

Configure uma página de relatório conforme quiser que apareça no marcador. Depois da página de relatório e dos elementos visuais serem dispostos como pretende, selecione **Adicionar** no painel **Marcadores** para adicionar um marcador. Neste exemplo, adicionámos alguns filtros para a região e a data. 

![Adicionar Marcadores pessoais.](media/end-user-bookmarks/power-bi-bookmark-personal.png)

O **Power BI** cria um marcador pessoal e atribui-lhe um nome genérico ou um nome que introduzir. Pode *mudar o nome*, *eliminar* ou *atualizar* o seu marcador ao selecionar as reticências junto ao nome do mesmo e, em seguida, ao selecionar uma ação no menu apresentado.

Depois de ter um marcador, pode visualizar o mesmo ao selecioná-lo simplesmente no painel **Marcadores**. 

![Adicionar Marcadores pessoais.](media/end-user-bookmarks/power-bi-bookmark-west.png)


<!--
## Arranging bookmarks
As you create bookmarks, you might find that the order in which you create them isn't necessarily the same order you'd like to present them to your audience. No problem, you can easily rearrange the order of bookmarks.

In the **Bookmarks** pane, simply drag-and-drop bookmarks to change their order, as shown in the following image. The yellow bar between bookmarks designates where the dragged bookmark will be placed.

![Change bookmark order by drag-and-drop](media/desktop-bookmarks/bookmarks_06.png)

The order of your bookmarks can become important when you use the **View** feature of bookmarks, as described in the next section. 

-->

## <a name="bookmarks-as-a-slide-show"></a>Marcadores como uma apresentação de diapositivos
Para apresentar ou ver marcadores, por ordem, selecione **Visualização** no painel **Marcadores** para iniciar uma apresentação de diapositivos.

Quando estiver no modo **Visualização**, existem alguns aspetos a ter em consideração:

- O nome do marcador é apresentado na barra de título, que aparece na parte inferior da tela.
- A barra de título do marcador tem setas que lhe permitem mover para o marcador anterior ou seguinte.
- Pode sair do modo **Visualização** ao selecionar **Sair** no painel **Marcadores** ou ao selecionar o **X** localizado na barra de título do marcador.

![Apresentação de diapositivos de marcadores](media/end-user-bookmarks/power-bi-slideshow.png)

Quando estiver no **Visualização**, pode fechar o painel **Marcadores** (ao clicar no X nesse painel) para dar mais espaço à sua apresentação. No modo **Visualização**, todos os elementos visuais são interativos e estão disponíveis para realce cruzado, tal como acontece quando interage com eles. 

<!--
## Visibility - using the Selection pane
With the release of bookmarks, the new **Selection** pane is also introduced. The **Selection** pane provides a list of all objects on the current page and allows you to select the object and specify whether a given object is visible. 

![Enable the Selection pane](media/desktop-bookmarks/bookmarks_08.png)

You can select an object using the **Selection** pane. Also, you can toggle whether the object is currently visible by clicking the eye icon to the right of the visual. 

![Selection pane](media/desktop-bookmarks/bookmarks_09.png)

When a bookmark is added, the visible status of each object is also saved based on its setting in the **Selection** pane. 

It's important to note that **slicers** continue to filter a report page, regardless of whether they are visible. As such, you can create many different bookmarks, with different slicer settings, and make a single report page appear very different (and highlight different insights) in various bookmarks.


## Bookmarks for shapes and images
You can also link shapes and images to bookmarks. With this feature, when you click on an object, it will show the bookmark associated with that object. This can be especially useful when working with buttons; you can learn more by reading the article about [using buttons in Power BI](desktop-buttons.md). 

To assign a bookmark to an object, select the object, then expand the **Action** section from the **Format Shape** pane, as shown in the following image.

![Add bookmark link to an object](media/desktop-bookmarks/bookmarks_10.png)

Once you turn the **Action** slider to **On** you can select whether the object is a back button, a bookmark, or a Q&A command. If you select bookmark, you can then select which of your bookmarks the object is linked to.

There are all sorts of interesting things you can do with object-linked bookmarking. You can create a visual table of contents on your report page, or you can provide different views (such as visual types) of the same information, just by clicking on an object.

When you are in editing mode you can use ctrl+click to follow the link, and when not in edit mode, simply click the object to follow the link. 


## Bookmark groups

Beginning with the August 2018 release of **Power BI Desktop**, you can create and use bookmark groups. A bookmark group is a collection of bookmarks that you specify, which can be shown and organized as a group. 

To create a bookmark group, hold down the CTRL key and select the bookmarks you want to include in the group, then click the ellipses beside any of the selected bookmarks, and select **Group** from the menu that appears.

![Create a bookmark group](media/desktop-bookmarks/bookmarks_15.png)

**Power BI Desktop** automatically names the group *Group 1*. Fortunately, you can just double-click on the name and rename it to whatever you want.

![Rename a bookmark group](media/desktop-bookmarks/bookmarks_16.png)

With any bookmark group, clicking on the bookmark group's name only expands or collapses the group of bookmarks, and does not represent a bookmark by itself. 

When using the **View** feature of bookmarks, the following applies:

* If the selected bookmark is in a group when you select **View** from bookmarks, only the bookmarks *in that group* are shown in the viewing session. 

* If the selected bookmark is not in a group, or is on the top level (such as the name of a bookmark group), then all bookmarks for the entire report are played, including bookmarks in any group. 

To ungroup bookmarks, just select any bookmark in a group, click the ellipses, and then select **Ungroup** from the menu that appears. 

![Ungroup a bookmark group](media/desktop-bookmarks/bookmarks_17.png)

Note that selecting **Ungroup** for any bookmark from a group takes all bookmarks out of the group (it deletes the group, but not the bookmarks themselves). So to remove a single bookmark from a group, you need to **Ungroup** any member from that group, which deletes the grouping, then select the members you want in the new group (using CTRL and clicking each bookmark), and select **Group** again. 
-->





## <a name="limitations-and-considerations"></a>Limitações e considerações
Nesta versão dos **marcadores**, existem algumas limitações e considerações a não esquecer.

* A maioria dos elementos visuais do Power BI deve funcionar devidamente com a marcação. Caso se depare com problemas com um marcador e um elemento visual do Power BI, contacte o criador desse elemento visual do Power BI e peça-lhe para adicionar suporte para marcadores ao elemento visual.
* Se adicionar um elemento visual numa página de relatório depois de criar um marcador, este será apresentado no estado predefinido. Isto também significa que se apresentar uma segmentação de dados numa página onde criou anteriormente marcadores, esta irá estar no estado predefinido.
* Em geral, os seus marcadores não serão afetados se o *designer* de relatórios atualizar ou republicar o relatório. No entanto, se o designer fizer alterações significativas ao relatório, como remover campos utilizados por um marcador, será apresentada uma mensagem de erro na próxima vez que tentar abrir esse marcador. 

<!--
## Next steps
spotlight?
-->
