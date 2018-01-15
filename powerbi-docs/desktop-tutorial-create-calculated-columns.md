---
title: 'Tutorial: criar colunas calculadas no Power BI Desktop'
description: 'Tutorial: criar colunas calculadas no Power BI Desktop'
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
ms.openlocfilehash: 9ea93980a095ca4e626b6f8071d044448af59635
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Tutorial: criar colunas calculadas no Power BI Desktop
Às vezes, os dados que está a analisar simplesmente não contêm um campo específico, do qual precisa para obter os resultados que procura. É aqui que entram as colunas calculadas. As colunas calculadas utilizam fórmulas DAX (Data Analysis Expressions) para definir os valores de uma coluna. Esses valores podem ser praticamente qualquer coisa, seja ao reunir valores de texto de duas colunas diferentes em outro lugar no modelo ou calcular um valor numérico por meio de outros valores. Por exemplo, digamos que os seus dados têm colunas Cidade e Estado (como campos na lista Campos), mas deseja um único campo Localização que englobe ambas num único valor como “Miami, FL”. É exatamente para isso que as colunas calculadas servem.

As colunas calculadas são semelhantes a medidas no sentido que ambas se baseiam numa fórmula DAX, mas diferem no modo como são usadas. As medidas são geralmente utilizadas na área Valores de uma visualização para calcular resultados com base em outros campos que tem numa linha de uma tabela, ou numa área de Eixo, Legenda ou Grupo de uma visualização. Por outro lado, as colunas calculadas são usadas quando quer os resultados da coluna contidos numa determinada linha na tabela, ou na área Eixo, Legenda ou Grupo.

Este tutorial serve como guia para que compreenda as colunas calculadas e crie-as mesmo no Power BI Desktop. Destina-se aos utilizadores do Power BI já familiarizados com a utilização do Power BI Desktop para criar modelos mais avançados. Já deve estar familiarizado com a utilização da Consulta para importar dados, trabalhar com múltiplas tabelas relacionadas e adicionar campos ao ecrã Relatório. Se ainda não estiver familiarizado com o Power BI Desktop, não deixe de conferir a [Introdução ao Power BI Desktop](desktop-getting-started.md).

Para concluir os passos neste tutorial, precisa de transferir o ficheiro [Exemplo de Vendas da Contoso para o Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip). Trata-se do mesmo ficheiro de exemplo utilizado no tutorial [Criar suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md). Já inclui dados de vendas da empresa fictícia, Contoso, Inc. Já que os dados no ficheiro foram importados de uma base de dados, não vai conseguir ligar-se à fonte de dados nem vê-los no Editor de Consulta. Quando tiver o ficheiro no seu próprio computador, avance e abra-o no Power BI Desktop.

## <a name="lets-create-a-calculated-column"></a>Vamos criar uma coluna calculada
Vamos supor que desejamos ver categorias de produtos juntamente com subcategorias de produtos num único valor em linhas, como Telemóveis – Acessórios, Telemóveis – Smartphones e PDAs, etc. Na Exibição de Relatório ou Exibição de Dados (estamos usando a Vista de Relatório aqui), se observarmos nossas tabelas de produtos na lista Campos, veremos que não há nenhum campo que fornece o que queremos. Temos, no entanto, um campo ProductCategory e um campo ProductSubcategory, cada um deles na sua própria tabela.

 ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_nonewcol.png)

Criaremos uma nova coluna calculada, para combinar os valores dessas duas colunas em novos valores para nossa nova coluna. O interessante é que precisamos de combinar dados de duas tabelas diferentes numa única coluna. Como nós vamos utilizar a DAX para criar nossa nova coluna, podemos aproveitar todo o potencial do modelo que já temos, incluindo as relações entre tabelas diferentes já existentes.

