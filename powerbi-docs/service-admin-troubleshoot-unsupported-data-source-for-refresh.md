---
title: Resolver problemas de origem de dados sem suporte para atualização
description: Resolver problemas de origem de dados sem suporte para atualização
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: bd0ea66b8caf32e3244ed4e5eef648100fc5169e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61188101"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Resolver problemas de origem de dados sem suporte para atualização
Vai ver um erro ao tentar configurar um conjunto de dados para atualização agendada.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Isso acontece quando a origem de dados usada no Power BI Desktop não tem suporte para atualização. Vai precisar de encontrar a origem de dados que está a utilizar e compará-la com a lista de origens de dados com suporte em [Atualizar dados no Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Encontrar a origem de dados
Se não tiver a certeza de que origem de dados foi utilizara, pode encontrar ao seguir os seguintes passos no Power BI Desktop.  

1. No Power BI Desktop, tenha certeza de que está no painel **Relatório**.  
   ![Painel de relatórios na versão Desktop](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Selecione **Editar Consultas** na barra da faixa de opções.  
   ![Editar consultas](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Selecione **Editor Avançado**.  
   ![Editor avançado](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Anote o fornecedor listado para a origem.  Neste exemplo, o fornecedor é Active Directory.  
   ![Fornecedor de origem de dados](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Compare o provedor com a lista de origens de dados com suporte encontrada em [Atualizar dados no Power BI](refresh-data.md).  Pode ver que o Active Directory não é uma origem de dados com suporte para a atualização.  

## <a name="next-steps"></a>Próximos passos
[Atualização de Dados](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[On-premises data gateway (Gateway de dados no local)](service-gateway-onprem.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
[Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

