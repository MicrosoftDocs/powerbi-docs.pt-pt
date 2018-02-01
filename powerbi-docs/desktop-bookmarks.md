---
title: "Utilizar marcadores no Power BI (Pé-visualização)"
description: "Os marcadores no Power BI Desktop permitem-lhe guardar vistas e definições nos seus relatórios, bem como criar apresentações como se fossem uma história"
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: d09dcf28989f19fa901cb5f829e1149b9b64567f
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi-preview"></a>Utilizar marcadores para partilhar informações e criar histórias no Power BI (Pré-visualização)
Ao utilizar **marcadores** no Power BI, pode capturar a vista atualmente configurada de uma página de relatório, incluindo a filtragem e o estado dos elementos visuais, e voltar mais tarde a esse estado ao selecionar esse marcador guardado. 

Também pode criar uma coleção de marcadores, dispô-los pela ordem que quiser e, subsequentemente, seguir cada marcador numa apresentação para realçar uma série de informações ou a história que quer contar com os seus elementos visuais e relatórios. 

![Marcadores no Power BI](media/desktop-bookmarks/bookmarks_01.png)

Existem muitas utilizações de marcadores. Pode utilizá-los para controlar o seu próprio progresso de criação de relatórios (os marcadores são fáceis de adicionar, eliminar e mudar o nome) e pode criar uma apresentação do PowerPoint que utilize marcadores por ordem, contando assim uma história com o seu relatório. Podem existir outras utilizações com base na forma como considera que os marcadores podem ser melhor utilizados.

### <a name="enable-the-bookmarks-preview"></a>Ativar a pré-visualização de marcadores
Pode experimentar a nova funcionalidade **marcadores** a partir da versão de **outubro de 2017** do **Power BI Desktop** e para relatórios compatíveis com marcadores, também no **serviço Power BI**. Para ativar esta funcionalidade de pré-visualização, selecione **Ficheiro > Opções e Definições > Opções > Funcionalidades de Pré-visualização** e, em seguida, selecione a caixa de verificação junto a **Marcadores**. Terá de reiniciar o Power BI Desktop depois de efetuar a seleção.

![Ativar marcadores na janela Opções](media/desktop-bookmarks/bookmarks_02.png)

Terá de reiniciar o **Power BI Desktop** depois de efetuar a seleção.

## <a name="using-bookmarks"></a>Utilizar marcadores
Para utilizar marcadores, selecione o friso **Ver** e, em seguida, selecione a caixa **Painel de Marcadores**. 

![O Painel de Marcadores pode ser ativado no friso Ver.](media/desktop-bookmarks/bookmarks_03.png)

Quando criar um marcador, os elementos seguintes são guardados com o marcador:

* Página atual
* Filtros
* Segmentações
* Sequência de ordenação
* Localização de agregação
* Visibilidade (de um objeto, através do painel **Seleção**)
* Os modos de detalhe ou **Em Destaque** de qualquer objeto visível

Os marcadores não guardam atualmente o estado de realce cruzado. 

Configure uma página de relatório conforme quiser que apareça no marcador. Depois da página de relatório e dos elementos visuais serem dispostos como pretende, selecione **Adicionar** no painel **Marcadores** para adicionar um marcador. 

![Adicionar um marcador](media/desktop-bookmarks/bookmarks_04.png)

O **Power BI Desktop** cria um marcador e atribui-lhe um nome genérico. Pode facilmente *mudar o nome*, *eliminar* ou *atualizar* um marcador ao selecionar as reticências junto ao respetivo nome e, em seguida, ao selecionar uma ação no menu apresentado.

![Selecionar o submenu de um marcador através das reticências](media/desktop-bookmarks/bookmarks_05.png)

Depois de ter um marcador, pode apresentá-lo ao clicar simplesmente nele no painel **Marcadores**. 

## <a name="arranging-bookmarks"></a>Dispor marcadores
À medida que cria marcadores, pode considerar que a ordem pela qual são criados não é necessariamente a mesma ordem pela qual quer apresentá-los ao seu público. Não há problema, pode reorganizar facilmente a ordem dos marcadores.

