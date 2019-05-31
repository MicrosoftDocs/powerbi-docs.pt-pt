---
title: Capturar informações de diagnóstico adicionais
description: Estas instruções fornecem duas opções possíveis para recolher manualmente informações de diagnóstico adicionais do cliente Web do Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100257"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Capturar informações de diagnóstico adicionais para o Power BI

Este artigo fornece instruções para recolher manualmente informações de diagnóstico adicionais do cliente de web do Power BI.

1. Navegue até [do Power BI](https://app.powerbi.com) com o Microsoft Edge ou o Internet Explorer.

1. Prima **F12** para abrir as ferramentas de desenvolvimento do Microsoft Edge.

   ![Guia de elementos de ferramentas de captura de ecrã do Microsoft Edge Developer.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selecione o separador **Network** (Rede). Este irá listar o tráfego já capturado.

   ![Guia de rede de ferramentas de captura de ecrã do Microsoft Edge Developer.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Pode:

    * Procurar dentro da janela e reproduzir qualquer problema que pode encontrar.

    * Ocultar e mostrar a janela de ferramentas de desenvolvedor em qualquer altura durante a sessão, premindo F12.

1. Para parar a sessão de criação de perfis, pode selecionar o quadrado vermelho na **rede** Guia do programador da área de ferramentas.

   ![Guia de rede de ferramentas de captura de ecrã do Microsoft Edge Developer com uma chamada fora o botão Parar.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Selecione o ícone de disquete, exportar os dados como um ficheiro de arquivo (HAR de HTTP).

   ![Guia de rede de ferramentas de captura de ecrã do Microsoft Edge Developer com uma nota de aviso do ícone diskette.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Escreva um nome de ficheiro e guarde o ficheiro HAR.

    O ficheiro HAR conterá todas as informações sobre pedidos de rede entre a janela do browser e o Power BI, incluindo:

    * Os IDs de atividade para cada solicitação.

    * O período de tempo preciso para cada solicitação.

    * Qualquer informação de erro devolvida ao cliente.

    Este rastreio também conterá os dados utilizados para povoar os elementos visuais mostrados no ecrã.

1. Pode enviar o ficheiro HAR para o suporte para revisão.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
