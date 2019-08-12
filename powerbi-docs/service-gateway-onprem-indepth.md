---
title: Gateway de dados no local detalhado
description: Este artigo analisa detalhadamente o gateway no local. É abordado o funcionamento do serviço com o Azure Active Directory e o Active Directory local quando é utilizado o Analysis Services
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 7d6948f7b5be25b7027a4aa2adaf244a2cde836a
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/02/2019
ms.locfileid: "68729953"
---
# <a name="on-premises-data-gateway-in-depth"></a>Gateway de dados no local detalhado

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Movemos as informações deste artigo para vários outros artigos no Power BI e em documentação geral. Siga as ligações abaixo de cada título para encontrar o conteúdo relevante.

## <a name="how-the-gateway-works"></a>Como funciona o gateway

Veja [Arquitetura de gateway de dados no local](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Relação dos tipos de origens de dados disponíveis

Veja [Manage data sources](service-gateway-data-sources.md) (Gerir origens de dados).

## <a name="authentication-to-on-premises-data-sources"></a>Autenticação em origens de dados no local

Veja [Autenticação em origens de dados no local](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticação numa origem de dados dinâmicos do Analysis Services

Veja [Autenticação numa origem de dados dinâmicos do Analysis Services](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Segurança baseada em funções

Veja [Segurança baseada em funções](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Row-level security

Veja [Segurança ao nível da linha](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>E o Azure Active Directory?

Veja [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Como posso saber qual é o meu UPN?

Veja [Como posso saber qual é o meu UPN?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Mapear nomes de utilizador a origens de dados do Analysis Services

Veja [Mapeamento de nomes de utilizador para origens de dados do Analysis Services](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizar uma conta do Active Directory no local com o Azure Active Directory

Veja [Sincronizar uma conta do Active Directory no local com o Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>O que fazer a seguir?

Veja os artigos sobre origens de dados:

[Manage data sources](service-gateway-data-sources.md)
 (Gerir origens de dados)[Gerir a sua origem de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gerir a sua origem de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gerir a sua origem de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gerir a sua origem de dados – Oracle](service-gateway-onprem-manage-oracle.md)  
[Gerir a sua origem de dados - Atualização Importada/Agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>O que pode correr mal

Veja [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot) e [Resolução de problemas de gateways – Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Conta de início de sessão

Veja [Conta de início de sessão](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Conta de Serviço Windows

Veja [Alterar a conta de serviço do gateway de dados no local](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Portas

Veja [Portas](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forçar a comunicação HTTPS com o Azure Service Bus

Veja [Forçar a comunicação HTTPS com o Azure Service Bus](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Suporte para TLS 1.2

Veja [TLS 1.2 para o tráfego do gateway](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Como reiniciar o gateway

Veja [Reiniciar um gateway](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Próximos passos

[O que é o gateway de dados no local?](service-gateway-onprem.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)