---
title: 'Tutorial: De um modelo dimensional a um relatório incrível no Power BI Desktop'
description: Neste tutorial, começará com um modelo dimensional e irá criar um relatório apelativo do início ao fim em 20 minutos.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/11/2021
LocalizationGroup: Reports
ms.openlocfilehash: f5d35d7fc189f055a6f51e493fd313eb31f0564f
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565975"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>Tutorial: De um modelo dimensional a um relatório incrível no Power BI Desktop 

Neste tutorial, começará com um modelo dimensional e irá criar um relatório apelativo do início ao fim em 45 minutos.

Trabalha na AdventureWorks e o seu gestor quer ver um relatório sobre os seus últimos números de vendas. Por isso, pediu um resumo executivo de: 

- Em que dia de fevereiro de 2019 efetuou mais vendas? 
- Em que país está a empresa a registar mais sucesso? 
- Em que categoria de produtos e tipos de negócio de revendedores deve a empresa continuar a investir? 

Com o nosso [Livro do Excel de exemplo de Sales (Vendas) da AdventureWorks](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx), podemos criar este relatório num instante. Eis como será o relatório final. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Relatório concluído da AdventureWorks.":::

Quer ver o resultado final? Também pode transferir o [ficheiro .pbix do Power BI concluído](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix).

Vamos começar! 

Neste tutorial, vai aprender a:

> [!div class="checklist"]
> * Preparar os dados com algumas transformações
> * Criar um relatório com um título, três elementos visuais e uma segmentação de dados
> * Publicar o relatório no serviço Power BI para poder partilhá-lo com os seus colegas

## <a name="prerequisites"></a>Pré-requisitos

- Antes de começar, tem de [transferir o Power BI Desktop](../fundamentals/desktop-get-the-desktop.md). 
- Se está a planear publicar o relatório no serviço Power BI e ainda não se inscreveu, [inscreva-se numa avaliação gratuita](../fundamentals/service-self-service-signup-for-power-bi.md). 

## <a name="get-data-download-the-sample"></a>Obter dados: Transferir o exemplo 

1. Transfira o [Livro do Excel de exemplo de Sales (Vendas) da AdventureWorks](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx). 

1. Abra o Power BI Desktop. 

1. Na secção **Dados** do friso **Base**, selecione **Excel**. 

1. Navegue até ao local onde guardou o livro de exemplo e selecione **Abrir**. 

## <a name="prepare-your-data"></a>Preparar os dados 

No painel do Navegador, tem a opção de *transformar* ou *carregar* os dados. O Navegador fornece uma pré-visualização dos dados para poder verificar que tem o intervalo de dados correto. Os tipos de dados numéricos estão em itálico. Neste tutorial, vamos transformar os dados antes de os carregar.

Selecione todas as tabelas e selecione  **Transformar Dados**. Certifique-se de que não seleciona as folhas (identificadas com *_data*). 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="Carregar tabelas no Navegador.":::

Verifique se os tipos de dados das colunas correspondem aos da tabela a seguir. Para fazer alterações, selecione uma consulta e, em seguida, selecione uma ou mais colunas.

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="Verificação dos tipos de dados das colunas.":::

No separador **Base**, selecione **Tipo de Dados** e, em seguida, selecione o tipo de dados adequado na tabela.

|Consulta  |Coluna  |Tipo de dados  |
|---------|---------|---------|
|Customer  |  CustomerKey | Número Inteiro |
|Date | DateKey |    Número Inteiro     |
|     | Date | Date      |
|     | MonthKey  | Número Inteiro |
|Produto  | ProductKey | Número Inteiro  | 
|     | Standard Cost | Número Decimal  | 
|     | Preço da Lista | Número Decimal  | 
|Reseller  | ResellerKey | Número Inteiro  | 
|Sales   | SalesOrderLineKey | Número Inteiro  | 
|     | ResellerKey  | Número Inteiro  | 
|     | CustomerKey | Número Inteiro  | 
|     | ProductKey  | Número Inteiro  | 
|     | OrderDateKey | Número Inteiro  | 
|     | DueDateKey  | Número Inteiro  | 
|     | ShipDateKey | Número Inteiro  | 
|     | SalesTerritoryKey | Número Inteiro  | 
|     | Quantidade de Encomendas   | Número Inteiro  | 
|     | Preço Unitário  | Número Decimal  | 
|     | Extended Amount  | Número Decimal  | 
|     | Percentagem de Desconto do Preço Unitário | Percentagem  | 
|     | Product Standard Cost | Número Decimal  | 
|     | Custo Total do Produto | Número Decimal  | 
|     | Sales Amount | Número Decimal  | 
| SalesTerritory  | SalesTerritoryKey | Número Inteiro  | 
|  SalesOrder   |  SalesOrderLineKey | Número Inteiro  | 

