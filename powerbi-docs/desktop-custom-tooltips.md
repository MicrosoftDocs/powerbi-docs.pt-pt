---
title: Personalizar descrições no Power BI Desktop
description: Criar descrições personalizadas para elementos visuais com arrastar e largar
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 75cafe7c3de05d901e95662829e30c809ae54ace
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalizar Descrições no Power BI Desktop
As descrições são uma forma elegante de fornecer informações mais contextuais e detalhes para pontos de dados num elemento visual. A imagem seguinte mostra uma descrição aplicada a um gráfico no Power BI Desktop.

![](media/desktop-custom-tooltips/custom-tooltips_1.png)

Quando uma visualização é criada, a descrição predefinida apresenta o valor e a categoria do ponto de dados. Existem várias instâncias em que a capacidade de personalizar as informações de descrição seria útil e forneceria contexto e informações adicionais aos utilizadores que visualizam o elemento visual. As descrições personalizadas permitem-lhe especificar os pontos de dados adicionais que são apresentados como parte da descrição.

## <a name="how-to-customize-tooltips"></a>Como personalizar descrições
Para criar uma descrição personalizada, no poço **Campos** do painel **Visualizações**, arraste um campo para o registo **Descrições**, conforme mostrado na imagem seguinte. Na imagem seguinte, quatro campos foram colocados no registo **Descrições**.

![](media/desktop-custom-tooltips/custom-tooltips_2.png)

Depois de as Descrições serem adicionadas ao poço do campo, pairar o rato sobre um ponto de dados na visualização mostra os valores desses campos na descrição.

![](media/desktop-custom-tooltips/custom-tooltips_3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizar as descrições com agregação ou Cálculos Rápidos
Pode personalizar ainda mais uma descrição, ao selecionar uma função de agregação ou um *Cálculo Rápido*, selecionando a seta junto do campo no registo **Descrições** e selecionando entre as opções disponíveis.

![](media/desktop-custom-tooltips/custom-tooltips_4.png)

Existem várias formas de personalizar **Descrições**, com qualquer campo disponível no conjunto de dados, para transmitir informações rápidas aos utilizadores que visualizam os dashboards ou relatórios.

