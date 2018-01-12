---
title: "Registar uma aplicação para incorporar conteúdo do Power BI"
description: "Saiba como registar uma aplicação no Azure Active Directory para utilizar ao incorporar conteúdo do Power BI."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: 55bd0ed1be7b5853c6de786df34812fddafc1db8
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="register-an-azure-ad-app-to-embed-power-bi-content"></a>Registar uma aplicação do Azure AD para incorporar conteúdo do Power BI
Saiba como registar uma aplicação no Azure Active Directory (Azure AD) para utilizar ao incorporar conteúdo do Power BI.

Pode registar a aplicação com o Azure AD para permitir que a sua aplicação aceda às APIs REST do Power BI. Isto permitirá que estabeleça uma identidade para a sua aplicação e especifique permissões para recursos REST do Power BI.

> [!IMPORTANT]
> Antes de registar uma aplicação do Power BI, precisa de um [inquilino do Azure Active Directory e um utilizador organizacional](create-an-azure-active-directory-tenant.md). Se ainda não se inscreveu no Power BI com um utilizador no seu inquilino, o registo da aplicação não será concluído com êxito.
> 
> 

Existem duas formas de registar a sua aplicação. A primeira é com a [Ferramenta de Registo de Aplicações do Power BI](https://dev.powerbi.com/apps/) ou pode fazê-lo diretamente no portal do Azure. A Ferramenta de Registo de Aplicações Power BI é a opção mais fácil, pois há apenas alguns campos para preencher. Se pretender realizar alterações na sua aplicação, utilize o portal do Azure.

## <a name="register-with-the-power-bi-app-registration-tool"></a>Registar com a Ferramenta de Registo de Aplicações do Power BI
Precisa de registar a aplicação no **Azure Active Directory** para estabelecer uma identidade para a sua aplicação e especificar permissões para recursos REST do Power BI. Ao registar uma aplicação, como uma aplicação de consola ou de um site, receberá um identificador que é utilizado pela aplicação para se identificar perante os utilizadores aos quais está a pedir permissões.

Veja aqui como registar a sua aplicação com a Ferramenta de Registo de Aplicações do Power BI:

1. Vá para [dev.powerbi.com/apps](https://dev.powerbi.com/apps).
2. Selecione **Iniciar sessão com a sua conta do Power BI existente**.
3. Indique um **Nome de Aplicação**.
4. A seleção do tipo de Aplicação irá depender do tipo de aplicação que está a utilizar.
   
   * Utilize **Aplicação Web do lado do servidor** para aplicações Web ou APIs Web.
   * Utilize a **Aplicação nativa** para aplicações que são executadas nos dispositivos cliente. ***Também irá escolher **Aplicação nativa** se estiver a incorporar conteúdo para os seus clientes, independentemente de qual é a aplicação real. Mesmo para aplicações Web.***
5. Introduza um valor para **URL de Redirecionamento** e **URL da Home Page**. Qualquer URL válido irá funcionar.
   
    O **URL da Home Page** só está disponível se escolher **Aplicação Web do lado do servidor** para o tipo de aplicação.
   
    Para os exemplos de *incorporar para os seus clientes* e de *integrate-dashboard-web-app*, o URL de redirecionamento será `http://localhost:13526/redirect`. Para o exemplo de relatório e do mosaico, o URL de redirecionamento será `http://localhost:13526/`.
6. Escolha as APIs a que esta aplicação terá acesso. Para obter mais informações sobre as permissões de acesso do Power BI, veja [Permissões do Power BI](power-bi-permissions.md).
   
    ![](media/register-app/app-registration-apis.png)
7. Selecione **Registar Aplicação**.
   
    Em seguida, receberá um **ID de Cliente**. Se tiver selecionado **Aplicação Web do lado do servidor**, também irá receber um **Segredo do Cliente**. O **ID de Cliente** pode ser obtido a partir do portal do Azure, posteriormente, se for preciso. Se perder o **Segredo do Cliente**, terá de criar um novo no portal do Azure.

Agora pode utilizar a aplicação registada como parte da sua aplicação personalizada para interagir com o serviço Power BI.

> [!IMPORTANT]
> Se estiver a incorporar conteúdo para os seus clientes, terá de configurar permissões adicionais no portal do Azure. Para obter mais informações, veja [Apply permissions to your application (Aplicar permissões à sua aplicação)](#apply-permissions-to-your-application).
> 
> 

## <a name="register-with-the-azure-portal"></a>Registar com o portal do Azure
A outra opção para registar a aplicação é fazê-lo diretamente no portal do Azure. Para registar a sua aplicação, siga estes passos.

1. Aceite os [Termos da API do Microsoft Power BI](https://powerbi.microsoft.com/api-terms).
2. Inicie sessão no [portal do Azure](https://portal.azure.com).
3. Escolha o seu inquilino do Azure AD, ao selecionar a sua conta no canto superior direito da página.
4. No painel de navegação esquerdo, escolha **Mais Serviços**, selecione **Registos de Aplicação** em **Segurança + Identidade** e selecione **Novo Registo de Aplicação**.
   
    ![](media/register-app/azuread-new-app-registration.png)
5. Siga as instruções e crie uma nova aplicação.
   
   * Para Aplicações Web, indique o URL de Início de Sessão, que é o URL de base da sua aplicação, onde os utilizadores podem iniciar sessão, por exemplo http://localhost:13526.
   * Para Aplicações Nativas, indique um URI de Redirecionamento, que o Azure AD utiliza para devolver respostas de token. Introduza um valor específico na sua aplicação, por exemplo http://myapplication/redirect

Para obter mais informações sobre como registar aplicações no Azure Active Directory, veja [Integrar aplicações com o Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)

## <a name="how-to-get-the-client-id"></a>Como obter o ID do cliente
Ao registar uma aplicação, receberá um **ID de Cliente**.  O **ID do Cliente** é utilizado pelo aplicação para se identificar aos utilizadores aos quais está a pedir permissões.

Eis como obter um ID do cliente:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Escolha o seu inquilino do Azure AD, ao selecionar a sua conta no canto superior direito da página.
3. No painel de navegação esquerdo, escolha **Mais Serviços** e selecione **Registos de Aplicação**.
4. Selecione a aplicação em que pretende obter o ID de cliente.
5. Verá o **ID de Aplicação** listado como um GUID. Este é o ID de cliente para a aplicação.
   
    ![ID de Cliente listado como ID de Aplicação no registo de aplicação](media/register-app/powerbi-embedded-app-registration-client-id.png)

## <a name="apply-permissions-to-your-application-within-azure-ad"></a>Aplicar permissões à sua aplicação no Azure AD
> [!IMPORTANT]
> Esta secção aplica-se apenas às aplicações que estão a **incorporar conteúdo para a sua organização**.
> 
> 

Terá de ativar permissões adicionais na sua aplicação, além do que foi fornecido na página de registo de aplicações. Pode realizar esta tarefa através do portal do Azure AD ou ao programar.

Precisa de ter sessão iniciada com uma conta *mestre* utilizada para incorporar ou uma conta de Administrador global.

### <a name="using-the-azure-ad-portal"></a>Utilizar o portal do Azure AD
1. Navegue até aos [Registos de aplicação](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) no portal do Azure e selecione a aplicação que estiver a utilizar para incorporar.
   
    ![](media/register-app/powerbi-embedded-azuread-registered-apps.png)
2. Selecione **Permissões precisas** em **Acesso à API**.
   
    ![](media/register-app/powerbi-embedded-azuread-app-required-permissions.png)
3. Selecione **Windows Azure Active Directory** e, em seguida, certifique-se de que seleciona **Aceder ao diretório como o utilizador com sessão iniciada**. Selecione **Guardar**.
   
    ![](media/register-app/powerbi-embedded-azuread-app-permissions01.png)
4. Nas **Permissões precisas**, selecione **Serviço Power BI (Power BI)**.
   
    ![](media/register-app/powerbi-embedded-azuread-app-permissions03.png)
   
   > [!NOTE]
   > Se criou a aplicação diretamente no portal do Azure AD, o **Serviço Power BI (Power BI)** pode não estar presente. Se não estiver, selecione **+ Adicionar** e, em seguida, **1 Selecionar e API**. Selecione **Serviço Power BI** na lista da API e selecione **Selecionar**.  Se o **Serviço Power BI (Power BI)** não estiver disponível em **+ Adicionar**, inscreva-se no Power BI com, pelo menos, um utilizador.
   > 
   > 
5. Selecione todas as permissões em **Permissões Delegadas**. Terá de as selecionar uma a uma para guardar as seleções. Selecione **Guardar** quando terminar.
   
    ![](media/register-app/powerbi-embedded-azuread-app-permissions04.png)
6. Em **Permissões precisas**, selecione **Conceder Permissões**.
   
    A ação **Conceder Permissões** é precisa para a *conta mestra*, para evitar que lhe seja pedido consentimento pelo Azure AD. Se a conta que executa esta ação for de um Administrador Global, este irá conceder permissões a todos os utilizadores na sua organização para esta aplicação. Se a conta que realiza esta ação é a *conta mestra* e não for de um Administrador Global, este irá conceder permissões apenas à *conta mestra* para esta aplicação.
   
    ![Conceder permissões na caixa de diálogo de permissões precisas](media/register-app/powerbi-embedded-azuread-app-grant-permissions.png)

### <a name="applying-permissions-programmatically"></a>Aplicar permissões programaticamente
1. Terá de obter os principais de serviço existentes (utilizadores) no seu inquilino. Para obter informações sobre como fazê-lo, veja [Obter servicePrincipal](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/serviceprincipal_get).
   
    Pode chamar a API *Obter servicePrincipal* sem {id} e irá dar-lhe todos os principais de serviço no inquilino.
2. Verifique a existência de um principal de serviço com o ID de cliente da aplicação como a propriedade **appId**.
3. Crie um novo plano de serviço se estiver em falta na sua aplicação.
   
    ```
    Post https://graph.microsoft.com/beta/servicePrincipals
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```
4. Conceder Permissão de Aplicação à API do PowerBI
   
    ```
    Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
    Authorization: Bearer ey..qw
    Content-Type: application/json
    { 
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"c78b2585-1df6-41de-95f7-dc5aeb7dc98e",
    "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```
5. Conceder Permissão de Aplicação ao AAD
   
    O valor para **consentType** irá depender do utilizador que realiza o pedido. Pode indicar **AllPrincipals** ou **Principal**. **AllPrincipals** pode ser utilizado apenas por um administrador para conceder permissão a todos os utilizadores. **Principal** serve para conceder permissão a um utilizador específico. 
   
    A concessão de permissão é precisa para a *conta mestra*, para evitar que lhe seja pedido consentimento pelo Azure AD. 
   
    Se estiver a utilizar um inquilino existente e não estiver interessado em conceder permissões em nome de todos os utilizadores de inquilino, pode conceder permissões a um utilizador específico, ao substituir o valor de **contentType** para **Principal**.
   
    ```
    Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
    Authorization: Bearer ey..qw
    Content-Type: application/json
    { 
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

## <a name="next-steps"></a>Passos seguintes
Agora que registou a aplicação no Azure AD, terá de autenticar os utilizadores na sua aplicação. Dê uma vista de olhos em [Autenticar utilizadores e obter um token de acesso do Azure AD para a sua aplicação do Power BI](get-azuread-access-token.md) para aprender mais.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

