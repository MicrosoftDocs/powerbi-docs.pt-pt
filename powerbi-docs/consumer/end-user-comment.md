---
title: Adicionar comentários a dashboards e relatórios
description: Este documento mostra como adicionar comentários a um dashboard, relatório ou elemento visual e como utilizar os comentários para ter conversas com os colaboradores.
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Consumer
ms.openlocfilehash: ee053fe000ad85b768ce3d451984f987e3c79e6f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96400759"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>Adicionar comentários a um dashboard ou relatório

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Adicione um comentário pessoal ou inicie uma conversa sobre um dashboard ou relatório com os seus colegas. A funcionalidade **comentários** é apenas uma das formas através das quais um *utilizador empresarial* pode colaborar com outras pessoas. 

![vídeo de comentários](media/end-user-comment/comment.gif)

> [!NOTE]
> Colaborar com outras pessoas, incluindo a adição de comentários em relatórios partilhados, requer uma licença do Power BI Pro ou que o conteúdo esteja alojado numa capacidade do Power BI Premium. [Qual é o meu tipo de licença?](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>Como utilizar a funcionalidade Comentários
Os comentários podem ser adicionados a um dashboard completo, a elementos visuais individuais num dashboard, a uma página de relatório, a um relatório paginado e a elementos visuais individuais numa página de relatório. Adicione um comentário geral ou um comentário direcionado a colegas específicos.  

Quando adiciona um comentário a um relatório, o Power BI captura os valores do filtro atual e da segmentação de dados e cria um [marcador](end-user-bookmarks.md). Isto significa que, quando seleciona ou responde a um comentário, a página de relatório ou o elemento visual de relatório pode mudar para mostrar as seleções de filtro e segmentação de dados que estavam ativas quando o comentário foi criado.  

![vídeo a mostrar um relatório com filtros](media/end-user-comment/power-bi-comment.gif)

Porque é que isto é importante? Imagine que um colega aplicou um filtro que revelou uma informação interessante que pretende partilhar com a equipa. Sem esse filtro selecionado, o comentário pode não fazer sentido.

Se estiver a utilizar um relatório paginado, só poderá deixar um comentário geral sobre o relatório.  O suporte para deixar comentários em elementos visuais de relatórios paginados individuais não está disponível.

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>Adicionar um comentário geral a um dashboard ou relatório
O processo para adicionar comentários a um dashboard ou relatório é semelhante.  Neste exemplo, estamos a utilizar um dashboard. 

1. Abra o dashboard ou um relatório do Power BI e selecione o ícone de **Comentários**. Esta ação abre a caixa de diálogo Comentários.

    ![ícone de comentários na barra de menus](media/end-user-comment/power-bi-comment-icon.png)

    Aqui podemos ver que o criador do dashboard já adicionou um comentário geral.  Qualquer pessoa com acesso a este dashboard pode ver este comentário.

    ![Captura de ecrã do dashboard com a secção Comentários selecionada](media/end-user-comment/power-bi-first-comments.png)

2. Para responder, selecione **Responder**, introduza a sua resposta e selecione **Publicar**.  

    ![Ecrã Selecionar Resposta](media/end-user-comment/power-bi-comments-reply.png)

    Por predefinição, o Power BI encaminha a sua resposta para o colega que iniciou o tópico do comentário, neste caso o Samuel. 

    ![Comentário com resposta](media/end-user-comment/power-bi-respond.png)

 3. Se quiser adicionar um comentário que não faça parte do tópico existente, escreva o seu comentário no campo de texto superior.

    ![Captura de ecrã a mostrar um novo tópico](media/end-user-comment/power-bi-new-commenting.png)

    Os comentários deste dashboard terão o seguinte aspeto.

    ![Conversas nos comentários](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>Adicionar um comentário a um elemento visual específico do dashboard ou relatório
Além de adicionar comentários a um dashboard completo ou a uma página de relatório completa, pode adicionar comentários a mosaicos do dashboard individuais e a elementos visuais de relatório individuais. Os processos são semelhantes e, neste exemplo, estamos a utilizar um relatório.

1. Paire o cursor sobre o elemento visual e selecione **Mais ações** (...).    
2. No menu pendente, selecione **Adicionar um comentário**.

    ![Adicionar um comentário é a primeira opção](media/end-user-comment/power-bi-comment-reports.png)  

3.  A caixa de diálogo **Comentários** é aberta e os outros elementos visuais na página ficam a cinzento. Este elemento visual ainda não tem comentários. 

    ![Captura de ecrã a mostrar um elemento visual selecionado e a caixa de diálogo Comentários aberta](media/end-user-comment/power-bi-comments-column.png)  

4. Escreva o seu comentário e selecione **Publicar**.

    ![Caixa de diálogo Comentários com nova mensagem](media/end-user-comment/power-bi-comment-spikes.png)  

    - Numa página de relatório, selecionar um comentário feito num elemento visual realça o mesmo (ver abaixo).

    - Num dashboard, o ícone de gráfico ![comentário com o ícone de gráfico](media/end-user-comment/power-bi-comment-chart-icon.png) permite-nos saber que o comentário está ligado a um elemento visual específico. Os comentários que se aplicam a todo o dashboard não têm um ícone especial. A seleção do ícone de gráfico realça o elemento visual relacionado no dashboard.
    

    ![o elemento visual realçado](media/end-user-comment/power-bi-highlights.png)

5. Selecione **Fechar** para voltar ao dashboard ou relatório.

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>Chame a atenção dos seus colegas ao utilizar o símbolo @
Quer esteja a criar um comentário num dashboard, relatório, mosaico ou elemento visual, chame a atenção dos seus colegas ao utilizar o símbolo "\@".  Quando escreve o símbolo "\@", o Power BI abre uma lista pendente onde pode procurar e selecionar pessoas da sua organização. Qualquer nome verificado que tenha o símbolo "\@" no início é apresentado a azul. Os indivíduos @mentioned receberão imediatamente um e-mail na sua caixa de entrada e, se estiverem a utilizar uma aplicação Power BI Mobile, receberão uma notificação push no seu dispositivo. Podem abrir o comentário diretamente a partir da notificação, ver os dados e responder em conformidade.

Aqui está uma conversa que estou a ter com o *designer* da visualização. O símbolo @ é utilizado para garantir que vejo o comentário. Recebo uma notificação e seleciono a ligação para abrir este dashboard e a conversação relevante.  

![Adicionar uma menção num comentário](media/end-user-comment/power-bi-comment-conversation.png)  

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

- Os marcadores não são capturados quando responde a uma conversação. Apenas o primeiro comentário numa conversação cria um marcador.
- Se estiver a utilizar um relatório paginado, só poderá deixar um comentário geral sobre o relatório.  O suporte para deixar comentários em elementos visuais de relatórios paginados individuais não está disponível.

## <a name="next-steps"></a>Passos seguintes
Voltar a [visualizações de utilizadores empresariais](end-user-visualizations.md)    
[Selecionar uma visualização para abrir um relatório](end-user-report-open.md)
