---
title: O editor de relatórios... Faça uma visita
description: O editor de relatórios no serviço Power BI e o editor de relatórios no Power BI Desktop são semelhantes.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 66e40462081ee2f1156840d137d4c67ad0eb7b45
ms.sourcegitcommit: b717118c44499c8fd8f57534a275f2f78aacc0f1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2019
ms.locfileid: "55971700"
---
# <a name="tour-the-report-editor-in-power-bi"></a>Apresentação do editor de relatórios no Power BI

O *editor de relatórios* no serviço Power BI e o editor de relatórios no Power BI Desktop são semelhantes. Normalmente, começa por criar relatórios no Power BI Desktop. Em seguida, publica-os no serviço Power BI, onde pode continuar a modificá-los. É também no serviço Power BI que cria os dashboards com base nos seus relatórios.

Depois de criar os seus dashboards e relatórios, distribui-os aos consumidores dos relatórios. Dependendo da forma como os partilha, os utilizadores finais poderão interagir com os mesmos na Vista de leitura no serviço Power BI, mas não podem editá-los. Leia mais sobre [o que os consumidores de relatórios podem fazer no serviço Power BI](consumer/end-user-reading-view.md). 

Este vídeo mostra o editor de relatórios no Power BI Desktop. Este artigo mostra o editor de relatórios no serviço Power BI. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

No serviço Power BI, o editor de relatórios está disponível apenas na Vista de Edição. Para abrir um relatório na Vista de Edição, tem de ser o respetivo proprietário ou criador, ou ser um contribuidor da área de trabalho da aplicação que aloja o mesmo.

O editor de relatórios do Power BI tem três secções:  

1. Filtros **Campos**, **Visualizações** e **Filtros**
2. barras de navegação superiores    
3. tela de relatórios     

![As secções do editor de relatórios](media/service-the-report-editor-take-a-tour/power-bi-report-canvas.png)

## <a name="1-the-report-editor-panes"></a>1. Os painéis do editor de relatórios
![Editor de relatórios do Power BI](media/service-the-report-editor-take-a-tour/power-bi-report-panes.png)

Quando abre um relatório pela primeira vez, são apresentados três painéis: Visualizações, Filtros e Campos. Os painéis no lado esquerdo, Visualizações e Filtros, controlam a aparência das visualizações: tipo, cores, filtragem, formato.  E o painel no lado direito, Campos, gere os dados subjacentes utilizados nas visualizações. 

O conteúdo exibido no editor de relatórios varia de acordo com as seleções feitas na tela de relatório.  Por exemplo, quando seleciona um elemento visual individual:

|  |  |
| --- | --- |
| ![Painéis do editor de relatórios](media/service-the-report-editor-take-a-tour/power-bi-panes.png) |<ul><li>a parte superior do painel Visualização identifica o tipo de visual em utilização: neste exemplo, um gráfico de colunas em Cluster.<br><br></li> <li>A parte inferior do painel Visualização (poderá ter de deslocar-se para baixo) mostra os campos utilizados no visual. Este gráfico utiliza a variância de FiscalMonth, DistrictManager e Vendas Totais. <br><br></li><li>O painel Filtros (poderá ter de deslocar-se para baixo) mostra os filtros que foram aplicados. <br><br></li><li>O painel Campos mostra as tabelas disponíveis e, se expandir o nome de uma tabela, os campos que constituem essa tabela. O tipo de letra amarelo mostra que pelo menos um campo dessa tabela está a ser utilizado na visualização.<br><br></li><li>![ícone de rolo de pintura](media/service-the-report-editor-take-a-tour/power-bi-paint-roller-icon.png) Para mostrar o painel de formatação, para a visualização selecionada, selecione o ícone do rolo de pintura.<br><br></li><li>![ícone de lupa](media/service-the-report-editor-take-a-tour/power-bi-magnifying-icon.png) Para apresentar o painel Análise, selecione o ícone de lupa.</ul> |

## <a name="the-visualizations-pane"></a>O painel Visualizações
![parte superior do painel Visualização](media/service-the-report-editor-take-a-tour/selectviz.png)

