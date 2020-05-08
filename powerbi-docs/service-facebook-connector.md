---
title: 'Serviço de terceiros: Facebook connector for Power BI Desktop'
description: 'Serviço de terceiros: Facebook connector for Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "77527708"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Utilizar o conector do Facebook para o Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende do Graph API do Facebook. Como tal, as funcionalidades e disponibilidade podem variar ao longo do tempo.

Pode ver um [tutorial sobre o conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Aviso de descontinuação do conector de dados do Facebook**: as funcionalidades de importação e atualização de dados do Facebook no Excel deixarão de funcionar corretamente a partir de abril de 2020. Até lá, pode utilizar o conector do Facebook *Obter e Transformar (Power Query)* . Após essa data, não conseguirá ligar ao Facebook e receberá uma mensagem de erro. Recomendamos a revisão ou remoção de quaisquer consultas existentes de *Obter e Transformar (Power Query)* que utilizem o conector do Facebook o mais rapidamente possível para evitar resultados inesperados.


A 30 de abril de 2015, o Facebook expirou a v1.0 da sua Graph API. O Power BI utiliza a Graph API nos bastidores para o conector do Facebook, permitindo que se ligue aos seus dados e os analise.

As consultas que foram criadas antes de 30 de maio de 2015 podem não funcionar ou devolver menos dados. Após 30 de abril de 2015, o Power BI utiliza a v2.8 em todas as chamadas para a API do Facebook. Se a consulta tiver sido criada antes de 30 de abril de 2015 e não a tiver utilizado, provavelmente precisa de autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, o API pode ser alterado de forma que afeta os resultados das consultas que gerarmos. Nalguns casos, determinadas consultas podem já não ser suportadas. Devido a esta dependência, não podemos garantir os resultados das suas consultas ao usar este conector.

Mais detalhes sobre a alteração no API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

