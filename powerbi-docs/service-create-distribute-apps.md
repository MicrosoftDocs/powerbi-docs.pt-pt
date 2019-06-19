---
title: Publicar uma aplicação no Power BI
description: Saiba como pode publicar novas aplicações, que são coleções de dashboards e relatórios com uma navegação incorporada.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: eccda071b6c6abc92640024c3587bafa71038dee
ms.sourcegitcommit: c122c1a8c9f502a78ccecd32d2708ab2342409f0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66826639"
---
# <a name="publish-an-app-in-power-bi"></a>Publicar uma aplicação no Power BI

No Power BI, pode criar conteúdos em pacote oficiais e, em seguida, distribuí-los para uma audiência vasta como uma *aplicação*. Crie aplicações nas *áreas de trabalho de aplicações*, onde pode colaborar em conteúdos do Power BI com os seus colegas. Em seguida, pode publicar aplicações concluídas em grandes grupos de pessoas na sua organização. 

![Aplicações do Power BI](media/service-create-distribute-apps/power-bi-new-apps.png)

Muitas vezes, os utilizadores empresariais precisam de vários dashboards e relatórios do Power BI para realizarem os seus negócios. Nas aplicações do Power BI, pode criar coleções de dashboards e relatórios e publicar estas aplicações para toda a organização ou para pessoas específicas ou grupos. Enquanto criador ou administrador de relatórios, as aplicações facilitam a gestão de permissões nestas coleções.

Os utilizadores empresariais obtêm as suas aplicações de algumas formas diferentes:

- Podem encontrar e instalar a sua aplicação a partir do Microsoft AppSource
- Pode enviar-lhes uma ligação direta.
- Pode instalar aplicações automaticamente nas contas do Power BI dos seus colegas de trabalho, se o administrador do Power BI lhe der permissão.

