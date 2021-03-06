---
title: Descrição geral dos marcadores nos relatórios do serviço Power BI
description: Tópico de descrição geral da documentação para marcadores no serviço Power BI.
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/03/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 7aa199547f6cad0b7d4dbfc6b75e9d9e25b2b153
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96578343"
---
# <a name="what-are-bookmarks"></a>O que são marcadores?

[!INCLUDE[consumer-appliesto-ynnm](../includes/consumer-appliesto-ynnm.md)]


Os marcadores capturam a vista atualmente configurada de uma página de relatório, incluindo filtros, segmentações e o estado dos elementos visuais. Ao selecionar um marcador, o Power BI permite-lhe voltar a essa vista. Existem dois tipos de marcadores: os criados por si e os criados por *designers* de relatórios. Qualquer utilizador do Power BI pode criar marcadores pessoais. No entanto, a capacidade de utilizar marcadores criados por outros exige uma licença Power BI Pro ou Premium. [Qual é a minha licença?](end-user-license.md)

## <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Utilizar marcadores para partilhar informações e criar histórias no Power BI 
Os marcadores podem ser utilizados de várias formas. Suponhamos que descobre informações interessantes e que quer preservá-las – crie um marcador para que possa voltar às mesmas mais tarde. Se precisar de sair e quiser preservar o seu trabalho atual, crie um marcador. Pode até fazer com que um marcador seja a sua vista predefinida do relatório para que, sempre que regressar, essa vista da página do relatório seja aberta em primeiro lugar. 

Também pode criar uma coleção de marcadores, dispô-los pela ordem que quiser e, posteriormente, seguir cada marcador numa apresentação para realçar uma série de informações que contam uma história.  

![Mostrar o Painel de Marcadores ao selecioná-lo no friso.](media/end-user-bookmarks/power-bi-bookmark-icon.png)

Partilhe o seu relatório com marcadores com colegas que também têm acesso de leitura ao seu relatório. A vista com marcadores do relatório não substitui o relatório original do criador.  Partilhar com colegas que ainda não têm acesso de leitura requer permissões de nova partilha. Se não conseguir partilhar a sua vista do relatório, contacte o proprietário do relatório para pedir permissão de nova partilha.  


### <a name="share-changes"></a>Partilhar alterações 
Se tiver permissões de leitura e partilha, quando partilhar o relatório, poderá optar por incluir as suas alterações.

:::image type="content" source="media/end-user-bookmarks/power-bi-personalize-share-changes.png" alt-text="Partilhar alterações":::
 


## <a name="open-bookmarks"></a>Abrir marcadores
Para abrir o painel Marcadores, selecione **Marcadores** > **Mostrar mais marcadores** na barra de menus. 

![captura de ecrã da tela de relatórios com o painel Marcadores aberto.](media/end-user-bookmarks/power-bi-show-bookmarks.png)

Para regressar à vista publicada original do relatório, selecione o ícone de **reposição**.

![captura de ecrã com o ícone de reposição selecionado](media/end-user-bookmarks/power-bi-revert.png)

### <a name="report-bookmarks"></a>Marcadores de relatório
Se o *designer* de relatórios tiver incluído marcadores de relatório, irá encontrá-los no título **Marcadores de relatório**. Esta página de relatório tem quatro marcadores: B1, B2, VanArsdel Ano Até à Data e Todos Ano Até à Data. O marcador **Todos Ano Até à Data** está atualmente selecionado.

> [!NOTE]
> Irá precisar do Power BI Pro ou Premium para ver relatórios partilhados. 

![Mostrar Marcadores de relatório.](media/end-user-bookmarks/power-bi-bookmark-list.png)

Selecione um marcador para mudar para essa vista de relatório. 

![Vídeo a mostrar a seleção de marcadores de relatório.](media/end-user-bookmarks/power-bi-bookmarks.gif)

### <a name="personal-bookmarks"></a>Marcadores pessoais

