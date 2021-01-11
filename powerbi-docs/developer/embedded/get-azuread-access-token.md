---
title: Autenticar utilizadores e obter o token de acesso do Azure AD para a sua aplicação de análise incorporada do Power BI para melhorar a experiência de BI incorporada dos clientes
description: Saiba como registar uma aplicação no Azure Active Directory para utilizar ao incorporar conteúdos do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/04/2019
ms.openlocfilehash: 8001dd0e15ef713fa67256a45f645b0d7a0890c0
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888449"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Obter um token de acesso do Azure AD para a sua aplicação do Power BI

Este artigo mostra como pode autenticar utilizadores na sua aplicação Power BI e obter um token de acesso para utilizar com a [API REST do Power BI](/rest/api/power-bi/).

Antes de a sua aplicação chamar a API REST, terá de obter um **token de acesso de autenticação** do Azure Active Directory (Azure AD). A sua aplicação utiliza um token para obter acesso a dashboards, mosaicos e relatórios do Power BI. Para saber mais, veja [Autorizar o acesso a aplicações Web do Azure Active Directory através do fluxo de concessão de código do OAuth 2.0](/azure/active-directory/develop/v1-protocols-oauth-code).

Consoante a forma como está a incorporar conteúdos, o token de acesso é obtido de forma diferente. Este artigo apresenta duas abordagens diferentes.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Token de acesso para utilizadores do Power BI (os dados pertencem ao utilizador)

Este exemplo destina-se a utilizadores que iniciam sessão manualmente no Azure AD com as credenciais de início de sessão da organização. Esta tarefa é utilizada ao incorporar conteúdos para utilizadores que tenham acesso ao serviço Power BI.

### <a name="get-an-azure-ad-authorization-code"></a>Obter um código de autorização do Azure AD

O primeiro passo para obter um **token de acesso** é obter um código de autorização do **Azure AD**. Deve construir uma cadeia de consulta com as seguintes propriedades e redirecionar para o **Azure AD**.

#### <a name="authorization-code-query-string"></a>Cadeia de consulta de código de autorização

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

Após construir uma cadeia de consulta, redirecione para o **Azure AD** para obter um **código de autorização**.  Segue-se um método C# completo para construir uma cadeia de consulta de **código de autorização** e redirecionar para o **Azure AD**. Em seguida, vai utilizar o **código de autorização** para obter um **token de acesso**.

Em redirect.aspx.cs, [AuthenticationContext.AcquireTokenByAuthorizationCode](/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) é chamado para gerar o token.

#### <a name="get-authorization-code"></a>Obter código de autorização

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Obter um token de acesso do código de autorização

Quando o **Azure AD** o redirecionar para a sua aplicação Web com um **código de autorização**, pode utilizá-lo para obter um token de acesso. Abaixo encontra-se um exemplo em C# que pode utilizar na sua página de redirecionamento, bem como o evento `Page_Load` do default.aspx.

Pode obter o espaço de nomes **Microsoft.IdentityModel.Clients.ActiveDirectory** a partir do pacote NuGet [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Token de acesso para utilizadores não pertencentes ao Power BI (os dados pertencem à aplicação)

Esta abordagem é geralmente utilizada para aplicações de fabricantes independentes de software (ISV) em que a aplicação detém o acesso aos dados. Os utilizadores não são necessariamente utilizadores do Power BI e a aplicação controla a autenticação e o acesso dos utilizadores.

### <a name="access-token-with-a-master-account"></a>Token de acesso com uma conta principal

Nesta abordagem, deve utilizar uma única conta *principal* que corresponde a um utilizador do Power BI Pro. As credenciais de conta são armazenadas na aplicação. A aplicação é autenticada no Azure AD com essas credenciais armazenadas. O código de exemplo mostrado abaixo provém do [exemplo App Owns Data](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Token de acesso com o principal de serviço

Nesta abordagem, deve utilizar um [principal de serviço](embed-service-principal.md), que seja um token **só para aplicações**. A aplicação é autenticada no Azure AD com o principal de serviço. O código de exemplo mostrado abaixo provém do [exemplo App Owns Data](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var AuthorityURL  = "https://login.microsoftonline.com/<TenantId>/"
var ResourceURL  = "https://analysis.windows.net/powerbi/api"
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Resolução de problemas

Mensagem de erro: "'AuthenticationContext' não contém uma definição para 'AcquireToken' e não foi possível localizar nenhum método de extensão 'AcquireToken' que aceitasse um primeiro argumento do tipo 'AuthenticationContext' (falta-lhe uma directiva de utilização ou uma referência de assemblagem?)".

   Se lhe for apresentado este erro, experimente transferir o pacote [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727).

## <a name="next-steps"></a>Passos seguintes

Agora que tem o token de acesso, pode chamar a API REST do Power BI para incorporar conteúdos.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)