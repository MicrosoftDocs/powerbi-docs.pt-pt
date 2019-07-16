---
title: Obter um conjunto de dados para adicionar linhas
description: Passo a passo para enviar dados por push - Obter um conjunto de dados para adicionar linhas a uma tabela do Power BI
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: f7dc84c9c6c84a30417d97f37d984b5f01ec9cd7
ms.sourcegitcommit: 3e72c6d564d930304886d51cdf12b8fc166aa33c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/05/2019
ms.locfileid: "67596457"
---
# <a name="step-4-get-a-dataset-to-add-rows-into-a-power-bi-table"></a>Passo 4: Obter um conjunto de dados para adicionar linhas numa tabela do Power BI

Este artigo faz parte das instruções passo-a-passo para [Enviar dados por push para um conjunto de dados](walkthrough-push-data.md).

No **passo 3** de Enviar dados por push para um conjunto de dados, [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md), invocou a operação [Criar Conjunto de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets) para criar um conjunto de dados no Power BI. Neste passo, irá utilizar a operação [Obter Conjuntos de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets) e Newtonsoft.Json para obter um ID do conjunto de dados. Pode utilizar o ID do conjunto de dados no passo 4 para adicionar linhas a um conjunto de dados. 

Para enviar dados por push para um conjunto de dados do Power BI, tem de referenciar a tabela no conjunto de dados. Para referenciar uma tabela num conjunto de dados, é necessário primeiro obter o **ID do Conjunto de Dados**. O **ID do Conjunto de Dados** é obtido com a operação [Obter Conjuntos de Dados](/rest/api/power-bi/datasets/getdatasets). A operação **Obter Conjuntos de Dados** devolve uma cadeia de carateres JSON que contém uma lista de todos os conjuntos de dados no Power BI. A forma recomendada para anular a serialização de uma cadeia de carateres JSON é com [Newtonsoft.Json](http://www.newtonsoft.com/json).

Eis como obter um conjunto de dados.

## <a name="get-a-power-bi-dataset"></a>Obter um conjunto de dados do Power BI

> **NOTA**: Antes de começar, certifique-se de que seguiu os passos anteriores nas instruções para [enviar dados para um conjunto de dados](walkthrough-push-data.md).

1. No projeto Aplicação de Consola que criou no Passo 2: Instruções para enviar dados por push, [Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md), instale o pacote NuGet Newtonsoft.Json. Veja como instalar o pacote:

     a. No Visual Studio 2015, escolha **Ferramentas** > **Gestor de Pacotes NuGet** > **Consola do Gestor de Pacotes**.

     b. Na **Consola do Gestor de Pacotes**, introduza Install-Package Newtonsoft.Json.
2. Depois de instalar o pacote, adicione **using Newtonsoft.Json;** a Program.cs.
3. Em Program.cs, adicione o código abaixo para obter o **ID do Conjunto de Dados**.
4. Execute a Aplicação de Consola e inicie sessão na conta do Power BI. Deverá ver **ID do Conjunto de Dados:** seguido de um ID na Janela da Consola.

**Exemplo de obtenção de um conjunto de dados**

Adicione este código a Program.cs.

* Em static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
  
    //Get an authentication access token
    token = GetToken();
  
    //Create a dataset in Power BI
    CreateDataset();
  
    //Get a dataset to add rows into a Power BI table
    string datasetId = GetDataset();
  }
  ```
* Adicione um método GetDatset():
  
  ```csharp
    #region Get a dataset to add rows into a Power BI table
    private static string GetDataset()
    {
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "GET";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        string datasetId = string.Empty;
        //Get HttpWebResponse from GET request
        using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
        {
            //Get StreamReader that holds the response stream
            using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
            {
                string responseContent = reader.ReadToEnd();
  
                //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                //and add using Newtonsoft.Json
                var results = JsonConvert.DeserializeObject<dynamic>(responseContent);
  
                //Get the first id
                datasetId = results["value"][0]["id"];
  
                Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                Console.ReadLine();
  
                return datasetId;
            }
        }
    }
    #endregion
  ```

O passo seguinte mostra como [adicionar linhas a uma tabela do Power BI](walkthrough-push-data-add-rows.md).

Segue-se a [lista completa de códigos](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Lista completa de códigos

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;
using Newtonsoft.Json;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

            //Create a dataset in Power BI
            CreateDataset();

            //Get a dataset to add rows into a Power BI table
            string datasetId = GetDataset();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

        #region Create a dataset in Power BI
        private static void CreateDataset()
        {
            //TODO: Add using System.Net and using System.IO

            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "POST";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            //Create dataset JSON for POST request
            string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                "[{\"name\": \"Product\", \"columns\": " +
                "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                "]}]}";

            //POST web request
            byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
            request.ContentLength = byteArray.Length;

            //Write JSON byte[] into a Stream
            using (Stream writer = request.GetRequestStream())
            {
                writer.Write(byteArray, 0, byteArray.Length);

                var response = (HttpWebResponse)request.GetResponse();

                Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                Console.ReadLine();
            }
        }
        #endregion

        #region Get a dataset to add rows into a Power BI table
        private static string GetDataset()
        {
            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "GET";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            string datasetId = string.Empty;
            //Get HttpWebResponse from GET request
            using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
            {
                //Get StreamReader that holds the response stream
                using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
                {
                    string responseContent = reader.ReadToEnd();

                    //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                    //and add using Newtonsoft.Json
                    var results = JsonConvert.DeserializeObject<dynamic>(responseContent);

                    //Get the first id
                    datasetId = results["value"][0]["id"];

                    Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                    Console.ReadLine();

                    return datasetId;
                }
            }
        }
        #endregion
    }
}
```

[Próximo Passo >](walkthrough-push-data-add-rows.md)

## <a name="next-steps"></a>Passos seguintes

[Adicionar linhas a uma tabela do Power BI](walkthrough-push-data-add-rows.md)  
[Newtonsoft.Json](http://www.newtonsoft.com/json)  
[Obter Conjuntos de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)  
[Enviar dados por push para o Power BI](walkthrough-push-data.md)  
[Descrição Geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
[Referência da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)