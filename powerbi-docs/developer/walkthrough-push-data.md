---
title: Enviar dados por push para um conjunto de dados
description: Enviar dados por push para um conjunto de dados do Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 01/05/2017
ms.openlocfilehash: 01bcc545d3ba8edb23ef583467322401780e657d
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45974190"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Enviar dados por push para um conjunto de dados do Power BI

Com a API Power BI, pode enviar dados por push para um conjunto de dados do Power BI. Por exemplo, pretende estender um fluxo de trabalho de negócios existente para enviar dados de chave por push para o conjunto de dados. Neste caso, pretende enviar por push um conjunto de dados de Marketing de vendas que tem uma Tabela de produto para um conjunto de dados.

Antes de começar a enviar dados por push para um conjunto de dados, necessita um Azure Active Directory (Azure AD) e uma [conta do Power BI](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Passos para o envio dados por push para um conjunto de dados

* Passo 1: [registar uma aplicação com o Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Passo 2: [obter um token de acesso de autenticação](walkthrough-push-data-get-token.md)
* Passo 3: [criar um conjunto de dados no Power BI](walkthrough-push-data-create-dataset.md)
* Passo 4: [obter um conjunto de dados para adicionar linhas a uma tabela do Power BI](walkthrough-push-data-get-datasets.md)
* Passo 5: [adicionar linhas a uma tabela do Power BI](walkthrough-push-data-add-rows.md)

A secção seguinte é uma discussão geral sobre as operações da API Power BI que enviam dados por push.

## <a name="power-bi-api-operations-to-push-data"></a>Operações da API Power BI para enviar dados por push

Com a API REST do Power BI, pode enviar por push origens de dados ao Power BI. Quando uma aplicação adiciona linhas a um conjunto de dados, os mosaicos no dashboard são atualizados automaticamente com os dados atualizados. Para enviar dados por push, deve usar a operação [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) juntamente com a operação [Publicar Linhas](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows). Para encontrar um conjunto de dados, use a operação [Obter Conjuntos de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets). Para qualquer uma destas operações, pode transmitir um ID de grupo para trabalhar com um grupo. Use a operação [Obter Grupos](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) para obter uma lista de IDs de grupo.

Estas são as operações para enviar dados por push a um conjunto de dados:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Obter Conjuntos de Dados](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [Publicar Linhas](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Obter Grupos](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Pode criar um conjunto de dados no Power BI ao transmitir uma cadeia JSON (JavaScript Object Notation) ao serviço Power BI. Para saber mais sobre JSON, veja [Introdução ao JSON](http://json.org/).

A cadeia JSON para um conjunto de dados tem o seguinte formato:

**Objeto JSON do Conjunto de Dados do Power BI**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Assim, no nosso exemplo de conjunto de dados de Marketing de Vendas, transmite uma cadeia JSON como o exemplo abaixo. Neste exemplo, **SalesMarketing** é o nome do conjunto de dados, e **Product** é o nome da tabela. Depois de definir a tabela, pode definir o esquema da tabela. Para o conjunto de dados **SalesMarketing**, o esquema da tabela tem as seguintes colunas: ProductID, Manufacturer, Category, Segment, Product e IsCompete.

**JSON de objeto de conjunto de dados de exemplo**

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

Para um esquema de tabela do Power BI, pode utilizar os seguintes tipos de dados.

## <a name="power-bi-table-data-types"></a>Tipos de dados de tabela do Power BI

| **Tipo de dados** | **Restrições** |
| --- | --- |
| Int64 |Int64.MaxValue e Int64.MinValue não permitidos. |
| Double |Valores de Double.MaxValue e Double.MinValue não permitidos. NaN não suportado. +Infinity e -Infinity não suportados em algumas funções (por exemplo, Min e Max). |
| Boolean |Nenhum |
| Datetime |Durante o carregamento de dados, podemos quantificar os valores com frações de dias para múltiplos inteiros de 1/300 de segundo (3,33 ms). |
| Cadeia |Atualmente, permite até 128 mil carateres. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Saiba mais sobre como enviar dados por push ao Power BI

Para começar a enviar dados por push para um conjunto de dados, Veja [Passo 1: registar uma aplicação com o Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) no painel de navegação à esquerda.

[Próximo Passo >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Próximos passos

[Inscreva-se no Power BI](create-an-azure-active-directory-tenant.md)  
[Introdução ao JSON](http://json.org/)  
[Visão geral da API REST do Power BI](overview-of-power-bi-rest-api.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)