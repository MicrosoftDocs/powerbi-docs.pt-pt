---
title: "Integrar um relatório do Power BI numa aplicação para a sua organização"
description: "Saiba como integrar ou incorporar um relatório numa aplicação Web com as APIs do Power BI."
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
ms.openlocfilehash: 8285cbbc2d8dee653863cad50036da58362c32d1
ms.sourcegitcommit: 7517c068db806f12bb0b953e9a1bd4249ca12da5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2018
---
# <a name="integrate-a-report-into-an-app-for-your-organization"></a>Integrar um relatório numa aplicação para a sua organização
Saiba como integrar ou incorporar um relatório numa aplicação Web através de chamadas à API REST, juntamente com a API JavaScript do Power BI ao incorporar para a sua organização.

![Exemplo de relatório incorporado](media/integrate-report/powerbi-embedded-report.png)

Para começar estas instruções, precisa de uma conta do **Power BI**. Se não tiver uma conta, pode [inscrever-se numa conta gratuita do Power BI](../service-self-service-signup-for-power-bi.md) ou pode criar o seu próprio [inquilino do Azure Active Directory](create-an-azure-active-directory-tenant.md) para fins de teste.

> [!NOTE]
> Quer incorporar um relatório para os seus clientes através de um embedtoken? Consulte [Integrar um dashboard, mosaico ou relatório na sua aplicação para os seus clientes](embed-sample-for-customers.md).
> 
> 

Para integrar um relatório numa aplicação Web, utilize a API REST do **Power BI** ou o SDK C# do Power BI e um **token de acesso** de autorização do Azure Active Directory (AD) para obter um relatório. Em seguida, carregue o relatório com o mesmo token de acesso. A API do **Power BI** fornece acesso programático a determinados recursos do **Power BI**. Para obter mais informações, consulte [Descrição geral da API REST do Power BI](https://msdn.microsoft.com/library/dn877544.aspx) e [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Transferir o exemplo
Este artigo mostra o código utilizado em [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app) no GitHub. Para acompanhar estas instruções, pode transferir o exemplo.

## <a name="step-1---register-an-app-in-azure-ad"></a>Passo 1 – registar uma aplicação no Azure AD
Terá de registar a sua aplicação no Azure AD para fazer chamadas à API REST. Para obter mais informações, consulte [Registar uma aplicação do Azure AD para incorporar conteúdo do Power BI](register-app.md).

Se transferiu [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), utilize o **ID de Cliente** e o **Segredo do Cliente** que recebe após o registo para que o exemplo possa ser autenticado no Azure AD. Para configurar o exemplo, altere o **ID de Cliente** e o **Segredo do Cliente** no ficheiro *cloud.config*.

![](media/integrate-report/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Passo 2 – obter um token de acesso do Azure AD
Na sua aplicação, primeiro terá de obter um **token de acesso** do Azure AD antes de poder fazer chamadas à API REST do Power BI. Para obter mais informações, consulte [Autenticar utilizadores e obter um token de acesso do Azure AD para a sua aplicação do Power BI](get-azuread-access-token.md).

## <a name="step-3---get-a-report"></a>Passo 3 – obter um relatório
Para obter um relatório do **Power BI**, utilize a operação [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx) que obtém uma lista dos relatórios do **Power BI**. Da lista de relatórios, pode obter um ID de relatório.

### <a name="get-reports-using-an-access-token"></a>Obter relatórios com um token de acesso
Com o **token de acesso** que obteve no [passo 2](#step-2-get-an-access-token-from-azure-ad), pode chamar a operação [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx). A operação [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx) devolve uma lista de relatórios. Pode obter um único relatório a partir da lista de relatórios. Segue-se um método C# completo para obter um relatório. 

Para efetuar a chamada à API REST, tem de incluir um cabeçalho de *Autorização* no formato de *Portador {token de acesso}*.

#### <a name="get-reports-with-the-rest-api"></a>Obter relatórios com a API REST
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-using-the-net-sdk"></a>Obter relatórios com o SDK .NET
Pode utilizar o SDK .NET para obter uma lista de relatórios em vez de chamar a API REST diretamente.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

## <a name="step-4---load-a-report-using-javascript"></a>Passo 4 – carregar um relatório com JavaScript
Pode utilizar JavaScript para carregar um relatório para um elemento div na sua página Web.

**Default.aspx**

```
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReporte, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

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
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

Se transferiu e executou [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), o exemplo será semelhante ao que se segue.

![Exemplo de relatório incorporado](media/integrate-report/powerbi-embedded-report.png)

## <a name="working-with-groups-app-workspaces"></a>Trabalhar com grupos (áreas de trabalho de aplicações)
Para incorporar um relatório a partir de um grupo (área de trabalho de aplicações), irá querer obter a lista de todos os relatórios disponíveis no dashboard de um grupo através da seguinte chamada à API REST. Para obter mais informações sobre esta chamada à API REST, consulte [Obter Relatórios](https://msdn.microsoft.com/library/mt634543.aspx). Terá de ter permissão no grupo para o pedido para devolver resultados.

```
https://api.powerbi.com/v1.0/myorg/groups/{group_id}/reports
```

A API acima devolve a lista dos relatórios disponíveis. Cada relatório tem uma propriedade EmbedUrl já criada para suportar a incorporação de grupos.

```
https://app.powerbi.com/reportEmbed?reportId={report_id}&groupId={group_id}
```

## <a name="next-steps"></a>Próximos passos
Um exemplo de aplicação está disponível no GitHub para rever. Para obter mais informações, consulte [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app).

Estão disponíveis mais informações para a API JavaScript em [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

