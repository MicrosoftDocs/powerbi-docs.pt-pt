---
title: Noções básicas do DAX no Power BI Desktop
description: Noções básicas do DAX no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9ff04510a786fa89e1e461e6eefee1af90e58a8e
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760641"
---
# <a name="apply-dax-basics-in-power-bi-desktop"></a>Aplicar as noções básicas do DAX no Power BI Desktop
Este artigo é destinado aos novos utilizadores do Power BI Desktop. Fornece-lhe uma introdução rápida e fácil sobre como pode utilizar o DAX (Data Analysis Expressions) para resolver vários problemas de análise de dados e de cálculo básico. Iremos abordar algumas informações conceptuais e uma série de tarefas que pode executar, além de uma prova de aferição para verificar o que aprendeu. Depois de ler este artigo, deverá ter uma boa compreensão dos conceitos fundamentais mais importantes no DAX.

## <a name="what-is-dax"></a>O que é o DAX?
O DAX é uma coleção de funções, operadores e constantes que podem ser usados numa fórmula, ou expressão, para calcular e devolver um ou mais valores. De uma forma mais simples, o DAX ajuda-o a criar nova informação a partir de dados já existentes no seu modelo.

## <a name="why-is-dax-so-important"></a>Por que razão o DAX é tão importante?
É fácil criar um novo ficheiro do Power BI Desktop e importar alguns dados para o mesmo. Pode até mesmo criar relatórios que mostrem informações valiosas sem usar nenhuma fórmula DAX. Mas, e se precisar de analisar a percentagem de crescimento em categorias de produto e para diferentes intervalos de datas? Ou tiver de calcular o crescimento de ano para ano comparativamente com as tendências do mercado? As fórmulas DAX oferecem esta e outras funcionalidades importantes. Aprender a criar fórmulas DAX eficientes vai ajudá-lo a tirar o máximo partido dos seus dados. Quando obtém as informações de que necessita, pode começar a resolver problemas comerciais reais que afetam o seu resultado final. É este o potencial do Power BI, e o DAX vai ajudá-lo a beneficiar dele.

## <a name="prerequisites"></a>Pré-requisitos
Pode já estar familiarizado com a criação de fórmulas no Microsoft Excel. Esse conhecimento vai ser útil na compreensão do DAX, mas mesmo que não tenha experiência com fórmulas do Excel, os conceitos descritos aqui vão ajudá-lo a começar a criar fórmulas DAX e a resolver problemas de BI do mundo real, imediatamente.

Iremos centrar-nos na compreensão das fórmulas DAX usadas em cálculos, mais especificamente, em medidas e colunas calculadas. Já deverá estar familiarizado com a utilização do Power BI Desktop para importar dados e adicionar campos a um relatório, bem como com os conceitos fundamentais de [Medidas](desktop-measures.md) e [Colunas calculadas](desktop-calculated-columns.md).

### <a name="example-workbook"></a>Livro de exemplo

A melhor forma de aprender sobre o DAX é criar algumas fórmulas básicas, utilizá-las com dados reais e ver os resultados. Os exemplos e tarefas aqui descritos utilizam o [Exemplo de Vendas da Contoso para o ficheiro do Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip). Este é o mesmo ficheiro de exemplo utilizado no artigo [Tutorial: Criar as suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md). 

## <a name="lets-begin"></a>Vamos começar!
Iremos estruturar a nossa compreensão do DAX em torno de três conceitos fundamentais: *Sintaxe*, *Funções* e *Contexto*. Existem outros conceitos importantes no DAX, mas entender estes três conceitos permitirá uma melhor base para o desenvolvimento das suas competências com o DAX.

### <a name="syntax"></a>Sintaxe
Antes de criar as suas próprias fórmulas, vamos dar uma vista de olhos na sintaxe das fórmulas DAX. A sintaxe inclui os vários elementos que compõem uma fórmula ou, de uma forma mais simples, o modo como a fórmula é escrita. Por exemplo, eis uma fórmula DAX simples para uma medida:

