---
title: A resolução de problemas da atualização agendada para Base de Dados SQL do Azure
description: A resolução de problemas em atualização agendada para a base de dados SQL Azure no Power BI
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 292f80b4fec7da9ff6ce42e3611bf4d6353bae2d
ms.sourcegitcommit: 90bd747b7c460d17b74cd386d3f5714234b1f6c9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74791945"
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
