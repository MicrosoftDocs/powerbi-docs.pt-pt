---
title: 'Tutorial: De um livro do Excel a um relatório incrível no Power BI Desktop'
description: Este tutorial explica como pode criar um relatório incrível rapidamente a partir de um livro do Excel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 02/10/2021
LocalizationGroup: Data from files
ms.openlocfilehash: cf63c16822e04e160da2765ae0be20bd707e89da
ms.sourcegitcommit: 24887643bd3e1b3749ce325dc0ae407432d7fee4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100489962"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>Tutorial: De um livro do Excel a um relatório incrível no Power BI Desktop

Neste tutorial, irá criar um relatório apelativo do início ao fim em 20 minutos! 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Captura de ecrã do relatório do Power BI concluído."::: 

O seu gestor quer ver um relatório sobre os seus últimos números de vendas. Por isso, pediu um resumo executivo de: 

- Que mês e ano tiveram mais lucro? 
- Onde está a empresa a registar mais sucesso (por país)? 
- Em que produto e segmento deve a empresa continuar a investir? 

Com o nosso livro de finanças de exemplo, podemos criar este relatório num instante. Eis como será o relatório final. Vamos começar! 

Neste tutorial, irá aprender a:

> [!div class="checklist"]
> * Transferir dados de exemplo de duas formas diferentes
> * Preparar os dados com algumas transformações
> * Criar um relatório com um título, três elementos visuais e uma segmentação de dados
> * Publicar o relatório no serviço Power BI para poder partilhá-lo com os seus colegas

## <a name="prerequisites"></a>Pré-requisitos

