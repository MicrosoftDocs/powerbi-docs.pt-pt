---
title: Funcionalidade supportsKeyboardFocus
description: Este artigo descreve como utilizar a funcionalidade supportsKeyboardFocus nos elementos visuais do Power BI e os seus requisitos.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: c8cf0f4e896b8a44764d1c363c597182f55d30b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276519"
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

Para experimentar o desenvolvimento do Power BI, veja [Desenvolver um elemento visual do Power BI](custom-visual-develop-tutorial.md).
