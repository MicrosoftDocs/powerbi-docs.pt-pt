---
title: Adicionar comentários a dashboards e relatórios
description: Este documento mostra como adicionar comentários a um dashboard, relatório ou elemento visual e como utilizar os comentários para ter conversas com os colaboradores.
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Consumer
ms.openlocfilehash: 59ba4d0e62613ed25569efd0602815e3d98aec4d
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496499"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>Adicionar comentários a um dashboard ou relatório

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Adicione um comentário pessoal ou inicie uma conversa sobre um dashboard ou relatório com os seus colegas. A funcionalidade de **comentário** é apenas uma das formas de como um *consumidor* pode colaborar com outros. 

![vídeo de comentários](media/end-user-comment/comment.gif)

> [!NOTE]
> Colaborar com outras pessoas, incluindo adicionar comentários a relatórios partilhados, requer um licença do Power BI Pro ou Premium. [Qual é o meu tipo de licença?](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>Como utilizar a funcionalidade Comentários
Os comentários podem ser adicionados a um dashboard completo, a elementos visuais individuais num dashboard, a uma página de relatório, a um relatório paginado e a elementos visuais individuais numa página de relatório. Adicione um comentário geral ou um comentário direcionado a colegas específicos.  

Quando adiciona um comentário a um relatório, o Power BI captura os valores atuais do filtro e da segmentação de dados. Isto significa que, quando seleciona ou responde a um comentário, a página de relatório ou o elemento visual de relatório pode mudar para mostrar as seleções de filtro e segmentação de dados que estavam ativas quando o comentário foi criado.  

![vídeo a mostrar um relatório com filtros](media/end-user-comment/power-bi-comment.gif)

Porque é que isto é importante? Imagine que um colega aplicou um filtro que revelou uma informação interessante que pretende partilhar com a equipa. Sem esse filtro selecionado, o comentário pode não fazer sentido.

Se estiver a utilizar um relatório paginado, só poderá deixar um comentário geral sobre o relatório.  O suporte para deixar comentários em elementos visuais de relatórios paginados individuais não está disponível.

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>Adicionar um comentário geral a um dashboard ou relatório
O processo para adicionar comentários a um dashboard ou relatório é semelhante.  Neste exemplo, estamos a utilizar um dashboard. 

1. Abra o dashboard ou relatório do Power BI e selecione o ícone de **Comentários**. Esta ação abre a caixa de diálogo Comentários.

    ![ícone de comentários](media/end-user-comment/power-bi-comment-menu.png)

    Aqui podemos ver que o criador do dashboard já adicionou um comentário geral.  Qualquer pessoa com acesso a este dashboard pode ver este comentário.

    ![ícone de comentários](media/end-user-comment/power-bi-first-comments.png)

2. Para responder, selecione **Responder**, introduza a sua resposta e selecione **Publicar**.  

    ![ícone de Resposta a Comentários](media/end-user-comment/power-bi-comment-reply.png)

    Por predefinição, o Power BI encaminha a sua resposta para o colega que iniciou o tópico do comentário, neste caso o Samuel. 

    ![Comentário com resposta](media/end-user-comment/power-bi-respond.png)

 3. Se quiser adicionar um comentário que não faça parte do tópico existente, escreva o seu comentário no campo de texto superior.

    ![ícone de Resposta a Comentários](media/end-user-comment/power-bi-new-comments.png)

    Os comentários deste dashboard terão o seguinte aspeto.

    ![Conversas nos comentários](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>Adicionar um comentário a um elemento visual específico do dashboard ou relatório
Além de adicionar comentários a um dashboard completo ou a uma página de relatório completa, pode adicionar comentários a mosaicos do dashboard individuais e a elementos visuais de relatório individuais. Os processos são semelhantes e, neste exemplo, estamos a utilizar um relatório.

1. Paire o cursor sobre o elemento visual e selecione **Mais opções** (...).    
2. No menu pendente, selecione **Abrir comentários**.

    ![Adicionar um comentário é a primeira opção](media/end-user-comment/power-bi-report-comment.png)  

3.  A caixa de diálogo **Comentários** é aberta e os outros elementos visuais na página ficam a cinzento. Este elemento visual ainda não tem comentários. 

    ![Adicionar um comentário para si próprio](media/end-user-comment/power-bi-comment-column.png)  

4. Escreva o seu comentário e selecione **Publicar**.

    ![Adicionar um comentário para si próprio](media/end-user-comment/power-bi-comment-logistics.png)  

    - Numa página de relatório, selecionar um comentário feito num elemento visual realça esse elemento visual (ver acima).

    - Num dashboard, o ícone de gráfico ![comentário com o ícone de gráfico](media/end-user-comment/power-bi-comment-chart-icon.png) permite-nos saber que o comentário está ligado a um elemento visual específico. Os comentários que se aplicam a todo o dashboard não têm um ícone especial. A seleção do ícone de gráfico realça o elemento visual relacionado no dashboard.
    

    ![o elemento visual realçado](media/end-user-comment/power-bi-highlight.png)

5. Selecione **Fechar** para voltar ao dashboard ou relatório.

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>Chame a atenção dos seus colegas ao utilizar o símbolo @
Quer esteja a criar um comentário num dashboard, relatório, mosaico ou elemento visual, chame a atenção dos seus colegas ao utilizar o símbolo "\@".  Quando escreve o símbolo "\@", o Power BI abre uma lista pendente onde pode procurar e selecionar pessoas da sua organização. Qualquer nome verificado que tenha o símbolo "\@" no início é apresentado a azul. 

Aqui está uma conversa que estou a ter com o *designer* da visualização. O símbolo @ é utilizado para garantir que vejo o comentário. Eu sei que este comentário é para mim. Quando abro o dashboard desta aplicação no Power BI, seleciono **Comentários** no cabeçalho. O painel **Comentários** apresenta a nossa conversa.

![Adicionar uma menção num comentário](media/end-user-comment/power-bi-comment-convo.png)  



## <a name="next-steps"></a>Próximos passos
Voltar às [visualizações para os consumidores](end-user-visualizations.md)    
<!--[Select a visualization to open a report](end-user-open-report.md)-->
