---
title: Utilizar conectores de dados personalizados com o gateway de dados no local
description: Pode utilizar conectores de dados personalizados com o gateway de dados no local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 074a8dd876e0612f87c220f9fb077b60b2b85c88
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271820"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Utilizar conectores de dados personalizados com o gateway de dados no local

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Os Conectores de Dados do Power BI permitem-lhe ligar e aceder aos dados de uma aplicação, serviço ou origem de dados. Pode desenvolver conectores de dados personalizados e utilizá-los no Power BI Desktop.

Para saber mais sobre como desenvolver conectores de dados personalizados do Power BI, veja a [página do Conector de Dados SDK do GitHub](http://aka.ms/dataconnectors). Este site inclui informações de introdução e exemplos relativos ao Power BI e ao Power Query.

Ao criar relatórios no Power BI Desktop que utilizam conectores de dados personalizados, pode utilizar o gateway de dados no local para atualizar esses relatórios a partir do serviço Power BI.

## <a name="how-to-enable-and-use-this-capability"></a>Como ativar e utilizar esta funcionalidade

Quando instalar a versão de julho de 2018 do gateway de dados no local ou uma versão posterior, verá o separador **Conectores** na aplicação do gateway de dados no local com uma opção para selecionar uma pasta na qual pode carregar conectores personalizados. Certifique-se de que escolhe uma pasta que pode ser acedida pelo utilizador que está a executar o serviço de gateway (por predefinição, o serviço *NT SERVICE\PBIEgwService*). O gateway carrega automaticamente os ficheiros dos conectores personalizados localizados nessa pasta. Verá estes ficheiros na lista de conectores de dados.

![Conector personalizado 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Se estiver a utilizar o gateway de dados no local (modo pessoal), agora poderá carregar o seu relatório do Power BI para o serviço Power BI e utilizar o gateway para o atualizar.

No caso do gateway de dados no local, continua a precisar de criar uma origem de dados para o seu conector personalizado. Na página de definições do gateway no serviço Power BI, quando selecionar o cluster de gateway, deverá ver uma nova opção para permitir a utilização de conectores personalizados. Certifique-se de que todos os gateways no cluster têm a versão atualizada de julho de 2018 ou posterior para que esta opção esteja disponível. Agora, selecione a opção para ativar a utilização de conectores personalizados com este cluster.

![Conector personalizado 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Quando esta opção estiver ativada, verá os seus conectores personalizados como origens de dados disponíveis que pode criar neste cluster de gateway. Após criar uma origem de dados com o seu novo conector personalizado, poderá atualizar os relatórios do Power BI com esse conector no serviço Power BI.

![Conector personalizado 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Certifique-se de que a pasta que cria está acessível ao serviço de gateway em segundo plano. Normalmente, as pastas que se encontram na pasta Windows ou nas pastas de sistema do utilizador não estarão acessíveis. A aplicação do gateway de dados no local mostra uma mensagem se a pasta não estiver acessível (isto não se aplica à versão pessoal do gateway).
* Para que os conectores personalizados possam funcionar com o gateway de dados no local, é necessário que seja implementada uma secção "TestConnection" no código do conector personalizado. Isto não é necessário ao utilizar conectores com o Power BI Desktop. Por este motivo, pode ter um conector que funciona com o Power BI Desktop, mas não com o gateway. Consulte a seguinte [documentação](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) sobre como implementar uma secção TestConnection.

## <a name="next-steps"></a>Próximos passos

* [Gerir a sua origem de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gerir a sua origem de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gerir a sua origem de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gerir a sua origem de dados – Oracle](service-gateway-onprem-manage-oracle.md)  
* [Gerir a sua origem de dados - Atualização Importada/Agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  

* [Configurar as definições de proxy do gateway de dados no local](/data-integration/gateway/service-gateway-proxy)  
* [Utilizar o Kerberos para SSO (início de sessão único) do Power BI para origens de dados no local](service-gateway-sso-kerberos.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)
