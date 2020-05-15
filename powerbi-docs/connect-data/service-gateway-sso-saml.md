---
title: Utilizar o formato SAML (Security Assertion Markup Language) para SSO do Power BI em origens de dados no local
description: Configure o seu gateway com o formato SAML (Security Assertion Markup Language) para permitir o SSO do Power BI em origens de dados no local.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 87684ee408663d3d3e68534fa89fd227327b6ac7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83328456"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>Utilizar o formato SAML (Security Assertion Markup Language) para SSO do Power BI em origens de dados no local

Ativar o SSO facilita a atualização de dados de origens no local em relatórios e dashboards do Power BI, ao mesmo tempo que respeita as permissões ao nível do utilizador configuradas nestas origens. Utilize o formato [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) para permitir uma conectividade de início de sessão único totalmente integrado. 

## <a name="supported-data-sources"></a>Supported data sources (Origens de dados suportadas)

Atualmente, suportamos a plataforma SAP HANA com SAML. Para obter mais informações sobre como configurar o início de sessão único na plataforma SAP HANA com SAML, veja [SAML SSO for BI Platform to HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) (SSO do SAML entre a Plataforma de BI e HANA).

Suportamos origens de dados adicionais com o [Kerberos](service-gateway-sso-kerberos.md) (incluindo SAP HANA).

Para o SAP HANA, é recomendado ativar a encriptação antes de estabelecer uma ligação SSO do SAML. Para ativar a encriptação, configure o servidor HANA para aceitar ligações encriptadas e configurar o gateway para utilizar a encriptação para comunicar com o servidor HANA. Como o controlador ODBC do HANA não encripta asserções do SAML por predefinição, a asserção do SAML assinada é enviada do gateway para o servidor HANA *com luz verde* e está vulnerável à interceção e reutilização por terceiros. Para obter instruções sobre como ativar a encriptação para o HANA com a biblioteca OpenSSL, veja [Enable encryption for SAP HANA](/power-bi/desktop-sap-hana-encryption) (Ativar encriptação para o SAP HANA).

## <a name="configuring-the-gateway-and-data-source"></a>Configurar o gateway e a origem de dados

Para utilizar o SAML, tem de estabelecer uma relação de confiança entre os servidores HANA para os quais quer ativar o SSO e o gateway. Neste cenário, o gateway serve de Fornecedor de Identidade (IdP) do SAML. Existem várias formas de estabelecer esta relação, tal como importar o certificado X509 do IdP do gateway para o arquivo de confiança do servidor ou dos servidores HANA, ou utilizar uma Autoridade de Certificação (AC) de raiz em que os servidores HANA confiam para assinar o certificado X509 do gateway. Embora descrevamos esta abordagem mais adiante neste guia, pode utilizar outra, se lhe for mais conveniente.

Apesar de este guia utilizar OpenSSL como o fornecedor criptográfico do servidor HANA, o SAP recomenda utilizar a Biblioteca Criptográfica do SAP (também conhecida como CommonCryptoLib ou sapcrypto) em vez de OpenSSL para concluir os passos de configuração em que estabelecemos a relação de confiança. Para obter mais informações, veja a documentação do SAP oficial.

Os seguintes passos descrevem como estabelecer uma relação de confiança entre um servidor HANA e o IdP do gateway ao assinar o certificado X509 do IdP do gateway com uma AC de Raiz considerada de confiança pelo servidor HANA. Vai criar esta AC de Raiz:

