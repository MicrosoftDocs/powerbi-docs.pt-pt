---
title: 'Tutorial: Combinar dados do Excel e de um feed OData no Power BI Desktop'
description: 'Tutorial: Combinar dados do Excel e de um feed OData'
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: tutorial
ms.date: 01/17/2020
LocalizationGroup: Learn more
ms.openlocfilehash: 391c8fef1e95aa39ff6dfcd8aab8088f692504e7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404922"
---
# <a name="tutorial-analyze-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: Analisar dados de vendas do Excel e de um feed OData

É comum ter dados em múltiplas origens de dados. Por exemplo, pode ter duas bases de dados, uma para informações sobre o produto e outra para as informações de vendas. Com o *Power BI Desktop*, pode combinar dados de diferentes origens para criar análises e visualizações de dados interessantes e apelativas.

Neste tutorial, irá combinar dados de duas origens de dados:

* Um livro do Excel com informações sobre o produto
* Um feed OData que contém dados de encomendas

Irá importar cada conjunto de dados e efetuar operações de transformação e agregação. Em seguida, irá utilizar as duas origens de dados para produzir um relatório de análise de vendas com visualizações interativas. Mais tarde, pode aplicar estas técnicas a consultas do SQL Server, ficheiros CSV e outras origens de dados no Power BI Desktop.

>[!NOTE]
>No Power BI Desktop, geralmente há algumas maneiras de realizar uma tarefa. Por exemplo, pode clicar com o botão direito do rato ou utilizar um menu **Mais opções** numa coluna ou célula para ver as seleções adicionais do friso. Os passos abaixo descrevem vários métodos alternativos.

## <a name="import-excel-product-data"></a>Importar dados de produtos do Excel

Primeiro, importe os dados de produtos do livro do Excel *Products.xlsx* para o Power BI Desktop.

