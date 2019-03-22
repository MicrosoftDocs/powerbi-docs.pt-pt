---
title: Publicar aplicações com dashboards e relatórios no Power BI
description: Saiba como publicar aplicações, que são coleções de dashboards e relatórios criados para fornecer métricas importantes à sua organização.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 051609c59e155cb6d5c2a982483a7e6d2d91a665
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964692"
---
# <a name="publish-apps-with-dashboards-and-reports-in-power-bi"></a>Publicar aplicações com dashboards e relatórios no Power BI

No Power BI pode publicar *aplicações* com coleções de dashboards e relatórios relacionados. Crie aplicações nas *áreas de trabalho de aplicações*, onde pode colaborar em conteúdos do Power BI com os seus colegas. Em seguida, pode publicar aplicações concluídas em grandes grupos de pessoas na sua organização. Leia mais sobre como [criar áreas de trabalho de aplicações](service-create-workspaces.md).

![Aplicações do Power BI](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

Muitas vezes, os utilizadores empresariais precisam de vários dashboards e relatórios do Power BI para realizarem os seus negócios. Nas aplicações do Power BI, pode criar coleções de dashboards e relatórios e publicar estas aplicações para toda a organização ou para pessoas específicas ou grupos. Enquanto criador ou administrador de relatórios, as aplicações facilitam a gestão de permissões nestas coleções.

Os utilizadores empresariais obtêm as suas aplicações de algumas formas diferentes. Se o administrador do Power BI lhe der permissão, pode instalar aplicações automaticamente nas contas do Power BI dos seus colegas de trabalho. Caso contrário, eles podem instalar as aplicações a partir da Microsoft AppSource ou pode enviar-lhes uma ligação direta. Eles podem facilmente encontrar e voltar aos seus conteúdos porque estes se encontram num só local. Não podem modificar os conteúdos da aplicação, mas podem interagir com a mesma no serviço Power BI ou numa das aplicações móveis para filtrar, realçar e ordenar os dados. Obtêm as atualizações automaticamente e pode controlar a frequência de atualização dos dados. Leia mais sobre a [experiência de aplicação para utilizadores empresariais](consumer/end-user-apps.md).

**Sabia que?** O Power BI está a apresentar uma nova experiência de área de trabalho em modo de pré-visualização. Leia [Criar as novas áreas de trabalho (pré-visualização)](service-create-the-new-workspaces.md) para saber como as áreas de trabalho irão mudar no futuro. 

## <a name="apps-and-organizational-content-packs"></a>Pacotes de conteúdos de aplicações e organizacionais
As aplicações são a evolução dos pacotes de conteúdos organizacionais. Os pacotes de conteúdos não estão disponíveis na pré-visualização das novas experiências de áreas de trabalho. Após a nova experiência de área de trabalho estar disponível para o público, não poderá utilizar pacotes de conteúdos nas novas áreas de trabalho que criar. Se ainda não o fez, comece a migrar os seus pacotes de conteúdos para as aplicações.

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicações e áreas de trabalho de aplicações
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>Licenças para aplicações
Todos os membros de uma área de trabalho de aplicações precisam de uma licença do Power BI Pro. Para os utilizadores da aplicação, existem duas opções.

* Opção 1: todos os utilizadores empresariais precisam de licenças do **Power BI Pro** para ver a aplicação. 
* Opção 2: se a aplicação residir numa capacidade do Power BI Premium, os utilizadores gratuitos na sua organização podem ver os conteúdos da mesma. Para mais detalhes, leia [O que é o Power BI Premium?](service-premium.md).

## <a name="publish-your-app"></a>Publicar a aplicação
Quando os dashboards e relatórios na sua área de trabalho estiverem prontos, pode escolher quais pretende publicar e publicá-los como uma aplicação. Pode enviar uma ligação direta para esse vasto público ou pode localizar a aplicação a partir do separador Aplicações, acedendo a **Transferir e explorar mais aplicações da AppSource**. 

1. Na vista de lista da área de trabalho, tem de decidir quais os dashboards e relatórios que pretende incluir na aplicação.

     ![Selecionar o dashboard a publicar](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Se optar por não publicar um relatório, verá um aviso junto ao relatório e dashboard relacionado. Pode publicar a aplicação, mas o dashboard relacionado não terá os mosaicos desse relatório.

     ![Aviso sobre o dashboard relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selecione o botão **Publicar aplicação** no canto superior direito para iniciar o processo de partilhar todo o conteúdo dessa área de trabalho.
   
     ![Publicar aplicação](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Em **Detalhes**, preencha a descrição para ajudar as pessoas a encontrarem a aplicação. Pode definir uma cor de fundo para personalizá-la.
   
     ![Detalhes da aplicação](media/service-create-distribute-apps/power-bi-apps-details.png)

4. Em **Conteúdo**, veja o conteúdo que vai ser publicado como parte da aplicação – tudo o que selecionou na área de trabalho. Também pode definir a página de destino da aplicação – o dashboard ou relatório que as pessoas irão ver primeiro quando entrarem na sua aplicação. Pode escolher **Nenhum**. As pessoas serão então direcionadas para uma lista de todos os conteúdos da aplicação. 
   
     ![Conteúdo da aplicação](media/service-create-distribute-apps/power-bi-apps-content.png)

5. Em **Acesso**, decida quem tem acesso à aplicação: todas as pessoas na sua organização, pessoas específicas ou grupos de segurança do Active Directory. Se tiver permissões, pode optar por instalar a aplicação automaticamente para os destinatários. Um administrador do Power BI pode ativar esta definição no Portal de Administração do Power BI. Leia mais sobre como [instalar automaticamente uma aplicação](#how-to-install-an-app-automatically-for-end-users).

    ![Acesso à aplicação](media/service-create-distribute-apps/power-bi-apps-access.png)

6. Quando selecionar **Concluir**, verá uma mensagem a confirmar que está pronto para publicar. Na caixa de diálogo de êxito, pode copiar o URL, que é uma ligação direta para esta aplicação, e enviá-lo às pessoas com as quais partilhou a aplicação.
   
     ![Conclusão da aplicação](media/service-create-distribute-apps/power-bi-apps-success.png)

Leia mais sobre a [experiência de aplicação para utilizadores empresariais](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Alterar a aplicação publicada
Depois de publicar a aplicação, poderá querer alterá-la ou atualizá-la. É fácil atualizá-la se for administrador ou membro da área de trabalho da aplicação, ou um contribuidor numa nova área de trabalho de aplicação. 

1. Abra a área de trabalho de aplicação que corresponde à aplicação. 
   
     ![Abrir área de trabalho](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. Abra o dashboard ou relatório. Pode constatar que pode efetuar todas as alterações que desejar.
   
     A área de trabalho da aplicação é a área de teste, pelo que as suas alterações não são apresentadas em direto na aplicação até a publicar novamente. Isto permite-lhe efetuar alterações sem afetar as aplicações publicadas.  
 
3. Volte à lista de conteúdos da área de trabalho da aplicação e selecione **Atualizar aplicação**.
   
     ![Botão Atualizar aplicação](media/service-create-distribute-apps/power-bi-app-update-button.png)

4. Atualize os **Detalhes**, o **Conteúdo**, e o **Acesso**, se necessário, e selecione **Atualizar aplicação**.
   
     ![Botão Atualizar aplicação](media/service-create-distribute-apps/power-bi-app-update-complete.png)

As pessoas com as quais partilhou a aplicação veem automaticamente a versão atualizada da aplicação. 

## <a name="automatically-install-apps-for-end-users"></a>Instalar automaticamente as aplicações para os utilizadores finais
As aplicações fornecem dados que os seus utilizadores finais precisam para realizarem as suas tarefas. Se um administrador lhe der permissões, pode instalar automaticamente aplicações para utilizadores finais, o que facilita a distribuição das aplicações adequadas de acordo com as pessoas ou grupos. A sua aplicação aparecerá automaticamente na Lista de conteúdos de aplicações dos seus utilizadores finais, pelo que os mesmos não terão de a procurar no Microsoft AppSource nem de seguir uma ligação de instalação. Esta ação torna mais simples implementar conteúdo padrão do Power BI para os seus utilizadores.

### <a name="how-to-install-an-app-automatically-for-end-users"></a>Como instalar uma aplicação automaticamente para os utilizadores finais
Após o administrador lhe ter atribuído permissões, tem uma nova opção para **instalar a aplicação automaticamente**. Ao selecionar a caixa e selecionar **Concluir** (ou **Atualizar aplicação**, para aplicações existentes), a aplicação é enviada por push para todos os utilizadores ou grupos incluídos na secção **Permissões** da aplicação, no separador **Acesso**.

![Permitir aplicações push](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-were-pushed-to-them"></a>Como é que os utilizadores obtêm as aplicações que lhes foram enviadas por push
Após enviar uma aplicação por push, esta é apresentada automaticamente na lista Aplicações. Pode organizar as aplicações que utilizadores ou cargos específicos na sua organização precisam de ter à disposição.

![Permitir aplicações push](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Considerações para instalar automaticamente as aplicações
Seguem-se alguns aspetos a ter em atenção quando enviar aplicações por push para utilizadores finais:

* Instalar uma aplicação automaticamente para os utilizadores pode demorar algum tempo. A maioria das aplicações será instalada automaticamente, mas as aplicações push podem demorar algum tempo.  Depende do número de itens na aplicação e do número de pessoas com acesso. Recomendamos que envie aplicações por push fora do horário de expediente e com bastante tempo de antecedência antes que os utilizadores precisem delas. Confirme com vários utilizadores antes de enviar comunicação abrangente sobre a disponibilidade das aplicações.

* Atualize o seu browser. Antes de ver a aplicação enviada por push na lista Aplicações, o utilizador poderá ter de atualizar ou fechar e abrir novamente o browser.

* Se o utilizador não vir imediatamente a aplicação na lista Aplicações, deve atualizar ou fechar e abrir novamente o seu browser.

* Tente não sobrecarregar os utilizadores. Tenha cuidado e não envie demasiadas aplicações por push para que os seus utilizadores compreendam que as aplicações pré-instaladas são úteis. É recomendável controlar quem pode enviar aplicações por push para os utilizadores finais para coordenar os horários. Pode estabelecer um ponto de contacto para enviar aplicações por push para os utilizadores finais na sua organização.

* Os utilizadores convidados que não tenham aceite um convite não recebem as aplicações automaticamente instaladas.  

## <a name="unpublish-an-app"></a>Anular publicação de uma aplicação
Qualquer membro da área de trabalho da aplicação pode anular a publicação da aplicação.

>[!NOTE]
>Quando anular a publicação de uma aplicação, os utilizadores da aplicação perdem as suas personalizações. Isto significa que quaisquer marcadores pessoais, comentários ou subscrições associadas ao conteúdo na aplicação são perdidos. Apenas anule a publicação de uma aplicação se precisar de a remover.
> 
> 

* Na área de trabalho da aplicação, selecione as reticências (**...** ) no canto superior direito > **Anular aplicação**.
  
     ![Anular publicação da aplicação](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Esta ação desinstala a aplicação de todas as pessoas para as quais a publicou e já não terão acesso à mesma. Não elimina a área de trabalho da aplicação nem os respetivos conteúdos.

## <a name="next-steps"></a>Próximos passos
* [Create an app workspace](service-create-workspaces.md) (Criar uma área de trabalho de aplicação)
* [Instalar e utilizar aplicações no Power BI](consumer/end-user-apps.md)
* [Aplicações do Power BI para serviços externos](service-connect-to-services.md)
* [Portal de Administração do Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
