---
title: Desagregação numa visualização no Power BI
description: Este documento demonstra como desagregar numa visualização no serviço Microsoft Power BI e no Power BI Desktop.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 02/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d622e6b461668d1972a78f6844bd269fb6596061
ms.sourcegitcommit: dcde910817720c05880ffe24755034f916c9b890
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2018
---
# <a name="drill-down-in-a-visualization-in-power-bi"></a>Desagregação numa visualização no Power BI
## <a name="drill-down-requires-a-hierarchy"></a>A desagregação requer uma hierarquia
Quando um visual tem uma hierarquia, pode desagregar para revelar detalhes adicionais. Por exemplo, pode ter uma visualização que observa a contagem de medalhas olímpicas por uma hierarquia constituída por desporto, disciplina e evento. Por predefinição, a visualização mostra a contagem de medalhas por desporto: ginástica, esqui, desportos aquáticos, etc. Mas, uma vez que tem uma hierarquia, selecionar um dos elementos visuais (como uma barra, linha ou bolha) mostraria uma imagem cada vez mais detalhada. Selecione o elemento **desportos aquáticos** para ver os dados sobre natação, mergulho e polo aquático.  Selecione o elemento **mergulho** para ver detalhes sobre eventos de prancha, plataforma e mergulho sincronizado.

Pode adicionar hierarquias a relatórios que lhe pertencem, mas não àqueles que foram partilhados consigo.
Não sabe que visualizações do Power BI contêm uma hierarquia?  Passe o cursor por uma visualização e, se vir estes controlos de desagregação nos cantos superiores, a sua visualização tem uma hierarquia.

![](media/power-bi-visualization-drill-down/power-bi-drill-icon4.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon3.png)
![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) ![](media/power-bi-visualization-drill-down/power-bi-drill-icon6.png)  

As datas são um tipo único de hierarquia. Quando adicionar um campo de data a uma visualização, o Power BI adiciona automaticamente uma hierarquia de tempo que contém ano, trimestre, mês e dia. Para obter mais informações, consulte [Hierarquias visuais e comportamento de desagregação](guided-learning/visualizations.yml?tutorial-step=18) ou veja o vídeo abaixo.


  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Para saber como criar hierarquias através do Power BI Desktop, veja o vídeo [Como criar e adicionar hierarquias](https://youtu.be/q8WDUAiTGeU)
> 
> 

## <a name="two-methods-to-drill-down"></a>Dois métodos de desagregação
Existem duas formas de desagregação (e agregação) na sua visualização.  Ambas estão descritas neste artigo. Ambos os métodos cumprem o mesmo objetivo, pelo que pode utilizar aquele de que gostar mais.

> [!NOTE]
> Para continuar, [abra o exemplo Análise de Retalho](sample-datasets.md) no serviço Power BI e crie um treemap que veja as **Unidades Totais Este Ano** (Valores) por **Território**, **Cidade**, **Código Postal**, e **Nome** (Grupo).  
> 
> 

## <a name="method-one-for-drill-down"></a>Primeiro Método de desagregação
Este método utiliza os ícones de desagregação que aparecem nos cantos superiores da própria visualização.

1. No Power BI, abra um relatório na [Vista de Leitura ou na Vista de Edição](service-reading-view-and-editing-view.md). A desagregação requer uma visualização com uma hierarquia. 
   
   Uma hierarquia é apresentada na animação abaixo.  A visualização tem uma hierarquia constituída por território, cidade, código postal e nome de cidade. Cada território tem uma ou mais cidades, cada cidade tem um ou mais códigos postais, etc. Por predefinição, a visualização mostra apenas os dados de território, uma vez que *Território* aparece em primeiro lugar na lista.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Para ativar a desagregação, selecione o ícone de seta no canto superior direito da visualização. Quando o ícone estiver escuro, a desagregação está ativada. Se não ativar a desagregação, selecionar um elemento visual (como uma barra ou uma bolha) irá fazer uma filtragem cruzada dos outros gráficos na página de relatórios.    
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-icon.png)
3. Para desagregar **um campo de cada vez**, selecione um dos elementos na sua visualização. Num gráfico de barras, isto significa clicar numa das barras. Num gráfico treemap, isto significa clicar numa das **folhas**. Repare que o título muda à medida que desagrega e regressa. Nesta animação, muda de "Total Units This Year by Territory" (Unidades Totais Este Ano por Território) para "Total Units This Year by Territory and City" (Unidades Totais Este Ano por Território e Cidade) e, em seguida, para "Total Units This Year by Territory, City and Postal Code" (Unidades Totais Este Ano por Território, Cidade e Código postal) para "Total Units This Year by Territory, City, Postal Code, and Name" (Unidades Totais Este Ano por Território, Cidade, Código postal e Nome). Para voltar a agregar, selecione o ícone **Agregar** ![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) no canto superior esquerdo da visualização, conforme mostrado abaixo.
   
   ![](media/power-bi-visualization-drill-down/drill.gif)
