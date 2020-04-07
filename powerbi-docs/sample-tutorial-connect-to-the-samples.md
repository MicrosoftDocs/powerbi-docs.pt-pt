---
title: Explorar o exemplo de Análise de Revenda
description: Saiba como instalar e explorar o exemplo de Análise de Revenda no serviço Power BI e no Power BI Desktop.
author: maggiesMSFT
ms.reviewer: amac
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/27/2020
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: f18ec650167b7872cb332bc9ccd606f7ea1f7500
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404600"
---
# <a name="explore-the-retail-analysis-sample"></a>Explorar o exemplo de Análise de Revenda

Este tutorial mostra-lhe como: 
- Importar o pacote de conteúdos do exemplo de Análise de Revenda, adicioná-lo ao serviço Power BI e abrir os conteúdos. Um *pacote de conteúdos* é um tipo de exemplo em que o conjunto de dados é fornecido num pacote com um dashboard e relatório. 
- Abrir o ficheiro .pbix de exemplo de Análise de Revenda no Power BI Desktop.

Caso queira obter mais informações detalhadas, veja [Conjuntos de dados de exemplo do Power BI](sample-datasets.md). Nesse artigo, irá aprender tudo sobre os exemplos; como obtê-los, onde guardá-los, como utilizá-los e algumas das histórias de cada um deles. 

## <a name="prerequisites"></a>Pré-requisitos
Os exemplos estão disponíveis para o serviço Power BI e para o Power BI Desktop. Estamos a utilizar o exemplo de Análise de Revenda, caso pretenda acompanhar.

O pacote de conteúdos de exemplo de *Análise de Retalho* utilizado neste tutorial consiste num dashboard, relatório e conjunto de dados.
Para se familiarizar com este pacote de conteúdos específico e o respetivo cenário, veja [Exemplo de Análise de Revenda do Power BI: ver uma apresentação](sample-retail-analysis.md) antes de começar.

## <a name="import-the-sample-in-the-power-bi-service"></a>Importar o exemplo no serviço Power BI

1. Abra o serviço Power BI (app.powerbi.com), inicie sessão e abra a área de trabalho onde quer guardar o exemplo. 

    Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho.

2. Selecione **Obter Dados** na parte inferior do painel de navegação. 

   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)

   Se não vir **Obter Dados**, expanda o painel de navegação ao selecionar o seguinte ícone na parte superior do painel: ![ícone de mais opções](media/sample-tutorial-connect-to-the-samples/expand-nav.png).

5. Na página **Obter Dados** apresentada, selecione **Exemplos**.
   
