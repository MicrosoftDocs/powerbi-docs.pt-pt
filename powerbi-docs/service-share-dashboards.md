---
title: Partilhar dashboards e relatórios do Power BI com colegas e outras pessoas
description: Como partilhar dashboards e relatórios do Power BI com colegas dentro e fora da organização e o que precisa de saber sobre a partilha.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d82b03325991276924f25da5511baadfe53127e1
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523012"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Partilhar dashboards e relatórios do Power BI com colegas e outras pessoas
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. O Power BI também disponibiliza [várias outras formas de colaborar e distribuir dashboards e relatórios](service-how-to-collaborate-distribute-dashboards-reports.md).

![Ícone Partilhar numa lista de dashboards favoritos](media/service-share-dashboards/power-bi-share-dash-report-favorites.png)

Para partilhar, seja conteúdo dentro ou fora da organização, precisa de uma [licença do Power BI Pro](service-features-license-type.md). Os destinatários também precisam de licenças do Power BI Pro, a menos que os conteúdos estejam numa [capacidade Premium](service-premium-what-is.md). 

Pode partilhar dashboards e relatórios a partir de maioria dos locais no serviço Power BI: Favoritos, Recentes, Partilhado comigo (se o proprietário permitir), A Minha Área de Trabalho ou outras áreas de trabalho. Ao partilhar um dashboard ou relatório, as pessoas com quem os partilhar poderão ver e interagir com os mesmos, mas não os poderão editar. As pessoas verão os mesmos dados que vê no dashboard ou no relatório, a menos que seja aplicada a [RLS (Segurança em nível de linha)](service-admin-rls.md). Os colegas com quem partilhar também os podem partilhar com os colegas deles, se assim o permitir. As pessoas fora da sua organização também podem ver e interagir com os dashboards ou relatórios, mas não os podem partilhar. 

Também pode [partilhar um dashboard a partir de qualquer uma das aplicações móveis do Power BI](consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md). No entanto, não é possível partilhar dashboards do Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Vídeo: Partilhar um dashboard
Veja a Margarida a partilhar o dashboard com colegas dentro e fora da empresa. Em seguida, siga as instruções passo-a-passo abaixo do vídeo para experimentar.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Partilhar um dashboard ou relatório

1. Numa lista de dashboards ou relatórios, ou num dashboard ou relatório abertos, selecione **Partilhar** ![Ícone Partilhar](media/service-share-dashboards/power-bi-share-icon.png).

