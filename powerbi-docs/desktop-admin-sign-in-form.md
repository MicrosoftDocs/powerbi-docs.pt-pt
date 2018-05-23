---
title: Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop
description: Aprenda como pode gerir o formulário de início de sessão inicial ao abrir o Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
ms.openlocfilehash: 98bf9579ae7ee551634eed765138c0e78156464c
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
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

