---
title: Recolher informações de diagnóstico adicionais
description: Estas instruções fornecem duas opções possíveis para recolher manualmente informações de diagnóstico adicionais do cliente Web do Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 670373afb5cb890c87a24a129cd43fde7bd5d892
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83128866"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Recolher informações de diagnóstico adicionais para o Power BI

Este artigo fornece instruções para recolher manualmente informações de diagnóstico adicionais do cliente Web do Power BI.

1. Navegue até ao [Power BI](https://app.powerbi.com) com o Microsoft Edge ou o Internet Explorer.

1. Prima **F12** para abrir as ferramentas de programador do Microsoft Edge.

   ![Captura de ecrã do separador Elementos das ferramentas de Programador do Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selecione o separador **Network** (Rede). Este irá listar o tráfego já capturado.

   ![Captura de ecrã do separador Rede das ferramentas de Programador do Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Pode:

    * Procure dentro da janela e reproduza qualquer problema que possa encontrar.

    * Oculte e mostre a janela de ferramentas de programador, em qualquer altura durante a sessão, ao premir F12.

1. Para parar a criação de perfis da sessão, pode selecionar o quadrado vermelho no separador **Rede** da área de ferramentas de programador.

   ![Captura de ecrã do separador Rede das ferramentas de programador do Microsoft Edge com uma chamada do botão Parar.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Selecione o ícone de disquete para exportar os dados como um ficheiro de HTTP Archive (HAR).

   ![Captura de ecrã do separador Rede das ferramentas de programador do Microsoft Edge com uma chamada do ícone da disquete.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Escreva um nome de ficheiro e guarde o ficheiro HAR.

    O ficheiro HAR conterá todas as informações sobre pedidos de rede entre a janela do navegador e o Power BI, incluindo:

    * Os IDs de atividade para cada pedido.

    * O carimbo de data/hora preciso para cada pedido.

    * Quaisquer informações de erro devolvidas ao cliente.

    Este rastreio também conterá os dados utilizados para povoar os elementos visuais mostrados no ecrã.

1. Pode enviar o ficheiro HAR para o suporte para revisão.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
