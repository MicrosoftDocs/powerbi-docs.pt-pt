---
title: 'Serviço de terceiros: Facebook connector for Power BI Desktop'
description: 'Serviço de terceiros: Facebook connector for Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 644e68ec827915c5457e22e1c1486a8f6f3299f6
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2020
ms.locfileid: "73877045"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Facebook connector for Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende do Graph API do Facebook. Como tal, as funcionalidades e disponibilidade podem variar ao longo do tempo.

Pode ver um [tutorial sobre o conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

A 30 de abril de 2015, o Facebook expirou a v1.0 da sua Graph API. O Power BI utiliza a Graph API nos bastidores para o conector do Facebook, permitindo que se ligue aos seus dados e os analise.

As consultas que foram criadas antes de 30 de maio de 2015 podem não funcionar ou devolver menos dados. Após 30 de abril de 2015, o Power BI utiliza a v2.8 em todas as chamadas para a API do Facebook. Se a consulta tiver sido criada antes de 30 de abril de 2015 e não a tiver utilizado, provavelmente precisa de autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, o API pode ser alterado de forma que afeta os resultados das consultas que gerarmos. Nalguns casos, determinadas consultas podem já não ser suportadas. Devido a esta dependência, não podemos garantir os resultados das suas consultas ao usar este conector.

Mais detalhes sobre a alteração no API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

