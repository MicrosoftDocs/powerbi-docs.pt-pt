---
title: Resolver problemas de origem de dados sem suporte para atualização
description: Resolver problemas de origem de dados sem suporte para atualização
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.author: davidi
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 49af2febbecb5061c4acb9ee20c3b707e3b81dff
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/01/2020
ms.locfileid: "91634901"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Resolver problemas de origem de dados sem suporte para atualização
Vai ver um erro ao tentar configurar um conjunto de dados para atualização agendada.

```output
You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.
```

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
5. Compare o fornecedor com a lista de origens de dados suportadas encontrada em [Origens de dados do Power BI](power-bi-data-sources.md).

> [!NOTE]
> Para problemas de atualização relacionados com origens de dados dinâmicas, incluindo origens de dados que incluam consultas criadas manualmente, veja [origens de dados atualizadas e dinâmicas](refresh-data.md#refresh-and-dynamic-data-sources).


## <a name="next-steps"></a>Próximos passos
[Atualização de Dados](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[On-premises data gateway (Gateway de dados no local)](service-gateway-onprem.md)  
[Resolução de problemas do Gateway de dados no local](service-gateway-onprem-tshoot.md)  
[Resolver problemas do Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
