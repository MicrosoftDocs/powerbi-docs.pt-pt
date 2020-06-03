---
title: Descrição geral do principal de serviço
description: Descrição geral do principal de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 8482278d9054228dedafb6bd1b37368f5a4b5dce
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315830"
---
O principal de serviço é um método de autenticação que pode ser utilizado para permitir que uma aplicação do Azure Active Directory aceda aos conteúdos e às APIs do serviço Power BI.

Quando cria uma aplicação do Azure Ative Directory (AAD), é criado um [objeto do principal de serviço](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). O objeto do principal de serviço, também conhecido como *principal de serviço*, permite que o AAD autentifique a aplicação. Uma vez autenticada, a aplicação pode aceder aos recursos do inquilino do AAD.

Para autenticar, o principal de serviço utiliza o *ID da Aplicação* do AAD e um dos seguintes:

* Segredo da aplicação
* Certificado