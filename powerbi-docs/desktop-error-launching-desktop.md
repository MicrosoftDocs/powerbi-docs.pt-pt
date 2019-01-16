---
title: Resolver Problemas ao iniciar o Power BI Desktop
description: Resolver Problemas ao iniciar o Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f527fa17ab242f6835ca99a3ff3ef3e2525a001f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277141"
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Resolver Problemas quando o Power BI Desktop não é iniciado
No **Power BI Desktop**, os utilizadores que instalaram e estão a executar versões anteriores do **Gateway de dados no local do Power BI** podem ser impedidos de iniciar o Power BI Desktop, devido às restrições de políticas administrativas que o gateway no local do Power BI estabeleceu nos pipes nomeados no computador local. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Resolver problemas no Gateway de dados no local e no Power BI Desktop
Existem três opções para resolver o problema associado ao Gateway de dados no local e permitir a inicialização do Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Resolução 1: instalar a versão mais recente do Gateway de dados no local do Power BI
A versão mais recente do Gateway de dados no local do Power BI não coloca restrições de pipe nomeado no computador local e permite que o Power BI Desktop seja iniciado corretamente. Se precisar de continuar a utilizar o Gateway de dados no local do Power BI, esta é a resolução recomendada. Pode transferir a versão mais recente do Gateway de dados no local do Power BI [nesta localização](https://go.microsoft.com/fwlink/?LinkId=698863). Veja que a ligação é uma ligação de transferência direta para o executável da instalação.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Resolução 2: desinstalar ou interromper o serviço Windows do Gateway de dados no local do Power BI
Se já não precisar do Gateway de dados no local do Power BI, é possível desinstalá-lo ou interromper o serviço Windows do Gateway de dados no local do Power BI, que remove a restrição de política e permite que o Power BI Desktop seja iniciado.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Resolução 3: executar o Power BI Desktop com privilégios de administrador
Como alternativa, pode iniciar o Power BI Desktop como administrador, o que também permite que seja iniciado com êxito. Ainda é recomendável que instale a versão mais recente do Gateway de dados no local do Power BI, conforme descrito anteriormente neste artigo.

É importante ter em atenção que o Power BI Desktop foi projetado como uma arquitetura com multiprocessos e vários desses processos comunicam através de pipes nomeados do Windows. Poderão existir outros processos que interferem com esses pipes nomeados. A razão mais comum para essa interferência é a segurança, incluindo situações em que o software antivírus ou as firewalls poderão estar a bloquear os pipes ou a redirecionar o tráfego para uma porta específica. Iniciar o Power BI Desktop com privilégios de administrador pode resolver este problema. Se não for possível iniciar com privilégios de administrador, contacte o seu administrador para determinar as regras de segurança aplicadas que impedem os pipes nomeados de comunicar devidamente e para colocar o Power BI Desktop e os seus subprocessos na lista de permissões.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Resolver problemas ao ligar ao SQL Server
Se obtiver uma mensagem de erro semelhante à seguinte, ao ligar a uma base de dados SQL Server, pode frequentemente resolver o problema ao iniciar o **Power BI Desktop** como administrador e, em seguida, efetuar a ligação do SQL Server:

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

Após iniciar como administrador e estabelecer a ligação, os DLLs necessários são registados corretamente. Depois disso, iniciar o Power BI Desktop como administrador não é necessário.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Ajuda com outros problemas ao iniciar o Power BI Desktop
Esforçamo-os por cobrir o máximo possível de problemas que ocorram com o **Power BI Desktop**. Estamos regularmente à procura de problemas que possam afetar muitos clientes para incluí-los nos nossos artigos.

Se o problema em iniciar o **Power BI Desktop** não estiver associado ao Gateway de dados no local ou quando as resoluções anteriores não funcionarem, poderá enviar um incidente de suporte ao [suporte do Power BI](https://support.powerbi.com) (https://support.powerbi.com)) para ajudar a identificar e resolver o problema.

Para outros problemas que possa encontrar futuramente no **Power BI Desktop** (que esperamos que sejam muito poucos ou nenhuns), é útil ativar o rastreio e reunir ficheiros de registo, para ajudar a isolar e identificar o problema. Para ativar o rastreio, selecione **Ficheiro > Opções e definições > Opções** selecione **Diagnóstico** e, em seguida, marque a opção **Ativar o rastreio** em *Opções de Diagnóstico*. Compreendemos que o **Power BI Desktop** tem de estar em execução para definir esta opção, que é mais útil para futuros problemas associados à inicialização do **Power BI Desktop**.

