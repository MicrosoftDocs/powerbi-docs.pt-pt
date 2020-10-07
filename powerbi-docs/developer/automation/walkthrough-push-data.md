---
title: Enviar dados por push para um conjunto de dados
description: Enviar dados por push para um conjunto de dados do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 792afe42cf302ae552b7f8f1c14d5f232ade320f
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746706"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Enviar dados por push para um conjunto de dados do Power BI

A API Power BI permite enviar dados por push para um conjunto de dados do Power BI. Neste artigo, mostraremos como enviar por push um conjunto de dados de Marketing de Vendas que tem uma Tabela de produto para um conjunto de dados existente.

Antes de começar, necessita de um Azure Active Directory (Azure AD) e uma [conta do Power BI](../embedded/create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Passos para o envio dados por push para um conjunto de dados

* Passo 1: [Registar uma aplicação no Azure AD](../embedded/register-app.md)
* Passo 2: [Obter um token de acesso de autenticação](walkthrough-push-data-get-token.md)
* Passo 3: [Criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)
* Step 4: [Obter um conjunto de dados para adicionar linhas numa tabela do Power BI](walkthrough-push-data-get-datasets.md)
* Step 5: [Adicionar linhas a uma tabela do Power BI](walkthrough-push-data-add-rows.md)

A secção seguinte é uma discussão geral sobre as operações da API Power BI que enviam dados por push.

## <a name="power-bi-api-operations-to-push-data"></a>Operações da API Power BI para enviar dados por push

Com a API REST do Power BI, pode enviar por push origens de dados ao Power BI. Quando uma aplicação adiciona linhas a um conjunto de dados, os mosaicos do dashboard são atualizados automaticamente com os novos dados. Para enviar dados por push, utilize as operações [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset) e [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows). Para encontrar um conjunto de dados, utilize a operação [Obter Conjuntos de Dados](/rest/api/power-bi/datasets/getdatasets). Para qualquer uma destas operações, pode transmitir um ID de grupo para trabalhar com um grupo. Para obter uma lista de IDs de grupo, utilize a operação [Obter Grupos](/rest/api/power-bi/groups/getgroups).

Estas são as operações para enviar dados por push a um conjunto de dados:

* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Obter Conjuntos de Dados](/rest/api/power-bi/datasets/getdatasets)
* [Publicar Linhas](/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Obter Grupos](/rest/api/power-bi/groups/getgroups)

Pode criar um conjunto de dados no Power BI ao transmitir uma cadeia JSON (JavaScript Object Notation) ao serviço Power BI. Para saber mais sobre JSON, veja [Introdução ao JSON](https://json.org/).

A cadeia JSON para um conjunto de dados tem o seguinte formato:

**Objeto JSON do Conjunto de Dados do Power BI**

```json
{"name": "dataset_name", "tables":
    [{"name": "", "columns":
        [{ "name": "column_name1", "dataType": "data_type"},
         { "name": "column_name2", "dataType": "data_type"},
         { ... }
        ]
      }
    ]
}
```

No nosso exemplo de conjunto de dados de Marketing de Vendas, transmite uma cadeia JSON conforme apresentado abaixo. Neste exemplo, **SalesMarketing** é o nome do conjunto de dados e **Product** é o nome da tabela. Depois de definir a tabela, pode definir o esquema da tabela. Para o conjunto de dados **SalesMarketing**, o esquema da tabela tem as seguintes colunas: ProductID, Manufacturer, Category, Segment, Product e IsCompete.

**JSON de objeto de conjunto de dados de exemplo**

```json
{
    "name": "SalesMarketing",
    "tables": [
        {
            "name": "Product",
            "columns": [
            {
                "name": "ProductID",
                "dataType": "int"
            },
            {
                "name": "Manufacturer",
                "dataType": "string"
            },
            {
                "name": "Category",
                "dataType": "string"
            },
            {
                "name": "Segment",
                "dataType": "string"
            },
            {
                "name": "Product",
                "dataType": "string"
            },
            {
                "name": "IsCompete",
                "dataType": "bool"
            }
            ]
        }
    ]
}
```

Para um esquema de tabela do Power BI, pode utilizar os seguintes tipos de dados.

## <a name="power-bi-table-data-types"></a>Tipos de dados de tabela do Power BI

| **Tipo de dados** | **Restrições** |
| --- | --- |
| Int64 |Int64.MaxValue e Int64.MinValue não permitidos. |
| Double |Valores de Double.MaxValue e Double.MinValue não permitidos. NaN não suportado. +Infinity e -Infinity não suportados em algumas funções (por exemplo, Min e Max). |
| Booleano |Nenhum |
| Datetime |Durante o carregamento de dados, podemos quantificar os valores com frações de dias para múltiplos inteiros de 1/300 de segundo (3,33 ms). |
| Cadeia |Atualmente, permite até 128 mil carateres. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Saiba mais sobre como enviar dados por push ao Power BI

Para começar a enviar dados por push para um conjunto de dados, veja [Passo 1: registar uma aplicação no Azure AD](../embedded/register-app.md) no painel de navegação.

## <a name="next-steps"></a>Próximos passos

* [Inscreva-se no Power BI](../embedded/create-an-azure-active-directory-tenant.md)  
* [Introdução ao JSON](https://json.org/)  
* [Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)