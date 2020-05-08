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
ms.openlocfilehash: 934827311e089e34e56fbcffe4d4c58a056df4ad
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761709"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>Administradores: Gerir o formulário de início de sessão do Power BI Desktop
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

