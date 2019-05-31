---
title: Criar áreas de trabalho clássicas no Power BI
description: Saiba como criar áreas de trabalho, coleções de dashboards, relatórios e relatórios paginados criados para proporcionar métricas importantes para a sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: dcf9b8befabfec98fcae154e6276f8e698b3ddc2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61151050"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Criar áreas de trabalho clássicas no Power BI

No Power BI, pode criar *áreas de trabalho*, coloca a colaborar com colegas para criar e refinar coleções de dashboards, relatórios e relatórios paginados. Em seguida, pode agrupar a coleção em *aplicações* que podem ser distribuídos para toda a organização ou para pessoas específicas ou grupos. 

**Sabia que?** O Power BI oferece uma nova experiência de área de trabalho, que agora é o padrão. Leia [organizar o trabalho em áreas de trabalho nova](service-new-workspaces.md) para obter detalhes sobre as novas áreas de trabalho. 

Quando cria uma área de trabalho clássica, está a criar um grupo do Office 365 subjacente, associado. Todas as tarefas de administração da área de trabalho são efetuadas no Office 365. Pode adicionar colegas a estas áreas de trabalho como membros ou administradores. Na área de trabalho, todos podem colaborar nos dashboards, relatórios e outros artigos que planeiam publicar para um público mais vasto. Todas as pessoas que adicionar à área de trabalho de uma aplicação precisam de ter uma licença do Power BI Pro. 

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicações e áreas de trabalho de aplicações
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-app-workspace-based-on-an-office-365-group"></a>Criar uma área de trabalho de aplicação clássico com base num grupo do Office 365

Quando cria uma área de trabalho de aplicação, esta é criada com base num grupo do Office 365.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Ao criá-la pela primeira vez, poderá ter de aguardar aproximadamente uma hora para a área de trabalho ser propagada para o Office 365. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Adicionar uma imagem à área de trabalho de aplicação do Office 365 (opcional)
Por predefinição, o Power BI cria um círculo ligeiramente colorido para a aplicação, com as iniciais da aplicação. Mas talvez o queira personalizar com uma imagem. Para adicionar uma imagem, precisa de uma licença do Exchange Online.

