---
title: Fazer uma visita ao painel Filtros de relatórios
description: Como adicionar um filtro a um relatório no serviço Power BI para utilizadores empresariais
author: mihart
ms.reviewer: mihart
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 09/29/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fb283858d9e6fe016e382f4c662de6b66bce0258
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91600753"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Fazer uma visita do painel Filtros

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Este artigo analisa o painel **Filtros** de relatórios no serviço Power BI. Utilize os filtros para descobrir novas informações nos seus dados.

Existem muitas formas diferentes de filtrar dados no Power BI. Este artigo explica como utilizar o painel **Filtros**.  Também pode filtrar os restantes elementos visuais na página ao selecionar pontos de dados num elemento visual do relatório. Esta operação é designada por **filtragem cruzada** e **realce cruzado**. Para obter mais informações sobre a filtragem cruzada e o realce cruzado, veja [Filtros e realces em relatórios do Power BI](../create-reports/power-bi-reports-filters-and-highlighting.md).

![Captura de ecrã a mostrar um relatório no browser com uma seta a apontar para a opção Filtros.](media/end-user-report-filter/power-bi-reports.png)

## <a name="working-with-the-report-filters-pane"></a>Trabalhar com o painel Filtros

Quando um colega partilha um relatório consigo, verifique o painel **Filtros**. Por vezes, é encolhido ao longo da margem direita do relatório. Selecione-o para expandi-lo.

![Captura de ecrã a mostrar o relatório com o painel Filtros expandido.](media/end-user-report-filter/power-bi-expand-filters-pane.png)

O painel **Filtros** contém filtros que o *estruturador* do relatório adicionou ao mesmo. Os *utilizadores empresariais* podem interagir com os filtros existentes e guardar alterações, mas não podem adicionar novos filtros ao relatório. Por exemplo, na captura de ecrã acima, o estruturador adicionou três filtros de nível de página: O **Segmento é Todos**, o **Ano é 2014** e a **Região é Central**. Pode interagir com estes filtros e alterá-los, mas não pode adicionar um quarto filtro ao nível da página.

Alguns filtros aparecem sombreados, mas outros não. Se um filtro estiver sombreado, significa que foi aplicado um filtro e que alguns dados estão a ser excluídos. Por exemplo, o cartão de filtro **Region** (Região) está sombreado. Ao expandir o cartão, pode ver que apenas a opção **Central** está selecionada no menu pendente. Dado que Region (Região) se encontra no cabeçalho **Filtros nesta página**, todos os elementos visuais nesta página estão a excluir os dados das regiões **West** (Oeste) e **East** (Este).

![Captura de ecrã do filtro Region expandido e a mostrar a opção Central selecionada.](media/end-user-report-filter/power-bi-filter-region.png)

No serviço Power BI, todas as alterações efetuadas no painel **Filtros** são mantidas nos relatórios. O serviço aplica essas alterações na versão do relatório para dispositivos móveis. 

Para repor o painel **Filtros** para as predefinições do designer, selecione **Repor predefinição** na barra de menus superior.

![Captura de ecrã que mostra o ícone Repor predefinição.](media/end-user-report-filter/power-bi-reset-icon.png) 

> [!NOTE]
> Se não vir a opção **Repor para predefinição**, é possível que tenha sido desativada pelo *designer* do relatório. O *designer* pode também bloquear filtros específicos para que não os possa alterar.

## <a name="view-all-the-filters-for-a-report-page"></a>Ver todos os filtros de uma página de relatórios

O painel **Filtros** apresenta todos os filtros que o estruturador adicionou ao relatório. O painel **Filtros** também é a área em que pode ver informações sobre os filtros e interagir com os mesmos. Guarde as alterações que efetuar ou utilize **Repor predefinição** para reverter para as definições originais dos filtros.

Se tiver alterações que pretende guardar, também pode criar um marcador pessoal. Para obter mais informações, veja [O que são os marcadores?](end-user-bookmarks.md).

O painel **Filtros** apresenta e gere vários tipos de filtros de relatórios: relatório, página de relatório e elemento visual.

Neste exemplo, selecionámos um elemento visual com três filtros: **Manufacturer** (Fabricante), **Month** (Mês) e **Total units** (Total de unidades). A página de relatórios também tem filtros, listados no cabeçalho **Filtros nesta página**. Além disso, todo o relatório tem um filtro para **Date** (Data), listado no cabeçalho **Filtros em todas as páginas**.

![Captura de ecrã a mostrar um relatório com os seus filtros relacionados e uma visualização em destaque.](media/end-user-report-filter/power-bi-filter-pane.png)

