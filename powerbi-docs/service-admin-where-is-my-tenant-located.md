---
title: Onde está localizado o meu inquilino do Power BI?
description: Saiba onde está localizado o seu inquilino do Power BI e como essa localização é selecionada. Isto é importante para saber porque é que pode afetar as interações com o serviço.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 3f12e6f0b54f85ebd626b2bd35bf1a03d513c17a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873332"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado o meu inquilino do Power BI?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Saiba onde está localizado o seu inquilino do Power BI e como essa localização é selecionada. É importante saber a localização, uma vez que pode afetar as interações com o serviço.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Como determinar onde está localizado o inquilino do Power BI

Para localizar a região na qual está o seu inquilino, siga estes passos.

1. No serviço Power BI, no menu superior, selecione ajuda ( **?** ) e, em seguida, **Acerca do Power BI**.

1. Procure o valor junto a **Os dados estão armazenados em**. É a região onde está localizado o seu inquilino. O valor é também a região onde os seus dados são armazenados, a menos que esteja a utilizar capacidades dedicadas em regiões diferentes para as suas áreas de trabalho.

    ![Região de dados](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Como é selecionada a região de dados

A região de dados baseia-se no país que selecionar ao criar o inquilino. A seleção aplica-se à inscrição tanto no Office 365 como no Power BI, uma vez que esta informação é partilhada. Se se tratar de um novo inquilino, selecione o país adequado na lista quando realizar a inscrição.

![Seleção do país](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

O Power BI escolha a região de dados mais próxima da sua seleção, que determina onde os dados são armazenados para o seu inquilino.

> [!IMPORTANT]
> Não pode alterar a seleção depois de criar o inquilino.

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

