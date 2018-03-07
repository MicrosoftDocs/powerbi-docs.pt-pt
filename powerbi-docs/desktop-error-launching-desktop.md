---
title: Resolver Problemas ao iniciar o Power BI Desktop
description: Resolver Problemas ao iniciar o Power BI Desktop
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6d5e4592d1bf041672f89dd38f03ddc6ff196735
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Resolver Problemas quando o Power BI Desktop não é iniciado
No **Power BI Desktop**, os utilizadores que instalaram e estão a executar versões anteriores do **gateway de dados no local do Power BI** podem ser impedidos de iniciar o Power BI Desktop, devido às restrições de políticas administrativas que o gateway de dados no local do Power BI estabeleceu nos pipes nomeados no computador local. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Resolver problemas no gateway de dados no local e no Power BI Desktop
Existem três opções para resolver o problema associado ao gateway de dados no local e permitir a inicialização do Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Resolução 1: instalar a versão mais recente do gateway de dados no local do Power BI
A versão mais recente do gateway de dados no local do Power BI não coloca restrições de pipe nomeado no computador local e permite que o Power BI Desktop seja iniciado corretamente. Se precisar de continuar a utilizar o gateway de dados no local do Power BI, esta é a resolução recomendada. Pode transferir a versão mais recente do gateway de dados no local do Power BI [nesta localização](https://go.microsoft.com/fwlink/?LinkId=698863). Veja que a ligação é uma ligação de transferência direta para o executável da instalação.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Resolução 2: desinstalar ou interromper o serviço Windows do gateway de dados no local do Power BI
Se já não precisar do gateway de dados no local do Power BI, é possível desinstalá-lo ou interromper o serviço Windows do gateway de dados no local do Power BI, que remove a restrição de política e permite que o Power BI Desktop seja iniciado.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Resolução 3: executar o Power BI Desktop com privilégios de administrador
Como alternativa, pode iniciar o Power BI Desktop como administrador, o que também permite que seja iniciado com êxito. Ainda é recomendável que instale a versão mais recente do gateway de dados no local do Power BI, conforme descrito anteriormente neste artigo.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Ajuda com outros problemas ao iniciar o Power BI Desktop
Esforçamo-os por cobrir o máximo possível de problemas que ocorram com o **Power BI Desktop**. Estamos regularmente à procura de problemas que possam afetar muitos clientes para incluí-los nos nossos artigos.

Se o problema em iniciar o **Power BI Desktop** não estiver associado ao gateway de dados no local, ou quando as resoluções anteriores não funcionarem, pode enviar um incidente de suporte ao [suporte do Power BI](https://support.powerbi.com) (https://support.powerbi.com) para ajudar a identificar e resolver o seu problema.

Para outros problemas que possa encontrar futuramente no **Power BI Desktop** (que esperamos que sejam muito poucos ou nenhuns), é útil ativar o rastreio e reunir ficheiros de registo, para ajudar a isolar e identificar o problema. Para ativar o rastreio, selecione **Ficheiro > Opções e definições > Opções** selecione **Diagnóstico** e, em seguida, marque a opção **Ativar o rastreio** em *Opções de Diagnóstico*. Compreendemos que o **Power BI Desktop** tem de estar em execução para definir esta opção, que é mais útil para futuros problemas associados à inicialização do **Power BI Desktop**.

