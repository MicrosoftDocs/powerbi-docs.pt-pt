---
title: Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop
description: Aprenda como pode gerir o formulário de início de sessão inicial ao abrir o Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: b1ab5188ba8f5ccf54589d359f6f8ced1ada3060
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2020
ms.locfileid: "73878846"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop
Na primeira vez que o Power BI Desktop é iniciado, é apresentado um formulário de início de sessão. Pode preencher as informações ou iniciar sessão no Power BI para continuar. Os administradores fazem a gestão deste formulário através de uma chave do registo. 

![Formulário de início de sessão inicial para o Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Os administradores utilizam a seguinte chave do registo para desativar o formulário de início de sessão. Isto também pode ser enviado para uma organização inteira através de políticas globais.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
Também pode experimentar a seguinte chave, que tem sido bem-sucedida para alguns clientes com base nas respetivas configurações:

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Um valor de 0 desativa a caixa de diálogo.




Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

