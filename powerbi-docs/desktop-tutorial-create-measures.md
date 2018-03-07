---
title: "Tutorial: Criar as suas próprias medidas no Power BI Desktop"
description: "Tutorial: Criar as suas próprias medidas no Power BI Desktop"
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
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 96295ced577ddb18b8c56031278bf9a81cddf981
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Tutorial: Criar as suas próprias medidas no Power BI Desktop
Algumas das mais poderosas soluções de análise de dados no Power BI Desktop podem ser criadas com a utilização de medidas. As medidas ajudam-nos a executar cálculos sobre os dados à medida que interagimos com os relatórios. Este tutorial serve de guia para que compreenda as medidas básicas e crie algumas delas no Power BI Desktop.

Este artigo destina-se aos utilizadores do Power BI já familiarizados com o Power BI Desktop para criar modelos mais avançados. Já deve estar familiarizado com as funcionalidades Obter Dados e Editor de Consultas para importar dados, trabalhar com várias tabelas relacionadas e adicionar campos à tela Relatório. Se ainda não estiver familiarizado com o Power BI Desktop, veja [Introdução ao Power BI Desktop](desktop-getting-started.md).

Para concluir os passos neste tutorial, tem de transferir o ficheiro [Exemplo de Vendas da Contoso para o Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip). Já inclui dados de vendas online da empresa fictícia, Contoso, Inc. Como os dados no ficheiro foram importados de um base de dados, não conseguirá ligar à origem de dados nem visualizá-los no Editor de Consultas. Quando tiver o ficheiro no seu computador, abra-o no Power BI Desktop.

## <a name="what-are-these-measures-all-about"></a>De que se tratam estas medidas?
Na maioria das vezes, as medidas são criadas automaticamente, como quando selecionamos a caixa de verificação junto ao campo **SalesAmount** da tabela **Sales** na lista de campos, ou arrastamos **SalesAmount** para a tela Relatório.

![](media/desktop-tutorial-create-measures/measurestut_salesamountinfieldlist.png)

É apresentada uma nova visualização do gráfico, como esta:

