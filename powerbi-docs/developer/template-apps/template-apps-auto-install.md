---
title: Automatizar a configuração da instalação da aplicação de modelo para os clientes
description: Saiba mais sobre como automatizar a configuração da instalação da aplicação de modelo.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: ca5db6ed7a07d5a6fb10133285378e8318527464
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386098"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Configuração automatizada da instalação de uma aplicação de modelo

As aplicações de modelo são uma forma excelente para os clientes começarem a obter informações sobre os dados. As aplicações de modelo permitem uma rápida colocação em funcionamento, através da ligação aos dados e ao fornecimento de relatórios pré-criados que podem ser personalizados se assim o pretenderem.

Os clientes nem sempre estão familiarizados com os detalhes sobre como ligar os dados e ter de proporcionar estes detalhes ao instalar uma aplicação de modelo pode ser incómodo.

Se for um fornecedor de serviços de dados e tiver criado uma aplicação de modelo para ajudar os clientes a começar a utilizar os dados no serviço, poderá facilitar-lhes a instalação da aplicação de modelo através da automatização da configuração dos parâmetros da aplicação de modelo. Quando o cliente inicia sessão no portal, este clica numa ligação especial que preparou. Esta ligação vai permitir iniciar a automatização e reunir as informações necessárias, pré-configurar os parâmetros da aplicação de modelo e redirecionar o cliente para a conta do Power BI onde pode instalar a aplicação. Em seguida, o cliente terá apenas de clicar em instalar, autenticar-se na origem de dados e poderá começar! 

Esta experiência de cliente é ilustrada abaixo.

![Ilustração da experiência de utilizador com a aplicação de instalação automática.](media/template-apps-auto-install/high-level-flow.png)

Este artigo descreve o fluxo básico, os pré-requisitos, os principais passos e as APIs necessárias para automatizar a configuração de uma instalação de aplicação de modelo. No entanto, se preferir começar imediatamente, poderá passar para o [tutorial](template-apps-auto-install-tutorial.md) onde automatiza a configuração da instalação da aplicação de modelo com uma aplicação de exemplo simples que preparamos, que utiliza uma Função do Azure.

## <a name="basic-flow"></a>Fluxo básico

O fluxo básico da automatização da configuração da instalação de uma aplicação de modelo é o seguinte:

1. O utilizador inicia sessão no portal do ISV e clica na ligação indicada para iniciar o fluxo automatizado. O portal do ISV prepara a configuração específica do utilizador nesta fase.

2. O ISV adquire um token **Apenas de aplicação** com base num [principal de serviço (token apenas de aplicação)](../embedded/embed-service-principal.md), que é registado no inquilino do ISV.

3. Com as [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/), o ISV cria um **Pedido de Instalação** que contém a configuração dos parâmetros específica do utilizador, conforme preparado pelo ISV.

4. O ISV redireciona o utilizador para o Power BI com um método de redirecionamento ```POST```, que contém o pedido de instalação.

5. O utilizador é redirecionado para a conta do Power BI com o pedido de instalação e é pedida a instalação com a aplicação de modelo. Quando o utilizador clicar em instalar, a aplicação de modelo será instalada.

>[!Note]
>Apesar de os valores dos parâmetros serem configurados pelo ISV ao criar o pedido de instalação, as credenciais relacionadas com a origem de dados são disponibilizadas apenas pelo utilizador nas fases finais da instalação, o que impede que sejam expostas a terceiros e garante ma ligação segura entre o utilizador e as origens de dados da aplicação de modelo.

## <a name="prerequisites"></a>Pré-requisitos

Para disponibilizar uma experiência de instalação pré-configurada para a aplicação de modelo, são necessários os seguintes pré-requisitos:

* Uma **licença do Power BI Pro**. Se não estiver inscrito no Power BI Pro, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/pricing/) antes de começar.

* Uma **configuração de inquilino do Azure Active Directory** própria. Veja [Criar um inquilino do Azure Active Directory](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant) para obter instruções sobre como configurar um.

* Um **principal de serviço (token apenas de aplicação)** registado no inquilino acima. Veja [Incorporar conteúdos do Power BI com o principal de serviço e um segredo da aplicação](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal), para obter mais detalhes. Confirme que regista a aplicação como uma **aplicação Web do lado do servidor**. Registe uma aplicação Web do lado do servidor para criar um segredo da aplicação. Neste processo, vai precisar de guardar o *ID da Aplicação* (ID do Cliente) e o *Segredo da Aplicação* (Segredo do Cliente) para os passos posteriores.