Novamente no separador **Base** , selecione **Fechar e Aplicar**. 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="Botão Fechar e Aplicar do Power Query.":::

## <a name="model-your-data"></a>Model your data (Modelar os seus dados) 

Os dados que carregou estão quase prontos para relatórios. Vamos inspecionar o modelo de dados e fazer algumas alterações. 

Selecione **Vista de Modelo** à esquerda. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="Seleção da Vista de modelo no Power BI Desktop.":::

O seu modelo de dados deverá ser semelhante à imagem que se segue, com cada tabela numa caixa. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="O modelo de dados para começar.":::

### <a name="create-relationships"></a>Criar relações

Este modelo é um *esquema de estrela* normal, que poderá ver em armazéns de dados: é semelhante a uma estrela. O centro da estrela é a tabela de Factos. As tabelas em redor são denominadas tabelas de Dimensão, relacionadas à tabela de Factos através de relações. A tabela de Factos contém informações numéricas de transações de vendas, tais como o Sales Amount (Montante de Vendas) e o Product Standard Cost (Custo Padrão do Produto). As Dimensões fornecem contexto para que possa, entre outras coisas, analisar: 

- Que Produto (Product) foi vendido... 
- a que Cliente (Client)... 
- por qual Revendedor (Reseller)... 
- em que Território de Vendas (Sales Territory).  

Se analisar atentamente, irá notar que todas as tabelas de Dimensões estão relacionadas a um Facto através de uma Relação, exceto a tabela Date (Data). Vamos agora adicionar algumas relações a Date (Data). Arraste DateKey da tabela Date (Data) para OrderDateKey na tabela Sales (Vendas). Criou uma relação “um-para-muitos” de Date (Data) para Sales (Vendas), conforme indicado pelo **1** e pelo asterisco * (muitos) nas duas extremidades da linha.  

A relação denomina-se “um-para-muitos” porque temos uma ou mais encomendas de Sales (Vendas) para uma determinada Date (Data). Se cada data tivesse apenas uma encomenda de Sales (Vendas), a relação seria “um-para-um”. A seta pequena no meio da linha indica a “direção-de-filtragem-cruzada”. A mesma indica que pode utilizar os valores da tabela Date (Data) para filtrar a tabela Sales (Vendas), para que a relação lhe permita analisar quando a encomenda de Sales (Vendas) foi efetuada.  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Relação entre as tabelas Sales (Vendas ) e Date (Data).":::

A tabela Sales (Vendas) contém mais informações sobre as datas relacionadas com as encomendas de Sales (Vendas), como a Data para Conclusão e a Data de Envio. Vamos adicionar mais duas relações à tabela Date (Data) ao arrastar: 

- DateKey para DueDateKey 
- DateKey para ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Três relações entre as tabelas Sales (Vendas) e Date (Data).":::

