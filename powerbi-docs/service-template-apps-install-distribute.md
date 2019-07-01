---
title: Distribuir aplicações de modelo na sua organização – Power BI
description: Aprenda a instalar, personalizar e distribuir aplicações de modelo na sua organização com o Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 158345c44f8801a98e19dcd9b4c7dde14aa6126b
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264529"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>Instalar e distribuir aplicações de modelo na sua organização – Power BI

É um analista do Power BI? Se for, veja este artigo para aprender a instalar *aplicações de modelo* para ligar a muitos dos serviços que utiliza para gerir a sua empresa, nomeadamente o Salesforce, o Microsoft Dynamics e o Google Analytics. Pode modificar o dashboard e os relatórios para satisfazer as necessidades da sua organização e, em seguida, distribuí-los aos seus colegas como uma *aplicação*. 

![Aplicações do Power BI instaladas](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Se estiver interessado em criar aplicações de modelo para distribuição própria, veja [Create a template app in Power BI](service-template-apps-create.md) (Criar uma aplicação de modelo no Power BI). Os parceiros do Power BI podem criar aplicações do Power BI com pouco ou nenhum código e implementá-las em clientes do Power BI. 

## <a name="prerequisites"></a>Pré-requisitos  

Eis os requisitos de instalação, personalização e distribuição de aplicações de modelo: 

- Uma [licença do Power BI Pro](service-self-service-signup-for-power-bi.md)
- Conhecer os [conceitos básicos do Power BI](service-basic-concepts.md)
- A ligação de instalação válida do criador da aplicação de modelo ou do AppSource. 
- Permissões para instalar aplicações de modelo. 

## <a name="install-a-template-app"></a>Instalar uma aplicação de modelo

Poderá receber uma ligação para uma aplicação de modelo. Caso contrário, pode procurar uma aplicação do seu interesse no AppSource. De qualquer forma, após instalar a aplicação de modelo, poderá modificar e distribuí-la para a sua organização.

### <a name="search-appsource-from-a-browser"></a>Procurar no AppSource a partir de um browser

Num browser, selecione a seguinte ligação para abrir o AppSource filtrado para apresentar aplicações do Power BI:

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>Procurar no AppSource a partir do serviço Power BI

1. No painel de navegação esquerdo do serviço Power BI, selecione **Aplicações** > **Obter aplicações**.

    ![Obter aplicações](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. No AppSource, selecione **Aplicações**.

    ![Procurar no AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. Navegue ou procure a aplicação e, em seguida, selecione **Obter agora**.

4. Na caixa de diálogo, selecione **Instalar**.

    ![Instalar aplicação](media/service-template-apps-install-distribute/power-install-dialog.png) Se tiver uma licença do Power BI Pro, a aplicação será instalada com a respetiva área de trabalho da aplicação. Irá personalizar a aplicação na área de trabalho associada.

    Quando a instalação for concluída com êxito, será apresentada uma notificação a indicar que a sua nova aplicação está pronta.
4. Selecione **Ir para a aplicação**.
5. Em **Comece já com a sua nova aplicação** , selecione uma das três opções:

    ![Comece já com a sua aplicação](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **Explorar a aplicação**: exploração de dados de exemplo básica. Comece aqui para obter o aspeto e funcionalidade da aplicação. 
    - **Ligar dados**: altere a origem de dados dos dados de exemplo para a sua própria origem de dados. Pode redefinir os parâmetros do conjunto de dados e as credenciais da origem de dados. Veja a secção [Limitações conhecidas](service-template-apps-tips.md#known-limitations) no artigo de sugestões sobre as aplicações de modelo. 
    - **Ir para a área de trabalho** (opção mais avançada): pode fazer todas as alterações permitidas pelo criador da aplicação.

    Em alternativa, ignore esta caixa de diálogo e aceda à área de trabalho diretamente através da opção **Áreas de trabalho** no painel de navegação esquerdo.
    >[!NOTE]
    >Instalar uma aplicação de modelo instalada numa *aplicação organizacional* e numa *área de trabalho de aplicação*. Leia mais sobre a [distribuição de aplicações no Power BI](service-create-distribute-apps.md).
 
6. Antes de partilhar a aplicação com os seus colegas, poderá querer ligar aos seus próprios dados. Também poderá querer modificar o relatório ou o dashboard de acordo com as necessidades da sua organização. Além disso, poderá adicionar outros relatórios ou dashboards neste passo.

   Se selecionar uma ligação de instalação para uma aplicação que não esteja listada no AppSource, obterá a caixa de diálogo de validação que lhe pede para confirmar a sua escolha.

   ![Instalar a aplicação](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >Para poder instalar aplicações de modelo que não estão listadas no AppSource, tem de pedir as permissões ao seu administrador. Veja as [Definições de aplicação de modelo do portal de administração](service-admin-portal.md#template-apps-settings) do Power BI para obter detalhes.

## <a name="update-and-distribute-the-app"></a>Atualizar e distribuir a aplicação

Depois de atualizar a aplicação para a sua organização, estará tudo pronto para publicá-la. Os passos são os mesmos que segue para publicar outra aplicação.

1. Quando concluir a personalização, na vista de lista da área de trabalho, selecione **Atualizar aplicação** no canto superior direito.  

    ![Iniciar a instalação da aplicação](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. Em **Detalhes**, pode modificar a descrição e a cor de fundo.

   ![Definir a cor e descrição da aplicação](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. Em **Conteúdo**, pode selecionar uma página de destino (o dashboard ou o relatório).

   ![Definir página de destino da aplicação](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. Em **Acesso**, pode conceder acesso a utilizadores específicos ou a toda a organização.  

   ![Definir o acesso à aplicação](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. Selecione **Atualizar aplicação**. 

6. Após publicar a aplicação com êxito, pode copiar a ligação e partilhá-la com as pessoas a quem concedeu acesso. Caso a tenha partilhado, essas pessoas também a verão no separador **A minha organização** no AppSource.

## <a name="next-steps"></a>Próximos passos 

[Criar áreas de trabalho com os seus colegas no Power BI](service-create-workspaces.md)





  

 
