---
title: "Mosaicos de dashboard no serviço Power BI"
description: Tudo sobre mosaicos de dashboard no Power BI. Inclui os mosaicos criados a partir do SQL Server Reporting Services (SSRS).
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: 
qualitydate: 03/15/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 3b6d8c31c9ba03b0119635af5f9270a584081139
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="dashboard-tiles-in-power-bi"></a>Mosaicos de dashboard no Power BI
Os dashboards e os mosaicos de dashboard são uma funcionalidade do serviço Power BI e não do Power BI Desktop. Enquanto não for possível criar ou afixar mosaicos de dashboards no Power BI Mobile, estes [podem ser visualizados e partilhados](mobile-tiles-in-the-mobile-apps.md). Além disso, no Power BI Mobile, pode [adicionar imagens ao seu dashboard com a aplicação para iPhone](mobile-iphone-app-get-started.md).

## <a name="dashboard-tiles"></a>Mosaicos do dashboard
![Dashboard do Power BI](media/service-dashboard-tiles/power-bi-dashboard.png)

Um mosaico é um instantâneo dos seus dados, afixado ao dashboard. Um mosaico pode ser criado a partir de um relatório, conjunto de dados, dashboard, a partir da caixa de Perguntas e Respostas, do Excel e do SQL Server Reporting Services (SSRS) e muito mais.  Esta captura de ecrã mostra vários mosaicos diferentes afixados a um dashboard.

Para além da afixação, os mosaicos autónomos podem ser criados diretamente no dashboard com a opção [Adicionar mosaico](service-dashboard-add-widget.md). Os mosaicos autónomos incluem: caixas de texto, imagens, vídeos, dados de transmissão em fluxo e conteúdo Web.

Precisa de ajuda para compreender os mosaicos modulares que compõem o Power BI?  Veja [Power BI – Conceitos básicos](service-basic-concepts.md).

> [!NOTE]
> Se a visualização original utilizada para criar o mosaico for alterada, o mosaico não será alterado.  Por exemplo, se afixou um gráfico de linhas de um relatório e, em seguida, alterou o gráfico de linhas para um gráfico de barras, o mosaico do dashboard continua a mostrar um gráfico de linhas. Os dados são atualizados, mas o tipo de visualização não.
> 
> 

## <a name="pin-a-tile-from"></a>Afixar um mosaico a partir de...
Existem diversas formas diferentes de adicionar (afixar) um mosaico a um dashboard. Os mosaicos podem ser afixados a partir de:

