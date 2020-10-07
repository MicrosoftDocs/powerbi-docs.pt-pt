---
title: API para exportar relatórios paginados do Power BI
description: Saiba como exportar um relatório paginado do Power BI incorporado
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: bb06f5b0a170189c3c98b734a09259645a650c55
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748178"
---
# <a name="export-paginated-report-to-file-preview"></a>Exportar relatórios paginados para ficheiros (pré-visualização)

A API `exportToFile` permite exportar um relatório paginado do Power BI através de uma chamada REST. São suportados os seguintes formatos de ficheiro:
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Imagem**
    * Ao exportar para uma imagem, defina o formato de imagem através da definição de formato `OutputFormat`
    * Os valores OutputFormat suportados são: .bmp, .emf, .gif, .jpeg, .png ou .tiff (predefinição)

## <a name="usage-examples"></a>Exemplos de utilização

Pode utilizar a funcionalidade de exportação de várias formas. Veja a seguir alguns exemplos:

* **Botão Enviar para impressão** – na aplicação, crie um botão que, quando clicado, aciona uma tarefa de exportação. A tarefa pode exportar o relatório visualizado como .pdf ou .pptx e, quando estiver concluída, o utilizador pode receber o ficheiro como transferência. Com as definições de formato e parâmetros de relatório, pode exportar o relatório num estado específico, incluindo dados filtrados, tamanhos de página personalizados e outras definições específicas do formato. Como a API é assíncrona, pode demorar algum tempo até o ficheiro estar disponível.

* **Enviar anexo por e-mail** – envie um e-mail automatizado, em intervalos definidos, com um relatório .pdf anexado. Este cenário poderá ser útil se quiser automatizar o envio de um relatório semanal aos executivos.

## <a name="using-the-api"></a>Utilizar a API

A API é assíncrona. Quando a API [exportToFile](/rest/api/power-bi/reports/exporttofile) é chamada, aciona uma tarefa de exportação. Depois de acionar uma tarefa de exportação, utilize a [consulta](/rest/api/power-bi/reports/getexporttofilestatus) para controlar a tarefa, até estar concluída.

Quando a exportação estiver concluída, a chamada à API de consulta devolve um [URL do Power BI](/rest/api/power-bi/reports/getfileofexporttofile) para obter o ficheiro. O URL estará disponível durante 24 horas.

## <a name="supported-features"></a>Funcionalidades suportadas

### <a name="format-settings"></a>Definições de formato

Especifique uma variedade de definições de formato para cada formato de ficheiro. Os valores e propriedades suportados são equivalentes a [parâmetros de Informações do Dispositivo](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) para parâmetros de URL de relatório paginado.

Eis dois exemplos, um para exportar as primeiras quatro páginas de um relatório com o tamanho da página do relatório para um ficheiro .pptx e outro para exportar a terceira página de um relatório para um ficheiro .jpeg.

**Exportar as primeiras quatro páginas para um .pptx**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**Exportar a terceira página para um .jpeg**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Parâmetros do relatório

Pode utilizar a API `exportToFile` para exportar programaticamente um relatório com um conjunto de parâmetros de relatório. Esta ação é efetuada com funcionalidades de [parâmetro de relatório](../../paginated-reports/paginated-reports-parameters.md).

Eis um exemplo para definir valores de parâmetro de relatório.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Autenticação

Pode autenticar com um utilizador (ou utilizador principal) ou um [principal de serviço](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Segurança ao Nível da Linha (RLS)

Ao utilizar um conjunto de dados do Power BI que tem a Segurança a Nível da Linha (RLS) definida como uma origem de dados, pode exportar uma relatório a mostrar dados que só são visíveis para determinados utilizadores. Por exemplo, se estiver a exportar um relatório de vendas definido com funções regionais, poderá filtrá-lo programaticamente para que seja apresentada apenas uma determinada região.

Para exportar com RLS, tem de ter permissão de leitura para o conjunto de dados do Power BI que o relatório está a utilizar como origem de dados.

Eis um exemplo para fornecer um nome de utilizador eficaz para RLS.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>Exemplos de código

O SDK da API do Power BI utilizado nos exemplos de código pode ser transferido [aqui](https://www.nuget.org/packages/Microsoft.PowerBI.Api).

Ao criar uma tarefa de exportação, existem três passos a seguir:

1. Enviar um pedido de exportação.
2. Consulta.
3. Obter o ficheiro.

Esta secção mostra exemplos de cada passo.

### <a name="step-1---sending-an-export-request"></a>Passo 1 – enviar um pedido de exportação

O primeiro passo é enviar um pedido de exportação. Neste exemplo, é enviado um pedido de exportação para valores de parâmetro de relatório, tamanho e intervalo de página específico.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Passo 2 – consulta

Depois de enviar um pedido de exportação, utilize a consulta para identificar quando o ficheiro de exportação que aguarda está pronto.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Passo 3 – obter o ficheiro

Depois de a consulta devolver um URL, utilize este exemplo para obter o ficheiro recebido.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Exemplo ponto a ponto

Trata-se de um exemplo ponto a ponto para exportar um relatório. Este exemplo inclui os seguintes passos:
1. [Enviar o pedido de exportação](#step-1---sending-an-export-request).
2. [Consulta](#step-2---polling).
3. [Obter o ficheiro](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Próximas etapas

Veja como incorporar conteúdo para os seus clientes e organização:

> [!div class="nextstepaction"]
>[Exportar relatório para ficheiro](export-to.md)

> [!div class="nextstepaction"]
>[Incorporar para os seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)