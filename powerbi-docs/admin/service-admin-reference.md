---
title: Bibliotecas de Cliente cmdlet, API REST e .NET para administradores
description: Saiba de que formas pode administrar o Power BI através de scripts e APIs de programação.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: e1c95c330687131a29753359f5223e096bddab1d
ms.sourcegitcommit: e9cd61eaa66eda01cc159251d7936a455c55bd84
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2020
ms.locfileid: "86952622"
---
# <a name="powershell-cmdlets-rest-apis-and-net-client-library-for-power-bi-administration"></a>Bibliotecas de Cliente cmdlet, API REST e .NET para administração do Power BI
O Power BI permite que os administradores efetuem o scripting de tarefas comuns com cmdlets do PowerShell. Também expõe as API REST e fornece uma biblioteca de cliente .NET para desenvolver soluções administrativas. Este tópico mostra uma lista de cmdlets e o ponto final de API e de API REST correspondentes. Para obter mais informações, veja:

- [Transferência](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) e [documentação](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) do PowerShell
- [Documentação](https://docs.microsoft.com/rest/api/power-bi/admin) da API REST
- [Transferir](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) a biblioteca de cliente .NET

> Os cmdlets abaixo devem ser chamados com `-Scope Organization` para utilizar com o inquilino para a administração.

| **Nome do cmdlet** | **Aliases** | **API** | **Ponto final de API REST** | **Descrição** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/D | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtém as origens de dados de um determinado conjunto de dados. |
| `Get-PowerBIDataset` | N/D | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Obtém a lista completa de conjuntos de dados num inquilino do Power BI. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Obtém a lista completa de áreas de trabalho num inquilino do Power BI. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Adiciona um utilizador como membro de uma determinada área de trabalho. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Remove um utilizador da lista de membros de uma determinada área de trabalho. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Restaura uma área de trabalho eliminada. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Atualiza as propriedades de uma determinada área de trabalho. |
| `Get-PowerBIDataset -WorkspaceId` | N/D | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtém os conjuntos de dados dentro de uma determinada área de trabalho. |
| `Get-PowerBIReport` | N/D | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Obtém a lista completa de conjuntos de relatórios num inquilino do Power BI. |
| `Get-PowerBIDashboard` | N/D | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Obtém a lista completa de dashboards num inquilino do Power BI. |
| `Get-PowerBIDashboard -WorkspaceId` | N/D | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtém os dashboards dentro de uma determinada área de trabalho. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtém os mosaicos de um determinado dashboard. |
| `Get-PowerBIReport` | N/D | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtém os relatórios dentro de uma determinada área de trabalho. |
| `Get-PowerBIImport` | N/D | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Obtém a lista completa de importações num inquilino do Power BI. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/D | N/D | Inicia sessão no Power BI e começa uma sessão. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/D | N/D | Termina a sessão no Power BI e fecha a sessão existente. |
| `Invoke-PowerBIRestMethod`| N/D | N/D | N/D | Envia chamadas arbitrárias à API REST para o Power BI. |
| `Get-PowerBIAccessToken`| N/D | N/D | N/D | Obtém o token de acesso do Power BI numa sessão. |
| `Resolve-PowerBIError`| N/D | N/D | N/D | Obtém informações detalhadas sobre os erros de ativações de cmdlets sem erro. |
