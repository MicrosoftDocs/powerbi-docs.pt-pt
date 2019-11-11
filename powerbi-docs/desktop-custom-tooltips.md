---
title: Personalizar descrições no Power BI Desktop
description: Criar descrições personalizadas para elementos visuais com arrastar e largar
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: efbae4250b7b3cab18892cf519bfac5da3a88e1b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73868658"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalizar Descrições no Power BI Desktop
As descrições são uma forma elegante de fornecer informações mais contextuais e detalhes para pontos de dados num elemento visual. A imagem seguinte mostra uma descrição aplicada a um gráfico no Power BI Desktop.

![Descrição predefinida](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando uma visualização é criada, a descrição predefinida apresenta o valor e a categoria do ponto de dados. Existem várias instâncias em que a personalização das informações de descrição é útil e poderia fornecer contexto e informações adicionais aos utilizadores que visualizam o elemento visual. As descrições personalizadas permitem-lhe especificar os pontos de dados adicionais que são apresentados como parte da descrição.

## <a name="how-to-customize-tooltips"></a>Como personalizar descrições
Para criar uma descrição personalizada, no poço **Campos** do painel **Visualizações**, arraste um campo para o registo **Descrições**, mostrado na imagem seguinte. Na seguinte imagem, foram colocados dois campos no registo **Descrições**.

![Adicionar campos de descrição](media/desktop-custom-tooltips/custom-tooltips-2.png)

Depois de as descrições serem adicionadas ao conjunto de campos, pairar o rato sobre um ponto de dados na visualização apresentará os valores desses campos na descrição.

![Descrição personalizada](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizar as descrições com agregação ou Cálculos Rápidos
Pode personalizar ainda mais uma descrição, ao selecionar uma função de agregação ou um *Cálculo Rápido*, selecionando a seta junto do campo no registo **Descrições** e selecionando entre as opções disponíveis.

![Descrição com Cálculo Rápido](media/desktop-custom-tooltips/custom-tooltips-4.png)

Existem várias formas de personalizar **descrições**, com qualquer campo disponível no conjunto de dados, para transmitir informações rápidas aos utilizadores que visualizam os dashboards ou relatórios.

