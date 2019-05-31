---
title: 'Serviço de terceiros: Facebook connector for Power BI Desktop'
description: 'Serviço de terceiros: Facebook connector for Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b02717c49a1207dfec39ebb1529e7e9b222fa62
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65512863"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Facebook connector for Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende do Graph API do Facebook. Como tal, as funcionalidades e disponibilidade podem variar ao longo do tempo.

Pode ver um [tutorial sobre o conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Facebook expirou a v1.0 da sua Graph API em 30 de Abril de 2015. O Power BI utiliza a Graph API nos bastidores para o conector do Facebook, permitindo que se ligue aos seus dados e os analise.

Consultas que foram criadas antes de 30 de Abril de 2015 já não podem funcionar ou devolver menos dados. Após 30 de Abril de 2015, Power BI utiliza a v2.8 em todas as chamadas à API do Facebook. Se a consulta tiver sido criada antes de 30 de abril de 2015 e não a tiver utilizado, provavelmente precisa de autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, o API pode ser alterado de forma que afeta os resultados das consultas que gerarmos. Nalguns casos, determinadas consultas podem já não ser suportadas. Devido a esta dependência não podemos garantir os resultados das suas consultas ao utilizar este conector.

Mais detalhes sobre a alteração no API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

