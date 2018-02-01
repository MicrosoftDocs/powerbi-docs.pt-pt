---
title: "Criar e publicar aplicações com dashboards e relatórios no Power BI"
description: "Aprenda a criar e publicar aplicações, que são coleções de dashboards e relatórios criados para fornecer métricas importantes à sua organização."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/16/2018
ms.author: maggies
ms.openlocfilehash: 89c376451199aec0a6f464f3298df44d468f37d2
ms.sourcegitcommit: 259d7689bcb1683d4d63a245a9b02becea072139
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="create-and-publish-apps-with-dashboards-and-reports-in-power-bi"></a>Criar e publicar aplicações com dashboards e relatórios no Power BI

No Power BI, pode criar *aplicações* para reunir dashboards e relatórios relacionados, tudo num só local, e publicá-los para grandes grupos de pessoas na sua organização. Pode também ligar a [Aplicações do Power BI para serviços externos](service-connect-to-services.md), como o Google Analytics e o Microsoft Dynamics CRM.

![Aplicações do Power BI](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

Muitas vezes, os utilizadores empresariais precisam de vários dashboards e relatórios do Power BI para realizarem os seus negócios. As aplicações reúnem as partes, para que os utilizadores não tenham de se lembrar dos nomes e localizações de todos os dashboards.  

Nas aplicações do Power BI, agora em pré-visualização, pode criar coleções de dashboards e relatórios e publicar estas aplicações para toda a organização ou para pessoas específicas ou grupos. Para si, como criador ou administrador de relatórios, as aplicações facilitam a gestão das permissões em coleções de dashboards.

Os utilizadores empresariais podem instalar estas aplicações a partir do Microsoft AppSource ou pode enviar-lhes uma ligação direta. Eles podem facilmente encontrar e voltar aos seus conteúdos porque estes se encontram num só local. Obtêm as atualizações automaticamente e pode controlar a frequência de atualização dos dados. Leia mais sobre a [experiência de aplicação para utilizadores empresariais](service-install-use-apps.md).

### <a name="apps-and-organizational-content-packs"></a>Pacotes de conteúdos de aplicações e organizacionais
As aplicações são a evolução dos pacotes de conteúdos organizacionais. Se já tiver pacotes de conteúdos organizacionais, estes continuarão a funcionar lado a lado com as aplicações.

Agora que tem uma descrição geral das aplicações, vamos abordar as *áreas de trabalho de aplicações*, onde criar aplicações. 

## <a name="video-apps-and-app-workspaces"></a>Vídeo: aplicações e áreas de trabalho de aplicações
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>Licenças para aplicações
Como criador de aplicações, precisa de uma licença do Power BI Pro. Para os utilizadores da aplicação, existem duas opções.

* Opção 1: todos os utilizadores empresariais precisam de licenças do **Power BI Pro** para ver a sua aplicação. 
* Opção 2: os utilizadores gratuitos na sua organização podem ver os conteúdos da aplicação, se esta residir numa capacidade do Power BI Premium. Leia [O que é o Power BI Premium?](service-premium.md) para obter detalhes.

## <a name="app-workspaces"></a>Áreas de trabalho de aplicações
As *Áreas de trabalho de aplicações* são os locais onde pode criar aplicações, por isso terá de criar uma área de trabalho de aplicação em primeiro lugar, antes de criar a aplicação. Se já tiver trabalhado numa área de trabalho de grupo do Power BI, estará familiarizado com as áreas de trabalho de aplicações. São a evolução das áreas de trabalho de grupo – áreas de teste e contentores para o conteúdo na aplicação. 

Pode adicionar colegas a estas áreas de trabalho como membros ou administradores. Todos os membros e administradores da área de trabalho da aplicação têm licenças do Power BI Pro. Na área de trabalho, todos podem colaborar nos dashboards, relatórios e outros artigos que planear publicar para um vasto público ou mesmo para toda a organização. 

Quando os conteúdos estiverem prontos, selecione os dashboards e relatórios que pretende publicar e poderá publicar a aplicação. Pode enviar uma ligação direta para esse vasto público ou pode localizar a aplicação a partir do separador Aplicações, acedendo a **Transferir e explorar mais aplicações da AppSource**. Essas pessoas não conseguem modificar os conteúdos da aplicação, mas podem interagir no serviço Power BI ou numa das aplicações móveis – filtrando, destacando e ordenando os próprios dados. 

## <a name="create-an-app-workspace"></a>Criar uma área de trabalho de aplicação
[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Está vazia, pelo que, agora pode adicionar conteúdo à mesma. Tenha em atenção que, quando a criar, poderá ter de aguardar uma hora, para a área de trabalho ser propagada para o Office 365. 

Adicionar conteúdo é como adicionar conteúdo a A minha área de trabalho, exceto que as outras pessoas na área de trabalho também a podem ver e trabalhar nela. Uma grande diferença é que, quando tiver concluído, pode publicar o conteúdo como uma aplicação. Enquanto estiver na área de trabalho da aplicação pode carregar ou ligar aos ficheiros ou ligar aos serviços de terceiros, tal como faria na sua própria área de trabalho. Por exemplo:

* [Ligar a serviços](service-connect-to-services.md), como o Microsoft Dynamics CRM, Salesforce ou Google Analytics.
* [Obter dados de ficheiros](service-get-data-from-files.md), como ficheiros do Excel, CSV ou Power BI Desktop (PBIX).

## <a name="add-an-image-to-your-app-optional"></a>Adicionar uma imagem à aplicação (opcional)
Por predefinição, o Power BI cria um círculo ligeiramente colorido para a aplicação, com as iniciais da aplicação. Mas talvez o queira personalizar com uma imagem. Para adicionar uma imagem, precisa de uma licença do Exchange Online.

1. Selecione **Áreas de trabalho**, selecione as reticências (…) junto ao nome da área de trabalho e, em seguida, **Membros**. 
   
     ![Selecionar Membros da Área de Trabalho](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    A conta do Office 365 Outlook para a área de trabalho é aberta numa nova janela do browser.
2. Quando paira o rato sobre o círculo colorido no canto superior esquerdo, transforma-se num ícone de lápis. Selecione-o.
   
     ![Ícone de lápis do Office 365](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Selecione novamente o ícone de lápis e localize a imagem que pretende utilizar.
   
     ![Selecionar o lápis novamente](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)
4. Selecione **Guardar**.
   
     ![Selecionar Guardar](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    A imagem substitui o círculo colorido na janela do Office 365 Outlook. 
   
     ![Imagem personalizada](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    Em alguns minutos, irá ser também apresentada na aplicação do Power BI.
   
     ![Imagem personalizada](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="publish-your-app"></a>Publicar a aplicação
Quando os dashboards e relatórios da área de trabalho da aplicação estiverem prontos, publique-os como uma aplicação. Lembre-se de que não tem de publicar todos os relatórios e dashboards da área de trabalho. Pode publicar apenas aqueles que estão prontos. 

1. Na vista de lista da área de trabalho, tem de decidir quais os dashboards e relatórios que pretende incluir na aplicação.

     ![Selecionar o dashboard a publicar](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Se optar por não publicar um relatório, verá um aviso junto ao relatório e dashboard relacionado. Pode publicar a aplicação, mas o dashboard relacionado não terá os mosaicos desse relatório.

     ![Aviso sobre o dashboard relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

1. Selecione o botão **Publicar aplicação** no canto superior direito para iniciar o processo de partilhar todo o conteúdo dessa área de trabalho.
   
     ![Publicar aplicação](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

2. Em primeiro lugar, em **Detalhes**, preencha a descrição para ajudar as pessoas a encontrarem a aplicação. Pode definir uma cor de fundo para personalizá-la.
   
     ![Detalhes da aplicação](media/service-create-distribute-apps/power-bi-apps-details.png)

3. Em seguida, em **Conteúdo**, veja o conteúdo que vai ser publicado como parte da aplicação – tudo o que selecionou na área de trabalho. Também pode definir a página de destino da aplicação – o dashboard ou relatório que as pessoas irão ver primeiro quando entrarem na sua aplicação. Pode escolher **Nenhum**. As pessoas serão então direcionadas para uma lista de todos os conteúdos da aplicação. 
   
     ![Conteúdo da aplicação](media/service-create-distribute-apps/power-bi-apps-content.png)

4. Por último, em **Acesso**, decida quem tem acesso à aplicação: todas as pessoas na sua organização, pessoas específicas ou grupos de segurança do Active Directory. 

5. Quando selecionar **Concluir**, verá uma mensagem a confirmar que está pronto para publicar. Na caixa de diálogo de êxito, pode copiar o URL, que é uma ligação direta para esta aplicação, e enviá-lo às pessoas com as quais partilhou a aplicação.
   
     ![Conclusão da aplicação](media/service-create-distribute-apps/power-bi-apps-success.png)

Os utilizadores empresariais que tenham publicado a aplicação podem localizá-la de duas formas diferentes. Pode enviar-lhes a ligação direta para a aplicação ou podem procurá-la no Microsoft AppSource, onde veem todas as aplicações a que podem aceder. Depois disso, sempre que acederem a Aplicações, verão esta aplicação na respetiva lista.

Leia mais sobre a [experiência de aplicação para utilizadores empresariais](service-install-use-apps.md).

## <a name="change-your-published-app"></a>Alterar a aplicação publicada
Depois de publicar a aplicação, poderá querer alterá-la ou atualizá-la. É fácil atualizá-la se for um administrador ou membro da área de trabalho da aplicação. 

1. Abra a área de trabalho de aplicação que corresponde à aplicação. 
   
     ![Abrir área de trabalho](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. Abra o dashboard ou relatório. Pode constatar que pode efetuar todas as alterações que desejar.
   
     A área de trabalho da aplicação é a área de teste, pelo que as suas alterações não são enviadas por push em direto para a aplicação até a publicar novamente. Isto permite-lhe efetuar alterações sem afetar as aplicações publicadas.  
 
1. Volte à lista de conteúdos da área de trabalho da aplicação e selecione **Atualizar aplicação**.
   
     ![Botão Atualizar aplicação](media/service-create-distribute-apps/power-bi-app-update-button.png)
4. Atualize os **Detalhes**, o **Conteúdo**, e o **Acesso**, se necessário, e selecione **Atualizar aplicação**.
   
     ![Botão Atualizar aplicação](media/service-create-distribute-apps/power-bi-app-update-complete.png)

As pessoas com as quais partilhou a aplicação veem automaticamente a versão atualizada da aplicação. 

## <a name="unpublish-an-app"></a>Anular publicação de uma aplicação
Qualquer membro da área de trabalho da aplicação pode anular a publicação da aplicação.

* Na área de trabalho da aplicação, selecione as reticências (**...** ) no canto superior direito > **Anular aplicação**.
  
     ![Anular publicação da aplicação](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Esta ação desinstala a aplicação de todas as pessoas para as quais a publicou e já não terão acesso à mesma. Não elimina a área de trabalho da aplicação nem os respetivos conteúdos.

## <a name="power-bi-apps-faq"></a>Perguntas frequentes sobre as aplicações do Power BI
### <a name="how-are-app-workspaces-different-from-group-workspaces"></a>Em que divergem as áreas de trabalho de aplicações das áreas de trabalho de grupo?
Nesta versão, mudámos o nome de todas as áreas de trabalho de grupo para áreas de trabalho de aplicação. Pode publicar uma aplicação a partir de qualquer uma destas áreas de trabalho. A funcionalidade permanece igual à de áreas de trabalho de grupo, na maior parte. Nos próximos meses, planeamos as seguintes melhorias para as áreas de trabalho de aplicações: 

* A criação de áreas de trabalho de aplicações não irá criar entidades correspondentes no Office 365, como nas áreas de trabalho de grupo. Portanto, pode criar qualquer número de áreas de trabalho da aplicações sem se preocupar com a criação de grupos do Office 365 em segundo plano (pode continuar a utilizar o OneDrive para Empresas de um grupo do Office 365 para armazenar os ficheiros). 
* Atualmente, só pode adicionar indivíduos aos membros da lista de administradores. Em breve, poderá adicionar vários grupos de segurança do Active Directory ou grupos modernos a estas listas, para uma gestão mais fácil.  

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Quais são as diferenças entre as aplicações e os pacotes de conteúdos organizacionais?
As aplicações são uma evolução e simplificação dos pacotes de conteúdos, com algumas diferenças principais. 

* Depois de os utilizadores empresariais instalarem um pacote de conteúdos, este perde a respetiva identidade agrupada: é apenas uma lista de dashboards e relatórios misturados com outros dashboards e relatórios. As aplicações, por outro lado, mantêm o respetivo agrupamento e identidade, mesmo após a instalação. Isto torna mais fácil aos utilizadores empresariais continuarem a navegar nelas ao longo do tempo.  
* Pode criar vários pacotes de conteúdos a partir de qualquer área de trabalho, mas uma aplicação tem uma relação de 1:1 com a respetiva área de trabalho. Acreditamos que isto faz com que as aplicações sejam mais fáceis de compreender e manter ao longo do tempo. Veja a secção de planos do blogue do Power BI para obter mais informações sobre como estamos a planear melhorar esta área. 
* Ao longo do tempo, planeamos preterir pacotes de conteúdos organizacionais, pelo que recomendamos que crie aplicações a partir de agora.  

### <a name="what-about-read-only-members-in-groups"></a>E os membros só de leitura em grupos?
Em grupos específicos, pode adicionar membros só de leitura que só podem ver o conteúdo. O problema principal desta abordagem era que não podia adicionar grupos de segurança como membros. Nas aplicações, pode publicar uma versão só de leitura da sua área de trabalho da aplicação destinada ao grande público, incluindo grupos de segurança. Pode testar as suas alterações dos dashboards e relatórios na aplicação, sem afetar os utilizadores finais. Recomendamos a utilização de aplicações desta forma no futuro. A longo prazo, planeamos preterir também os membros só de leitura de áreas de trabalho.  

## <a name="next-steps"></a>Passos seguintes
* [Instalar e utilizar aplicações no Power BI](service-install-use-apps.md)
* [Aplicações do Power BI para serviços externos](service-connect-to-services.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
