---
title: Como os administradores podem gerir o formulário de início de sessão do Power BI Desktop
description: Aprenda como pode gerir o formulário de início de sessão inicial ao abrir o Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: 44cb8d3f646b0bd8e673c8ef3c1743b58bcbcaba
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491190"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>Administradores: Gerir o formulário de início de sessão do Power BI Desktop
Na primeira vez que o Power BI Desktop é iniciado, é apresentado um formulário de início de sessão. Pode preencher as informações ou iniciar sessão no Power BI para continuar. Os administradores fazem a gestão deste formulário através de uma chave do registo. 

![Captura de ecrã a mostrar um formulário de início de sessão inicial para o Power B I Desktop.](media/desktop-admin-sign-in-form/sign-in-form.png)

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