6. Selecione **Exemplo de Análise de Revenda** e, em seguida, selecione **Ligar**.   
   
   ![Botão Ligar](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-was-imported"></a>O que foi importado?
Com os pacotes de conteúdos de exemplo, quando seleciona **Ligar**, o Power BI obtém uma cópia desse pacote de conteúdos e armazena-a na cloud. Uma vez que a pessoa que criou o pacote de conteúdos incluiu um conjunto de dados, um relatório e um dashboard, é isso que obtém ao selecionar **Ligar**. 

1. Quando seleciona **Ligar**, o Power BI cria o novo dashboard e lista-o no separador **Dashboards**. 
   
   ![Entrada do Exemplo de Análise de Revenda](media/sample-retail-analysis/retail-entry.png)
2. Abra o separador **Relatórios**. Aqui, verá um novo relatório denominado *Exemplo de Análise de Revenda*.
   
   ![Entrada do Relatório de Exemplo de Análise de Revenda](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Consulte o separador **Conjuntos de Dados**. Também há lá um novo conjunto de dados.
   
   ![Entrada de conjunto de dados do Exemplo de Análise de Revenda](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Explorar o conteúdo novo
Agora explore o dashboard, o conjunto de dados e o relatório por conta própria. Existem muitas formas diferentes de navegar para os dashboards, relatórios e conjuntos de dados. Uma dessas formas está descrita no procedimento que se segue.  

1. Regresse ao separador **Dashboards** e, em seguida, selecione o dashboard **Exemplo de Análise de Revenda** para o abrir.       

   O dashboard é aberto e tem vários mosaicos de visualização.   
 
1. Selecione um dos mosaicos do dashboard para abrir o relatório subjacente. Neste exemplo, selecionaremos o gráfico de área **Vendas deste Ano, Vendas do Ano Passado por Mês Fiscal**.  

   ![Dashboard do Exemplo de Análise de Revenda com o elemento visual realçado](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)

   O relatório é aberto na página que contém o gráfico de área selecionado, sendo nesse caso a página **Vendas Mensais Distritais** do relatório.
   
   ![Página Vendas Mensais Distritais do relatório](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Se o mosaico tiver sido criado com recurso às [Perguntas e Respostas do Power BI](power-bi-tutorial-q-and-a.md), será aberta a página Perguntas e Respostas em vez da página Vendas Mensais Distritais. Se o mosaico tiver sido [afixado do Excel](service-dashboard-pin-tile-from-excel.md), o Excel Online será aberto no Power BI.
   > 
   > 
1. Quando alguém partilha um pacote de conteúdos com colegas, normalmente quer partilhar apenas as informações e não dar aos colegas acesso direto aos dados. No separador **Conjuntos de Dados**, tem várias opções para explorar o conjunto de dados. No entanto, não consegue ver as linhas nem as colunas dos seus dados como consegue no Power BI Desktop ou no Excel. 
   
   ![Entrada de conjunto de dados do Exemplo de Análise de Revenda](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)
   
1. Uma forma de explorar o conjunto de dados é ao criar as suas próprias visualizações e relatórios do zero. Selecione o ícone de gráfico ![Ícone de gráfico](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) para abrir o conjunto de dados no modo de edição de relatórios.
     
   ![Relatório totalmente novo](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)

1. Outra forma de explorar o conjunto de dados é executar as [informações rápidas](consumer/end-user-insights.md). Selecione **Mais opções** (...) e, em seguida, selecione **Obter informações rápidas**. Quando as informações estiverem prontas, selecione **Ver informações**.
     
    ![Relatório de informações](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="download-the-sample-in-power-bi-desktop"></a>Transferir o exemplo no Power BI Desktop 
Quando abre o ficheiro .pbix de exemplo no Power BI Desktop pela primeira vez, este apresenta a Vista de Relatório, na qual pode explorar, criar e modificar qualquer número de páginas de relatórios com visualizações. A Vista de relatório proporciona praticamente a mesma experiência de design que a Vista de edição de um relatório no serviço Power BI. Pode mover as visualizações de um lado para o outro, copiar e colar, unir, etc. 

Ao contrário do que acontece quando se edita um relatório no serviço Power BI, no Power BI Desktop também pode trabalhar com as suas consultas e modelar os seus dados para se certificar de que os seus dados suportam as melhores informações nos seus relatórios. Em seguida, pode guardar o seu ficheiro do Power BI Desktop onde quiser, quer seja na sua unidade local ou na cloud.

1. Transfira o [ficheiro .pbix Exemplo de Análise de Revenda](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) e abra-o no Power BI Desktop. 

    ![Exemplo na vista de relatório do Power BI](media/sample-tutorial-connect-to-the-samples/power-bi-samples-desktop.png)

1. O ficheiro é aberto na Vista de relatório. Repare que há quatro separadores na parte inferior do editor de relatório. Estes separadores representam as quatro páginas deste relatório. Neste exemplo, está atualmente selecionada a página **Novas Lojas**. 

    ![Separador Novas Lojas realçado](media/sample-tutorial-connect-to-the-samples/power-bi-sample-tabs.png).

1. Para obter uma descrição detalhada do editor de relatórios, veja [Apresentação do editor de relatórios](service-the-report-editor-take-a-tour.md).

## <a name="whats-in-your-report"></a>O que há no seu relatório?
Quando transfere um ficheiro .pbix de exemplo, transfere não apenas um relatório, como também o *conjunto de dados subjacente*. Quando abre o ficheiro, o Power BI Desktop carrega os dados com as consultas e relações associadas. Pode ver os dados e as relações subjacentes, mas não pode ver as consultas subjacentes no Editor de Consultas.


1. Mude para a [Vista de Dados](desktop-data-view.md) ao selecionar o ícone de tabela ![ícone de tabela](media/sample-tutorial-connect-to-the-samples/power-bi-data-icon.png).
 
    ![Vista de dados do Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-sample-data.png)

    Na Vista de Dados, pode inspecionar, explorar e compreender os dados no seu modelo do Power BI Desktop. É diferente do modo como vê as tabelas, as colunas e os dados no Editor de Consultas. Na Vista de Dados, os dados já estão carregados no modelo.

    Quando está a modelar os dados, às vezes quer ver o que está realmente nas linhas e colunas de uma tabela sem criar um elemento visual na tela de relatório. Isso é particularmente verdadeiro quando está a criar colunas calculadas e medidas, ou quando precisa de identificar um tipo de dados ou uma categoria de dados.

1. Mude para a [Vista de Relações](desktop-relationship-view.md) ao selecionar o seguinte ícone: ![Ícone de Vista de Relações](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-relationship-icon.png).
 
    ![Vista de relações no Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-relationships.png)

    A Vista de Relações mostra todas as tabelas, colunas e relações no modelo. Aqui pode ver, alterar e criar relações.

## <a name="next-steps"></a>Próximos passos
Aqui pode explorar à vontade, pois pode optar por não guardar as alterações. No entanto, se as guardar, pode sempre aceder a **Obter Dados** para obter uma nova cópia deste exemplo.

Esperamos que esta apresentação tenha mostrado como os dashboards, os conjuntos de dados, as relações e os relatórios do Power BI podem fornecer informações sobre os dados do exemplo. Agora, é a sua vez: ligue-se aos seus próprios dados. Com o Power BI, pode ligar-se a uma grande variedade de origens de dados. Para saber mais, veja [Introdução ao serviço Power BI](service-get-started.md) e [Introdução ao Power BI Desktop](desktop-getting-started.md).  

Para obter mais informações, veja:  
- [Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)
- [Exemplos para o serviço Power BI](sample-datasets.md)
- [Origens de dados para o Power BI](service-get-data.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
