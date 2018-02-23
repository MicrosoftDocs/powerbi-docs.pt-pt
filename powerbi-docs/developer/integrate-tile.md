---
title: "Integrar um mosaico do Power BI numa aplicação para a sua organização"
description: "Instruções para integrar um mosaico numa aplicação, código de exemplo"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 02/13/2018
ms.author: maghan
ms.openlocfilehash: c4c1b9223554491968a541c9d6b698a9655eded5
ms.sourcegitcommit: 2ceea44d3606c15b57142c37649c9d481ec4becc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/15/2018
---
# <a name="integrate-a-tile-into-an-app-user-owns-data"></a>Integrar um mosaico numa aplicação (os dados são do utilizador)
Saiba como integrar ou incorporar um mosaico numa aplicação Web através de chamadas à API REST, juntamente com a API JavaScript do Power BI ao incorporar para a sua organização.

![Mosaico incorporado na aplicação Web](media/integrate-tile/powerbi-embedded-tile.png)

Para começar estas instruções, é preciso uma conta do **Power BI**. Se não tiver uma conta, pode [inscrever-se numa conta gratuita do Power BI](../service-self-service-signup-for-power-bi.md) ou pode criar o seu próprio [inquilino do Azure Active Directory](create-an-azure-active-directory-tenant.md) para fins de teste.

> [!NOTE]
> Quer incorporar um mosaico para os seus clientes através de um embedtoken? Veja [Integrar um dashboard, mosaico ou relatório na sua aplicação para os seus clientes](embed-sample-for-customers.md).
> 
> 

Para integrar um mosaico numa aplicação Web, utilize a API REST do **Power BI** ou o SDK C# do Power BI e um **token de acesso** de autorização do Azure Active Directory (AD) para obter um mosaico. Em seguida, carregue o mosaico com o mesmo token de acesso. A API do **Power BI** fornece acesso programático a determinados recursos do **Power BI**. Para obter mais informações, consulte [Descrição geral da API REST do Power BI](https://msdn.microsoft.com/library/dn877544.aspx) e [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Transferir o exemplo
Este artigo mostra o código utilizado em [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) no GitHub. Para acompanhar estas instruções, pode transferir o exemplo.

## <a name="step-1---register-an-app-in-azure-ad"></a>Passo 1 – registar uma aplicação no Azure AD
Terá de registar a sua aplicação no Azure AD para fazer chamadas à API REST. Para obter mais informações, veja [Registar uma aplicação do Azure AD para incorporar conteúdo do Power BI](register-app.md).

Se transferiu [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app), utilize o **ID de Cliente** e o **Segredo do cliente** que recebe após o registo para que o exemplo possa ser autenticado no Azure AD. Para configurar o exemplo, altere o **ID de Cliente** e o **Segredo do Cliente** no ficheiro *cloud.config*.