4. Para desagregar ***todos os campos de uma vez***, selecione a seta dupla no canto superior esquerdo da visualização.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillall.png)
5. Para voltar a agregar, selecione a seta para cima no canto superior esquerdo da visualização.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillup2.png)

## <a name="method-two-for-drill-down"></a>Segundo Método de desagregação
Este método utiliza o menu pendente **Explorar** da barra de menus superior do Power BI.

1. No Power BI, abra um relatório na [Vista de Leitura ou na Vista de Edição](service-reading-view-and-editing-view.md). A desagregação requer uma visualização com uma hierarquia. 
   
   Uma hierarquia é apresentada na imagem abaixo.  A visualização tem uma hierarquia constituída por território, cidade, código postal e nome de cidade. Cada território tem uma ou mais cidades, cada cidade tem um ou mais códigos postais, etc. Por predefinição, a visualização mostra apenas os dados de território, uma vez que *Território* aparece em primeiro lugar na lista.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Para ativar a desagregação, selecione uma visualização para torná-la ativa e, na barra de menus superior do Power BI, selecione **Explorar** > **Desagregar**. O ícone de desagregar no canto superior direito da visualização muda para um fundo preto. ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  
   
   ![](media/power-bi-visualization-drill-down/power-bi-explore2.png)
3. Depois da ativação, desagregue um campo de cada vez ao selecionar uma das folhas do treemap. Neste exemplo, o território intitulado **NC** está selecionado para ver o total de unidades vendidas este ano na Carolina do Norte por cidade.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drilldown-1.png)
4. Para desagregar todos os campos de uma vez, selecione **Explorar** > **Mostrar Nível Seguinte**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-show-next-level.png)
5. Para voltar a agregar, selecione **Explorar** > **Agregar**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-up2.png)

6. Para ver os dados em utilização para a criação do visual, selecione **Ver dados**. Os dados são apresentados num painel por baixo do visual. Este painel permanece visível à medida que continua a desagregar no visual. Para obter mais informações, consulte [Mostrar dados utilizados para criar o visual](service-reports-show-data.md).

## <a name="understanding-the-hierarchy-axis-and-hierarchy-group"></a>Compreender o eixo de hierarquia e o grupo de hierarquia
Pode pensar no eixo de hierarquia e no grupo de hierarquia como os mecanismos que pode utilizar para aumentar e diminuir a granularidade dos dados que pretende ver. Considera-se que têm uma hierarquia todos os dados que possam ser organizados em categorias e subcategorias. Isto, obviamente, inclui datas e horas.

Pode criar uma visualização no Power BI para ter uma hierarquia, ao selecionar um ou mais campos de dados para adicionar ao conjunto de dados **Eixo** ou ao conjunto de dados **Grupo**, com os dados que pretende examinar como campos de dados no conjunto de campos **Valores**. Saberá se os seus dados são hierárquicos se os ícones do Modo de Desagregação aparecerem nos cantos superiores esquerdo e direito da sua visualização. 

Essencialmente, é conveniente pensar em dois tipos de dados hierárquicos:
- Dados de data e hora: se tiver um campo com um tipo de dados DateTime, já tem dados hierárquicos. O Power BI cria automaticamente uma hierarquia para todos os campos de dados cujos valores podem ser analisados numa estrutura [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx). Apenas precisa de adicionar um campo DateTime ao conjunto de dados **Eixo** ou **Grupo**.
- Dados categóricos: se os seus dados tiverem origem em coleções que contêm subcoleções ou tiverem linhas de dados que partilham valores comuns, tem dados hierárquicos.

O Power BI permite-lhe expandir por um ou por todos os subconjuntos. Pode desagregar os seus dados para ver um único subconjunto em cada nível ou para ver todos os subconjuntos simultaneamente em cada nível. Por exemplo, pode desagregar para um ano específico ou ver todos os resultados para cada ano à medida que se desce na hierarquia. Por outro lado, pode agregar da mesma forma.