### <a name="to-create-a-productfullcategory-column"></a>Para criar uma coluna ProductFullCategory
1.  Clique com o botão direito do mouse na tabela **ProductSubcategory** na lista Campos ou clique na seta para baixo nessa mesma tabela; em seguida, clique em **Nova Coluna**. Isso vai assegurar que a nossa nova coluna seja adicionada à tabela ProductSubcategory.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumn.png)
    
    A barra de fórmulas aparece na parte superior da tela Relatório ou grade de Dados. É ali que podemos mudar o nome da nossa coluna e inserir uma fórmula DAX.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumnformula.png)
    
    Por predefinição, uma nova coluna calculada é nomeada simplesmente como Coluna. Se não mudarmos o seu nome, a próxima coluna que criamos terá como nome Coluna 2, Coluna 3 e assim sucessivamente. Queremos que as nossas colunas sejam identificadas com mais facilidade, então vamos dar um novo nome a nossa nova coluna.
    
2.  Como o nome **Coluna** já está realçado na barra de fórmulas, basta escrever **ProductFullCategory**.
    
    Agora, podemos começar a inserir nossa fórmula. Queremos que os valores na coluna nova comecem com o nome ProductCategory, da tabela ProductCategory. Como esta coluna está numa tabela diferente, mas relacionada, vamos utilizar a função [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) para nos ajudar a obtê-la.
    
3.  Após o sinal de igual, escreva um **R**. Vai ver uma lista suspensa de sugestões aparecer com todas as funções DAX a começar pela letra R. Quanto mais escrevemos, mais a lista de sugestões é dimensionada aproximando-se da função que precisamos. Vai ver uma descrição da função ao lado desta. Selecione **RELATED** ao deslocar para baixo e pressionar Enter.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_1.png)
    
    Um parêntesis de abertura aparece junto com outra lista de sugestões de todas as colunas disponíveis que podemos passar para a função RELATED. Também aparecem uma descrição e detalhes sobre quais os parâmetros esperados.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_2.png)
    
    Uma expressão sempre aparece entre parênteses de abertura e de fechamento. Nesse caso, a nossa expressão vai conter um único argumento passado para a função RELATED: uma coluna relacionada, da qual retornar valores. A lista de colunas é reduzida automaticamente para mostrar somente as colunas relacionadas. Nesse caso, queremos a coluna ProductCategory na tabela ProductCategory.
    
    Selecione **ProductCategory[ProductCategory]**, e, em seguida, escreva um parêntesis de fecho.
    
    > [!TIP]
    > Os erros de sintaxe são causados frequentemente por um parêntesis de fecho deslocado ou em falta. Mas, muitas vezes, o Power BI Desktop adiciona-o se se esquecer.
    > 
    > 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_3.png)
    
4. Queremos adicionar um símbolo de hífen para separar cada valor, portanto, após o parêntesis de fecho da primeira expressão, escreva um espaço, E comercial (&), aspas, espaço, hífen (-), outro espaço, aspas de fecho e, em seguida, outro E comercial. A sua fórmula agora deve ter este aspeto:
    
    **ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &**
    
    > [!TIP]
    > Clique na divisa para baixo do lado direito da barra de fórmulas para aumentar o editor de fórmuls. Clique em Alt + Enter para mover uma linha para baixo e pressione Tab para mudar a posição das coisas.
    > 
    > 
    
5.  Por mim, insira outro parêntesis reto de abertura e selecione a coluna **[ProductSubcategory]** para terminar a fórmula. A sua fórmula deve ter este aspeto:
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_5.png)
    
    Pode ver que não utilizamos outra função RELATED na segunda expressão, chamando a coluna ProductSubcategory. Isso ocorre porque essa coluna já está na mesma tabela em que estamos a criar a nossa nova coluna. Podemos inserir [ProductCategory] com o nome da tabela (totalmente qualificado) ou sem (não qualificado).
    
6.  Complete a fórmula, ao pressionar Enter ou clicar na marca de confirmação na barra de fórmulas. A fórmula é validada e adicionada à lista de campos na tabela **ProductSubcategory** .
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_6.png)
    
    Pode ver que colunas calculadas recebem um ícone especial na lista de campos. Isso mostra que contêm uma fórmula. Elas aparecem assim apenas no Power BI Desktop. No serviço PowerBI.com (o seu site do Power BI), não é possível alterar uma fórmula; portanto, um campo de coluna calculada não tem um ícone.
    
## <a name="lets-add-our-new-column-to-a-report"></a>Vamos adicionar a nossa nova coluna a um relatório
Agora podemos adicionar nossa nova coluna ProductFullCategory ao ecrã de relatório. Vamos examinar SalesAmount por ProductFullCategory.

