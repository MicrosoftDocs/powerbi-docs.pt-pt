---
title: Utilizar os exemplos do Power BI, tutorial.
description: 'Tutorial: utilizar os exemplos do Power BI'
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 03/08/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: 6d043f21635308def7b119c072a7f99c118e901d
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="the-power-bi-samples-a-tutorial"></a>Exemplos do Power BI, tutorial
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

Recomendamos que comece pelo artigo [Conjuntos de dados de exemplo do Power BI](sample-datasets.md). Nesse artigo, irá aprender tudo sobre os exemplos; como obtê-los, onde guardá-los, como utilizá-los e algumas das histórias de cada um deles. Em seguida, quando tiver algumas noções básicas, volte a este Tutorial.   

## <a name="about-this-tutorial"></a>Acerca deste tutorial
Este tutorial ensina-o a importar pacotes de conteúdos de exemplo, a adicioná-los ao serviço Power BI e a abrir o conteúdo. Um *pacote de conteúdos* é um tipo de exemplo em que o conjunto de dados é fornecido num pacote com um dashboard e relatório. Os pacotes de conteúdos de exemplo estão disponíveis no Power BI com **Obter Dados**.

> [!NOTE]
> Este tutorial aplica-se ao serviço Power BI e não ao Power BI Desktop.
> 
> 

O pacote de conteúdos de exemplo de *Análise de Retalho* utilizado neste tutorial consiste num dashboard, relatório e conjunto de dados.
Para se familiarizar com este pacote de conteúdos específico e o respetivo cenário, pode [ver uma apresentação do exemplo Análise de Revenda](sample-retail-analysis.md) antes de começar.

## <a name="get-data-in-this-case-get-a-sample-content-pack"></a>Obter dados (neste caso, obter um pacote de conteúdos de exemplo)
1. Abra e inicie sessão no serviço Power BI (app.powerbi.com).
2. Selecione uma área de trabalho e crie um novo dashboard.  
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-create-dashboard2.png)
3. Dê-lhe o nome **Exemplo de análise de revenda**.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-name-dashboard.png)
4. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo. Se **Obter Dados** não for apresentado, expanda o painel de navegação, selecionando ![](media/sample-tutorial-connect-to-the-samples/expand-nav.png).
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_getdata.png)
5. Selecione **Exemplos**.  
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_samplesdownload.png)
6. Selecione o *Exemplo de Análise de Revenda* e selecione **Ligar**.   
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-exactly-was-imported"></a>O que foi importado exatamente?
Com os pacotes de conteúdos de exemplo, quando seleciona **Ligar**, o Power BI está, na verdade, a trazer uma cópia desse pacote de conteúdos e a armazená-la na cloud. Uma vez que a pessoa que criou o pacote de conteúdos incluiu um conjunto de dados, um relatório e um dashboard, é isso que obtém ao clicar em **Ligar**.

1. O Power BI cria o novo dashboard e lista-o no separador **Dashboards**. O asterisco amarelo permite-lhe saber que é novo.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dashboard.png)
2. Abra o separador **Relatórios**.  Aqui, verá um novo relatório denominado *Exemplo de Análise de Revenda*.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Veja o separador **Conjuntos de dados**.  Existe também um novo conjunto de dados.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Explorar o conteúdo novo
Agora explore o dashboard, o conjunto de dados e o relatório por conta própria. Existem muitas formas diferentes de navegar para os dashboards, relatórios e conjuntos de dados e apenas uma dessas formas está descrita abaixo.  

> [!TIP]
> Quer uma pequena ajuda primeiro?  Experimente ver a [Apresentação do exemplo de Análise de Revenda](sample-retail-analysis.md) para obter instruções passo a passo deste exemplo.
> 
> 

1. Regresse ao separador **Dashboards** e selecione o dashboard *Exemplo de Análise de Revenda* para abri-lo.    
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards.png)
2. É aberto o dashboard.  Tem uma variedade de mosaicos de visualização.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)
3. Selecione um dos mosaicos para abrir o relatório subjacente.  Neste exemplo, vamos selecionar o gráfico de área (descrito a rosa na imagem anterior). O relatório é aberto na página que contém esse gráfico de área.
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Se o mosaico tiver sido criado com as [Perguntas e Respostas do Power BI](service-q-and-a.md), deve ter sido aberta a página Perguntas e Respostas.
   > 
   > 
4. De volta ao separador **Conjuntos de dados**, tem várias opções para explorar o conjunto de dados.  Não poderá abrir e ver todas as linhas e colunas (como no Power BI Desktop ou no Excel).  Quando alguém partilha um pacote de conteúdos com colegas, normalmente, quer partilhar as informações e não dar aos colegas acesso direto aos dados. No entanto, isso não significa que não pode explorar o conjunto de dados.  
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon2.png)
   
   * Uma forma de explorar o conjunto de dados é ao criar as suas próprias visualizações e relatórios do zero.  Selecione o ícone de gráfico ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) para abrir o conjunto de dados no modo de edição de relatórios.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)
   * Outra forma de explorar o conjunto de dados é executar as [Informações Rápidas](service-insights.md). Selecione as reticências (...) e a opção **Obter informações**. Quando as informações estiverem prontas, selecione **Ver informações**.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="next-steps"></a>Próximos passos
[Conceitos básicos do Power BI](service-basic-concepts.md)

[Exemplos para o serviço Power BI](sample-datasets.md)

[Origens de dados para o Power BI](service-get-data.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

