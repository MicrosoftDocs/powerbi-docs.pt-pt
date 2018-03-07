---
title: "Vista de Relações no Power BI Desktop"
description: "Vista de Relações no Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: e94977a8b9a106798f0facd962d6e766f6410da3
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="relationship-view-in-power-bi-desktop"></a>Vista de Relações no Power BI Desktop
A **Vista de Relações** mostra todas as tabelas, colunas e relações no seu modelo. Isto pode ser especialmente útil quando o modelo tiver relações complexas entre várias tabelas.

Vamos dar uma vista de olhos.

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Ícone Vista de Relações – clique para mostrar o modelo na Vista de Relações

**B.** Relação – pode passar o cursor sobre uma relação para mostrar as colunas usadas. Faça duplo clique numa relação para abri-la na caixa de diálogo **Editar Relação**. 

Na figura acima, pode ver que a tabela *Stores* tem uma coluna *StoreKey* que está relacionada com a tabela *Sales*, que também tem uma coluna *StoreKey*. Podemos ver que é uma relação do tipo *Muitos para Um* (\*:1) e que o ícone no meio da linha mostra a direção da Filtragem cruzada definida como *Ambas*. A seta no ícone mostra a direção do fluxo do contexto de filtro.

Para saber mais sobre as relações, consulte [Criar e gerir relações no Power BI Desktop](desktop-create-and-manage-relationships.md).

