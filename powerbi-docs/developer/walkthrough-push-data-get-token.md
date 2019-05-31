---
title: Obter um token de acesso de autenticação
description: Passo a passo para enviar dados por push - Obter um token de acesso de autenticação
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 4a0b0f5e7d697c137da343576d05fbcc91b4a4f7
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710363"
---
# <a name="step-2-get-an-authentication-access-token"></a>Passo 2: Obter um token de acesso de autenticação

Este artigo faz parte das instruções passo-a-passo para [Enviar dados por push para um conjunto de dados](walkthrough-push-data.md).

No **passo 1** de Enviar dados por push a um conjunto de dados, [Registar a aplicação no Azure AD](walkthrough-push-data-register-app-with-azure-ad.md), registou uma aplicação cliente no Azure AD. Neste passo, obtém um token de acesso de autenticação. As aplicações do Power BI são integradas no **Azure AD** para fornecer autorização e início de sessão seguros para a sua aplicação. Pode utilizar um token para autenticar para o **Azure AD** e obter acesso aos recursos do Power BI.

Veja como obter um token de acesso de autenticação.

## <a name="get-an-authentication-access-token"></a>Obter um token de acesso de autenticação

> **NOTA**: Antes de começar, certifique-se de que seguiu os passos anteriores nas instruções para [enviar dados para um conjunto de dados](walkthrough-push-data.md).

1. No Visual Studio (versão 2015 ou posterior), crie uma **aplicação de consola** projeto.
2. Instale o [pacote de Biblioteca de Autenticação do Azure AD para .NET NuGet](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). Para obter um token de segurança de autenticação numa aplicação .NET, utilize este pacote. Veja como instalar o pacote:

     a. No Visual Studio (versão 2015 ou posterior), escolha **ferramentas** > **Gestor de pacotes NuGet** > **Package Manager Console**.

     b. Na **Consola do Gestor de Pacotes**, introduza Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612.
3. Adicione o código a seguir à classe Program {…}.
4. Substitua "{ClientID}" pelo **ID de Cliente** que obteve quando registou a aplicação. Consulte [Registar a aplicação no Azure AD](walkthrough-push-data-register-app-with-azure-ad.md).
5. Depois de instalar o pacote Microsoft.IdentityModel.Clients.ActiveDirectory, adicione **using Microsoft.IdentityModel.Clients.ActiveDirectory;** a Program.cs.
6. Execute a Aplicação de Consola e inicie sessão na sua conta do Power BI. Deve ver uma cadeia de token na Janela da Consola.

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

Depois de obter um token de autenticação, pode chamar qualquer operação do Power BI. O próximo passo mostra como chamar a operação [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) para criar um conjunto de dados para enviar dados por push para um dashboard.

O próximo passo mostra-lhe como [criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md).

Segue-se a [listagem de código completo](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Lista completa de códigos

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

[Próximo Passo >](walkthrough-push-data-create-dataset.md)

## <a name="next-steps"></a>Passos seguintes

[Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)  
[Registar uma aplicação no Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)  
[Biblioteca de Autenticação do Azure AD para o pacote NuGet .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)  
[Enviar dados por push para um conjunto de dados do Power BI](walkthrough-push-data.md)  
[Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
[Referência da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)