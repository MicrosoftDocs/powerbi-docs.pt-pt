---
title: Funcionalidade supportsMultiVisualSelection
description: Este artigo descreve como utilizar a funcionalidade supportsMultiVisualSelection nos elementos visuais do Power BI e os seus requisitos.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272701"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Utilizar a funcionalidade supportsMultiVisualSelection

A funcionalidade `supportsMultiVisualSelection` permite-lhe utilizar a seleção em vários elementos visuais num relatório.

## <a name="example"></a>Exemplo

Num relatório com mais de um elemento visual, selecione dois valores para que esses valores sejam aplicados aos outros elementos visuais. Por exemplo, no [Exemplo de Análise de Revenda](../../create-reports/sample-retail-analysis.md), selecione **Fashions Direct** num elemento visual. Prima Ctrl e selecione **Jan** noutro elemento visual. No relatório, as seleções serão aplicadas aos outros elementos visuais que suportam a utilização desta funcionalidade. Os outros elementos visuais encontram-se agora no âmbito de **Fashions Direct** e **Jan**.

## <a name="requirements"></a>Requirements

Esta funcionalidade requer a API v3.2.0 ou superior.

Não pode aplicar esta funcionalidade a elementos visuais de imagem. Não pode aplicá-la a alguns elementos visuais avançados, como elementos chave, árvore de decomposição, elementos visuais das Perguntas e Respostas, caixa de texto e gráficos de medidor.

## <a name="usage"></a>Usage

Para utilizar a funcionalidade `supportsMultiVisualSelection`, adicione o seguinte código ao ficheiro `capabilities.json` do elemento visual.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre os conceitos do Power BI, veja [Elementos Visuais do Power BI](power-bi-visuals-concept.md).

Para experimentar o desenvolvimento do Power BI, veja [Desenvolver um elemento visual do Power BI](custom-visual-develop-tutorial.md).
