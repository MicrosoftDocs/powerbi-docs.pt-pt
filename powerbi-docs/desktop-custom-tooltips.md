---
title: Personalizar descrições no Power BI Desktop
description: Criar descrições personalizadas para elementos visuais com arrastar e largar
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5dfd22f8b45253ece4ed8f699adec9abcaa1a8ed
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34721162"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalizar Descrições no Power BI Desktop
As descrições são uma forma elegante de fornecer informações mais contextuais e detalhes para pontos de dados num elemento visual. A imagem seguinte mostra uma descrição aplicada a um gráfico no Power BI Desktop.

![Descrição predefinida](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando uma visualização é criada, a descrição predefinida apresenta o valor e a categoria do ponto de dados. Existem várias instâncias em que a capacidade de personalizar as informações de descrição seria útil e forneceria contexto e informações adicionais aos utilizadores que visualizam o elemento visual. As descrições personalizadas permitem-lhe especificar os pontos de dados adicionais que são apresentados como parte da descrição.

## <a name="how-to-customize-tooltips"></a>Como personalizar descrições
Para criar uma descrição personalizada, no poço **Campos** do painel **Visualizações**, arraste um campo para o registo **Descrições**, conforme mostrado na imagem seguinte. Na seguinte imagem, foram colocados dois campos no registo **Descrições**.

![Adicionar campos de descrição](media/desktop-custom-tooltips/custom-tooltips-2.png)

Depois de as descrições serem adicionadas ao conjunto de campos, pairar o rato sobre um ponto de dados na visualização apresentará os valores desses campos na descrição.

![Descrição personalizada](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizar as descrições com agregação ou Cálculos Rápidos
Pode personalizar ainda mais uma descrição, ao selecionar uma função de agregação ou um *Cálculo Rápido*, selecionando a seta junto do campo no registo **Descrições** e selecionando entre as opções disponíveis.

![Descrição com Cálculo Rápido](media/desktop-custom-tooltips/custom-tooltips-4.png)

Existem várias formas de personalizar **Descrições**, com qualquer campo disponível no conjunto de dados, para transmitir informações rápidas aos utilizadores que visualizam os dashboards ou relatórios.

