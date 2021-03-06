---
title: Utilizar o Kerberos para início de sessão único (SSO) na SAP HANA
description: Configurar o seu servidor SAP HANA para ativar o SSO a partir do serviço Power BI
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 3f50b174e8293d75a0077e1799cb64ff4fdcd696
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675126"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Utilizar o Kerberos para início de sessão único (SSO) na SAP HANA

> [!IMPORTANT]
> Uma vez que o [SAP já não suporta o OpenSSL](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.05/en-US/de15ffb1bb5710148386ffdfd857482a.html), a Microsoft também descontinuou o suporte. As ligações existentes continuarão a funcionar, mas não poderá criar novas ligações a partir de fevereiro de 2021. No futuro, em alternativa, utilize o CommonCryptoLib.

Este artigo descreve como configurar a sua origem de dados SAP HANA para ativar o SSO a partir do serviço Power BI.

> [!NOTE]
> Antes de tentar atualizar um relatório baseado em SAP HANA que utiliza o SSO do Kerberos, conclua os passos neste artigo e os passos em [Configurar SSO do Kerberos](service-gateway-sso-kerberos.md).

## <a name="enable-sso-for-sap-hana"></a>Para ativar o SSO para SAP HANA

Para ativar o SSO para SAP HANA, siga estes passos:

1. Certifique-se de que o servidor SAP HANA está a executar a versão mínima exigida, consoante o nível de plataforma do servidor SAP HANA:
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. Na máquina do gateway, instale o controlador OBDC do SAP HANA mais recente. A versão mínima é ODBC HANA, versão 2.00.020.00 de agosto de 2017.

3. Verifique se o servidor SAP HANA foi configurado para SSO baseado em Kerberos. Para obter mais informações sobre como configurar o SSO para o SAP HANA com o Kerberos, veja [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Início de Sessão Único com o Kerberos) no Guia de Segurança do SAP HANA. Veja também as ligações nessa página, em particular, SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

Também recomendamos que siga estes passos adicionais, que podem resultar numa pequena melhoria no desempenho:

1. No diretório de instalação do gateway, localize e abra este ficheiro de configuração: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Localize a propriedade `FullDomainResolutionEnabled` e altere o valor para `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Agora, [Execute um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o gateway de dados no local e o DirectQuery, veja os seguintes recursos:

* [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-onprem) (O que é um gateway de dados no local?)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](power-bi-data-sources.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-bw.md) (DirectQuery e SAP HANA)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
