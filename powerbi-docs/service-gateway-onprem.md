---
title: Gateway de dados local
description: "Esta é uma descrição geral do gateway de dados no local para o Power BI. Pode utilizar este gateway para trabalhar com origens de dados de DirectQuery. Também pode utilizar este gateway para atualizar os conjuntos de dados na cloud com dados no local."
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
ms.date: 01/10/2018
ms.author: davidi
ms.openlocfilehash: 0e0ad501ed809fc1f7cd8cc66d7f5d13badf7d15
ms.sourcegitcommit: afd6e9e6f8b192b26486cd04d2cbc9de046911b3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2018
---
# <a name="on-premises-data-gateway"></a>Gateway de dados local
O gateway de dados no local funciona como uma ponte ao proporcionar a transferência rápida e segura de dados entre dados no local (dados que não estão na cloud) e os serviços do Power BI, Microsoft Flow, Logic Apps e PowerApps.

Pode utilizar um único gateway com diferentes serviços em simultâneo. Se estiver a utilizar o Power BI, bem como o PowerApps, pode utilizar um único gateway para ambos. Depende da conta com que inicia sessão.

> [!NOTE]
> O gateway de dados no local implementa a compressão de dados e a encriptação de transporte em todos os modos.
> 
> 

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Limitações das ligações em direto do Analysis Services
Pode utilizar uma ligação em direto para instâncias em tabela ou multidimensionais.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 |SKU Standard ou superior |

* As funcionalidades de conversão e Formatação ao nível da célula não são suportadas.
* As Ações e os Conjuntos com Nome não são expostos ao Power BI, mas pode ligar a cubos multidimensionais que também contêm Ações ou Conjuntos com Nome e criar elementos visuais e relatórios.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>Transferir e instalar o gateway de dados no local
Para transferir o gateway, selecione **Gateway de Dados** no menu Transferências. Transfira o [gateway de dados no local](http://go.microsoft.com/fwlink/?LinkID=820925).

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>Instalar o gateway no modo pessoal
> [!NOTE]
> O modo Pessoal só irá funcionar com o Power BI.
> 
> 

Após a instalação do gateway pessoal, terá de iniciar o **Assistente de Configuração do Power BI Gateway - Personal**.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Em seguida, terá de iniciar sessão no Power BI para registar o gateway no serviço cloud.

![](media/service-gateway-onprem/personal-gateway-signin.png)

Também terá de fornecer o nome de utilizador e a palavra-passe do Windows com os quais o serviço Windows será executado. Pode especificar uma conta Windows diferente da sua própria conta. O serviço do gateway será executado através dessa conta.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

Após a conclusão da instalação, terá de aceder aos seus conjuntos de dados no Power BI e certificar-se de que as credenciais são introduzidas para as origens de dados no local.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Armazenar credenciais encriptadas na cloud
Quando adiciona uma origem de dados ao gateway, é necessário fornecer credenciais para essa origem de dados. Todas as consultas à origem de dados serão executadas com essas credenciais. As credenciais são encriptadas com segurança, com a encriptação assimétrica, para que não possam ser desencriptadas na cloud antes de serem armazenadas na cloud. As credenciais são enviadas para o computador que executa o gateway no local, onde são desencriptadas quando as origens de dados são acedidas.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="troubleshooting"></a>Resolução de problemas
Se tiver problemas ao instalar e configurar um gateway, veja [Resolver problemas do gateway de dados no local](service-gateway-onprem-tshoot.md). Se pensa que está a ter um problema com a firewall, veja a secção [firewall ou proxy](service-gateway-onprem-tshoot.md#firewall-or-proxy) do artigo de resolução de problemas.

Se pensa que está a ter problemas de proxy, com o gateway, veja [Configurar definições de proxy para os gateways do Power BI](service-gateway-proxy.md).

## <a name="next-steps"></a>Próximos passos
[Gerir a sua origem de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gerir a sua origem de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gerir a sua origem de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gerir a sua origem de dados – Oracle](service-gateway-onprem-manage-oracle.md)  
[Gerir a sua origem de dados - Atualização Importada/Agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  
[Gateway de dados no local detalhado](service-gateway-onprem-indepth.md)  
[Gateway de dados local (modo pessoal) - a nova versão do gateway pessoal](service-gateway-personal-mode.md)
[Configurar as definições de proxy para os gateways de dados no local](service-gateway-proxy.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

