---
title: Change data source connection strings with PowerShell (Alterar cadeias de ligação de origem de dados com o PowerShell)
description: Alterar cadeias de ligação da origem de dados ao utilizar APIs no PowerShell – Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: b7f431ba6b8f559380916c17689d0eab74a0c9a7
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044316"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Alterar cadeias de ligação da origem de dados em relatórios do Power BI com o PowerShell – Power BI Report Server


A partir do lançamento de outubro de 2020 do Power BI Report Server, permitimos a possibilidade de atualizar as ligações para relatórios power BI para DirectQuery e refresh.

> [!IMPORTANT]
> Também é uma alteração interruptiva de como fazia a configuração em versões anteriores. Se estiver a utilizar uma versão do Power BI Report Server anterior à de outubro de 2020, veja [Alterar cadeias de ligação de origem de dados em relatórios do Power BI com o PowerShell – Power BI Report Server anterior a outubro de 2020](connect-data-source-apis-pre-oct-2020.md)

## <a name="prerequisites"></a>Pré-requisitos:
- Descarregue o Download do Servidor de Relatório de Power BI de outubro de 2020 [e power BI Desktop para Power BI Report Server](https://powerbi.microsoft.com/report-server/).
- Um relatório guardado com o outubro de 2020 ou posterior lançamento do Power BI Desktop otimizado para o Report Server, com **metadados de DataSet melhorados** ativados.
- Um relatório que utiliza ligações parametrizadas. Apenas os relatórios com ligações e bases de dados parametrizadas podem ser atualizados após a publicação.
- Este exemplo utiliza as ferramentas do Reporting Services do PowerShell. Pode alcançar o mesmo resultado através das novas APIs REST.

## <a name="create-a-report-with-parameterized-connections"></a>Criar um relatório com ligações parametrizadas
    
1. Crie uma ligação do SQL Server a um servidor. No exemplo abaixo, ligamos o localhost a uma base de dados chamada ReportServer e solicitamos dados do ExecutionLog.

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="Ligar à base de dados do SQL Server":::

    Eis o aspeto da consulta M neste momento:

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. Selecione **Gerir Parâmetros** no friso do Editor do Power Query.

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="Selecionar Gerir Parâmetros":::

1.  Crie parâmetros para o servername e o databasename.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="Faça a gestão dos Parâmetros, defina o servername e o databasename.":::


3. Edite a consulta para a primeira ligação e mapeie a base de dados e o servername.

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="Mapear o nome do Servidor e da Base de Dados":::

    Agora, a consulta tem o seguinte aspeto:

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. Publique esse relatório no servidor. Neste exemplo, o relatório é denominado executionlogparameter. A imagem seguinte é um exemplo de uma página de gestão de origens de dados.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="A página de gestão de origens de dados.":::

## <a name="update-parameters-using-the-powershell-tools"></a>Atualizar parâmetros através das ferramentas do PowerShell

1. Abra o PowerShell e instale as ferramentas do Reporting Services mais recentes, ao seguir as instruções em [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools).
    
2.  Para obter o parâmetro para o relatório, utilize a nova API REST DataModelParameters com a seguinte chamada do PowerShell:

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. Guardamos o resultado desta chamada numa variável:

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. Essa variável é atualizada com os valores que precisamos de alterar.
5. Guardamos o resultado desta chamada numa variável:

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. Com os valores atualizados, podemos utilizar o commandlet `Set-RsRestItemDataModelParameters` para atualizar os valores no servidor:

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. Assim que os parâmetros estiverem atualizados, o servidor atualiza todas as origens de dados que estavam dependentes dos parâmetros. Ao voltar à caixa de diálogo **Editar origem de dados**, deverá conseguir definir credenciais para o servidor e a base de dados atualizados.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="Definir as credenciais para o servidor e a base de dados atualizados.":::

## <a name="next-steps"></a>Passos seguintes

[Origens de dados de relatórios paginados no Power BI Report Server](connect-data-sources.md) 

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
