---
title: Change data source connection strings with PowerShell (Alterar cadeias de ligação de origem de dados com o PowerShell)
description: Alterar cadeias de ligação da origem de dados ao utilizar APIs no PowerShell – Power BI Report Server.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 09/01/2020
ms.author: maggies
ms.openlocfilehash: 69aa11216624416f005dcb2e47d1b818204ae7ec
ms.sourcegitcommit: 89ce1777a85b9fc476f077cbe22978c6cf923603
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89286734"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Alterar cadeias de ligação da origem de dados em relatórios do Power BI com o PowerShell – Power BI Report Server


Pode alterar as cadeias de ligação das origens de dados dos relatórios do Power BI alojados no Power BI Report Server ao utilizar o PowerShell para interagir com as APIs necessárias. 

> [!NOTE]
> Atualmente, esta funcionalidade funciona apenas para o DirectQuery. O suporte para a importação e a atualização dos dados estará disponível em breve.

1. Instale os commandlets do PowerShell do Power BI Report Server. Pode encontrar os commandlets e as instruções de instalação em [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

    Instale o módulo `ReportingServicesTools` diretamente da [Galeria do PowerShell](https://www.powershellgallery.com/packages/ReportingServicesTools/) com o comando seguinte.

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. Obtenha as informações da origem de dados existente para o ficheiro do Power BI através dos commandlets do PowerShell:

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Para ver as informações da primeira origem de dados contida no relatório do Power BI: 

    ```powershell
    $dataSources[0]
    ```

3. Atualize as informações de ligação e as credenciais, conforme necessário. Se atualizar a cadeia de ligação e a origem de dados utilizar credenciais armazenadas, terá de fornecer a palavra-passe da conta. 

    Para atualizar uma cadeia de ligação da origem de dados:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Para alterar o tipo de credencial da origem de dados:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    Para alterar o nome de utilizador/palavra-passe da origem de dados:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Guarde as credenciais atualizadas novamente no servidor.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Passos seguintes

[Origens de dados de relatórios paginados no Power BI Report Server](connect-data-sources.md) 

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
