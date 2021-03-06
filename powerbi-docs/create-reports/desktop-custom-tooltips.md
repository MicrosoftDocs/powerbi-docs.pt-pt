---
title: Customizing tooltips in Power BI Desktop (Personalizar descrições no Power BI Desktop)
description: Criar descrições personalizadas para elementos visuais com arrastar e largar
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 18658937d1e53340f4bdd5075479bd2926f295bd
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414214"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Personalizar descrições no Power BI Desktop

As descrições são uma forma elegante de fornecer informações mais contextuais e detalhes para pontos de dados num elemento visual. A imagem seguinte mostra uma descrição aplicada a um gráfico no Power BI Desktop.

![Descrição predefinida](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando uma visualização é criada, a descrição predefinida apresenta o valor e a categoria do ponto de dados. Há muitas instâncias nas quais a personalização das informações das descrições é útil. A personalização das descrições disponibiliza contexto e informações adicionais aos utilizadores que visualizam o elemento visual. As descrições personalizadas permitem-lhe especificar os pontos de dados adicionais que são apresentados como parte da descrição.

## <a name="how-to-customize-tooltips"></a>Como personalizar descrições

Para criar uma descrição personalizada, na área **Campos** do painel **Visualizações**, arraste um campo para o registo **Descrições**, mostrado na imagem seguinte. Na seguinte imagem, foram colocados três campos no registo **Descrições**.

![Adicionar campos de descrição](media/desktop-custom-tooltips/custom-tooltips-2.png)

Depois de adicionar as descrições a **Descrições**, pairar o rato sobre um ponto de dados na visualização mostra os valores desses campos.

![Descrição personalizada](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>Personalizar as descrições com agregação ou medidas rápidas

Pode personalizar ainda mais uma descrição ao selecionar uma função de agregação ou uma *medida rápida*. Selecione a seta ao lado do campo no registo **Descrições**. Em seguida, selecione a partir das opções disponíveis.

![Descrição com medida rápida](media/desktop-custom-tooltips/custom-tooltips-4.png)

Existem muitas formas de personalizar as descrições, com qualquer campo disponível no conjunto de dados, para transmitir informações rápidas aos utilizadores que visualizam os dashboards ou relatórios.
