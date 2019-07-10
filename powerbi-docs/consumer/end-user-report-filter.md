---
title: Fazer uma visita ao painel Filtros de relatórios
description: Como adicionar um filtro a um relatório no serviço Power BI para consumidores
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532992"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Fazer uma visita do painel Filtros

Este artigo analisa o painel **Filtros** de relatórios no serviço Power BI. Utilize os filtros para descobrir novas informações nos seus dados.

Existem muitas formas diferentes de filtrar dados no Power BI. Para obter mais informações sobre os filtros, veja [Filtros e realces nos relatórios do Power BI](../power-bi-reports-filters-and-highlighting.md).

![Captura de ecrã a mostrar um relatório no browser com uma seta a apontar para a opção Filtros.](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Trabalhar com o painel Filtros

Quando um colega partilha um relatório consigo, verifique o painel **Filtros**. Por vezes, é encolhido ao longo da margem direita do relatório. Selecione-o para expandi-lo.

![Captura de ecrã a mostrar o relatório com o painel Filtros expandido.](media/end-user-report-filter/power-bi-filter-pane.png)

O painel **Filtros** contém filtros que o *estruturador* do relatório adicionou ao mesmo. Os *consumidores* podem interagir com os filtros existentes e guardar alterações, mas não podem adicionar novos filtros ao relatório. Por exemplo, na captura de ecrã acima, o estruturador adicionou dois filtros de nível de página: **Segment** (Segmento) e **Year** (Ano). Pode interagir com estes filtros e alterá-los, mas não pode adicionar um terceiro filtro de nível de página.

No serviço Power BI, todas as alterações efetuadas no painel **Filtros** são mantidas nos relatórios. O serviço aplica essas alterações na versão do relatório para dispositivos móveis.

Para repor o painel **Filtros** para as predefinições do estruturador, selecione ![Captura de ecrã a mostrar a opção Repor para predefinição](media/end-user-report-filter/power-bi-reset.png) na barra de menus superior.

## <a name="view-all-the-filters-for-a-report-page"></a>Ver todos os filtros de uma página de relatórios

O painel **Filtros** apresenta todos os filtros que o estruturador adicionou ao relatório. O painel **Filtros** também é a área em que pode ver informações sobre os filtros e interagir com os mesmos. Pode guardar as alterações que efetuar ou utilizar a opção **Repor para predefinição** para reverter para as definições originais de filtros.

Se tiver alterações que pretende guardar, também pode criar um marcador pessoal.  Para obter mais informações, veja [O que são os marcadores?](end-user-bookmarks.md).

O painel **Filtros** apresenta e gere vários tipos de filtros de relatórios. Estes podem ser aplicados a um elemento visual, a uma página de relatório e a todo um relatório.

Neste exemplo, selecionámos um elemento visual com dois filtros. A página de relatórios também tem filtros, listados no cabeçalho **Filtros nesta página**. O relatório tem um filtro de **Data**.

![Captura de ecrã a mostrar um relatório com os seus filtros relacionados e uma visualização em destaque.](media/end-user-report-filter/power-bi-all-filters2.png)

Alguns filtros têm **(Todos)** junto aos mesmos. **(Todos)** significa que todos os valores são incluídos no filtro. Na captura de ecrã apresentada acima, **Segment (Todos)** (Segmento [Tudo]) indica que esta página de relatório inclui dados sobre todos os segmentos de produtos. Se selecionar o filtro de nível de página **Region is West** (A Região é Oeste), a página do relatório só inclui dados da região Oeste.

Qualquer pessoa a ver este relatório pode interagir com estes filtros.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Ver apenas estes filtros aplicados a um elemento visual

Para examinar mais detalhadamente os filtros aplicados a um elemento visual específico, paire o cursor sobre o elemento visual para revelar o ícone de filtro ![Captura de ecrã a mostrar o ícone Filtrar.](media/end-user-report-filter/power-bi-filter-icon.png). Selecione este ícone de filtro para ver um menu de pop-up com todos os filtros, segmentações de dados, entre outros, que afetam este elemento visual. Os filtros no menu de pop-up são os mesmos filtros apresentados no painel **Filtros**.

![Captura de ecrã a mostrar uma lista de filtros com setas a apontar para a localização destes filtros no painel Filtros.](media/end-user-report-filter/power-bi-hover-visual-filter.png)

Eis os tipos de filtros que esta vista pode apresentar:

- Filtros básicos

- Segmentações

- Realce cruzado

- Filtragem cruzada

- Filtros avançados

- Filtros de itens principais

- Filtros de Data Relativa

- Segmentações de dados síncronas

- Filtros de Inclusão/Exclusão

- Filtros passados por um URL

No seguinte exemplo:

1. Podemos verificar que o gráfico de colunas foi alvo de filtragem cruzada.

1. **Incluído** indica que os filtros cruzados são para **Segment** (Segmento) e que estão incluídos três filtros.

1. Foi aplicada uma segmentação de dados a **Quarter** (Trimestre).

1. **Region** (Região) é um filtro aplicado a esta página de relatório e

1. **isVanArsdel** (éVanArsdel) e **Year** (Ano) são filtros aplicados a este elemento visual.

![Captura de ecrã a mostrar um relatório e dos seus filtros com a lista de filtros numerada para coincidir com a lista numerada apresentada acima.](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Pesquisar num filtro

Por vezes, um filtro pode ter uma grande lista de valores. Utilize a caixa de pesquisa para procurar e selecionar o valor pretendido.

![Captura de ecrã a mostrar o método de pesquisa num filtro.](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Apresentar detalhes de filtros

Para compreender os filtros, observe os valores e números disponíveis.  Veja os detalhes do filtro ao pairar o rato e selecionar a seta junto ao nome do mesmo.
  
![Captura de ecrã a mostrar um filtro que apresenta a região oeste selecionada.](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Alterar as seleções de filtros

Uma forma de procurar informações de dados é interagir com os filtros. Pode alterar seleções de filtros com a seta pendente junto ao nome do campo.  Conforme o filtro e o tipo de dados filtrados pelo Power BI, as suas opções irão variar entre seleções simples de uma lista e a identificação de intervalos de datas ou números. No filtro avançado apresentado abaixo, alterámos o filtro **Total Units YTD** (Total de Unidades do Ano até à Data) no gráfico treemap para um valor entre 2000 e 3000. Tenha em atenção que esta alteração remove o fabricante Pirum do gráfico treemap.
  
![Captura de ecrã a mostrar um relatório e dos seus filtros que apresenta a opção Fashions Direct selecionada.](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Para selecionar mais do que um valor de filtro de uma só vez, mantenha a tecla Ctrl premida. A maioria dos filtros suporta a seleção múltipla.

### <a name="reset-filter-to-default"></a>Repor os filtros para a predefinição

Se quiser anular todas as alterações efetuadas aos filtros, selecione **Repor para predefinição** na barra de menus superior.  Esta seleção reverte os filtros para o seu estado original, conforme definido pelo estruturador do relatório.

![Captura de ecrã a mostrar a opção Repor para predefinição.](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>Limpar um filtro

Se quiser definir apenas um filtro para **(Tudo)** , limpe o filtro ao selecionar o ícone de borracha ![Captura de ecrã do ícone Borracha.](media/end-user-report-filter/power-bi-eraser-icon.png) junto ao nome do filtro.
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Próximos passos

Saiba de que forma e por que motivo os [elementos visuais realizam filtragem cruzada e realce cruzado entre si numa página de relatório](end-user-interactions.md)