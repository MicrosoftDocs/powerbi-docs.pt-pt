---
title: Descrição geral do principal de serviço
description: Descrição geral do principal de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 6086185fb671b9f418ef2ec070b762020fbe8f75
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989508"
---
O principal de serviço é um método de autenticação que pode ser utilizado para permitir que uma aplicação do Azure Active Directory aceda aos conteúdos e às APIs do serviço Power BI.

Quando cria uma aplicação do Azure Ative Directory (AAD), é criado um [objeto do principal de serviço](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). O objeto do principal de serviço, também conhecido como *principal de serviço*, permite que o AAD autentifique a aplicação. Uma vez autenticada, a aplicação pode aceder aos recursos do inquilino do AAD.

Para autenticar, o principal de serviço utiliza o *ID da Aplicação* do AAD e um dos seguintes:

* Segredo da aplicação
* Certificado