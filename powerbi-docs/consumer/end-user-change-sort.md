---
title: Alterar a forma como um gráfico é ordenado num relatório
description: Alterar a forma como um gráfico é ordenado num relatório do Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852376"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Alterar a forma como um gráfico é ordenado num relatório do Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

No serviço Power BI, pode alterar o aspeto de um elemento visual ao ordená-lo por campos de dados diferentes. Ao alterar a forma como ordena um elemento visual, pode destacar as informações que pretende transmitir e certificar-se de que o elemento visual reflete essa tendência (ou ênfase).

Se estiver a utilizar dados numéricos (como o volume de vendas) ou dados de texto (como nomes de estado), pode ordenar as visualizações conforme quiser e dar-lhes o aspeto que preferir. O Power BI oferece bastante flexibilidade para ordenação e menus rápidos para utilização. Em qualquer elemento visual, selecione **Mais ações** (...) e, em seguida, selecione o campo pelo qual pretende ordenar.

![gráfico de barras ordenado alfabeticamente pelo eixo X](media/end-user-change-sort/power-bi-more-actions.png)

Os elementos visuais num dashboard não podem ser ordenados, mas num relatório do Power BI, pode ordenar alfabeticamente a maioria das visualizações pelos nomes das categorias no gráfico ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico está ordenado alfabeticamente pela categoria **nome de loja**.

![gráfico de barras ordenado alfabeticamente pelo eixo X](media/end-user-change-sort/pbi-chartsortcategory.png)

É fácil alterar a ordenação de uma categoria (nome de arquivo) para um valor (vendas por metro quadrado).

1. Selecione **Mais ações** (...) e selecione **Ordenar por > Vendas Por Metro Quadrado**.
2. Se necessário, selecione novamente **Mais ações** (...) e selecione **Ordenação descendente**. O campo que está a ser utilizado na ordenação está a negrito e tem uma barra amarela.

   ![vídeo que mostra a ordem de seleção ascendente e descendente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nem todos os elementos visuais podem ser ordenados. Por exemplo, os seguintes elementos visuais não podem ser ordenados: treemap, mapa, mapa de manchas, dispersão, medidor, cartão, cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Guardar as alterações feitas à sequência de ordenação
Os relatórios do Power BI mantêm os filtros, as segmentações de dados, a ordenação e outras alterações que fizer à vista de dados. Por isso, se sair de um relatório e regressar mais tarde, as alterações são guardadas.  Se quiser reverter as alterações para as definições do designer do relatório, selecione **Repor para predefinição** na barra de menus superior. 

![Ordenação persistente](media/end-user-change-sort/power-bi-reset.png)

No entanto, se o botão **Repor para predefinição** for apresentado a cinzento, isso significa que o designer do relatório desativou a capacidade de guardar (fazer persistir) as suas alterações.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordenar através de outros critérios
Por vezes, quer ordenar o elemento visual através de um campo diferente (que não esteja incluído no elemento visual) ou outros critérios.  Por exemplo, talvez queira ordenar por mês (e não por ordem alfabética) ou por números inteiros em vez de por dígitos (exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  O designer do relatório poderá atualizar o conjunto de dados para permitir este tipo de ordenação. As informações de contacto do designer podem ser encontradas ao selecionar o nome do relatório na barra de cabeçalho.

![Lista pendente a mostrar informações de contacto](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Próximos passos
Mais sobre [Visualizações em relatórios do Power BI](end-user-visualizations.md).

[Power BI - Conceitos Básicos](end-user-basic-concepts.md)
