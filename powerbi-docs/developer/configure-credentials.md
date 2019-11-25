---
title: Configurar credenciais para o Power BI através de programação
description: Como configurar credenciais para automatização do Power BI através de programação
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: 73ef45b5dbed8535b13aa557cb52929d4eea0e46
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265594"
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

3. Encripte a cadeia de credenciais com a chave pública do Gateway através do algoritmo de encriptação RSA.

    Utilize a seguinte classe do programa auxiliar para encriptação:

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

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
