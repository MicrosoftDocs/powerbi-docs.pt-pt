---
title: Propriedades do conjunto de dados do Power BI na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Saiba mais sobre as propriedades das APIs de conjuntos de dados do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b4bd173c2f3730a0a6082214afbfdf5760048102
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887690"
---
# <a name="dataset-properties"></a>Dataset properties (Propriedades do conjunto de dados)

A versão 1 atual da API de conjuntos de dados só permite a criação de um conjunto de dados com um nome e uma coleção de tabelas. Cada tabela pode ter um nome e uma coleção de colunas. Cada coluna tem um nome e um tipo de dados. Estamos a expandir estas propriedades principalmente com suporte para medidas e relações entre tabelas. Segue-se a lista completa de propriedades suportadas para esta versão:

> [!IMPORTANT]
> É possível aceder à lista na página [Datasets Operation Groups](/rest/api/power-bi/datasets) (Grupos de Operações de Conjuntos de Dados).

## <a name="dataset"></a>Conjunto de dados

Nome  |Tipo  |Descrição  |Só de Leitura  |Necessário
---------|---------|---------|---------|---------
ID     |  GUID       | Identificador exclusivo ao nível do sistema para o conjunto de dados.        | Verdadeiro        | Falso        
name     | String        | Nome do conjunto de dados definido pelo utilizador.        | Falso        | Verdadeiro        
Tabelas     | Tabela[]        | Coleção de tabelas.        |  Falso       | Falso        
relationships     | Relação[]        | Coleção de relações entre tabelas.        | Falso        |  Falso  
defaultMode     | String        | Determina se o conjunto de dados foi emitido, transmitido ou ambos com os valores "Push" e "Streaming".         | Falso        |  Falso

## <a name="table"></a>Tabela

Nome  |Tipo  |Descrição  |Só de Leitura  |Necessário
---------|---------|---------|---------|---------
name     | String        |  Nome definido pelo utilizador da tabela. Também é utilizado como o identificador da tabela.       | Falso        |  Verdadeiro       
colunas     |  coluna[]       |  Coleção de colunas.       | Falso        |  Verdadeiro       
measures     | medida[]        |  Coleção de medidas.       | Falso        |  Falso       
isHidden     | Booleano        | Se for verdadeiro, a tabela será ocultada das ferramentas de cliente.        | Falso        | Falso        

## <a name="column"></a>Coluna

Nome  |Tipo  |Descrição  |Só de Leitura  |Necessário
---------|---------|---------|---------|---------
name     |  String        | Nome definido pelo utilizador da coluna.        |  Falso       | Verdadeiro       
dataType     |  String       |  [Tipos de dados EDM](/dotnet/framework/data/adonet/entity-data-model-primitive-data-types) suportados e restrições. Veja [Data type restrictions](#data-type-restrictions) (Restrições de tipos de dados).      |  Falso       | Verdadeiro        
formatString     | String        | Uma cadeia que descreve como o valor deveria ser formatado ao ser apresentado. Para saber mais sobre a formatação de cadeias, veja [FORMAT_STRING Contents](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents) (Conteúdos FORMAT_STRING).      | Falso        | Falso        
sortByColumn    | String        |   Nome de cadeia de uma coluna na mesma tabela a utilizar para ordenar a coluna atual.     | Falso        | Falso       
dataCategory     | String        |  Valor de cadeia a utilizar para a categoria de dados que descreve os dados nesta coluna. Alguns valores comuns incluem: Endereço, Cidade, Continente, País, Imagem, URL da Imagem, Latitude, Longitude, Organização, Lugar, Código Postal, Distrito, URL da Web       |  Falso       | Falso        
isHidden    |  Booleano       |  Propriedade que indica se a coluna foi ocultada da vista. A predefinição é falso.       | Falso        | Falso        
summarizeBy     | String        |  Método de agregação predefinido da coluna. Os valores incluem: predefinição, nenhum, soma, mín., máx., contagem, média, Contagem Distinta     |  Falso       | Falso

## <a name="measure"></a>Medida

Nome  |Tipo  |Descrição  |Só de Leitura  |Necessário
---------|---------|---------|---------|---------
name     | String        |  Nome definido pelo utilizador da medida.       |  Falso       | Verdadeiro        
expression     | String        | Uma expressão DAX válida.        | Falso        |  Verdadeiro       
formatString     | String        |  Uma cadeia que descreve como o valor deveria ser formatado ao ser apresentado. Para saber mais sobre a formatação de cadeias, veja [FORMAT_STRING Contents](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents) (Conteúdos FORMAT_STRING).       | Falso        | Falso        
isHidden     | String        |  Se for verdadeiro, a tabela será ocultada das ferramentas de cliente.       |  Falso       | Falso       

## <a name="relationship"></a>Relação

Nome  |Tipo  |Descrição  |Só de Leitura  |Necessário 
---------|---------|---------|---------|---------
name     | String        | Nome definido pelo utilizador da relação. Também é utilizado como o identificador da relação.        | Falso       | Verdadeiro        
crossFilteringBehavior     | String        |    A direção de filtro da relação: OneDirection (predefinição), BothDirections, Automatic       | Falso        | Falso        
fromTable     | String        | Nome da tabela de chave externa.        | Falso        | Verdadeiro         
fromColumn    | String        | Nome da coluna de chave externa.        | Falso        | Verdadeiro         
toTable    | String        | Nome da tabela de chave primária.        | Falso        | Verdadeiro         
toColumn     | String        | Nome da coluna de chave primária.        | Falso        | Verdadeiro        

## <a name="data-type-restrictions"></a>Restrições de tipos de dados

Estas restrições aplicam-se à propriedade dataType.

Tipo de dados  |Restrições  
---------|---------
Int64     |   Int64.MaxValue e Int64.MinValue não permitidos.      
Double (Duplo)     |  Valores de Double.MaxValue e Double.MinValue não permitidos. NaN não suportado. +Infinity e -Infinity não suportados em algumas funções (por exemplo, Min e Max).       
Booleano     |   Verdadeiro ou Falso.
Datetime    |   Durante o carregamento de dados, podemos quantificar os valores com frações de dias para múltiplos inteiros de 1/300 de segundo (3,33 ms).      
String     |  Atualmente, permite até 4000 carateres por cada valor de cadeia.
Decimal|precision=28, scale=4

## <a name="example"></a>Exemplo
O seguinte exemplo de código inclui várias destas propriedades:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```