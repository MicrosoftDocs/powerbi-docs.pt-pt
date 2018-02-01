---
title: 'Project Online: ligar aos dados a partir do Power BI Desktop'
description: 'Project Online: ligar aos dados a partir do Power BI Desktop'
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.openlocfilehash: c85262d14101900443eff276ce0471ba5c08322f
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="project-online-connect-to-data-through-power-bi-desktop"></a>Project Online: ligar aos dados a partir do Power BI Desktop
Pode ligar aos dados no Project Online a partir do Power BI Desktop.

### <a name="step-1-download-power-bi-desktop"></a>Passo 1: Transferir o Power BI Desktop
1. [Transfira o Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662) e, em seguida, execute o instalador para obter o **Power BI Desktop** no seu computador.

### <a name="step-2-connect-to-project-online-with-odata"></a>Passo 2: Ligar ao Project Online com o OData
1. Abra o **Power BI Desktop**.
2. No ecrã de *Boas-vindas*, selecione **Obter Dados**.
3. Selecione **Feed OData** e selecione **Ligar**.
4. Introduza o endereço para o feed OData na caixa URL e, em seguida, clique em OK.
   
   Se o endereço do seu site Project Web App for semelhante a https://\<nomeinquilino\>.sharepoint.com/sites/pwa, o endereço que vai introduzir para o Feed OData é https://\<nomeinquilino\>.sharepoint.com/sites/pwa/\_api/Projectdata.
   
   No nosso exemplo, vamos utilizar https://contoso.sharepoint.com/sites/pwa/default.aspx
5. O Power BI Desktop pedirá para se autenticar com a sua conta do Office 365. Selecione Conta organizacional e, em seguida, introduza as suas credenciais.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Aqui, pode escolher as tabelas às quais quer ligar e criar uma consulta.  Quer uma ideia de como começar?  A mensagem de blogue seguinte mostra como criar um gráfico de evolução com base nos dados do Project Online.  A mensagem de blogue refere-se à utilização do Power Query para ligar ao Project Online, mas isto aplica-se também ao Power BI Desktop.

[Criar gráficos burndown para o Project através do Power Pivot e do Power Query](http://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)
