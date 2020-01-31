---
title: Ligar um relatório a um conjunto de dados através do enlace dinâmico
description: Saiba como incorporar um relatório através do enlace dinâmico.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: 1f54ce3a6bfd69caa3f386b7684e3df7f725523d
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709543"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Ligar um relatório a um conjunto de dados através do enlace dinâmico 

Quando um relatório está ligado a um conjunto de dados, pode utilizar o enlace dinâmico. A ligação entre o relatório e o conjunto de dados é denominada *enlace*. Quando o enlace é determinado no ponto da incorporação, por oposição a ser predeterminado numa altura anterior, o enlace é denominado enlace dinâmico.

Ao incorporar um relatório do Power BI através do *enlace dinâmico*, pode ligar o mesmo relatório a conjuntos de dados diferentes consoante as credenciais do utilizador.

Isto significa que pode utilizar um relatório para apresentar informações diferentes, consoante o conjunto de dados ao qual o relatório está ligado. Por exemplo, um relatório a mostrar os valores de vendas a retalho pode ser ligado a conjuntos de dados de revendedores diferentes e produzir resultados diferentes, consoante o conjunto de dados do revendedor ao qual o relatório está ligado.

O relatório e o conjunto de dados não têm de se encontrar na mesma área de trabalho. Ambas as áreas de trabalho (a que contém o relatório e a que contém o conjunto de dados) têm de ser atribuídas a uma [capacidade](azure-pbie-create-capacity.md).

Como parte do processo de incorporação, certifique-se de que *gera um token com permissões suficientes* e que *ajusta o objeto de configuração*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Gerar um token com permissões suficientes

O enlace dinâmico é suportado para ambos os cenários de incorporação, ou seja, *Incorporar para a sua organização* e *Incorporar para os seus clientes*. A tabela apresentada abaixo descreve as considerações para cada cenário.

|Scenario  |Propriedade de dados  |Token  |Requirements  |
|---------|---------|---------|---------|
|*Incorporar para a sua organização*    |Os dados pertencem ao utilizador         |Token de acesso para utilizadores do Power BI         |O utilizador cujo token do Azure AD é utilizado tem de ter permissões adequadas para todos os artefactos.         |
|*Incorporar para os seus clientes*     |Os dados pertencem à aplicação         |Token de acesso para utilizadores não pertencentes ao Power BI         |Tem de incluir permissões para o relatório e para o conjunto de dados com enlace dinâmico. Utilize a [API para gerar um token de incorporação para múltiplos itens](embed-sample-for-customers.md#multiEmbedToken), para gerar um token de incorporação que suporte múltiplos artefactos.         |

## <a name="adjusting-the-config-object"></a>Ajustar o objeto de configuração
Adicione `datasetBinding` ao objeto de configuração. Utilize o exemplo apresentado abaixo como referência.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Próximos passos

Se não estiver familiarizado com a incorporação no Power BI, consulte os seguintes tutoriais para saber como incorporar os seus conteúdos do Power BI:
* [Tutorial: Incorporar conteúdos do Power BI numa aplicação para os seus clientes](embed-sample-for-customers.md)
* [Tutorial: Incorporar conteúdos do Power BI numa aplicação para a sua organização](embed-sample-for-your-organization.md)