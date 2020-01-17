---
title: Configurar credenciais para o Power BI através de programação
description: Como configurar credenciais para automatização do Power BI através de programação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836602"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurar credenciais para o Power BI através de programação

Siga estes passos para configurar credenciais para o Power BI através de programação.

## <a name="configure-a-credential-flow-for-data-sources"></a>Configurar um fluxo de credenciais para origens de dados

1. Chame a API [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) para descobrir as origens de dados do conjunto de dados. No corpo da resposta de cada origem de dados estará o tipo, os detalhes da ligação, o gateway e o ID da origem de dados.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Crie a cadeia de credenciais de acordo com a secção [Update Datasource Examples](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Exemplos de Update Datasource), consoante o tipo de credenciais.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Crie os detalhes das credenciais.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Chame a API [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) para definir as credenciais ao utilizar o gateway e o ID da origem de dados do passo 1 e os detalhes das credenciais do passo 4.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Fluxo de credenciais da origem de dados no local expirado

1. [Siga os passos 1 e 2 do cenário anterior](#configure-a-credential-flow-for-data-sources).

2. Chame a API [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) para obter a chave pública do gateway.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Encripte a cadeia de credenciais com a chave pública do Gateway. As versões diferentes do gateway podem ter diferentes tamanhos de chave pública.
    
    Veja o exemplo no código do SDK, disponível no repositório do GitHub PowerBI-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. Crie os detalhes das credenciais com credenciais encriptadas.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Chame a API [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) para definir credenciais.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurar uma nova origem de dados para um gateway de dados

1. Instale o [Gateway de dados no local](https://powerbi.microsoft.com/gateway/) no seu computador.

2. Chame a API [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) para obter a chave pública e o ID do gateway.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Crie os detalhes das credenciais, como no cenário anterior, através da chave pública do gateway obtida no passo [Fluxo de credenciais da origem de dados no local expirado](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway).

4. Crie o corpo do pedido.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
    dataSourceType: "SQL",
    connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
    credentialDetails: credentialDetails,
    dataSourceName: "my sql datasource");
    ```

5. Chame a API [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="troubleshooting"></a>Resolução de problemas

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Não é encontrado nenhum ID da origem de dados e gateway ao chamar a API Get Datasources

Este problema significa que o conjunto de dados não está vinculado a um gateway. Ao criar um novo conjunto de dados, é criada automaticamente uma origem de dados sem credenciais no gateway de cloud do utilizador para cada ligação à cloud. Este gateway é utilizado para armazenar as credenciais para ligações à cloud.

Depois de criar o conjunto de dados, é efetuado um enlace automático entre o conjunto de dados e um gateway adequado, que contém origens de dados correspondentes para todas as ligações. Se não existir um ou múltiplos gateways adequados, o enlace automático irá falhar.

Crie as origens de dados no local em falta (se aplicável) e vincule manualmente o conjunto de dados a um gateway através da API [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Para descobrir os gateways que podem ser vinculados, utilize a API [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).