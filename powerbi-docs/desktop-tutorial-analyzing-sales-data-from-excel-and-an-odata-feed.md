---
title: 'Tutorial: Analisar dados de vendas do Excel e de um feed OData no Power BI Desktop'
description: 'Tutorial: analisar dados de vendas do Excel e de um feed OData'
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 03c5afae78e1688cadfdef9c0a96ca9f24247e12
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="tutorial-analyzing-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: analisar dados de vendas do Excel e de um feed OData
Com o **Power BI Desktop**, pode ligar a todos os tipos de origens de dados diferentes, combinar e moldá-los de forma a facilitar a criação de visualizações e análises de dados interessantes e apelativas. Neste tutorial, aprenderá a combinar dados de duas origens de dados. 

É comum ter dados distribuídos em várias origens de dados, como informações de produtos numa base de dados e informações de vendas noutra. As técnicas que aprenderá neste documento incluem um livro do Excel e um feed OData, mas estas técnicas podem ser aplicadas também a outras origens de dados, como consultas do SQL Server, ficheiros CSV ou qualquer origem de dados no Power BI Desktop.

Neste tutorial, importará dados do Excel (inclui informações de produto) e do feed OData (que contém dados de encomendas). Efetuará passos de transformação e agregação, além de combinar dados de ambas as origens, para produzir um relatório **Total de Vendas por Produto e Ano** que inclua visualizações interativas. 

O relatório final será semelhante ao seguinte:

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

Para seguir os passos neste tutorial, precisa do livro Produtos, que pode transferir**:**[ clique](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)[aqui](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)[ para transferir](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**[Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**[. ](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)

Na caixa de diálogo **Guardar Como**, dê o nome **Products.xlsx** ao ficheiro.

## <a name="task-1-get-product-data-from-an-excel-workbook"></a>Tarefa 1: obter dados de produtos de um livro do Excel
Nesta tarefa, importará produtos do ficheiro Products.xlsx para o Power BI Desktop.

### <a name="step-1-connect-to-an-excel-workbook"></a>Passo 1: ligar a um livro do Excel
1. Inicie o Power BI Desktop.
2. No friso Base, selecione **Obter Dados**. O Excel é uma das ligações de dados **Mais Comum**, pelo que pode selecioná-lo diretamente a partir do menu **Obter Dados**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
3. Se selecionar diretamente o botão Obter Dados, também pode selecionar **Ficheiro \> Excel** e selecionar **Ligar**.
4. Na caixa de diálogo **Abrir Ficheiro**, selecione o ficheiro **Products.xlsx**.
5. No painel **Navegador**, selecione a tabela **Products** e selecione **Editar**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

### <a name="step-2-remove-other-columns-to-only-display-columns-of-interest"></a>Passo 2: remover outras colunas para apresentar apenas as colunas de interesse
Neste passo, remova todas as colunas, exceto **ProductID**, **ProductName**, **UnitsInStock** e **QuantityPerUnit**. No Power BI Desktop, geralmente há algumas maneiras de realizar a mesma tarefa. Por exemplo, vários botões no friso também podem ser obtidos através do menu de contexto numa coluna ou célula.

O Power BI Desktop inclui um Editor de Consultas, que é onde formata e transforma as suas ligações de dados. O Editor de Consultas é aberto automaticamente quando selecionar **Editar** no **Navegador**. Também pode abri-lo ao selecionar **Editar Consultas** no friso **Base** do Power BI Desktop. Os passos seguintes são executados no Editor de Consultas.

1. No Editor de Consultas, selecione as colunas **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** (utilize **Ctrl+Clique** para selecionar mais de uma coluna ou **Shift+Clique** para selecionar colunas próximas umas das outras).
2. Selecione **Remover Colunas** \> **Remover Outras Colunas** no friso ou clique com o botão direito do rato num cabeçalho de coluna e clique em **Remover Outras Colunas**.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_removeothercolumns.png)

### <a name="step-3-change-the-data-type-of-the-unitsinstock-column"></a>Passo 3: alterar o tipo de dados da coluna UnitsInStock
Quando o Editor de Consultas liga aos dados, avalia cada campo e determina o melhor tipo de dados. Para o livro do Excel, os produtos em stock serão sempre um número inteiro, por isso, neste passo, confirme se o tipo de dados da coluna **UnitsInStock** é um Número Inteiro.

1. Selecione a coluna **UnitsInStock**.
2. Selecione o botão pendente **Tipo de Dados** no friso **Base**.
3. Se não for um Número Inteiro, selecione **Número Inteiro** para o tipo de dados no menu pendente (o botão **Tipo de Dados:** também apresenta o tipo de dados da seleção atual).
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_wholenumber.png)      

