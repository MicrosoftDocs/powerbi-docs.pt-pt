---
title: Ligar um relatório do Power BI a um conjunto de dados através do enlace dinâmico
description: Saiba como incorporar um relatório do Power BI através do enlace dinâmico na análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 01/17/2021
ms.openlocfilehash: 0bc33ed37e389b42f5c27f8271cc461eb99e229a
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565813"
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
|*Incorporar para os seus clientes*     |Os dados pertencem à aplicação         |Token de acesso para utilizadores não pertencentes ao Power BI         |Tem de incluir permissões para o relatório e para o conjunto de dados com enlace dinâmico. Utilize a [API para gerar um token de incorporação para múltiplos itens](/rest/api/power-bi/embedtoken/generatetoken), para gerar um token de incorporação que suporte múltiplos artefactos.         |

## <a name="adjusting-the-config-object"></a>Ajustar o objeto de configuração

Para o enlace dinâmico funcionar, terá de adicionar `datasetBinding` ao objeto de configuração. Para saber como fazê-lo, veja [Vincular conjuntos de dados a um relatório de forma dinâmica](/javascript/api/overview/powerbi/bind-report-datasets). 

## <a name="next-steps"></a>Próximos passos

Se não estiver familiarizado com a incorporação no Power BI, consulte os seguintes tutoriais para saber como incorporar os seus conteúdos do Power BI.

>[!div class="nextstepaction"]
>[Incorporar conteúdo do Power BI numa aplicação para os seus clientes](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Incorporar conteúdos do Power BI numa aplicação para a sua organização](embed-sample-for-your-organization.md)