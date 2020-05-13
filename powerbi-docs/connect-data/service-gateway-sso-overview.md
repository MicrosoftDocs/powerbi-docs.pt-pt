---
title: Descrição geral do início de sessão único (SSO) para gateways no Power BI
description: Configure o seu gateway para permitir o início de sessão único (SSO) a partir do Power BI em origens de dados no local.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5eab21418eb1028d94ba2e50ffd6e736e6226018
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83301799"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Descrição geral do início de sessão único (SSO) para gateways no Power BI

Pode obter conectividade totalmente integrada de início de sessão único, ao ativar os relatórios e dashboards do Power BI para atualizarem a partir de dados no local em tempo real, através da configuração do Gateway de dados no local. Tem a opção de configurar o gateway com delegação restrita de [Kerberos](service-gateway-sso-kerberos.md) ou Security Assertion Markup Language ([SAML](service-gateway-sso-saml.md)). O gateway de dados no local suporta SSO com recurso ao [DirectQuery](desktop-directquery-about.md) ou à Atualização, que liga às origens de dados no local. 

O Power BI suporta as seguintes origens de dados:

* SQL Server (Kerberos)
* SAP HANA (Kerberos e SAML)
* Servidor de Aplicações SAP BW (Kerberos)
* Servidor de Mensagens SAP BW (Kerberos) 
* Oracle (Kerberos) 
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

Atualmente, não suportamos o SSO para [extensões M](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

Quando um utilizador interage com um relatório do DirectQuery no serviço Power BI, cada filtro cruzado, setor, ordenação e operação de edição do relatório pode resultar em consultas que são executadas em direto com a origem de dados no local subjacente. Quando configura o SSO para a origem de dados, as consultas são executadas sob a identidade do utilizador que interage com o Power BI (ou seja, através da experiência Web ou das aplicações móveis do Power BI). Portanto, cada utilizador vê exatamente os dados para os quais tem permissões na origem de dados subjacente. 

Também pode configurar um relatório para ser atualizado no Serviço Power BI para utilizar SSO. Quando configura o SSO para esta origem de dados, as consultas são executadas na identidade do proprietário do conjunto de dados no Power BI. Assim, a atualização ocorre com base nas permissões do proprietário do conjunto de dados na origem de dados subjacente. A atualização através de SSO está atualmente ativada apenas para origens de dados que utilizam a [delegação restrita de Kerberos](service-gateway-sso-kerberos.md) 

## <a name="query-steps-when-running-sso"></a>Passos de consulta ao executar o SSO

Uma consulta que é executada com o SSO consiste em três passos, conforme mostrado no diagrama seguinte.

![Passos de consulta com o SSO](media/service-gateway-sso-overview/sso-query-steps.png)

Seguem-se detalhes adicionais sobre cada passo:

1. Para cada consulta, o serviço Power BI inclui o *nome principal de utilizador (UPN)* ou seja, o nome de utilizador totalmente qualificado do utilizador que tem sessão atualmente iniciada no serviço Power BI, ao enviar um pedido de consulta para o gateway configurado.

2. O gateway tem de mapear o UPN do Azure Active Directory para uma identidade do Active Directory local:

   a. Se o Azure AD DirSync (também conhecido como *Azure AD Connect*) estiver configurado, o mapeamento funciona automaticamente no gateway.

   b.  Caso contrário, o gateway pode procurar e mapear o UPN do Azure AD para um utilizador local do AD, ao efetuar uma pesquisa de domínio do Active Directory local.

3. O processo do serviço de gateway representa o utilizador local mapeado, abre a ligação à base de dados subjacente e envia a consulta. Não tem de instalar o gateway na mesma máquina que a base de dados.

## <a name="next-steps"></a>Próximas etapas

Agora que já tem as noções básicas de ativar o SSO através do gateway, leia informações mais detalhadas sobre o Kerberos e SAML:

* [Single sign-on (SSO) - Kerberos](service-gateway-sso-kerberos.md) (Início de sessão único (SSO) – Kerberos)
* [Single sign-on (SSO) - SAML](service-gateway-sso-saml.md) (Início de sessão único (SSO) – SAML)
