---
title: 'Tutorial: combinar dados do Excel e de um feed OData no Power BI Desktop'
description: 'Tutorial: combinar dados do Excel e de um feed OData'
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 00c4915df0e18504ec6f5d26540d9289c2f5ddb2
ms.sourcegitcommit: 773ba0d1cc1d1fcee8e666e1c20450f5e343c5c1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
ms.locfileid: "33945992"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: combinar dados de vendas do Excel e de um feed OData

É comum ter dados distribuídos em várias origens de dados, como informações de produtos numa base de dados e informações de vendas noutra. Com o **Power BI Desktop**, pode combinar dados de diferentes origens para criar análises e visualizações de dados interessantes e apelativas. 

Neste tutorial, vai aprender a combinar dados de duas origens de dados: um livro do Excel que inclui informações de produtos e um feed OData que contém dados de ordens. Depois de importar cada conjunto de dados e executar passos de transformação e agregação, utilize dados de ambas as origens para produzir um relatório de análise de vendas com visualizações interativas. Estas técnicas também podem ser aplicadas a consultas do SQL Server, ficheiros CSV e quaisquer outras fontes de dados no Power BI Desktop.

>[!NOTE]
>No Power BI Desktop, geralmente há algumas maneiras de realizar uma tarefa. Por exemplo, muitas seleções de friso também estão disponíveis com um clique no botão direito do rato ou o menu **Mais opções** numa coluna ou célula. Os passos abaixo descrevem vários métodos alternativos. 

## <a name="import-the-product-data-from-excel"></a>Importar os dados de produtos a partir do Excel

Primeiro, importe os dados de produtos a partir do livro Products.xlsx do Excel para o Power BI Desktop.

1. [Transfira o livro do Excel Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) e guarde-o como **Products.xlsx**.
   
