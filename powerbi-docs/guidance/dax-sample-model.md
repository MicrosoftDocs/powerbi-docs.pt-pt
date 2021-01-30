---
title: Modelo de exemplo DAX
description: Modelo de exemplo DAX para suportar artigos de referência.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/25/2020
ms.openlocfilehash: f9fabfe8ccb4350a8d00a7d140618d742dd8c1e4
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088448"
---
# <a name="dax-sample-model"></a>Modelo de exemplo DAX

O modelo de exemplo do Power BI Desktop **Exemplo de Armazém da Adventure Works 2020** foi concebido para suportar a aprendizagem DAX. O modelo baseia-se no [exemplo de armazém de dados da Adventure Works](/sql/samples/adventureworks-install-configure#data-warehouse-downloads) para AdventureWorksDW2017 – no entanto, os dados foram modificados de acordo com os objetivos do modelo de exemplo.

## <a name="scenario"></a>Scenario

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Imagem do logótipo da empresa Adventure Works apresentado.":::

A empresa Adventure Works representa um fabricante de bicicletas que vende bicicletas e acessórios para mercados globais. A empresa tem os dados do armazém de dados armazenados numa Base de Dados SQL do Azure.

## <a name="model-structure"></a>Estrutura do modelo

O modelo tem sete tabelas:

|Tabela|Descrição|
|-----|-------|
|**Cliente**|Descreve os clientes e a localização geográfica. Os clientes compram produtos online (vendas na Internet).|
|**Data**|Existem três relações entre as tabelas **Data** e **Vendas**, para data de encomenda, data de envio e data de vencimento. A relação da data da encomenda está ativa. Os relatórios de vendas da empresa com um ano fiscal que começa a 1 de julho de cada ano. A tabela está marcada como uma tabela de data com a coluna **Data**.|
|**Produto**|Armazena apenas produtos acabados.|
|**Revendedor**|Descreve os revendedores e a localização geográfica. Revendedor de produtos vendidos aos clientes.|
|**Vendas**|Armazena linhas na agregação de linhas da nota de venda. Todos os valores financeiros estão em dólares americanos (USD). A data de encomenda mais antiga é 1 de julho de 2017 e a data de encomenda mais recente é 15 de junho de 2020.|
|**Nota de Venda**|Descreve a nota de venda e os números da nota de venda, bem como o canal de vendas, que é **Revendedor** ou **Internet**. Esta tabela tem uma relação um-para-um com a tabela **Vendas**.|
|**Território de Vendas**|Os territórios de vendas são organizados em grupos (América do Norte, Europa e Pacífico), países e regiões. Apenas os Estados Unidos vendem produtos a nível regional.|

O modelo não contém nenhum cálculo DAX.

## <a name="download-sample"></a>Transferir exemplo

Pode transferir o ficheiro do modelo de exemplo do Power BI Desktop [aqui](https://aka.ms/dax-docs-sample-file).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Referência do DAX (Data Analysis Expressions)](/dax/)
- Percurso de aprendizagem: [Utilizar a DAX no Power BI Desktop](/learn/paths/dax-power-bi/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)