### <a name="power-bi-desktop-steps-created"></a>Passos criados do Power BI Desktop
À medida que efetua as atividades de consulta no Editor de Consultas, os passos de consulta são criados e listados no painel **Definições de Consulta**, na lista **Passos Aplicados**. Cada passo de consulta tem uma fórmula correspondente, também conhecida como a linguagem "M". Para obter mais informações sobre a linguagem de fórmula "M", veja [Saiba mais sobre as fórmulas do Power BI](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f).

| Tarefa | Passo de consulta | Fórmula |
| --- | --- | --- |
| Ligar a um livro do Excel |Origem |Source{[Name="Products"]}[Data] |
| Promover a primeira linha para títulos de colunas da tabela |FirstRowAsHeader |[Table.PromoteHeaders](https://support.office.com/Article/TablePromoteHeaders-b8eaeb95-042a-42e1-9164-6d3c646acadc "Table.PromoteHeaders") <br /> (Produtos) |
| Remover outras colunas para apresentar apenas as colunas de interesse |RemovedOtherColumns |[Table.SelectColumns](https://support.office.com/Article/TableSelectColumns-20bb9e28-9fd3-4cd2-a21b-97972c82ec22 "Table.SelectColumns")  <br />(FirstRowAsHeader,{"ProductID", "ProductName", "QuantityPerUnit", "UnitsInStock"}) |
| Alterar tipo de dados |Tipo Alterado |Table.TransformColumnTypes(\#"Outras Colunas Removidas",{{"UnitsInStock", Int64.Type}}) |

## <a name="task-2-import-order-data-from-an-odata-feed"></a>Tarefa 2: importar dados de encomendas de um feed OData
Nesta tarefa, poderá inserir dados de encomendas. Este passo representa a ligação a um sistema de vendas. Importe dados para o Power BI Desktop a partir do feed de exemplo OData Northwind no URL seguinte, que pode copiar (e colar) nos passos abaixo: <http://services.odata.org/V3/Northwind/Northwind.svc/> 

### <a name="step-1-connect-to-an-odata-feed"></a>Passo 1: ligar a um feed OData
1. No separador do friso **Base** no Editor de Consultas, selecione **Obter Dados**.
2. Navegue até à origem de dados **Feed OData**.
3. Na caixa de diálogo **Feed OData**, cole o **URL** do feed OData Northwind.
4. Selecione **OK**.
5. No painel **Navegador**, selecione a tabela **Orders** e, em seguida, **Editar**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_odatafeed.png)

>[!NOTE]
>Pode clicar num nome de tabela sem selecionar a caixa de verificação para ver uma pré-visualização.

### <a name="step-2-expand-the-orderdetails-table"></a>Passo 2: expandir a tabela Order\_Details
A tabela **Orders** contém uma referência a uma tabela **Details**. Esta tabela contém os produtos individuais que foram incluídos em cada Encomenda. Quando liga a origens de dados com várias tabelas (como uma base de dados relacional), é possível utilizar estas referências para criar a sua consulta. 

Neste passo, vai expandir a tabela **Order\_Details** relacionada com a tabela **Orders** para combinar as colunas **ProductID**, **UnitPrice** e **Quantity** da tabela **Order\_Details** com a tabela **Orders**. Esta é uma representação dos dados nestas tabelas:

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orderdetails.png)

A operação **Expandir** combina as colunas de uma tabela relacionada com uma tabela de entidade. Quando a consulta é executada, as linhas da tabela relacionada (**Order\_Details**) são combinadas com as linhas da tabela de entidade (**Orders**).

Depois de expandir a tabela **Order\_Details**, são adicionadas três novas colunas e linhas adicionais à tabela **Orders**, uma para cada linha na tabela aninhada ou relacionada.

1. Na **Vista da Consulta**, desloque-se até à coluna **Order\_Details**.
2. Na coluna **Order\_Details**, selecione o ícone de expansão (![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)).
3. No menu pendente **Expandir**:
   1. Selecione **(Selecionar Todas as Colunas)** para limpar todas as colunas.
   2. Selecione **ProductID**, **UnitPrice** e **Quantity**.
   3. Clique em **OK**.
      ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)

