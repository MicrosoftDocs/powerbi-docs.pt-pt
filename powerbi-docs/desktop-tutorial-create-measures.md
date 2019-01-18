---
title: 'Tutorial: Criar as suas próprias medidas no Power BI Desktop'
description: 'Tutorial: Criar as suas próprias medidas no Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: ba9cc81c966ebadb2aaff8c339b8a151aef7b6fd
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54287607"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Tutorial: Criar as suas próprias medidas no Power BI Desktop
Pode criar algumas das mais poderosas soluções de análise de dados no Power BI Desktop com a utilização de medidas. As medidas ajudam-no a executar cálculos sobre os dados à medida que interage com os relatórios. Este tutorial serve de guia para que compreenda as medidas e crie algumas das suas medidas básicas no Power BI Desktop.

### <a name="prerequisites"></a>Pré-requisitos
- Este tutorial destina-se aos utilizadores do Power BI já familiarizados com o Power BI Desktop para criar modelos mais avançados. Já deve estar familiarizado com as funcionalidades Obter Dados e Editor de Consultas para importar dados, trabalhar com várias tabelas relacionadas e adicionar campos à tela Relatório. Se ainda não estiver familiarizado com o Power BI Desktop, não deixe de conferir a [Introdução ao Power BI Desktop](desktop-getting-started.md).
  
- Transfira o ficheiro [Exemplo de Vendas da Contoso para o Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), que inclui os dados de vendas online da empresa fictícia, Contoso, Inc. Estes dados foram importados de uma base de dados; portanto, não conseguirá ligar-se à origem de dados nem visualizá-la no Editor de Consultas. Extraia o ficheiro para o seu computador e, em seguida, abra-o no Power BI Desktop.

## <a name="understand-measures"></a>Compreender as medidas

As medidas são frequentemente criadas de forma automática. No ficheiro Exemplo de Vendas da Contoso, selecione a caixa de verificação junto ao campo **SalesAmount** na tabela **Vendas** na secção Campos ou arraste **SalesAmount** para a tela de relatórios. É apresentada uma visualização do novo gráfico de colunas, que mostra a soma total de todos os valores na coluna SalesAmount da tabela Vendas.

