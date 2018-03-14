---
title: "Serviço de terceiros: conector do Facebook para o Power BI Desktop"
description: "Serviço de terceiros: conector do Facebook para o Power BI Desktop"
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
ms.date: 02/22/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 894791ddc4eb632ad4dc0ee55f19bbadad5e28d6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Facebook connector for Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende da Graph API do Facebook. Como tal, as funcionalidades e disponibilidade podem variar ao longo do tempo.

Pode ver um [tutorial sobre o conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

A 30 de abril<sup>de</sup> 2015, o Facebook expirou a v1.0 da sua Graph API. O Power BI utiliza a Graph API nos bastidores para o conector do Facebook, permitindo que se ligue aos seus dados e os analise.

As consultas que foram criadas antes de 30 de maio<sup> </sup>de 2015 podem não funcionar ou devolver menos dados. Após 30 de abril<sup> </sup>de 2015, o Power BI utiliza a v2.8 em todas as chamadas para a API do Facebook. Se a consulta tiver sido criada antes de 30 de abril de 2015 e não a tiver utilizado, provavelmente precisa de autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, a API pode ser alterada de forma que afeta os resultados das consultas que gerarmos. Nalguns casos, determinadas consultas podem já não ser suportadas. Devido a essa dependência não podemos garantir os resultados das suas consultas ao utilizar esse conector.

Mais detalhes sobre a alteração na API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