Arraste a coluna **ProductFullCategory** da tabela **ProductSubcategory** até ao ecrã Relatório e, em seguida, arraste o campo **SalesAmount** da tabela **Sales** até o gráfico.

![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_report_1.png)

## <a name="lets-create-another"></a>Vamos criar mais uma
Agora que sabe como criar uma coluna calculada, vamos criar outra.

O modelo “Exemplo de Vendas da Contoso para o Power BI Designer” contém dados de vendas tanto para repositórios ativos quanto inativos. Queremos garantir que dados mostrados para repositórios inativos sejam identificados como tal. Por isso, queremos um campo chamado Active StoreName. Para fazer isso, criaremos outra coluna. Nesse caso, quando um repositório estiver inativo, queremos que a nossa nova coluna Active StoreName (como um campo) mostre o nome do repositório como "Inactive", mas mostre o verdadeiro nome do repositório quando este for um repositório ativo.

Felizmente, a nossa tabela Stores tem uma coluna chamada Status, com um valor “On” para repositórios ativos e “Off” para repositórios inativos. Podemos testar valores para cada linha na coluna Status, para criar novos valores na nossa nova coluna.

### <a name="to-create-an-active-storename-column"></a>Para criar uma coluna Active StoreName
1.  Crie uma nova coluna calculada chamada **Active StoreName** na tabela **Stores**.
    
    Para esta coluna, a nossa fórmula DAX verifica o estado de cada repositório. Se o estado de um repositório for “On”, a nossa fórmula devolve o nome do repositório. Se o estado for “Off”, o repositório terá o nome "Inactive". Para fazer isso, vamos usar a função lógica [IF](https://msdn.microsoft.com/library/ee634824.aspx) para testar o status das lojas e devolver um valor específico se o resultado for “true” ou “false”.
    
2.  Comece a escrever **IF**. A lista de sugestões mostra o que podemos adicionar. Selecione **IF**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_1.png)
    
    O primeiro argumento para IF é um teste lógico. Queremos testar se um repositório tem ou não um status "On".
    
3.  Escreva um parêntesis de abertura **[**, que nos permite selecionar colunas na tabela Stores. Selecione **[Status]**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_2.png)
    
4.  Logo após **[Status]**, digite **="On"** e, em seguida, escreva uma vírgula (**,**) para inserir o segundo argumento. A dica de contexto sugere que precisamos adicionar o valor quando o resultado é “true”.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_3.png)
    
5.  Se o status do repositório for “On”, queremos que o nome desse repositório seja mostrado. Escreva um parêntesis de abertura **[** e selecione a coluna **[StoreName]** , então escreva outra vírgula para que possamos inserir o nosso terceiro argumento.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step5.png)
    
6.  Precisamos adicionar um valor quando o resultado for “false”; neste caso, queremos que o valor seja **“Inactive”**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step6.png)
    
7.  Complete a fórmula, ao pressionar Enter ou clicar na marca de confirmação na barra de fórmulas. A fórmula é validada e adicionada à lista de campos na tabela Stores.
    
    Assim como ocorre com qualquer outro campo, podemos usar a nossa nova coluna Active StoreName em visualizações. Neste gráfico, os repositórios com um estado “On” são mostrados individualmente por nome, mas os repositórios com um estado “Off” são agrupados juntos e mostrados como “Inactive”. 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_viz.png)
    
## <a name="what-weve-learned"></a>O que aprendemos
As colunas calculadas podem enriquecer nossos dados, facilitando a compreensão das informações. Aprendemos como criar colunas calculadas usando a barra de fórmulas, como usar a lista de sugestões e o melhor modo de nomear nossas novas colunas.

## <a name="next-steps"></a>Próximos passos
Se desejar aprofundar os conhecimentos sobre as fórmulas DAX e criar colunas calculadas com fórmulas DAX mais avançadas, veja [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Este artigo foca-se nos conceitos fundamentais no DAX, como sintaxe, funções e uma compreensão mais abrangente sobre o contexto.

Certifique-se de que adiciona a [Referência ao DAX Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) aos favoritos. É aqui que encontrará informações detalhadas sobre a sintaxe do DAX, operadores e mais de 200 funções DAX.