As seguintes secções descrevem a desagregação da vista mais elevada, da vista central e da vista mais baixa.

### <a name="hierarchical-data-and-time-data"></a>Dados hierárquicos e dados de hora
Para este exemplo, acompanhe o [exemplo de Análise de Revenda](sample-datasets.md) e crie uma visualização de gráfico de colunas empilhadas que apresente o **Mês** (Eixo) por **TotalSales** (Total de Vendas) (Valores).  

Apesar de o campo de dados Eixo ser **Mês**, este cria uma categoria **Ano** no conjunto de dados **Eixo**. Isto deve-se ao facto de o Power BI fornecer uma estrutura DateTime completa para todos os valores que lê. A parte superior da hierarquia mostra os dados do ano.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-datetime-1.png)

Com o modo Desagregar ativado, clique na barra no gráfico para descer um nível na hierarquia. Verá três barras para os dados dos trimestres disponíveis. Em seguida, nos ícones do canto superior esquerdo, selecione **Expandir tudo para um nível na hierarquia**. Em seguida, faça-o novamente para obter o nível mais baixo da hierarquia, que mostra resultados para cada mês.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-datetime-2.png)

Além da visualização, podemos ver a hierarquia refletida nos dados compostos para cada relatório. A seguinte tabela mostra os resultados de **Mostrar Dados** num relatório a desagregar de um único mês ou todos os meses. 

Tenha em atenção que os dados são os mesmos para relatórios trimestrais e anuais, mas após desagregar o nível de detalhe especificado para **Valores**, pode ver que o relatório único é mais específico e o relatório "todos os meses" tem mais dados.


|Modo Expandir|Year|Trimestre|Mês|Dia|
| ---|:---:|:---:|:---:|---|
|Único|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-year.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-quarter.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-month.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-day.png)|
|Tudo|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-year.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-quarter.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-month.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-day.png)|


### <a name="hierarchical-category-data"></a>Dados de categoria hierárquica
Os dados modelados a partir de coleções e subcoleções são hierárquicos. Um bom exemplo disto são os dados de localização. Pense numa tabela numa origem de dados cujas colunas são Country (País), State (Estado), City (Cidade) e Zip (Código Postal). Os dados que partilham o mesmo Country (País), State (Estado), City (Cidade) são hierárquicos.

Para este exemplo, acompanhe o [exemplo de Análise de Revenda](sample-datasets.md). Crie uma visualização de gráfico de coluna empilhada que abranja as **Total Units This Year** (Unidades Totais Este Ano) (Valores) por **Territory** (Território), **City** (Cidade), **PostalCode** (Código Postal) e **Name** (Nome) (Grupo).  

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-category-1.png)

Com o modo Desagregar ativado, nos ícones do canto superior esquerdo, selecione **Expandir tudo para um nível na hierarquia** três vezes.
Deverá estar no nível mais baixo da hierarquia, que mostra resultados para Territory (Território), City (Cidade) e Postal Code (Código Postal).

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-category-2.png)

Além da visualização, podemos ver a hierarquia refletida nos dados compostos para cada relatório. A seguinte tabela mostra os resultados de **Mostrar Dados** num relatório a desagregar para um único território ou todos os territórios. À medida que desagrega, pode ver como o relatório relativo a um território se torna mais específico e o relatório "todos os territórios" tem mais dados.


| Modo Expandir|Território|Cidade|Postal|Nome|
| ---|:---:|:---:|:---:|---|
|Único|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-territory.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city-postal.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Tudo|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-territory.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city-postal.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city-postal-name.png)|


## <a name="considerations-and-limitations"></a>Considerações e limitações
* Se adicionar um campo de data a uma visualização não criar uma hierarquia, pode ser que o campo "data" não esteja realmente guardado como uma data. Se for o proprietário do conjunto de dados, abra-o na vista de *Dados* no Power BI Desktop, selecione a coluna que contém a data e, no separador Modelação, altere o **Tipo de Dados** para **Data** ou **Data/Hora**. Se o relatório tiver sido partilhado consigo, contacte o proprietário para pedir a alteração.  
  
  ![](media/power-bi-visualization-drill-down/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Passos seguintes
[Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md)

[Relatórios do Power BI](service-reports.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

