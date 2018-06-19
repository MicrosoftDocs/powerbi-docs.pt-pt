---
title: Integrar um dashboard numa aplicação para a sua organização
description: Saiba como integrar ou incorporar um dashboard numa aplicação Web com as APIs do Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 02/13/2018
ms.author: maghan
ms.openlocfilehash: dd7276eb436dfd9d842930f6a2c550a2a6b521f3
ms.sourcegitcommit: 8ee0ebd4d47a41108387d13a3bc3e7e2770cbeb8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34812957"
---
# <a name="integrate-a-dashboard-into-an-app-for-your-organization"></a>Integrar um dashboard numa aplicação para a sua organização
Saiba como integrar ou incorporar um dashboard numa aplicação Web através de chamadas à API REST, juntamente com a API JavaScript do Power BI ao incorporar para a sua organização.

![Dashboard incorporado](media/integrate-dashboard/powerbi-embed-dashboard.png)

Para começar a utilizar estas instruções, precisa de uma conta do **Power BI**. Se não tiver uma conta, pode [inscrever-se numa conta gratuita do Power BI](../service-self-service-signup-for-power-bi.md) ou pode criar o seu próprio [inquilino do Azure Active Directory](create-an-azure-active-directory-tenant.md) para fins de teste.

> [!NOTE]
> Quer incorporar um dashboard para os seus clientes através de um embedtoken? Veja [Integrar um dashboard, mosaico ou relatório na sua aplicação para os seus clientes](embed-sample-for-customers.md).
> 
> 

Para integrar um dashboard numa aplicação Web, utilize a API REST do **Power BI** ou o SDK C# do Power BI e um **token de acesso** de autorização do Azure Active Directory (AD) para obter um dashboard. Em seguida, carregue o dashboard com o mesmo token de acesso. A API do **Power BI** fornece acesso programático a determinados recursos do **Power BI**. Para obter mais informações, veja [API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) e [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Transferir o exemplo
Este artigo mostra o código utilizado em [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) no GitHub. Para acompanhar estas instruções, pode transferir o exemplo.

## <a name="step-1---register-an-app-in-azure-ad"></a>Passo 1 – registar uma aplicação no Azure AD
Terá de registar a sua aplicação no Azure AD para fazer chamadas à API REST. Para obter mais informações, veja [Registar uma aplicação do Azure AD para incorporar conteúdo do Power BI](register-app.md).

Se transferiu o [exemplo Integrar um dashboard](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app), utilize o **ID de Cliente** e o **Segredo do Cliente** que recebe após o registo, para que o exemplo possa ser autenticado no Azure AD. Para configurar o exemplo, altere o **ID de Cliente** e o **Segredo do Cliente** no ficheiro *cloud.config*.

