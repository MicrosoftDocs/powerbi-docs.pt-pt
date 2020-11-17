---
title: Registar uma aplicação para incorporar conteúdo do Power BI
description: Saiba como registar uma aplicação no Azure Active Directory para utilizar ao incorporar conteúdo do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 52e835f4ff0d3dc4cad13c2e3ecc77d254f3be9d
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412262"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>Registar uma aplicação do Azure AD para utilizar com o Power BI

Para utilizar a análise incorporada do Power BI, precisa de registar uma aplicação do Azure Active Directory (Azure AD) no Azure. A aplicação do Azure AD estabelece permissões para os recursos REST do Power BI e permite o acesso às [APIs REST do Power BI](/rest/api/power-bi/).

## <a name="determine-your-embedding-solution"></a>Determinar a sua solução incorporada

Antes de registar a sua aplicação, decida qual das seguintes soluções é a mais adequada para si:

* Incorporar para os seus clientes
* Incorporar para a sua organização

### <a name="embed-for-your-customers"></a>Incorporar para os seus clientes

Utilize a solução [Incorporar para os seus clientes](embed-sample-for-customers.md), também conhecida como *dados que pertencem à aplicação*, se estiver a planear criar uma aplicação concebida para os seus clientes. Os utilizadores não irão precisar de iniciar sessão no Power BI ou de ter uma licença do Power BI para utilizarem a sua aplicação. A sua aplicação irá utilizar um dos seguintes métodos para autenticar face ao Power BI:

* Conta de **utilizador principal** (uma licença do Power BI Pro utilizada para iniciar sessão no Power BI)

*  [Service principal (Principal de serviço)](embed-service-principal.md)

Normalmente, a solução Incorporar para os seus clientes é utilizada por programadores e fornecedores de software independentes (ISVs) que estão a criar uma aplicação para terceiros.

### <a name="embed-for-your-organization"></a>Incorporar para a sua organização

Utilize a solução [Incorporar para a sua organização](embed-sample-for-your-organization.md), também conhecida como *os dados pertencem ao utilizador*, se estiver a planear criar uma aplicação que precise que os utilizadores utilizem as suas credenciais para se autenticarem face ao Power BI.

Normalmente, a solução Incorporar para a sua organização é utilizada por grandes empresas e organizações e é destinada a utilizadores internos.

## <a name="register-an-azure-ad-app"></a>Registar uma aplicação do Azure AD