1. [Transfira o livro do Excel Products.xlsx](https://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) e guarde-o como *Products.xlsx*.

1. Selecione a seta junto a **Obter Dados** no separador **Home Page** do friso do Power BI Desktop e, em seguida, selecione **Excel** no menu **Mais Comuns**.

   ![Obter dados](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)

   >[!NOTE]
   >Também pode selecionar o próprio item **Obter Dados** ou selecionar **Obter Dados** na caixa de diálogo **Introdução** do Power BI e, em seguida, selecionar **Excel** ou **Ficheiro** > **Excel** na caixa de diálogo **Obter Dados** e depois selecionar **Ligar**.

1. Na caixa de diálogo **Abrir**, navegue até ao ficheiro **Products.xlsx** e selecione-o e, em seguida, selecione **Abrir**.

1. No **Navegador**, selecione a tabela **Products** e selecione **Transformar Dados**.

   ![Painel de navegação para Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

É aberta uma pré-visualização da tabela no Editor do Power Query, onde pode aplicar transformações para limpar os dados.

![Editor do Power Query](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)

>[!NOTE]
>Também pode abrir o Editor do Power Query ao selecionar **Editar Consultas** > **Editar Consultas** no friso **Home Page** no Power BI Desktop, ou ao clicar com o botão direito do rato ou selecionar **Mais opções** junto a qualquer consulta na vista de **Relatório** e selecionar **Editar Consulta**.

## <a name="clean-up-the-products-columns"></a>Limpar as colunas de produtos

O seu relatório combinado utiliza as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** do livro do Excel. Pode remover as outras colunas.

1. No Editor do Power Query, selecione as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock**. Pode premir Ctrl para selecionar mais do que uma coluna ou Shift para selecionar colunas próximas umas das outras.

1. Clique com o botão direito do rato num dos cabeçalhos selecionados. Selecione **Remover Outras Colunas** no menu pendente.
   Também pode selecionar **Remover Colunas** > **Remover Outras Colunas** no grupo **Gerir Colunas**, no separador do friso **Base**.

   ![Remover outras colunas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-odata-feeds-order-data"></a>Importar os dados de encomendas do feed OData

Em seguida, importe os dados de encomendas a partir do feed de OData do sistema de vendas Northwind.

1. No Editor do Power Query, selecione **Nova Origem** e, em seguida, no menu **Mais Comuns**, selecione **Feed OData**.

   ![Obter OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)

1. Na caixa de diálogo **Feed OData**, cole o URL do feed OData Northwind, `https://services.odata.org/V3/Northwind/Northwind.svc/`. Selecione **OK**.

   ![Caixa de diálogo de feed OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)

1. No **Navegador**, selecione a tabela **Orders** e, em seguida, selecione **Transformar Dados** para carregar os dados para o Editor do Power Query.

   ![Navegador do OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)

   >[!NOTE]
   >No **Navegador**, pode selecionar qualquer nome de tabela sem selecionar a caixa de verificação para ver uma pré-visualização.

## <a name="expand-the-order-data"></a>Expandir os dados de encomendas

Pode utilizar referências de tabelas para compilar consultas quando se liga a origens de dados que tenham múltiplas tabelas, tais como bases de dados relacionais ou o feed OData Northwind. A tabela **Ordens** contém referências a várias tabelas relacionadas. Pode utilizar a operação expandir para adicionar as colunas **ProductID**, **UnitPrice** e **Quantity** da tabela relacionada **Order_Details** para a tabela de assunto (**Orders**).

1. Desloque-se para a direita na tabela **Ordens** até ver a coluna **Order_Details**. Contém referências a outra tabela e não dados.

   ![Coluna Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/order-details-column.png)

1. Selecione o ícone **Expandir** (![ícone Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) no cabeçalho da coluna **Order_Details**.

1. No menu pendente:

   1. Selecione **(Selecionar Todas as Colunas)** para limpar todas as colunas.

   1. Selecione **ProductID**, **UnitPrice** e **quantidade** e, em seguida, selecione **OK**.

      ![Menu pendente Expandir](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand-drop-down-menu.png)

Depois de expandir a tabela **Order_Details**, três novas colunas de tabela aninhada de tabela substituem a coluna **Order_Details**. Existem novas linhas na tabela para os dados adicionados de cada encomenda.

![Colunas expandidas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expanded-columns.png)

## <a name="create-a-custom-calculated-column"></a>Criar uma coluna calculada personalizada

O Editor do Power Query permite-lhe criar cálculos e campos personalizados para enriquecer os seus dados. Irá criar uma coluna personalizada que multiplica o preço unitário pela quantidade de itens para calcular o preço total para o item de linha de cada encomenda.

1. No Editor do Power Query do separador do friso **Adicionar Coluna**, selecione **Coluna Personalizada**.

   ![Adicionar uma coluna personalizada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/adding-a-custom-column.png)

1. Na caixa de diálogo **Coluna Personalizada**, escreva **LineTotal** no campo **Nome da coluna nova**.

1. No campo **Fórmula de coluna personalizada** a seguir ao **=** , introduza **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . Também pode selecionar os nomes de campo na caixa de deslocamento **Colunas disponíveis** e selecionar **<< Inserir**, em vez de os escrever.

1. Selecione **OK**.

   ![Caixa de diálogo Coluna Personalizada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/custom-column-dialog-box.png)

   O novo campo **LineTotal** aparece como a última coluna na tabela **Ordens**.

## <a name="set-the-new-fields-data-type"></a>Definir o tipo de dados para o novo campo

Quando o Editor do Power Query se liga aos dados, faz uma melhor estimativa sobre o tipo de dados de cada campo para fins de apresentação. Um ícone de cabeçalho indica o tipo de dados atribuído de cada campo. Também pode procurar **Tipo de Dados** no separador do friso **Base** do grupo **Transformar**.

A nova coluna **LineTotal** tem um tipo de dados **Qualquer**, mas tem valores de moeda. Para atribuir um tipo de dados, clique com o botão direito do rato no cabeçalho da coluna **LineTotal**, selecione **Alterar Tipo** no menu pendente e, em seguida, selecione **Número decimal fixo**.

![Alterar o tipo de dados para número decimal fixo](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/change-data-type-to-fixed-decimal.png)

>[!NOTE]
>Também pode selecionar a coluna **LineTotal** e, em seguida, selecionar a seta junto a **Tipo de Dados** na área **Transformar** do separador do friso **Home Page** e, em seguida, selecionar **Número decimal fixo**.

## <a name="clean-up-the-orders-columns"></a>Limpar as colunas de ordens

Para fazer com que seja mais fácil trabalhar no seu modelo em relatórios, pode eliminar, reordenar e mudar o nome de algumas colunas.

O relatório irá utilizar as seguintes colunas:

* **OrderDate**
* **ShipCity**
* **ShipCountry**
* **Order_Details.ProductID**
* **Order_Details.UnitPrice**
* **Order_Details.Quantity**
* **LineTotal**

Selecione estas colunas e utilize a opção **Remover Outras Colunas** como fez com os dados do Excel. Em alternativa, pode selecionar as colunas não listadas, clicar com o botão direito do rato numa delas e selecionar **Remover Colunas**.

Pode mudar o nome das colunas antecedidas por "**Order_Details.** " para as tornar mais fáceis de ler:

1. Faça duplo clique ou toque sem soltar no cabeçalho de cada coluna, ou clique com o botão direito do rato no cabeçalho da coluna e selecione **Mudar o nome** no menu pendente.

1. Elimine o prefixo **Order_Details.** de cada nome.

Finalmente, para tornar a coluna **LineTotal** mais fácil de aceder, arraste e largue-a à esquerda, imediatamente à direita da coluna **ShipCountry**.

![Tabela limpa](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/cleaned-up-table.png)

## <a name="review-the-query-steps"></a>Rever os passos da consulta

As ações de Editor do Power Query para formatar e transformar dados são registadas. Cada ação aparece à direita no painel **Definições da Consulta**, em **Passos Aplicados**. Pode recuar nos **Passos Aplicados** para rever os seus passos e editar, eliminar ou reorganizá-los, se for necessário. No entanto, é arriscado alterar passos anteriores, dado que podem interromper passos posteriores.

Selecione cada uma das suas consultas na lista **Consultas** no lado esquerdo do Editor do Power Query e reveja os **Passos Aplicados** nas **Definições da Consulta**. Depois de aplicar as transformações de dados anteriores, os **Passos Aplicados** das suas duas consultas deverão ter o seguinte aspeto:

![Passos Aplicados da consulta de produtos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/products-query-applied-steps.png) &nbsp;&nbsp; ![Passos Aplicados da consulta de encomendas](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orders-query-applied-steps.png)

>[!TIP]
>Subjacentes aos Passos Aplicados, estão as fórmulas escritas na *Linguagem do Power Query*, também conhecida como a [linguagem M](/powerquery-m/power-query-m-reference). Para ver e editar as fórmulas, selecione **Editor Avançado** no grupo **Consulta** do separador **Home Page** do friso.

## <a name="import-the-transformed-queries"></a>Importar as consultas transformadas

Quando estiver satisfeito com os seus dados transformados e preparado para os importar para a Vista de **Relatório** do Power BI Desktop, selecione **Fechar e Aplicar** > **Fechar e Aplicar** no grupo **Fechar** do separador do friso **Home Page**.

![Fechar e Aplicar](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Depois de os dados serem carregados, as consultas são apresentadas na lista **Campos** na Vista de **Relatório** do Power BI Desktop.

![Consultas na lista de Campos](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/queries-in-fields-list.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Gerir a relação entre os conjuntos de dados

Com o Power BI Desktop, não tem de combinar consultas para comunicar informações sobre as mesmas. No entanto, pode utilizar as relações entre os conjuntos de dados, com base nos campos que tenham em comum, para expandir e enriquecer os seus relatórios. O Power BI Desktop pode detetar relações automaticamente, ou o utilizador pode criá-las na caixa de diálogo **Gerir Relações** do Power BI Desktop. Para obter mais informações, veja [Criar e gerir relações no Power BI Desktop](../transform-model/desktop-create-and-manage-relationships.md).

O campo partilhado `ProductID` cria uma relação entre os conjuntos de dados `Orders` e `Products` deste tutorial.

1. Na vista **Relatório** do Power BI Desktop, selecione **Gerir Relações** na área **Relações** do separador do friso **Home Page**.

   ![Friso Gerir Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)

1. Na caixa de diálogo **Gerir Relações**, pode ver que o Power BI Desktop já tem detetada e listada uma relação ativa entre as tabelas **Products** e **Orders**. Para visualizar a relação, selecione **Editar**.

   ![Caixa de diálogo Gerir Relações](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)

   **Editar relação** é apresentado e mostra detalhes sobre a relação.  

   ![Caixa de diálogo Editar Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)

1. O Power BI Desktop detetou automaticamente a relação de forma correta, pelo que pode selecionar **Cancelar** e, em seguida, **Fechar**.

No Power BI Desktop, no lado esquerdo, selecione **Modelo** para ver e gerir relações de consulta. Faça duplo clique na seta na linha que liga as duas consultas para abrir a caixa de diálogo **Editar Relação** e veja ou altere a relação.

![Vista de Relação](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Para voltar à vista de **Relatório** da vista de **Modelo**, selecione o ícone **Relatório**.

![Ícone de Vista de Relatório](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Criar visualizações com os seus dados

Pode criar visualizações diferentes na Vista de Relatório do Power BI Desktop para obter informações de dados. Os relatórios podem ter múltiplas páginas e cada página pode ter múltiplos elementos visuais. Você e outras pessoas podem interagir com as visualizações para ajudar a analisar e compreender os dados. Para obter mais informações, veja [Interagir com um relatório na Vista de Edição no serviço Power BI](../create-reports/service-interact-with-a-report-in-editing-view.md).

Pode utilizar ambos os conjuntos de dados e a relação entre eles, para ajudar a visualizar e analisar os seus dados de vendas.

Primeiro, crie um gráfico de colunas empilhadas que utilize os campos de ambas as consultas para mostrar a quantidade de cada produto encomendado.

1. Selecione o campo **Quantidade** em **Encomendas** no painel **Campos** à direita, ou arraste-o para um espaço em branco na tela. É criado um gráfico de colunas empilhadas que mostra a quantidade total de todos os produtos encomendados.

1. Para mostrar a quantidade de cada produto encomendado, selecione **ProductName** em **Produtos**, no painel **Campos**, ou arraste-o para o gráfico.

1. Para ordenar os produtos dos mais encomendados para os menos encomendados, selecione as reticências **Mais opções** ( **...** ) no canto superior direito da visualização e, em seguida, selecione **Ordenar por Quantidade**.

1. Utilize as alças nos cantos do gráfico para o ampliar, para que fiquem visíveis mais nomes de produtos.

   ![Gráfico de barras Quantidade por ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/quantity-by-productname-bar-chart.png)

Em seguida, criar um gráfico que mostre as quantias em dólares das encomendas (**LineTotal**) ao longo do tempo (**OrderDate**).

1. Sem nada selecionado na tela, selecione **LineTotal** em **Encomendas** no painel **Campos**, ou arraste-o para um espaço em branco na tela. O gráfico de colunas empilhadas mostra a quantia total em dólares de todas as encomendas.

1. Selecione o gráfico de colunas empilhadas e, em seguida, selecione **OrderDate**, em **Encomendas**, ou arraste-o para o gráfico. O gráfico mostra agora os totais de linhas para cada data de encomenda.

1. Arraste os cantos para redimensionar a visualização e ver mais dados.

   ![Gráfico de linhas LineTotals por OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-orderdate-line-chart.png)

   >[!TIP]
   >Se vir apenas **Anos** no gráfico e apenas três pontos de dados, selecione a seta junto a **OrderDate** no campo **Eixo** do painel **Visualizações** e selecione **OrderDate** em vez de **Hierarquia de Dados**.

Finalmente, crie uma visualização de mapa que apresente as quantidades de encomendas de cada país.

1. Sem nada selecionado na tela, selecione **ShipCountry** em **Encomendas** no painel **Campos**, ou arraste-o para um espaço em branco na tela. O Power BI Desktop deteta que os dados são nomes de países. Em seguida, cria automaticamente uma visualização de mapa, com um ponto de dados para cada país com encomendas.

1. Para fazer com que os tamanhos dos pontos de dados reflitam as quantidades de encomendas de cada país, arraste o campo **LineTotal** para o mapa. Também pode arrastá-lo para **Arrastar os campos de dados para aqui** em **Tamanho**, no painel **Visualizações**. Os tamanhos dos círculos no mapa passam a refletir as quantias em dólares das encomendas de cada país.

   ![Visualização de mapa LineTotals por ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-shipcountry-map-visualization.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagir com os elementos visuais do seu relatório para analisar com mais profundidade

No Power BI Desktop, pode interagir com elementos visuais que realizam ações cruzadas de realce e filtragem entre si para revelar outras tendências. Para obter mais informações, veja [Filtros e realce em relatórios do Power BI](../create-reports/power-bi-reports-filters-and-highlighting.md).

Devido à relação entre as suas consultas, as interações com uma visualização afetam todas as outras visualizações na página.

Na visualização de mapa, selecione círculo centrado no **Canadá**. As outras duas visualizações filtram para destacar as quantidades de encomendas e os totais das linhas para o Canadá.

![Dados de vendas filtrados para o Canadá](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/sales-data-filtered-for-canada.png)

Selecione um produto de gráfico **Quantidade por ProductName** para ver o mapa e o filtro de gráfico de data para refletir os dados desse produto. Selecione uma data de gráfico **LineTotal por OrderDate** para ver o mapa e o filtro de gráfico de produto para mostrar os dados dessa data.

>[!TIP]
>Para anular uma seleção, selecione-a novamente ou selecione uma das outras visualizações.

## <a name="complete-the-sales-analysis-report"></a>Concluir o relatório de análise de vendas

O seu relatório concluído combina dados do ficheiro *Products.xlsx* do Excel e do feed OData Northwind em elementos visuais que o ajudam a analisar as informações de encomendas de vários países, intervalos de tempo e produtos. Quando o seu relatório estiver pronto, pode [carregá-lo para o serviço Power BI](../create-reports/desktop-upload-desktop-files.md) para o partilhar com outros utilizadores do Power BI.

## <a name="next-steps"></a>Próximos passos

* [Microsoft Learn para Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
* [Ver vídeos do Power BI Desktop](../fundamentals/desktop-videos.md)
* [Visitar o Fórum do Power BI](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Ler o Blogue do Power BI](https://go.microsoft.com/fwlink/?LinkID=519327)