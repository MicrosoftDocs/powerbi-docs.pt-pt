---
title: Sobre filtros e realces em relatórios do Power BI
description: Sobre filtros e realces em relatórios do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/13/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 855ed26172fa0f157787ba4cfdc3e7e6ab4ff4ba
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="about-filters-and-highlighting-in-power-bi-reports"></a>Sobre filtros e realces em relatórios do Power BI
Os ***Filtros*** removem tudo, menos os dados em que se pretende focar.  O ***Destaque*** não filtra, pois não remove dados, mas realça um subconjunto dos dados visíveis; os dados não realçados permanecem visíveis, mas obscurecidos.

Existem várias formas diferentes de filtrar e realçar relatórios no Power BI. Colocar todas as informações num artigo seria confuso, pelo que dividimo-las desta forma:

* Introdução aos filtros e realce (este artigo)
* Formas de [criar e utilizar filtros e realçar na Vista de Edição/relatórios pertencentes a si](power-bi-report-add-filter.md). Quando tem permissões de edição de um relatório, pode criar, modificar e eliminar filtros e realces nos relatórios.
* Formas de [utilizar filtros e realce num relatório partilhado consigo ou na Vista de Leitura do relatório](service-reading-view-and-editing-view.md). As ações que pode efetuar são mais limitadas, mas o Power BI ainda lhe oferece uma grande diversidade de opções de filtragem e realce.  
* [Uma visita detalhada dos controlos de filtros e realce disponíveis na Vista de Edição](power-bi-how-to-report-filter.md), incluindo um olhar aprofundado sobre os tipos de ficheiros (por exemplo, data e hora, numéricos, texto) e a diferença entre as opções básicas e avançadas.
* Agora que sabe como os filtros e o realce funcionam por predefinição, [saiba como mudar a forma como as visualizações numa página se filtram e realçam](service-reports-visual-interactions.md)

> [!TIP]
> Como é que o Power BI conhece as relações entre os dados?  Utiliza as relações entre as diferentes tabelas e campos no [modelo de dados](https://support.office.com/article/Create-a-Data-Model-in-Excel-87e7a54c-87dc-488e-9410-5c75dbcb0f7b?ui=en-US&rs=en-US&ad=US) subjacente para fazer com que os itens numa página de relatório interajam um com o outro.
> 
> 

## <a name="introduction-to-filters-and-highlighting-in-reports-using-the-filters-pane"></a>Introdução aos filtros e realce nos relatórios através do painel Filtros
 Este artigo apresenta-lhe os filtros e os realces no serviço Power BI.  No entanto, a experiência é praticamente a mesma no Power BI Desktop.  

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Pode aplicar filtros e realce através do painel **Filtros** ou ao efetuar as seleções diretamente no próprio relatório (caso a caso, consultar parte inferior da página). O painel Filtros mostra as tabelas e os campos utilizados no relatório e os filtros que foram aplicados, se existirem. Os filtros estão divididos ao nível da **Página**, do **Relatório**, da **Pormenorização** e do **Visual**.  Só verá filtros ao nível visual se tiver selecionado uma visualização na tela de relatório.

> [!TIP]
> Se o filtro tiver a palavra **Tudo** junto ao mesmo, significa que todo o campo está a ser incluído como filtro.  Por exemplo, na captura de ecrã abaixo, **Chain(All)** (Cadeia(Tudo)) indica-nos que esta página de relatório inclui dados sobre todas as cadeias de lojas.  Por outro lado, o filtro ao nível de relatório de **FiscalYear is 2013 or 2014** indica que o relatório inclui apenas dados correspondentes aos anos fiscais de 2013 e 2014.
> 
> 

## <a name="filters-in-reading-view-versus-editing-view"></a>Filtros na Vista de Leitura versus Vista de Edição
Existem duas formas de interagir com os relatórios: [Vista de Leitura e Vista de Edição](service-reading-view-and-editing-view.md).  E as funções de filtragem disponíveis para si dependem do modo no qual se encontra.

* Na Vista de Edição, pode adicionar filtros de relatório, página, pormenorização e elemento visual. Ao guardar o relatório, os filtros são guardados com o relatório, mesmo que abra o relatório numa aplicação móvel. As pessoas que veem o relatório na Vista de Leitura podem interagir com os filtros que adicionou, mas não podem adicionar novos filtros.
* Na Vista de Leitura, pode interagir com qualquer filtro existente no relatório e guardar as seleções que fizer.  No entanto, não poderá adicionar novos filtros.

### <a name="the-filters-pane-in-reading-view"></a>Painel Filtros na Vista de Leitura
Se apenas tiver acesso a um relatório na Vista de Leitura, o painel Filtros terá um aspeto semelhante a este:

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Significa que esta página do relatório tem 6 filtros ao nível de página e 1 filtro ao nível de relatório.

Para ver se existem filtros ao nível de visual, selecione um visual. Na imagem abaixo, o gráfico de bolhas tem 6 filtros aplicados.

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

Na Vista de Leitura, explore os dados ao modificar os filtros existentes. As alterações que fizer são guardadas com o relatório, mesmo que abra o relatório numa aplicação móvel. Saiba como no artigo [Vista de Leitura e Vista de Edição no serviço Power BI](service-reading-view-and-editing-view.md)

### <a name="the-filters-pane-in-editing-view"></a>Painel Filtros na Vista de Edição
Quando tiver permissões de proprietário para um relatório e abrir o mesmo na Vista de Edição, irá ver que **Filtros** é apenas um de vários painéis de edição disponíveis.

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

Conforme acontece na Vista de Leitura (acima), vemos que esta página do relatório tem 6 filtros ao nível de página e 1 filtro ao nível de relatório. Ao selecionar o gráfico de bolhas, vemos que tem 6 filtros de nível visual aplicados.

No entanto, na Vista de Edição, há muito mais que se pode fazer com filtros e realces. A principal diferença é o facto de se poder adicionar novos filtros. Saiba como fazer isto e muito mais no artigo [Adicionar um filtro a um relatório](power-bi-report-add-filter.md)

## <a name="ad-hoc-filtering-and-highlighting"></a>Filtragem e realce caso a caso
Selecione um filtro na tela de relatório para filtrar e realçar o resto da página. Selecione um espaço vazio no mesmo visual para removê-lo. Este tipo de filtragem e realce é uma forma divertida de explorar rapidamente os impactos de dados. Para ajustar a forma como este tipo de filtragem cruzada e realce cruzado funciona, veja [Interações de visualização](service-reports-visual-interactions.md).

![](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

Ao sair do relatório, as suas alterações são guardadas. Para anular a sua filtragem, selecione **Repor para predefinição** na barra de menus superior.

![](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

## <a name="next-steps"></a>Próximos passos
[Interação com os filtros e realce (na Vista de Leitura)](service-reading-view-and-editing-view.md)

[Adicionar um filtro a um relatório (na Vista de Edição)](power-bi-report-add-filter.md)

[Fazer uma visita aos filtros de relatórios](power-bi-how-to-report-filter.md)

[Alterar como visuais de relatórios executam filtro cruzado e realce cruzado entre si](service-reports-visual-interactions.md)

Leia mais sobre os [relatórios no Power BI](service-reports.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