![](media/integrate-dashboard/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Passo 2 – obter um token de acesso do Azure AD
Na sua aplicação, primeiro terá de obter um **token de acesso** do Azure AD antes de poder fazer chamadas à API REST do Power BI. Para obter mais informações, veja [Autenticar utilizadores e obter um token de acesso do Azure AD para a sua aplicação do Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-dashboard"></a>Passo 3 – obter um dashboard
Para obter um dashboard do **Power BI**, utilize a operação [Obter Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards) que obtém uma lista dos dashboards do **Power BI**. A partir da lista de dashboards, pode obter um ID de dashboard.

![](media/integrate-dashboard/powerbi-embed-dashboard-get-dashboards.png)

### <a name="get-dashboards-using-an-access-token"></a>Obter dashboards com um token de acesso
Com o **token de acesso** que obteve no [passo 2](#step-2-get-an-access-token-from-azure-ad), pode chamar a operação [Obter Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). A operação [Obter Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards) devolve uma lista de dashboards. Pode obter um único dashboard da lista de dashboards. Segue-se um método C# completo para obter um dashboard. 

Para efetuar a chamada à API REST, tem de incluir um cabeçalho de *Autorização* no formato de *Portador {token de acesso}*.

#### <a name="get-dashboards-with-the-rest-api"></a>Obter dashboards com a API REST
**Default.aspx.cs**

```
protected void getDashboardsButton_Click(object sender, EventArgs e)
{
    string responseContent = string.Empty;

    //Configure dashboards request
    System.Net.WebRequest request = System.Net.WebRequest.Create(String.Format("{0}dashboards", baseUri)) as System.Net.HttpWebRequest;
    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", authResult.AccessToken));

    //Get dashboards response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            responseContent = reader.ReadToEnd();

            //Deserialize JSON string
            PBIDashboards PBIDashboards = JsonConvert.DeserializeObject<PBIDashboards>(responseContent);

            if (PBIDashboards != null)
            {
                var gridViewDashboards = PBIDashboards.value.Select(dashboard => new {
                    Id = dashboard.id,
                    DisplayName = dashboard.displayName,
                    EmbedUrl = dashboard.embedUrl
                });

                this.GridView1.DataSource = gridViewDashboards;
                this.GridView1.DataBind();
            }
        }
    }
}

//Power BI Dashboards used to deserialize the Get Dashboards response.
public class PBIDashboards
{
    public PBIDashboard[] value { get; set; }
}
public class PBIDashboard
{
    public string id { get; set; }
    public string displayName { get; set; }
    public string embedUrl { get; set; }
    public bool isReadOnly { get; set; }
}
```

#### <a name="get-dashboards-using-the-net-sdk"></a>Obter dashboards através do SDK .NET
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
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    var embedUrl = dashboard.EmbedUrl
}
```

## <a name="step-4---load-a-dashboard-using-javascript"></a>Passo 4 – carregar um dashboard com JavaScript
Pode utilizar JavaScript para carregar um dashboard para um elemento div na sua página Web.

**Default.aspx**

```
<!-- Embed Dashboard-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a dashboard</div>

            <div>Enter an embed url for a dashboard from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedDashboardAction" value="Embed Dashboard" />
        </div>

        <div id="dashboardContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected dashboard.
    var el = document.getElementById("bEmbedDashboardAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedDashboard, false);
    } else {
        el.attachEvent('onclick', updateEmbedDashboard);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded dashboard if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedDashboard();
    }
};

// update embed dashboard
function updateEmbedDashboard() {

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
        type: 'dashboard',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the dashboard.
    var dashboardContainer = document.getElementById('dashboardContainer');

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("tileClicked", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Se transferiu e executou o [exemplo Integrar um dashboard](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app), o exemplo será semelhante ao que se segue.

![](media/integrate-dashboard/powerbi-embed-dashboard.png)

## <a name="tile-clicked-events"></a>Eventos de clique em mosaico
No exemplo acima, pode ter reparado que pode gerir eventos quando o mosaico no dashboard é clicado. Para obter mais informações sobre eventos, consulte [Handling Events within the JavaScript API (Gerir Eventos na API do JavaScript - em inglês)](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

```
// dashboard.on will add an event handler which prints to Log window.
dashboard.on("tileClicked", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});

// dashboard.on will add an event handler which prints to Log window.
dashboard.on("error", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Error<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});
```

Se transferiu e instalou o [exemplo Integrar um dashboard](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/PowerBI.com%20Integrate/integrate-dashboard-web-app), clicar num mosaico irá fazer surgir texto abaixo do dashboard. O texto terá um aspeto semelhante a este. Isto permitir-lhe-á registar o clique num mosaico e, em seguida, direcionar o utilizador para a localização adequada.

```
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "", "navigationUrl": "https://app.powerbi.com/dashboards/fcff76f9-15ff-4a8e-8242-275ac9c25b90/qna?q=count%20of%20new%20hires%20from%20July%202014%20to%20December%202014", "tileId": "0e99b45c-9b53-4920-b239-cee7d37d2369" }
---------
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "https://app.powerbi.com/reportEmbed?reportId=ab199308-80b1-4626-9823-43a84623bd9c", "navigationUrl": "https://app.powerbi.com/reports/ab199308-80b1-4626-9823-43a84623bd9c/ReportSection1", "tileId": "ffc30447-674a-4511-944f-79e182d719de", "pageName": "ReportSection1" }
---------
```

## <a name="working-with-groups-app-workspaces"></a>Trabalhar com grupos (áreas de trabalho de aplicações)
Para incorporar um dashboard a partir de um grupo (área de trabalho de aplicação), irá querer obter a lista de todos os dashboards disponíveis num grupo através da seguinte chamada à API REST. Para obter mais informações sobre esta chamada à API REST, consulte [Obter Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Terá de ter permissão no grupo para o pedido para devolver resultados.

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards
```

A API acima devolve a lista dos dashboards disponíveis. Cada dashboard tem uma propriedade EmbedUrl já criada para suportar a incorporação de grupos.

```
https://app.powerbi.com/dashboardEmbed?dashboardId={dashboardId}&groupId={groupId}
```

## <a name="limitations"></a>Limitações
* Os utilizadores finais que acedem aos dashboards incorporados têm de ter uma conta do Power BI e ter acesso ao dashboard. Ou eles são proprietários do dashboard, ou o dashboard foi partilhado com o utilizador.
* Atualmente, as Perguntas e Respostas não são suportadas em dashboards incorporados.
* Como limitação temporária, ao partilhar um dashboard com grupos de segurança, os utilizadores têm primeiro de aceder aos dashboards em PowerBI.com antes de os poderem ver incorporados.

## <a name="next-steps"></a>Próximos passos
Um exemplo de aplicação está disponível no GitHub para rever. Os exemplos acima baseiam-se nesse exemplo. Para obter mais informações, veja [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app).

Estão disponíveis mais informações para a API JavaScript em [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