![Sintaxe da fórmula DAX](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Esta fórmula inclui os seguintes elementos de sintaxe:

**A.** O nome da medida: **Total Sales**.

**B.** O operador de sinal de igual ( **=** ), que indica o início da fórmula. Quando calculada, devolve um resultado.

**C.** A função **SUM** do DAX, que soma todos os números na coluna **Sales[SalesAmount]** . Irá aprender mais sobre as funções mais tarde.

**D.** Os parênteses **()** , que envolvem uma expressão que contém um ou mais argumentos. Todas as funções exigem pelo menos um argumento. Um argumento transmite um valor a uma função.

**E.** A tabela referenciada **Sales**.

**F.** A coluna referenciada **[SalesAmount]** na tabela Sales. Com este argumento, a função SUM sabe em que coluna deve agregar uma SUM.

Ao tentar entender uma fórmula DAX, geralmente é útil decompor os elementos numa linguagem que usa e fala todos os dias. Por exemplo, pode ler esta fórmula como:

> *Para a medida chamada Total Sales, calcule (=) a SOMA dos valores na coluna [SalesAmount], na tabela Sales.*
> 
> 

Quando adicionada a um relatório, essa medida calcula e devolve valores somando os valores das vendas para cada um dos outros campos que são incluídos, por exemplo, “Cell Phones in the USA”.

Provavelmente, estará a pensar: “Por acaso esta medida não faz o mesmo que adicionar o campo SalesAmount ao meu relatório?” Bem, sim. Porém, há um bom motivo para criarmos a nossa própria medida que soma os valores do campo SalesAmount: podemos utilizá-la como um argumento noutras fórmulas. Isto pode parecer-lhe um pouco confuso agora, mas ao desenvolver as suas capacidades com fórmulas DAX, saber esta medida tornará as suas fórmulas e o seu modelo mais eficientes. Na verdade, verá mais tarde a medida Total Sales a aparecer como um argumento noutras fórmulas.

Observemos mais algumas coisas sobre essa fórmula. Em especial, introduzimos uma função, [SUM](https://msdn.microsoft.com/library/ee634387.aspx). As funções são fórmulas previamente gravadas que facilitam cálculos complexos e manipulações de números, datas, hora, texto e muito mais. Irá aprender mais sobre as funções posteriormente.

Também observa que o nome da coluna [SalesAmount] era precedido pela tabela Sales, à qual pertence a coluna. Este nome é conhecido como um nome de coluna completamente qualificado, que inclui o nome da coluna precedido do nome da tabela. As colunas referenciadas na mesma tabela não exigem que o nome da tabela seja incluído na fórmula, o que pode tornar as fórmulas longas mais curtas e fáceis de ler quando fazem referência a várias colunas. No entanto, é uma melhor prática incluir o nome da tabela nas suas fórmulas de medida, mesmo quando se trata da mesma tabela.

> [!NOTE]
> Se um nome de tabela contiver espaços, palavras-chave reservadas ou carateres não permitidos, terá de colocar o nome da tabela entre plicas. Além disso, precisará de colocar os nomes de tabela entre aspas se o nome contiver quaisquer caracteres fora do conjunto de caracteres alfanuméricos ANSI, independentemente de a sua região suportar ou não o conjunto de caracteres.
> 
> 

É importante que as suas fórmulas tenham a sintaxe correta. Na maioria dos casos, se a sintaxe não estiver correta, será devolvido um erro de sintaxe. Noutros casos, a sintaxe pode estar correta, mas os valores devolvidos podem não ser o que esperava. O editor de DAX no Power BI Desktop inclui uma funcionalidade de sugestões, que é utilizada para criar fórmulas sintaticamente corretas ao ajudá-lo a selecionar os elementos corretos.

Vamos criar uma fórmula simples. Esta tarefa permitirá perceber melhor a sintaxe da fórmula e como a funcionalidade das sugestões na barra de fórmulas o pode ajudar.

### <a name="task-create-a-measure-formula"></a>Tarefa: Criar uma fórmula de medida

1. [Transfira](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip) e abra o ficheiro do Power BI Desktop do Exemplo de Vendas da Contoso. 
    
2. Na vista Relatório, na lista de campos, clique com o botão direito do rato na tabela **Sales** e selecione **Nova Medida**.
    
3. Na barra de fórmulas, substitua **Measure** ao introduzir um novo nome de medida: *Previous Quarter Sales*.
    
4. Após o sinal de igual, escreva as primeiras letras *CAL* e, em seguida, faça duplo clique na função que pretende utilizar. Nesta fórmula, quer utilizar a função **CALCULATE**.

   Irá usar a função CALCULATE para filtrar os valores que desejamos somar por um argumento que transmitimos à função CALCULATE. A isto chama-se aninhamento de funções. A função CALCULATE tem pelo menos dois argumentos. O primeiro é a expressão a ser avaliada e o segundo é um filtro.
   
5. Depois do parêntesis de abertura *(* para a função **CALCULATE**, escreva *SUM* seguido de outro parêntesis de abertura *(* . 

   Em seguida, iremos passar um argumento para a função SUM.

6. Comece a escrever *Sal* e, em seguida, selecione **Sales [SalesAmount]** , seguido de um parêntesis de fecho *)* . 

   Este é o primeiro argumento de expressão para a função CALCULATE.
    
7. Escreva uma vírgula ( *,* ) seguida de um espaço para especificar o primeiro filtro e, em seguida, escreva *PREVIOUSQUARTER*. 
    
   Irá utilizar a função de análise de tempo PREVIOUSQUARTER para filtrar os resultados SUM pelo trimestre anterior.
    
8. Depois do parêntesis de abertura *(* da função PREVIOUSQUARTER, escreva *Calendar[DateKey]* .
    
   A função PREVIOUSQUARTER tem um argumento, uma coluna contendo um intervalo contíguo de datas. No nosso caso, é a coluna DateKey na tabela Calendário.
    
9. Feche ambos os argumentos transmitidos para as funções PREVIOUSQUARTER e CALCULATE ao escrever dois parêntesis de fecho *))* .
    
   A sua fórmula agora deve ter este aspeto:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
10. Selecione a marca de verificação ![Ícone de marca de verificação](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) na barra de fórmulas ou prima Enter para validar a fórmula e adicioná-la ao modelo.

Conseguiu! Acabou de criar uma medida complexa ao utilizar o DAX, e não estamos a falar de uma medida fácil. O que esta fórmula vai fazer é calcular o total de vendas do trimestre anterior, dependendo dos filtros aplicados num relatório. Por exemplo, se colocarmos SalesAmount e a nossa nova medida Previous Quarter Sales num gráfico e adicionarmos Year e QuarterOfYear como Segmentações de Dados, obteremos algo semelhante ao exemplo abaixo:

![Gráfico Previous Quarter Sales e SalesAmount](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Acabou de conhecer vários aspetos importantes das fórmulas DAX: 

- Esta fórmula incluiu duas funções. [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx), uma função de análise de tempo, está aninhada como um argumento transmitido a [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx), uma função de filtro. 

   As fórmulas DAX podem conter até 64 funções aninhadas. É pouco provável que uma fórmula venha a conter tantas funções aninhadas. Na verdade, tal fórmula seria difícil de criar e depurar; além disso, provavelmente, não seria muito rápida.

- Nesta fórmula, também usou filtros. Os filtros restringem o que será calculado. Neste caso, selecionou um filtro como um argumento que, na verdade, é o resultado de outra função. Irá aprender mais sobre os filtros mais tarde.

- Utilizou a função CALCULATE. Esta função é uma das mais poderosas no DAX. À medida que for criando modelos e fórmulas mais complexos, provavelmente utilizará esta função muitas vezes. Embora uma discussão mais profunda sobre a função CALCULATE esteja fora do âmbito deste artigo, à medida que for desenvolvendo os seus conhecimentos de DAX, preste especial atenção à função.

### <a name="syntax-quickquiz"></a>Teste rápido sobre sintaxe
1. O que faz este botão na barra de fórmulas?
   
   > ![Seleção de botão](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. O que está sempre à volta de um nome de coluna numa fórmula DAX?

As respostas são fornecidas no final deste artigo.

### <a name="functions"></a>Functions
As funções são fórmulas predefinidas que realizam cálculos com valores específicos, chamados argumentos, numa determinada ordem ou estrutura. Os argumentos podem ser outras funções, outra fórmula, expressão, referências de coluna, números, texto, valores lógicos como TRUE ou FALSE, ou constantes.

O DAX inclui as seguintes categorias de funções: [Data e Hora](https://msdn.microsoft.com/library/ee634786.aspx), [Análise de Tempo](https://msdn.microsoft.com/library/ee634763.aspx), [Informações](https://msdn.microsoft.com/library/ee634552.aspx), [Lógica](https://msdn.microsoft.com/library/ee634365.aspx), [Matemática](https://msdn.microsoft.com/library/ee634241.aspx), [Estatísticas](https://msdn.microsoft.com/library/ee634822.aspx), [Texto](https://msdn.microsoft.com/library/ee634938.aspx), [Principal/Subordinado](https://msdn.microsoft.com/library/mt150102.aspx) e [Outras](https://msdn.microsoft.com/library/mt150101.aspx). Se já estiver familiarizado com as funções em fórmulas do Excel, muitas das funções no DAX irão parecer semelhantes. No entanto, as funções DAX são únicas nos seguintes aspetos:

* Uma função DAX referencia sempre uma coluna ou uma tabela completa. Se desejar usar apenas valores específicos de uma tabela ou coluna, é possível adicionar filtros à fórmula.
* Se precisar de personalizar cálculos linha por linha, o DAX fornece funções que permitem usar o valor da linha atual ou um valor relacionado como um tipo de argumento, para realizar cálculos que variam de acordo com o contexto. Irá aprender mais sobre o contexto posteriormente.
* O DAX inclui várias funções que devolvem uma tabela em vez de um valor. A tabela não é apresentada, mas é utilizada para fornecer informações de entrada a outras funções. Por exemplo, é possível recuperar uma tabela e, em seguida, contar os valores distintos contidos nela, ou calcular somas dinâmicas em colunas ou tabelas filtradas.
* O DAX inclui uma variedade de funções de análise de tempo. Estas funções permitem definir ou selecionar intervalos de datas e executar cálculos dinâmicos baseados nesses intervalos. Por exemplo, é possível comparar somas em períodos paralelos.
* O Excel tem uma função popular chamada VLOOKUP. As funções DAX não usam uma célula ou intervalo de células como referência, como a VLOOKUP faz no Excel. As funções DAX usam uma coluna ou tabela como referência. Lembre-se: no Power BI Desktop, está a trabalhar com um modelo de dados relacionais. Procurar valores noutra tabela é fácil e, na maioria dos casos, não tem de criar nenhuma fórmula.
  
  Como pode ver, as funções no DAX podem ajudá-lo a criar fórmulas avançadas. Abordámos apenas as noções básicas das funções. À medida que desenvolver as suas competências com o DAX, irá criar fórmulas ao utilizar muitas funções diferentes. Um dos melhores locais para obter detalhes sobre cada uma das funções DAX é a [Referência de funções DAX](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference).

### <a name="functions-quickquiz"></a>Teste rápido sobre funções
1. Uma função referencia sempre o quê?
2. Uma fórmula pode conter mais de uma função?
3. Que categoria de funções usaria para concatenar duas cadeias de texto numa só cadeia?

As respostas são fornecidas no final deste artigo.

### <a name="context"></a>Contexto
O contexto é um dos conceitos do DAX mais importantes. Existem dois tipos de contexto no DAX: o contexto de linha e o contexto de filtro. Primeiro, vamos analisar primeiro o contexto de linha.

**Contexto de linha**

É mais fácil pensar no contexto de linha como a linha atual. Aplica-se sempre que uma fórmula tem uma função que utiliza filtros para identificar uma única linha numa tabela. A função aplicará inerentemente um contexto de linha a cada linha da tabela que essa função está a filtrar. Este tipo de contexto de linha geralmente aplica-se a medidas.

**Contexto de filtro**

O contexto de filtro é um pouco mais difícil de perceber do que o contexto de linha. É mais fácil pensar no contexto de filtro como: um ou mais filtros aplicados num cálculo que determina um resultado ou um valor.

O contexto de filtro não existe em vez do contexto de linha, mas aplica-se adicionalmente ao contexto de linha. Por exemplo, para restringir ainda mais os valores a serem incluídos num cálculo, pode aplicar um contexto de filtro que, além de especificar o contexto de linha, também especifica um determinado valor (filtro) nesse contexto de linha.

O contexto de filtro é visto facilmente nos seus relatórios. Por exemplo, ao adicionar TotalCost a uma visualização e, em seguida, Year e Region, está a definir um contexto de filtro que seleciona um subconjunto de dados com base num determinado ano e região.

Por que razão o contexto de filtro é tão importante no DAX? A razão é que, embora o contexto de filtro possa ser aplicado mais facilmente pela adição de campos a uma visualização, este também pode ser aplicado numa fórmula DAX pela definição de um filtro com funções como ALL, RELATED, FILTER, CALCULATE, por relações e por outras medidas e colunas. Por exemplo, vejamos a seguinte fórmula numa medida chamada Store Sales:

![Medida Store Sales](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Para perceber melhor esta fórmula podemos decompô-la, de modo muito similar ao que ocorre noutras fórmulas.

Esta fórmula inclui os seguintes elementos de sintaxe:

**A.** O nome da medida: **Store Sales**.

**B.** O operador de sinal de igual ( **=** ), que indica o início da fórmula.

**C.** A função **CALCULATE**, que avalia uma expressão, como um argumento, num contexto que é modificado pelos filtros especificados.

**D.** Os parênteses **()** , que envolvem uma expressão que contém um ou mais argumentos.

**E.** Uma medida **[Total Sales]** na mesma tabela como uma expressão. A medida Total Sales tem a fórmula: =SUM(Sales[SalesAmount]).

**F.** Uma vírgula ( **,** ), que separa o primeiro argumento de expressão do argumento de filtro.

**G.** A coluna referenciada completamente qualificada, **Channel[ChannelName]** . Este é o nosso contexto de linha. Cada linha nesta coluna especifica um canal, como Store ou Online.

**H.** O valor específico **Store** como um filtro. Este é o nosso contexto de filtro.

Esta fórmula garante que somente valores de vendas definidos pela medida Total Sales são calculados para linhas na coluna Channel[ChannelName], com o valor *Store* utilizado como um filtro.

Como pode imaginar, a capacidade de definir o contexto de filtro numa fórmula apresenta funcionalidades incríveis e poderosas. A capacidade de referenciar um determinado valor numa tabela relacionada é apenas um exemplo. Não se preocupe se não entender totalmente o contexto já. Quando criar as suas próprias fórmulas, entenderá melhor o contexto e a razão pela qual é tão importante no DAX.

### <a name="context-quickquiz"></a>Teste rápido de contexto
1. Quais são os dois tipos de contexto?
2. O que é o contexto de filtro?
3. O que é o contexto de linha?

As respostas são fornecidas no final deste artigo.

## <a name="summary"></a>Resumo
Agora que já tem uma noção básica dos conceitos mais importantes do DAX, pode começar a criar as suas próprias fórmulas DAX para medidas. O DAX pode ser realmente um pouco difícil de aprender, mas há muitos recursos disponíveis para si. Depois de ler este artigo e experimentar algumas das suas próprias fórmulas, pode aprender mais sobre outros conceitos e fórmulas do DAX que podem ajudá-lo a resolver os seus problemas empresariais. Há muitos recursos do DAX disponíveis para si: o mais importante é a [Referência do DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx).

Uma vez que o DAX já existe há alguns anos noutras ferramentas de BI da Microsoft, como modelos de tabela do Analysis Services e do Power Pivot, há muitas informações disponíveis. Pode encontrar mais informações em livros, documentos técnicos e blogues tanto da Microsoft como de profissionais de BI de topo. O [Wiki do Centro de Recursos do DAX no TechNet](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) é também um local excelente para começar.

### <a name="quickquiz-answers"></a>Respostas do QuickQuiz
Sintaxe:

1. Valida e insere a medida no modelo.
2. Parêntesis retos [].

Funções:

1. Uma tabela e uma coluna.
2. Yes. Uma fórmula pode conter até 64 funções aninhadas.
3. [Funções de texto](https://msdn.microsoft.com/library/ee634938.aspx).

Contexto:

1. Contexto de linha e contexto de filtro.
2. Um ou mais filtros num cálculo que determina um único valor.
3. A linha atual.

