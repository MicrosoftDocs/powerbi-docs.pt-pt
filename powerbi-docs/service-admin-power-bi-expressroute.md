---
title: Power BI e ExpressRoute
description: Power BI e ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0c4618150094a4eabb0dc9745e9ac93e4f342ff1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187900"
---
# <a name="power-bi-and-expressroute"></a>Power BI e ExpressRoute

O **ExpressRoute** é um serviço do Azure que permite criar ligações privadas entre datacenters do Azure (nos quais o Power BI reside) e a sua infraestrutura no local ou entre datacenters do Azure e o seu ambiente de colocação.

Com o **Power BI** e o **ExpressRoute**, pode criar uma ligação de rede privada entre a sua organização e o Power BI (ou através de um recurso de colocação de um ISP) ao ignorar a Internet para proteger melhor as ligações e os dados confidenciais do Power BI.

Para obter mais informações, veja [Descrição geral do ExpressRoute](/azure/expressroute/expressroute-introduction). O Power BI está em conformidade com o ExpressRoute, exceto em alguns casos nos quais o Power BI recebe ou envia dados pela Internet pública. Para obter uma lista dos URLs que o Power BI utiliza, veja [URLs do Power BI](power-bi-whitelist-urls.md).

![Diagrama do ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)