![Gráfico SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Qualquer campo que apareça na secção Campos com um ícone de sigma ![ícone de sigma](media/desktop-tutorial-create-measures/meastut_sigma.png) é numérico e os seus valores podem ser agregados. Em vez de mostrar uma tabela com a totalidade dos dois milhões de linhas de valores de SalesAmount, o Power BI Desktop detetou um tipo de dados numérico e criou e calculou automaticamente uma medida para agregar os dados. Soma é a agregação predefinida para um tipo de dados numérico, mas pode facilmente aplicar diferentes agregações, como média ou contagem. Compreender o funcionamento das agregações é fundamental para compreender as medidas, pois cada medida executa algum tipo de agregação. 

Para alterar a agregação do gráfico para a média, na área **Valor** do painel Visualizações, clique na seta para baixo junto a **SalesAmount** e selecione **Média**. A visualização muda para uma média de todos os valores de vendas no campo SalesAmount.

![Gráfico de média de SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Pode alterar o tipo de agregação consoante o resultado desejado, mas nem todos os tipos de agregação são aplicáveis a todos os tipos de dados numéricos. Por exemplo, para o campo SalesAmount, as funções Soma e Média fazem sentido. Minimum e Maximum também são importantes. No entanto, Contagem não faz muito sentido para o campo SalesAmount, porque embora os valores sejam numéricos, na verdade, referem-se à moeda.

Os valores calculados com medidas mudam de acordo com as suas interações com o relatório. Por exemplo, se arrastar o campo **RegionCountryName** da tabela **Geografia** para o gráfico, são apresentadas as médias dos valores de vendas para cada país.

![SaleAmount por País](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quando o resultado de uma medida é alterado devido a uma interação com o relatório, afeta o *contexto* da medida. Sempre que interage com as visualizações de relatórios, altera o contexto no qual uma medida calcula e apresenta os resultados.

## <a name="create-and-use-your-own-measures"></a>Criar e utilizar as suas próprias medidas

Na maioria dos casos, o Power BI calcula e devolve automaticamente os valores de acordo com os tipos de campos e agregações que escolher. Mas, em alguns casos, poderá querer criar as suas próprias medidas para realizar cálculos mais complexos e exclusivos. Com o Power BI Desktop, pode criar as suas próprias medidas com a linguagem das fórmulas DAX (Data Analysis Expressions). 

As fórmulas DAX utilizam muitos operadores, funções e sintaxe também utilizados pelas fórmulas do Excel. No entanto, as funções DAX foram concebidas para trabalhar com dados relacionais e realizar cálculos mais dinâmicos à medida que interage com os relatórios. Existem mais de 200 funções DAX que fazem tudo, desde agregações simples, como soma e média, até funções de estatística e de filtragem mais complexas. Existem muitos recursos para ajudá-lo a saber mais sobre o DAX. Depois de concluir este tutorial, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Quando cria a sua própria medida, esta é adicionada à lista Campos da tabela que selecionar e é designada de medida *modelo*. Algumas das vantagens das medidas modelo incluem a possibilidade de atribuir o nome que quiser, tornando-as mais identificáveis; pode utilizá-las como argumentos noutras expressões DAX e pode colocá-las a realizar cálculos complexos muito rapidamente.

>[!TIP]
>A partir da versão fevereiro de 2018 do Power BI Desktop, muitos cálculos comuns estão disponíveis como **medidas rápidas**, as quais escrevem as fórmulas DAX para o utilizador com base nas suas entradas numa caixa de diálogo. Estes cálculos rápidos e poderosos também são ideias para aprender o DAX ou propagar as suas próprias medidas personalizadas. Para criar ou explorar medidas rápidas, selecione **Nova medida rápida** na lista **Mais opções** de uma tabela ou em **Cálculos** no separador Base do friso. Veja [Utilizar medidas rápidas](desktop-quick-measures.md) para obter mais informações sobre como criar e utilizar medidas rápidas.

### <a name="create-a-measure"></a>Criar uma medida

Pretende analisar as vendas líquidas ao subtrair descontos e devoluções a partir dos valores de vendas totais. Independentemente do contexto existente na sua visualização, precisa de uma medida para subtrair a soma de DiscountAmount e ReturnAmount da soma de SalesAmount. Não há nenhum campo para Vendas Líquidas na lista Campos, mas o utilizador possui os blocos modulares para criar as suas próprias medidas para calcular as vendas líquidas. 

1.  Clique com botão direito do rato na tabela **Vendas** na secção Campos ou posicione o cursor sobre a tabela e selecione as reticências (…) **Mais opções** e, em seguida, selecione **Nova medida**. Este procedimento guardará a nova medida na tabela Vendas, onde será mais fácil de ser encontrada.
    
    ![Nova medida](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    Também pode criar uma nova medida ao selecionar **Nova Medida** no grupo Cálculos do separador Base do friso Power BI Desktop.
    
    ![Nova medida do friso](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Quando cria uma medida a partir do friso, esta pode ser criada em qualquer uma das tabelas, mas será mais fácil encontrá-la se a criar no local em que a pretende utilizar. Neste caso, selecione a tabela Vendas para a ativar e, em seguida, selecione **Nova Medida**. 
    
    A barra de fórmulas é apresentada na parte superior da tela de relatórios, onde pode mudar o nome da medida e introduzir uma fórmula DAX.
    
    ![Barra de fórmulas](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
2.  Por predefinição, uma nova medida é simplesmente denominada Medida. Se não alterar o seu nome, as novas medidas adicionais serão denominadas Medida 2, Medida 3 e assim sucessivamente. Pretende que as suas medidas sejam mais identificáveis. Para isso, realce **Medida** na barra de fórmulas e, em seguida, escreva **Vendas Líquidas**.
    
3.  Agora, pode começar a inserir a sua fórmula. Depois do sinal igual, começa a escrever **Sum**. À medida que escreve, é apresentada uma lista de sugestão de lista pendente, que mostra todas as funções DAX que começam com as letras que escreveu. Desloque-se para baixo, se necessário, para selecionar **SUM** na lista e, em seguida, prima Enter.
    
    ![Escolher SUM](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    É apresentado um parêntese esquerdo, juntamente com outra lista de sugestões pendente de todas as colunas disponíveis que pode transmitir à função SUM.
    
    ![Escolher coluna](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    As expressões aparecem sempre entre parênteses. A expressão conterá um argumento único para passar à função SUM: a coluna SalesAmount. Comece a escrever “SalesAmount” até restar apenas um valor na lista: Sales(SalesAmount). O nome da coluna precedido pelo nome da tabela é designado de *nome completamente qualificado* da coluna. Os nomes de coluna completamente qualificados tornam as suas fórmulas mais fáceis de ler. 
    
    ![Selecionar SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
4. Selecione **Sales[SalesAmount]** e, em seguida, escreva um parêntesis de fecho.
    
    > [!TIP]
    > Os erros de sintaxe são causados frequentemente por um parêntesis de fecho deslocado ou em falta.
    
    
    
5.  Para subtrair as outras duas colunas:
    1. Após o parêntese direito da primeira expressão, insira um espaço, um operador de subtração (**-**) e outro espaço. 
    2. Introduza outra função SUM e comece a escrever “DiscountAmount” até que possa escolher a coluna **Sales[DiscountAmount]** como o argumento. Adicione um parêntese direito. 
    3. Insira um espaço, outro operador de subtração, outra função SUM com **Sales[ReturnAmount]** como o argumento e um parêntese direito.
    
    ![Fórmula completa](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
6.  Prima Enter ou clique na marca de verificação na barra de fórmulas para concluir e validar a fórmula. A medida validada está agora pronta a ser utilizada na lista Campo da tabela Vendas. 
    
    ![Medida na lista de campos](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
Se ficar sem espaço para introduzir uma fórmula ou pretender que fique em linhas separadas, selecione a divisa para baixo no lado direito da barra de fórmulas para abrir mais espaço.

![Divisa da fórmula](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

Pode separar partes da sua fórmula em linhas diferentes ao premir **Alt-Enter** ou ao mover o conteúdo através da tecla de **Tabulação**.

![Fórmula expandida](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Utilizar a medida no relatório
Agora, pode adicionar a medida Vendas Líquidas à tela de relatório e calcular as vendas líquidas de todos os outros campos adicionados ao relatório. Para analisar as vendas líquidas por país:

1. Selecione a medida **Vendas Líquidas** na tabela **Vendas** ou arraste-a para a tela de relatórios.
    
2. Selecione o campo **RegionCountryName** na tabela **Geografia** ou arraste-o para o gráfico.
    
    ![Vendas Líquidas por País](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
Para ver a diferença entre as vendas líquidas e as vendas totais por país, selecione o campo **SalesAmount** ou arraste-o para o gráfico. 

![Montante de Vendas e Vendas Líquidas por País](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

O gráfico utiliza agora duas medidas: SalesAmount, que foi somada automaticamente, e a medida Net Sales que o utilizador criou. Cada medida foi calculada no contexto de outro campo, RegionCountryName.
    
### <a name="use-your-measure-with-a-slicer"></a>Utilizar a medida com uma segmentação de dados

Pode adicionar uma segmentação de dados para filtrar ainda mais as vendas líquidas e os montantes de vendas por ano civil.
    
1.  Clique numa área em branco ao lado do gráfico e, em **Visualizações**, selecione a visualização **Tabela**. Este procedimento cria uma nova visualização de tabela em branco na tela de relatórios.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
2.  Arraste o campo **Ano** da tabela **Calendário** para a nova visualização de tabela em branco. Uma vez que o ano é um campo numérico, o Power BI Desktop soma os seus valores, mas isso não faz muito sentido como uma agregação. 
    
    ![Agregação de ano](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3.  Em **Valores** no painel Visualizações, selecione a seta para baixo junto a **Ano** e, em seguida, selecione **Não resumir**. A tabela apresenta agora anos individuais.
    
    ![Não resumir](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Selecione o ícone **Segmentação de Dados** no painel Visualizações para converter a tabela numa segmentação de dados.

    ![Alterar para a segmentação de dados](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Selecione qualquer valor na segmentação de dados **Ano** para filtrar o gráfico **Vendas Líquidas e Montante de Vendas por País** em conformidade. As medidas Vendas Líquidas e SalesAmount recalculam e apresentam os resultados no contexto do campo Ano selecionado. 
    
    ![Gráfico segmentado por Ano](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Utilizar a medida noutra medida

Pretende saber quais os produtos com a maior quantidade de vendas líquidas por unidade vendida, por isso, precisa de uma medida que divida as vendas líquidas pela quantidade de unidades vendidas. Pode criar uma nova medida que divida o resultado da medida Vendas Líquidas pela soma de Sales[SalesQuantity].

1.  Crie uma nova medida chamada **Vendas Líquidas por Unidade** na tabela Vendas.
    
2.  Na barra de fórmulas, começa a escrever **Vendas Líquidas**. A lista de sugestões mostrará o que pode adicionar. Selecione **[Net Sales]**.
    
    ![Fórmula a utilizar Vendas Líquidas](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    Também pode fazer referência a medidas ao introduzir apenas um parêntese reto esquerdo (**[**). A lista de sugestões mostrará apenas medidas para adicionar à sua fórmula.
    
    ![O parêntese reto mostra apenas as medidas](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  Introduza um espaço, um operador de divisão (**/**), outro espaço, uma função SUM e, em seguida, escreva **Quantidade**. A lista de sugestões mostra todas as colunas cujo nome contém Quantidade. Selecione **Sales[SalesQuantity]**, insira o parêntese direito e prima ENTER ou selecione a marca de verificação para validar a fórmula. A fórmula deve ter este aspeto:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
4. Selecione a medida **Vendas Líquidas por Unidade** na tabela Vendas ou arraste-a para uma área em branco na tela de relatório. O gráfico mostra o montante de vendas líquidas por unidade em relação a todos os produtos vendidos, o que não é muito informativo. 
    
    ![Vendas líquidas gerais por unidade](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
5. Para alterar o aspeto, altere o tipo de visualização de gráfico para **Mapa de árvore**.
    
    ![Alterar para o mapa de árvore](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. Selecione o campo **Categoria do Produto** ou arraste-o para o mapa de árvore ou para o campo Grupo do painel Visualizações. Agora, tem algumas boas informações!
    
    ![Mapa de árvore por Categoria de Produto](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Experimente remover o campo **ProductCategory** e arrastar o campo **ProductName** para o gráfico em alternativa. 
    
    ![Mapa de árvore por Nome do Produto](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
OK, agora estamos apenas a experimentar, mas temos de admitir que é interessante! Experimente outras formas de filtrar e formatar a visualização.

## <a name="what-youve-learned"></a>O que aprendeu
As medidas dão-lhe uma grande ajuda na obtenção das informações que pretende retirar dos seus dados. Aprendeu com criar medidas com a barra de fórmulas, atribuir-lhes nomes que façam mais sentido e localizar e selecionar os elementos da fórmula corretos através das listas de sugestões DAX. Também aprendeu o contexto, no qual os resultados dos cálculos em medidas mudam de acordo com outros campos ou através de outras expressões na sua fórmula.

## <a name="next-steps"></a>Próximos passos
- Para saber mais sobre as medidas rápidas do Power BI Desktop, que fornecem muitos cálculos de medidas comuns, veja [Utilizar medidas rápidas para realizar facilmente cálculos comuns e poderosos](desktop-quick-measures.md).
  
- Se quiser aprofundar as fórmulas DAX e criar algumas medidas mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo foca os conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente do contexto.
  
- Certifique-se de que adiciona a [Referência ao DAX Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) aos favoritos. É aqui que encontrará informações detalhadas sobre a sintaxe do DAX, operadores e mais de 200 funções DAX.

