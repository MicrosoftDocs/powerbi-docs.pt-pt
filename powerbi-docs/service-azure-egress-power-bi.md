---
title: Saída do Power BI e Azure
description: Compreenda os custos de saída do Azure e do Power BI com base na localização do inquilino e no Power BI Premium
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: 720ef2f059c3c87be84c3d8db98e89400c161ad0
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514396"
---
# <a name="power-bi-and-azure-egress"></a>Saída do Power BI e Azure

Quando utilizar o Power BI com origens de dados do Azure, pode evitar custos de saída do Azure ao certificar-se de que o seu inquilino do Power BI se encontra na mesma região que as suas origens de dados do Azure.

Se o seu inquilino do Power BI for implementado na mesma região do Azure onde implementa as origens de dados, não irá incorrer em custos devido a atualizações agendadas e interações do DirectQuery. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Determinar onde está localizado o inquilino do Power BI

Para descobrir onde o seu inquilino do Power BI está localizado, veja o artigo [Onde está localizado o meu inquilino do Power BI](service-admin-where-is-my-tenant-located.md).

Para clientes do Multi-Geo no Power BI Premium, se o seu inquilino do Power BI não estiver na localização ideal para algumas das suas origens de dados com base no Azure, pode implementar o Multi-Geo no Power BI Premium na região do Azure pretendida e tirar partido da vantagem de ter o inquilino do Power BI e as origens de dados do Azure na mesma região do Azure.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o Power BI Premium ou a funcionalidade Multi-Geo, consulte os seguintes recursos:

* [O que é o Microsoft Power BI Premium?](service-premium-what-is.md)
* [Como comprar o Power BI Premium](service-admin-premium-purchase.md)
* [Suporte Multi-Geo para o Power BI Premium (Pré-visualização)](service-admin-premium-multi-geo.md)
* [Onde está localizado o meu inquilino do Power BI?](service-admin-where-is-my-tenant-located.md)
* [Perguntas Frequentes do Power BI Premium](service-premium-faq.md)


