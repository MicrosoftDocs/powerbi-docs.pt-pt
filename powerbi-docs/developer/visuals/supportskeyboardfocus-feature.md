---
title: A funcionalidade supportsKeyboardFocus na análise incorporada do Power BI para melhores informações de BI incorporadas
description: Este artigo descreve como utilizar a funcionalidade supportsKeyboardFocus nos elementos visuais do Power BI e os seus requisitos. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 5ba87db8118076de4bf13abc0280223f9f04f871
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887966"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>Utilizar a funcionalidade supportsKeyboardFocus

Este artigo descreve como utilizar a funcionalidade `supportsKeyboardFocus` nos elementos visuais do Power BI.
A funcionalidade `supportsKeyboardFocus` permite-lhe navegar nos pontos de dados do elemento visual apenas com o teclado.

Para saber mais sobre a navegação dos elementos visuais através do teclado, veja [Navegação Através do Teclado](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation).

## <a name="example"></a>Exemplo

Abra um elemento visual que utilize a funcionalidade `supportsKeyboardFocus`. Selecione um ponto de dados dentro do elemento visual e prima a tecla de tabulação. O foco passa para o ponto de dados seguinte de cada vez que prime a tecla de tabulação. Prima enter para selecionar o ponto de dados realçado.

![Suporta o exemplo de foco do teclado](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Requirements

Esta funcionalidade requer a API v2.1.0 ou superior.

Esta funcionalidade pode ser aplicada a todos os elementos visuais, exceto a elementos visuais de imagem.

## <a name="usage"></a>Usage

Para utilizar a funcionalidade `supportsKeyboardFocus`, adicione o seguinte código ao ficheiro *capabilities.json* do elemento visual.
Esta capacidade permite que o elemento visual receba o foco através da navegação por teclado.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre as funcionalidades de acessibilidade, veja [Criar relatórios do Power BI para acessibilidade](../../create-reports/desktop-accessibility-creating-reports.md).

Para experimentar o desenvolvimento do Power BI, veja [Desenvolver um elemento visual do cartão circular do Power BI](develop-circle-card.md).
