---
title: Utilizar o SAML para o início de sessão único (SSO) em origens de dados no local
description: Configure o seu gateway com o formato SAML (Security Assertion Markup Language) para permitir o início de sessão único (SSO) do Power BI em origens de dados no local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 03/05/2019
LocalizationGroup: Gateways
ms.openlocfilehash: c1ca797efa2e40bf74384a1e9f2362acd26c6f8f
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555648"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Utilizar o formato SAML (Security Assertion Markup Language) para início de sessão único (SSO) do Power BI em origens de dados no local

Utilize o formato [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) para permitir uma conectividade de início de sessão único totalmente integrado. Ativar o SSO facilita a atualização de dados de origens no local através de relatórios e dashboards do Power BI.

## <a name="supported-data-sources"></a>Supported data sources (Origens de dados suportadas)

Atualmente, suportamos a plataforma SAP HANA com SAML. Para obter mais informações sobre como configurar o início de sessão único na plataforma SAP HANA com SAML, veja o tópico [SAML SSO for BI Platform to HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) (SSO em SAML entre a Plataforma do BI e a HANA) na documentação sobre SAP HANA.

Suportamos origens de dados adicionais com o [Kerberos](service-gateway-sso-kerberos.md).

## <a name="configuring-the-gateway-and-data-source"></a>Configurar o gateway e a origem de dados

Para utilizar SAML, primeiro tem de gerar um certificado para o fornecedor de identidade de SAML e, em seguida, mapear um utilizador do Power BI à identidade.

1. Crie um certificado. Certifique-se de que utiliza o FQDN do servidor SAP HANA ao preencher o campo *common name* (nome comum). O certificado expira dentro de 365 dias.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. No SAP HANA Studio, clique com o botão direito do rato no seu servidor SAP HANA e, em seguida, navegue até **Security** (Segurança)  > **Open Security Console** (Abrir Consola de Segurança)  > **SAML Identity Provider** (Fornecedor de Identidade de SAML)  > **OpenSSL Cryptographic Library** (Biblioteca Criptográfica OpenSSL).

    Também é possível utilizar a Biblioteca Criptográfica SAP (também conhecida como CommonCryptoLib ou sapcrypto) em vez de OpenSSL para concluir estes passos de configuração. Veja a documentação oficial do SAP para obter mais informações.

1. Selecione **Import** (Importar), navegue até samltest.crt e importe o certificado.

    ![Fornecedores de identidade](media/service-gateway-sso-saml/identity-providers.png)

1. No SAP HANA Studio, selecione a pasta **Security** (Segurança).

    ![Pasta Security (Segurança)](media/service-gateway-sso-saml/security-folder.png)

1. Expanda a secção **Users** (Utilizadores) e, em seguida, selecione o utilizador ao qual pretende mapear o utilizador do Power BI.

1. Selecione **SAML** e, em seguida, **Configure** (Configurar).

    ![Configurar SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Selecione o fornecedor de identidade que criou no passo 2. Em **External Identity** (Identidade Externa), introduza o UPN do utilizador do Power BI e, em seguida, selecione **Add** (Adicionar).

    ![Selecionar o fornecedor de identidade](media/service-gateway-sso-saml/select-identity-provider.png)

Agora que configurou o certificado e a identidade, converta o certificado num formato pfx e configure a máquina do gateway para utilizar o certificado.

1. Converta o certificado no formato pfx ao executar o seguinte comando.

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
    ```

1. Copie o ficheiro pfx para a máquina do gateway:

    1. Faça duplo clique em samltest.pfx e, em seguida, selecione **Local Machine** (Máquina Local)  > **Next** (Seguinte).

    1. Introduza a palavra-passe e, em seguida, selecione **Next** (Seguinte).

    1. Selecione **Place all certificates in the following store** (Colocar todos os certificados no seguinte arquivo) e, em seguida, **Browse** (Procurar)  > **Personal** (Pessoal)  > **OK**.

    1. Selecione **Next** (Seguinte) e, em seguida, **Finish** (Concluir).

    ![Importar o certificado](media/service-gateway-sso-saml/import-certificate.png)

1. Permita que a conta do serviço de gateway aceda à chave privada do certificado:

    1. Na máquina do gateway, execute a Consola de Gestão da Microsoft (MMC).

        ![Executar a MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. Em **Ficheiro**, selecione **Adicionar/Remover Snap-in**.

        ![Adicionar snap-in](media/service-gateway-sso-saml/add-snap-in.png)

    1. Selecione **Certificados** > **Adicionar** e, em seguida, selecione **Conta de computador** > **Seguinte**.

    1. Selecione **Computador Local** > **Concluir** > **OK**.

    1. Expanda a secção **Certificados** > **Pessoais** > **Certificados** e localize o certificado.

    1. Clique com o botão direito do rato no certificado e navegue até **Todas as Tarefas** > **Gerir Chaves Privadas**.

        ![Gerir chaves privadas](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Adicione a conta do serviço de gateway à lista. Por predefinição, a conta é **NT SERVICE\PBIEgwService**. Pode descobrir a conta que está a executar o serviço de gateway ao executar **services.msc** e localizar o **Serviço de gateway de dados no local**.

        ![Serviço de gateway](media/service-gateway-sso-saml/gateway-service.png)

Por fim, siga estes passos para adicionar o thumbprint do certificado à configuração do gateway.

1. Execute o seguinte comando do PowerShell para listar os certificados no seu computador.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Copie o thumbprint para o certificado que criou.

1. Navegue até ao diretório do gateway, cuja predefinição é C:\Programas\On-premises data gateway.

1. Abra PowerBI.DataMovement.Pipeline.GatewayCore.dll.config e localize a secção \*SapHanaSAMLCertThumbprint\*. Cole o thumbprint que copiou.

1. Reinicie o serviço de gateway.

## <a name="running-a-power-bi-report"></a>Executar um relatório do Power BI

Agora pode utilizar a página **Gerir Gateways** no Power BI para configurar a origem de dados e ativar o SSO nas respetivas **Definições Avançadas**. Em seguida, pode publicar relatórios e conjuntos de dados vinculados a essa origem de dados.

![Definições avançadas](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Resolução de problemas

Depois de configurar o SSO, poderá ver o erro seguinte no portal do Power BI: "Não pode utilizar as credenciais disponibilizadas para a origem SapHana." Este erro indica que a credencial SAML foi rejeitada pelo SAP HANA.

Os rastreios de autenticação proporcionam informações detalhadas para a resolução de problemas de credenciais no SAP HANA. Siga estes passos para configurar o rastreio para o seu servidor SAP HANA.

1. No servidor SAP HANA, ative o rastreio de autenticação ao executar a consulta seguinte.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reproduza o problema com o qual se depara.

1. No HANA Studio, abra a consola de administração e aceda ao separador **Ficheiros de Diagnóstico**.

1. Abra o rastreio indexserver mais recente e procure SAMLAuthenticator.cpp.

    Deve encontrar uma mensagem de erro detalhada que indica a causa raiz, tal como no exemplo seguinte.

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Assim que a resolução de problemas estiver concluída, desative o rastreio de autenticação ao executar a consulta seguinte.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o **Gateway de dados no local** e o **DirectQuery**, consulte os seguintes recursos:

* [Gateway de dados no local](service-gateway-onprem.md)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
