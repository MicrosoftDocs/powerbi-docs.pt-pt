---
title: Troubleshooting scheduled refresh for Azure SQL Databases (Resolução de problemas da atualização agendada para Bases de Dados SQL do Azure)
description: A resolução de problemas em atualização agendada para a base de dados SQL Azure no Power BI
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: davidi
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6efc7b031b9eb5708fe55c5b4167af0428ff7c19
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485720"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>A resolução de problemas em atualização agendada para a base de dados SQL Azure no Power BI

Para obter informações detalhadas sobre a atualização, veja [Atualizar dados no Power BI](refresh-data.md) e [Configurar a atualização agendada](refresh-scheduled-refresh.md).

Ao configurar a atualização agendada para a base de dados SQL do Azure, se receber um erro com o código de erro 400 durante a edição de credenciais, experimente o seguinte para configurar a regra de firewall adequada:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).

1. Aceda à base de dados SQL do Azure na qual está a configurar a atualização.

1. Na parte superior do painel **Descrição geral**, selecione **Definir firewall do servidor**.

1. No painel **Definições de firewall**, certifique-se de que a opção **Permitir acesso aos serviços do Azure** está definida como **ATIVADO**.

    ![Serviços permitidos do Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