![](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

O que obtemos é um gráfico de colunas com uma soma total dos valores de vendas obtidos do campo SalesAmount.  Na verdade, o campo SalesAmount é apenas uma coluna denominada SalesAmount na tabela Sales, que já importámos.

A coluna SalesAmount contém mais de dois milhões de linhas de valores de vendas. Deve estar a perguntar-se por que não vê uma tabela com linhas com todos esses valores. Bem, o Power BI Desktop sabe que todos os valores em SalesAmount são de um tipo de dados numérico e provavelmente quer agregá-los de algum modo, seja a somá-los, a obter a média, a contá-los, etc.

Sempre que vir um campo na lista Campos com um ícone de sigma ![](media/desktop-tutorial-create-measures/meastut_sigma.png), significa que o campo é numérico e os seus valores podem ser agregados. Neste caso, quando selecionamos SalesAmount, o Power BI Desktop cria as suas próprias medidas e a soma de todos os valores de vendas é calculada e apresentada no gráfico.

Sum (soma) é a agregação predefinida quando selecionamos um campo com um tipo de dados numérico, mas podemos mudar facilmente para outro tipo de agregação.

Na área **Value**, se clicarmos na seta para baixo junto a **SalesAmount**, podemos selecionar **Average**.

![](media/desktop-tutorial-create-measures/meastut_salesamountaverage.png)

A nossa visualização muda para uma média de todos os valores de vendas no campo SalesAmount.

![](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Podemos alterar o tipo de agregação consoante o resultado desejado, mas nem todos os tipos de agregação são aplicáveis a qualquer tipo de dados numérico. Por exemplo, para o campo SalesAmount, Sum e Average fazem sentido. Minimum e Maximum também são importantes. No entanto, Count não faz muito sentido para o campo SalesAmount, porque embora os valores sejam numéricos, na verdade, referem-se à moeda.

Compreender o funcionamento das agregações é fundamental para compreender as medidas, pois cada medida executará algum tipo de agregação. Veremos mais exemplos de utilização de uma agregação de Soma um pouco mais tarde, quando criar algumas das suas próprias medidas.

Os valores calculados com medidas estão sempre a mudar de acordo com as interações que temos com o relatório. Por exemplo, se arrastarmos o campo **RegionCountryName** da tabela **Geography** para o gráfico, as médias dos valores de vendas para cada país são calculadas e apresentadas.

![](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quando o resultado de uma medida é alterado devido a uma interação com o relatório, estamos a afetar o *contexto* da medida. Na verdade, sempre que interage com o relatório, altera o contexto no qual uma medida calcula e apresenta os resultados.

Na maioria dos casos, o Power BI faz o seu trabalho e calcula e devolve valores de acordo com os campos que adicionamos e os tipos de agregação que escolhemos. No entanto, noutros casos, talvez tenha de criar as suas próprias medidas para executar cálculos mais complexos e exclusivos.

Com o Power BI Desktop, cria as suas próprias medidas com a linguagem de fórmulas DAX (Data Analysis Expressions). As fórmulas DAX são muito semelhantes às fórmulas do Excel. Na verdade, o DAX utiliza muitos operadores, funções e sintaxe também utilizados pelas fórmulas do Excel. No entanto, as funções DAX foram concebidas para trabalhar com dados relacionais e realizar cálculos mais dinâmicos durante a interação com os relatórios.

Existem mais de 200 funções DAX que fazem tudo, desde agregações simples, como Soma e Média, até funções de estatística e de filtragem mais complexas. Não vamos entrar em muitos detalhes sobre a linguagem DAX aqui, mas existem muitos recursos para ajudá-lo a saber mais. Depois de seguir este tutorial, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Quando criamos as nossas próprias medidas, estas são adicionadas à lista Campos da tabela desejada. Isto é conhecido como uma medida *modelo*, que permanecerá na nossa tabela como um campo. Algumas das grandes vantagens para medidas modelo são o facto de podermos dar-lhes o nome que pretendermos, tornando-as mais identificáveis. Também podemos utilizá-las como um argumento noutras expressões DAX, além de criar medidas que executam cálculos complexos muito rapidamente.

## <a name="lets-create-our-own-measure"></a>Vamos criar a nossa própria medida
Vamos supor que queremos analisar as nossas vendas líquidas. Se observarmos a tabela Sales na lista de campos, vemos que não existe nenhum campo denominado NetSales. No entanto, temos os blocos modulares para criar a nossa própria medida para calcular as vendas líquidas.

Precisamos de uma medida para subtrair descontos e devoluções dos valores de vendas. Como queremos que a medida calcule um resultado para qualquer contexto que tenhamos na visualização, temos de subtrair a soma de DiscountAmount e ReturnAmount da soma de SalesAmount. Isto pode parecer um pouco confuso neste momento; não se preocupe, ficará mais claro em breve.

### <a name="net-sales"></a>Vendas líquidas
1.  Clique com o botão direito do rato ou na seta para baixo na tabela **Sales** na lista de campos e, em seguida, clique em **Nova Medida**. Isto garante que a nova medida é guardada na tabela Sales, onde será mais fácil de ser encontrada.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    > [!TIP]
    > Também pode criar uma nova medida clicando no botão Nova Medida no friso que se encontra no separador Base do Power BI Desktop.
    > 
    > ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    > 
    > Quando cria uma medida no friso, a medida pode ser criada em qualquer uma das tabelas. Embora uma medida não tenha de pertencer a uma tabela específica, será mais fácil de localizar se a criar na tabela que, por lógica, faz mais sentido para si. Se quiser que fique numa tabela específica, clique primeiro na tabela para torná-la ativa. Em seguida, clique em Nova Medida. No nosso caso, vamos criar a primeira medida na tabela Sales.
    > 
    > 
    
    A barra de fórmulas aparece na parte superior da tela Relatório. É aqui que podemos mudar o nome da medida e introduzir uma fórmula DAX.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
    Vamos dar um nome à nova medida. Por predefinição, uma nova medida é simplesmente denominada Measure. Se não mudarmos o nome, a próxima medida que criarmos terá o nome Measure 2, Measure 3 e assim sucessivamente. Queremos que as medidas sejam identificáveis mais facilmente, por isso vamos chamar a nova medida de Net Sales.
    
2. Realce **Medida** na barra de fórmulas e, em seguida, escreva **Net Sales**.
    
    Agora, podemos começar a introduzir a fórmula.
    
3.  Após o sinal de igual, escreva um **S**. Verá uma lista de sugestões pendente com todas as funções DAX começadas pela letra S. Quanto mais escrevermos, mais aproximada será a lista de sugestões da função que precisamos. Selecione **SUM** ao deslocar-se para baixo e prima Enter.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Depois de premir Enter, é apresentado um parêntese de abertura junto de outra lista de sugestões de todas as colunas disponíveis que podemos transmitir à função SUM.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    Aparece sempre uma expressão entre parênteses de abertura e de fecho. Neste caso, a expressão vai conter um único argumento para transmitir à função SUM; uma coluna a somar. Podemos restringir a lista de colunas ao escrever as primeiras letras do que queremos. Neste caso, queremos a coluna SalesAmount, assim, quando começarmos a escrever "salesam", a lista fica menor e vemos dois itens que podem ser selecionados. Na verdade, estão na mesma coluna. Um mostra apenas [SalesAmount], porque estamos a criar a medida na mesma tabela em que está a coluna SalesAmount. No outro, podemos ver o nome da tabela antes do nome da coluna.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
    Em geral, é uma boa prática introduzir o nome completamente qualificado de uma coluna. Tornará as fórmulas mais fáceis de ler.
    
4. Selecione **Sales[SalesAmount]** e, em seguida, escreva um parêntesis de fecho.
    
    > [!TIP]
    > Os erros de sintaxe são causados frequentemente por um parêntesis de fecho deslocado ou em falta.
    > 
    > 
    
    Agora, queremos subtrair as outras duas colunas.
    
5.  Após o parêntesis de fecho para a nossa primeira expressão, escreva um espaço e, em seguida, um operador de subtração (**-**), seguido de outro espaço. Em seguida, introduza outra função SUM com a coluna **Sales[DiscountAmount]** como o argumento.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
    Estamos a começar a ficar sem espaço para a fórmula. Não há problema.
    
6.  Clique na divisa inferior no lado direito da barra de fórmulas.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)
    
    Agora temos mais espaço. Podemos introduzir novas partes da fórmula numa nova linha ao premir Alt-Enter. Também podemos mover os itens com a tecla Tab.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)
    
    Agora, podemos adicionar a parte final da fórmula.
    
7.  Adicione outro operador de subtração, seguido de outra função SUM que tenha a coluna **Sales[ReturnAmount]** como argumento.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
    A fórmula parece agora pronta.

8.  Prima Enter ou clique na marca de verificação na barra de fórmulas para concluir. A fórmula é validada e adicionada à lista de campos na tabela Sales.

### <a name="lets-add-our-new-measure-to-a-report"></a>Vamos adicionar a nova medida a um relatório
Agora, podemos adicionar a medida Net Sales à tela Relatório. As vendas líquidas serão calculadas para quaisquer outros campos adicionados ao relatório. Vamos analisar as vendas líquidas por país.

1.  Arraste a medida **Net Sales** da tabela **Sales** para a tela Relatório.
    
2. Agora, arraste o campo **RegionCountryName** da tabela **Geography** para o gráfico.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
    Vamos adicionar mais alguns dados.
    
3.  Arraste o campo **SalesAmount** para o gráfico, para ver a diferença entre o valor de vendas e o de vendas líquidas.
    
    Agora, temos realmente duas medidas no gráfico. SalesAmount, que foi somada automaticamente, e a medida Net Sales que criámos. Em cada um dos casos, os resultados foram calculados no contexto de outro campo que temos no gráfico, os países em RegionCountryName.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)
    
    Vamos adicionar uma Segmentação de Dados, para podermos dividir as vendas líquidas e valores de vendas por ano civil.
    
