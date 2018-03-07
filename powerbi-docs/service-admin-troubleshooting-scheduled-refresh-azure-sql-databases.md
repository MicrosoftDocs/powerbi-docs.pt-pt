---
title: "A resolução de problemas da atualização agendada para Base de Dados SQL do Azure"
description: "A resolução de problemas em atualização agendada para a base de dados SQL Azure no Power BI"
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 5f699ed013f35edd4f958b3c958e56ebeb05029c
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>A resolução de problemas em atualização agendada para a base de dados SQL Azure no Power BI
Para obter etapas detalhadas sobre como configurar a atualização agendada, certifique-se de ver [Atualizar dados no Power BI](refresh-data.md).

Ao configurar a atualização agendada para a base de dados SQL Azure, se receber um erro com o código de erro 400 durante a edição de credenciais, tente o seguinte para configurar a regra de firewall apropriada:

1. Entre no Portal de Gestão do Azure
2. Vá para o servidor SQL Azure no qual está a configurar a atualização
3. Ative os “Serviços do Microsoft Azure” na secção de serviços permitidos

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

