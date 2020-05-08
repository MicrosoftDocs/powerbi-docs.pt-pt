---
title: Get an authentication access token (Obter um token de acesso de autenticação)
description: Instruções para enviar dados por push – obter um token de acesso de autenticação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 7e74b01a6b12302393a3e4bc40b2e9cccfc13d63
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488275"
---
# <a name="step-2-get-an-authentication-access-token"></a>Passo 2: Obter um token de acesso de autenticação

Este artigo é o segundo passo da série [Enviar dados por push para um conjunto de dados do Power BI](walkthrough-push-data.md).

No passo 1, [registou uma aplicação de cliente no Azure AD](../embedded/register-app.md). Neste passo, obtém um token de acesso de autenticação. As aplicações do Power BI estão integradas no Azure Active Directory para fornecer início de sessão seguro e autorização à sua aplicação. A sua aplicação utiliza um token para autenticar no Azure AD e obter acesso aos recursos do Power BI.

## <a name="get-an-authentication-access-token"></a>Get an authentication access token (Obter um token de acesso de autenticação)

Antes de começar, certifique-se de que concluiu o [passo anterior](../embedded/register-app.md) na série [Enviar dados por push para um conjunto de dados do Power BI](walkthrough-push-data.md). 

Este procedimento exige o Visual Studio 2015 ou uma versão posterior.

1. No Visual Studio, crie um novo projeto de **Console Application** (Aplicação de Consola) em C#.

2. Instale o [pacote de Biblioteca de Autenticação do Azure AD para .NET NuGet](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). A sua aplicação .Net precisa deste pacote para obter um token de segurança de autenticação. 

     a. Selecione **Tools** (Ferramentas)  > **NuGet Package Manager** (Gestor de Pacotes NuGet)  > **Package Manager Console** (Consola do Gestor de Pacotes).

     b. Introduza **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**

     c. Em Program.cs, adicione `using Microsoft.IdentityModel.Clients.ActiveDirectory;`.

3. Adicione a Program.cs o código de exemplo listado a seguir a estes passos.

4. Substitua "{ClientID}" pelo **ID de Cliente** que obteve no [artigo da série anterior](../embedded/register-app.md), quando registou a sua aplicação.

5. Execute a sua aplicação de consola e inicie sessão na sua conta do Power BI. 

   Deve aparecer uma cadeia de token na janela da consola.

**Exemplo de código para obter um token de segurança de autenticação**

Adicione este código a Program {...}.

* Uma variável de token para chamar operações: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* Em static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Adicione um método GetToken():

```csharp
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Depois de obter um token de autenticação, pode chamar qualquer operação do Power BI.

O próximo artigo desta série explica como [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Listagem de código completo

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Próximas etapas

* O próximo artigo desta série é [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)
* [Descrição Geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
* [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)