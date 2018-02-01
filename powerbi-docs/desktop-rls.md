---
title: "Compreender a segurança ao nível da linha (RLS) com o Power BI Desktop"
description: "Como configurar a segurança ao nível da linha para conjuntos de dados importados, e DirectQuery, no Power BI Desktop."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maghan
ms.openlocfilehash: fccb2094158ed2dffaa0a80cc5609dfbf382be30
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Segurança ao nível da linha (RLS) com o Power BI Desktop
A segurança ao nível da linha (RLS) com o Power BI Desktop pode ser utilizada para restringir o acesso a dados para determinados utilizadores. Os filtros restringem os dados ao nível da linha. Pode definir filtros nas funções.

Pode agora configurar a RLS para os modelos de dados importados para o Power BI com o Power BI Desktop. Também pode configurar a RLS em conjuntos de dados que utilizem o DirectQuery, como o SQL Server. Anteriormente, só era possível implementar a RLS em modelos dos Analysis Services no local fora do Power BI. Para as ligações em direto dos Analysis Services, configure a segurança ao nível da linha no modelo no local. A opção de segurança não vai ser apresentada para conjuntos de dados de ligação em direto.

> [!IMPORTANT]
> Se definiu funções/regras no serviço Power BI, precisa de recriar essas funções no Power BI Desktop e publicar o relatório no serviço.
> 
> 

Saiba mais sobre as opções para [RLS no Serviço Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Passos seguintes
[Segurança ao nível da linha (RLS) com o serviço Power BI](service-admin-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

