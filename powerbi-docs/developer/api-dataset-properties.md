---
title: Propriedades do conjunto de dados do Power BI
description: Saiba mais sobre as propriedades das APIs de conjuntos de dados do Power BI
author: markingmyname
manager: kfile
ms.author: maghan
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 4654534d9643b9c5cf5911249a0eda33b5cc32af
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277905"
---
# <a name="dataset-properties"></a>Dataset properties (Propriedades do conjunto de dados)

A versão 1 atual da API de conjuntos de dados só permite a criação de um conjunto de dados com um nome e uma coleção de tabelas. Cada tabela pode ter um nome e uma coleção de colunas. Cada coluna tem um nome e um tipo de dados. Estamos a expandir estas propriedades principalmente com suporte para medidas e relações entre tabelas. Segue-se a lista completa de propriedades suportadas para esta versão:

> [!IMPORTANT]
> É possível aceder à lista na página [Datasets Operation Groups](https://docs.microsoft.com/rest/api/power-bi/datasets) (Grupos de Operações de Conjuntos de Dados).

## <a name="dataset"></a>Conjunto de dados

Nome  |Tipo  |Descrição  |Só de Leitura  |Obrigatório
---------|---------|---------|---------|---------
ID     |  GUID       | Identificador exclusivo ao nível do sistema para o conjunto de dados.        | Verdadeiro        | Falso        
nome     | Cadeia        | Nome do conjunto de dados definido pelo utilizador.        | Falso        | Verdadeiro        
tables     | Tabela[]        | Coleção de tabelas.        |  Falso       | Falso        
relationships     | Relação[]        | Coleção de relações entre tabelas.        | Falso        |  Falso  
defaultMode     | Cadeia        | Determina se o conjunto de dados foi emitido, transmitido ou ambos com os valores "Push", "Streaming" e "PushStreaming".         | Falso        |  Falso

## <a name="table"></a>Table

Nome  |Tipo  |Descrição  |Só de Leitura  |Obrigatório
---------|---------|---------|---------|---------
nome     | Cadeia        |  Nome definido pelo utilizador da tabela. Também é utilizado como o identificador da tabela.       | Falso        |  Verdadeiro       
colunas     |  coluna[]       |  Coleção de colunas.       | Falso        |  Verdadeiro       
measures     | medida[]        |  Coleção de medidas.       | Falso        |  Falso       
isHidden     | Booleano        | Se for verdadeiro, a tabela será ocultada das ferramentas de cliente.        | Falso        | Falso        

## <a name="column"></a>Estruturada

Nome  |Tipo  |Descrição  |Só de Leitura  |Obrigatório
---------|---------|---------|---------|---------
nome     |  Cadeia        | Nome definido pelo utilizador da coluna.        |  Falso       | Verdadeiro       
dataType     |  Cadeia       |  [Tipos de dados EDM](https://msdn.microsoft.com/library/ee382832.aspx) suportados e restrições. Veja [Data type restrictions](#DataTypeRestrictions) (Restrições de tipos de dados).      |  Falso       | Verdadeiro        
formatString     | Cadeia        | Uma cadeia que descreve como o valor deveria ser formatado ao ser apresentado. Para saber mais sobre a formatação de cadeias, veja [FORMAT_STRING Contents](https://msdn.microsoft.com/library/ms146084.aspx) (Conteúdos FORMAT_STRING).      | Falso        | Falso        
sortByColumn    | Cadeia        |   Nome de cadeia de uma coluna na mesma tabela a utilizar para ordenar a coluna atual.     | Falso        | Falso       
dataCategory     | Cadeia        |  Valor de cadeia a utilizar para a categoria de dados que descreve os dados nesta coluna. Alguns valores comuns incluem: Endereço, Cidade, Continente, País, Imagem, URL da Imagem, Latitude, Longitude, Organização, Lugar, Código Postal, Distrito, URL da Web       |  Falso       | Falso        
isHidden    |  Booleano       |  Propriedade que indica se a coluna foi ocultada da vista. A predefinição é falso.       | Falso        | Falso        
summarizeBy     | Cadeia        |  Método de agregação predefinido da coluna. Os valores incluem: predefinição, nenhum, soma, mín., máx., contagem, média, Contagem Distinta     |  Falso       | Falso

## <a name="measure"></a>Medida

Nome  |Tipo  |Descrição  |Só de Leitura  |Obrigatório
---------|---------|---------|---------|---------
nome     | Cadeia        |  Nome definido pelo utilizador da medida.       |  Falso       | Verdadeiro        
expression     | Cadeia        | Uma expressão DAX válida.        | Falso        |  Verdadeiro       
formatString     | Cadeia        |  Uma cadeia que descreve como o valor deveria ser formatado ao ser apresentado. Para saber mais sobre a formatação de cadeias, veja [FORMAT_STRING Contents](https://msdn.microsoft.com/library/ms146084.aspx) (Conteúdos FORMAT_STRING).       | Falso        | Falso        
isHidden     | Cadeia        |  Se for verdadeiro, a tabela será ocultada das ferramentas de cliente.       |  Falso       | Falso       

## <a name="relationship"></a>Relação

Nome  |Tipo  |Descrição  |Só de Leitura  |Obrigatório 
---------|---------|---------|---------|---------
nome     | Cadeia        | Nome definido pelo utilizador da relação. Também é utilizado como o identificador da relação.        | Falso       | Verdadeiro        
crossFilteringBehavior     | Cadeia        |    A direção do filtro da relação: OneDirection (predefinição), BothDirections, Automático       | Falso        | Falso        
fromTable     | Cadeia        | Nome da tabela de chave externa.        | Falso        | Verdadeiro         
fromColumn    | Cadeia        | Nome da coluna de chave externa.        | Falso        | Verdadeiro         
toTable    | Cadeia        | Nome da tabela de chave primária.        | Falso        | Verdadeiro         
toColumn     | Cadeia        | Nome da coluna de chave primária.        | Falso        | Verdadeiro        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Restrições de tipo de dados (aplica-se à propriedade dataType)

Tipo de dados  |Restrições  
---------|---------
Int64     |   Int64.MaxValue e Int64.MinValue não permitidos.      
Double     |  Valores de Double.MaxValue e Double.MinValue não permitidos. NaN não suportado. +Infinity e -Infinity não suportados em algumas funções (por exemplo, Min e Max).       
Booleano     |   Verdadeiro ou Falso.
Datetime    |   Durante o carregamento de dados, podemos quantificar os valores com frações de dias para múltiplos inteiros de 1/300 de segundo (3,33 ms).      
Cadeia     |  Atualmente, permite até 4000 carateres por cada valor de cadeia.
Decimal|precision=28, scale=4

## <a name="example"></a>Exemplo
O seguinte exemplo de código inclui várias destas propriedades:

```
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