2. Na caixa superior, introduza os endereços de e-mail completos de pessoas, grupos de distribuição ou grupos de segurança. Não pode partilhar com listas de distribuição dinâmicas. 
   
   Pode partilhar com pessoas cujos endereços são externos à sua organização, mas irá ver um aviso.
   
   ![Aviso sobre partilha externa](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >A caixa de entrada suporta um máximo de cem utilizadores ou grupos. Se precisar de partilhar com um grande número de utilizadores, considere criar o dashboard numa área de trabalho e [distribuí-lo como uma aplicação](service-create-distribute-apps.md).
   > 
   > 


3. Se preferir, adicione uma mensagem. É opcional.
4. Para permitir que os seus colegas partilhem os seus conteúdos com outras pessoas, selecione a opção **Permitir aos destinatários partilhar o dashboard (ou relatório)** .
   
   Permitir a partilha a outras pessoas denomina-se *voltar a partilhar*. Se o permitir, eles podem voltar a partilhar a partir do serviço do Power BI e das aplicações móveis ou encaminhar o convite por e-mail para outras pessoas na sua organização. O convite expira após um mês. As pessoas fora da sua organização não podem voltar a partilhar. Como proprietário do conteúdo, pode desativar ou revogar a possibilidade de voltar a partilhar a nível individual. Veja [Deixar de partilhar ou impedir outras pessoas de partilhar](#stop-sharing-or-stop-others-from-sharing).

5. Selecione **Partilhar**.
   
   ![Selecione o botão Partilhar](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   O Power BI envia um convite por e-mail às pessoas, mas não aos grupos, com uma ligação para o conteúdo partilhado. Verá uma notificação de **Êxito**. 
   
   Quando os destinatários na organização clicam na ligação, o Power BI adiciona o dashboard ou o relatório à página da lista **Partilhado comigo**. Esses destinatários podem selecionar o seu nome para ver todo o conteúdo que partilhou com eles. 
   
   ![Página de lista Partilhado comigo](media/service-share-dashboards/power-bi-shared-with-me-dashboards-reports.png)
   
   Quando os destinatários externos à sua organização clicam na ligação, veem o dashboard ou o relatório, mas não no portal do Power BI habitual. Para obter mais informações, veja [Partilhar um dashboard ou relatório com pessoas fora da organização](#share-a-dashboard-or-report-with-people-outside-your-organization).

## <a name="who-has-access-to-a-dashboard-or-report-you-shared"></a>Quem tem acesso a um dashboard ou relatório que partilhou?
Por vezes, pode querer ver as pessoas com quem partilhou um conteúdo e as pessoas com quem estas também o partilharam:

1. Na lista de dashboards e relatórios, ou nos próprios dashboard ou relatórios, selecione **Partilhar** ![Ícone Partilhar](media/service-share-dashboards/power-bi-share-icon.png). 
2. Na caixa de diálogo **Partilhar dashboard** ou **Partilhar relatório**, selecione **Acesso**.
   
    ![Caixa de diálogo Partilhar dashboard, separador Acesso](media/service-share-dashboards/power-bi-share-dialog-access.png)

    As pessoas fora da sua organização estão listadas como **Convidado**.

## <a name="stop-sharing-or-stop-others-from-sharing"></a>Deixar de partilhar ou impedir outras pessoas de partilhar
Apenas o proprietário do dashboard ou do relatório pode ativar ou desativar a possibilidade de voltar a partilhar.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Se ainda não enviou o convite de partilha
* Antes de enviar o convite, desselecione a caixa de verificação **Permitir que os destinatários partilhem o dashboard (ou relatório)** , na parte inferior.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Se já partilhou o dashboard ou o relatório
1. Na lista de dashboards e relatórios, ou nos próprios dashboard ou relatórios, selecione **Partilhar** ![Ícone Partilhar](media/service-share-dashboards/power-bi-share-icon.png). 
2. Na caixa de diálogo **Partilhar dashboard** ou **Partilhar relatório**, selecione **Acesso**.
   
    ![Caixa de diálogo Partilhar dashboard, separador Acesso](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Clique nas reticências ( **...** ) junto a **Ler e voltar a partilhar** e selecione:
   
   ![Reticências Ler e voltar a partilhar](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Leitura** para impedir a pessoa de partilhar com outros.
   * **Remover acesso** para impedir a pessoa de ver o conteúdo partilhado na íntegra.

4. Na caixa de diálogo **Remover acesso**, pode decidir se também quer remover o acesso a conteúdos relacionados, como relatórios e conjuntos de dados. Se remover itens com um ícone de aviso ![ícone de aviso do Power BI](media/service-share-dashboards/power-bi-warning-icon.png), recomendamos que também remova os conteúdos relacionados, pois não serão apresentados corretamente.

    ![Caixa de diálogo de aviso das definições de partilha do Power BI](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="share-a-dashboard-or-report-with-people-outside-your-organization"></a>Partilhar um dashboard ou relatório com pessoas fora da organização
Quando partilha com pessoas fora da sua organização, estas recebem um e-mail com uma ligação para o dashboard ou relatório partilhado e têm de iniciar sessão no Power BI para os ver. Se elas não tiverem uma licença do Power BI Pro, poderão inscrever-se para uma após clicarem na ligação.

Após iniciarem sessão, verão o dashboard ou o relatório partilhado na janela do browser e não no portal do Power BI. Para acederem mais tarde a este dashboard ou relatório, têm de marcar a ligação.

Não podem editar conteúdos neste dashboard ou relatório. Embora possam interagir com os gráficos e alterar os filtros ou as segmentações de dados, não podem guardar as alterações. 

Apenas os destinatários diretos podem ver o dashboard ou relatório partilhado. Por exemplo, se tiver enviado o e-mail para Vicki@contoso.com, apenas a Vicki poderá ver o dashboard. Mais ninguém pode ver o dashboard, mesmo que tenha a ligação. A Vicki deve utilizar o mesmo endereço de e-mail para aceder ao dashboard. Se alguém se inscrever com outro endereço de e-mail, não terá acesso ao dashboard.

As pessoas fora da sua organização não poderão ver os dados se a segurança ao nível da linha ou da função for implementada nos modelos de tabela do Analysis Services no local.

Se enviar uma ligação de uma aplicação móvel do Power BI para pessoas externas à sua organização, quando estas clicarem na mesma, o dashboard será aberto num browser e não na aplicação móvel do Power BI.

Se [permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](service-admin-portal.md#export-and-sharing-settings), a experiência predefinida limitada ao consumo de conteúdos não se aplica aos mesmos. [Saiba mais](service-admin-azure-ad-b2b.md).

## <a name="limitations-and-considerations"></a>Limitações e considerações
Elementos a ter em conta sobre a partilha de dashboards e relatórios:

* Em geral, o utilizador e os seus colegas veem os mesmos dados no dashboard ou no relatório. Portanto, se tiver permissões para ver mais dados do que os seus colegas, eles conseguirão ver todos os seus dados no dashboard ou no relatório. No entanto, se a [RLS (segurança em nível de linha)](service-admin-rls.md) for aplicada ao conjunto de dados subjacente a um dashboard ou a um relatório, as credenciais de cada pessoa serão utilizadas para determinar a que dados podem aceder.
* Todas as pessoas com quem partilhar o dashboard podem vê-lo e interagir com os relatórios relacionados na [Vista de leitura](consumer/end-user-reading-view.md#reading-view). Não podem criar relatórios ou guardar alterações a relatórios existentes.
* Embora ninguém possa ver ou transferir o conjunto de dados, é possível aceder ao conjunto de dados diretamente através da funcionalidade Analisar no Excel. Um administrador pode restringir a capacidade de utilização da funcionalidade Analisar no Excel para todos os utilizadores num grupo. No entanto, a restrição destina-se a todos os utilizadores desse grupo para cada área de trabalho a que o grupo pertence.
* Todas as pessoas podem [atualizar os dados](refresh-data.md) manualmente.
* Se utilizar o Office 365 para e-mail, pode partilhar com membros de um grupo de distribuição ao introduzir o endereço de e-mail associado ao grupo de distribuição.
* Os colegas com quem partilhe o domínio de e-mail e os colegas cujo domínio é diferente, mas esteja registado no mesmo inquilino, podem partilhar o dashboard com outras pessoas. Por exemplo, se os domínios contoso.com e contoso2.com forem registados no mesmo inquilino, e o seu endereço de e-mail for konrads@contoso.com, os utilizadores ravali@contoso.com e gustav@contoso2.com podem partilhar, desde que lhes tenha concedido permissão de partilha.
* Se os seus colegas já tiverem acesso a um dashboard ou a um relatório específico, pode enviar uma ligação direta ao copiar o URL quando estiver no dashboard ou relatório. Por exemplo: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* De igual modo, se os seus colegas já tiverem acesso a um dashboard específico, pode [enviar uma ligação direta para o relatório subjacente](service-share-reports.md). 
* Pode partilhar com um máximo de cem utilizadores ou grupos numa única ação de partilha. No entanto, pode dar acesso a um item a mais de 500 utilizadores. Para tal, pode partilhar várias vezes ao especificar os utilizadores individualmente ou partilhar com um grupo que inclua todos os utilizadores.

## <a name="troubleshoot-sharing"></a>Resolução de problemas da partilha

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Os destinatários do meu dashboard vêm um ícone de cadeado num mosaico ou a mensagem "Permissão necessária"

As pessoas com quem partilha vêm um ícone de cadeado num dashboard ou a mensagem "Permissão necessária" quanto tentam ver um relatório.

![Mosaico bloqueado do Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

Se for o caso, terá de lhes conceder permissão para o conjunto de dados subjacente:

1. Aceda ao separador **Conjuntos de dados** na sua lista de conteúdos.

1. Selecione as reticências ( **...** ) junto ao conjunto de dados e, em seguida, selecione **Gerir permissões**.

    ![Gerir permissões](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Selecione **Adicionar utilizador**.

    ![Selecione Adicionar utilizador](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Introduza os endereços de e-mail completos de pessoas, grupos de distribuição ou grupos de segurança. Não pode partilhar com listas de distribuição dinâmicas.

    ![Adicionar endereços de e-mail](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Selecione **Adicionar**.

### <a name="i-cant-share-a-dashboard-or-report"></a>Não consigo partilhar um dashboard nem um relatório

Para partilhar um dashboard ou relatório, precisa de permissão para voltar a partilhar os conteúdos subjacentes, ou seja, relatórios e conjuntos de dados relacionados. Se lhe for apresentada uma mensagem a informar que não pode partilhar, peça ao autor do relatório que lhe conceda permissão para voltar a partilhar esses relatórios e conjuntos de dados.

![Mensagem "Não é possível partilhar"](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Próximos passos
* Tem comentários? Vá ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.
* [Como devo colaborar e partilhar os meus dashboards e relatórios?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar um relatório do Power BI filtrado](service-share-reports.md).
* Perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

