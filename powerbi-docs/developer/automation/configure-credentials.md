---
title: Configurar credenciais para o Power BI através de programação
description: Como configurar credenciais ao automatizar o Power BI através de programação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/23/2020
ms.openlocfilehash: df5e82af012f4d85fd81399d6e31fde3b7539ce6
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95513832"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurar credenciais para o Power BI através de programação

Siga os passos neste artigo para configurar as credenciais do Power BI através de programação.

>[!NOTE]
>* O utilizador chamador tem de ser um proprietário do conjunto de dados ou um administrador do gateway. Também pode utilizar um [principal de serviço](../embedded/embed-service-principal.md). Por exemplo, o principal de serviço pode ser o proprietário do conjunto de dados.
>* As origens de dados da cloud e as credenciais correspondentes são geridas ao nível do utilizador.

## <a name="update-credentials-flow-for-data-sources"></a>Atualizar o fluxo de credenciais das origens de dados

1. Chame a API [Get Datasources](/rest/api/power-bi/datasets/getdatasourcesingroup) para descobrir as origens de dados do conjunto de dados. No corpo da resposta de cada origem de dados está o tipo, os detalhes da ligação, o gateway e o ID da origem de dados.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Crie a cadeia de credenciais de acordo com a secção [Update Datasource Examples](/rest/api/power-bi/gateways/updatedatasource) (Exemplos de Update Datasource), consoante o tipo de credenciais.

    # <a name="net-sdk-v3"></a>[SDK .NET v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[SDK .NET v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

    >[!NOTE]
    >Se estiver a utilizar origens de dados na cloud, não siga os próximos passos desta secção. Configure as credenciais através do ID do gateway e do ID de origem de dados, obtidos no passo 1, ao chamar [Atualizar a Origem de Dados](/rest/api/power-bi/gateways/updatedatasource). 

3. Chame a API [Get Gateway](/rest/api/power-bi/gateways/getgateways) para obter a chave pública do gateway.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

4. Encripte as credenciais.

    # <a name="net-sdk-v3"></a>[SDK .NET v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[SDK .NET v2](#tab/sdk2)

    Encripte a cadeia de credenciais com a chave pública do Gateway do passo 2. As versões diferentes do gateway podem ter diferentes tamanhos de chave pública. Veja os seguintes exemplos no código do SDK, disponíveis no [repositório do GitHub PowerBI-CSharp](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

5. Crie os detalhes das credenciais com credenciais encriptadas.

    # <a name="net-sdk-v3"></a>[SDK .NET v3](#tab/sdk3)

    Utilize a classe AssymetricKeyEncriptor com a chave pública obtida no **Passo 3**.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[SDK .NET v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

6. Chame a API [Update Datasource](/rest/api/power-bi/gateways/updatedatasource) para definir credenciais.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurar uma nova origem de dados para um gateway de dados

1. Instale o [Gateway de dados no local](https://powerbi.microsoft.com/gateway/) no seu computador.

2. Chame a API [Get Gateways](/rest/api/power-bi/gateways/getgateways) para obter a chave pública e o ID do gateway.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Crie os detalhes das credenciais da forma descrita na secção [Atualizar o fluxo de credenciais das origens de dados](#update-credentials-flow-for-data-sources), através da chave pública do gateway obtida no **passo 2**.

4. Crie o corpo do pedido.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. Chame a API [Create Datasource](/rest/api/power-bi/gateways/createdatasource).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>Tipos de credenciais

Quando chama [Criar Origem de Dados](/rest/api/power-bi/gateways/createdatasource) ou [Atualizar Origens de Dados](/rest/api/power-bi/gateways/updatedatasource) num **gateway empresarial no local** através da [API REST Power BI](/rest/api/power-bi/), o valor das credenciais tem de estar encriptado com a chave pública do gateway.

>[!NOTE]
>O SDK .NET v3 também pode executar os exemplos do SDK .NET v2 listados abaixo.

### <a name="windows-and-basic-credentials"></a>Credenciais básicas e do Windows

# <a name="net-sdk-v3"></a>[SDK .NET v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Credenciais de chave

# <a name="net-sdk-v3"></a>[SDK .NET v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**Credenciais do OAuth2**

# <a name="net-sdk-v3"></a>[SDK .NET v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Credenciais anónimas**

# <a name="net-sdk-v3"></a>[SDK .NET v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[SDK .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Resolução de problemas

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Não é encontrado nenhum ID da origem de dados e gateway ao chamar a API Get Datasources

Este problema significa que o conjunto de dados não está vinculado a um gateway. Ao criar um novo conjunto de dados, é criada automaticamente uma origem de dados sem credenciais no gateway de cloud do utilizador para cada ligação à cloud. Este gateway é utilizado para armazenar as credenciais para ligações à cloud.

Depois de criar o conjunto de dados, é criado um enlace automático entre o conjunto de dados e um gateway adequado, que contém origens de dados correspondentes para todas as ligações. Se não existir um ou múltiplos gateways adequados, o enlace automático irá falhar.

Se estiver a utilizar conjuntos de dados no local, crie as origens de dados no local em falta e vincule manualmente o conjunto de dados a um gateway através da API [Bind To Gateway](/rest/api/power-bi/datasets/bindtogateway).

Para descobrir os gateways que podem ser vinculados, utilize a API [Discover Gateways](/rest/api/power-bi/datasets/discovergateways).