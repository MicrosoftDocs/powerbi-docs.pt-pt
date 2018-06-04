---
title: Capturar informações de diagnóstico adicionais
description: Capturar informações de diagnóstico adicionais
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 76860e740d43a1907692a7cd4fed1a6df68c93d4
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34239228"
---
# <a name="capturing-additional-diagnostic-information"></a>Capturar informações de diagnóstico adicionais
## <a name="capturing-additional-diagnostic-information-for-power-bi"></a>Capturar Informações de Diagnóstico Adicionais para o Power BI
Estas instruções fornecem duas opções possíveis para recolher manualmente informações de diagnóstico adicionais do cliente Web do Power BI.  Apenas uma dessas opções tem de ser seguida.

## <a name="network-capture---edge--internet-explorer"></a>Captura de rede – Edge e Internet Explorer 11
1. Navegue até ao [Power BI](https://app.powerbi.com) com o Microsoft Edge ou o Internet Explorer.
2. Abra as ferramentas de programador do Edge, premindo F12.
3. Isso abrirá a janela de ferramentas de programador: 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)
4. Mude para o separador Rede. Este irá listar o tráfego já capturado. 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)
5. Pode procurar dentro da janela e reproduzir qualquer problema que possa encontrar. Pode ocultar e mostrar a janela de ferramentas de programador, em qualquer altura durante a sessão, premindo F12.
6. Para parar a captura, pode selecionar o quadrado vermelho no separador de rede da área de ferramentas de programador.
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)
7. No ícone de disquete, selecione **Exportar como HAR**
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)
8. Escreva um nome de ficheiro e guarde o ficheiro HAR.
   
    O ficheiro HAR conterá todas as informações sobre pedidos de rede entre a janela do navegador e o Power BI.  Isto incluirá os IDs de atividade de cada pedido, o carimbo de data/hora preciso de cada pedido e quaisquer informações de erro devolvidas ao cliente.  Este rastreio também conterá os dados utilizados para povoar os elementos visuais mostrados no ecrã.
9. Pode enviar o ficheiro HAR para o suporte para revisão.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

