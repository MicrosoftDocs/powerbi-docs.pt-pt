---
title: Enlace dinâmico
description: Saiba como incorporar um relatório através do enlace dinâmico.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776243"
---
# <a name="dynamic-binding"></a>Enlace dinâmico

O enlace dinâmico permite selecionar dinamicamente um conjunto de dados ao incorporar um relatório. O relatório e o conjunto de dados não têm de se encontrar na mesma área de trabalho. Os utilizadores finais veem resultados diferentes consoante o conjunto de dados selecionado.

Ambas as áreas de trabalho (a que contém o relatório e a que contém o conjunto de dados) têm de ser atribuídas a uma capacidade.

A incorporação de um relatório através do enlace dinâmico tem duas fases:
1. Gerar um token
2. Ajustar o objeto de configuração

## <a name="generating-a-token"></a>Gerar um token
Para gerar um token, utilize a [API para gerar um token de incorporação para múltiplos itens](embed-sample-for-customers.md#multiEmbedToken).

O enlace dinâmico é suportado para ambos os cenários de incorporação, ou seja, *Incorporar para a sua organização* e *Incorporar para os seus clientes*.

| Solução                   | Token                               | Requirements                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Incorporar para a sua organização* | Token de acesso para utilizadores do Power BI     | O utilizador cujo token do Azure AD é utilizado tem de ter permissões adequadas para todos os artefactos.                                                                    |
| *Incorporar para os seus clientes*    | Token de acesso para utilizadores não pertencentes ao Power BI | Tem de incluir permissões para o relatório e para o conjunto de dados com enlace dinâmico. Utilize a nova API para gerar um token incorporado que suporte múltiplos artefactos. |

## <a name="adjusting-the-config-object"></a>Ajustar o objeto de configuração
Adicione `datasetBinding` ao objeto de configuração. Utilize o exemplo na parte inferior da página como referência.

Se não estiver familiarizado com a incorporação no Power BI, consulte os seguintes tutoriais para saber como incorporar os seus conteúdos do Power BI:
* [Incorporar conteúdo do Power BI numa aplicação para os seus clientes](embed-sample-for-customers.md)
* [Tutorial: Incorporar conteúdos do Power BI numa aplicação para a sua organização](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Exemplo
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```