No painel **Marcadores**, basta arrastar e largar marcadores para alterar a sua ordem, conforme mostrado na imagem seguinte. A barra amarela entre os marcadores designa onde o marcador arrastado será colocado.

![Alterar a ordem de marcadores ao arrastar e largar](media/desktop-bookmarks/bookmarks_06.png)

A ordem dos marcadores pode tornar-se importante quando utiliza a funcionalidade **Ver** dos marcadores, conforme descrito na secção seguinte.

## <a name="bookmarks-as-a-slide-show"></a>Marcadores como uma apresentação de diapositivos
Quando tiver uma coleção de marcadores que queira apresentar, por ordem, pode selecionar **Ver** no painel **Marcadores** para iniciar uma apresentação de diapositivos.

Quando estiver no modo **Visualização**, existem alguns aspetos a ter em consideração:

1. O nome do marcador é apresentado na barra de título, que aparece na parte inferior da tela.
2. A barra de título do marcador tem setas que lhe permitem mover para o marcador anterior ou seguinte
3. Pode sair do modo **Visualização** ao selecionar **Sair** no painel **Marcadores** ou ao selecionar o **X** localizado na barra de título do marcador. 

![Funcionalidades da barra de título do marcador](media/desktop-bookmarks/bookmarks_07.png)

Quando estiver no **Visualização**, pode fechar o painel **Marcadores** (ao clicar no X nesse painel) para dar mais espaço à sua apresentação. No modo **Visualização**, todos os elementos visuais são interativos e estão disponíveis para realce cruzado, tal como estão quando interage com os mesmos. 

## <a name="visibility---using-the-selection-pane"></a>Visibilidade – através do painel Seleção
Com o lançamento de marcadores, também é introduzido o novo painel **Seleção**. O painel **Seleção** fornece uma lista de todos os objetos na página atual e permite-lhe selecionar o objeto e especificar se um determinado objeto está visível. 

![Ativar o painel Seleção](media/desktop-bookmarks/bookmarks_08.png)

Pode selecionar um objeto através do painel **Seleção**. Além disso, pode alternar se o objeto está atualmente visível ao clicar no ícone de olho à direita do elemento visual. 

![Painel Seleção](media/desktop-bookmarks/bookmarks_09.png)

Quando é adicionado um marcador, o estado visível de cada objeto também é guardado com base na respetiva definição no painel **Seleção**. 

É importante ter em atenção que as **segmentações de dados** continuam a filtrar uma página de relatório, independentemente de estarem visíveis. Como tal, pode criar vários marcadores diferentes, com diversas definições de segmentação de dados e fazer uma única página de relatório parecer muito diferente (e realçar diferentes informações) em vários marcadores.

## <a name="bookmarks-for-shapes-and-images"></a>Marcadores para formas e imagens
Também pode ligar formas e imagens a marcadores. Com esta funcionalidade, quando clica num objeto, será apresentado o marcador associado a esse objeto. 

Para atribuir um marcador a um objeto, selecione o objeto e, em seguida, selecione **Ligar** no painel **Formatar Forma**, conforme mostrado na imagem seguinte.

![Adicionar uma ligação de marcador a um objeto](media/desktop-bookmarks/bookmarks_10.png)

Depois de colocar o controlo de deslize **Ligar** como **Ativado**, pode selecionar se o objeto é uma ligação ou um marcador. Se selecionar vários marcadores, pode selecionar a qual deles o objeto está ligado.

Existem todos os tipos de coisas interessantes que pode fazer com marcadores ligados a objetos. Pode criar um índice visual da página de relatório ou pode fornecer diferentes vistas (por exemplo, tipos visuais) dessas mesmas informações apenas ao clicar num objeto.

Quando estiver no modo de edição, pode utilizar ctrl+clique para seguir a ligação e, quando não estiver nesse modo, basta clicar no objeto para seguir a ligação. 

## <a name="using-spotlight"></a>Utilizar o modo Em Destaque
Outra funcionalidade lançada com os marcadores é o modo **Em Destaque**. Com o modo **Em Destaque**, pode chamar a atenção para um gráfico específico, por exemplo, quando apresentar os seus marcadores no modo **Visualização**.