![](media/integrate-tile/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Passo 2 – obter um token de acesso do Azure AD
Na sua aplicação, primeiro terá de obter um **token de acesso** do Azure AD antes de poder fazer chamadas à API REST do Power BI. Para obter mais informações, veja [Autenticar utilizadores e obter um token de acesso do Azure AD para a sua aplicação do Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-tile"></a>Passo 3 – obter um mosaico
Para obter um mosaico do **Power BI**, utilize a operação [Obter Mosaicos](https://msdn.microsoft.com/library/mt465741.aspx) que obtém uma lista dos mosaicos do **Power BI** a partir de um determinado dashboard. Na lista de mosaicos, pode obter um ID de mosaico e o URL de incorporação.

É necessário obter primeiro um ID de dashboard antes de poder obter o mosaico. Para obter informações sobre como obter um dashboard, veja [Integrar um dashboard numa aplicação (os dados são do utilizador)](integrate-dashboard.md).

### <a name="get-tiles-using-an-access-token"></a>Obter mosaicos com um token de acesso
Com o **token de acesso** que obteve no [passo 2](#step-2-get-an-access-token-from-azure-ad), pode chamar a operação [Obter Mosaicos](https://msdn.microsoft.com/library/mt465741.aspx). A operação [Obter Mosaicos](https://msdn.microsoft.com/library/mt465741.aspx) devolve uma lista de mosaicos. Pode obter um único mosaico a partir da lista de mosaicos. Segue-se um método C# completo para obter um mosaico. 

Para efetuar a chamada à API REST, tem de incluir um cabeçalho de *Autorização* no formato de *Portador {token de acesso}*.

#### <a name="get-tiles-with-the-rest-api"></a>Obter mosaicos com a API REST
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a tile from a dashboard. In this sample, you get the first tile.
protected void GetTile(string dashboardId, int index)
{
    //Configure tiles request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}Dashboards/{1}/Tiles",
        baseUri,
        dashboardId)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get tiles response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBITiles tiles = JsonConvert.DeserializeObject<PBITiles>(reader.ReadToEnd());

            //Sample assumes at least one Dashboard with one Tile.
            //You could write an app that lists all tiles in a dashboard
            if (tiles.value.Length > 0)
                tileEmbedUrl.Text = tiles.value[index].embedUrl;
        }
    }
}

//Power BI Tiles used to deserialize the Get Tiles response.
public class PBITiles
{
    public PBITile[] value { get; set; }
}
public class PBITile
{
    public string id { get; set; }
    public string title { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-tiles-using-the-net-sdk"></a>Obter mosaicos com o SDK .NET
Pode utilizar o SDK .NET para obter uma lista de dashboards em vez de chamar a API REST diretamente.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get a list of dashboards your "My Workspace"
    ODataResponseListDashboard tiles = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    // Get the first tile from the above dashbaord
    ODataResponseListTile tiles = client.Dashboards.GetTiles(dashboard.Id);

    Tile tile = tiles.Value.FirstOrDefault();
}
```

## <a name="step-4---load-a-tile-using-javascript"></a>Passo 4 – carregar um item com JavaScript
Pode utilizar JavaScript para carregar um mosaico para um elemento div na sua página Web.

**Default.aspx**

```
<!-- Embed Tile-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a tile</div>

            <div>Enter an embed url for a tile from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedTileAction" value="Embed Tile" />
        </div>

        <div id="tileContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected tile.
    var el = document.getElementById("bEmbedTileAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedTile, false);
    } else {
        el.attachEvent('onclick', updateEmbedTile);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded tile if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedTile();
    }
};

// update embed tile
function updateEmbedTile() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the tile.
    var tileContainer = document.getElementById('tileContainer');

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);

    // tile.on will add an event handler which prints to Log window.
    tile.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Se transferiu e executou [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app), o exemplo será semelhante ao que se segue.

![Mosaico incorporado na aplicação Web](media/integrate-tile/powerbi-embedded-tile.png)

## <a name="working-with-groups-app-workspaces"></a>Utilizar grupos (áreas de trabalho de aplicações)
Para incorporar um mosaico a partir de um grupo (área de trabalho de aplicações), irá querer obter a lista de todos os mosaicos disponíveis no dashboard de um grupo através da seguinte chamada à API REST. Para obter mais informações sobre esta chamada à API REST, veja [Obter Mosaicos](https://msdn.microsoft.com/library/mt465741.aspx). Terá de ter permissão no grupo para o pedido para devolver resultados.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards/{dashboard_id}/tiles
```

A API acima devolve a lista dos mosaicos disponíveis. Cada mosaico tem uma propriedade EmbedUrl já criada para suportar a incorporação de grupos.

```
https://app.powerbi.com/embed?dashboardId={dashboard_id}&tileId={tile_id}&groupId={group_id}
```

## <a name="next-steps"></a>Próximos passos
[Incorporar Mosaico](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Tile-Embed) no Wiki do PowerBI-JavaScript

[API de JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Exemplo [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) no GitHub.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

