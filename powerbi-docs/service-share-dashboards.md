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
ms.date: 12/11/2017
ms.author: maggies
ms.openlocfilehash: 276f663b8454ef0938222576cec13fcfb073e2cf
ms.sourcegitcommit: bb577045145b2e6e5807622a53cefa2d46574618
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2017
---
# <a name="share-your-power-bi-dashboards-with-coworkers-and-others"></a>Partilhar dashboards do Power BI com colegas e outras pessoas
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. O Power BI disponibiliza [várias formas de colaborar e distribuir os seus dashboards](service-how-to-collaborate-distribute-dashboards-reports.md), uma das quais é partilhar.

![Ícone de partilha numa lista de dashboards](media/service-share-dashboards/power-bi-share-dash.png)

Na partilha, seja para partilhar conteúdos dentro ou fora da sua organização, o utilizador e os seus destinatários necessitam de uma [licença do Power BI Pro](service-free-vs-pro.md), ou os conteúdos precisam de estar numa [capacidade Premium](service-premium.md). Sugestões? A equipa do Power BI está sempre interessada nos seus comentários, por isso, aceda ao [site da Comunidade do Power BI](https://community.powerbi.com/).

Pode partilhar um dashboard a partir de A minha área de trabalho ou a partir de uma área de trabalho de aplicação. Ao partilhar um dashboard ou relatório, as pessoas com quem o partilhar podem ver e interagir com o mesmo, mas não podem editá-lo. As pessoas verão os mesmos dados que vê no dashboard e nos relatórios, a menos que seja aplicada [RLS (Segurança em nível de linha)](service-admin-rls.md). Os colegas com quem o partilhar podem partilhar o dashboard com os respetivos colegas, se assim o permitir. As pessoas fora da sua organização também podem ver e interagir com o dashboard, mas não podem partilhá-lo. 

Também pode [partilhar um dashboard a partir de qualquer uma das aplicações móveis do Power BI](mobile-share-dashboard-from-the-mobile-apps.md). Pode partilhar dashboards a partir do serviço do Power BI e das aplicações móveis do Power BI, mas não a partir do Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Vídeo: Partilhar um dashboard
Veja a Amanda a partilhar o dashboard dela com colegas dentro e fora da empresa. Em seguida, siga as instruções passo a passo abaixo do vídeo para experimentar.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard"></a>Partilhar um dashboard
1. Em A minha área de trabalho ou numa área de trabalho de aplicação, abra um dashboard e selecione **Partilhar** ![Ícone de partilha](media/service-share-dashboards/power-bi-share-icon.png).
2. Na caixa superior, introduza os endereços de e-mail completos de pessoas, grupos de distribuição ou grupos de segurança. Não pode partilhar com listas de distribuição dinâmicas. 
   
   Pode partilhar com pessoas cujos endereços são externos à sua organização, mas irá ver um aviso.
   
   ![Aviso sobre partilha externa](media/service-share-dashboards/power-bi-share-dialog-warning.png)  
3. Se preferir, adicione uma mensagem. É opcional.
4. Para permitir que os seus colegas partilhem o seu dashboard com outras pessoas, marque a opção **Permitir aos destinatários partilhar o dashboard**.
   
   Permitir a partilha a outras pessoas denomina-se *voltar a partilhar*. Se o permitir, eles podem voltar a partilhar a partir do serviço do Power BI e das aplicações móveis ou encaminhar o convite por e-mail para outras pessoas na sua organização. O convite expira após um mês. As pessoas fora da sua organização não podem voltar a partilhar. Como proprietário do dashboard, pode desativar a possibilidade de voltar a partilhar ou revogá-la individualmente. Consulte [Impedir a partilha de um dashboard ou impedir outras pessoas de partilhar](service-share-dashboards.md#stop-sharing-a-dashboard-or-stop-others-from-sharing), mais abaixo.
5. Selecione **Partilhar**.
   
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
   
    As pessoas fora da sua organização estão listadas como **Convidado**.

## <a name="stop-sharing-a-dashboard-or-stop-others-from-sharing"></a>Deixar de partilhar um dashboard ou impedir outras pessoas de partilhar
Apenas o proprietário do dashboard pode ativar ou desativar a possibilidade de voltar a partilhar.

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

4. Na caixa de diálogo **Remover acesso**, pode decidir se também quer remover o acesso a conteúdos relacionados, como relatórios e conjuntos de dados. Se remover itens com um ícone de aviso ![ícone de aviso do Power BI](media/service-share-dashboards/power-bi-warning-icon.png), será melhor remover os conteúdos relacionados, porque não serão apresentados de forma adequada.

## <a name="share-a-dashboard-with-people-outside-your-organization"></a>Partilhar um dashboard com pessoas fora da sua organização
Quando partilha com pessoas fora da sua organização, elas recebem um e-mail com uma ligação para o dashboard partilhado, e elas têm de iniciar sessão no Power BI para ver o dashboard. Se estas não tiverem uma licença do Power BI Pro, poderão inscrever-se numa após clicarem na ligação.

Após iniciarem sessão, verão o dashboard partilhado nas respetivas janelas do browser sem o painel de navegação à esquerda, não no respetivo portal do Power BI normal. Têm de adicionar a ligação aos Favoritos para acederem a este dashboard no futuro.

Não podem editar conteúdos neste dashboard ou relatório. Elas podem interagir com os gráficos no relatório (realce cruzado) e alterar filtros/segmentações de dados disponíveis nos relatórios ligados ao dashboard, mas não podem guardar as alterações.

Apenas os destinatários diretos podem ver o dashboard partilhado. Por exemplo, se tiver enviado o e-mail para Vicki@contoso.com, apenas a Vicki poderá ver o dashboard. Mais ninguém consegue ver esse dashboard (mesmo que tenham uma ligação) e a Vicki tem de utilizar o mesmo endereço de e-mail para aceder a esse dashboard. Se ela iniciar sessão com outro endereço de e-mail, também não terá acesso ao dashboard.

As pessoas de fora da sua organização não poderão ver os dados se a segurança em nível de linha ou de função for implementada nos modelos de tabela Analysis Services no local.

Se enviar uma ligação de uma aplicação móvel do Power BI para pessoas externas à sua organização, quando estas clicarem na ligação, o dashboard é aberto num browser, não na aplicação móvel do Power BI.

## <a name="limitations-and-considerations"></a>Limitações e considerações
Elementos a ter em conta sobre a partilha de dashboards:

* Em geral, o utilizador e os seus colegas veem os mesmos dados no dashboard. Portanto, se tiver permissões para ver mais dados do que os seus colegas, eles conseguirão ver todos os seus dados no seu dashboard. No entanto, se a [RLS (Segurança em nível de linha)](service-admin-rls.md) for aplicada ao conjunto de dados subjacente a um dashboard, as credenciais de cada pessoa serão utilizadas para determinar a que dados podem aceder.
* Todas as pessoas com quem partilha o dashboard podem vê-lo e interagir com os seus relatórios na [Vista de Leitura](service-report-open-in-reading-view.md). Não podem criar relatórios ou guardar alterações a relatórios existentes.
* Ninguém pode ver ou transferir o conjunto de dados.
* Todas as pessoas podem, manualmente, [atualizar os dados do dashboard](refresh-data.md).
* Se utilizar o Office 365 para e-mail, pode partilhar com membros de um grupo de distribuição ao introduzir o endereço de e-mail associado ao grupo de distribuição.
* Os colegas com o mesmo domínio de e-mail que o utilizador e os colegas com um domínio diferente, mas que estejam registados no mesmo inquilino, podem partilhar o dashboard com outras pessoas. Por exemplo, suponhamos que os domínios contoso.com e contoso2.com estão registados no mesmo inquilino. Se o seu endereço de e-mail for konrads@contoso.com, isso quer dizer que ravali@contoso.com e gustav@contoso2.com podem partilhar, desde que lhes tenha dado permissão para partilhar.
* Se os seus colegas já tiverem acesso a um dashboard específico, poderá enviar uma ligação direta para esse dashboard ao copiar o URL quando estiver no dashboard. Por exemplo: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* De igual modo, se os seus colegas já tiverem acesso a um dashboard específico, pode [enviar uma ligação direta para o relatório subjacente](service-share-reports.md). 

## <a name="troubleshoot-sharing"></a>Resolução de problemas da partilha

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Os destinatários do meu dashboard vêm um ícone de cadeado num mosaico ou a mensagem "Permissão necessária"

Se as pessoas com quem partilha vêm um ícone de cadeado num mosaico ou a mensagem "Permissão necessária" quanto tentam ver um relatório, tem de lhes dar permissão para o conjunto de dados subjacente. Eis como fazê-lo.

1. Aceda ao separador **Conjuntos de dados** na sua lista de conteúdos.

1. Selecione as reticências (**...**) junto ao conjunto de dados > **Gerir permissões**.

    ![Gerir permissões](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

3. Selecione **Adicionar utilizador**.

    ![Selecione Adicionar utilizador](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Introduza os endereços de e-mail completos de pessoas, grupos de distribuição ou grupos de segurança. Não pode partilhar com listas de distribuição dinâmicas.

    ![Adicionar endereços de e-mail](media/service-share-dashboards/power-bi-add-user-dataset.png)

5. Selecione **Adicionar**.

### <a name="i-cant-share-a-dashboard"></a>Não consigo partilhar um dashboard

Para partilhar um dashboard, tem de ter permissão para voltar a partilhar os conteúdos subjacentes: relatórios e conjuntos de dados relacionados. Se vir uma mensagem a informá-lo que não pode partilhar, peça ao autor do relatório que lhe dê permissão para voltar a partilhar esses relatórios e conjuntos de dados.


## <a name="next-steps"></a>Passos seguintes
* Tem comentários? Aceda ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.
* [Como devo colaborar e partilhar os meus dashboards e relatórios?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar apenas um relatório do Power BI](service-share-reports.md)
* Perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