* Uma **aplicação de modelo parametrizada** pronta para instalação. A aplicação de modelo deve ser criada no mesmo inquilino no qual registou a aplicação no Azure Active Directory (AAD). Para obter mais informações, veja [sugestões da aplicação modelo](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips.md) ou [Criar uma aplicação de modelo no Power BI](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create). Na aplicação de modelo, deve anotar as seguintes informações para os próximos passos:
     * *ID da Aplicação*, *Chave do Pacote* e *ID do Proprietário* como aparecem no URL de instalação no final do processo de [Definir as propriedades da aplicação de modelo](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) quando a aplicação foi criada. Também pode obter a mesma ligação ao clicar em **Obter ligação** na [Gestão de Versão](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) da aplicação de modelo.

    * *Nomes dos Parâmetros* como definidos no conjunto de dados da aplicação de modelo. Os nomes dos parâmetros são cadeias de carateres sensíveis às maiúsculas e minúsculas e também podem ser obtidos no separador **Definições dos Parâmetros** quando [Definir as propriedades da aplicação de modelo](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) ou nas definições dos conjuntos de dados no Power BI.

    >[!NOTE]
    >Poderá testar a aplicação de instalação pré-configurada na aplicação de modelo se esta estiver pronta para instalação, mesmo que ainda não esteja publicamente disponível no AppSource. No entanto, para que os utilizadores fora do inquilino sejam capazes de utilizar a aplicação de instalação automatizada para instalar a aplicação de modelo, esta deve estar publicamente disponível no [Marketplace de Aplicações do Power BI](https://app.powerbi.com/getdata/services). Portanto, antes de distribuir a aplicação de modelo com a aplicação de instalação automatizada que está a criar, confirme que a publica no [Centro de Parceiros](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Passos principais e APIs

Os passos principais para automatizar a configuração de uma instalação da aplicação de modelo e as APIs necessárias são descritas nas secções a seguir. Embora a maioria dos passos utilize as [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/), os exemplos de código descritos abaixo utilizam o **SDK .NET**.

## <a name="step-1-create-a-power-bi-client-object"></a>Passo 1: Criar um objeto de cliente do Power BI 

A utilização das APIs REST do Power BI exige a obtenção de um **token de acesso** para o [principal de serviço](../embedded/embed-service-principal.md) no **Azure Active Directory**. É necessário obter um [token de acesso do Azure AD](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) para a sua aplicação Power BI antes de fazer chamadas às [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/).
Para criar o Cliente do Power BI com o **token de acesso**, tem de criar o objeto de cliente do Power BI, que lhe permite interagir com as [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/). Cria o objeto de cliente do Power BI ao encapsular num wrapper o **AccessToken** com um objeto **_Microsoft.Rest.TokenCredentials_* _.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Passo 2: Criar um pedido de instalação

Crie um pedido de instalação, que será utilizado para quando redireciona os utilizadores para o Power BI. A API utilizada para esta operação é a API _ *CreateInstallTicket**.
* [Template Apps CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

Está disponível um exemplo da criação de um pedido de instalação para a instalação e configuração da aplicação de modelo no ficheiro [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) na [aplicação de exemplo](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


Veja abaixo um exemplo de código de como utilizar a API REST *CreateInstallTicket* da aplicação de modelo.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Passo 3: Redirecionar os utilizadores para o Power BI com o pedido

Após criar um pedido de instalação, poderá utilizá-lo para redirecionar os utilizadores para o Power BI para continuar com a instalação e configuração da aplicação de modelo. Tal é feito ao utilizar o redirecionamento de um método ```POST``` para o URL de instalação da aplicação de modelo, com o pedido de instalação no corpo do pedido.

Existem vários métodos documentados de como emitir um redirecionamento com pedidos ```POST```. Escolher um ou outro depende do cenário e de como os utilizadores interagem com o portal ou com o serviço.

Um exemplo simples, utilizado principalmente para fins de teste, recorre a um formulário com um campo oculto, que é submetido automaticamente aquando do carregamento.

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

Veja abaixo está um exemplo da resposta da [aplicação de exemplo](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample), que contém o pedido de instalação e redireciona automaticamente os utilizadores para o Power BI. A resposta para esta Função do Azure é, na verdade, o mesmo formulário submetido automaticamente no exemplo de html acima.

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>Embora existam vários métodos de utilizar os redirecionamentos ```POST``` do browser, deve sempre utilizar o método mais seguro, o que depende das necessidades e restrições do serviço. Lembre-se de que alguns formulários de redirecionamento não seguro podem resultar na exposição dos utilizadores ou do serviço a problemas de segurança.

## <a name="step-4-move-your-automation-to-production"></a>Step 4: Mover a automatização para produção

Quando a automatização que criou estiver pronta, confirme que a move para produção.

## <a name="next-steps"></a>Passos seguintes

* Experimente o nosso [tutorial](template-apps-auto-install-tutorial.md) que utiliza uma Função do Azure simples para automatizar a configuração da instalação da aplicação de modelo.

* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
