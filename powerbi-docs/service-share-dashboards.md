---
title: Partilhar dashboards com colegas e outras pessoas - Power BI
description: "Como partilhar dashboards do Power BI com colegas dentro e fora da sua organização e o que precisa de saber sobre a partilha."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
featuredvideoid: 0tUwn8DHo3s
qualityfocus: monitoring
qualitydate: 08/14/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: maggies
ms.openlocfilehash: 0b50568e49df8e2594519028b90d5d833d17c6b7
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/17/2017
---
# <a name="share-your-power-bi-dashboards-with-coworkers-and-others"></a>Partilhar dashboards do Power BI com colegas e outras pessoas
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. O Power BI disponibiliza [várias formas de colaborar e distribuir os seus dashboards](service-how-to-collaborate-distribute-dashboards-reports.md), uma das quais é partilhar.

![Ícone de partilha numa lista de dashboards](media/service-share-dashboards/power-bi-share-dash.png)

Na partilha, seja para partilhar conteúdos dentro ou fora da sua organização, o utilizador e os seus destinatários necessitam de uma [licença do Power BI Pro](service-free-vs-pro.md), ou os conteúdos precisam de estar numa [capacidade Premium](service-premium.md). Sugestões? A equipa do Power BI está sempre interessada nos seus comentários, por isso, aceda ao [site da Comunidade do Power BI](https://community.powerbi.com/).

Pode partilhar um dashboard a partir de A minha área de trabalho ou a partir de uma área de trabalho de aplicação. Quando você compartilha um painel, as pessoas com as quais você o compartilha poderão exibi-lo e interagir com ele, mas não poderão editá-lo. As pessoas verão os mesmos dados que vê no dashboard e nos relatórios, a menos que seja aplicada [RLS (Segurança em nível de linha)](service-admin-rls.md). Os colegas com quem o partilhar podem partilhar o dashboard com os respetivos colegas, se assim o permitir. As pessoas fora da sua organização também podem ver e interagir com o dashboard, mas não podem partilhá-lo. 

Também pode [partilhar um dashboard a partir de qualquer uma das aplicações móveis do Power BI](mobile-share-dashboard-from-the-mobile-apps.md). Pode partilhar dashboards a partir do serviço do Power BI e das aplicações móveis do Power BI, mas não a partir do Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Vídeo: Partilhar um dashboard
Veja a Amanda a partilhar o dashboard dela com colegas dentro e fora da empresa. Em seguida, siga as instruções passo a passo abaixo do vídeo para experimentar.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard"></a>Compartilhar um painel
1. Em A minha área de trabalho ou numa área de trabalho de aplicação, abra um dashboard e selecione **Partilhar** ![Ícone de partilha](media/service-share-dashboards/power-bi-share-icon.png).
2. Na caixa superior, introduza os endereços de e-mail completos de pessoas, grupos de distribuição ou grupos de segurança. Não pode partilhar com listas de distribuição dinâmicas. 
   
   Pode partilhar com pessoas cujos endereços são externos à sua organização, mas irá ver um aviso.
   
   ![Aviso sobre partilha externa](media/service-share-dashboards/power-bi-share-dialog-warning.png)  
3. Se preferir, adicione uma mensagem. É opcional.
4. Para permitir que os seus colegas partilhem o seu dashboard com outras pessoas, marque a opção **Permitir aos destinatários partilhar o dashboard**.
   
   Permitir a partilha a outras pessoas denomina-se *voltar a partilhar*. Se o permitir, eles podem voltar a partilhar a partir do serviço do Power BI e das aplicações móveis ou encaminhar o convite por e-mail para outras pessoas na sua organização. O convite expira após um mês. As pessoas de fora da sua organização não podem compartilhar novamente. Como proprietário do dashboard, pode desativar a possibilidade de voltar a partilhar ou revogá-la individualmente. Consulte [Impedir a partilha de um dashboard ou impedir outras pessoas de partilhar](service-share-dashboards.md#stop-sharing-a-dashboard-or-stop-others-from-sharing), mais abaixo.
5. Selecione **Compartilhar.**
   
   ![Selecione o botão Partilhar](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   O Power BI envia um convite por e-mail para as pessoas, mas não para os grupos, com uma ligação para o dashboard partilhado. Irá ver uma notificação de **Êxito**. 
   
   Quando os destinatários na sua organização clicam na ligação, o Power BI adiciona o dashboard à respetiva página da lista **Partilhado comigo**. Podem selecionar o seu nome para ver todos os dashboards que partilhou. 
   
   ![Página de lista Partilhado comigo](media/service-share-dashboards/power-bi-shared-with-me-list-page.png)
   
   Quando os destinatários externos à sua organização clicam na ligação, veem o dashboard, mas não no habitual portal do Power BI. Consulte [Partilhar um dashboard com pessoas fora da sua organização](service-share-dashboards.md#share-a-dashboard-with-people-outside-your-organization), mais abaixo, para obter detalhes.

## <a name="who-has-access-to-a-dashboard-you-shared"></a>Quem tem acesso a um dashboard que partilhou?
Por vezes, é necessário ver as pessoas com quem partilhou um dashboard e as pessoas com quem estas o partilharam.

1. Na lista de dashboards ou no próprio dashboard, selecione **Partilhar** ![Ícone de partilha](media/service-share-dashboards/power-bi-share-icon.png). 
2. Na caixa de diálogo **Partilhar dashboard**, selecione **Acesso**.
   
    ![Caixa de diálogo Partilhar dashboard, separador Acesso](media/service-share-dashboards/power-bi-share-dialog-access.png)
   
    As pessoas externas à sua organização são listadas como **Convidado**.

## <a name="stop-sharing-a-dashboard-or-stop-others-from-sharing"></a>Deixar de partilhar um dashboard ou impedir outras pessoas de partilhar
Somente o proprietário do painel pode ativar e desativar o novo compartilhamento.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Se ainda não enviou o convite de partilha
* Desmarque a caixa de verificação **Permitir que os destinatários partilhem este dashboard**, na parte inferior do convite, antes de enviar.

### <a name="if-youve-already-shared-the-dashboard"></a>Se já partilhou o dashboard
1. Na lista de dashboards ou no próprio dashboard, selecione **Partilhar** ![Ícone de partilha](media/service-share-dashboards/power-bi-share-icon.png). 
2. Na caixa de diálogo **Partilhar dashboard**, selecione **Acesso**.
   
    ![Caixa de diálogo Partilhar dashboard, separador Acesso](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Clique nas reticências (**...**) junto a **Ler e voltar a partilhar** e selecione:
   
   ![Reticências Ler e voltar a partilhar](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Leitura** para impedir a pessoa de partilhar com outros.
   * **Remover acesso** para impedir a pessoa de ver o dashboard.

## <a name="share-a-dashboard-with-people-outside-your-organization"></a>Partilhar um dashboard com pessoas fora da sua organização
Quando partilha com pessoas fora da sua organização, elas recebem um e-mail com uma ligação para o dashboard partilhado, e elas têm de iniciar sessão no Power BI para ver o dashboard. Se elas não tiverem uma licença do Power BI Pro, poderão inscrever-se numa após clicarem na ligação.

Depois de entrar, elas poderão ver o painel compartilhado em sua própria janela do navegador sem o painel de navegação à esquerda, e não no portal do Power BI normal. Elas precisam do indicador no link para acessar esse painel no futuro.

Elas não podem editar nenhum conteúdo nesse painel ou relatório. Elas podem interagir com os gráficos no relatório (realce cruzado) e alterar filtros/segmentações de dados disponíveis nos relatórios ligados ao dashboard, mas não podem guardar as alterações.

Somente os destinatários diretos podem ver o painel compartilhado. Por exemplo, se tiver enviado o e-mail para Vicki@contoso.com, apenas a Vicki poderá ver o dashboard. Ninguém mais poderá ver esse painel, mesmo se tiver o link, e a Clara terá de usar o mesmo endereço de email para acessar o painel. Se ela se inscrever com qualquer outro endereço de email, não terá acesso ao painel.

As pessoas de fora da sua organização não poderão ver os dados se a segurança em nível de linha ou de função for implementada nos modelos de tabela Analysis Services no local.

Se enviar uma ligação de uma aplicação móvel do Power BI para pessoas externas à sua organização, quando estas clicarem na ligação, o dashboard é aberto num browser, não na aplicação móvel do Power BI.

## <a name="limitations-and-considerations"></a>Limitações e considerações
Elementos a ter em conta sobre a partilha de dashboards:

* Em geral, o utilizador e os seus colegas veem os mesmos dados no dashboard. Portanto, se você tiver permissões para ver mais dados do que eles, eles poderão ver todos os seus dados no seu painel. No entanto, se a [RLS (Segurança em nível de linha)](service-admin-rls.md) for aplicada ao conjunto de dados subjacente a um dashboard, as credenciais de cada pessoa serão utilizadas para determinar a que dados podem aceder.
* Todas as pessoas com quem partilha o dashboard podem vê-lo e interagir com os seus relatórios na [Vista de Leitura](service-report-open-in-reading-view.md). Não podem criar relatórios ou guardar alterações a relatórios existentes.
* Ninguém pode ver ou transferir o conjunto de dados.
* Todas as pessoas podem, manualmente, [atualizar os dados do dashboard](refresh-data.md).
* Se você usar o Office 365 para email, poderá compartilhar com os membros de um grupo de distribuição inserindo o endereço de email associado ao grupo de distribuição.
* Os colegas com o mesmo domínio de e-mail que o utilizador e os colegas com um domínio diferente, mas que estejam registados no mesmo inquilino, podem partilhar o dashboard com outras pessoas. Por exemplo, suponhamos que os domínios contoso.com e contoso2.com estão registados no mesmo inquilino. Se o seu endereço de e-mail for konrads@contoso.com, isso quer dizer que ravali@contoso.com e gustav@contoso2.com podem partilhar, desde que lhes tenha dado permissão para partilhar.
* Se os seus colegas já tiverem acesso a um dashboard específico, poderá enviar uma ligação direta para esse dashboard ao copiar o URL quando estiver no dashboard. Por exemplo: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* De igual modo, se os seus colegas já tiverem acesso a um dashboard específico, pode [enviar uma ligação direta para o relatório subjacente](service-share-reports.md). 

## <a name="next-steps"></a>Próximas etapas
* Tem comentários? Aceda ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.
* [Como devo colaborar e partilhar os meus dashboards e relatórios?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar apenas um relatório do Power BI](service-share-reports.md)
* Perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

