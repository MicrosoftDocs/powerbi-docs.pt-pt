---
title: "Criar um dashboard do Power BI a partir de um relatório"
description: "Criar um dashboard do Power BI a partir de um relatório"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/09/2017
ms.author: mihart
ms.openlocfilehash: 67cc9508d71fa29303d09e8901294a2d6b7f8a56
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2018
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Criar um dashboard do Power BI a partir de um relatório
Já leu [Dashboards no Power BI](service-dashboards.md) e agora deseja criar o seu próprio. Há várias formas diferentes de criar um dashboard: a partir de um relatório, de raiz, de um conjunto de dados, ao duplicar um dashboard existente e muito mais.  Este tópico e o vídeo mostram como criar um novo dashboard ao afixar visualizações de um relatório existente.

> **NOTA**: os dashboards são uma funcionalidade do serviço Power BI, não do Power BI Desktop. Os dashboards não podem ser criados no Power BI mobile, mas podem ser [visualizados e partilhados](mobile-apps-view-dashboard.md).
> 
> 

![](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Vídeo: Criar um dashboard ao afixar visuais e imagens de um relatório
Veja a Amanda a criar um novo dashboard ao afixar visualizações de um relatório. Depois experimente fazê-lo com o exemplo de Análise de Aprovisionamento, seguindo os passos abaixo do vídeo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importar um conjunto de dados com um relatório
Vamos importar um dos conjuntos de dados de exemplo do Power BI e utilizá-lo para criar o nosso novo dashboard. O exemplo que vamos utilizar é um livro do Excel com duas folhas do PowerView. Quando o Power BI importar o livro, este irá adicionar um conjunto de dados e também um relatório à sua área de trabalho.  O relatório é automaticamente criado a partir das folhas do PowerView.

1. [Selecione esta ligação](http://go.microsoft.com/fwlink/?LinkId=529784) para transferir e guardar o ficheiro do Excel de exemplo de Análise de Aprovisionamento. Recomendamos que o guarde no seu OneDrive para Empresas.
2. Abra o serviço Power BI no seu browser (app.powerbi.com).
3. Selecione uma área de trabalho existente ou crie uma nova área de trabalho de aplicação.
4. Na navegação à esquerda, selecione **Obter Dados**.
   
    ![](media/service-dashboard-create/power-bi-get-data3.png)
5. Selecione **Ficheiros**.
   
   ![](media/service-dashboard-create/power-bi-select-files.png)
6. Navegue para o local onde guardou o ficheiro de exemplo de Análise de Aprovisionamento do Excel. Selecione-o e selecione **Ligar**.
   
   ![](media/service-dashboard-create/power-bi-connectnew.png)
7. Neste exercício, selecione **Importar**.
   
    ![](media/service-dashboard-create/power-bi-import.png)
8. Quando aparecer a mensagem de Sucesso, selecione o **x** para fechá-la.
   
   ![](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-some-tiles-to-a-dashboard"></a>Abrir o relatório e afixar mosaicos a um dashboard
1. Mantendo-se na mesma área de trabalho, selecione o separador **Relatórios**. O relatório recém-importado é apresentado com um asterisco amarelo. Selecione o nome do relatório para abril-lo.
   
    ![](media/service-dashboard-create/power-bi-reports.png)
2. O relatório é aberto na [Vista de leitura](service-reading-view-and-editing-view.md). Repare que tem dois separadores na parte inferior: Análise de Desconto e Descrição Geral de Gastos. Cada separador representa uma página do relatório.
   
    ![](media/service-dashboard-create/power-bi-reading-view.png)
3. Passe o cursor sobre uma visualização para ver as opções disponíveis. Para adicionar uma visualização a um dashboard, selecione o ícone de pino ![](media/service-dashboard-create/power-bi-pin-icon.png).
   
    ![](media/service-dashboard-create/power-bi-hover.png)
4. Uma vez que estamos a criar um novo dashboard, selecione a opção de **Novo dashboard** e atribua um nome ao mesmo. 
   
   ![](media/service-dashboard-create/power-bi-pin-tile.png)
5. Quando selecionar **Afixar**, o Power BI irá criar o novo dashboard na área de trabalho atual. Quando for apresentada a mensagem **Afixado ao dashboard**, selecione **Ir para o dashboard**. Se lhe for pedido que guarde o relatório, selecione **Guardar**.
   
     ![](media/service-dashboard-create/power-bi-pin-success.png)
6. O Power BI abre o novo dashboard e há um mosaico (a visualização que acabámos de afixar). 
   
   ![](media/service-dashboard-create/power-bi-pinned.png)
7. Para regressar ao relatório, selecione o mosaico. Afixe mais alguns mosaicos ao dashboard. Desta vez, quando for apresentada a janela **Afixar ao dashboard**, selecione **Dashboard existente**.  
   
   ![](media/service-dashboard-create/power-bi-existing-dashboard.png)

Parabéns pela criação do seu primeiro dashboard! Agora que tem um dashboard, pode fazer muito mais com ele.  Experimente um dos **Próximos passos** sugeridos abaixo ou comece a experimentar e explorar de forma autónoma.   

## <a name="next-steps"></a>Próximos passos
* [Redimensionar e mover mosaicos](service-dashboard-edit-tile.md)
* [Tudo sobre mosaicos de dashboards](service-dashboard-tiles.md)
* [Partilhar o seu dashboard ao criar uma aplicação](service-create-distribute-apps.md)
* [Power BI - Conceitos Básicos](service-basic-concepts.md)
* [Dashboards no Power BI](service-dashboards.md)
* [Sugestões para criar um excelente dashboard](service-dashboards-design-tips.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