### <a name="step-3-remove-other-columns-to-only-display-columns-of-interest"></a>Passo 3: remover outras colunas para apresentar apenas as colunas de interesse
Neste passo, vai remover todas as colunas, exceto **OrderDate, ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** e **Order\_Details.Quantity**. Na tarefa anterior, utilizou **Remover Outras Colunas**. Para esta tarefa, remova as colunas selecionadas.

1. Na **Vista da Consulta**, selecione todas as colunas ao preencher a. e b.:
   1. Clique na primeira coluna (**OrderID**).
   2. Shift+Clique na última coluna (**Shipper**).
   3. Agora que todas as colunas estão selecionadas, utilize Ctrl+Clique para desmarcar as seguintes colunas: **OrderDate**, **ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** e **Order\_Details.Quantity**.
2. Agora que apenas as colunas que queremos remover estão selecionadas, clique com o botão direito do rato em qualquer cabeçalho de coluna selecionado e clique em **Remover Colunas**.

### <a name="step-4-calculate-the-line-total-for-each-orderdetails-row"></a>Passo 4: calcular o total de cada linha de Order\_Details
O Power BI Desktop permite criar cálculos com base nas colunas que está a importar, para enriquecer os dados aos quais liga. Neste passo, vai criar uma **Coluna Personalizada** para calcular o total de cada linha de **Order\_Details**.

Calcular o total de cada linha de **Order\_Details**:

1. No separador do friso **Adicionar Coluna**, clique em **Adicionar** **Coluna Personalizada**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. Na caixa de diálogo **Adicionar Coluna Personalizada**, na caixa de texto **Fórmula de Coluna Personalizada**, introduza **[Order\_Details.UnitPrice] \* [Order\_Details.Quantity]**.
3. Na caixa de texto **Nome da nova coluna**, introduza **LineTotal**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)
4. Clique em **OK**.

### <a name="step-5-set-the-datatype-of-the-linetotal-field"></a>Passo 5: definir o tipo de dados do campo LineTotal
1. Clique com o botão direito do rato na coluna **LineTotal**.
2. Selecione **Alterar Tipo** e **Número Decimal.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

### <a name="step-6-rename-and-reorder-columns-in-the-query"></a>Passo 6: mudar o nome e reordenar colunas na consulta
Nesta passo, ao mudar o nome das colunas finais e ao alterar a respetiva ordem, concluirá o processo de facilitar o trabalho no modelo na criação de relatórios.

1. No **Editor de Consultas**, arraste a coluna **LineTotal** para a esquerda, depois de **ShipCountry**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
2. Remova o prefixo *Order\_Details.* das colunas **Order\_Details.ProductID**, **Order\_Details.UnitPrice** e **Order\_Details.Quantity** ao fazer duplo clique em cada cabeçalho de coluna e ao eliminar esse texto do nome da coluna.

