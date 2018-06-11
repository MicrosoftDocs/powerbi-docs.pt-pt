---
title: Configurar as definições de proxy do Gateway de dados no local
description: Informações relativas à configuração das definições de proxy do Gateway de dados no local.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: ef554d7190709565610336169b4883d71970f822
ms.sourcegitcommit: b25ae650643b0a62f33d7c1741307137b9cec316
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34799562"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Configurar as definições de proxy do Gateway de dados no local
O seu ambiente de trabalho pode requerer que passe por um proxy para aceder à Internet. Esta configuração poderá impedir o Gateway de dados no local de se ligar ao serviço.

## <a name="does-your-network-use-a-proxy"></a>A sua rede utiliza um proxy?
A seguinte publicação em superuser.com debate como pode tentar determinar se tem um proxy na sua rede.

[How do I know what proxy server I'm using? (Como posso saber que servidor de proxy estou a utilizar? - em inglês) (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Configuração predefinida e localização do ficheiro de configuração
As informações de proxy são configuradas num ficheiro de configuração .NET. A localização e os nomes de ficheiros variam consoante o gateway que está a utilizar.

### <a name="on-premises-data-gateway"></a>Gateway de dados local
Existem dois ficheiros de configuração principais envolvidos no Gateway de dados no local.

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

A configuração de proxy predefinida é compatível com a autenticação do Windows. Se o seu proxy utiliza outra forma de autenticação, tem de alterar as definições. Se não souber, deverá contactar o seu administrador de rede. Não é recomendada a autenticação de proxy básica. A tentativa de utilização da autenticação de proxy básica pode causar erros de autenticação de proxy e resultar na configuração incorreta do gateway. Utilize um mecanismo de autenticação de proxy mais forte para resolver este erro.

Além de utilizar credenciais predefinidas, pode adicionar um elemento <proxy> para determinar as definições do servidor proxy de forma mais específica. Por exemplo, pode especificar que o seu gateway de dados no local deve utilizar sempre o proxy, mesmo para recursos locais, ao definir o parâmetro bypassonlocal como "false". Isto pode ajudar em situações de resolução de problemas, se quiser controlar todos os pedidos https provenientes de um gateway de dados no local, nos ficheiros de registo do proxy. A seguinte configuração de exemplo especifica que todos os pedidos têm de passar por um proxy com o endereço IP 192.168.1.10.

    <system.net>
        <defaultProxy useDefaultCredentials="true">
            <proxy  
                autoDetect="false"  
                proxyaddress="http://192.168.1.10:3128"  
                bypassonlocal="false"  
                usesystemdefault="true"
            />  
        </defaultProxy>
    </system.net>

Para saber mais sobre a configuração dos elementos proxy para os ficheiros de configuração .NET, consulte [defaultProxy Element (Network Settings) (Elemento defaultProxy (Definições de Rede) - em inglês)](https://msdn.microsoft.com/library/kd3cf2ex.aspx).

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Alterar a conta de serviço do gateway para um utilizador de domínio
Ao configurar as definições de proxy para utilizar as credenciais predefinidas, conforme anteriormente explicado, poderá encontrar problemas de autenticação no proxy. Isto deve-se ao facto de a conta de serviço predefinida ser o SID de Serviço, e não um utilizador de domínio autenticado. Pode alterar a conta de serviço do gateway para permitir uma devida autenticação com o seu proxy.

> [!NOTE]
> Recomenda-se que utilize uma conta de serviço gerida para evitar ter de repor palavras-passe. Saiba como criar uma [conta de serviço gerida](https://technet.microsoft.com/library/dd548356.aspx) no Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Alterar a conta de serviço do Gateway de dados no local
1. Altere a conta de serviço do Windows para o **serviço de Gateway de dados no local**.
   
    A conta predefinida deste serviço é *NT SERVICE\PBIEgwService*. Deverá alterá-la para uma conta de utilizador de domínio no seu domínio do Active Directory. Em alternativa, deverá utilizar uma conta de serviço gerida para evitar ter de alterar a palavra-passe.
   
    Deverá alterar a conta no separador **Iniciar Sessão** nas propriedades do serviço Windows.
2. Reinicie o **serviço de Gateway de dados no local**.
   
    Numa linha de comandos de administrador, emita os seguintes comandos.
   
        net stop PBIEgwService
   
        net start PBIEgwService
3. Inicie o **configurador do Gateway de dados no local**. Pode selecionar o botão de início Windows e procurar *Gateway de dados no local*.
4. Inicie sessão no Power BI.
5. Restaure o gateway utilizando a sua chave de recuperação.
   
    Isto irá permitir que a nova conta de serviço consiga desencriptar credenciais armazenadas para origens de dados.
    
> [!NOTE]
> Quando altera a conta de serviço diretamente com o painel de Controlo de Serviços, as ACLs não são atualizadas automaticamente. Tem de garantir que a nova conta de serviço tem acesso à pasta e aos ficheiros de instalação. Pode encontrar a pasta de Instalação do Gateway em C:\Programas\On-premises data gateway. 
> 

## <a name="next-steps"></a>Próximos passos
[Gateway de dados no local (modo pessoal)](service-gateway-personal-mode.md)
[Informações de firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