Este local é onde seleciona um tipo de visualização. As imagens pequenas chamam-se *modelos*. Na imagem acima, o Gráfico de barras agrupadas está selecionado. Se não selecionar primeiro um tipo de visualização, mas começar a criar uma visualização ao selecionar campos, o Power BI irá selecionar o tipo de visualização. Pode manter a seleção do Power BI ou alterar o tipo ao selecionar um modelo diferente. Pode mudar as vezes que precisar até encontrar o tipo de visualização que melhor representa os seus dados.

### <a name="manage-the-fields-in-your-visual"></a>Gerir os campos no seu elemento visual
![parte central do painel Visualização](media/service-the-report-editor-take-a-tour/power-bi-field-list.png)

Os registos (por vezes denominados *wells*) mostrados neste painel variam consoante o tipo de visualização que selecionou.  Por exemplo, se tiver selecionado um gráfico de barras, verá registos para: Valores, Eixo e Legenda. Quando seleciona um campo, ou o arrasta para a tela, o Power BI adiciona esse campo a um dos registos.  Também pode arrastar campos da lista Campos diretamente para os registos.  Alguns registos são limitados a determinados tipos de dados.  Por exemplo, **Valores** não aceita campos não numéricos. Por isso, se arrastar um campo **employeename** para o registo **Valores**, o Power BI altera-o para **contagem de employeename**.

### <a name="remove-a-field"></a>Remover um campo
Para remover um campo da visualização, selecione o **X** à direita do nome do campo.

![Remover Tipo de Loja da Legenda](media/service-the-report-editor-take-a-tour/deletefield.png)

Para obter mais informações, consulte [Adicionar visualizações a um relatório do Power BI](visuals/power-bi-report-add-visualizations-i.md)

### <a name="format-your-visuals"></a>Formatar os elementos visuais
Selecione o ícone do rolo de pintura para apresentar o painel Formatar. As opções disponíveis dependem do tipo de visualização selecionada.

![Painel Formatação no editor de relatórios](media/service-the-report-editor-take-a-tour/power-bi-formatting.png)

As possibilidades de formatação são praticamente infinitas.  Para saber mais, explore de forma autónoma ou consulte estes artigos:

* [Personalizar o título, fundo e legenda da visualização](visuals/power-bi-visualization-customize-title-background-and-legend.md)
* [Formatação de cor](visuals/service-getting-started-with-color-formatting-and-axis-properties.md)
* [Personalizar as propriedades dos eixos X e Y](visuals/power-bi-visualization-customize-x-axis-and-y-axis.md)

### <a name="add-analytics-to-your-visualizations"></a>Adicionar análises às suas visualizações
Selecione o ícone da lupa para mostrar o painel Análise. As opções disponíveis dependem do tipo de visualização selecionada.

![Painel Análise no editor de relatórios](media/service-the-report-editor-take-a-tour/power-bi-analytics.png)    
Com o painel Análise no serviço Power BI, pode adicionar linhas de referência dinâmicas a visualizações e dar foco a tendências ou informações importantes. Para saber mais, veja o [painel Análise no serviço Power BI](service-analytics-pane.md) ou o [painel Análise no Power BI Desktop](desktop-analytics-pane.md).

- - -
## <a name="the-filters-pane"></a>O painel Filtros
Utilize o painel Filtros para ver, definir e modificar os filtros persistentes dos relatórios ao nível da página, do relatório, da pormenorização e ao nível visual. Sim, pode efetuar uma filtragem ad-hoc nas páginas e nos elementos visuais do relatório ao selecionar os elementos visuais ou ao utilizar as ferramentas como segmentações de dados. Porém, ao utilizar o painel Filtros, o estado dos filtros é guardado com o relatório. 

O painel Filtros possui uma outra funcionalidade poderosa: a capacidade de filtrar através de um campo ***que já não está a ser utilizado num dos elementos visuais do relatório***. Passo a explicar. Quando cria uma página de relatório, o Power BI adiciona automaticamente todos os campos que utiliza nas visualizações à área de filtros do Nível visual do painel Filtros.  No entanto, se pretender definir um filtro visual, de página, de pormenorização ou de relatório através de um campo que já não é utilizado numa visualização, basta arrastar o campo para um dos grupos Filtros.   

![Painel Filtros](media/service-the-report-editor-take-a-tour/power-bi-formatting-pane.png)