Alguns filtros têm **(Todos)** junto aos mesmos. **(Todos)** significa que todos os valores são incluídos no filtro. Na captura de ecrã apresentada acima, **Segment (Todos)** (Segmento [Tudo]) indica que esta página de relatório inclui dados sobre todos os segmentos de produtos. 

Qualquer pessoa com permissões para ver este relatório pode interagir com estes filtros.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Ver apenas estes filtros aplicados a um elemento visual

Para examinar mais detalhadamente os filtros que afetam um elemento visual específico, paire o cursor sobre o elemento visual para revelar o ícone de filtro ![Captura de ecrã a mostrar o ícone Filtrar.](media/end-user-report-filter/power-bi-filter-icon.png). Selecione este ícone de filtro para ver um menu de pop-up com todos os filtros, segmentações de dados, entre outros, que afetam este elemento visual. Os filtros no pop-up incluem os mesmos filtros apresentados no painel **Filtros**, além da filtragem adicional que afeta o elemento visual selecionado.

![Captura de ecrã a mostrar uma lista de filtros com setas a apontar para a localização destes filtros no painel Filtros.](media/end-user-report-filter/power-bi-filters-hover.png)

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

Neste exemplo:
1. **Incluído** informa-nos que o elemento visual foi alvo de filtragem cruzada, o que significa que os Estados do Alabama e Texas foram selecionados num dos outros elementos visuais nesta página de relatório. Neste caso, é o elemento visual do mapa. A seleção desses dois Estados fez com que os dados fossem eliminados para os outros Estados e não fossem apresentados no gráfico de barras selecionado.  

1. O filtro **Date** é aplicado a todas as páginas neste relatório.

1. O filtro **Region é Central** e **Year é 2014** são aplicados a esta página do relatório.

4. **O Fabricante é VanArsdel, Natura, Aliqui ou Pirum** é um filtro aplicado a este elemento visual.


### <a name="search-in-a-filter"></a>Pesquisar num filtro

Por vezes, um filtro pode ter uma grande lista de valores. Utilize a caixa de pesquisa para procurar e selecionar o valor pretendido.

![Captura de ecrã a mostrar o método de pesquisa num filtro.](media/end-user-report-filter/power-bi-search-filter.png)

### <a name="display-filter-details"></a>Apresentar detalhes de filtros

Para compreender um determinado filtro, expanda-o e observe os valores e números disponíveis.  Para expandir o filtro, selecione a seta junto ao respetivo nome.
  
![Captura de ecrã a mostrar um filtro que apresenta a região oeste selecionada.](media/end-user-report-filter/power-bi-filters-expand.png)

### <a name="change-filter-selections"></a>Alterar as seleções de filtros

Uma forma de procurar informações de dados é interagir com os filtros. Pode alterar seleções de filtros com a seta pendente junto ao nome do campo.  Consoante o filtro e o tipo de dados filtrados pelo Power BI, as suas opções irão variar entre seleções simples de uma lista e a identificação de intervalos de datas ou números. No filtro avançado apresentado abaixo, alterámos o filtro **Total Units YTD** (Total de Unidades do Ano até à Data) no gráfico treemap para um valor entre 2000 e 3000. Tenha em atenção que esta alteração remove o fabricante Pirum do gráfico treemap.
  
![Captura de ecrã de um relatório e dos seus filtros que mostra o elemento visual do gráfico treemap selecionado.](media/end-user-report-filter/power-bi-treemap-filter.png)

> [!TIP]
> Para selecionar mais do que um valor de filtro de uma só vez, mantenha a tecla Ctrl premida. A maioria dos filtros suporta a seleção múltipla.

### <a name="reset-filter-to-default"></a>Repor os filtros para a predefinição

Se quiser anular todas as alterações efetuadas aos filtros, selecione **Repor para predefinição** na barra de menus superior.  Esta seleção reverte os filtros para o seu estado original, conforme definido pelo estruturador do relatório.

![Captura de ecrã a mostrar a opção Repor para predefinição.](media/end-user-report-filter/power-bi-reset-icon.png)

### <a name="clear-a-filter"></a>Limpar um filtro

Para repor um filtro para (Todos), desmarque-o ao selecionar o ícone de borracha junto ao nome do filtro.

![Captura de ecrã do ícone de Borracha.](media/end-user-report-filter/power-bi-erase.png)
  
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

## <a name="next-steps"></a>Passos seguintes

Saiba de que forma e por que motivo os [elementos visuais realizam filtragem cruzada e realce cruzado entre si numa página de relatório](end-user-interactions.md)