Notou que a primeira relação, em OrderDateKey, está ativa, representada por uma linha contínua. As outras duas estão inativas, representadas por linhas tracejadas. O Power BI utiliza a relação ativa para predefinição para estabelecer uma relação entre Sales (Vendas) e Date (Data). Por este motivo, a soma de SalesAmount é calculada através da Data de Encomenda, e não da Data para Conclusão ou da Data de Envio. Pode influenciar este comportamento. Consulte [Pontos extra: escrever uma medida em DAX](#extra-credit-write-a-measure-in-dax) mais à frente neste tutorial.

### <a name="hide-key-columns"></a>Ocultar colunas chave

O esquema de estrela normal contém várias chaves que detêm as relações entre Factos e Dimensões. Normalmente, não queremos utilizar nenhuma coluna chave nos nossos relatórios. Vamos ocultar as colunas chave da vista, para que a Lista Campos apresente menos campos e o modelo de dados seja mais fácil de utilizar. 

Observe todas as tabelas e oculte todas as colunas cujo nome termine em *Key* (Chave): 

Selecione o ícone de **Olho** junto à coluna e selecione **Ocultar na vista de relatório**.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="Coluna visível com o ícone de Olho.":::

Também pode selecionar o ícone de **Olho** junto à coluna no painel Propriedades.

Os campos ocultos têm este ícone, um olho com uma linha a atravessá-lo. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="Campo com o ícone de Olho oculto.":::
 
Oculte estes campos.

|Tabela  |Coluna  |
|---------|---------|
|Customer  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|Produto     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| SalesOrder    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

O seu modelo de dados deverá ter agora o aspeto deste modelo de dados, com relações entre Sales (Vendas) e todas as outras tabelas e todos os campos chave ocultos: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="Modelo de dados com colunas chave ocultas.":::

### <a name="create-hierarchies"></a>Criar hierarquias

Agora que o nosso modelo de dados foi simplificado através das colunas ocultas, podemos adicionar algumas *hierarquias* para que o modelo seja ainda mais fácil de utilizar. As hierarquias permitem uma navegação mais simples de agrupamentos. Por exemplo, as cidades localizam-se num Estado ou Província, num determinado País ou Região. 

Crie as seguintes hierarquias. 

1. Clique com o botão direito do rato no nível mais elevado ou no campo menos granular da hierarquia e selecione **Criar hierarquia**. 

1. No painel **Propriedades**, defina o **Nome** da hierarquia e defina os níveis. 

1. Em seguida, selecione **Aplicar Alterações de Nível**. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="Painel de Propriedades de Hierarquia.":::

Pode também mudar o nome dos níveis da hierarquia no painel Propriedades após serem adicionados. Vai ter de mudar o nome dos níveis Ano e Trimestre da Hierarquia fiscal na tabela Date (Data). 

Eis as hierarquias que precisa de criar.

| Tabela |Nome da hierarquia |Níveis  |
|---------|---------|---------|
|Customer     | Geografia   | País/Região  |
|     | | Estado/Província  |
|     |         | City |
|Row4     |         | Código Postal |
|Row5     |         | Cliente   |
|Data     | Fiscal  | Ano (Ano Fiscal)  |
|     |         | Trimestre (Trimestre Fiscal) |
|     |         | Mensal |
|     |         | Data |
| Product  | Produtos | Categoria |
|     |         | Subcategoria |
|     |         | Modelação |
|     |         | Product |
| Reseller   | Geografia | País/Região |
|     |         | Estado/Província |
|     |         | City  |
|     |         | Código Postal  |
|     |         | Reseller |
| SalesOrder  | Sales Orders | Encomenda de Vendas |
|     |         | Linha de Nota de Venda |
| SalesTerritory    | Sales Territories | Group |
|     |         | Country |
|     |         | Region |
 
O seu modelo de dados deverá ter um aspeto semelhante ao do seguinte modelo de dados. Contém as mesmas tabelas, mas cada tabela de dimensão possui uma hierarquia: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="Modelo de dados com tabelas de dimensão com hierarquias.":::

### <a name="rename-tables"></a>Mudar o nome das tabelas

Para concluir a modelação, vamos mudar o nome das seguintes tabelas no painel Propriedades: 

|Nome antigo da tabela  |Nome novo da tabela  |
|---------|---------|
|SalesTerritory    |  Território de Vendas   |
|SalesOrder  |  Encomenda de Vendas   |

Este passo é necessário, uma vez que os nomes de tabelas do Excel não podem conter espaços.

Agora o seu modelo de dados final está pronto.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="Modelo de dados concluído com as tabelas renomeadas.":::

## <a name="extra-credit-write-a-measure-in-dax"></a>Pontos extra: Escrever uma medida em DAX 

Escrever *medidas* na linguagem de fórmulas DAX é bastante eficiente para a modelação de dados. Há muito a [aprender sobre DAX na documentação do Power BI](/dax/). Por agora, vamos escrever uma medida básica que calcula o montante total de vendas por data de conclusão na encomenda de vendas em vez da data de encomenda predefinida. Esta medida utiliza a [função USERELATIONSHIP](/dax/userelationship-function-dax) para ativar a relação entre Sales (Vendas) e Date (Data) em DueDate (Data para Conclusão) para o contexto de medição. Em seguida, utiliza [CALCULATE](/dax/calculate-function-dax) para somar o Montante de Vendas nesse contexto.

1. Selecione Vista de Dados à esquerda. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="Seleção da Vista de Dados à esquerda.":::

1. Selecione a tabela Sales (Vendas) na lista Campos.

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="Seleção da tabela Sales (Vendas) na lista Campos.":::

1. No friso  **Base** , selecione  **Nova Medida**. 

1. Selecione ou escreva esta medida para calcular o montante total de vendas por data para conclusão na encomenda de vendas em vez da data de encomenda predefinida:

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. Selecione a marca de verificação para consolidar. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="Seleção da marca de verificação para consolidar a medida DAX.":::

## <a name="build-your-report"></a>Criar o relatório 

Agora que já modelou os seus dados, está na altura de criar o seu relatório. Aceda à Vista de Relatório. No painel Campos à direita, pode observar os campos no modelo de dados que criou.

Vamos criar o relatório final, um elemento visual de cada vez. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="Relatório concluído, com números a marcar cada elemento visual":::

### <a name="visual-1-add-a-title"></a>Elemento visual 1: Adicionar um título 

1. No friso **Inserir**, selecione **Caixa de Texto**. Escreva “Resumo Executivo – Relatório de Vendas”. 

1. Selecione o texto que escreveu. Defina o tamanho do tipo de letra para **20** e **Negrito**. 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="Formatação do texto do Resumo Executivo.":::

1. No painel Visualizações, alterne a opção **Fundo** para **Desativado**. 

1. Redimensione a caixa para se ajustar a uma linha. 

### <a name="visual-2-sales-amount-by-date"></a>Elemento visual 2: Montante de Vendas por Data 

Em seguida, irá criar um gráfico de linhas para ver que mês e ano tiveram o maior montante de vendas.

1. No painel Campos, arraste o campo **Sales Amount** (Montante de Vendas) da tabela **Sales** (Vendas) para uma área em branco da tela de relatórios. Por predefinição, o Power BI apresenta um gráfico de colunas com uma coluna, Sales Amount (Montante de Vendas). 

1. Arraste o campo **Month** (Mês) da hierarquia **Fiscal** na tabela **Date** (Data) e largue-o no gráfico de colunas. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="Criação de um gráfico de colunas para cada ano.":::

1. Na secção **Campos** do painel Visualizações, remova os campos **Year** (Ano) e **Quarter** (Trimestre): 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="Remoção dos campos Year (Ano) e Quarter (Trimestre) na secção Campos do painel Visualizações.":::

1. No painel Visualizações, altere o tipo de visualização para **Gráfico de Área**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="Alteração do gráfico de colunas para um gráfico de área.":::

1. Se adicionou a medida DAX nos pontos extra acima, adicione-a também a **Valores**. 
1. Abra o painel Formatação, abra as Cores de dados e altere a cor do **Montante Total de Vendas por Data para Conclusão** para uma cor mais contrastante, como vermelho.

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="Gráfico de área do Montante Total de Vendas por Data para Conclusão.":::

    Como pode verificar, o registo do Montante Total de Vendas por Data para Conclusão encontra-se um pouco abaixo do Montante de Vendas. Isto comprova que o mesmo utiliza a relação entre as tabelas Sales (Vendas) e Date (Data) que utilizam DueDateKey. 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>Elemento visual 3: Quantidade de Encomendas por País Revendedor 

Agora vamos criar um mapa para ver para qual Country (País) os Resellers (Revendedores) recebem a Quantidade de Encomendas mais elevada.

1. No painel Campos, arraste o campo **País/Região** da tabela **Reseller** (Revendedor) para uma área em branco da tela de relatórios. O Power BI cria um mapa. 

1. Arraste o campo **Quantidade de Encomendas** da tabela **Sales** (Vendas) e largue-o no mapa. Certifique-se de que o **País/Região** está no painel **Localização** e a **Quantidade de Encomendas** no painel **Tamanho**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="Mapa da quantidade de encomendas por país/região.":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>Elemento visual 4: Montante de Vendas por Categoria de Produto e Tipo de Negócio de Revendedores 

Em seguida, vamos criar um gráfico de colunas para investigarmos que produtos são vendidos por que tipo de negócio de revendedores.

1. Arraste os dois gráficos que criou para estarem lado a lado na parte superior da tela. Reserve algum espaço no lado esquerdo da tela. 

1. Selecione uma área em branco na metade inferior da sua tela de relatório. 

1. No painel Campos, selecione **Sales Amount** (Montante de Vendas) das **Sales** (Vendas), **Categoria de Produto** de **Product** (Produto) e **Business Type** (Tipo de Negócio) de **Reseller** (Revendedor). 

    O Power BI cria automaticamente um gráfico de colunas agrupadas. Altere a visualização para uma **Matriz**: 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="Alteração de um gráfico de colunas agrupadas para uma matriz.":::

1. Com a matriz ainda selecionada, no painel Filtros, em **Tipo de Negócio**, **Selecionar tudo** e, em seguida, desselecione a caixa **[Não Aplicável]** . 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="Filtrar o tipo de negócio Não Aplicável.":::

1. Arraste a matriz para que tenha uma largura suficiente para preencher o espaço sob os dois gráficos superiores. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="Alargar a matriz para preencher o relatório.":::

1. No painel Formatação da matriz, abra a secção **Formatação condicional** e ative as **Barras de dados**. Selecione os **Controlos avançados** e defina uma cor mais clara para a barra positiva. Selecione **OK**. 

1. Aumente a largura da coluna Sales Amount (Montante de Vendas) de forma a abranger toda a área. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="Matriz com barras de dados para Sales Amount (Montante de Vendas).":::

Parece que Bikes (Bicicletas) têm um total de Sales Amount (Montante de Vendas) superior e os Value Added Resellers (Revendedores de Valor Acrescentado) detêm o maior número de vendas, seguidos de Warehouses (Armazéns). Para Components (Componentes), Warehouses (Armazéns) obtêm vendas superiores aos Value Added Resellers (Revendedores de Valor Acrescentado). 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>Elemento visual 5: Segmentação do calendário fiscal 

As segmentações são uma ferramenta valiosa para filtrar os elementos visuais numa página de relatório para uma seleção específica. Neste caso, podemos criar uma segmentação de dados para nos focarmos no desempenho de cada mês, trimestre e ano. 

1. No painel Campos, selecione a hierarquia **Fiscal** da tabela **Date** (Data) e arraste-a e largue-a na área em branco do lado esquerdo da tela. 

1. No painel Visualizações, selecione **Segmentação de Dados**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="Adicionar a segmentação do calendário do relatório de vendas.":::

1. Na secção Campos do painel Visualizações, remova **Quarter** (Trimestre) e **Date** (Data) para que restem as opções **Year** (Ano) e **Month** (Mês). 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="Remoção de Quarter (Trimestre) e Date (Data) da segmentação Fiscal.":::

Agora, se o seu gestor pedir para ver os dados de um mês específico, pode utilizar a segmentação para alternar entre anos ou meses específicos de cada ano. 

## <a name="extra-credit-format-the-report"></a>Pontos extra: Formatar o relatório 

Se quiser efetuar alguma formatação ligeira neste relatório para o melhorar, seguem-se alguns passos fáceis. 

### <a name="theme"></a>Tema 

- No friso  **Vista** , selecione **Temas** e altere o tema para **Executivo**. 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="Seleção do tema Executivo.":::

### <a name="spruce-up-the-visuals"></a>Dinamizar os elementos visuais 

Faça as seguintes alterações no separador  **Formato**  no painel Visualizações. 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="Captura de ecrã a mostrar o separador Formato no painel Visualizações.":::

**Elemento visual 2, Montante de Vendas por Data**

1. Selecione o Elemento visual 2, Montante de Vendas por Data. 
1. Na secção  **Título** , se não adicionou a medida DAX, altere o texto  **Título** para “Montante de Vendas por Data”. 

    Se adicionou a medida DAX, altere o **Texto do título** para “Montante de Vendas por Data/Data de Conclusão”. 

1. Defina o tamanho do **Texto** para  **16 pt**. 
1. Altere a opção **Sombra** para **Ativado**. 

**Elemento visual 3, Quantidade de Encomendas por País Revendedor**

1. Selecione o Elemento visual 3, Quantidade de Encomendas por País Revendedor. 
1. Na secção **Estilos de mapa** , altere o **Tema** para **Tons de cinzento**. 
1. Na secção  **Título** , altere o **Texto do título** para “Quantidade de Encomendas por País Revendedor”.
1. Defina o **Tamanho do texto** para **16 pt**. 
1. Altere a opção **Sombra** para **Ativado**.  

**Elemento visual 4, Montante de Vendas por Categoria de Produto e Tipo de Negócio de Revendedores**

1. Selecione o Elemento visual 4, Montante de Vendas por Categoria de Produto e Tipo de Negócio de Revendedores. 
1. Na secção  **Título** , altere o **Texto do título** para “Montante de Vendas por Categoria de Produto e Tipo de Negócio de Revendedores”.
1. Defina o **Tamanho do texto** para **16 pt**. 
1. Altere a opção **Sombra** para **Ativado**. 

**Elemento visual 5, Segmentação do calendário fiscal**

1. Selecione o Elemento visual 5, Segmentação do calendário fiscal.
1. Na secção  **Controlos de seleção** , alterne a opção  **Mostrar a opção “Selecionar tudo”** para  **Ativado**. 
1. Na secção  **Cabeçalho de segmentação** , defina o **Tamanho do texto** para **16 pt**. 

### <a name="add-a-background-shape-for-the-title"></a>Adicionar uma forma de fundo para o título 

1. No friso **Inserir**, selecione **Formas** > **Retângulo**. 
1. Coloque-o na parte superior da página e estique-o para ter a largura da página e a altura do título. 
1. No painel **Formatar forma** , na secção **Linha** , altere a **Transparência** para **100%** . 
1. Na secção **Preenchimento** , altere a **Cor de preenchimento** para **Cor de tema 5 #6B91C9 (azul)** . 
1. No separador **Formatar** , selecione **Enviar Para Segundo Plano** > **Enviar para trás**. 
1. Selecione o texto no Elemento visual 1, o título e altere a **Cor do tipo de letra** para  **Branco**. 

## <a name="finished-report"></a>Relatório concluído 

Selecione **FY2019** na segmentação.

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Relatório final concluído.":::

Em suma, este relatório responde às principais perguntas do seu gestor: 

- Em que dia de fevereiro de 2019 efetuou mais vendas? 
    25 de fevereiro, com um montante de vendas de 253 915,47 $. 

- Em que país está a empresa a registar mais sucesso? 
    Nos Estados Unidos, com uma encomenda de 132 748. 

- Em que categoria de produtos e tipos de negócio de revendedores deve a empresa continuar a investir? 
    A empresa deve continuar a investir na categoria Bikes (Bicicletas) e nos negócios de revendedores Value Added Resellers (Revendedores de Valor Acrescentado) e Warehouse (Armazéns). 

## <a name="save-your-report"></a>Guardar relatório 

- No menu **Ficheiro** , selecione **Guardar**. 


## <a name="publish-to-the-power-bi-service-to-share"></a>Publicar no serviço Power BI para partilhar 

Para partilhar o relatório com o seu gestor e colegas, publique-o no serviço Power BI. Quando partilhar com colegas que têm uma conta do Power BI, os mesmos poderão interagir com o relatório, mas não poderão guardar alterações.

1. No Power BI Desktop, no friso **Base** , selecione **Publicar**. 
1. Poderá ter de iniciar sessão no serviço Power BI. Se ainda não tiver uma conta, [inscreva-se para obter uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web). 

1. Selecione um destino como A minha área de trabalho no serviço Power BI > **Selecionar**. 

1. Selecione **Abrir “nome-do-ficheiro” no Power BI**. O relatório concluído é aberto no browser. 

1. Selecione **Partilhar**  na parte superior do relatório para partilhar o seu relatório com outras pessoas.

## <a name="next-steps"></a>Passos seguintes 

- Transferir o [ficheiro .pbix do Power BI concluído](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)
- Saiba mais sobre [DAX e modelação de dados no Power BI Desktop](/learn/modules/dax-power-bi-models/)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
