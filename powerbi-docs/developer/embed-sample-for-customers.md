---
title: "Incorporar conteúdo do Power BI numa aplicação para os seus clientes"
description: "Saiba como integrar ou incorporar um dashboard, mosaico ou relatório numa aplicação Web com as APIs do Power BI para os seus clientes."
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: 8c703b93e87ad32ab3f730979292b85a86fd53c0
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="embed-a-power-bi-dashboard-tile-or-report-into-your-application"></a>Incorporar um dashboard, mosaico ou relatório do Power BI na sua aplicação
Saiba como integrar ou incorporar um dashboard, mosaico ou relatório numa aplicação Web com o SDK .NET do Power BI, juntamente com a API JavaScript do Power BI ao incorporar para os seus clientes. Normalmente, este é o cenário de ISV.

![Dashboard incorporado](media/embed-sample-for-customers/powerbi-embed-dashboard.png)

Para começar estas instruções, é preciso uma conta do **Power BI Pro**. Se não tiver uma conta, pode [inscrever-se numa conta gratuita do Power BI](../service-self-service-signup-for-power-bi.md) e, em seguida, inscrever-se numa [versão de avaliação do Power BI Pro](../service-self-service-signup-for-power-bi.md#in-service-power-bi-pro-60-day-trial) ou pode criar o seu próprio [inquilino do Azure Active Directory ](create-an-azure-active-directory-tenant.md) para fins de teste.

> [!NOTE]
> Pretende incorporar um dashboard para a sua organização em alternativa? Veja [Integrar um dashboard numa aplicação para a sua organização](integrate-dashboard.md).
> 
> 

Para integrar um dashboard numa aplicação Web, utilize a API do **Power BI** e um **token de acesso** de autorização do Azure Active Directory (AD) para obter um dashboard. Em seguida, carregue o dashboard com um token de incorporação. A API do **Power BI** fornece acesso programático a determinados recursos do **Power BI**. Para obter mais informações, veja [Descrição geral da API REST do Power BI](https://msdn.microsoft.com/library/dn877544.aspx), [SDK .NET do Power BI](https://github.com/Microsoft/PowerBI-CSharp) e [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Transferir o exemplo
Este artigo mostra o código utilizado no [Exemplo de incorporação para a sua organização](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data) no GitHub. Para acompanhar estas instruções, pode transferir o exemplo.

## <a name="step-1---register-an-app-in-azure-ad"></a>Passo 1 - registar uma aplicação no Azure AD
Terá de registar a sua aplicação no Azure AD para fazer chamadas à API REST. Para obter mais informações, veja [Register an Azure AD app to embed Power BI content (Registar uma aplicação do Azure AD para incorporar conteúdo do Power BI)](register-app.md).

Se transferiu o [Exemplo de incorporação para a sua organização](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data), utilize o **ID de Cliente** que recebe após o registo para que o exemplo possa ser autenticado no Azure AD. Para configurar o exemplo, altere o **clientId** no ficheiro *web.config*.

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Passo 2 - obter um token de acesso do Azure AD
Na sua aplicação, primeiro terá de obter um **token de acesso** do Azure AD antes de poder fazer chamadas à API REST do Power BI. Para obter mais informações, veja [Authenticate users and get an Azure AD access token for your Power BI app (Autenticar utilizadores e obter um token de acesso do Azure AD para a sua aplicação do Power BI)](get-azuread-access-token.md).

Pode ver exemplos dentro de cada tarefa de item de conteúdo em **Controllers\HomeController.cs**.

## <a name="step-3---get-a-content-item"></a>Passo 3 - obter um item de conteúdo
Para incorporar o conteúdo do Power BI, terá de executar algumas ações para se certificar de que é incorporado corretamente. Embora todos estes passos possam ser executados diretamente com a API REST, o exemplo de aplicação e os exemplos aqui apresentados são executados com o SDK .NET.

### <a name="create-the-power-bi-client-with-your-access-token"></a>Criar o Cliente do Power BI com o seu token de acesso
Com o seu token de acesso, irá querer criar o objeto de cliente do Power BI que lhe permitirá interagir com as APIs do Power BI. Isto é feito ao encapsular num wrapper o AccessToken com um objeto *Microsoft.Rest.TokenCredentials*.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Obter o item de conteúdo que pretende incorporar
Utilize o objeto de cliente do Power BI para obter uma referência para o item que pretende incorporar. Pode incorporar dashboards, mosaicos ou relatórios. Eis um exemplo de como obter o primeiro dashboard, mosaico ou relatório a partir de uma determinada área de trabalho.

Um exemplo está disponível em **Controllers\HomeController.cs** do [exemplo de App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data).

**Dashboards**

```
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You will need to provide the GroupID where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(GroupId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();
```

**Mosaico**

```
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// To retrieve the tile, you first need to retrieve the dashboard.

// You will need to provide the GroupID where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(GroupId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();

// Get a list of tiles from a specific dashboard
ODataResponseListTile tiles = client.Dashboards.GetTilesInGroup(GroupId, dashboard.Id);

// Get the first tile in the group.
Tile tile = tiles.Value.FirstOrDefault();
```

**Relatório**

```
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You will need to provide the GroupID where the dashboard resides.
ODataResponseListReport reports = client.Reports.GetReportsInGroupAsync(GroupId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Criar o token de incorporação
É preciso gerar um token de incorporação que pode ser utilizado a partir da API JavaScript. O token de incorporação será específico do item que está a incorporar. Isto significa que sempre que incorporar um fragmento de conteúdo do Power BI, tem de criar um novo token de incorporação para o mesmo. Para obter mais informações, incluindo que **accessLevel** utilizar, veja [API GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx).

Um exemplo está disponível em **Controllers\HomeController.cs** do [Exemplo de incorporação para a sua organização](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data).

Este exemplo parte do princípio de que uma classe é criada para **EmbedConfig** e **TileEmbedConfig**. Um exemplo destes estão disponíveis em **Models\EmbedConfig.cs** e **Models\TileEmbedConfig.cs**.

**Dashboard**

```
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Dashboards.GenerateTokenInGroup(GroupId, dashboard.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = dashboard.EmbedUrl,
    Id = dashboard.Id
};
```

**Mosaico**

```
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token for a tile.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Tiles.GenerateTokenInGroup(GroupId, dashboard.Id, tile.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new TileEmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = tile.EmbedUrl,
    Id = tile.Id,
    dashboardId = dashboard.Id
};
```

**Relatório**

```
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(GroupId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

## <a name="step-4---load-an-item-using-javascript"></a>Passo 4 - carregar um item com JavaScript
Pode utilizar JavaScript para carregar um dashboard para um elemento div na sua página Web. Este exemplo utiliza um modelo de EmbedConfig/TileEmbedConfig juntamente com vistas para um dashboard, mosaico ou relatório. Para obter um exemplo completo de utilização da API JavaScript, pode utilizar o [Exemplo do Microsoft Power BI Embedded](https://microsoft.github.io/PowerBI-JavaScript/demo).

Um exemplo de aplicação está disponível em [Exemplo de incorporação para a sua organização](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data).

**Views\Home\EmbedDashboard.cshtml**

```
<script src="~/scripts/powerbi.js"></script>
<div id="dashboardContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'dashboard',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedDashboardId
    };

    // Get a reference to the embedded dashboard HTML element
    var dashboardContainer = $('#dashboardContainer')[0];

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);
</script>
```

**Views\Home\EmbedTile.cshtml**

```
<script src="~/scripts/powerbi.js"></script>
<div id="tileContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read tile Id from Model
    var embedTileId = "@Model.Id";

    // Read dashboard Id from Model
    var embedDashboardeId = "@Model.dashboardId";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedTileId,
        dashboardId: embedDashboardeId
    };

    // Get a reference to the embedded tile HTML element
    var tileContainer = $('#tileContainer')[0];

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);
</script>
```

**Views\Home\EmbedReport.cshtml**

```
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="next-steps"></a>Passos seguintes
Um exemplo de aplicação está disponível no GitHub para rever. Os exemplos acima baseiam-se nesse exemplo. Para obter mais informações, veja [Exemplo de incorporação para a sua organização](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data).

Estão disponíveis mais informações para a API JavaScript. Veja [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

