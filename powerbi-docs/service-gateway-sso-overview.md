---
title: Utilizar o início de sessão único (SSO) em origens de dados no local
description: Configure o seu gateway para permitir o início de sessão único (SSO) a partir do Power BI em origens de dados no local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/15/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 9e91c162c9b748fd0ef122aed8fc7ffee6dba5fc
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448304"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Descrição geral do início de sessão único (SSO) para gateways no Power BI

Pode obter uma conectividade totalmente integrada de início de sessão único, permitindo a atualização de relatórios e dashboards do Power BI a partir de dados no local, ao configurar o seu Gateway de dados no local com a delegação restrita do Kerberos ou através de SAML (Security Assertion Markup Language). O Gateway de dados no local facilita o SSO com o DirectQuery, que é utilizado para ligar às origens de dados no local.

Atualmente, suportamos as seguintes origens de dados:

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) e [SAML](service-gateway-sso-saml.md))
* SAP BW ([Kerberos](service-gateway-sso-kerberos.md)
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))
* Também é possível que SSO [outras origens de dados](desktop-directquery-data-sources.md#single-sign-on-sso-for-directquery-sources) sem utilizar um gateway de dados

Quando um utilizador interage com um relatório do DirectQuery no serviço Power BI, cada filtro cruzado, setor, ordenação e operação de edição do relatório pode resultar em consultas que são executadas em direto com a origem de dados no local subjacente.  Quando o SSO é configurado para a origem de dados, as consultas são executadas sob a identidade do utilizador que interage com o Power BI (ou seja, através da experiência Web ou das aplicações móveis do Power BI). Assim, cada utilizador verá precisamente os dados para os quais tem permissões na origem de dados subjacente – com o início de sessão único configurado, não existe colocação em cache de dados partilhados com diferentes utilizadores.

## <a name="query-steps-when-running-sso"></a>Passos de consulta ao executar o SSO

Uma consulta que é executada com o SSO consiste em três passos, conforme mostrado no diagrama seguinte.

![Passos de consulta com o SSO](media/service-gateway-sso-overview/sso-query-steps.png)

> [!NOTE]
> O SSO para Oracle não está ativado ainda, mas está em desenvolvimento e ficará disponível em breve.

Seguem-se detalhes adicionais sobre esses passos:

1. Para cada consulta, o **serviço Power BI** inclui o *nome principal de utilizador* (UPN) ao enviar um pedido de consulta para o gateway configurado.

2. O gateway tem de mapear o UPN do Azure Active Directory para uma identidade do Active Directory local.

   a.  Se o Azure AD DirSync (também conhecido como *Azure AD Connect*) estiver configurado, o mapeamento funciona automaticamente no gateway.

   b.  Caso contrário, o gateway pode procurar e mapear o UPN do Azure AD para um utilizador local, efetuando uma pesquisa de domínio do Active Directory local.

3. O processo do serviço de gateway representa o utilizador local mapeado, abre a ligação à base de dados subjacente e envia a consulta. O gateway não tem de ser instalado na mesma máquina da base de dados.

## <a name="next-steps"></a>Próximos passos

Agora que já tem as noções básicas do SSO, leia informações mais detalhadas sobre o Kerberos e SAML:

* [Single sign-on (SSO) - Kerberos](service-gateway-sso-kerberos.md) (Início de sessão único (SSO) – Kerberos)
* [Single sign-on (SSO) - SAML](service-gateway-sso-saml.md) (Início de sessão único (SSO) – SAML)
