---
title: Utilizar o SAML no gateway no local para início de sessão único (SSO) a partir do Power BI para origens de dados no local
description: Configure o seu gateway com o formato SAML (Security Assertion Markup Language) para permitir o início de sessão único (SSO) do Power BI em origens de dados no local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 4fbfa38bd235d37fea730bda8d200e97530f0ce9
ms.sourcegitcommit: 2c4a075fe16ccac8e25f7ca0b40d404eacb49f6d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/20/2018
ms.locfileid: "49474578"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Utilizar o formato SAML (Security Assertion Markup Language) para início de sessão único (SSO) do Power BI em origens de dados no local

Utilize o formato [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) para permitir uma conectividade de início de sessão único totalmente integrado. Ativar o SSO facilita a atualização de dados de origens no local através de relatórios e dashboards do Power BI.

## <a name="supported-data-sources"></a>Origens de dados suportadas

Atualmente, suportamos a plataforma SAP HANA com SAML. Para obter mais informações sobre como configurar o início de sessão único na plataforma SAP HANA com SAML, veja o tópico [SAML SSO for BI Platform to HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) (SSO em SAML entre a Plataforma do BI e a HANA) na documentação sobre SAP HANA.

Suportamos origens de dados adicionais com o [Kerberos](service-gateway-sso-kerberos.md).

## <a name="configuring-the-gateway-and-data-source"></a>Configurar o gateway e a origem de dados

Para utilizar SAML, primeiro tem de gerar um certificado para o fornecedor de identidade de SAML e, em seguida, mapear um utilizador do Power BI à identidade.

1. Crie um certificado. Certifique-se de que utiliza o FQDN do servidor SAP HANA ao preencher o campo *common name* (nome comum). O certificado expira dentro de 365 dias.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. No SAP HANA Studio, clique com o botão direito do rato no seu servidor SAP HANA e, em seguida, navegue até **Security** (Segurança)  > **Open Security Console** (Abrir Consola de Segurança)  > **SAML Identity Provider** (Fornecedor de Identidade de SAML)  > **OpenSSL Cryptographic Library** (Biblioteca Criptográfica OpenSSL).

1. Selecione **Import** (Importar), navegue até samltest.crt e importe o certificado.

    ![Fornecedores de identidade](media/service-gateway-sso-saml/identity-providers.png)

1. No SAP HANA Studio, selecione a pasta **Security** (Segurança).

    ![Pasta Security (Segurança)](media/service-gateway-sso-saml/security-folder.png)

1. Expanda a secção **Users** (Utilizadores) e, em seguida, selecione o utilizador ao qual pretende mapear o utilizador do Power BI.

1. Selecione **SAML** e, em seguida, **Configure** (Configurar).

    ![Configurar SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Selecione o fornecedor de identidade que criou no passo 2. Em **External Identity** (Identidade Externa), introduza o UPN do utilizador do Power BI e, em seguida, selecione **Add** (Adicionar).

    ![Selecionar o fornecedor de identidade](media/service-gateway-sso-saml/select-identity-provider.png)

Em seguida, valide a configuração com uma *asserção SAML* ao utilizar a [ferramenta xmlsec1](http://sgros.blogspot.com/2013/01/signing-xml-document-using-xmlsec1.html).

1. Guarde a asserção abaixo como assertion-template.xml. Substitua \<MyUserId\> pelo UPN do utilizador do Power BI que introduziu no passo 7.

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <saml2:Assertion ID="Assertion12345789" IssueInstant="2015-07-16T04:47:49.858Z" Version="2.0" xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
      <saml2:Issuer></saml2:Issuer> 
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
          <CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
          <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
          <Reference URI="">
            <Transforms>
              <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
              <Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
            </Transforms>
            <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
            <DigestValue />
          </Reference>
        </SignedInfo>
        <SignatureValue />
        <KeyInfo>
          <X509Data />
        </KeyInfo>
      </Signature>
      <saml2:Subject>
        <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified"><MyUserId></saml2:NameID>
      </saml2:Subject>
      <saml2:Conditions NotBefore="2010-01-01T00:00:00Z" NotOnOrAfter="2050-01-01T00:00:00Z"/>
    </saml2:Assertion>
    ```

1. Execute o seguinte comando. saltest.key e samltest.crt são a chave e o certificado que gerou no passo 1.

    ```
    xmlsec1 --sign --privkey-pem samltest.key, samltest.crt --output signed.xml assertion-template.xml
    ```

1. No SAP HANA Studio, abra uma janela da consola SQL e execute o seguinte comando. Substitua \<SAMLAssertion\> pelos conteúdos do ficheiro xml do passo anterior.

    ```SQL
    CONNECT WITH SAML ASSERTION '<SAMLAssertion>'
    ```

Se a consulta for bem-sucedida, significa que a sua configuração de SSO em SAML no SAP HANA foi concluída com êxito.

Agora que configurou o certificado e a identidade com êxito, converta o certificado num formato pfx e configure a máquina do gateway para utilizar o certificado.

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

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o **Gateway de dados no local** e o **DirectQuery**, consulte os seguintes recursos:

* [Gateway de dados no local](service-gateway-onprem.md)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)