1. Crie o certificado X509 e chave privada da AC de Raiz. Por exemplo, para criar o certificado X509 e a chave privada da AC de Raiz no formato .pem, introduza o seguinte comando:

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
   ```

    Certifique-se de que a chave privada da AC de Raiz está devidamente protegida. Se for obtida por terceiros, poderá ser utilizada para ter acesso não autorizado ao servidor HANA. 

 1. Adicione o certificado (por exemplo, CA_Cert.pem) ao arquivo de confiança do servidor HANA para que o mesmo confie nos certificados assinados pela AC de Raiz que criou. 

    Pode encontrar a localização do arquivo de confiança do seu servidor HANA ao examinar a definição de configuração **ssltruststore**. Se seguiu as instruções na documentação do SAP sobre como configurar OpenSSL, o seu servidor HANA poderá já confiar numa AC de Raiz que pode reutilizar. Para obter mais informações, veja [How to Configure Open SSL for SAP HANA Studio to SAP HANA Server](https://archive.sap.com/documents/docs/DOC-39571) (Como Configurar o OpenSSL entre o SAP HANA Studio e o Servidor SAP HANA). Se tiver múltiplos servidores HANA para os quais quer ativar o SSO do SAML, certifique-se de que cada um confia nesta AC de Raiz.

1. Crie o certificado X509 do IdP do gateway. 

   Por exemplo, para criar um pedido de assinatura de certificado (IdP_Key.pem) e uma chave privada (IdP_Key.pem) válidos por um ano, execute o seguinte comando:

   ```
   openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
   ```

 1. Assine o pedido de assinatura de certificado com a AC de Raiz que configurou para os seus servidores HANA confiarem. 

    Por exemplo, para assinar IdP_Req.pem através de CA_Cert.pem e CA_Key.pem (o certificado e chave da AC de Raiz), execute o seguinte comando:

    ```
    openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
    ```

     O certificado de Idp resultante é válido por um ano (veja a opção -days). 

Importe o certificado do seu Idp para o HANA Studio para criar um novo Fornecedor de Identidade do SAML:

1. No SAP HANA Studio, clique com o botão direito do rato no nome do servidor SAP HANA e, em seguida, navegue para **Security** (Segurança) &gt; **Open Security Console** (Abrir Consola de Segurança) &gt; **SAML Identity Provider** (Fornecedor de Identidade do SAML) &gt; **OpenSSL Cryptographic Library** (Biblioteca Criptográfica OpenSSL).

    ![Fornecedores de identidade](media/service-gateway-sso-saml/identity-providers.png)

1. Selecione **Import** (Importar), navegue até ao IdP_Cert.pem e importe o certificado.

1. No SAP HANA Studio, selecione a pasta **Security** (Segurança).

    ![Pasta Security (Segurança)](media/service-gateway-sso-saml/security-folder.png)

1. Expanda a secção **Utilizadores** e, em seguida, selecione o utilizador para o qual quer mapear o utilizador do Power BI.

1. Selecione **SAML** e, em seguida, selecione **Configurar**.

    ![Configurar SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Selecione o fornecedor de identidade que criou no passo 2. Em **Identidade Externa**, introduza o UPN do utilizador do Power BI (normalmente, o endereço de e-mail com o qual o utilizador inicia sessão no Power BI) e selecione **Adicionar**. Se tiver configurado o gateway para utilizar a opção de configuração *ADUserNameReplacementProperty*, introduza o valor que irá substituir o UPN original do utilizador do Power BI. 

   Por exemplo, se definir *ADUserNameReplacementProperty* como **SAMAccountName**, deverá introduzir o atributo **SAMAccountName** do utilizador.

    ![Selecionar o fornecedor de identidade](media/service-gateway-sso-saml/select-identity-provider.png)

Agora que configurou o certificado e a identidade do gateway, converta o certificado num formato pfx e configure o gateway para utilizar o certificado:

1. Converta o certificado no formato pfx ao executar o seguinte comando. Este comando atribui o nome samlcert.pfx ao ficheiro .pfx resultante e define *root* como a respetiva palavra-passe:

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. Copie o ficheiro pfx para a máquina do gateway:

    1. Faça duplo clique no samltest.pfx e, em seguida, selecione **Computador Local** &gt; **Seguinte**.

    1. Introduza a palavra-passe e, em seguida, selecione **Next** (Seguinte).

    1. Selecione **Colocar todos os certificados no seguinte arquivo** e, em seguida, selecione **Procurar** &gt; **Pessoal** &gt; **OK**.

    1. Selecione **Seguinte** e, em seguida, **Concluir**.

       ![Importar o certificado](media/service-gateway-sso-saml/import-certificate.png)

1. Permita que a conta do serviço de gateway aceda à chave privada do certificado:

    1. Na máquina do gateway, execute a Consola de Gestão da Microsoft (MMC).

        ![Executar a MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. Em **Ficheiro**, selecione **Adicionar/Remover Snap-in**.

        ![Adicionar snap-in](media/service-gateway-sso-saml/add-snap-in.png)

    1. Selecione **Certificados** &gt; **Adicionar** e, em seguida, selecione **Conta do computador** &gt; **Seguinte**.

    1. Selecione **Computador Local** &gt; **Concluir** &gt; **OK**.

    1. Expanda a secção **Certificados** &gt; **Pessoal** &gt; **Certificados** e procure o certificado.

    1. Clique com o botão direito do rato no certificado e navegue até **Todas as Tarefas** &gt; **Gerir Chaves Privadas**.

        ![Gerir chaves privadas](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Adicione a conta do serviço de gateway à lista. Por predefinição, a conta é **NT SERVICE\PBIEgwService**. Pode descobrir a conta que está a executar o serviço de Gateway ao executar **services.msc** e ao localizar o **Serviço de gateway de dados no local**.

        ![Serviço de gateway](media/service-gateway-sso-saml/gateway-service.png)

Por fim, siga estes passos para adicionar o thumbprint do certificado à configuração do gateway:

1. Execute o seguinte comando do PowerShell para listar os certificados no seu computador:

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

1. Copie o thumbprint para o certificado que criou.

1. Navegue até ao diretório do gateway que, por predefinição, é C:\Programas\On-premises data gateway.

1. Abra PowerBI.DataMovement.Pipeline.GatewayCore.dll.config e localize a secção *SapHanaSAMLCertThumbprint*. Cole o thumbprint que copiou.

1. Reinicie o serviço de gateway.

## <a name="running-a-power-bi-report"></a>Executar um relatório do Power BI

Agora, pode utilizar a página **Gerir Gateways** no Power BI para configurar a origem de dados do SAP HANA. Em **Definições Avançadas**, ative o SSO via SAML. Assim, pode publicar relatórios e conjuntos de dados vinculados a essa origem de dados.

   ![Definições avançadas](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Resolução de problemas

Depois de configurar o SSO baseado no SAML, poderá ver o seguinte erro no portal do Power BI: *Não pode utilizar as credenciais disponibilizadas para a origem SapHana.* Este erro indica que a credencial SAML foi rejeitada pelo SAP HANA.

Os rastreios de autenticação do lado do servidor proporcionam informações detalhadas para a resolução de problemas de credenciais no SAP HANA. Siga estes passos para configurar o rastreio para o seu servidor SAP HANA:

1. No servidor SAP HANA, ative o rastreio de autenticação ao executar a seguinte consulta:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reproduza o problema.

1. No HANA Studio, abra a consola de administração e selecione o separador **Ficheiros de Diagnóstico**.

1. Abra o rastreio do servidor de índice mais recente e procure *SAMLAuthenticator.cpp*.

    Deve encontrar uma mensagem de erro detalhada que indica a causa raiz, por exemplo:

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Depois de a resolução de problemas estar concluída, desative o rastreio de autenticação ao executar a seguinte consulta:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o gateway de dados no local e o DirectQuery, veja os seguintes recursos:

* [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-onprem) (O que é um gateway de dados no local?)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](power-bi-data-sources.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-bw.md) (DirectQuery e SAP HANA)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)