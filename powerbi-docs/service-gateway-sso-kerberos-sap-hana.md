---
title: Utilizar o Kerberos para início de sessão único (SSO) na SAP HANA
description: Configurar o seu servidor SAP HANA para ativar o SSO a partir do serviço Power BI
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9e7bdb0ae2f1e512e3e431cf69395d601cbc7b3f
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968539"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Utilizar o Kerberos para início de sessão único (SSO) na SAP HANA

Este artigo descreve como configurar a sua origem de dados SAP HANA para ativar o SSO a partir do serviço Power BI.

> [!NOTE]
> Conclua os passos neste artigo, além dos passos em [Configurar SSO do Kerberos](service-gateway-sso-kerberos.md) antes de tentar atualizar um relatório baseado em SAP HANA que usa o SSO do Kerberos.

## <a name="enable-sso-for-sap-hana"></a>Para ativar o SSO para SAP HANA

Para ativar o SSO para SAP HANA, siga estes passos:

* Certifique-se de que o servidor SAP HANA está a executar a versão mínima exigida, consoante o nível de plataforma do servidor SAP HANA:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* Na máquina do gateway, instale o controlador OBDC HANA mais recente do SAP.  A versão mínima é ODBC HANA, versão 2.00.020.00 de agosto de 2017.

Verifique se o servidor SAP HANA foi configurado para SSO baseado em Kerberos. Para obter mais informações sobre como configurar o SSO para o SAP HANA com o Kerberos, veja [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Início de Sessão Único com o Kerberos) no Guia de Segurança do SAP HANA. Veja também as ligações nessa página, em particular, SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

Também recomendamos que siga estes passos adicionais, que podem resultar numa pequena melhoria no desempenho.

1. No diretório de instalação do gateway, localize e abra este ficheiro de configuração: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

2. Localize a propriedade *FullDomainResolutionEnabled* e altere o respetivo valor para *True* (Verdadeiro).

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Agora, [Execute um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o **gateway de dados no local** e o **DirectQuery**, consulte os seguintes recursos:

* [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-getting-started) (O que é um gateway de dados no local?)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
