---
title: Saída do Power BI e Azure
description: Compreenda os custos de saída do Azure e do Power BI com base na localização do inquilino e no Power BI Premium
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: b39812eb155d1d1c32ddba984986e5260f4b1ad1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302236"
---
# <a name="power-bi-and-azure-egress"></a>Saída do Power BI e Azure

Quando utilizar o Power BI com origens de dados do Azure, pode evitar custos de saída do Azure ao certificar-se de que o seu inquilino do Power BI se encontra na mesma região que as suas origens de dados do Azure.

Se o seu inquilino do Power BI for implementado na mesma região do Azure onde implementa as origens de dados, não irá incorrer em custos devido a atualizações agendadas e interações do DirectQuery. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Determinar onde está localizado o inquilino do Power BI

Para descobrir onde o seu inquilino do Power BI está localizado, veja o artigo [Onde está localizado o meu inquilino do Power BI](../admin/service-admin-where-is-my-tenant-located.md).

Para clientes do Multi-Geo no Power BI Premium, se o seu inquilino do Power BI não estiver na localização ideal para algumas das suas origens de dados com base no Azure, pode implementar o Multi-Geo no Power BI Premium na região do Azure pretendida e tirar partido da vantagem de ter o inquilino do Power BI e as origens de dados do Azure na mesma região do Azure.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o Power BI Premium ou a funcionalidade Multi-Geo, consulte os seguintes recursos:

* [O que é o Microsoft Power BI Premium?](../admin/service-premium-what-is.md)
* [Como comprar o Power BI Premium](../admin/service-admin-premium-purchase.md)
* [Suporte Multi-Geo para o Power BI Premium (Pré-visualização)](../admin/service-admin-premium-multi-geo.md)
* [Onde está localizado o meu inquilino do Power BI?](../admin/service-admin-where-is-my-tenant-located.md)
* [Perguntas Frequentes do Power BI Premium](../admin/service-premium-faq.md)
