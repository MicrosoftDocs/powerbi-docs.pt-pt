---
title: O modo de edição avançado em elementos visuais do Power BI na análise incorporada do Power BI para obter melhores informações de BI incorporadas
description: Este artigo aborda como definir controlos avançados de IU em elementos visuais do Power BI. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 02f02f23d3dfd7ec514e17d1bab17be715e9cd7d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889139"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Modo de edição avançado nos elementos visuais do Power BI

Se precisar de controlos avançados de IU no seu elemento visual do Power BI, poderá tirar proveito do modo de edição avançado. No modo de edição de relatórios, selecione o botão **Editar** para definir o modo de edição para **Avançado**. O elemento visual pode utilizar o sinalizador `EditMode` para determinar se esse controlo de IU deve ser apresentado.

Por predefinição, o elemento visual não suporta o modo de edição avançado. Se for necessário um comportamento diferente, pode declará-lo explicitamente no ficheiro *capabilities.json* do elemento visual, através da definição da propriedade `advancedEditModeSupport`.

Os valores possíveis são:

- `0` – NotSupported

- `1` – SupportedNoAction

- `2` – SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Entrar no modo de edição avançado

Um botão **Editar** será apresentado se:

* A propriedade `advancedEditModeSupport` estiver definida no ficheiro *capabilities.json* para `SupportedNoAction` ou `SupportedInFocus`.

* O elemento visual for visualizado no modo de edição de relatórios.

Se a propriedade `advancedEditModeSupport` estiver fora do ficheiro *capabilities.json* ou estiver definida como `NotSupported`, o botão **Editar** não é apresentado.

![Entrar no modo de edição](media/advanced-edit-mode/edit-mode.png)

Ao selecionar **Editar**, o elemento visual obtém uma chamada de atualização() com EditMode definido como `Advanced`. Consoante o valor definido no ficheiro *capabilities.json*, irão ocorrer as seguintes ações:

* `SupportedNoAction`: Não será necessária qualquer ação adicional da parte do anfitrião.
* `SupportedInFocus`: O anfitrião irá apresentar o elemento visual no modo de detalhe.

## <a name="exit-advanced-edit-mode"></a>Sair do modo de edição avançado

O botão **Voltar ao relatório** é apresentado se:

* A propriedade `advancedEditModeSupport` estiver definida no ficheiro *capabilities.json* para `SupportedInFocus`.
