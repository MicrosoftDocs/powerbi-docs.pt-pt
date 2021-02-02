---
title: Exportar a API dos relatórios da análise incorporada do Power BI para obter melhores informações de BI incorporadas
description: Saiba como exportar um relatório do Power BI incorporado para melhorar a experiência de BI incorporada da análise incorporada do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 02/01/2021
ms.openlocfilehash: 64a9472960195c8d4f91013a778bb61cdf029ab4
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2021
ms.locfileid: "99422358"
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

* **Enviar anexo por e-mail** – envie um e-mail automatizado, em intervalos definidos, com um relatório .pdf anexado. Este cenário poderá ser útil se quiser automatizar o envio de um relatório semanal aos executivos. Para obter mais informações, veja [Exportar e enviar um relatório do Power BI por e-mail com o Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)

## <a name="using-the-api"></a>Utilizar a API

Antes de utilizar a API, verifique se estão ativadas as seguintes [definições de inquilino de administração](../../admin/service-admin-portal.md#tenant-settings):
* **Exportar relatórios como apresentações do PowerPoint ou documentos PDF** – ativada por predefinição.
* **Exportar relatórios como ficheiros de imagem** – obrigatória apenas para *.png* e desativada por predefinição.

A API é assíncrona. Quando a API [exportToFile](/rest/api/power-bi/reports/exporttofile) é chamada, aciona uma tarefa de exportação. Depois de acionar uma tarefa de exportação, utilize a [consulta](/rest/api/power-bi/reports/getexporttofilestatus) para controlar a tarefa, até estar concluída.

Durante a consulta, a API devolve um número que representa a quantidade de trabalho concluído. O trabalho em cada trabalho de exportação é calculado com base no total das exportações no trabalho. Uma exportação inclui a exportação de um único visual, ou uma página com ou sem marcadores. Todas as exportações têm o mesmo peso. Se, por exemplo, o seu trabalho de exportação incluir a exportação de um relatório com 10 páginas, e a votação devolver 70, significa que a API processou sete das 10 páginas do trabalho de exportação.

Quando a exportação estiver concluída, a chamada à API de consulta devolve um [URL do Power BI](/rest/api/power-bi/reports/getfileofexporttofile) para obter o ficheiro. O URL estará disponível durante 24 horas.

## <a name="supported-features"></a>Funcionalidades suportadas

Esta secção descreve o funcionamento das seguintes funcionalidades suportadas:

* [Selecionar as páginas a imprimir](#selecting-which-pages-to-print)
* [Exportando uma página ou um único visual](#exporting-a-page-or-a-single-visual)
* [Marcadores](#bookmarks)
* [Filtros](#filters)
* [Autenticação](#authentication)
* [Segurança ao Nível da Linha (RLS)](#row-level-security-rls)
* [Proteção de dados](#data-protection)
* [Localização](#localization)

### <a name="selecting-which-pages-to-print"></a>Selecionar as páginas a imprimir

Especifique as páginas que quer imprimir de acordo com o valor devolvido de [Obter Páginas](/rest/api/power-bi/reports/getpages) ou [Obter Páginas no Grupo](/rest/api/power-bi/reports/getpagesingroup). Também pode especificar a ordem das páginas que está a exportar.

### <a name="exporting-a-page-or-a-single-visual"></a>Exportando uma página ou um único visual

Pode especificar uma página ou um único visual para exportar. As páginas podem ser exportadas com ou sem marcadores.

Dependendo do tipo de exportação, é necessário passar diferentes atributos para o objeto [ExportReportPage.](/rest/api/power-bi/reports/exporttofile#exportreportpage) O quadro a seguir especifica quais os atributos necessários para cada trabalho de exportação.  

>[!NOTE]
>Exportar um único visual tem o mesmo peso que exportar uma página (com ou sem marcadores). Isto significa que, em termos de cálculos do sistema, ambas as operações têm o mesmo valor.

|Atributo   |Página     |Visuais únicos  |Comentários|
|------------|---------|---------|---|
|`bookmark`  |Opcional |![Não se aplica a:](../../media/no.png)|Utilizar para exportar uma página num estado específico|
|`pageName`  |![Aplica-se a:](../../media/yes.png)|![Aplica-se a:](../../media/yes.png)|Utilize a [API GETPages](/rest/api/power-bi/reports/getpage) REST ou a `getPages` API do cliente. Para mais informações consulte [Obter páginas e visuais.](/javascript/api/overview/powerbi/get-visuals)   |
|`visualName`|![Não se aplica a:](../../media/no.png)|![Aplica-se a:](../../media/yes.png)|Há duas maneiras de obter o nome do visual:<li>Use a `getVisuals` API cliente. Para obter mais informações, consulte [obter páginas e visuais.](/javascript/api/overview/powerbi/get-visuals)</li><li>Ouça e registe o evento *visualClicked,* que é desencadeado quando um visual é selecionado. Para mais informações, consulte [Como lidar com eventos](/javascript/api/overview/powerbi/handle-events)</li>. |

### <a name="bookmarks"></a>Marcadores

Os [marcadores](../../consumer/end-user-bookmarks.md) podem ser utilizados para guardar um relatório numa configuração específica, incluindo filtros aplicados e o estado dos elementos visuais do relatório. Pode utilizar a API [exportToFile](/rest/api/power-bi/reports/exporttofile) para exportar programaticamente o marcador de um relatório de duas formas:

* **Exportar um marcador existente**

    Para exportar um [marcador de relatório existente](../../consumer/end-user-bookmarks.md#report-bookmarks), utilize a propriedade `name`, um identificador exclusivo (sensível a maiúsculas e minúsculas) que pode obter através da [API JavaScript de marcadores](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

* **Exportar o estado do relatório**

    Para exportar o estado atual do relatório, use a propriedade `state`. Por exemplo, pode utilizar o método `bookmarksManager.capture` do marcador para capturar as alterações que um utilizador específico fez a um relatório e, em seguida, exportá-lo no estado atual com `capturedBookmark.state`.

>[!NOTE]
>Não são suportados [marcadores pessoais](../../consumer/end-user-bookmarks.md#personal-bookmarks) nem [filtros persistentes](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/).

### <a name="filters"></a>Filtros

Com `reportLevelFilters` em [PowerBIReportExportConfiguration](/rest/api/power-bi/reports/exporttofile#powerbireportexportconfiguration), pode exportar um relatório numa condição filtrada.

Para exportar um relatório filtrado, introduza os [parâmetros de cadeia de consulta de URL](../../collaborate-share/service-url-filters.md) que pretende utilizar como filtro, para [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter). Ao introduzir a cadeia, tem de remover a parte `?filter=` do parâmetro de consulta de URL.

A tabela abaixo inclui alguns exemplos de sintaxe de cadeias que pode transmitir para `ExportFilter`.

|Filtro    |Syntax    |Exemplo    |
|---|----|----|----|
|Um valor num campo    |Table/Field eq 'value'    |Store/Territory eq 'NC'    |
|Vários valores num campo    |Table/Field in ('value1', 'value2')     |Store/Territory in ('NC', 'TN')    |
|Um valor distinto num campo e um valor diferente noutro campo    |Table/Field1 eq 'value1' and Table/Field2 eq 'value2'    |Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'    |

>[!NOTE]
>`ReportLevelFilters` só pode conter um único [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter).

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

>[!NOTE]
>A exportação de um relatório do Power BI para um ficheiro através da `exporToFile`API não é suportada para o [Premium Por Utilizador (PPU)](../../admin/service-premium-per-user-faq.md). 

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
* Para visualização pública, o número de exportações de Power BI por hora é limitado a 50 por capacidade. Uma exportação refere-se à exportação de uma única página visual ou de relatório com ou sem marcadores, e não inclui a exportação de relatórios paginados.
* Os relatórios exportados não podem exceder o tamanho de ficheiro de 250 MB.
* Ao exportar para .png, as etiquetas de confidencialidade não são suportadas.
* O número de exportações (visuais únicos ou páginas de relatório) que podem ser incluídas num relatório exportado é de 50 (isto não inclui a exportação de relatórios paginados). Se o pedido incluir mais exportações, a API devolve um erro e o trabalho de exportação é cancelado.
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
    IList<string> pageNames = null, /* Get the page names from the GetPages REST API */
    string urlFilter = null)
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
        // ReportLevelFilters collection needs to be instantiated explicitly
        ReportLevelFilters = !string.IsNullOrEmpty(urlFilter) ? new List<ExportFilter>() { new ExportFilter(urlFilter) } : null,

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
    IList<string> pageNames = null,  /* Get the page names from the GetPages REST API */
    string urlFilter = null)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames, urlFilter);
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

> [!div class="nextstepaction"]
>[Exportar e enviar um relatório do Power BI por e-mail com o Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)
