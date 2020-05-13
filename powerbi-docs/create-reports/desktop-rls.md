---
title: Restringir o acesso aos dados com segurança ao nível da linha (RLS) para o Power BI Desktop
description: Como configurar a segurança ao nível da linha para conjuntos de dados importados, e DirectQuery, no Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 89c33de2ef7319c6dcbeace0df79786128e16cd9
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83334321"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Restringir o acesso aos dados com segurança ao nível da linha (RLS) para o Power BI Desktop

Pode utilizar a segurança ao nível da linha (RLS) com o Power BI Desktop para restringir o acesso a dados para determinados utilizadores. Os filtros restringem os dados ao nível da linha. Pode definir filtros nas funções.

Pode agora configurar a RLS para os modelos de dados importados para o Power BI com o Power BI Desktop. Também pode configurar a RLS em conjuntos de dados que utilizem o [DirectQuery](../connect-data/desktop-use-directquery.md), como o SQL Server. Anteriormente, só era possível implementar a RLS em modelos do Analysis Services no local fora do Power BI. Para as ligações em direto dos Analysis Services, configure a segurança ao nível da linha no modelo no local. A opção de segurança não é apresentada para conjuntos de dados de ligação em direto.

> [!IMPORTANT]
> Se tiver definido funções e regras no serviço Power BI, tem de recriar essas funções no Power BI Desktop e publicar o relatório no serviço. Saiba mais sobre as opções para [RLS no serviço Power BI](../admin/service-admin-rls.md).

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Próximas etapas

[Segurança ao nível da linha (RLS) com o serviço Power BI](../admin/service-admin-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/).