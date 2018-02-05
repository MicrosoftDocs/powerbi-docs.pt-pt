---
title: "Tutorial – Criar um novo relatório a partir de um conjunto de dados "
description: "Criar um novo relatório do Power BI a partir de um conjunto de dados."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: mihart
ms.openlocfilehash: 7405f2c5663c071d58253f2103c9c7d778ea8299
ms.sourcegitcommit: be5223b62e9a5d57c52f8588d4e539d814751dd6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2018
---
# <a name="create-a-new-power-bi-report-by-importing-a-dataset"></a>Criar um novo relatório do Power BI ao importar um conjunto de dados
Leu o artigo [Relatórios no Power BI](service-reports.md) e pretende agora criar o seu. Existem várias formas diferentes de criar um relatório. Neste artigo, vamos começar por criar um relatório muito básico a partir de um conjunto de dados do Excel. Após compreender as noções básicas da criação de um relatório, os **Passos seguintes** na parte inferior irão direcioná-lo para os tópicos de relatórios mais avançados.  

> **SUGESTÃO**: Para criar um relatório ao copiar um relatório existente, consulte [Copiar um relatório](power-bi-report-copy.md)
> 
### <a name="prerequisites"></a>Pré-requisitos
- Serviço Power BI (para criar relatórios com o Power BI Desktop, veja [Vista de relatórios do Desktop](desktop-report-view.md))   
- Conjunto de dados de exemplo da Análise de Revenda

## <a name="import-the-dataset"></a>Importar o conjunto de dados
Este método de criação de um relatório começa por um conjunto de dados e uma tela de relatório em branco. Para acompanhar, [transfira o conjunto de dados em Excel de exemplo, Análise de Revenda](http://go.microsoft.com/fwlink/?LinkId=529778), e guarde-o no OneDrive para Empresas (preferencial) ou localmente.

1. Vamos criar o relatório numa área de trabalho do serviço Power BI, por isso, selecione uma área de trabalho existente ou crie uma nova.
   
   ![](media/service-report-create-new/power-bi-workspaces2.png)
2. Na parte inferior da barra de navegação à esquerda, selecione **Obter dados**.
   
   ![](media/service-report-create-new/power-bi-get-data3.png)
3. Selecione **Ficheiros** e navegue para o local onde guardou o exemplo de Análise de Revenda.
   
    ![](media/service-report-create-new/power-bi-select-files.png)
4. Para este exercício, selecione **Importar**.
   
   ![](media/service-report-create-new/power-bi-import.png)
5. Após o conjunto de dados ser importado, selecione **Ver conjunto de dados**.
   
   ![](media/service-report-create-new/power-bi-view-dataset.png)
6. Ver um conjunto de dados abre o editor de relatórios.  Irá ver uma tela em branco e as ferramentas de edição de relatórios.
   
   ![](media/service-report-create-new/power-bi-blank-report.png)

> **SUGESTÃO**: se não estiver familiarizado com a tela de edição de relatórios ou precisar de relembrar alguns aspetos, [Faça uma visita ao editor de relatórios](service-the-report-editor-take-a-tour.md) antes de continuar.
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Adicionar um Medidor Radial ao relatório
Agora que o nosso conjunto de dados foi importado, vamos começar a responder a algumas perguntas.  A nossa Diretora de Marketing (CMO) quer saber quanto falta para atingirmos os nossos objetivos de vendas para este ano. Os Medidores são [uma boa opção de visualização](power-bi-report-visualizations.md) para mostrar este tipo de informação.

1. No painel Campos, selecione **Sales (Vendas)** > **This Year Sales (Vendas Deste Ano)** > **Value (Valor)**.
   
    ![](media/service-report-create-new/power-bi-report-step1.png)
2. Converta o visual para um Medidor ao selecionar o modelo Medidor ![](media/service-report-create-new/powerbi-gauge-icon.png) no painel **Visualizações**.
   
    ![](media/service-report-create-new/power-bi-report-step2.png)
3. Arraste **Sales (Vendas)** > **This Year Sales (Vendas Este Ano)** > **Goal (Objetivo)** para o well **Target value (Valor de destino)**. Parece que estamos bastante próximos do nosso objetivo.
   
    ![](media/service-report-create-new/power-bi-report-step3.png)
4. Esta é uma boa altura para [guardar o seu relatório](service-report-save.md).
   
   ![](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Adicionar um gráfico de área e segmentação de dados ao relatório
A nossa CMO quer que respondamos a algumas perguntas adicionais. Ela quer comparar as vendas deste ano com as do ano anterior. Quer também saber os dados por distrito.

1. Primeiro, vamos arranjar algum espaço na nossa tela. Selecione o Medidor e mova-o para o canto superior direito. Depois, arraste e largue um dos cantos para diminuir o tamanho.
2. Desselecione o medidor. No painel Campos, selecione **Sales (Vendas)** > **This Year Sales (Vendas Este Ano)** > **Value (Valor)** e selecione **Sales (Vendas)** > **Last Year Sales (Vendas no Ano Passado)**.
   
    ![](media/service-report-create-new/power-bi-report-step4.png)
3. Converta o visual para um Gráfico de área ao selecionar o modelo Gráfico de área ![](media/service-report-create-new/power-bi-areachart-icon.png) no painel **Visualizações**.
4. Selecione **Time (Tempo)** > **Period (Período)** para adicioná-lo ao well **Axis (Eixo)**.
   
    ![](media/service-report-create-new/power-bi-report-step5.png)
5. Para ordenar a visualização por período de tempo, selecione as reticências e escolha **Ordenar por Período**.
6. Agora, vamos adicionar a segmentação de dados. Selecione uma área vazia na tela e selecione o modelo de Segmentação de Dados ![](media/service-report-create-new/power-bi-slicer-icon.png). Isto irá adicionar uma segmentação de dados vazia à tela.
   
    ![](media/service-report-create-new/power-bi-report-step6.png)    
7. No painel Campos, selecione **District (Distrito)** > **District (Distrito)**. Mova e redimensione a segmentação de dados.
   
    ![](media/service-report-create-new/power-bi-report-step7.png)  
8. Utilize a segmentação de dados para procurar padrões e informações por Distrito.
   
   ![](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continue a explorar os dados e a adicionar visualizações. Quando encontrar informações especialmente interessantes, [afixe-as num dashboard](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Próximos passos
* [Adicionar uma página nova ao relatório](power-bi-report-add-page.md)  
* Saiba como [afixar visualizações a um dashboard](service-dashboard-pin-tile-from-report.md)   
* Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

