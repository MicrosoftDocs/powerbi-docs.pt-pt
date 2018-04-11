---
title: Onde está localizado o meu inquilino do Power BI?
description: Saiba onde está localizado o seu inquilino do Power BI e como essa localização é selecionada. Isto é importante para compreender como pode afetar as interações com o serviço.
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 22b5319cf95beb3ea4a4a498c7174a701e56fb95
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2018
---
# <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado o meu inquilino do Power BI?
<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Saiba onde está localizado o seu inquilino do Power BI e como essa localização é selecionada. Isto é importante para compreender como pode afetar as interações com o serviço.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Como determinar onde está localizado o inquilino do Power BI
Para localizar a região do seu inquilino, pode fazer o seguinte.

1. Selecione o **?** no serviço Power BI.
2. Selecione **Acerca do Power BI**.
3. Procure o valor junto a **Os dados estão armazenados em**. Esta é a região onde está localizado.

![](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Como é selecionada a região de dados
A região de dados baseia-se no país selecionado quando o inquilino foi criado pela primeira vez. Isto aplica-se à inscrição no Office 365 além do Power BI, uma vez que esta informação é partilhada. Se se tratar de um novo inquilino, quando se inscrever, verá uma lista pendente de países.

![](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Isto seleciona a localização de armazenamento dos dados. O Power BI irá escolher a região de dados mais próxima desta seleção.

> [!WARNING]
> Não é possível alterar esta seleção!
> 
> 

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

