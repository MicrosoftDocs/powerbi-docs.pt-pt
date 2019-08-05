---
title: Analytics pane (Painel de análise)
description: Como criar linhas de referência dinâmicas em Elementos Visuais do Power BI
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425534"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Painel de Análise em Elementos Visuais do Power BI

O **Painel de Análise** foi [apresentado para elementos visuais nativos](https://docs.microsoft.com/power-bi/desktop-analytics-pane) em novembro de 2018.
Os elementos visuais com a API v2.5.0 podem apresentar e gerir as suas propriedades no **Painel de Análise**.

![Painel de Análise](./media/visualization-pane-analytics-tab.png)

É tratado de forma semelhante a [gerir propriedades no painel Formatar](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options), ao definir um objeto no ficheiro capabilities.json do elemento visual. 

As diferenças são as seguintes:

1. Por baixo da definição de `object`, adicione um campo `objectCategory` com o valor 2.

    > [!NOTE]
    > `objectCategory` é um campo opcional apresentado na API 2.5.0. Define o aspeto do elemento visual que o objeto controla (1 = Formatação, 2 = Análise). A "Formatação" é utilizada para o aspeto e funcionalidade, cores, eixos, etiquetas, etc. A "Análise" é utilizada para previsões, linhas de tendência, linhas de referência, formas, etc.
    >
    > `objectCategory` é predefinido para "Formatação", se for omitido.

2. O objeto tem de ter as duas propriedades seguintes:
    1. `show` de tipo booleano, com o valor predefinido falso.
    2. `displayName` de tipo de texto. O valor predefinido que escolher será o nome a apresentar inicial da instância.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

As outras propriedades podem ser definidas da mesma forma que os objetos de Formato. A enumeração de objeto é feita exatamente da mesma forma que no **painel Formato**.

***Limitações e problemas conhecidos***

  1. Ainda não existe suporte de várias instâncias. Os objetos não podem ter um [seletor](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) diferente de estático (ou seja, "seletor": nulo) e os elementos visuais personalizados não podem ter múltiplas instâncias de um cartão definidas pelo utilizador.
  2. As propriedades do tipo `integer` não são apresentadas corretamente. Como alternativa, utilize o tipo `numeric`.

> [!NOTE]
> Utilize o Painel de Análise apenas para objetos que adicionam novas informações ou que revelam detalhes sobre as informações apresentadas. Por exemplo, as linhas de referência dinâmicas ilustram tendências importantes.
> Quaisquer opções que controlem o aspeto e funcionalidade do elemento visual, ou seja, a formatação, devem ser mantidas no painel Formatação.
