---
title: Passar uma aplicação de análise incorporada do Power BI para a fase de produção para melhores informações de BI incorporadas
description: Saiba quais são os passos necessários para passar a sua aplicação do Power BI para a fase de produção. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 71eff0f09c0e34ffd8789f1b56347d754b6589bc
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886678"
---
# <a name="move-your-embedded-app-to-production"></a>Passar uma aplicação incorporada para a fase de produção

Agora que concluiu o desenvolvimento da aplicação, para poder passá-la para a fase de produção irá precisar de uma capacidade para a sua área de trabalho.

> [!Important]
> Todas as áreas de trabalho (as que contêm os relatórios ou dashboards e as que contêm os conjuntos de dados) têm de ser atribuídas a uma capacidade.

## <a name="create-a-capacity"></a>Criar uma capacidade

Ao criar uma capacidade, pode tirar partido de ter um recurso para os seus clientes. Existem dois tipos de capacidade que pode escolher:

* **Power BI Premium** – uma subscrição do Microsoft 365 ao nível do inquilino, disponível em duas famílias de SKUs, *EM* e *P*. Ao incorporar conteúdo do Power BI, esta solução é conhecida como *incorporação do Power BI*. Para saber mais sobre esta subscrição, veja [O que é o Power BI Premium?](../../admin/service-premium-what-is.md)

* **Azure Power BI Embedded** – pode comprar uma capacidade no [portal do Microsoft Azure](https://portal.azure.com). Esta subscrição utiliza os SKUs *A*. Para obter mais informações sobre como criar uma capacidade do Power BI Embedded, veja [Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md) (Criar capacidade do Power BI Embedded no portal do Azure).

    > [!NOTE]
    > Com os SKUs A, não pode aceder a conteúdos do Power BI com uma licença do Power BI GRATUITA.

### <a name="capacity-specifications"></a>Especificações da capacidade

A seguinte tabela descreve os recursos e limites de cada SKU. Para determinar qual a capacidade mais adequada às suas necessidades, veja a tabela [que SKU devo comprar para o meu cenário](./embedded-faq.md#which-solution-should-i-choose).

| Nós de Capacidade | Núcleos virtuais totais | Núcleos virtuais de back-end | RAM (GB) | Núcleos virtuais de front-end | DirectQuery/Ligação em Direto (por segundo) | Paralelismo de Atualização do Modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>Testes de desenvolvimento

Pode utilizar tokens de avaliação incorporados com uma licença Pro para fins de teste de desenvolvimento. Utilize uma capacidade para incorporar num ambiente de produção.

O número de tokens de avaliação incorporados que um *principal de serviço* ou *utilizador principal* (conta principal) do Power BI pode gerar é limitado. Utilize a API [Funcionalidades Disponíveis](/rest/api/power-bi/availablefeatures/getavailablefeatures) para verificar a sua percentagem de utilização atual incorporada. O valor de utilização é apresentado por principal do serviço ou conta principal.

Se ficar sem tokens incorporados durante as avaliações, tem de adquirir uma [capacidade](embedded-capacity.md) do Power BI Incorporada ou Premium. Não existe um número limite de tokens de incorporação que pode gerar com uma capacidade.

## <a name="assign-a-workspace-to-a-capacity"></a>Atribuir uma área de trabalho a uma capacidade

Assim que criar uma capacidade, pode atribuir a área de trabalho a essa capacidade.

Todas as áreas de trabalho que contêm recursos do Power BI relacionados com os conteúdos incorporados (incluindo conjuntos de dados, relatórios e dashboards) têm de ser atribuídas a capacidades. Por exemplo, se um relatório incorporado e o conjunto de dados a este vinculado residirem em diferentes áreas de trabalho, ambas as áreas de trabalho têm de ser atribuídas a capacidades.

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>Atribuir uma área de trabalho a uma capacidade com um principal de serviço

Para atribuir uma capacidade a uma área de trabalho com um [principal de serviço](embed-service-principal.md), utilize a [API REST do Power BI](/rest/api/power-bi/capacities/groups_assigntocapacity). Ao utilizar as APIs REST do Power BI, certifique-se de que utiliza o [ID de objeto do principal de serviço](embed-service-principal.md).

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>Atribuir uma área de trabalho a uma capacidade com um utilizador principal

Siga os passos abaixo para atribuir uma capacidade a uma área de trabalho com um **utilizador principal**.

1. Abra a área de trabalho no **serviço Power BI**. 

1. No **serviço Power BI**, expanda as áreas de trabalho e selecione as reticências da área de trabalho que está a utilizar para incorporar os seus conteúdos. Em seguida, selecione **Editar área de trabalho**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="Uma captura de ecrã a mostrar o menu de definições de área de trabalho no portal do serviço Power B I.":::

2. Selecione o separador **Premium** e faça o seguinte:

    * Ative a opção **Capacidade**.

    * Selecione a capacidade que criou.

    * Selecione **Guardar**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="Uma captura de ecrã a mostrar o separador de definições de área de trabalho premium no portal do serviço Power B I.":::

    Depois de atribuir a sua área de trabalho a uma capacidade, é apresentado um símbolo de diamante junto à mesma 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="Uma captura de ecrã a mostrar o símbolo de diamante junto a uma área de trabalho com uma capacidade premium no portal do serviço Power B I.":::

## <a name="next-steps"></a>Próximos passos

>[!div class="nextstepaction"]
>[Capacidade e SKUs na análise incorporada do Power BI](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Capacidade de planeamento na análise incorporada do Power BI](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[Considerações ao gerar um token de incorporação](generate-embed-token.md)