4.  Clique numa área em branco ao lado do gráfico e, em **Visualizações**, clique na visualização de Tabela.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktablevisbutton.png)
    
    Isto cria uma nova visualização de tabela em branco na tela Relatório.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
5.  Arraste o campo **Year** da tabela **Calendar** para a nova tabela em branco.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
    Como Year é um campo numérico, o Power BI Desktop somou os valores e forneceu um gráfico. No entanto, isto não nos ajuda muito como Segmentação de Dados.
    
6. Em **Valores**, clique na seta para baixo junto a **Year** e, em seguida, clique em **Não Resumir**.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
    Agora, podemos alterar o campo Year na visualização de tabela para uma Segmentação de Dados.

    7.  Em **Visualizações**, clique na visualização **Segmentação de Dados**.

    ![](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
    Agora, temos Year como Segmentação de Dados. Podemos selecionar qualquer ano individual ou grupo de anos e as visualizações do relatório serão todas segmentadas.
    
8. Clique em **2013**. Verá o gráfico mudar. As medidas Net Sales e SalesAmount são recalculadas e mostram os novos resultados apenas para 2013. Aqui, mais uma vez, alteramos o contexto no qual as medidas calculam e apresentam os resultados.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

## <a name="lets-create-another-measure"></a>Vamos criar outra medida
Agora que sabe como criar as suas próprias medidas, vamos criar outra.

### <a name="net-sales-per-unit"></a>Net sales per unit
E se quisermos descobrir quais são os produtos com o maior valor líquido de vendas por unidade vendida?

Bem, vamos criar outra medida. Neste caso, queremos dividir as vendas líquidas pela quantidade de unidades vendidas. Na verdade, queremos dividir o resultado da medida Net Sales pela soma de Sales[SalesQuantity].

1.  Crie uma nova medida chamada **Net Sales per Unit** na tabela Sales ou Products.
    
    Nesta medida, vamos utilizar a medida Net Sales que criámos anteriormente. Com o DAX, podemos fazer referência a outras medidas na fórmula.
    
2.  Comece por escrever **Net Sales**. A lista de sugestões mostrará o que podemos adicionar. Selecione **[Net Sales]**.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    Também pode fazer referência a outra medida ao escrever apenas um parêntese de abertura (**[**). A lista de sugestões mostrará apenas as medidas que podemos adicionar à fórmula.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  Logo após **[Net Sales]**, insira um espaço e, em seguida, um operador de divisão (**/**). Depois, introduza uma função SUM e escreva **Quantity**. A lista de sugestões mostra todas as colunas cujo nome contém Quantity. Selecione **Sales[SalesQuantity]**. A fórmula deve ter o seguinte aspeto:
    
    > **Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])**
    > 
    > 
    
    Muito interessante, não acha? Introduzir fórmulas DAX é realmente muito fácil quando utilizamos a funcionalidade de pesquisa e sugestão do Editor DAX. Agora, vamos ver o que obtemos com a nova medida Net Sales per Unit.
    
4. Arraste a medida **Net Sales per Unit** para uma área em branco na tela de relatório.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
    Não é muito interessante, certo? Não se preocupe.
    
5.  Altere o tipo de visualização de gráfico para **Tree Map**.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. Agora, arraste o campo **ProductCategory** da tabela **ProductCategory** para baixo até à área **Group**.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
    São boas informações, mas e se quisermos analisar as vendas líquidas por produto?
    
7. Remova o campo **ProductCategory** e arraste o campo **ProductName** da tabela **Product** para baixo até à área **Group**, substituindo-o. 
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
    OK, agora estamos apenas a experimentar, mas temos de admitir que é bastante interessante! Obviamente que podemos filtrar este mapa de árvore de várias formas, mas está fora do âmbito deste tutorial.

## <a name="what-weve-learned"></a>O que aprendemos
As medidas oferecem-nos uma enorme capacidade de obter as informações que queremos dos nossos dados. Aprendemos a criar medidas com a barra de fórmulas. Podemos atribuir nomes às medidas de uma forma lógica, enquanto que as listas de sugestão facilitam a localização e seleção do elemento certo a ser adicionado às fórmulas. Também aprendemos o contexto, no qual o resultado de cálculos em medidas muda de acordo com outros campos ou através de outras expressões na fórmula da medida.

## <a name="next-steps"></a>Passos seguintes
Se quiser aprofundar as fórmulas DAX e criar algumas medidas mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo foca os conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente do contexto.

Certifique-se de que adiciona a [Referência ao DAX Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) aos favoritos. É aqui que encontrará informações detalhadas sobre a sintaxe do DAX, operadores e mais de 200 funções DAX.

