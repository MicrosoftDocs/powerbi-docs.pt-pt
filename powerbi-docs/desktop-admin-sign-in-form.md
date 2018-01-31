---
title: "Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop"
description: "Aprenda como pode gerir o formulário de início de sessão inicial ao abrir o Power BI Desktop."
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 519f8b56b5086292addf577d969a707a6d6efcc8
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop
Na primeira vez que o Power BI Desktop é iniciado, é apresentado um formulário de início de sessão. As informações podem ser preenchidas, ou inicie a sessão no Power BI para continuar. Os administradores podem gerir este formulário ao utilizar uma chave do registo. 

![Formulário de início de sessão inicial para o Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Os administradores podem utilizar a seguinte chave do registo para desativar o formulário de início de sessão. Isto também pode ser utilizado com políticas globais para a organização inteira.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Um valor de 0 desativa a caixa de diálogo.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