A forma mais fácil de registar uma aplicação do Azure AD é ao utilizar a [ferramenta de configuração de incorporação do Power BI](https://app.powerbi.com/embedsetup). A ferramenta oferece um processo de registo rápido para ambas as soluções de incorporação, ao utilizar uma interface gráfica simples.

Se estiver a criar uma aplicação com a solução *Incorporar para a sua organização* e quiser obter mais controlo sobre a sua aplicação do Azure AD, pode registá-la manualmente no portal do Azure.

> [!IMPORTANT]
> Antes de registar uma aplicação do Power BI, precisa de um [inquilino do Azure Active Directory e um utilizador organizacional](create-an-azure-active-directory-tenant.md).

# <a name="embed-for-your-customers"></a>[Incorporar para os seus clientes](#tab/customers)

Estes passos descrevem como registar uma aplicação do Azure AD para a solução [Incorporar para os seus clientes](embed-sample-for-customers.md) do Power BI.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Na secção *Selecionar uma solução de incorporação*, selecione **Incorporar para os seus clientes**.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. Em *Passo 2 – Registar a sua aplicação*, preencha os seguintes campos:

    * **Nome da Aplicação**: atribua um nome à sua aplicação.

    * **Acesso à API**: selecione as APIs do Power BI (também conhecidas como âmbitos) de que a sua aplicação precisa. Pode utilizar a opção *Selecionar tudo* para selecionar todas as APIs. Para obter mais informações sobre as permissões de acesso do Power BI, consulte [Permissões e consentimento no ponto final da plataforma de identidades da Microsoft](/azure/active-directory/develop/v2-permissions-and-consent).

5. Selecione **Registar**.

    O **ID da Aplicação** da sua aplicação do Azure AD é apresentado na caixa *Resumo*. Copie este valor para utilizar mais tarde.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. Em *Passo 5 – Conceder permissão*, selecione **Conceder permissões** e, na janela de pop-up, selecione **Aceitar**. Isto permite à sua aplicação do Azure AD aceder às API's que selecionou (também conhecidas como âmbitos) com o seu utilizador com sessão iniciada. Este utilizador também é conhecido como **utilizador principal**.

9. (Opcional) Se criou uma área de trabalho do Power BI e carregou conteúdos para a mesma com a ferramenta, pode selecionar **Transferir aplicação de exemplo**. Certifique-se de que copia todas as informações na caixa *Resumo*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[Incorporar para a sua organização](#tab/organization)

Estes passos descrevem como registar uma aplicação do Azure AD para a solução [Incorporar para a sua organização](embed-sample-for-your-organization.md) do Power BI.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Na secção *Selecionar uma solução de incorporação*, selecione **Incorporar para a sua organização**.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. Em *Passo 2 – Registar a sua aplicação*, preencha os seguintes campos:

    * **Nome da Aplicação**: atribua um nome à sua aplicação.

    * **URL da Home Page**: introduza um URL para a sua home page.

    * **URL de redirecionamento**: após iniciarem sessão, os utilizadores da sua aplicação serão redirecionados para este endereço enquanto a sua aplicação recebe um código de autenticação do Azure. Selecione uma das seguintes opções:

        * **Utilizar um URL predefinido**: esta opção irá criar e transferir automaticamente uma aplicação de análise incorporada de exemplo. O URL predefinido é http://localhost:13526/.

        * **Utilizar um URL personalizado**: selecione esta opção se já tiver uma aplicação de análise incorporada e sabe o que pretende utilizar como URL de redirecionamento.

    * **Acesso à API**: selecione as APIs do Power BI (também conhecidas como âmbitos) de que a sua aplicação precisa. Pode utilizar a opção *Selecionar tudo* para selecionar todas as APIs. Para obter mais informações sobre as permissões de acesso do Power BI, consulte [Permissões e consentimento no ponto final da plataforma de identidades da Microsoft](/azure/active-directory/develop/v2-permissions-and-consent).

5. Selecione **Registar**.

    Os valores **ID da Aplicação** e **Segredo da aplicação** da sua aplicação do Azure AD são apresentados na caixa *Resumo*. Copie estes valores para utilizar mais tarde.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (Opcional) Se criou uma área de trabalho do Power BI e carregou conteúdos para a mesma com a ferramenta, pode selecionar **Transferir aplicação de exemplo**. Certifique-se de que copia todas as informações na caixa *Resumo*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[Registo manual](#tab/manual)

Utilize o registo de aplicações manual do Azure AD apenas se for criar uma solução *Incorporar para a sua organização*. Para obter mais informações sobre como registar aplicações no Azure Active Directory, veja [Registar aplicações com o Azure Active Directory](/azure/active-directory/develop/quickstart-v2-register-an-app).

1. Inicie sessão no [portal do Azure](https://portal.azure.com).

2. Selecione o seu inquilino do Azure AD ao selecionar a sua conta no canto superior direito da página.

3. Selecione **Registos de aplicações**. Se não conseguir ver esta opção, procure-a.
 
4. Em *Registos de aplicações*, selecione **Novo registo**.

5. Preencha os seguintes campos:

    * **Nome**: atribua um nome à sua aplicação.

    * **Tipo de conta suportada**: selecione quem pode utilizar a aplicação.

6. (Opcional) No campo **URI de redirecionamento**, adicione um URL de redirecionamento.

7. Selecione **Registar**. Após a sua aplicação estar registada, será direcionado para a página Descrição Geral da sua aplicação, onde poderá obter o *ID da Aplicação*.

---

## <a name="change-your-azure-ad-apps-permissions"></a>Alterar as permissões da sua aplicação do Azure AD

Após registar a sua aplicação, pode fazer alterações às respetivas permissões. As alterações às permissões podem ser efetuadas através de programação ou no portal do Azure.

# <a name="azure"></a>[Azure](#tab/Azure)

No portal do Azure, pode ver a sua aplicação e fazer alterações às respetivas permissões.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).

2. Selecione o seu inquilino do Azure AD ao selecionar a sua conta no canto superior direito da página.

3. Selecione **Registos de aplicações**. Se não conseguir ver esta opção, procure-a.

4. No separador **Aplicações Próprias**, selecione a sua aplicação. A aplicação abre no separador *Descrição Geral*, onde pode rever o *ID da Aplicação*.

5. Selecione o separador **Permissões da API**.

6. Para adicionar permissões, siga estes passos:

    1. Selecione **Adicionar uma permissão** e, em seguida, selecione **Serviço Power BI**.

    2. Selecione **Permissões Delegadas** e adicione ou remova as permissões específicas que precisar.

    3. Quando terminar, selecione **Adicionar permissões** para guardar as alterações.

7. Para remover uma permissão, siga estes passos:

    1. Selecione as reticências (...) à direta da permissão.
    
    2. Selecione **Remover permissão**.
    
    3. Na janela de pop-up *Remover permissão*, selecione **Sim, remover**.

# <a name="http"></a>[HTTP](#tab/HTTP)

Para alterar as permissões da sua aplicação do Azure AD através de programação, irá precisar de obter os principais (utilizadores) de serviço existentes no seu inquilino. Para obter informações sobre como fazê-lo, veja [servicePrincipal](/graph/api/resources/serviceprincipal).

1. Para obter todos os principais de serviço no seu inquilino, chame a API `Get servicePrincipal` sem `{ID}`.

2. Verifique a existência de um principal de serviço com o *ID de aplicação* da aplicação como a propriedade `appId`.

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` é opcional.

3. Conceda permissões ao Power BI para a sua aplicação, ao atribuir um destes valores a `consentType`:

    * `AllPrincipals`: só pode ser utilizado por um administrador do Power BI para conceder permissões em nome de todos os utilizadores no inquilino.

    * `Principal`: utilize para conceder permissões em nome de um utilizador específico. Se estiver a utilizar esta opção, adicione a propriedade `principalId={User_ObjectId}` ao corpo do pedido.

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* Se estiver a utilizar um **utilizador principal**, para evitar que lhe seja pedido consentimento pelo Azure AD, precisa de conceder permissões à conta principal.
    >* O `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* é dependente de inquilino e não universal. Este valor é o *objectId* da aplicação *Serviço Power BI* no Azure AD. Para obter este valor no portal do Azure, navegue para [Aplicações empresariais > Todas as aplicações](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps) e procure *Serviço Power BI*.

4. Conceda permissões da aplicação ao Azure AD, ao atribuir um valor a `consentType`.

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
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

# <a name="c"></a>[C#](#tab/CSharp)

Também pode alterar as permissões da sua aplicação do Azure AD com o C#. Este método pode ser útil se estiver a considerar automatizar alguns dos seus processos.

Para obter mais informações relativamente aos pedidos HTTP, consulte o [separador HTTP](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions).

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

```

---

## <a name="next-steps"></a>Passos seguintes

>[!div class="nextstepaction"]
>[Obter um token de acesso do Azure AD para a sua aplicação do Power BI](get-azuread-access-token.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)