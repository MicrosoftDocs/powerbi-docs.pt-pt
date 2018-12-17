---
title: Mosaicos de dashboard no serviço Power BI para consumidores
description: Tudo sobre mosaicos de dashboard no Power BI para consumidores. Inclui os mosaicos criados a partir do SQL Server Reporting Services (SSRS).
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/05/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: b4ce5c811b2aa18803483ed9780c6b73a6b04bb1
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2018
ms.locfileid: "52979243"
---
# <a name="dashboard-tiles-in-power-bi"></a>Mosaicos de dashboard no Power BI
Um mosaico é um instantâneo dos seus dados, afixado ao dashboard por um *designer*. Um mosaico pode ser criado a partir de um relatório, conjunto de dados, dashboard, a partir da caixa de Perguntas e Respostas, do Excel, do SQL Server Reporting Services (SSRS) e muito mais.  Esta captura de ecrã mostra vários mosaicos diferentes afixados a um dashboard.

![Dashboard do Power BI](./media/end-user-tiles/power-bi-dashboard.png)


Além de mosaicos afixados a partir de relatórios, os *designers* podem adicionar mosaicos autónomos diretamente no dashboard através da opção **Adicionar mosaico**. Os mosaicos autónomos incluem: caixas de texto, imagens, vídeos, dados de transmissão em fluxo e conteúdo Web.

Precisa de ajuda para compreender os mosaicos modulares que compõem o Power BI?  Veja [Power BI – Conceitos básicos](end-user-basic-concepts.md).


## <a name="interacting-with-tiles-on-a-dashboard"></a>Interagir com mosaicos num dashboard

1. Passe o rato sobre o mosaico para apresentar as reticências.
   
    ![reticências do mosaico](./media/end-user-tiles/ellipses_new.png)
2. Selecione as reticências para abrir o menu de ação do mosaico. As opções disponíveis variam consoante o tipo de elemento visual e o método utilizados para criar o mosaico. Eis alguns exemplos do que poderá ver.

    - mosaico criado com as Perguntas e Respostas
   
        ![ícone de reticências](./media/end-user-tiles/power-bi-menu1.png)

    - mosaico criado a partir de um livro
   
        ![ícone de reticências](./media/end-user-tiles/power-bi-menu2.png)

    - mosaico criado a partir de um relatório
   
        ![ícone de reticências](./media/end-user-tiles/power-bi-menu3.png)
   
    A partir daqui, pode:
   
   * [Abrir o relatório utilizado para criar este mosaico ](end-user-reports.md) ![ícone de relatório](./media/end-user-tiles/chart-icon.jpg)  
   
   * [Abrir a pergunta das Perguntas e Respostas que foi utilizada para criar o mosaico ](end-user-reports.md) ![ícone das Perguntas e Respostas](./media/end-user-tiles/qna-icon.png)  
   

   * [Abrir o livro que foi utilizado para criar este mosaico ](end-user-reports.md) ![ícone de folha de cálculo](./media/end-user-tiles/power-bi-open-worksheet.png)  
    * [Ver o mosaico no modo de detalhe ](end-user-focus.md) ![ícone de detalhe](./media/end-user-tiles/fullscreen-icon.jpg)  
     * [Executar informações ](end-user-insights.md) ![ícone informações](./media/end-user-tiles/power-bi-insights.png)
    * [Adicionar um comentário e iniciar um debate](end-user-comment.md) ![ícone de comentário](./media/end-user-tiles/comment-icons.png)

3. Para fechar o menu de ação, selecione uma área em branco na tela.

### <a name="select-click-a-tile"></a>Selecionar (clicar) um mosaico
Ao selecionar um mosaico, o que ocorre em seguida depende de como o mosaico foi criado e se este tem uma [ligação personalizada](../service-dashboard-edit-tile.md). Se este tiver uma ligação personalizada, a seleção do mosaico levá-lo-á a essa ligação. Caso contrário, a seleção do mosaico leva-o para o relatório, o livro do Excel Online, a relatório do SSRS que está no local ou para a pergunta das Perguntas e Respostas que foi utilizada para criar o mosaico.

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
* Se a visualização original utilizada para criar o mosaico for alterada, o mosaico não será alterado.  Por exemplo, se o *designer* afixou um gráfico de linhas a partir de um relatório e, em seguida, alterou o gráfico de linhas para um gráfico de barras, o mosaico do dashboard continua a mostrar um gráfico de linhas. Os dados são atualizados, mas o tipo de visualização não.

## <a name="next-steps"></a>Próximos passos
[Atualização de dados](../refresh-data.md)

[Power BI - Conceitos Básicos](end-user-basic-concepts.md)
