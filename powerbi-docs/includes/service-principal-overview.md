---
title: Descrição geral do principal de serviço
description: Descrição geral do principal de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 7fc4412a66602fe3a6548c3e1afb06de788da90d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82616118"
---
O principal de serviço é um método de autenticação que pode ser utilizado para permitir que uma aplicação do Azure Active Directory aceda aos conteúdos e às APIs do serviço Power BI.

Quando cria uma aplicação do Azure Ative Directory (AAD), é criado um [objeto do principal de serviço](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). O objeto do principal de serviço, também conhecido como *principal de serviço*, permite que o AAD autentifique a aplicação. Uma vez autenticada, a aplicação pode aceder aos recursos do inquilino do AAD.

Para autenticar, o principal de serviço utiliza o *ID da Aplicação* do AAD e um dos seguintes:
* Segredo da aplicação
* Certificado