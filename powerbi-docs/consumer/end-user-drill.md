---
title: Desagregar e agregar numa visualização
description: Este artigo mostra como efetuar a desagregação numa visualização no serviço Microsoft Power BI e no Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 6/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 29823a2f1ca7f1448df54282e0ce081310974eb3
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/16/2019
ms.locfileid: "67265131"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Modo de desagregação numa visualização no Power BI

Este artigo mostra como efetuar a desagregação numa visualização no serviço Microsoft Power BI e no Power BI Desktop. Os relatórios do Power BI permitem várias hierarquias de dados para lhe fornecer o máximo de informações sobre os seus dados. Com a desagregação e a agregação nos pontos de dados, pode explorar os detalhes mais aprofundados sobre os seus dados. Pode até mesmo utilizá-las nos dispositivos móveis mais pequenos.

## <a name="drill-requires-a-hierarchy"></a>A desagregação requer uma hierarquia

Quando uma visualização tem uma hierarquia, pode efetuar a desagregação para revelar detalhes adicionais. Por exemplo, pode ter uma visualização que observa a contagem de medalhas olímpicas por uma hierarquia constituída por desporto, disciplina e evento. Por predefinição, a visualização mostra a contagem de medalhas por desporto: ginástica, esqui, desportos aquáticos, etc. Mas, uma vez que existe uma hierarquia, a seleção de um dos elementos de visualização (como uma barra, uma linha ou uma bolha) mostraria uma imagem ainda mais detalhada. Selecione o elemento **desportos aquáticos** para ver os dados sobre natação, mergulho e polo aquático.  Selecione o elemento **mergulho** para ver detalhes sobre eventos de prancha, plataforma e mergulho sincronizado.

Pode adicionar hierarquias a relatórios que lhe pertencem, mas não àqueles relatórios que foram partilhados consigo.
Não sabe quais as visualizações do Power BI que contêm uma hierarquia? Passe o cursor sobre uma visualização. Se vir estes controlos de desagregação nos cantos superiores, significa que a visualização tem uma hierarquia.

![Captura de ecrã do ícone da desagregação um nível abaixo.](./media/end-user-drill/power-bi-drill-icon4.png)  ![Captura de ecrã do ícone de ativação e desativação da desagregação.](./media/end-user-drill/power-bi-drill-icon2.png)  ![Captura de ecrã do ícone de desagregação de todos os campos de uma só vez.](./media/end-user-drill/power-bi-drill-icon3.png)
![ícone da agregação](./media/end-user-drill/power-bi-drill-icon5.png) ![Captura de ecrã do ícone da expansão para baixo.](./media/end-user-drill/power-bi-drill-icon6.png)  

