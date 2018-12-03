---
title: Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop
description: Aprenda como pode gerir o formulário de início de sessão inicial ao abrir o Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
ms.openlocfilehash: 3c92063c82c370bd59ecd7bfa2798ae60a3b425d
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578250"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop
Na primeira vez que o Power BI Desktop é iniciado, é apresentado um formulário de início de sessão. Pode preencher as informações ou iniciar sessão no Power BI para continuar. Os administradores fazem a gestão deste formulário através de uma chave do registo. 

![Formulário de início de sessão inicial para o Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Os administradores utilizam a seguinte chave do registo para desativar o formulário de início de sessão. Isto também pode ser enviado para uma organização inteira através de políticas globais.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Um valor de 0 desativa a caixa de diálogo.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