Vamos comparar o modo **Em Destaque** com o modo de **detalhe** para ver as diferenças.

1. No modo de **detalhe**, pode ter um elemento visual a preencher toda a tela ao selecionar o ícone **modo de detalhe**.
2. Ao utilizar o modo **Em Destaque**, pode realçar um elemento visual no respetivo tamanho original, fazendo com que todos os outros elementos visuais na página desvaneçam para uma quase transparência. 

![Comparar os modos de detalhe e Em Destaque](media/desktop-bookmarks/bookmarks_11.png)

Quando o elemento visual na imagem anterior tiver o respetivo ícone de **detalhe** clicado, a página tem o seguinte aspeto:

![modo de detalhe](media/desktop-bookmarks/bookmarks_12.png)

Em contrapartida, quando o modo **Em Destaque** é selecionado no menu de reticências do elemento visual, a página parece ter o seguinte aspeto:

![modo em destaque](media/desktop-bookmarks/bookmarks_13.png)

Se qualquer um dos modos for selecionado quando é adicionado um marcador, esse modo (detalhe ou Em Destaque) é mantido no marcador.

## <a name="bookmarks-in-the-power-bi-service"></a>Marcadores no serviço Power BI
Quando publica um relatório no **serviço Power BI** com, pelo menos, um marcador, pode ver e interagir com esses marcadores no **serviço Power BI**. Para cada relatório que publicar, tem de ter, pelo menos, um marcador no relatório, antes de publicar, para a funcionalidade estar disponível no **serviço Power BI**.

Quando estão disponíveis marcadores num relatório, pode selecionar **Ver > Painel de seleção** ou **Ver > Painel de marcadores** para mostrar todos os painéis.

![Ver os painéis de marcadores e de seleção no serviço Power BI](media/desktop-bookmarks/bookmarks_14.png)

No **serviço Power BI**, o **Painel de marcadores** funciona tal como no **Power BI Desktop**, incluindo a capacidade de selecionar **Ver** para mostrar os marcadores por ordem, como uma apresentação de diapositivos.

Tenha em atenção que tem de utilizar a barra de título do marcador cinzenta para navegar pelos marcadores e não as setas pretas (as setas pretas movem-no nas páginas de relatório, não nos marcadores).

## <a name="limitations-and-considerations"></a>Limitações e considerações
Nesta versão de pré-visualização dos **marcadores**, existem algumas limitações e considerações a não esquecer.

* Os elementos visuais personalizados não funcionam com marcadores se forem a *origem* do filtro. Se estiver a utilizar elementos visuais personalizados para filtrar os elementos numa página (por exemplo, a segmentação de dados chiclete) e voltar a essa página através de um marcador, a página poderá ser filtrada, mas o elemento visual personalizado não será atualizado para mostrar como a página está a ser filtrada. 
* O estado de realce cruzado do painel do relatório *não* é guardado quando cria um marcador. 
* Se adicionar um elemento visual numa página de relatório depois de criar um marcador, este será apresentado no estado predefinido. Isto também significa que se apresentar uma segmentação de dados numa página onde criou anteriormente marcadores, esta irá estar no estado predefinido.
* O movimento entre os elementos visuais depois de ser criado um marcador será refletido no marcador. 
* *Tem* de ter, pelo menos, um marcador no relatório quando o publicar no **serviço Power BI**, para que os marcadores estejam disponíveis no serviço. Este é um requisito para cada relatório que publicar.
* Uma vez que os marcadores são, neste momento, uma Funcionalidade de Pré-visualização, ainda não estão disponíveis no [**Power BI Desktop para o Report Server**](report-server/quickstart-create-powerbi-report.md).

## <a name="next-steps"></a>Próximos passos
Para obter mais informações sobre funcionalidades semelhantes ou como interagir com marcadores, veja os artigos seguintes:

* [Utilizar a pormenorização no Power BI Desktop](desktop-drillthrough.md)
* [Apresentar um mosaico do dashboard ou um elemento visual do relatório no modo de detalhe](service-focus-mode.md)

