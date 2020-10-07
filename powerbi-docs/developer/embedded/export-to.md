---
title: API para exportar relatórios do Power BI
description: Saiba como exportar um relatório do Power BI incorporado
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 07/13/2020
ms.openlocfilehash: f024959c0d7e8bd0b51893a277161c67b5f4dfc6
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746131"
---
# <a name="export-power-bi-report-to-file-preview"></a>Exportar relatório do Power BI para ficheiro (pré-visualização)

A API `exportToFile` permite exportar um relatório do Power BI através de uma chamada REST. São suportados os seguintes formatos de ficheiro:
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * Ao exportar para um .png, os relatórios com várias páginas são comprimidos num ficheiro .zip
    * Cada ficheiro no .zip representa uma página de relatório
    * Os nomes de página são os mesmos que os valores devolvidos das APIs [Obter Páginas](/rest/api/power-bi/reports/getpages) ou [Obter Páginas no Grupo](/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Exemplos de utilização

Pode utilizar a funcionalidade de exportação de várias formas. Veja a seguir alguns exemplos:

* **Botão Enviar para impressão** – na aplicação, crie um botão que, quando clicado, aciona uma tarefa de exportação. A tarefa pode exportar o relatório visualizado como .pdf ou .pptx e, quando estiver concluída, o utilizador pode receber o ficheiro como transferência. Através de marcadores, pode exportar o relatório num estado específico, incluindo filtros configurados, segmentações de dados e definições adicionais. Como a API é assíncrona, pode demorar algum tempo até o ficheiro estar disponível.

* **Enviar anexo por e-mail** – envie um e-mail automatizado, em intervalos definidos, com um relatório .pdf anexado. Este cenário poderá ser útil se quiser automatizar o envio de um relatório semanal aos executivos.

## <a name="using-the-api"></a>Utilizar a API

Antes de utilizar a API, verifique se estão ativadas as seguintes [definições de inquilino de administração](../../admin/service-admin-portal.md#tenant-settings):
* **Exportar relatórios como apresentações do PowerPoint ou documentos PDF** – ativada por predefinição.
* **Exportar relatórios como ficheiros de imagem** – obrigatória apenas para *.png* e desativada por predefinição.

A API é assíncrona. Quando a API [exportToFile](/rest/api/power-bi/reports/exporttofile) é chamada, aciona uma tarefa de exportação. Depois de acionar uma tarefa de exportação, utilize a [consulta](/rest/api/power-bi/reports/getexporttofilestatus) para controlar a tarefa, até estar concluída.

Durante a consulta, a API devolve um número que representa a quantidade de trabalho concluído. O trabalho em cada tarefa de exportação é calculado com base no número de páginas que o relatório tem. Todas as páginas têm o mesmo tamanho. Por exemplo, se estiver a exportar um relatório com 10 páginas e a consulta devolver 70, significa que a API processou sete das 10 páginas na tarefa de exportação.

Quando a exportação estiver concluída, a chamada à API de consulta devolve um [URL do Power BI](/rest/api/power-bi/reports/getfileofexporttofile) para obter o ficheiro. O URL estará disponível durante 24 horas.

## <a name="supported-features"></a>Funcionalidades suportadas

### <a name="selecting-which-pages-to-print"></a>Selecionar as páginas a imprimir

Especifique as páginas que quer imprimir de acordo com o valor devolvido de [Obter Páginas](/rest/api/power-bi/reports/getpages) ou [Obter Páginas no Grupo](/rest/api/power-bi/reports/getpagesingroup). Também pode especificar a ordem das páginas que está a exportar.

### <a name="bookmarks"></a>Marcadores

 Pode utilizar a API `exportToFile` para exportar programaticamente um relatório num estado específico, depois de aplicar filtros. Este procedimento é feito com as capacidades de [Marcadores](../../consumer/end-user-bookmarks.md). Para exportar um relatório com marcadores, utilize a [API JavaScript de marcadores](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

 Por exemplo, pode utilizar o método `capturedBookmark.state` do marcador para capturar as alterações que um utilizador específico fez a um relatório e, em seguida, exportá-lo no estado atual.

Não são suportados [marcadores pessoais](../../consumer/end-user-bookmarks.md#personal-bookmarks) nem [filtros persistentes](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/).

### <a name="authentication"></a>Autenticação

Pode autenticar com um utilizador (ou utilizador principal) ou um [principal de serviço](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Segurança ao Nível da Linha (RLS)

Com a [Segurança ao Nível da Linha (RLS)](embedded-row-level-security.md), pode exportar um relatório que mostre dados apenas visíveis para certos utilizadores. Por exemplo, se estiver a exportar um relatório de vendas definido com funções regionais, poderá filtrá-lo programaticamente para que seja apresentada apenas uma determinada região.

Para exportar com RLS, tem de ter as seguintes permissões:
* Permissões de escrita e de nova partilha para o conjunto de dados a que o relatório está ligado
* Se o relatório residir numa área de trabalho v1, terá de ser o administrador da área de trabalho
* Se o relatório residir numa área de trabalho v2, terá de ser membro ou o administrador da área de trabalho

### <a name="data-protection"></a>Proteção de dados

Os formatos .pdf e .pptx suportam [etiquetas de confidencialidade](../../admin/service-security-sensitivity-label-overview.md). Se exportar um relatório com uma etiqueta de confidencialidade para .pdf ou .pptx, o ficheiro exportado apresentará o relatório com a etiqueta de confidencialidade.

Um relatório com uma etiqueta de confidencialidade não pode ser exportado para um .pdf ou um .pptx através de um [principal de serviço](embed-service-principal.md).

### <a name="localization"></a>Localização

Ao utilizar a API `exportToFile`, pode transmitir o local desejado. As definições de localização afetam a forma como o relatório é apresentado, por exemplo, ao alterar a formatação de acordo com o local selecionado.

## <a name="concurrent-requests"></a>Pedidos simultâneos

`exportToFile` suporta pedidos de tarefas de exportação simultâneos. A tabela abaixo mostra o número de tarefas que pode executar ao mesmo tempo, consoante o SKU em que o relatório reside. Os pedidos simultâneos referem-se a páginas de relatório. Por exemplo, 20 páginas num pedido de exportação de um SKU A6 serão processadas simultaneamente. Este processamento demorará aproximadamente o mesmo tempo que o envio de 20 pedidos de exportação com uma página cada.

Uma tarefa que exceda o número de pedidos simultâneos não termina. Por exemplo, se exportar três páginas num SKU A1, a primeira tarefa será executada e as duas últimas esperarão pelos próximos dois ciclos de execução.

|SKU do Azure  |SKU do Office  |Número máximo de páginas simultâneas  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Limitações

* O relatório que está a exportar tem de residir numa capacidade Premium ou Incorporada.
* O conjunto de dados do relatório que está a exportar tem de residir numa capacidade Premium ou Incorporada.
* Na pré-visualização pública, o número de páginas de relatórios do Power BI exportadas por hora está limitado a 50 por capacidade.
* Os relatórios exportados não podem exceder o tamanho de ficheiro de 250 MB.
* Ao exportar para .png, as etiquetas de confidencialidade não são suportadas.
* O número de páginas que podem ser incluídas num relatório exportado é de 50. Se o relatório incluir mais páginas, a API devolverá um erro e a tarefa de exportação será cancelada.
* Não são suportados [marcadores pessoais](../../consumer/end-user-bookmarks.md#personal-bookmarks) nem [filtros persistentes](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/).
* Os elementos visuais do Power BI listados abaixo não são suportados. Quando for exportado um relatório com estes elementos visuais, as partes do relatório que contêm estes elementos visuais não serão compostas e apresentarão um símbolo de erro.
    * Elementos visuais do Power BI não certificados
    * Visuais R
    * PowerApps
    * Elementos visuais do Python
    * Visio

## <a name="code-examples"></a>Exemplos de código

Ao criar uma tarefa de exportação, existem três passos a seguir:

1. [Enviar um pedido de exportação](#step-1---sending-an-export-request).
2. [Consulta](#step-2---polling).
3. [Obter o ficheiro](#step-3---getting-the-file).
4. [Utilizar o fluxo de ficheiros](#step-4---using-the-file-stream).

Esta secção mostra exemplos de cada passo.

### <a name="step-1---sending-an-export-request"></a>Passo 1 – enviar um pedido de exportação

O primeiro passo é enviar um pedido de exportação. Neste exemplo, é enviado um pedido de exportação para uma página específica.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages REST API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Passo 2 – consulta

Depois de enviar um pedido de exportação, utilize a consulta para identificar quando o ficheiro de exportação que aguarda está pronto.

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### <a name="step-3---getting-the-file"></a>Passo 3 – obter o ficheiro

Depois de a consulta devolver um URL, utilize este exemplo para obter o ficheiro recebido.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="step-4---using-the-file-stream"></a>Passo 4 – Utilizar o fluxo de ficheiros

Quando tiver o fluxo de ficheiros, pode processá-lo da forma que melhor se adequa às suas necessidades. Por exemplo, pode enviar um e-mail ou utilizá-lo para transferir os relatórios exportados.

### <a name="end-to-end-example"></a>Exemplo ponto a ponto

Trata-se de um exemplo ponto a ponto para exportar um relatório. Este exemplo inclui os seguintes passos:
1. [Enviar o pedido de exportação](#step-1---sending-an-export-request).
2. [Consulta](#step-2---polling).
3. [Obter o ficheiro](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null  /* Get the page names from the GetPages REST API */)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
            var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
            export = httpMessage.Body;
            if (export == null)
            {
                // Error, failure in exporting the report
                return null;
            }
            if (export.Status == ExportState.Failed)
            {
                // Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
                // In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                if(retryAfter == null)
                {
                    // Failed state with no RetryAfter header indicates that the export failed permanently
                    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Próximos passos

Veja como incorporar conteúdo para os seus clientes e organização:

> [!div class="nextstepaction"]
>[Export paginated report to file](export-paginated-report.md) (Exportar relatórios paginados para ficheiros)

> [!div class="nextstepaction"]
>[Incorporar para os seus clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)