### <a name="power-bi-desktop-steps-created"></a>Passos criados do Power BI Desktop
À medida que efetua as atividades de consulta no Editor de Consultas, os passos de consulta são criados e listados no painel **Definições de Consulta**, na lista **Passos Aplicados**. Cada passo de consulta tem uma fórmula Power Query correspondente, também conhecida como a linguagem "M". Para obter mais informações sobre esta linguagem de fórmula, veja [Saiba mais sobre as fórmulas do Power BI](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f "Saiba mais sobre as fórmulas do Power Query").

| Tarefa | Passo de consulta | Fórmula |
| --- | --- | --- |
| Ligar a um feed OData |Origem |Source{[Name="Orders"]}[Data] |
| Expandir a tabela Order\_Details |Expandir Order\_Details |[Table.ExpandTableColumn](https://support.office.com/Article/TableExpandTableColumn-54903f25-75a2-4a44-a9a3-52a9d895ee98 "Table.ExpandTableColumn") <br /> (Orders, "Order\_Details", {"ProductID", "UnitPrice", "Quantity"}, {"Order\_Details.ProductID", "Order\_Details.UnitPrice", "Order\_Details.Quantity"}) |
| Remover outras colunas para apresentar apenas as colunas de interesse |RemovedColumns |[Table.RemoveColumns](https://support.office.com/Article/TableRemoveColumns-6265190e-2f58-4300-85b8-df88fc1a67d3 "Table.RemoveColumns") <br />(\#"Expand Order\_Details",{"OrderID", "CustomerID", "EmployeeID", "RequiredDate", "ShippedDate", "ShipVia", "Freight", "ShipName", "ShipAddress", "ShipCity", "ShipRegion", "ShipPostalCode", "ShipCountry", "Customer", "Employee", "Shipper"}) |
| Calcular o total de cada linha de Order\_Details |InsertedColumn |[Table.AddColumn](https://support.office.com/Article/TableAddColumn-6c64d0a5-9654-4d15-bfb6-9cc380aaf3c0 "Table.AddColumn") <br /> (RemovedColumns, "Custom", each [Order\_Details.UnitPrice] \* [Order\_Details.Quantity]) |

## <a name="task-3-combine-the-products-and-total-sales-queries"></a>Tarefa 3: combinar as consultas de Produtos e Total de Vendas
O Power BI Desktop não requer que combine consultas para reportar informações sobre as mesmas. Em vez disso, pode criar **Relações** entre conjuntos de dados. Estas relações podem ser criadas em qualquer coluna que seja comum aos seus conjuntos de dados. Para obter mais informações, veja [Criar e gerir relações](desktop-create-and-manage-relationships.md).

Neste tutorial, temos os dados de Encomendas e Produtos que partilham um campo “ProductID” comum; portanto, temos de garantir que há uma relação entre elas no modelo que estamos a utilizar com o Power BI Desktop. Basta especificar no Power BI Desktop que as colunas de cada tabela estão relacionadas (ou seja, são colunas que contêm os mesmos valores). O Power BI Desktop estabelece a direção e a cardinalidade da relação por si. Em alguns casos, até detetará as relações automaticamente.

Nesta tarefa, confirma que foi estabelecida uma relação no Power BI Desktop entre as consultas **Produtos** e **Total de Vendas**.

### <a name="step-1-confirm-the-relationship-between-products-and-total-sales"></a>Passo 1: confirmar a relação entre Produtos e Total de Vendas
1. Em primeiro lugar, precisamos de carregar o modelo que criámos no Editor de Consultas para o Power BI Desktop. No friso **Base** do Editor de Consultas, selecione **Fechar e Carregar**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. O Power BI Desktop carrega os dados das duas consultas.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)      
3. Depois de carregar os dados, selecione o botão **Gerir Relações** no friso **Base**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
4. Selecione o botão **New…** .
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
5. Ao tentar criar a relação, vemos que ela já existe! Conforme mostrado na caixa de diálogo **Criar Relação** (pelas colunas sombreadas), os campos **ProductsID** em cada consulta já têm uma relação estabelecida.
   
    ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)
6. Selecione **Cancelar** e, em seguida, a vista **Relação** no Power BI Desktop.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
7. Vemos o seguinte, que visualiza a relação entre as consultas.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)
8. Quando fizer duplo clique na seta da linha que liga às consultas, é apresentada a caixa de diálogo **Editar Relação**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)
9. Como não é necessário fazer nenhuma alteração, vamos apenas selecionar **Cancelar** para fechar a caixa de diálogo **Editar Relação**.