2. Selecione a seta para baixo junto a **Obter Dados** no separador **Base** do friso do Power BI Desktop e, em seguida, selecione **Excel** do menu pendente **Mais Comuns**. 
   
   ![Obter dados](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >Também pode selecionar o próprio item **Obter Dados**, ou selecione **Obter Dados** na caixa de diálogo **Introdução** do Power BI e, em seguida, selecione **Excel** ou **Ficheiro** > **Excel** na caixa de diálogo **Obter Dados** e, em seguida, selecione **Ligar**.
   
3. Na caixa de diálogo **Abrir**, navegue até ao ficheiro **Products.xlsx** e selecione-o e, em seguida, selecione **Abrir**.
   
4. No painel **Navegador**, selecione a tabela **Products** e selecione **Editar**.
   
   ![Painel de navegação para Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
Abre-se uma pré-visualização da tabela no **Editor do Power Query**, onde pode aplicar transformações para limpar os dados. 
   
![Editor do Power Query](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>Também pode abrir o **Editor do Power Query** ao selecionar **Editar Consultas** > **Editar Consultas** no friso **Base** no Power BI Desktop, ou ao clicar com o botão direito do rato ou escolher **Mais opções** junto de qualquer consulta em **Vista de Relatório** e selecionar **Editar Consulta**.

## <a name="clean-up-the-products-columns"></a>Limpar as colunas de produtos

O seu relatório combinado utiliza apenas as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** do livro do Excel, pelo que pode remover as outras colunas. 

1. No **Editor do Power Query**, selecione as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** (utilize **Ctrl**+**Clique** para selecionar mais de uma coluna ou **Shift**+**Clique** para selecionar colunas próximas umas das outras).
   
2. Clique com o botão direito do rato em qualquer dos cabeçalhos selecionados e selecione **Remover Outras Colunas** no menu pendente para remover todas, exceto as colunas selecionadas da tabela. 
   Também pode selecionar **Remover Colunas** > **Remover Outras Colunas** no grupo **Gerir Colunas**, no separador do friso **Base**. 
   
   ![Remover outras colunas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>Importar os dados de encomendas de um feed OData

Em seguida, importe os dados de encomendas a partir do feed de OData do sistema de vendas Northwind. 

1. No **Editor do Power Query**, selecione **Nova Origem** e, em seguida, selecione **Feed de OData** no menu pendente **Mais Comuns**. 
   
   ![Obter OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. Na caixa de diálogo **Feed OData**, cole o URL do feed de OData Northwind, `http://services.odata.org/V3/Northwind/Northwind.svc/`, e selecione **OK**.
   
   ![Caixa de diálogo de feed de OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. No painel **Navegador**, selecione a tabela **Ordens** e, em seguida, selecione **OK** para carregar os dados para o **Editor do Power Query**.
   
   ![Painel de navegação para OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >No **Navegador**, pode selecionar qualquer nome de tabela sem selecionar a caixa de verificação para ver uma pré-visualização.

## <a name="expand-the-order-data"></a>Expandir os dados de encomendas

Quando se liga a origens de dados que tenham várias tabelas, tais como bases de dados relacionais ou o feed de OData Northwind, pode utilizar referências entre as tabelas para as suas consultas. A tabela **Ordens** contém referências a várias tabelas relacionadas. Pode adicionar as colunas **ProductID**, **UnitPrice** e **Quantity** da tabela **Order_Details** relacionada à tabela de assunto (**Ordens**) com a operação **Expandir**. 

1. Desloque-se para a direita na tabela **Ordens** até poder ver a coluna **Order_Details**. Tenha em atenção que, em vez de dados, contém referências a outra tabela.
   
   ![Coluna Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Selecione o ícone **Expandir** (![ícone Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) no cabeçalho da coluna **Order_Details**. 
   
3. No menu pendente **Expandir**:
   
   1. Selecione **(Selecionar Todas as Colunas)** para limpar todas as colunas.
      
   2. Selecione **ProductID**, **UnitPrice** e **quantidade** e, em seguida, selecione **OK**.
      
      ![Caixa de diálogo Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

Depois de expandir a tabela **Order_Details**, a coluna **Order_Details** é substituída por três novas colunas da tabela aninhada, e existem novas linhas na tabela para os dados adicionados a partir de cada encomenda. 

![Colunas expandidas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Criar uma coluna calculada personalizada

O Editor do Power Query permite-lhe criar cálculos e campos personalizados para enriquecer os seus dados. Vai criar uma coluna personalizada que calcula o preço total para cada item de linha numa encomenda ao multiplicar o preço unitário por quantidade de itens.

1. No separador do friso **Adicionar Coluna** do Editor do Power Query, selecione **Coluna Personalizada**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. Na caixa de diálogo **Coluna Personalizada**, escreva **LineTotal** no campo **Nome da coluna nova**.

3. No campo **Fórmula de coluna personalizada** após o **=**, introduza **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]**. (Também pode selecionar os nomes de campo na caixa de deslocamento **Colunas disponíveis** e selecione **<< Inserir**, em vez de os escrever.) 
3. Selecione **OK**.
   
   ![Caixa de diálogo Coluna Personalizada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

O novo campo **LineTotal** aparece como a última coluna na tabela **Ordens**.

## <a name="set-the-data-type-for-the-new-field"></a>Definir o tipo de dados para o novo campo

Quando o Editor do Power Query se liga aos dados, determina o melhor tipo de dados para cada campo e apresenta os dados em conformidade. Pode ver os tipos de dados atribuídos aos campos pelos ícones nos cabeçalhos, ou em **Tipo de Dados** no grupo **Transformar** do separador do friso **Base**. 

A nova coluna **LineTotal** tem um tipo de dados de **Qualquer**, mas os valores são moeda. Para atribuir um tipo de dados, clique com botão direito do rato no cabeçalho da coluna **LineTotal**, selecione **Alterar Tipo de Dados** na lista pendente e, em seguida, selecione **Número decimal fixo**. 

![Alterar o tipo de dados](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>Também pode selecionar a coluna **LineTotal** e, em seguida, selecionar a seta para baixo junto a **Tipo de Dados** na área **Transformar** do separador do Friso **Base** e, em seguida, selecione **Número decimal fixo**.

## <a name="clean-up-the-orders-columns"></a>Limpar as colunas de ordens

Para fazer com que seja mais fácil trabalhar no seu modelo em relatórios, pode eliminar, mudar o nome e reordenar algumas das colunas.

O relatório vai utilizar apenas as colunas **OrderDate**, **ShipCity**, **ShipCountry**, **Order_Details.ProductID**, **Order_Details.UnitPrice** e **Order_Details.Quantity**. Pode selecionar estas colunas e utilizar **Remover Outras Colunas** como fez com os dados do Excel, ou pode selecionar todas as colunas exceto as que estão listadas, clique com o botão direito do rato numa das colunas selecionadas e selecione **Remover Colunas** para as remover todas. 

Pode tornar as colunas **Order_Details.ProductID**, **Order_Details.UnitPrice** e **Order_Details.Quantity** mais fáceis de identificar através da remoção de *Order_Details.* prefixos dos nomes das colunas. Para mudar o nome das colunas para **ProductID**, **UnitPrice** e **Quantity**, respetivamente:

1. Faça duplo clique ou toque sem soltar no cabeçalho de cada coluna, ou clique com o botão direito do rato no cabeçalho da coluna e selecione **Mudar o nome** no menu pendente. 
2. Elimine o prefixo *Order_Details.* de cada nome e, em seguida, prima **Enter**.

Finalmente, para tornar a coluna **LineTotal** mais fácil de aceder, arraste e largue-a à esquerda, imediatamente à direita da coluna **ShipCountry**.

![Tabela limpa](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>Rever os passos da consulta

À medida que formou e transformou os dados no Editor do Power Query, cada passo foi registado na área **Passos Aplicados** do painel **Definições da Consulta** no lado direito do Editor do Power Query. Pode recuar através dos Passos Aplicados para rever as alterações realizadas e editar, eliminar ou reorganizar as mesmas, se necessário (embora tal possa ser arriscado, uma vez que os passos anteriores à alteração podem impedir passos posteriores). 

Selecione cada uma das suas consultas na lista **Consultas** no lado esquerdo do Editor do Power Query e reveja os **Passos Aplicados** nas **Definições da Consulta**. Depois de aplicar as transformações de dados anteriores, os Passos Aplicados das suas duas consultas devem ter o seguinte aspeto:

![Passos Aplicados da consulta de produtos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Passos Aplicados da consulta de encomendas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>Subjacentes aos Passos Aplicados estão as fórmulas escritas na **Linguagem do Power Query**, também conhecida como a linguagem **M**. Para ver e editar as fórmulas, selecione **Editor Avançado** no grupo **Consulta** do separador Base do friso. 

## <a name="import-the-transformed-queries"></a>Importar as consultas transformadas

Quando estiver satisfeito com os seus dados transformados, selecione **Fechar e Aplicar** > **Fechar e Aplicar** no grupo **Fechar** do separador do friso **Base** para importar os dados para o Power BI Desktop Report View. 

![Fechar e Aplicar](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Depois de os dados serem carregados, as consultas são apresentadas na lista **Campos** na Vista Relatório do Power BI Desktop.

![Consultas na lista de Campos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Gerir a relação entre os conjuntos de dados

O Power BI Desktop não requer que combine consultas para reportar informações sobre as mesmas. No entanto, pode utilizar as relações entre os conjuntos de dados, com base nos campos que tenham em comum, para expandir e enriquecer os seus relatórios. O Power BI Desktop pode detetar relações automaticamente, ou o utilizador pode criá-las na caixa de diálogo **Gerir Relações** do Power BI Desktop. Para obter mais detalhes sobre as relações no Power BI Desktop, veja [Criar e gerir relações](desktop-create-and-manage-relationships.md).

Os conjuntos de dados Encomendas e Produtos neste tutorial partilham um campo *ProductID* comum, pelo que não existe uma relação entre os mesmos com base nessa coluna. 

1. Na Vista de Relatório do Power BI Desktop, selecione **Gerir Relações** na área **Relações** do separador do friso **Base**.
   
   ![Friso Gerir Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. Na caixa de diálogo **Gerir Relações**, tenha em atenção que o Power BI Desktop já tem detetada e listada uma relação ativa entre as tabelas Produtos e Encomendas. Para visualizar a relação, selecione **Editar**. 
   
   ![Caixa de diálogo Gerir Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   A caixa de diálogo **Editar relação** é apresentada e mostra detalhes sobre a relação.  
   
   ![Caixa de diálogo Editar Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. O Power BI Desktop detetou automaticamente a relação de forma correta, pelo que pode selecionar **Cancelar** e, em seguida, **Fechar** para sair das caixas de diálogo da relação.

Também pode visualizar e gerir as relações entre as suas consultas ao selecionar a vista de **Relação** no lado esquerdo da janela do Power BI Desktop. Faça duplo clique na seta na linha que liga as duas consultas para abrir a caixa de diálogo **Editar Relação** e visualize ou altere a relação. 

![Vista de Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Para voltar à Vista de Relatório da Vista de Relações, selecione o ícone **Vista de Relatório**. 

![Ícone de Vista de Relatório](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Criar visualizações com os seus dados

Na Vista de Relatório do Power BI Desktop, pode criar diversas visualizações para obter informações dos seus dados. Pode criar relatórios com várias páginas, e cada página pode ter vários elementos visuais. O utilizador (e outros) pode interagir com as suas visualizações para ajudar a analisar e compreender os seus dados. Para obter mais informações sobre a visualização e edição de relatórios no Serviço Power BI (o seu site), veja [Editar um Relatório](service-interact-with-a-report-in-editing-view.md).

Pode utilizar ambos os conjuntos de dados e a relação entre eles, para ajudar a visualizar e analisar os seus dados de vendas. 

Primeiro, crie um gráfico de colunas empilhadas que utilize os campos de ambas as consultas para mostrar a quantidade de cada produto encomendado. 

1. Selecione o campo **Quantidade** em **Encomendas** no painel **Campos** à direita, ou arraste-o para um espaço em branco na tela. Esta ação cria um gráfico de colunas empilhadas com a quantidade total de todos os produtos encomendados. 
   
2. Selecione **ProductName** em **Produtos** no painel **Campos** ou arraste-o para o gráfico, para mostrar a quantidade de cada produto encomendado. 
   
3. Para ordenar os produtos dos mais encomendados para os menos encomendados, selecione as reticências **Mais opções** (**...**) no canto superior direito da visualização e, em seguida, selecione **Ordenar por Quantidade**.
   
4. Utilize as alças nos cantos do gráfico para o ampliar, para que fiquem visíveis mais nomes de produtos. 
   
   ![Gráfico de barras Quantidade por ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

Em seguida, criar um gráfico que mostre as quantias em dólares das encomendas (**LineTotal**) ao longo do tempo (**OrderDate**). 

1. Sem nada selecionado na tela, selecione **LineTotal** em **Encomendas** no painel **Campos**, ou arraste-o para um espaço em branco na tela. O gráfico de colunas empilhadas mostra a quantia total em dólares de todas as encomendas. 
   
2. Com o gráfico selecionado, selecione **OrderDate** em **Encomendas**, ou arraste-o para o gráfico. O gráfico mostra agora os totais de linhas para cada data de encomenda. 
   
3. Redimensione a visualização ao arrastar os cantos para poder ver mais dados. 
   
   ![Gráfico de linhas LineTotals por OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Se apenas vir Anos no gráfico (apenas pontos de três dados), clique na seta pendente junto a **OrderDate** no campo **Eixo** do painel **Visualizações** e selecione **OrderDate** em vez de **Hierarquia de Data**. 

Finalmente, crie uma visualização de mapa que apresente as quantidades de encomendas de cada país. 

1. Sem nada selecionado na tela, selecione **ShipCountry** em **Encomendas** no painel **Campos**, ou arraste-o para um espaço em branco na tela. O Power BI Desktop deteta que os dados são nomes de países e cria automaticamente uma visualização de mapa, com um ponto de dados para cada país que tinha encomendas. 
   
2. Para fazer com que os tamanhos dos pontos de dados reflitam as quantidades de encomendas de cada país, arraste o campo **LineTotal** para o mapa (ou arraste-o para **Arrastar campos de dados para aqui** em **Tamanho**, na metade inferior do painel **Visualizações**). Os tamanhos dos círculos no mapa passam a refletir as quantias em dólares das encomendas de cada país. 
   
   ![Visualização de mapa LineTotals por ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagir com os elementos visuais do seu relatório para analisar com mais profundidade

O Power BI Desktop permite revelar mais tendências ao interagir com elementos visuais que realizam ações cruzadas de realce e filtragem entre si. Para obter mais informações, veja [Filtragem e Realce em Relatórios](power-bi-reports-filters-and-highlighting.md). 

Devido à relação entre as suas consultas, as interações com uma visualização vão afetar todas as outras visualizações na página. 

Na visualização de mapa, selecione círculo centrado no **Canadá**. Tenha em atenção que as outras duas visualizações filtram para destacar os totais das linhas e as quantidades de encomendas apenas para o Canadá.

![Dados de vendas filtrados para o Canadá](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Se selecionar um dos produtos no gráfico **Quantidade por ProductName**, o mapa e o gráfico de data filtram para refletir os dados desse produto e, se selecionar uma das datas no gráfico **LineTotal por OrderDate**, o mapa e o gráfico de produto filtram para mostrar os dados dessa data. 
>[!TIP]
>Para anular uma seleção, selecione-a novamente ou selecione uma das outras visualizações. 

## <a name="complete-the-sales-analysis-report"></a>Concluir o relatório de análise de vendas

O seu relatório concluído combina dados do ficheiro Products.xlsx do Excel e o feed OData Northwind em elementos visuais que ajudam a analisar as informações de encomendas de vários países, períodos de tempo e produtos. Quando o seu relatório estiver pronto, pode [carregá-lo para o serviço Power BI](desktop-upload-desktop-files.md) para o partilhar com outros utilizadores do Power BI.

## <a name="next-steps"></a>Próximos passos
* [Ler outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Ver vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visitar o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Ler o Blogue do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)