---
title: Introdução aos mosaicos dos dashboards para designers do Power BI
description: Este artigo descreve os mosaicos do dashboard no Power BI, que incluem os mosaicos que forem criados a partir dos relatórios do SQL Server Reporting Services (SSRS).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 4577ca5d12002e18406b66036244d895fa7ee5fd
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68994849"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Introdução aos mosaicos dos dashboards para designers do Power BI

Um mosaico é um instantâneo dos seus dados, afixado ao dashboard. Um mosaico pode ser criado a partir de um relatório, de um conjunto de dados, dashboard, a partir da caixa de Perguntas e Respostas, do Excel, dos relatórios do SQL Server Reporting Services (SSRS) e muito mais.  Esta captura de ecrã mostra vários mosaicos diferentes afixados a um dashboard.

![Dashboard do Power BI](media/service-dashboard-tiles/power-bi-dashboard.png)

Os dashboards e os mosaicos de dashboard são uma funcionalidade do serviço Power BI e não do Power BI Desktop. Não pode criar dashboards em dispositivos móveis, mas pode [ver e partilhá-los](mobile-apps-view-dashboard.md) lá.

Para além dos mosaicos de afixação, pode criar mosaicos autónomos diretamente no dashboard com o controlo [Adicionar mosaico](service-dashboard-add-widget.md). Os mosaicos autónomos incluem: caixas de texto, imagens, vídeos, dados de transmissão em fluxo e conteúdo Web.

Precisa de ajuda para compreender os blocos modulares que compõem o Power BI? Veja [Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md).

> [!NOTE]
> Se a visualização original utilizada para criar o mosaico for alterada, o mosaico não será alterado.  Por exemplo, se afixou um gráfico de linhas de um relatório e, em seguida, alterou o gráfico de linhas para um gráfico de barras, o mosaico do dashboard continua a mostrar um gráfico de linhas. Os dados são atualizados, mas o tipo de visualização não.
> 
> 

## <a name="pin-a-tile"></a>Afixar um mosaico
Existem diversas formas diferentes de adicionar (afixar) um mosaico a um dashboard. Pode afixar mosaicos a partir de:

* [Perguntas e Respostas do Power BI](service-dashboard-pin-tile-from-q-and-a.md)
* [Um relatório](service-dashboard-pin-tile-from-report.md)
* [Outro dashboard](service-pin-tile-to-another-dashboard.md)
* [um livro do Excel no OneDrive para Empresas](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher para Excel](publisher-for-excel.md)
* [Quick Insights (Informações Rápidas)](service-insights.md)
* [Um relatório paginado no local no Power BI Report Server ou SQL Server Reporting Services](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Crie mosaicos autónomos para imagens, caixas de texto, vídeos, dados de transmissão em fluxo e conteúdo Web diretamente no dashboard com o controlo [Adicionar mosaico](service-dashboard-add-widget.md).

  ![Ícone Adicionar mosaico](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>Interagir com mosaicos num dashboard
Após adicionar um mosaico a um dashboard, pode mover e redimensioná-lo, ou alterar a aparência e o comportamento do mesmo.

### <a name="move-and-resize-a-tile"></a>Mover e redimensionar um mosaico
Pegue num mosaico e [mova-o no dashboard](service-dashboard-edit-tile.md). Paire o cursor e selecione a alça ![alça do Mosaico](media/service-dashboard-tiles/resize-handle.jpg) para redimensionar o mosaico.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Passe o rato sobre um mosaico para alterar a aparência e o comportamento
1. Paire o cursor sobre o mosaico para apresentar as reticências.
   
    ![Reticências do mosaico](media/service-dashboard-tiles/ellipses_new.png)
2. Selecione as reticências para abrir o menu de ação do mosaico.
   
    ![Ícone de reticências](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    A partir daqui, pode:
   
     * [Adicionar comentários ao dashboard](consumer/end-user-comment.md).
     * [Abrir o relatório utilizado para criar este mosaico](service-reports.md).  
     * [Ver no modo de detalhe](service-focus-mode.md).   
     * [Exportar os dados utilizados no mosaico](visuals/power-bi-visualization-export-data.md).
     * [Editar o título e subtítulo e adicionar uma hiperligação](service-dashboard-edit-tile.md). 
     * [Executar informações](service-insights.md). 
     * [Afixar o mosaico a outro dashboard](service-pin-tile-to-another-dashboard.md).
     * [Eliminar o mosaico](service-dashboard-edit-tile.md).

3. Para fechar o menu de ação, selecione uma área em branco no dashboard.

### <a name="select-a-tile"></a>Selecionar um mosaico
Ao selecionar um mosaico, o que ocorre a seguir depende de como o criou. Caso contrário, a seleção do mosaico encaminha para o relatório, livro do Excel Online, relatório local do Reporting Services ou pergunta das Perguntas e Respostas que foi utilizada para criar o mosaico. Em alternativa, se este tiver uma [ligação personalizada](service-dashboard-edit-tile.md), a seleção do mosaico redirecioná-lo-á para essa ligação.

> [!NOTE]
> Uma exceção são os mosaicos de vídeo criados diretamente no dashboard com a opção **Adicionar mosaico**. A seleção de um mosaico de vídeo (criado desta forma) faz com que o vídeo seja reproduzido diretamente no dashboard.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

* Se o relatório utilizado para criar a visualização não tiver sido guardado, a seleção do mosaico não produzirá nenhuma ação.
* Se o mosaico foi criado a partir de um livro no Excel Online, terá de ter pelo menos permissões de leitura para esse livro. Caso contrário, selecionar o mosaico não abrirá o livro no Excel Online.
* Digamos que cria um mosaico diretamente no dashboard através da opção **Adicionar mosaico** e define uma hiperligação personalizada para o mesmo. Se assim for, quando selecionar o título, o subtítulo ou o mosaico, esse URL será aberto. Caso contrário, por predefinição, ao selecionar um destes mosaicos criados diretamente no dashboard para uma imagem, código Web ou caixa de texto, não será produzida nenhuma ação.
* Os mosaicos podem ser criados a partir de relatórios paginados no local no Power BI Report Server ou SQL Server Reporting Services. Se não tiver permissão para aceder ao relatório no local, ao selecionar o mosaico será redirecionado para uma página com a indicação de que não tem acesso (rsAccessDenied).
* Suponhamos que seleciona um mosaico criado a partir de um relatório paginado no local no Power BI Report Server ou SQL Server Reporting Services. Se não tiver acesso à rede onde o servidor de relatórios está localizado, ao selecionar um mosaico criado a partir desse relatório paginado será redirecionado para uma página com a indicação de que não é possível localizar o servidor (HTTP 404). O seu dispositivo precisa de acesso de rede ao servidor de relatórios para ver o relatório.
* Se a visualização original utilizada para criar o mosaico for alterada, o mosaico não será alterado. Por exemplo, se afixar um gráfico de linhas de um relatório e, em seguida, alterar o gráfico de linhas para um gráfico de barras, o mosaico do dashboard continuará a apresentar um gráfico de linhas. Os dados são atualizados, mas o tipo de visualização não.

## <a name="next-steps"></a>Próximos passos
- [Criar um cartão (mosaico de número grande) para o dashboard](power-bi-visualization-card.md)
- [Introdução aos dashboards para designers do Power BI](service-dashboards.md)  
- [Atualização de dados no Power BI](refresh-data.md)
- [Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)
- [Integrar mosaicos do Power BI em documentos do Office](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)
- [Afixar itens do Reporting Services nos dashboards do Power BI](https://msdn.microsoft.com/library/mt604784.aspx)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