## <a name="task-4-build-visuals-using-your-data"></a>Tarefa 4: criar elementos visuais com os seus dados
O Power BI Desktop permite criar diversas visualizações para obter informações dos seus dados. Pode criar relatórios com várias páginas, e cada página pode ter vários elementos visuais. Pode interagir com as suas visualizações para ajudar a analisar e compreender os seus dados. Para obter mais informações sobre como editar relatórios, veja [Editar um Relatório](service-interact-with-a-report-in-editing-view.md).

Nesta tarefa, criará um relatório com base nos dados carregados anteriormente. Utilize o painel Campos para selecionar as colunas a partir das quais criará as visualizações.

### <a name="step-1-create-charts-showing-units-in-stock-by-product-and-total-sales-by-year"></a>Passo 1: criar gráficos que mostram as Unidades em Stock por Produto e o Total de Vendas por Ano
Arraste **UnitsInStock** do painel Campo (o painel Campos está à direita do ecrã) para um espaço em branco na tela. Uma visualização de Tabela é criada. Em seguida, arraste ProductName para a caixa Eixo, localizada na metade inferior do painel Visualizações. Em seguida, selecionamos **Ordenar Por \> UnitsInStock** através do marcador no canto superior direito da visualização.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

Arraste **OrderDate** para a tela abaixo do primeiro gráfico e, em seguida, arraste LineTotal (novamente, do painel Campos) para o elemento visual e selecione Gráfico de Linhas. A visualização seguinte é criada.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png)

 Em seguida, arraste **ShipCountry** para um espaço na parte superior direita da tela. Como selecionou um campo geográfico, um mapa foi criado automaticamente. Agora, arraste **LineTotal** para o campo **Values**; os círculos no mapa para cada país são agora relativos em tamanho em relação ao **LineTotal** das encomendas enviadas para esse país.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

### <a name="step-2-interact-with-your-report-visuals-to-analyze-further"></a>Passo 2: interagir com os elementos visuais do seu relatório para analisar com mais profundidade
O Power BI Desktop permite interagir com elementos visuais que realizam ações cruzadas de realce e filtragem entre si para revelar outras tendências. Para obter mais detalhes, veja [Filtragem e Realce em Relatórios](power-bi-reports-filters-and-highlighting.md)

1. Clique no círculo azul claro central em **Canad****a**. Tenha em atenção como os outros elementos visuais são filtrados para mostrar Stock (**ShipCountry**) e Total de Encomendas (**LineTotal**) apenas para o Canadá.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="complete-sales-analysis-report"></a>Relatório de Análise de Vendas completo
Depois de realizar todos estes passos, terá um Relatório de Vendas que combina dados do ficheiro Products.xlsx e do feed OData Northwind. O relatório mostra os elementos visuais que ajudam a analisar informações de vendas de diferentes países. Pode transferir um ficheiro completo do Power BI Desktop para este tutorial [aqui](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Sales_Data.pbix).

## <a name="next-steps"></a>Próximos passos
* [Ler outros tutoriais do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Ver vídeos do Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Visitar o Fórum do Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Ler o Blogue do Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)



