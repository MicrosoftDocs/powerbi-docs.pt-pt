---
title: Partilhar diretamente no Microsoft Teams a partir do serviço Power BI
description: Pode partilhar dashboards e relatórios do Power BI diretamente para o Microsoft Teams a partir do serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 07/31/2020
ms.openlocfilehash: db9084e7f7e78ecf17abe38ade732ab7ad2df754
ms.sourcegitcommit: 5bbe7725918a72919ba069c5f8a59e95453ec14c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94946777"
---
# <a name="share-directly-to-microsoft-teams-from-the-power-bi-service"></a>Partilhar diretamente no Microsoft Teams a partir do serviço Power BI

Pode partilhar dashboards, relatórios e elementos visuais do Power BI diretamente para o Microsoft Teams a partir do serviço Power BI. Utilize a funcionalidade **Partilhar no Teams** para iniciar rapidamente conversas quando vê relatórios e dashboards no serviço Power BI.

## <a name="requirements"></a>Requirements

Para utilizar a funcionalidade **Partilhar no Teams** no Power BI, certifique-se de que esta definição está ativada:

- Os administradores do Power BI não desativaram a definição do inquilino **Partilhar no Teams** no portal de administração do Power BI. Esta definição permite que as organizações ocultem os botões **Partilhar no Teams**. Para obter mais detalhes, veja o artigo do [portal de administração do Power BI](../admin/service-admin-portal.md#share-to-teams).

Veja [Colaborar no Microsoft Teams com o Power BI](service-collaborate-microsoft-teams.md) para obter informações sobre como o Power BI e o Microsoft Teams funcionam em conjunto, incluindo outros requisitos.

## <a name="share-power-bi-content-to-microsoft-teams"></a>Partilhar conteúdo do Power BI no Microsoft Teams

Siga estes passos para partilhar ligações para relatórios, dashboards e elementos visuais no serviço Power BI em canais e chats do Microsoft Teams.

1. Selecione uma das seguintes opções:

   * **Partilhar no Teams** na barra de ação de um dashboard ou relatório:

       ![Captura de ecrã a mostrar o botão Partilhar no Teams na barra de ação.](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * **Partilhar no Teams** no menu de contexto de um único elemento visual:
    
      ![Captura de ecrã a mostrar o botão Partilhar no Teams, no menu contextual de um elemento visual.](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. Na caixa de diálogo **Partilhar no Microsoft Teams**, selecione a equipa ou o canal para onde quer enviar a ligação. Se preferir, pode introduzir uma mensagem. Primeiro, pode ser-lhe pedido para iniciar sessão no Microsoft Teams.

    ![Captura de ecrã a mostrar a caixa de diálogo Partilhar no Microsoft Teams com informações e mensagem.](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. Selecione **Partilhar** para enviar a ligação.
    
1. A ligação é adicionada às conversas existentes ou inicia um novo chat.

    ![Captura de ecrã a mostrar a conversa do Microsoft Teams com ligação para um item do Power BI.](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. Selecione a ligação para abrir o item no serviço Power BI.

1. Se utilizar o menu contextual de um elemento visual específico, este será realçado quando o relatório for aberto.

    ![Captura de ecrã a mostrar o relatório do Power BI aberto com um elemento visual específico realçado.](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

- Os utilizadores sem uma licença do Power BI ou permissão para aceder ao relatório verão uma mensagem a indicar “Conteúdo não disponível”.
- Os botões **Partilhar no Teams** poderão não funcionar se o browser utilizar definições de privacidade rigorosas. Utilize a opção **Continua a ter problemas? Tente abrir numa nova janela** se a caixa de diálogo não abrir corretamente.
- **Partilhar no Teams** não inclui uma pré-visualização de ligação.
- As pré-visualizações de ligações e **Partilhar no Teams** não dão permissão aos utilizadores para ver o item. As permissões têm de ser geridas separadamente.
- O botão **Partilhar no Teams** não está disponível nos menus de contexto do elemento visual quando um autor de relatório define **Mais opções** como **Desativado** para o elemento visual.
- Para outros problemas, veja a secção [Limitações e problemas conhecidos](service-collaborate-microsoft-teams.md#known-issues-and-limitations) do artigo "Colaborar no Microsoft Teams".

## <a name="next-steps"></a>Próximos passos

- [Colaborar no Microsoft Teams com o Power BI](service-collaborate-microsoft-teams.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/).