* [Perguntas e Respostas do Power BI](service-dashboard-pin-tile-from-q-and-a.md)
* [um relatório](service-dashboard-pin-tile-from-report.md)
* [outro dashboard](service-pin-tile-to-another-dashboard.md)
* [um livro do Excel no OneDrive para Empresas](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher para Excel](publisher-for-excel.md)
* [Informações Rápidas](service-insights.md)
* [SSRS](https://msdn.microsoft.com/library/mt604784.aspx)

E os mosaicos autónomos para imagens, caixas de texto, vídeos, dados de transmissão em fluxo e conteúdo Web podem ser criados diretamente no dashboard com a opção [Adicionar mosaico](service-dashboard-add-widget.md).

  ![Ícone Adicionar mosaico](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interacting-with-tiles-on-a-dashboard"></a>Interagir com mosaicos num dashboard
### <a name="move-and-resize-a-tile"></a>Mover e redimensionar um mosaico
Pegue num mosaico e [mova-o no dashboard](service-dashboard-edit-tile.md). Paire o cursor e selecione a ![alça](media/service-dashboard-tiles/resize-handle.jpg) para redimensionar o mosaico.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Passe o rato sobre um mosaico para alterar a aparência e o comportamento
1. Passe o rato sobre o mosaico para apresentar as reticências.
   
    ![reticências do mosaico](media/service-dashboard-tiles/ellipses_new.png)
2. Selecione as reticências para abrir o menu de ação do mosaico.
   
    ![ícone de reticências](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    A partir daqui, pode:
   
   * [Abrir o relatório utilizado para criar este mosaico ](service-reports.md) ![ícone de relatório](media/service-dashboard-tiles/chart-icon.jpg)  
   
   * [Abrir a folha de cálculo utilizada para criar este mosaico ](service-reports.md) ![ícone de folha de cálculo](media/service-dashboard-tiles/power-bi-open-worksheet.png)  
     
     * [Ver no modo de detalhe ](service-focus-mode.md) ![ícone de detalhe](media/service-dashboard-tiles/fullscreen-icon.jpg)  
     * [Exportar os dados utilizados no mosaico](power-bi-visualization-export-data.md) ![ícone exportar dados](media/service-dashboard-tiles/export-icon.png)
     * [Editar o título e subtítulo, adicionar uma hiperligação, apresentar a hora da última atualização](service-dashboard-edit-tile.md) ![ícone editar](media/service-dashboard-tiles/pencil-icon.jpg)
     * [Executar informações ](service-insights.md) ![ícone informações](media/service-dashboard-tiles/power-bi-insights.png)
     * [Afixar o mosaico a outro dashboard ](service-pin-tile-to-another-dashboard.md)
       ![ícone afixar](media/service-dashboard-tiles/pin-icon.jpg)
     * [Remover o mosaico](service-dashboard-edit-tile.md)
     ![ícone eliminar](media/service-dashboard-tiles/trash-icon.png)
3. Para fechar o menu de ação, selecione uma área em branco na tela.

### <a name="select-click-a-tile"></a>Selecionar (clicar) um mosaico
Ao selecionar um mosaico, o que ocorre em seguida depende de como o mosaico foi criado e se este tem uma [ligação personalizada](service-dashboard-edit-tile.md). Se este tiver uma ligação personalizada, a seleção do mosaico levá-lo-á a essa ligação. Caso contrário, a seleção do mosaico leva-o para o relatório, o livro do Excel Online, a relatório do SSRS que está no local ou para a pergunta das Perguntas e Respostas que foi utilizada para criar o mosaico.

> [!NOTE]
> A exceção são os mosaicos de vídeo criados diretamente no dashboard com a opção **Adicionar mosaico**. A seleção de um mosaico de vídeo (criado desta forma) faz com que o vídeo seja reproduzido diretamente no dashboard.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Se o relatório usado para criar a visualização não tiver sido guardado, então selecionar um mosaico não produzirá nenhuma ação.
* Se o mosaico tiver sido criado a partir de um livro no Excel Online e se não tiver permissões pelo menos de Leitura para o livro, selecionar o mosaico de dados não abrirá o livro no Excel Online.
* No caso dos mosaicos criados diretamente no dashboard com a opção **Adicionar mosaico**, se uma hiperligação personalizada tiver sido definida,a seleção do título, subtítulo e/ou do mosaico abrirá esse URL.  Caso contrário, por predefinição, a seleção de um destes mosaicos criados diretamente no dashboard para uma imagem, código Web ou caixa de texto não produz qualquer ação.
* Se não tiver permissão para o relatório no SSRS, a seleção de um mosaico criado a partir do SSRS produzirá uma página com a indicação de que não tem acesso (rsAccessDenied).
* Se não tiver acesso à rede onde o servidor SSRS está localizado, a seleção de um mosaico criado a partir do SSRS produzirá uma página com a indicação de que não é possível localizar o servidor (HTTP 404). O dispositivo tem de ter acesso de rede ao servidor de relatórios para ver o relatório.
* Se a visualização original utilizada para criar o mosaico for alterada, o mosaico não será alterado.  Por exemplo, se fixou um gráfico de linhas de um relatório e, em seguida, alterar o gráfico de linhas para um gráfico de barras, o mosaico do dashboard continuará a mostrar um gráfico de linhas. Os dados são atualizados, mas o tipo de visualização não.

## <a name="next-steps"></a>Próximos passos
[Criar um cartão (mosaico de número grande) para o dashboard](power-bi-visualization-card.md)

[Dashboards no Power BI](service-dashboards.md)  

[Atualização de dados](refresh-data.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

[Exportar um mosaico para o Power Point](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)

[Afixar itens do Reporting Services nos Dashboards do Power BI](https://msdn.microsoft.com/library/mt604784.aspx)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