As datas são um tipo único de hierarquia. Quando adicionar um campo de data a uma visualização, o Power BI adiciona automaticamente uma hierarquia de tempo que contém ano, trimestre, mês e dia. Para obter mais informações, veja [Hierarquias das visualizações e comportamento da desagregação](../guided-learning/visualizations.yml?tutorial-step=18) ou veja o vídeo abaixo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Para saber como criar hierarquias através do Power BI Desktop, veja o vídeo [How to create and add hierarchies](https://youtu.be/q8WDUAiTGeU) (Como criar e adicionar hierarquias).

## <a name="prerequisites"></a>Pré-requisitos

1. No serviço Power BI ou no Power BI Desktop, a desagregação requer uma visualização com uma hierarquia.

1. Para acompanhar, abra o [exemplo de Análise de Revenda](../sample-datasets.md). Crie uma visualização do **Treemap** com o seguinte:

    | Conjunto de dados | Campo |
    | ---- | ----- |
    | Valor |Vendas<br>\|\_ Total de Unidades Deste Ano |
    | Grupo | Loja<br>\|\_ Território<br>\|\_ Cidade<br>\|\_ Código Postal<br>\|\_ Nome

    O treemap tem uma hierarquia constituída por território, cidade, código postal e nome de cidade. Cada território tem uma ou mais cidades, cada cidade tem um ou mais códigos postais, etc. Por predefinição, a visualização mostra apenas os dados do território, uma vez que o campo *Território* aparece em primeiro lugar na lista.

    ![Captura de ecrã do painel Visualizações com o campo Território em destaque.](media/end-user-drill/power-bi-hierarcy-list.png)

1. Aprender a utilizar diferentes ícones de desagregação em simultâneo pode ser uma tarefa confusa. Vamos filtrar o treemap para mostrar apenas dois dos territórios mais pequenos: **KY** e **TN**. Selecione o treemap e, em **Filtros de nível visual**, expanda **Território** e selecione **KY** e **TN**.

    ![Captura de ecrã do painel Visualizações com o filtro KY e TN.](./media/end-user-drill/power-bi-filter.png)

    Agora, apenas dois territórios são apresentados no treemap.

    ![Captura de ecrã do elemento visual com KY e TN em destaque.](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-use-the-drill-features"></a>Três formas de utilizar as funcionalidades de desagregação

Existem várias opções para aceder às funcionalidades de agregação, desagregação e expansão para visualizações com hierarquias. Este artigo mostra como utilizar a primeira opção abaixo. Depois de aprender as noções básicas de desagregação e expansão, saberá como utilizar estas funcionalidades. Todas têm o mesmo objetivo. Experimente-as e escolha a sua preferida.

- Coloque o cursor sobre uma visualização para ver e utilizar os ícones.  

    ![Captura de ecrã do exemplo de passagem do cursor.](./media/end-user-drill/power-bi-hover.png)

- Faça clique com o botão direito do rato numa visualização para ver e utilizar o menu.

    ![Captura de ecrã do exemplo de clique no botão direito do rato.](./media/end-user-drill/power-bi-drill-menu.png)

- Na barra de menus do Power BI, selecione o botão **Explorar**.

   ![Captura de ecrã da seleção da opção Explorar a mostrar os ícones e as opções da desagregação.](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>Caminhos de desagregação

### <a name="drill-down"></a>Desagregar

Existem várias formas de explorar a visualização. A **Desagregação** fá-lo avançar para o próximo nível na hierarquia. Se estiver no nível **Território**, poderá efetuar a desagregação até ao nível Cidade e, em seguida, até ao nível Código Postal e, finalmente, até ao nível Nome. Cada passo do caminho apresenta novas informações.

![Diagrama a mostrar o caminho da desagregação](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Expandir

**Expandir** adiciona outro nível de hierarquia à vista atual. Por isso, se estiver no nível **Território**, poderá expandir e adicionar detalhes da cidade, código postal e nome ao treemap. Cada passo no caminho apresenta as mesmas informações e adiciona um nível de informações novas.

![Diagrama a mostrar o caminho da expansão](./media/end-user-drill/power-bi-expand-path.png)

Também pode optar pela desagregação ou expansão de um campo de cada vez ou de todos os campos de uma só vez.

## <a name="drill-down-all-fields-at-once"></a>Desagregar todos os campos de uma só vez

1. Comece pelo nível superior do treemap que apresenta dados para KY e TN. Alargue o treemap ao selecionar uma das alças e ao arrastar para a direita.

    ![Captura de ecrã do elemento visual do treemap a mostrar KY e TN](./media/end-user-drill/power-bi-drill-down.png)

1. Para desagregar *todos os campos de uma só vez*, selecione a seta dupla no canto superior esquerdo da visualização ![ícone de desagregação duplo](./media/end-user-drill/power-bi-drill-icon3.png). O treemap mostra agora dados de cidade para Kentucky e Tennessee.

    ![Captura de ecrã do elemento visual do treemap a mostrar a desagregação das cidades.](./media/end-user-drill/power-bi-drill-down1.png)

1. Efetue mais uma vez a desagregação até ao nível do código postal da hierarquia.

    ![Captura de ecrã do elemento visual do treemap a mostrar a desagregação dos códigos postais.](./media/end-user-drill/power-bi-drill-down2.png)

1. Para voltar a agregar, selecione a seta para cima no canto superior esquerdo da visualização ![Captura de ecrã do ícone da agregação um nível acima.](./media/end-user-drill/power-bi-drill-icon5.png).

## <a name="drill-down-one-field-at-a-time"></a>Desagregar um campo de cada vez

Este método utiliza o ícone de desagregação apresentado no canto superior direito da própria visualização.

1. Selecione o ícone de desagregação para a ativar ![Captura de ecrã do ícone de desagregação ativada.](./media/end-user-drill/power-bi-drill-icon2.png).

    Agora tem a opção de desagregar **um campo de cada vez**.

    ![Captura de ecrã do elemento visual com seta a apontar para o ícone de desagregação ativada.](media/end-user-drill/power-bi-drill-icon-new.png)

    Se não ativar a desagregação, a seleção de um elemento de visualização (como uma barra, bolha ou folha) não procederá à desagregação. Em vez disso, será efetuada a filtragem cruzada dos outros gráficos na página do relatório.

1. Selecione a folha para **TN**. O treemap apresenta agora todas as cidades no Tennessee que têm uma loja.

    ![Captura de ecrã do treemap a mostrar apenas os dados de TN.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Neste momento, pode:

    1. Continuar a desagregação no Tennessee.

    1. Efetuar uma desagregação numa determinada cidade do Tennessee.

    1. Em vez disso, expanda (veja abaixo **Expandir todos os campos de uma só vez**).

    Continuemos a desagregar um campo de cada vez.  Selecione **Knoxville, TN**. O treemap mostra agora o código postal da sua loja em Knoxville.

    ![Captura de ecrã do treemap a mostrar o código postal 37919.](media/end-user-drill/power-bi-drill-down-one2.png)

    Repare que o título muda à medida que desagrega e regressa.

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandir tudo e expandir um campo de cada vez

Um treemap a mostrar apenas um código postal não é algo informativo.  Por isso, vamos expandir para baixo um nível na hierarquia.  

1. Com o treemap ativo, selecione o ícone *Expandir para baixo* ![Captura de ecrã do ícone Expandir para baixo.](./media/end-user-drill/power-bi-drill-icon6.png). O treemap mostra agora dois níveis da nossa hierarquia: código postal e nome da loja.

    ![Captura de ecrã do treemap a mostrar o código postal e o nome da loja](./media/end-user-drill/power-bi-expand1.png)

1. Para ver os quatro níveis de dados da hierarquia do Tennessee, selecione a seta de agregação até chegar ao segundo nível do treemap, **Total de unidades deste ano por território e por cidade**.

    ![Captura de ecrã do treemap a mostrar todos os dados de TN.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Confirme que a desagregação ainda está ativada, ![Captura de ecrã do ícone da desagregação ativado.](./media/end-user-drill/power-bi-drill-icon2.png) e selecione o ícone *expandir para baixo* ![Captura de ecrã do ícone Expandir para baixo.](./media/end-user-drill/power-bi-drill-icon6.png). O treemap mostra agora alguns detalhes adicionais. Em vez de apresentar apenas a cidade e o estado, agora também apresenta o código postal.

    ![Captura de ecrã do elemento visual a mostrar a cidade, o estado e o código postal.](./media/end-user-drill/power-bi-expand-one3.png)

1. Selecione novamente o ícone *Expandir para baixo* para apresentar os quatro níveis de detalhe da hierarquia do Tennessee no treemap. Coloque o cursor sobre uma folha para ver ainda mais detalhes.

    ![Captura de ecrã do treemap a mostrar uma sugestão de ferramenta com dados específicos da folha.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>A exploração filtra outros elementos visuais

Ao trabalhar no Modo de desagregação, pode decidir de que forma é que a desagregação e a expansão afetam outras visualizações na página.

Por predefinição, a desagregação não filtrará outros elementos visuais num relatório. Esta funcionalidade pode ser ativada no Power BI Desktop e no serviço Power BI.

1. No Power BI Desktop, selecione o separador **Formato** e a caixa de verificação **Desagregar filtra outros elementos visuais**.

    ![Captura de ecrã a mostrar a definição Desagregar filtra outros elementos visuais no Power BI Desktop](./media/end-user-drill/power-bi-drill-filters-desktop.png)

1. Agora, quando desagregar, agregar ou expandir numa visualização com uma hierarquia, esta ação filtrará os outros elementos visuais na página.

    ![Captura de ecrã do resultado no Desktop.](./media/end-user-drill/power-bi-drill-filters.png)

    ![Captura de ecrã de outro resultado no Desktop.](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> Para ativar esta opção no serviço Power BI, selecione **Interações visuais** > **Desagregar filtra outros elementos visuais** na barra de menus superior.
>
> ![Captura de ecrã a mostrar a definição Desagregar filtra outros elementos visuais no serviço Power BI](./media/end-user-drill/power-bi-drill-filters-service.png)

## <a name="learn-about-the-hierarchy-axis-and-hierarchy-group"></a>Saiba mais sobre o eixo da hierarquia e o grupo da hierarquia

Pode pensar no eixo de hierarquia e no grupo de hierarquia como os mecanismos que pode utilizar para aumentar e diminuir a granularidade dos dados que pretende ver. Considera-se que têm uma hierarquia todos os dados, incluindo datas e horas, que possam ser organizados em categorias e subcategorias.

Pode criar uma visualização no Power BI para ter uma hierarquia ao selecionar um ou mais campos de dados para adicionar ao conjunto de dados **Eixo** ou ao conjunto de dados **Grupo**. Em seguida, adicione os dados que quer examinar como campos de dados no conjunto **Valores**. Saberá se os dados têm uma hierarquia se os ícones do *Modo de desagregação* aparecerem nos cantos superiores esquerdo e direito da visualização.

Essencialmente, é conveniente pensar em dois tipos de dados hierárquicos:

- Dados de data e hora: se tiver um campo com um tipo de dados DateTime, já tem dados hierárquicos. O Power BI cria automaticamente uma hierarquia para qualquer campo de dados. Pode analisar os valores numa estrutura [DataHora](https://msdn.microsoft.com/library/system.datetime.aspx). Apenas precisa de adicionar um campo DateTime ao conjunto de dados **Eixo** ou **Grupo**.

- Dados categóricos – se os dados do Power BI tiverem origem em coleções que contenham subcoleções ou se tiverem linhas de dados que partilhem valores comuns, estará perante dados com hierarquia.

O Power BI permite-lhe expandir por um ou por todos os subconjuntos. Pode desagregar os dados para ver um único subconjunto em cada nível ou para ver todos os subconjuntos simultaneamente em cada nível. Por exemplo, pode desagregar para um ano específico ou ver todos os resultados para cada ano à medida que se desce na hierarquia.

Também pode efetuar a agregação da mesma forma.

As seguintes secções descrevem a desagregação da vista mais elevada, da vista central e da vista mais baixa.

### <a name="hierarchical-data-and-time-data"></a>Dados hierárquicos e dados de hora

Neste exemplo:

1. Acompanhe o [exemplo de Análise de Revenda](../sample-datasets.md) e crie uma visualização de gráfico com colunas empilhadas com o seguinte:

    | Conjunto de dados | Campo |
    | ---- | ----- |
    | Eixo | Hora<br>\|\_ Mês |
    | Valores | Vendas<br>\|\_ TotalDeVendas |

    Apesar de o campo de dados Eixo ser **Mês**, este cria uma categoria **Ano** no conjunto de dados **Eixo**. Tal deve-se ao facto de o Power BI fornecer uma estrutura DataHora completa para todos os valores que lê. A parte superior da hierarquia mostra os dados do ano.

    ![Captura de ecrã da barra simples a mostrar os dados agrupados por ano](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

1. Com o modo de desagregação ativado, selecione a barra no gráfico que deverá descer um nível na hierarquia. Verá três barras para os dados dos trimestres disponíveis.

1. Em seguida, nos ícones do canto superior esquerdo, selecione **Expandir tudo para um nível abaixo na hierarquia**.

1. Faça-o novamente para aceder ao nível mais baixo da hierarquia que mostra os resultados referentes a cada mês.

    ![Captura de ecrã do gráfico de barras para ver a barra referente a cada mês](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

Além da visualização, podemos ver a hierarquia refletida nos dados compostos para cada relatório. Selecione o botão das reticências (...) no canto superior direito e, em seguida, selecione **Mostrar Dados**. A seguinte tabela mostra os resultados da desagregação de um único mês ou de todos os meses:

|Modo Expandir|Year|Trimestre|Mês|Dia|
| --- |:---:|:---:|:---:|---|
|Único|![ano único](./media/end-user-drill/power-bi-hierarchical-year.png)|![trimestre único](media/end-user-drill/power-bi-hierarchical-quarter.png)|![mês único](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![dia único](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Tudo|![todos os anos](./media/end-user-drill/power-bi-hierarchical-year.png)|![todos os trimestres](media/end-user-drill/power-bi-hierarchical-quarter.png)|![todos os meses](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![todos os dias](media/end-user-drill/power-bi-hierarchical-all-day.png)|

Repare que os dados são os mesmos para os relatórios **Trimestrais** e **Anuais**. Depois de efetuar a desagregação até ao nível de detalhe especificado em **Valores**, pode ver que o relatório único é mais específico e o relatório de “todos os meses” inclui mais dados.

### <a name="hierarchical-category-data"></a>Dados de categoria hierárquica

Os dados modelados a partir de coleções e subcoleções são hierárquicos.

Um bom exemplo disto são os dados de localização. Pense numa tabela numa origem de dados cujas colunas são Country (País), State (Estado), City (Cidade) e Zip (Código Postal). Os dados que partilham o mesmo Country (País), State (Estado), City (Cidade) são hierárquicos.

Neste exemplo:

1. Acompanhe o [exemplo de Análise de Revenda](../sample-datasets.md). Crie uma visualização de gráficos de colunas empilhadas com o seguinte:

    | Conjunto de dados | Campo |
    | ---- | ----- |
    | Valor |Vendas<br>\|\_ Total de Unidades Deste Ano |
    | Eixo | Loja<br>\|\_ Território<br>\|\_ Cidade – poderá ter de arrastar a cidade do conjunto de dados **Legenda** para o conjunto de dados **Eixo**.<br>\|\_ Código Postal<br>\|\_ Nome |

    ![Captura de ecrã do gráfico de barras a mostrar o total de unidades deste ano por território.](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

1. Com o modo de desagregação ativado, nos ícones do canto superior esquerdo, selecione três vezes **Expandir tudo para um nível abaixo na hierarquia**.

    Deverá estar no nível mais baixo da hierarquia que mostra os resultados referentes ao Território, Cidade e Código Postal.

    ![Captura de ecrã do gráfico de barras a mostrar o nível mais baixo da hierarquia e a maioria dos detalhes.](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

Além da visualização, podemos ver a hierarquia refletida nos dados compostos para cada relatório. Selecione o botão das reticências (...) no canto superior direito e, em seguida, selecione **Mostrar Dados**. A seguinte tabela mostra os resultados da desagregação de um único território ou de todos os territórios.

| Modo Expandir|Território|Cidade|Postal|Nome|
| ---|:---:|:---:|:---:|---|
|Único|![território único](./media/end-user-drill/power-bi-hierarchical-territory.png)|![cidade única](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![código postal único](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![nome único](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Tudo|![todos os territórios](./media/end-user-drill/power-bi-hierarchical-territory.png)|![todas as cidades](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![todos os códigos postais](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![todos os nomes](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|

 Ao longo da desagregação, pode ver como um relatório **único** se torna mais específico e o relatório sobre **todos** os territórios inclui mais dados.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Se ao adicionar um campo de data a uma visualização não criar uma hierarquia, o campo da data poderá não estar realmente guardado como uma data. Se for o proprietário do conjunto de dados:

1. Abra a vista *Dados* no Power BI Desktop.

1. Selecione a coluna com a data.

1. No separador **Modelo**, altere o **Tipo de Dados** para **Data** ou **Data/Hora**.

![Captura de ecrã da vista para selecionar os dados e, no canto superior direito, pode ver o tipo de data.](media/end-user-drill/power-bi-change-data-type2.png)

Se o relatório tiver sido partilhado consigo, contacte o proprietário para pedir a alteração.

## <a name="next-steps"></a>Passos seguintes

[Visualizações nos relatórios do Power BI](../visuals/power-bi-report-visualizations.md)

[Relatórios do Power BI](end-user-reports.md)

[Power BI - Conceitos Básicos](end-user-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