Para obter mais informações, consulte [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Uma nova experiência de filtros está atualmente em pré-visualização. Nos novos filtros, pode formatá-los para que se pareçam com o relatório propriamente dito. Também pode bloquear filtros ou ocultá-los dos consumidores dos seus relatórios. 

![Nova experiência de filtro](media/service-the-report-editor-take-a-tour/power-bi-filter-reading.png)

Leia mais sobre [a nova experiência de filtros](power-bi-report-filter-preview.md).

- - -
## <a name="the-fields-pane"></a>O painel Campos
O painel Campos mostra as tabelas e os campos que existem nos seus dados e estão disponíveis para que utilize e crie visualizações.

|  |  |
| --- | --- |
| ![o painel Campos](media/service-the-report-editor-take-a-tour/reportfields.png) |<ul><li>Arraste um campo para a página para iniciar uma nova visualização.  Também pode arrastar um campo para uma visualização existente para adicionar o campo a essa visualização.<br><br></li> <li>Quando adicionar uma marca de verificação junto a um campo, o Power BI adiciona esse campo à visualização ativa (ou nova). Também decide em que registo colocar esse campo.  Por exemplo, o campo deve ser utilizado como legenda, eixo ou valor? O Power BI faz uma suposição e, se for necessário, pode movê-lo desse registo para outro. <br><br></li><li>De qualquer das formas, cada campo selecionado é adicionado ao painel Visualizações no editor de relatórios.</li></ul> |

**NOTA**: se estiver a utilizar o Power BI Desktop, também terá opções para mostrar/ocultar campos, adicionar cálculos, etc.

### <a name="what-do-the-field-icons-mean"></a>O que significam os ícones de campo?
**Agregados ∑** Um agregado é um valor numérico cuja soma ou média, por exemplo, será calculada. Os agregados são importados com os dados (definidos no modelo de dados no qual se baseia o seu relatório).
Para obter mais informações, consulte [Agregados em relatórios do Power BI](service-aggregates.md).

![ícone de calculadora](media/service-the-report-editor-take-a-tour/pbi_calculated_icon.png) **Medidas calculadas (também denominadas campos calculados)**  
Cada campo calculado tem a sua própria fórmula calculada. Não é possível alterar o cálculo; por exemplo, se for uma soma, só poderá ser uma soma. Para obter mais informações, consulte [Noções básicas sobre medidas](desktop-measures.md)

![ícone de Campos exclusivos](media/service-the-report-editor-take-a-tour/icon.png) **Campos exclusivos**  
Os campos com este ícone foram importados do Excel e estão definidos para mostrar todos os valores, mesmo se tiverem duplicados. Por exemplo, os seus dados podem ter dois registos para pessoas chamadas "Guilherme Sarmento" e cada um deles será tratado como exclusivo – estes não serão somados.  

**![ícone de Campos geográficos](media/service-the-report-editor-take-a-tour/pbi_geo_icon.png) Campos geográficos**  
Os campos de localização podem ser utilizados para criar visualizações de mapas. 

**![ícone de Hierarquia](media/service-the-report-editor-take-a-tour/power-bi-hierarchy-icon.png) Hierarquia**  
Selecione a seta para mostrar os campos que constituem a hierarquia. 

## <a name="2-the-top-navigation-bar"></a>2. A barra de navegação superior
As ações disponíveis na barra de navegação superior são bastantes, e estão sempre a ser adicionadas novas ações. Para obter informações sobre uma ação específica, utilize a Caixa de pesquisa ou o Índice da Documentação do Power BI.

## <a name="3-the-report-canvas"></a>3. A tela de relatórios
A tela de relatórios é onde o seu trabalho é apresentado. Quando utiliza os painéis Campos, Filtros e Visualizações para criar visuais, estes são criados e apresentados na sua tela de relatórios. Cada separador na parte inferior da tela representa uma página no relatório. Selecione um separador para abrir essa página. 

## <a name="next-steps"></a>Próximos passos
[Criar um relatório](service-report-create-new.md)

Mais informações sobre relatórios no [serviço Power BI](service-report-create-new.md), no [Power BI Desktop](desktop-report-view.md) e nas [aplicações móveis do Power BI](consumer/mobile/mobile-apps-view-phone-report.md).

[Conceitos básicos para designers do Power BI](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