Se conseguir ver um relatório, significa que também pode adicionar marcadores pessoais.  Quando criar um marcador, os elementos seguintes são guardados com o marcador:

* Página atual
* Filtros
* Segmentação de Dados, incluindo o tipo de segmentação de dados (por exemplo, lista pendente ou lista) e o estado da segmentação de dados
* Estado da seleção do elemento visual (por exemplo, os filtros de realce cruzado)
* Sequência de ordenação
* Localização de agregação
* Visibilidade (de um objeto, através do painel **Seleção**)
* Os modos de detalhe ou **Em Destaque** de qualquer objeto visível

Configure uma página de relatório conforme quiser que apareça no marcador. Neste exemplo:

1. Alterámos o filtro Data existente no painel **Filtros**,
1. alterámos o filtro Regiões existente no painel **Filtros** e
1.  selecionámos pontos de dados no elemento visual do gráfico em anel para filtrar e realçar de forma cruzada a tela do relatório. 

Depois da página de relatório e dos elementos visuais serem dispostos como pretende, selecione **Adicionar** no painel **Marcadores** para adicionar um marcador. 

![Adicionar Marcadores pessoais.](media/end-user-bookmarks/power-bi-personal.png)

O **Power BI** cria um marcador pessoal e atribui-lhe um nome genérico ou um nome que introduzir. Pode *mudar o nome*, *eliminar* ou *atualizar* o seu marcador ao selecionar as reticências junto ao nome do mesmo e, em seguida, ao selecionar uma ação no menu apresentado.

Depois de ter um marcador, selecione-o para o visualizar no painel **Marcadores**. 

![Visualize um marcador específico ao selecioná-lo.](media/end-user-bookmarks/power-bi-selected.png)


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

![Apresentação de diapositivos de marcadores](media/end-user-bookmarks/power-bi-view-bookmarks.png)

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
You can also link shapes and images to bookmarks. With this feature, when you click on an object, it will show the bookmark associated with that object. This can be especially useful when working with buttons; you can learn more by reading the article about [using buttons in Power BI](../create-reports/desktop-buttons.md). 

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


### <a name="reset-all-your-changes-to-a-report"></a>Repor todas as alterações a um relatório

No canto superior direito da tela do relatório, selecione **Repor para predefinição**. Esta ação remove todas as alterações no relatório e volta para a última vista guardada pelo autor do relatório.

:::image type="content" source="media/end-user-bookmarks/power-bi-personalize-reset-all.png" alt-text="Repor todas as alterações":::



## <a name="limitations-and-considerations"></a>Limitações e considerações
Nesta versão dos **marcadores**, existem algumas limitações e considerações a não esquecer.

* A maioria dos elementos visuais personalizados do Power BI deve funcionar devidamente com a marcação. Caso se depare com problemas com um marcador e um elemento visual personalizado do Power BI, contacte o criador desse elemento visual personalizado e peça-lhe para adicionar suporte para marcadores.    
* Se adicionar um elemento visual numa página de relatório depois de criar um marcador, este será apresentado no estado predefinido. Isto também significa que se apresentar uma segmentação de dados numa página onde criou anteriormente marcadores, esta irá estar no estado predefinido.
* Em geral, os seus marcadores não serão afetados se o *designer* de relatórios atualizar ou republicar o relatório. No entanto, se o designer fizer alterações significativas ao relatório, como remover campos utilizados por um marcador, será apresentada uma mensagem de erro na próxima vez que tentar abrir esse marcador. 
* Esta funcionalidade é suportada nas aplicações móveis do Power BI para tablets iOS e Android e na aplicação Windows do Power BI; não é suportada nas aplicações móveis do Power BI para telemóveis. No entanto, qualquer alteração a um elemento visual que guardar num marcador pessoal enquanto está no serviço Power BI será respeitada em todas as aplicações móveis do Power BI.


## <a name="next-steps"></a>Passos seguintes
[Personalizar os elementos visuais num relatório](end-user-personalize-visuals.md)
