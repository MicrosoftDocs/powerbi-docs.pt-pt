---
title: Utilizar o Proxy de Aplicações Web e os Serviços Federados do Active Directory – Power BI Report Server
description: Saiba como utilizar o Proxy de Aplicações Web (WAP) e os Serviços Federados do Active Directory (AD FS) para se ligar ao Power BI Report Server e ao SQL Server Reporting Services (SSRS) 2016 e posterior.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 01/14/2020
ms.openlocfilehash: 2bc2e026acf0f895796158408afa6449c93ce254
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236178"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Utilizar o Proxy de Aplicações Web e os Serviços Federados do Active Directory – Power BI Report Server

Este artigo aborda a utilização do Proxy de Aplicações Web (WAP) e dos Serviços Federados do Active Directory (AD FS) para se ligar ao Power BI Report Server e ao SQL Server Reporting Services (SSRS) 2016 e posterior. Através desta integração, os utilizadores que estão fora da rede empresarial podem aceder aos relatórios Reporting Services e do Power BI Report Server a partir dos browsers cliente e estar protegidos pela autenticação AD FS. Para as aplicações móveis do Power BI, pode também precisar de [configurar o OAuth para se ligar ao Power BI Report Server e ao SSRS](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Pré-requisitos

### <a name="domain-name-services-dns-configuration"></a>Configuração dos Serviços de Nomes de Domínio (DNS)

- Determinar o URL público ao qual o utilizador se vai ligar. Deve ter um aspeto semelhante a este exemplo: `https://reports.contosolab.com`.
- Configurar o registo DNS para o nome do anfitrião, `reports.contosolab.com`, por exemplo, para apontar para o endereço IP público do servidor do Proxy de Aplicações Web (WAP).
- Configurar um registo DNS público para o servidor do AD FS. Por exemplo, poderá ter configurado o servidor do AD FS com o seguinte URL: `https://adfs.contosolab.com`.
- Configurar o registo DNS para apontar para o endereço IP público do servidor do Proxy de Aplicações Web (WAP), por exemplo `adfs.contosolab.com`. É publicado como parte da aplicação WAP.

### <a name="certificates"></a>Certificados

Terá de configurar certificados para a aplicação WAP e para o servidor do AD FS. Ambos estes certificados têm de fazer parte de uma autoridade de certificação válida que os seus computadores reconhecem.

## <a name="1-configure-the-report-server"></a>1. Configurar o servidor de relatório

É necessário garantir que temos um SPN (Nome do Principal do Serviço) válido. O SPN válido permite que ocorra uma autenticação Kerberos correta e permite ao servidor de relatórios negociar a autenticação.

### <a name="service-principal-name-spn"></a>Nome do Principal do Serviço (SPN)

O SPN é um identificador exclusivo para um serviço que utiliza a autenticação Kerberos. Confirme que tem um SPN HTTP adequado para o servidor de relatórios.

Para obter informações sobre como configurar o Nome do Principal do Serviço (SPN) adequado para o servidor de relatórios, veja [Register a Service Principal Name (SPN) for a Report Server (Registar um Nome do Principal do Serviço (SPN) para um Servidor de Relatórios)](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Ativar a autenticação de negociação

Para permitir que um servidor de relatórios utilize a autenticação Kerberos, tem de configurar o Tipo de Autenticação do servidor de relatórios como RSWindowsNegotiate. Pode configura-lo no ficheiro rsreportserver.config.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Para obter mais informações, veja [Modify a Reporting Services Configuration File (Modificar um Ficheiro de Configuração do Reporting Services)](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) e [Configure Windows Authentication on a Report Server (Configurar a Autenticação do Windows num Servidor de Relatórios)](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Configurar o Active Directory Federation Services (AD FS)

Tem de configurar o AD FS num servidor Windows 2016 no seu ambiente. A configuração pode ser feita através do Gestor de Servidor, ao selecionar Adicionar Funções e Funcionalidades em Gerir. Para obter mais informações, veja [Active Directory Federation Services](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services).

No servidor do AD FS, com a Aplicação de Gestão do AD FS, conclua estes passos.

1. Clique com o botão direito do rato em **Fidedignidades da Entidade Confiadora** > **Adicionar Fidedignidade da Entidade Confiadora**.

    ![Adicionar Fidedignidades da Entidade Confiadora](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Siga os passos no assistente **Adicionar Fidedignidade de Entidade Confiadora**.

    Escolha a opção **Sem suporte para afirmações** para utilizar a Segurança integrada do Windows como mecanismo de autenticação.

    ![Bem-vindo ao assistente para Adicionar Fidedignidade da Entidade Confiadora](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Introduza um nome da sua preferência no **Nome a Apresentar Específico** e selecione **Seguinte**.
    Adicione o identificador de Fidedignidade da entidade confiadora: `<ADFS\_URL>/adfs/services/trust`

    Por exemplo: `https://adfs.contosolab.com/adfs/services/trust`

    ![Report Server](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Escolha a **Política de Controlo de Acesso** que se adequa às necessidades da sua organização e selecione **Seguinte**.

    ![Escolher o controlo de acesso](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Selecione **Seguinte** e, em seguida, **Concluir** para concluir o assistente **Adicionar Fidedignidade da Entidade Confiadora**.

    Quando concluído, as propriedades das Fidedignidades da Entidade Confiadora devem ter o seguinte aspeto.

    ![Fidedignidades da entidade confiadora](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Configurar o Proxy de Aplicações Web (WAP)

Deve ativar a função do Proxy de Aplicações Web (Função) do Windows num servidor do seu ambiente. Esta ação só é suportada num servidor do Windows 2016. Para obter mais informações, veja [Web Application Proxy in Windows Server 2016 (Proxy de Aplicações Web no Windows Server 2016)](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) e [Publishing Applications using AD FS Preauthentication (Publicar aplicações com a Pré-autenticação do AD FS)](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Configurar a delegação restrita

Para realizar a transição da Autenticação de formulários para a Autenticação do Windows, precisamos de utilizar a delegação restrita com a transição do protocolo. Este passo faz parte da configuração Kerberos. Já definimos o SPN do servidor de relatórios na configuração do servidor de relatórios.

Precisamos de configurar a delegação restrita na conta de computador do servidor do WAP do Active Directory. Se não tiver direitos para aceder ao Active Directory, terá de trabalhar com um administrador de domínio.

Para configurar a delegação restrita, siga estes passos.

1. Num computador que tenha as ferramentas do Active Directory instaladas, inicie **Utilizadores e Computadores do Active Directory**.
2. Encontre a conta de computador do servidor do WAP. Por predefinição, a conta estará no contentor **Computadores**.
3. Clique com o botão direito do rato no servidor WAP e aceda a **Propriedades**.
4. No separador **Delegação**, selecione **Confiar neste computador para delegação apenas de serviços especificados** e, em seguida, **Utilizar qualquer protocolo de autenticação**.

    ![Confiar neste computador](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Esta opção configura a delegação restrita para esta conta de computador do Servidor WAP. Em seguida, especificamos os serviços que esta máquina tem permissão para delegar.
2. Selecione **Adicionar** na caixa de serviços.

    ![Adicionar fidedignidade do AD FS](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Selecione **Utilizadores ou Computadores**.
2. Introduza a conta de serviço que está a utilizar para o servidor de repositórios. Esta conta é a mesma que utilizou para adicionar o SPN HTTP na secção [Configuração do servidor de relatórios](#1-configure-the-report-server) anterior. 

3. Selecione o SPN HTTP do servidor de relatórios e, em seguida, selecione **OK**.

    > [!NOTE]
    > Só poderá ver o SPN do NetBIOS. Na realidade, seleciona os SPNs do NetBIOS e do FQDN, se existirem ambos.

1. Quando selecionar a caixa de verificação **Expandido**, o resultado deverá ser semelhante ao exemplo seguinte.

    ![Propriedades WAP](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Adicionar Aplicação WAP

1. No servidor do Proxy de Aplicações Web, abra a consola **Gestão de Acesso Remoto** e selecione **Proxy de Aplicações Web** no painel Navegação. 

2. No painel **Tarefas**, selecione **Publicar**.

2. Na página Bem-vindo, selecione **Seguinte**.

    ![Bem-vindo à Publicação](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. Na página **Pré-autenticação**, selecione **Active Directory Federation Services (AD FS)** e, em seguida, selecione **Seguinte**.

    ![Pré-autorização](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Selecione a pré-autenticação **Web e MSOFBA**, pois vamos configurar apenas o acesso do Browser ao servidor de relatórios e não o acesso à aplicação móvel.

    ![Clientes suportados](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Adicione a **Entidade Confiadora** que criamos no servidor do AD FS, conforme ilustrado abaixo, e selecione **Seguinte**.

    ![Publicar a Entidade Confiadora](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. Na secção **URL Externo**, coloque o URL publicamente acessível, configurado no servidor WAP. Adicione o URL configurado com o servidor de relatórios (Gestor de Configuração do Servidor de Relatórios), conforme apresentado abaixo na secção **URL do Servidor de Back-end**. Adicione o SPN do servidor de relatórios na secção **SPN de servidores de back-end**.

    ![Definições da publicação](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Selecione **Seguinte** e **Publicar**.
8. Execute o comando PowerShell que se segue para validar a configuração WAP.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![Comando do PowerShell](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Ligar ao servidor de relatórios através do browser

Em seguida, pode aceder ao URL do WAP Público, por exemplo, `https://reports.contosolab.com/ReportServer` para o serviço Web e `https://reports.contosolab.com/Reports` para o portal Web do browser. Quando for autenticado com sucesso, poderá ver os relatórios.

![Iniciar sessão do AD FS](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Próximos passos

* [Configurar o OAuth para se ligar ao Power BI Report Server e ao SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[O que é o Power BI Report Server?](get-started.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