- Antes de começar, tem de [transferir o Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Se está a planear publicar o relatório no serviço Power BI e ainda não se inscreveu, [inscreva-se numa avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="get-data"></a>Obter dados 

Pode obter os dados deste tutorial através de um de dois métodos.

### <a name="get-data-in-power-bi-desktop"></a>Obter dados no Power BI Desktop

Quando abrir o Power BI Desktop, selecione **Experimentar um conjunto de dados de exemplo** a partir da tela em branco.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-desktop-canvas-sample-dataset.png" alt-text="Captura de ecrã de Experimente um exemplo de conjunto de dados na tela."::: 

Se foi encaminhado para este tutorial a partir do Power BI Desktop, avance e escolha **Carregar dados**.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-two-ways-load-data.png" alt-text="Captura de ecrã de Duas formas para utilizar dados de exemplo > Carregar dados.":::

### <a name="download-the-sample"></a>Transferir o exemplo

Também pode transferir diretamente o livro de exemplo. 

1. Transfira o [livro Financial sample (Exemplo financeiro) do Excel](https://go.microsoft.com/fwlink/?LinkID=521962).
1. Abra o Power BI Desktop.
1. Na secção **Dados** do friso **Base**, selecione **Excel**.
1. Navegue até ao local onde guardou o livro de exemplo e selecione **Abrir**.

## <a name="prepare-your-data"></a>Preparar os dados 

Em **Navegador**, tem a opção de *transformar* ou *carregar* os dados. O Navegador fornece uma pré-visualização dos dados para poder verificar que tem o intervalo de dados correto. Os tipos de dados numéricos estão em itálico. Se precisar de fazer alterações, transforme os seus dados antes de carregar. Para tornar as visualizações mais fáceis de ler posteriormente, queremos transformar os dados agora. Ao efetuar cada transformação, verá a mesma adicionada à lista em **Definições de Consulta**, em **Passos Aplicados** 

1. Selecione a tabela **Financials** e selecione **Transformar Dados**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="Captura de ecrã a mostrar o Navegador do Power BI com os dados de exemplo financeiros."::: 

1. Selecione a coluna **Units Sold**. No separador **Base**, selecione **Tipo de Dados** e, em seguida, selecione **Número Inteiro**. Selecione **Substituir atual** para alterar o tipo de coluna. 

    O melhor passo de limpeza de dados que os utilizadores efetuam com maior frequência é a alteração dos tipos de dados. Neste caso, as unidades vendidas estão no formato decimal. Não faz sentido ter 0,2 ou 0,5 de uma unidade vendida, pois não? Vamos então mudar isto para um número inteiro. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="Captura de ecrã a mostrar a alteração de um número decimal para um número inteiro."::: 

1. Selecione a coluna **Segmento**. No separador **Transformar**, selecione **Formato** e, em seguida, selecione **MAIÚSCULAS**.

    Também queremos tornar os segmentos mais fáceis de ver na tabela mais tarde. Vamos formatar a coluna Segmento. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="Captura de ecrã a mostrar a alteração de títulos em minúsculas para maiúsculas.":::

1. Vamos encurtar o nome da coluna de **Nome de Mês** para apenas **Mês**. Faça duplo clique na coluna **Nome de Mês** e mude o nome para apenas **Mês**.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="Captura de ecrã a mostrar a redução do nome da coluna.":::

1. Na coluna **Produto**, selecione o menu pendente e desselecione a caixa de verificação junto a **Montana**. 

     Sabemos que o produto Montana foi descontinuado no mês passado, pelo que queremos filtrar estes dados do nosso relatório para evitar confusões. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Captura de ecrã a mostrar a eliminação de dados do Montana.":::

1. Pode ver que cada transformação foi adicionada à lista em **Definições de Consulta** em **Passos Aplicados**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="Captura de ecrã a mostrar uma lista dos passos aplicados.":::

1. No separador **Base**, selecione **Fechar e Aplicar**. Os nossos dados estão quase prontos para a criação de um relatório. 

    Vê o Sigma na lista Campos? O Power BI detetou que esses campos são numéricos. O Power BI também indica o campo de dados com um símbolo de calendário.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="Captura de ecrã a mostrar a lista Campos com campos numéricos e campo de dados.":::

### <a name="extra-credit-write-a-measure-in-dax"></a>Pontos extra: Escrever uma medida em DAX

Escrever *medidas* na linguagem de fórmulas *DAX* é bastante eficiente para a modelação de dados. Há muito a aprender sobre DAX na documentação do Power BI. Por agora, vamos escrever uma medida básica e unir duas tabelas. 

1. Selecione **Vista de Dados** à esquerda. 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="Captura de ecrã a mostrar o ícone Vista de Dados.":::

1. No friso **Base**, selecione **Nova Tabela**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="Captura de ecrã a mostrar o ícone Nova Tabela.":::

1. Escreva esta medida para gerar uma tabela de Calendário de todas as datas entre 1 de janeiro de 2013 e 31 de dezembro de 2014.  

    ```dax
    Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))    
    ```

2. Selecione a marca de verificação para consolidar.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="Captura de ecrã a mostrar uma expressão DAX.":::

1. Agora, selecione **Vista de Modelo** à esquerda. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="Captura de ecrã a mostrar o ícone Vista de Modelo.":::

1. Arraste o campo **Data** da tabela Finanças para o campo **Data** na tabela Calendário para unir as tabelas e criar uma *relação* entre as mesmas.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="Captura de ecrã a mostrar uma relação entre campos de Data.":::

## <a name="build-your-report"></a>Criar o relatório 

Agora que transformou e carregou os seus dados, está na altura de criar o relatório. No painel Campos à direita, pode observar os campos no modelo de dados que criou. 

Vamos criar o relatório final, um elemento visual de cada vez. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="Captura de ecrã a mostrar todos os elementos do relatório, por número.":::

### <a name="visual-1-add-a-title"></a>Elemento visual 1: Adicionar um título 

1. No friso **Inserir**, selecione **Caixa de Texto**. Escreva "Resumo Executivo – Relatório Financeiro". 
1. Selecione o texto que escreveu. Defina o tamanho do tipo de letra para 20 e negrito. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="Captura de ecrã a mostrar o título de formatação.":::

1. No painel Visualizações, alterne a opção **Fundo** para **Desativado**. 
1. Redimensione a caixa para se ajustar a uma linha. 

### <a name="visual-2-profit-by-date"></a>Elemento visual 2: Profit by Date 

Agora, irá criar um gráfico de linhas para ver que mês e ano tiveram o maior lucro. 

1. No painel Campos, arraste o campo **Profit** para uma área em branco na tela do relatório. Por predefinição, o Power BI apresenta um gráfico de colunas com uma coluna, Profit. 
1. Arraste o campo **Data** para o mesmo elemento visual. O Power BI atualiza o gráfico de colunas para apresentar o lucro dos dois anos.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="Captura de ecrã a mostrar o gráfico de colunas Lucro.":::

1. Na secção **Campos** do painel Visualizações, selecione o menu pendente no valor **Eixo**. Altere a **Data** de **Hierarquia de Datas** para **Data**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="Captura de ecrã a mostrar uma alteração de Hierarquia de datas para Data.":::

    O Power BI atualiza o gráfico de colunas para apresentar o lucro de cada mês.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="Captura de ecrã a mostrar um gráfico de colunas por mês.":::

1. No painel Visualizações, altere o tipo de visualização para **Gráfico de linhas**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="Captura de ecrã a mostrar uma alteração de gráfico de linhas para gráfico de barras.":::

    Agora, pode ver facilmente que dezembro de 2014 foi o mês com maior lucro.

### <a name="visual-3-profit-by-country"></a>Elemento visual 3: Lucro por País 

Crie um mapa para ver que país teve o maior lucro.

1. No painel Campos, arraste o campo **Country** para uma área em branco na tela do relatório para criar um mapa.
1. Arraste o campo **Profit** para o mapa.

    O Power BI cria um elemento visual de mapa com bolhas que representam o lucro relativo de cada local. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="Captura de ecrã a mostrar a criação de um gráfico de mapa.":::

    A Europa parece estar a ter melhores resultados do que a América do Norte. 

### <a name="visual-4-sales-by-product-and-segment"></a>Elemento visual 4: Vendas por Produto e Segmento 

Crie um gráfico de barras para determinar quais as empresas e segmentos em que deve investir.

1. Arraste os dois gráficos que criou para estarem lado a lado na parte superior da tela. Reserve algum espaço no lado esquerdo da tela. 
1. Selecione uma área em branco na metade inferior da sua tela de relatório. 

1. No painel Campos, selecione os campos **Sales**, **Product** e **Segment**. 

    O Power BI cria automaticamente um gráfico de colunas agrupadas. 

1. Arraste o gráfico para que tenha uma largura suficiente para preencher o espaço sob os dois gráficos superiores.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="Captura de ecrã a mostrar um gráfico de colunas agrupadas.":::

    Parece que a empresa deve continuar a investir no produto Paseo e focar-se nos segmentos Small Business (Pequenas Empresas) e Government (Administração Pública).  

### <a name="visual-5-year-slicer"></a>Elemento visual 5: Segmentação de dados de ano 

As segmentações são uma ferramenta valiosa para filtrar os elementos visuais numa página de relatório para uma seleção específica. Neste caso, podemos criar dois cortadores diferentes para reduzir o desempenho para cada mês e ano. Um cortador usa o campo de data na tabela original. O outro usa a [tabela de datas que pode ter criado para "crédito extra"](#extra-credit-write-a-measure-in-dax) mais cedo neste tutorial.


**Cortador de data usando a mesa original**

1. No painel Fields, selecione o campo **Data** na tabela Finanças. Arraste-o para a área em branco à esquerda da tela. 
2. No painel Visualizações, selecione **Segmentação de Dados**. 

    O Power BI cria automaticamente um cortador de gama numérica. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-numeric-range.png" alt-text="Screenshot do cortador de gama numérica Date.":::

1. Pode arrastar as pontas para filtrar, ou selecionar a seta no canto superior direito e alterá-la para um tipo diferente de cortador.

**Cortador de data usando a tabela DAX**

1. No painel Fields, selecione o campo **Data** na tabela Calendário. Arraste-o para a área em branco à esquerda da tela. 
2. No painel Visualizações, selecione **Segmentação de Dados**. 
3. Na secção Campos do painel Visualizações, selecione o menu pendente em **Campos**. Remova Trimestre e Dia para que restem apenas Ano e Mês. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="Captura de ecrã a mostrar a alteração da Hierarquia de datas.":::

4. Expanda cada ano e redimensione o elemento visual, para que todos os meses estejam visíveis.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="Captura de ecrã a mostrar a segmentação de dados de hierarquia de datas.":::

    Este é o cortador que usaremos no relatório final.

Agora, se o seu gestor pedir para ver apenas dados de 2013, pode usar um cortador para selecionar anos, ou meses específicos de cada ano.

### <a name="extra-credit-format-the-report"></a>Pontos extra: Formatar o relatório

Se quiser efetuar alguma formatação ligeira neste relatório para o melhorar, seguem-se alguns passos fáceis. 

**Tema**

- No friso **Vista**, altere o tema para **Executivo**.  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="Captura de ecrã a mostrar a seleção do tema Executivo."::: 

**Dinamizar os elementos visuais** 

Faça as seguintes alterações no separador **Formato** no painel Visualizações.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="Captura de ecrã a mostrar o separador Formato no painel Visualizações.":::

1. Selecione o Elemento visual 2. Na secção **Título**, altere o **Texto do título** para "Lucro por Mês e Ano" e o **Tamanho do texto** para **16 pt**. Altere a opção **Sombra** para **Ativado**. 

1. Selecione o Elemento visual 3. Na secção **Estilos de mapa**, altere o **Tema** para **Tons de cinzento**. Na secção **Título**, altere o **Tamanho do texto** do título para **16 pt**. Altere a opção **Sombra** para **Ativado**.

1. Selecione o Elemento visual 4. Na secção **Título**, altere o **Tamanho do texto** do título para **16 pt**. Altere a opção **Sombra** para **Ativado**.

1. Selecione o Elemento visual 5. Na secção **Controlos de seleção**, altere a opção **Mostrar a opção "Selecionar tudo"** para **Ativado**. Na secção **Cabeçalho de segmentação de dados**, aumente o **Tamanho do texto** para **16 pt**. 

**Adicionar uma forma de fundo para o título**

1. No friso **Inserir**, selecione **Formas** > **Retângulo**. Coloque-o na parte superior da página e estique-o para ter a largura da página e a altura do título. 
1. No painel **Formatar forma**, na secção **Linha**, altere **Transparência** para **100%** . 
1. Na secção **Preenchimento**, altere a **Cor de preenchimento** para **Cor de tema 5 #6B91C9** (azul). 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="Captura de ecrã a mostrar a Cor de tema 5.":::

1. No separador **Formato**, selecione **Enviar para trás** > **Enviar para segundo plano**. 
1. Selecione o texto no Elemento visual 1 e o título e altere a cor do tipo de letra para **Branco**. 

**Adicionar uma forma de fundo para os elementos visuais 2 e 3**

1. No friso **Inserir**, selecione **Formas** > **Retângulo** e estique-o para ter a largura e altura dos Elementos visuais 2 e 3. 
1. No painel **Formatar forma**, na secção **Linha**, altere **Transparência** para **100%** . 
1. No separador **Formato**, selecione **Enviar para trás** > **Enviar para segundo plano**. 

### <a name="finished-report"></a>Relatório concluído

O relatório final melhorado será semelhante a:  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Captura de ecrã a mostrar um relatório final e formatado.":::

Em suma, este relatório responde às principais perguntas do seu gestor: 

- Que mês e ano tiveram mais lucro? 

    Dezembro de 2014 

- Em que país está a empresa a registar mais sucesso? 

    Na Europa, especificamente em França e na Alemanha. 

- Em que produto e segmento deve a empresa continuar a investir? 

    A empresa deve continuar a investir no produto Paseo e focar-se nos segmentos Small Business (Pequenas Empresas) e Government (Administração Pública). 

## <a name="save-your-report"></a>Guardar relatório

- No menu **Ficheiro**, selecione **Guardar**.

## <a name="publish-to-the-power-bi-service-to-share"></a>Publicar no serviço Power BI para partilhar 

Para partilhar o relatório com o seu gestor e colegas, publique-o no serviço Power BI. Quando partilhar com colegas que têm uma conta do Power BI, os mesmos poderão interagir com o relatório, mas não poderão guardar alterações. 

1. No Power BI Desktop, selecione **Publicar** no friso **Base**. 

    Poderá ter de iniciar sessão no serviço Power BI. Se ainda não tiver uma conta, pode inscrever-se para obter uma [avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Selecione um destino como **A minha área de trabalho** no serviço Power BI > **Selecionar**.
1. Selecione **Abrir "nome-do-ficheiro" no Power BI**.

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Captura de ecrã a mostrar a abertura do relatório no serviço Power BI.":::

    O relatório concluído é aberto no browser.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Captura de ecrã do relatório do Power BI concluído no serviço Power BI."::: 

1. Selecione **Partilhar** na parte superior do relatório para partilhar o seu relatório com outras pessoas.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Captura de ecrã a mostrar a partilha do relatório no serviço Power BI.":::

## <a name="next-steps"></a>Próximos passos

- [Tutorial: Analisar dados de vendas do Excel e de um feed OData](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).
