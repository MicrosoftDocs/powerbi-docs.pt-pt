---
title: Resolução de problemas ao iniciar o Power BI Desktop
description: Resolução de problemas ao iniciar o Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 01/14/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 8d33973f1a11050d104399c98866fdae0ffb1f8a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404899"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Resolver problemas ao abrir o Power BI Desktop

No Power BI Desktop, os utilizadores que instalaram e estão a executar versões anteriores do *Gateway de dados no local do Power BI* podem ser impedidos de abrir o Power BI Desktop, devido às restrições de políticas administrativas que o Gateway no local do Power BI estabeleceu nos pipes nomeados no computador local.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Resolver problemas no Gateway de dados no local e no Power BI Desktop

Tem três opções para resolver o problema associado ao Gateway de dados no local e para permitir a abertura do Power BI Desktop:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Resolução 1: instalar a versão mais recente do Gateway de dados no local do Power BI

A versão mais recente do Gateway de dados no local do Power BI não coloca restrições aos pipes nomeados no computador local e permite que o Power BI Desktop abra corretamente. Se precisar de continuar a utilizar o Gateway de dados no local do Power BI, esta é a resolução recomendada para o atualizar. Pode transferir a [versão mais recente do Gateway de dados no local do Power BI](https://go.microsoft.com/fwlink/?LinkId=698863). Esta é uma ligação de transferência direta para o executável de instalação.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Resolução 2: desinstalar ou interromper o serviço Windows do Gateway de dados no local do Power BI

Poderá desinstalar o Gateway de dados no local do Power BI se não precisar mais dele. Em alternativa, pode interromper o serviço Microsoft do Gateway de dados no local do Power BI, que remove a restrição de política e permite que o Power BI Desktop seja aberto.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Resolução 3: executar o Power BI Desktop com privilégios de administrador

Por outro lado, pode iniciar o Power BI Desktop como administrador, o que também permite que seja aberto com êxito. Ainda é recomendável que instale a versão mais recente do Gateway de dados no local do Power BI, conforme descrito anteriormente.

O Power BI Desktop foi projetado como uma arquitetura com multiprocessos e vários desses processos comunicam através de pipes nomeados do Windows. Poderão existir outros processos que interferem com esses pipes nomeados. A razão mais comum para essa interferência é a segurança, incluindo situações em que o software antivírus ou as firewalls podem bloquear os pipes ou redirecionar o tráfego para uma porta específica. Abrir o Power BI Desktop com privilégios de administrador pode resolver esse problema. Se não conseguir abrir com privilégios de administrador, peça ao administrador para determinar quais as regras de segurança que estão a impedir que os pipes nomeados comuniquem corretamente. Em seguida, adicione o Power BI Desktop e os subprocessos à lista de permissões.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Resolver problemas ao ligar ao SQL Server

Quando tentar ligar a uma base de dados do SQL Server, poderá deparar-se com uma mensagem de erro semelhante à seguinte:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Geralmente, poderá resolver o problema se abrir o Power BI Desktop como administrador antes de fazer a ligação ao SQL Server.

Depois de abrir o Power BI Desktop como administrador e estabelecer a ligação, os DLLs necessários serão registados corretamente. Depois disso, não será necessário abrir o Power BI Desktop como administrador.

## <a name="get-help-with-other-launch-issues"></a>Obter ajuda com outros problemas de arranque

Esforçamo-nos por cobrir o máximo possível de problemas que ocorram com o Power BI Desktop. Estamos regularmente à procura de problemas que possam afetar muitos clientes para incluí-los nos nossos artigos.

Se o problema ao abrir o Power BI Desktop não estiver associado ao Gateway de dados no local ou quando as resoluções anteriores não funcionarem, poderá enviar um incidente de suporte ao *suporte do Power BI* (<https://support.powerbi.com>) para ajudar a identificar e resolver o problema.

Caso se depare com outros problemas no futuro com o Power BI Desktop, poderá ser útil ativar o rastreio e recolher ficheiros de registo. Os ficheiros de registo podem ajudar a isolar e identificar o problema. Para ativar o rastreio, selecione **Ficheiro** > **Opções e definições** > **Opções**, selecione **Diagnóstico** e, em seguida, selecione **Ativar rastreio**. O Power BI Desktop tem de estar em execução para definir esta opção, mas é útil para futuros problemas associados à abertura do Power BI Desktop.
