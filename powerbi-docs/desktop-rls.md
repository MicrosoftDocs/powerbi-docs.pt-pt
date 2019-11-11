---
title: Compreender a segurança ao nível da linha (RLS) com o Power BI Desktop
description: Como configurar a segurança ao nível da linha para conjuntos de dados importados, e DirectQuery, no Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 08/14/2019
LocalizationGroup: Create reports
ms.openlocfilehash: d3c3310b6fd60d0e6f30eabd4c5136af5b8c54ff
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73866025"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Segurança ao nível da linha (RLS) com o Power BI Desktop

Pode utilizar a segurança ao nível da linha (RLS) com o Power BI Desktop para restringir o acesso a dados para determinados utilizadores. Os filtros restringem os dados ao nível da linha. Pode definir filtros nas funções.

Pode agora configurar a RLS para os modelos de dados importados para o Power BI com o Power BI Desktop. Também pode configurar a RLS em conjuntos de dados que utilizem o [DirectQuery](desktop-use-directquery.md), como o SQL Server. Anteriormente, só era possível implementar a RLS em modelos do Analysis Services no local fora do Power BI. Para as ligações em direto dos Analysis Services, configure a segurança ao nível da linha no modelo no local. A opção de segurança não é apresentada para conjuntos de dados de ligação em direto.

> [!IMPORTANT]
> Se tiver definido funções e regras no serviço Power BI, tem de recriar essas funções no Power BI Desktop e publicar o relatório no serviço.

Saiba mais sobre as opções para [RLS no Serviço Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Passos seguintes

[Segurança ao nível da linha (RLS) com o serviço Power BI](service-admin-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)