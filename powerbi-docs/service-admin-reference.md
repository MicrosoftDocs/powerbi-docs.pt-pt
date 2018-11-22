---
title: APIs REST, SDK .NET e cmdlets do PowerShell para administradores
description: Saiba de que formas pode administrar o Power BI através de scripts e APIs de programação.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 1ed4298e4ed4cddcdf965bd427c654cab6adf1e6
ms.sourcegitcommit: 46f1ba3f972f6e64bce05ad0fd527b27c49aedd6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52157017"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>APIs REST, SDK .NET e cmdlets do PowerShell para administração do Power BI
O Power BI permite que os administradores efetuem o scripting de tarefas comuns com cmdlets do PowerShell. Também expõe as APIs REST e fornece um SDK .NET para desenvolver soluções administrativas. Este tópico mostra uma lista de cmdlets e o método SDK e o ponto final de API REST correspondentes. Para obter mais informações, veja:

- [Transferência](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) e [documentação](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) do PowerShell
- [Documentação](https://docs.microsoft.com/rest/api/power-bi/admin) da API REST
- [Transferência](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) do SDK .NET

| **Nome do cmdlet** | **Aliases** | **Método SDK** | **Ponto final de API REST** | **Descrição** |
| --- | --- | --- | --- | --- |
| **Get-PowerBIDatasource** | N/D | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtém as origens de dados de um determinado conjunto de dados. |
| **Get-PowerBIDataset** | N/D | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | Obtém a lista completa de conjuntos de dados num inquilino do Power BI. |
| **Get-PowerBIWorkspace** | **Get-PowerBIGroup** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Obtém a lista completa de áreas de trabalho num inquilino do Power BI. |
| **Add-PowerBIWorkspaceUser** | **Add-PowerBIGroupUser** |Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Adiciona um utilizador como membro de uma determinada área de trabalho. |
| **Remove-PowerBIWorkspaceUser** | **Remove-PowerBIGroupUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Remove um utilizador da lista de membros de uma determinada área de trabalho. |
| **Restore-PowerBIWorkspace** |**Restore-PowerBIGroup** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Restaura uma área de trabalho eliminada. |
| **Set-PowerBIWorkspace** |**Set-PowerBIGroup** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Atualiza as propriedades de uma determinada área de trabalho. |
| **Get-PowerBIDataset -WorkspaceId** | N/D | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtém os conjuntos de dados dentro de uma determinada área de trabalho. |
| **Export-PowerBIReport** | N/D | Reports\_ExportReportAsAdmin | N/D | Exporta um determinado relatório para um ficheiro local. |
| **Get-PowerBIReport** | N/D | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Obtém a lista completa de conjuntos de relatórios num inquilino do Power BI. |
| **Get-PowerBIDashboard** | N/D | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Obtém a lista completa de dashboards num inquilino do Power BI. |
| **Get-PowerBIDashboard** | N/D | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtém os dashboards dentro de uma determinada área de trabalho. |
| **Get-PowerBITile** | **Get-PowerBIDashboardTile** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtém os mosaicos de um determinado dashboard. |
| **Get-PowerBIReport** | N/D | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtém os relatórios dentro de uma determinada área de trabalho. |
| **Get-PowerBIImport** | N/D | Imports\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Obtém a lista completa de importações num inquilino do Power BI. |
| **Connect-PowerBIServiceAccount** | **Login-PowerBI** &  **Login-PowerBIServiceAccount** | N/D | N/D | Inicia sessão no Power BI e começa uma sessão. |
| **Disconnect-PowerBIServiceAccount** | **Logout-PowerBI** & **Logout-PowerBIServiceAccount** | N/D | N/D | Termina a sessão no Power BI e fecha a sessão existente. |
| **Invoke-PowerBIRestMethod**| N/D | N/D | N/D | Envia chamadas arbitrárias à API REST para o Power BI. |
| **Get-PowerBIAccessToken**| N/D | N/D | N/D | Obtém o token de acesso do Power BI numa sessão. |
| **Resolve-PowerBIError**| N/D | N/D | N/D | Obtém informações detalhadas sobre os erros de ativações de cmdlets sem erro. |