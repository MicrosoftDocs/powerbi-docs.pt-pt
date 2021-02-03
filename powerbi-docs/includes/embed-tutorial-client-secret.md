---
title: Tutorial de análise incorporado para obter o segredo do cliente
description: Obter o segredo do cliente para os tutoriais de análise incorporados.
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 12/09/2020
ms.custom: include file
ms.openlocfilehash: 875243aa890b80d21a73b20dec291329d256ba21
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494731"
---
Para obter o segredo do cliente, siga estes passos:

1. Inicie sessão no [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Procure **Registos de aplicações** e selecione a ligação **Registos de aplicações**.

3. Selecione a aplicação do Azure AD que está a utilizar para incorporar os seus conteúdos do Power BI.

4. Em **Gerir**, selecione **Certificados e segredos**.

5. Em **Segredos do cliente**, selecione **Novo segredo do cliente**.

6. Na janela de pop-up **Adicionar um segredo de cliente**, forneça uma descrição para o seu segredo da aplicação, selecione quando o segredo da aplicação expira e selecione **Adicionar**.

7. Na secção **Segredos do cliente**, copie a cadeia na coluna **Valor** do segredo da aplicação criado recentemente. O valor do segredo do cliente é o seu *ID do cliente*.