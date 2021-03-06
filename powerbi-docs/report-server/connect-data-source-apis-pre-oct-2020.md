---
title: Alterar cadeias de ligação da origem de dados com o PowerShell – Power BI Report Server anterior a outubro de 2020
description: Alterar cadeias de ligação da origem de dados ao utilizar APIs no PowerShell – Power BI Report Server anterior a outubro de 2020.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: f0dd30e721d8325fdbfd8b562083fbedef2af9c0
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044201"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server-pre-october-2020"></a>Alterar cadeias de ligação da origem de dados em relatórios do Power BI com o PowerShell – Power BI Report Server anterior a outubro de 2020


Pode alterar as cadeias de ligação das origens de dados dos relatórios do Power BI alojados no Power BI Report Server ao utilizar o PowerShell para interagir com as APIs necessárias. 

> [!IMPORTANT]
> Se estiver a utilizar a versão mais recente do Power BI Report Server, consulte as cadeias de [ligação de fonte de dados change em relatórios PowerShell - Power BI Report Server](connect-data-source-apis.md).

> [!NOTE]
> Atualmente, esta funcionalidade funciona apenas para o DirectQuery. O suporte para a importação e a atualização dos dados estará disponível em breve.

1. Instale os commandlets do PowerShell do Power BI Report Server. Pode encontrar os commandlets e as instruções de instalação em [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

    Instale o módulo `ReportingServicesTools` diretamente da [Galeria do PowerShell](https://www.powershellgallery.com/packages/ReportingServicesTools/) com o comando seguinte.

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. Obtenha as informações da origem de dados existente para o ficheiro do Power BI através dos commandlets do PowerShell:

    ```powershell
    $dataSources = Get-RsRestItemDataSource -RsItem '/MyPbixReport'
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
