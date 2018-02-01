---
title: "Configurar definições de proxy para o gateway de dados no local"
description: "Informações relativas à configuração de definições de proxy para o gateway de dados no local."
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
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 11/21/2017
ms.author: davidi
ms.openlocfilehash: 1598a2580c24623abc1bbb5fb5a3590ab0f2a6f6
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/23/2017
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Configurar definições de proxy para o gateway de dados no local
O seu ambiente de trabalho pode requerer que passe por um proxy para aceder à Internet. Isto poderá impedir o gateway de dados no local de se ligar ao serviço.

## <a name="does-your-network-use-a-proxy"></a>A sua rede utiliza um proxy?
A seguinte publicação em superuser.com debate como pode tentar determinar se tem um proxy na sua rede.

[How do I know what proxy server I'm using? (Como posso saber que servidor de proxy estou a utilizar? - em inglês) (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Configuração predefinida e localização do ficheiro de configuração
As informações de proxy são configuradas num ficheiro de configuração .NET. A localização e os nomes de ficheiros variam consoante o gateway que está a utilizar.

### <a name="on-premises-data-gateway"></a>Gateway de dados local
Existem dois ficheiros de configuração principais envolvidos no gateway de dados no local.

**Configuração**

O primeiro destina-se aos ecrãs de configuração que configuram efetivamente o gateway. Se estiver a ter problemas na configuração do gateway, é este o ficheiro que deve ver.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Serviço Windows**

O segundo é relativo ao serviço Windows que interage com o serviço Power BI e processa os pedidos.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>Definir configurações de proxy
A configuração de proxy predefinida é a seguinte.

    <system.net>
        <defaultProxy useDefaultCredentials="true" />
    </system.net>

A configuração de proxy predefinida é compatível com a autenticação do Windows. Se o seu proxy utiliza outra forma de autenticação, tem de alterar as definições. Se não souber, deverá contactar o seu administrador de rede.

Para saber mais sobre a configuração dos elementos proxy para os ficheiros de configuração .NET, consulte [defaultProxy Element (Network Settings) (Elemento defaultProxy (Definições de Rede) - em inglês)](https://msdn.microsoft.com/library/kd3cf2ex.aspx).

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Alterar a conta de serviço do gateway para um utilizador de domínio
Ao configurar as definições de proxy para utilizar as credenciais predefinidas, conforme anteriormente explicado, poderá encontrar problemas de autenticação no proxy. Isto deve-se ao facto de a conta de serviço predefinida ser o SID de Serviço, e não um utilizador de domínio autenticado. Pode alterar a conta de serviço do gateway para permitir uma devida autenticação com o seu proxy.

> [!NOTE]
> Recomenda-se que utilize uma conta de serviço gerida para evitar ter de repor palavras-passe. Saiba como criar uma [conta de serviço gerida](https://technet.microsoft.com/library/dd548356.aspx) no Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Alterar a conta de serviço do gateway de dados no local
1. Altere a conta de serviço do Windows para o **serviço de gateway de dados no local**.
   
    A conta predefinida deste serviço é *NT SERVICE\PBIEgwService*. Deverá alterá-la para uma conta de utilizador de domínio no seu domínio do Active Directory. Em alternativa, deverá utilizar uma conta de serviço gerida para evitar ter de alterar a palavra-passe.
   
    Deverá alterar a conta no separador **Iniciar Sessão** nas propriedades do serviço Windows.
2. Reinicie o **serviço de gateway de dados no local**.
   
    Numa linha de comandos de administrador, emita os seguintes comandos.
   
        net stop PBIEgwService
   
        net start PBIEgwService
3. Inicie o **configurador do gateway de dados no local**. Pode selecionar o botão de início Windows e procurar *gateway de dados no local*.
4. Iniciar sessão no Power BI.
5. Restaure o gateway utilizando a sua chave de recuperação.
   
    Isto irá permitir que a nova conta de serviço consiga desencriptar credenciais armazenadas para origens de dados.

## <a name="next-steps"></a>Próximos passos
[Gateway de dados no local (modo pessoal)](service-gateway-personal-mode.md)
[Informações de firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
