---
title: 'Criar um relatório a partir de um ficheiro do Excel no serviço Power BI '
description: Crie um relatório do Power BI a partir de um ficheiro do Excel no serviço Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/14/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: d6a52fd72ab96541eee621d6be6cb50005f293e2
ms.sourcegitcommit: fddba666c6ea90d525a1c3188bbd3c4a03410cdc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2020
ms.locfileid: "92462752"
---
# <a name="create-a-report-from-an-excel-file-in-the-power-bi-service"></a>Criar um relatório a partir de um ficheiro do Excel no serviço Power BI
Leu o artigo [Relatórios no Power BI](../consumer/end-user-reports.md) e pretende agora criar o seu. Existem várias formas de criar um relatório. Neste artigo, vamos começar por criar um relatório básico no serviço Power BI a partir de um ficheiro do Excel. Após compreender as noções básicas da criação de um relatório, verifique os [Passos seguintes](#next-steps) na parte final da página para ver tópicos mais avançados sobre relatórios.  

## <a name="prerequisites"></a>Pré-requisitos
- [Inscreva-se no serviço Power BI](../fundamentals/service-self-service-signup-for-power-bi.md). 
- [Transfira o ficheiro do Excel do exemplo de Análise de Revenda](https://go.microsoft.com/fwlink/?LinkId=529778) e guarde-o localmente ou no OneDrive para Empresas.

## <a name="import-the-excel-file"></a>Importar o ficheiro do Excel
Este método de criação de um relatório começa por um ficheiro e uma tela de relatório em branco. Poderá seguir a importação a partir do ficheiro do Excel do exemplo de Análise de Revenda.

1. Na barra de navegação, selecione **A Minha Área de Trabalho** .
   
   :::image type="content" source="media/service-report-create-new/power-bi-select-my-workspace.png" alt-text="Captura de ecrã a mostrar a seleção da opção A Minha Área de Trabalho.":::
2. Na parte inferior do painel de navegação, selecione **Obter dados** .
   
   ![Obter dados](media/service-report-create-new/power-bi-get-data3.png)
3. Selecione **Ficheiros** e navegue para o local onde guardou o exemplo de Análise de Revenda.
   
    ![selecionar Ficheiros](media/service-report-create-new/power-bi-select-files.png)
4. Neste exercício, selecione **Importar** .
   
   ![selecionar Importar](media/service-report-create-new/power-bi-import.png)
5. Selecione **Abrir** .

   Assim que o ficheiro do Excel for importado, é listado como um *conjunto de dados* na lista da área de trabalho.

1. Selecione **Mais opções (...)** junto ao conjunto de dados e selecione **Gerir relatório** .
   
   :::image type="content" source="media/service-report-create-new/power-bi-dataset-create-report.png" alt-text="Captura de ecrã a mostrar a seleção da opção A Minha Área de Trabalho.":::
6. O editor de relatórios é aberto. 
   
   ![Captura de ecrã a mostrar o editor de relatórios.](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Selecione o ícone de menu para ocultar o painel de navegação, para ter mais espaço.
> 
> :::image type="content" source="../media/power-bi-hide-navigation-pane.png" alt-text="Captura de ecrã a mostrar a seleção da opção A Minha Área de Trabalho.":::


## <a name="add-a-radial-gauge-to-the-report"></a>Adicionar um Medidor Radial ao relatório
Agora que o nosso conjunto de dados foi importado, vamos começar a responder a algumas perguntas.  A nossa Diretora de Marketing (CMO) quer saber quanto falta para atingirmos os nossos objetivos de vendas para este ano. Os Medidores são [uma boa opção de visualização](../visuals/power-bi-report-visualizations.md) para mostrar este tipo de informação.

1. No painel Campos, selecione **Sales (Vendas)**  > **This Year Sales (Vendas Deste Ano)**  > **Value (Valor)** .
   
    ![gráfico de barras no editor de relatórios](media/service-report-create-new/power-bi-report-step1.png)
2. Converta o visual num Medidor ao selecionar o modelo Medidor ![ícone de Medidor](media/service-report-create-new/powerbi-gauge-icon.png) no painel **Visualizações** .
   
    ![Elemento visual do Medidor no editor de relatórios](media/service-report-create-new/power-bi-report-step2.png)
3. Arraste **Sales (Vendas)**  > **This Year Sales (Vendas Este Ano)**  > **Goal (Objetivo)** para o well **Target value (Valor de destino)** . Parece que estamos bastante próximos do nosso objetivo.
   
    ![Elemento visual do Medidor com Goal (Objetivo) como Target value (Valor de destino)](media/service-report-create-new/power-bi-report-step3.png)
4. Esta é uma boa altura para guardar o seu relatório.
   
   ![Menu Ficheiro](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Adicionar um gráfico de área e segmentação de dados ao relatório
A nossa CMO quer que respondamos a algumas perguntas adicionais. Ela gostaria de comparar as vendas deste ano com as do ano anterior. Quer também saber os resultados por distrito.

1. Primeiro, vamos arranjar algum espaço na nossa tela. Selecione o Medidor e mova-o para o canto superior direito. Depois, arraste e largue um dos cantos para diminuir o tamanho.
2. Desselecione o medidor. No painel Campos, selecione **Sales (Vendas)**  > **This Year Sales (Vendas Este Ano)**  > **Value (Valor)** e selecione **Sales (Vendas)**  > **Last Year Sales (Vendas no Ano Passado)** .
   
    ![editor de relatórios com o Medidor e um gráfico de barras](media/service-report-create-new/power-bi-report-step4.png)
3. Converta o elemento visual num Gráfico de área ao selecionar o modelo Gráfico de Área ![ícone do gráfico](media/service-report-create-new/power-bi-areachart-icon.png) no painel **Visualizações** .
4. Selecione **Time (Tempo)**  > **Period (Período)** para adicioná-lo ao well **Axis (Eixo)** .
   
    ![editor de relatórios com o Gráfico de área ativo](media/service-report-create-new/power-bi-report-step5.png)
5. Para ordenar a visualização por período de tempo, selecione as reticências e escolha **Ordenar por Período** .
6. Agora, vamos adicionar a segmentação de dados. Selecione uma área vazia na tela e selecione o modelo de ![ícone da Segmentação de Dados](media/service-report-create-new/power-bi-slicer-icon.png) Segmentação de Dados. Temos agora uma segmentação de dados vazia na nossa tela.
   
    ![tela de relatórios](media/service-report-create-new/power-bi-report-step6.png)    
7. No painel Campos, selecione **District (Distrito)**  > **District (Distrito)** . Mova e redimensione a segmentação de dados.
   
    ![Editor de relatórios, adicionar Distrito](media/service-report-create-new/power-bi-report-step7.png)  
8. Utilize a segmentação de dados para procurar padrões e informações por Distrito.
   
   ![vídeo de utilização da Segmentação de Dados](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continue a explorar os dados e a adicionar visualizações. Quando encontrar informações especialmente interessantes, [afixe-as num dashboard](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Passos seguintes

* [Afixar visualizações num dashboard](service-dashboard-pin-tile-from-report.md)
* [Alterar as definições de relatórios no serviço Power BI](power-bi-report-settings.md)
* Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