Pode criar a aplicação com a sua própria navegação incorporada, para que os utilizadores possam navegar facilmente nos seus conteúdos. Estes não podem modificar os conteúdos da aplicação. No entanto, podem interagir com a mesma no serviço Power BI ou numa das aplicações móveis para filtrar, realçar e ordenar os dados. Obtêm as atualizações automaticamente e pode controlar a frequência de atualização dos dados. Leia mais sobre a [experiência de aplicação para utilizadores empresariais](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licenças para aplicações
Para criar ou atualizar uma aplicação, necessita de uma licença do Power BI Pro. Para os *consumidores* da aplicação, existem duas opções.

* Opção 1: todos os utilizadores empresariais precisam de licenças do **Power BI Pro** para ver a aplicação. 
* Opção 2: se a área de trabalho da aplicação residir numa capacidade do Power BI Premium, os utilizadores gratuitos na sua organização podem ver os conteúdos da mesma. Para mais detalhes, leia [O que é o Power BI Premium?](service-premium.md).

## <a name="publish-your-app"></a>Publicar a aplicação
Quando os dashboards e relatórios na sua área de trabalho estiverem prontos, pode escolher quais pretende publicar e publicá-los como uma aplicação. 

1. Na vista de lista da área de trabalho, tem de decidir quais os dashboards e relatórios que pretende que sejam **Incluídos na aplicação**.

     ![Selecionar o dashboard a publicar](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Se optar por não incluir um relatório com um dashboard relacionado, verá um aviso junto ao relatório. Pode publicar a aplicação, mas o dashboard relacionado não terá os mosaicos desse relatório.

     ![Aviso sobre o dashboard relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selecione o botão **Publicar aplicação** no canto superior direito para iniciar o processo de criar e publicar uma aplicação a partir da área de trabalho.
   
     ![Publicar aplicação](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Em **Configuração**, preencha o nome e a descrição para ajudar as pessoas a encontrarem a aplicação. Pode definir uma cor de tema para personalizá-la. Também pode adicionar uma ligação para um site de suporte.
   
     ![Criar a sua aplicação](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. Em **Navegação**, selecione os conteúdos que pretende que sejam publicados como parte da aplicação. Em seguida, adicione a navegação da aplicação para organizar os conteúdos em secções. Veja [Conceber a experiência de navegação da aplicação](#design-the-navigation-experience-for-your-app) neste artigo para obter detalhes.
   
     ![Navegação da aplicação](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. Em **Permissões**, decida quem vai ter acesso à aplicação e o que essas pessoas podem fazer com a mesma. 
    - Em [áreas de trabalho clássicas](service-create-workspaces.md): todas as pessoas na sua organização, pessoas específicas ou grupos de segurança do Azure Active Directory (AAD).
    - Na [nova experiência de áreas de trabalho](service-create-the-new-workspaces.md): pessoas específicas, grupos de segurança e listas de distribuição do AAD e Grupos do Office 365. Todos os utilizadores da área de trabalho recebem automaticamente acesso à aplicação da mesma.
    - Pode permitir que os utilizadores da aplicação se liguem aos conjuntos de dados subjacentes da aplicação através da permissão Compilação. Estes conjuntos de dados serão apresentados em experiências de pesquisa de conjuntos de dados.
    - Pode permitir que os utilizadores da aplicação façam cópias dos relatórios na mesma para A minha área de trabalho. 
    
    >[!IMPORTANT]
    >Se a sua aplicação se basear em conjuntos de dados de outras áreas de trabalho, é responsável por garantir que todos os utilizadores da aplicação têm acesso aos conjuntos de dados subjacentes.
> 
>     


6. Pode instalar a aplicação automaticamente para os destinatários se o seu administrador do Power BI tiver ativado esta definição no Portal de Administração do Power BI. Leia mais sobre como [instalar automaticamente uma aplicação](#automatically-install-apps-for-end-users) neste artigo.

     ![Permissões da aplicação](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Quando selecionar **Publicar aplicação**, verá uma mensagem a confirmar que está pronto para publicar. Na caixa de diálogo **Partilhar esta aplicação**, pode copiar o URL que é uma ligação direta para esta aplicação.
   
     ![Conclusão da aplicação](media/service-create-distribute-apps/power-bi-apps-success.png)

Pode enviar essa ligação direta para as pessoas com quem a partilhou ou pode localizar a aplicação no separador Aplicações ao aceder a **Transferir e explorar mais aplicações do AppSource**. Leia mais sobre a [experiência de aplicação para utilizadores empresariais](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Alterar a aplicação publicada
Depois de publicar a aplicação, poderá querer alterá-la ou atualizá-la. É fácil atualizá-la se for um administrador ou membro da nova área de trabalho da aplicação. 

1. Abra a área de trabalho de aplicação que corresponde à aplicação. 
   
     ![Abrir área de trabalho](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Faça as alterações que pretende aos dashboards ou relatórios.
 
     A área de trabalho da aplicação é a área de teste, pelo que as suas alterações não são apresentadas em direto na aplicação até a publicar novamente. Isto permite-lhe efetuar alterações sem afetar as aplicações publicadas.  
 
    > [!IMPORTANT]
    > Se remover um relatório e atualizar a aplicação, mesmo que volte a adicioná-lo à mesma, os consumidores da sua aplicação irão perder todas as personalizações como marcadores, comentários, etc.  
 
3. Volte à lista de conteúdos da área de trabalho da aplicação e selecione **Atualizar aplicação** no canto superior direito.
   
1. Atualize as secções **Configuração**, **Navegação** e **Permissões** se necessário e, em seguida, selecione **Atualizar aplicação**.
   
As pessoas com as quais partilhou a aplicação veem automaticamente a versão atualizada da aplicação. 

## <a name="design-the-navigation-experience-for-your-app"></a>Conceber a experiência de navegação da aplicação
A opção **Novo construtor de navegação** permite-lhe criar uma navegação personalizada para a sua aplicação. A navegação personalizada torna mais fácil para os seus utilizadores localizarem e utilizarem os conteúdos na aplicação. As aplicações existentes têm esta opção desativada e, por predefinição, as novas aplicações têm esta opção ativada.

Quando a opção está desativada, pode selecionar a **Página de destino da aplicação** como sendo de **Conteúdo específico** (por exemplo, um dashboard ou relatório) ou selecionar **Nenhum** para mostrar uma lista básica de conteúdos ao utilizador.

Quando ativar o **Novo construtor de navegação**, pode conceber uma navegação personalizada. Por predefinição, todos os relatórios, dashboards e livros do Excel que incluiu na sua aplicação são apresentados como uma lista não hierárquica. 

![Navegação da aplicação](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Pode personalizar ainda mais a navegação da aplicação ao:
* Reordenar os itens com as teclas Seta Para Cima/Seta Para Baixo. 
* Mudar o nome dos itens nos **Detalhes do relatório**, nos **Detalhes do dashboard** e nos **Detalhes do livro**.
* Ocultar determinados itens da navegação.
* Utilizar a opção **Novo** para adicionar **secções** a conteúdos relacionados com grupos.
* Utilizar a opção **Novo** para adicionar uma **ligação** a um recurso externo ao painel de navegação esquerdo. 

Ao adicionar uma **ligação**, em **Detalhes da ligação** pode selecionar o local onde a ligação será aberta. Por predefinição, as ligações são abertas no **Separador atual**, mas pode selecionar as opções **Novo separador** ou **Área de conteúdo**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Considerações sobre a utilização da opção Novo construtor de navegação
Seguem-se alguns aspetos gerais a ter em atenção ao utilizar o novo construtor de navegação:
* As páginas de relatórios são apresentadas na área de navegação da aplicação como uma secção expansível
* Se desativar o novo construtor de navegação e, em seguida, publicar ou atualizar a sua aplicação, irá perder as personalizações que efetuou. Por exemplo, as secções, ordenações, ligações e nomes personalizados dos itens de navegação serão perdidos.

Ao adicionar ligações à navegação da sua aplicação e ao selecionar a opção Área de conteúdo:
* Certifique-se de que a ligação pode ser incorporada. Alguns serviços impedem a incorporação dos respetivos conteúdos em sites de terceiros, como o Power BI.
* A incorporação de conteúdos do serviço Power BI como relatórios ou dashboards noutras áreas de trabalho não é suportada. 
* Incorpore conteúdos do Power BI Report Server através do respetivo URL incorporado nativo a partir de uma implementação no local. Siga os passos indicados em [Criar o URL do Power BI Report Server](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) para obter o URL. Tenha em atenção que são aplicadas regras de autenticação normais, pelo que a visualização de conteúdos requer uma ligação ao servidor no local. 
* Será apresentado um aviso de segurança na parte superior dos conteúdos incorporados para indicar que estes não se encontram no Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Instalar automaticamente as aplicações para os utilizadores finais
Se um administrador lhe atribuir permissões, pode instalar aplicações de forma automática ao *emiti-las* por push para os utilizadores finais. Esta funcionalidade de push torna mais fácil distribuir as aplicações certas para as pessoas ou grupos certos. A sua aplicação é apresentada automaticamente na lista de conteúdos das Aplicações dos seus utilizadores finais. Estes não precisam de a procurar no Microsoft AppSource ou de seguir uma ligação de instalação. Veja como os administradores permitem a [emissão de aplicações por push para utilizadores finais](service-admin-portal.md#push-apps-to-end-users) no artigo do portal de administração do Power BI.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Como emitir uma aplicação por push automaticamente para os utilizadores finais
Após o administrador lhe ter atribuído permissões, tem uma nova opção para **instalar a aplicação automaticamente**. Ao selecionar a caixa de verificação e selecionar **Publicar aplicação** (ou **Atualizar aplicação**), a aplicação é emitida por push para todos os utilizadores ou grupos incluídos na secção **Permissões** da aplicação, no separador **Acesso**.

![Permitir aplicações push](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Como os utilizadores obtêm as aplicações que lhes emitiu por push
Após emitir uma aplicação por push, esta é apresentada automaticamente na lista Aplicações dos utilizadores. Desta forma, pode organizar as aplicações que utilizadores ou cargos específicos na sua organização precisam de ter à disposição.

![Permitir aplicações push](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Considerações para instalar automaticamente as aplicações
Seguem-se alguns aspetos a ter em atenção quando enviar aplicações por push para utilizadores finais:

* Instalar uma aplicação automaticamente para os utilizadores pode demorar algum tempo. A maioria das aplicações é instalada automaticamente, mas as aplicações emitidas por push podem demorar algum tempo.  Depende do número de itens na aplicação e do número de pessoas com acesso. Recomendamos que envie aplicações por push fora do horário de expediente e com bastante tempo de antecedência antes que os utilizadores precisem delas. Confirme com vários utilizadores antes de enviar comunicação abrangente sobre a disponibilidade das aplicações.

* Atualize o browser. Antes de ver a aplicação enviada por push na lista Aplicações, o utilizador poderá ter de atualizar ou fechar e abrir novamente o browser.

* Se os utilizadores não virem imediatamente a aplicação na lista Aplicações, devem atualizar ou fechar e abrir novamente o respetivo browser.

* Tente não sobrecarregar os utilizadores. Tenha cuidado e não envie demasiadas aplicações por push para que os seus utilizadores compreendam que as aplicações pré-instaladas são úteis. É recomendável controlar quem pode enviar aplicações por push para os utilizadores finais para coordenar os horários. Estabeleça um ponto de contacto para emitir aplicações por push para os utilizadores finais na sua organização.

* Os utilizadores convidados que não tiverem aceitado um convite não recebem as aplicações automaticamente instaladas.  

## <a name="allowing-users-to-connect-to-the-apps-underlying-datasets"></a>Permitir que os utilizadores se liguem aos conjuntos de dados subjacentes da aplicação
Ao selecionar a opção para permitir que todos os utilizadores se liguem aos conjuntos de dados subjacentes da aplicação, estes recebem a permissão Compilação para o conjunto de dados subjacente. Isto permite que os utilizadores [utilizem os conjuntos de dados da aplicação em áreas de trabalho](service-datasets-across-workspaces.md) para procurá-los no Power BI Desktop e nas experiências de obtenção de dados do serviço, bem como para criar relatórios e dashboards. 

Ao desselecionar esta opção, os novos utilizadores que adicionar à aplicação deixarão de receber a permissão Compilação. No entanto, as permissões existentes nos conjuntos de dados subjacentes não serão alteradas. Pode utilizar a interface de utilizador fornecida para remover manualmente a permissão Compilação dos utilizadores da aplicação que já não deviam tê-la. Saiba mais sobre a [permissão de compilação](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="allowing-users-to-make-a-copy-of-the-reports-in-the-app"></a>Permitir que os utilizadores façam cópias dos relatórios na aplicação
Ao selecionar a opção **Permitir que os utilizadores façam uma cópia dos relatórios nesta aplicação**, está a permitir que os utilizadores guardem quaisquer relatórios na aplicação em A Minha Área de Trabalho. Desta forma, os utilizadores podem personalizar os relatórios consoante as suas necessidades. Esta ação exige que a opção **Permitir que todos os utilizadores se liguem aos conjuntos de dados subjacentes da aplicação através da permissão Compilação** esteja ativada. Esta funcionalidade tem um comportamento semelhante ao da nova funcionalidade [Copiar relatórios de outras áreas de trabalho](service-datasets-copy-reports.md).

## <a name="unpublish-an-app"></a>Anular publicação de uma aplicação
Qualquer membro da área de trabalho da aplicação pode anular a publicação da aplicação.

>[!IMPORTANT]
>Quando anular a publicação de uma aplicação, os utilizadores da aplicação perdem as suas personalizações. Estes perderão todos os marcadores pessoais, comentários ou subscrições associadas aos conteúdos na aplicação. Apenas anule a publicação de uma aplicação se precisar de a remover.
> 
> 

* Na área de trabalho da aplicação, selecione as reticências ( **...** ) no canto superior direito > **Anular aplicação**.
  
     ![Anular publicação da aplicação](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Esta ação desinstala a aplicação de todas as pessoas para as quais a publicou e já não terão acesso à mesma. Não elimina a área de trabalho da aplicação nem os respetivos conteúdos.

## <a name="view-your-published-app"></a>Ver a aplicação publicada

Quando os consumidores da sua aplicação abrirem a mesma, verão o painel de navegação que criou em vez do painel de navegação esquerdo padrão do Power BI. As listas de navegação da aplicação apresentam os relatórios e dashboards nas secções que definiu. Também apresentam as páginas individuais em cada relatório em vez de apenas mostrarem o nome do relatório.

![Aplicação com navegação](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Próximos passos
* [Create an app workspace](service-create-workspaces.md) (Criar uma área de trabalho de aplicação)
* [Instalar e utilizar aplicações no Power BI](consumer/end-user-apps.md)
* [Aplicações do Power BI para serviços externos](service-connect-to-services.md)
* [Portal de Administração do Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
