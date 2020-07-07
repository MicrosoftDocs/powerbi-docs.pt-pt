---
title: Restringir o acesso aos dados com segurança ao nível da linha (RLS) para o Power BI Desktop
description: Como configurar a segurança ao nível da linha para conjuntos de dados importados, e DirectQuery, no Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 9036967c826dee83847c3bc3d4a903bbe749b2ce
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238635"
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

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Segurança ao nível da linha (RLS) com o Power BI](../admin/service-admin-rls.md)
- [Orientação de segurança ao nível da linha (RLS) com o Power BI Desktop](../guidance/rls-guidance.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