1. Selecione **Áreas de trabalho**, selecione as reticências (…) junto ao nome da área de trabalho e, em seguida, **Membros**. 
   
     ![Selecionar Membros da Área de Trabalho](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    A conta do Office 365 Outlook para a área de trabalho é aberta numa nova janela do browser.
2. Quando paira o rato sobre o círculo colorido no canto superior esquerdo, transforma-se num ícone de lápis. Selecione-o.
   
     ![Ícone de lápis do Office 365](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Selecione novamente o ícone de lápis e localize a imagem que pretende utilizar.
   
     ![Selecionar o lápis novamente](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)

     Imagens podem ser arquivos. bmp,. jpg ou. png. Seu tamanho de ficheiro pode ser grande, cópia de segurança para 3 MB. 

4. Selecione **Guardar**.
   
     ![Selecionar Guardar](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    A imagem substitui o círculo colorido na janela do Office 365 Outlook. 
   
     ![Imagem personalizada](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    Em alguns minutos, irá ser também apresentada na aplicação do Power BI.
   
     ![Imagem personalizada](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="add-content-to-your-app-workspace"></a>Adicionar conteúdos à área de trabalho da sua aplicação

Depois de ter criado uma área de trabalho de aplicação, é altura de adicionar conteúdos à mesma. O processo é igual ao de adicionar conteúdos em A Minha Área de Trabalho, exceto que as outras pessoas na área de trabalho também a podem ver e trabalhar nela. Uma grande diferença é que, quando tiver concluído, pode publicar o conteúdo como uma aplicação. Ao visualizar os conteúdos na lista de conteúdos de uma área de trabalho de aplicação, o nome da área de trabalho de aplicação é indicado como sendo o do proprietário.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Ligar a serviços de terceiros em áreas de trabalho de aplicações

As aplicações são disponibilizadas para todos os serviços de terceiros suportados pelo Power BI, para que possa obter dados dos serviços que utiliza mais facilmente, como o Microsoft Dynamics CRM, o Salesforce ou o Google Analytics. Pode publicar aplicações organizacionais para fornecer aos utilizadores os dados de que estes precisam.

Também pode ligar-se a serviços nas áreas de trabalho atuais através de pacotes de conteúdos organizacionais e de terceiros, como o Microsoft Dynamics CRM, o Salesforce ou o Google Analytics. Pondere migrar os seus pacotes de conteúdos organizacionais para aplicações.

## <a name="distribute-an-app"></a>Distribuir uma aplicação

Se pretender distribuir conteúdo oficial para uma vasta audiência dentro da sua organização, pode publicar uma aplicação da sua área de trabalho.  Quando o conteúdo estiver pronto, selecione os dashboards e relatórios que pretende publicar e, em seguida, publicá-la como uma *aplicação*. Pode criar uma aplicação a partir de cada área de trabalho.

A lista de aplicações no painel de navegação à esquerda mostra todas as aplicações de que instalou. Os seus colegas podem obter a sua aplicação de algumas formas diferentes. 
- Eles possam localizar e instalar a aplicação do Microsoft AppSource
- Pode enviar-lhes uma ligação direta. 
- Pode instalar aplicações automaticamente nas contas do Power BI dos seus colegas de trabalho, se o administrador do Power BI lhe der permissão. 

Os utilizadores veem o conteúdo da aplicação atualizada automaticamente depois de publicar uma atualização da sua área de trabalho. Pode controlar a frequência de atualização dos dados ao definir a agenda de atualização em conjuntos de dados utilizados pelo conteúdo da aplicação na sua área de trabalho. Ver [publicar uma aplicação a partir de novas áreas de trabalho no Power BI](service-create-distribute-apps.md) para obter detalhes.

## <a name="power-bi-classic-apps-faq"></a>Aplicações do Power BI clássicas FAQ

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Quais são as diferenças entre as aplicações e os pacotes de conteúdos organizacionais?
As aplicações são a evolução dos pacotes de conteúdos organizacionais. Se já tiver pacotes de conteúdos organizacionais, estes continuarão a funcionar lado a lado com as aplicações. As aplicações e os pacotes de conteúdos apresentam algumas diferenças importantes. 

* Depois de os utilizadores empresariais instalarem um pacote de conteúdos, este perde a respetiva identidade agrupada: é apenas uma lista de dashboards e relatórios misturados com outros dashboards e relatórios. As aplicações, por outro lado, mantêm o respetivo agrupamento e identidade, mesmo após a instalação. Este agrupamento torna mais fácil aos utilizadores empresariais continuarem a navegar nas aplicações ao longo do tempo.
* Pode criar vários pacotes de conteúdos a partir de qualquer área de trabalho, mas uma aplicação tem uma relação de 1:1 com a respetiva área de trabalho. 
* Ao longo do tempo, planeamos preterir pacotes de conteúdos organizacionais, pelo que recomendamos que crie aplicações a partir de agora.  
* Com a pré-visualização da nova experiência de área de trabalho, estamos a dar os primeiros passos no sentido de preterir os pacotes de conteúdos organizacionais. Não os poderá utilizar ou criar em áreas de trabalho de pré-visualização.

Veja [How are the new app workspaces different from existing app workspaces?](service-new-workspaces.md#how-are-the-new-workspaces-different-from-current-workspaces) (Em que diferem as novas áreas de trabalho de aplicação das já existentes?) para comparar ambas as áreas de trabalho de aplicação. 

## <a name="next-steps"></a>Próximos passos
* [Instalar e utilizar aplicações no Power BI](service-create-distribute-apps.md)
- [Criar as novas áreas de trabalho (pré-visualização)](service-create-the-new-workspaces.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
