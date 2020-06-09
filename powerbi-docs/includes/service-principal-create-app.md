---
title: Criação da aplicação do principal de serviço
description: Criação da aplicação do principal de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315843"
---
1. Inicie sessão no [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Procure **Registos de aplicações** e clique na ligação **Registos de aplicações**.

    ![registo de aplicações do Azure](media/embedded-service-principal/azure-app-registration.png)

3. Clique em **Novo registo**.

    ![novo registo](media/embedded-service-principal/new-registration.png)

4. Preencha as informações necessárias:
    * **Nome** – introduza um nome para a aplicação
    * **Tipos de conta suportados** – selecione os tipos de conta suportados
    * (Opcional) **URI de Redirecionamento** – introduza um URI, se necessário

5. Clique em **Registar**.

6. Após o registo, o *ID da Aplicação* está disponível no separador **Descrição geral**. Copie e guarde o *ID da Aplicação* para utilizar mais tarde.

    ![ID da aplicação](media/embedded-service-principal/application-id.png)