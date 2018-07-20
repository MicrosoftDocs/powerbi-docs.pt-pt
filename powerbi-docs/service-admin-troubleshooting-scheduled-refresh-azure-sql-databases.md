---
title: A resolução de problemas da atualização agendada para Base de Dados SQL do Azure
description: A resolução de problemas em atualização agendada para a base de dados SQL Azure no Power BI
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9439ac6bd0b4df568b964f548372fb94d2fd0b26
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34238532"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>A resolução de problemas em atualização agendada para a base de dados SQL Azure no Power BI
Para obter etapas detalhadas sobre como configurar a atualização agendada, certifique-se de ver [Atualizar dados no Power BI](refresh-data.md).

Ao configurar a atualização agendada para a base de dados SQL Azure, se receber um erro com o código de erro 400 durante a edição de credenciais, tente o seguinte para configurar a regra de firewall apropriada:

1. Entre no Portal de Gestão do Azure
2. Vá para o servidor SQL Azure no qual está a configurar a atualização
3. Ative os “Serviços do Microsoft Azure” na secção de serviços permitidos

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

