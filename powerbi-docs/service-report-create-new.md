---
title: Criar um relatório a partir de um conjunto de dados
description: Crie um relatório do Power BI a partir de um conjunto de dados.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c3f30206a01dce9cf9fd3ce0600b46b401df2b1f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73871753"
---
# <a name="create-a-report-in-the-power-bi-service-by-importing-a-dataset"></a>Criar um relatório no serviço Power BI através da importação de um conjunto de dados
Leu o artigo [Relatórios no Power BI](consumer/end-user-reports.md) e pretende agora criar o seu. Existem várias formas de criar um relatório. Neste artigo, vamos começar por criar um relatório básico no serviço Power BI a partir de um conjunto de dados do Excel. Após compreender as noções básicas da criação de um relatório, verifique os [Passos seguintes](#next-steps) na parte final da página para ver tópicos mais avançados sobre relatórios.  

## <a name="prerequisites"></a>Pré-requisitos
- [Inscreva-se no serviço Power BI](service-self-service-signup-for-power-bi.md). Para criar relatórios com o Power BI Desktop, veja [Vista de relatórios do Desktop](desktop-report-view.md). 
- [Transfira o conjunto de dados do Excel do exemplo de Análise de Revenda](https://go.microsoft.com/fwlink/?LinkId=529778) e guarde-o localmente ou no OneDrive para Empresas.

## <a name="import-the-dataset"></a>Importar o conjunto de dados
Este método de criação de um relatório começa por um conjunto de dados e uma tela de relatório em branco. Poderá seguir a importação a partir do conjunto de dados do Excel do exemplo de Análise de Revenda.

1. Vamos criar o relatório numa área de trabalho do serviço Power BI, portanto selecione uma área de trabalho existente ou crie uma nova.
   
   ![lista de áreas de trabalho](media/service-report-create-new/power-bi-workspaces2.png)
2. Na parte inferior do painel de navegação, selecione **Obter dados**.
   
   ![Obter dados](media/service-report-create-new/power-bi-get-data3.png)
3. Selecione **Ficheiros** e navegue para o local onde guardou o exemplo de Análise de Revenda.
   
    ![selecionar Ficheiros](media/service-report-create-new/power-bi-select-files.png)
4. Para este exercício, selecione **Importar**.
   
   ![selecionar Importar](media/service-report-create-new/power-bi-import.png)
5. Após o conjunto de dados ser importado, selecione **Ver conjunto de dados**.
   
   ![selecionar Ver conjunto de dados](media/service-report-create-new/power-bi-view-dataset.png)
6. Ver um conjunto de dados abre o editor de relatórios.  Irá ver uma tela em branco e as ferramentas de edição de relatórios.
   
   ![editor de relatórios](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Se não estiver familiarizado com a tela de edição de relatórios ou precisar de relembrar alguns aspetos, veja a [Apresentação do editor de relatórios](service-the-report-editor-take-a-tour.md) antes de continuar. 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Adicionar um Medidor Radial ao relatório
Agora que o nosso conjunto de dados foi importado, vamos começar a responder a algumas perguntas.  A nossa Diretora de Marketing (CMO) quer saber quanto falta para atingirmos os nossos objetivos de vendas para este ano. Os Medidores são [uma boa opção de visualização](visuals/power-bi-report-visualizations.md) para mostrar este tipo de informação.

1. No painel Campos, selecione **Sales (Vendas)**  > **This Year Sales (Vendas Deste Ano)**  > **Value (Valor)** .
   
    ![gráfico de barras no editor de relatórios](media/service-report-create-new/power-bi-report-step1.png)
2. Converta o visual num Medidor ao selecionar o modelo Medidor ![ícone de Medidor](media/service-report-create-new/powerbi-gauge-icon.png) no painel **Visualizações**.
   
    ![Elemento visual do Medidor no editor de relatórios](media/service-report-create-new/power-bi-report-step2.png)
3. Arraste **Sales (Vendas)**  > **This Year Sales (Vendas Este Ano)**  > **Goal (Objetivo)** para o well **Target value (Valor de destino)** . Parece que estamos bastante próximos do nosso objetivo.
   
    ![Elemento visual do Medidor com Goal (Objetivo) como Target value (Valor de destino)](media/service-report-create-new/power-bi-report-step3.png)
4. Esta é uma boa altura para guardar o seu relatório.
   
   ![Menu de Ficheiros](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Adicionar um gráfico de área e segmentação de dados ao relatório
A nossa CMO quer que respondamos a algumas perguntas adicionais. Ela gostaria de comparar as vendas deste ano com as do ano anterior. Quer também saber os resultados por distrito.

1. Primeiro, vamos arranjar algum espaço na nossa tela. Selecione o Medidor e mova-o para o canto superior direito. Depois, arraste e largue um dos cantos para diminuir o tamanho.
2. Desselecione o medidor. No painel Campos, selecione **Sales (Vendas)**  > **This Year Sales (Vendas Este Ano)**  > **Value (Valor)** e selecione **Sales (Vendas)**  > **Last Year Sales (Vendas no Ano Passado)** .
   
    ![editor de relatórios com o Medidor e um gráfico de barras](media/service-report-create-new/power-bi-report-step4.png)
3. Converta o elemento visual num Gráfico de área ao selecionar o modelo Gráfico de Área ![ícone do gráfico](media/service-report-create-new/power-bi-areachart-icon.png) no painel **Visualizações**.
4. Selecione **Time (Tempo)**  > **Period (Período)** para adicioná-lo ao well **Axis (Eixo)** .
   
    ![editor de relatórios com o Gráfico de área ativo](media/service-report-create-new/power-bi-report-step5.png)
5. Para ordenar a visualização por período de tempo, selecione as reticências e escolha **Ordenar por Período**.
6. Agora, vamos adicionar a segmentação de dados. Selecione uma área vazia na tela e selecione o modelo de ![ícone da Segmentação de Dados](media/service-report-create-new/power-bi-slicer-icon.png) Segmentação de Dados. Temos agora uma segmentação de dados vazia na nossa tela.
   
    ![tela de relatórios](media/service-report-create-new/power-bi-report-step6.png)    
7. No painel Campos, selecione **District (Distrito)**  > **District (Distrito)** . Mova e redimensione a segmentação de dados.
   
    ![Editor de relatórios, adicionar Distrito](media/service-report-create-new/power-bi-report-step7.png)  
8. Utilize a segmentação de dados para procurar padrões e informações por Distrito.
   
   ![vídeo de utilização da Segmentação de Dados](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continue a explorar os dados e a adicionar visualizações. Quando encontrar informações especialmente interessantes, [afixe-as num dashboard](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Próximas etapas

* Saiba como [afixar visualizações a um dashboard](service-dashboard-pin-tile-from-report.md)   
* Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

