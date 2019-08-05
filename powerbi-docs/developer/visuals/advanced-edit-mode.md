---
title: Advanced Edit Mode (Modo de Edição Avançado)
description: Elementos visuais do Power BI com controlos de IU avançados
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 625105aed773bce5cf70932f092faf60ea001c2c
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425557"
---
# <a name="advanced-edit-mode"></a>Modo de edição avançada

Os elementos visuais que necessitam de controlos de IU avançados podem declarar suporte para o Modo de Edição Avançada.
Se for suportado, no modo de edição de relatórios, será apresentado um botão `Edit` no menu do elemento visual.
Ao clicar no botão `Edit`, o EditMode é definido como `Advanced`.
O elemento visual pode utilizar o sinalizador EditMode para determinar se esses controlos de IU devem ser apresentados.

Por predefinição, o elemento visual não é suportado pelo Modo de Edição Avançada.
Se for necessário um comportamento diferente, este deve ser declarado explicitamente no ficheiro `capabilities.json` do elemento visual, através da definição da propriedade `advancedEditModeSupport`.

Os valores possíveis são:

- 0 – NotSupported

- 1 – SupportedNoAction

- 2 – SupportedInFocus

## <a name="entering-advanced-edit-mode"></a>Entrar no Modo de Edição Avançada

O botão `Edit` ficará visível se:

 1 – a propriedade `advancedEditModeSupport` for definida em capabilities.json como `SupportedNoAction` ou `SupportedInFocus`.

 2 – o elemento visual for visualizado no modo de edição de relatórios.

Se a propriedade `advancedEditModeSupport` estiver fora do ficheiro capabilities.json ou estiver definida como `NotSupported`, o botão "Editar" desaparecerá.

![Entrar no modo de edição](./media/edit-mode.png)

Quando o utilizador clicar em `Edit`, o elemento visual irá receber uma chamada de atualização com o EditMode definido como `Advanced`.
De acordo com o valor definido nas capacidades, serão executadas as seguintes ações:

* `SupportedNoAction` – não será necessária qualquer ação adicional da parte do anfitrião.
* `SupportedInFocus` – o anfitrião irá apresentar o elemento visual no modo de detalhe.

## <a name="exiting-advanced-edit-mode"></a>Sair do Modo de Edição Avançada

O botão `Back to report` ficará visível se:

1 – a propriedade `advancedEditModeSupport` for definida em capabilities.json como `SupportedInFocus`.
