---
title: Vista de modelo no Power BI Desktop
description: Vista de modelo no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 1c580d403ef33f1c61d5fcd0707d78b4b331da5d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239867"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Trabalhar com a vista de Modelo no Power BI Desktop

A *vista de Modelo* mostra todas as tabelas, colunas e relações no modelo. Esta vista pode ser especialmente útil quando o modelo tiver relações complexas entre várias tabelas.

Selecione o ícone **Modelo** perto da lateral da janela para ver uma vista do modelo existente. Paire o cursor sobre uma linha de relação para mostrar as colunas usadas.

![Vista de modelo, Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

Na figura, a tabela *Stores* tem uma coluna *StoreKey* que está relacionada com a tabela *Sales*, que também tem uma coluna *StoreKey*. As duas tabelas têm uma relação de *Muitos para Um* (\*:1). Uma seta no meio da linha mostra a direção do fluxo de contexto de filtro. As setas duplas significam que a direção do filtro cruzado está definida como *Ambas*.

Pode fazer duplo clique numa relação para abri-la na caixa de diálogo **Editar Relação**. Para saber mais sobre as relações, consulte [Criar e gerir relações no Power BI Desktop](desktop-create-and-manage-relationships.md).
