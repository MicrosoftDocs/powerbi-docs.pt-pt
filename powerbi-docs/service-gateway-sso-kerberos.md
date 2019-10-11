---
title: Configurar o SSO – Kerberos
description: Configurar o gateway com o Kerberos para permitir o SSO a partir do Power BI para origens de dados no local
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 0fb52262790c6c1935d8152f043f726a9471817d
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968972"
---
# <a name="configure-kerberos-based-sso-from-power-bi-service-to-on-premises-data-sources"></a>Configurar o SSO baseado no Kerberos a partir do serviço Power BI para as origens de dados no local

Utilize a [delegação restrita de Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para ativar a conectividade de SSO totalmente integrada. Ativar o SSO facilita a atualização de dados de origens no local em relatórios e dashboards do Power BI, ao mesmo tempo que respeita as permissões ao nível do utilizador configuradas nestas origens.

Vários itens têm de ser configurados para que a delegação restrita de Kerberos funcione corretamente, incluindo os _Nomes dos Principais do Serviço_ (SPN) e as definições de delegação em contas de serviço.

### <a name="prerequisite-1-install-and-configure-the-microsoft-on-premises-data-gateway"></a>Pré-requisito 1: instalar e configurar o gateway de dados no local da Microsoft

O gateway de dados no local suporta uma atualização no local e o _controlo das definições_ dos gateways existentes.

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>Pré-requisito 2: Executar o serviço Windows do gateway como uma conta de domínio

Numa instalação padrão, o gateway é executado como uma conta de serviço do computador local (especificamente, _NT Service\PBIEgwService_), conforme mostrado na imagem seguinte:

![Captura de ecrã a mostrar a conta de serviço](media/service-gateway-sso-kerberos/service-account.png)

Para ativar a delegação restrita de Kerberos, o gateway tem de ser executado como uma conta de domínio, a menos que a instância do Azure Active Directory (Azure AD) já esteja sincronizada com a instância do Active Directory local (através do Azure AD DirSync/Connect). Para mudar para uma conta de domínio, veja [Alterar a conta do serviço de gateway](/data-integration/gateway/service-gateway-service-account).

> [!NOTE]
> Se o Azure AD Connect estiver configurado e as contas de utilizador estiverem sincronizadas, o serviço de gateway não precisará de realizar pesquisas do Azure AD locais no runtime. Em vez disso, pode simplesmente utilizar o SID do serviço local para o serviço de gateway para concluir toda a configuração necessária no Azure Active Directory. Os passos de configuração da delegação restrita de Kerberos descritos neste artigo são os mesmos que os passos de configuração necessários no contexto do Azure Active Directory. São simplesmente aplicados ao objeto do computador do gateway (conforme identificado pelo SID do serviço local) no Azure AD, em vez de à conta do domínio.

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Pré-requisito 3: ter direitos de administrador de domínio para configurar as definições de delegação restrita de Kerberos e SPN (SetSPN)

Não recomendamos que um administrador de domínio conceda direitos, temporária ou permanentemente, a outro utilizador para configurar SPNs e as definições de delegação de Kerberos, sem ser necessário que esse utilizador tenha direitos de administração do domínio. Na secção seguinte, abordamos mais detalhadamente os passos de configuração recomendados.

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Configurar a delegação restrita de Kerberos para o gateway e a origem de dados

Como administrador de domínio, configure um SPN para a conta de domínio do serviço de gateway (se necessário) e configure as definições de delegação na conta de domínio do serviço de gateway.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Configurar um SPN para a conta do serviço de gateway

Em primeiro lugar, determine se já foi criado um SPN para a conta de domínio utilizada como a conta do serviço de gateway:

1. Como administrador de domínio, inicie **Utilizadores e Computadores do Active Directory**.

2. Clique com o botão direito no domínio, selecione **Localizar** e escreva o nome da conta do serviço de gateway.

3. No resultado da pesquisa, clique com o botão direito do rato na conta do serviço de gateway e selecione **Propriedades**.

4. Se o separador **Delegação** for apresentado na caixa de diálogo **Propriedades**, isso significa que já foi criado um SPN e pode avançar para [Escolher uma delegação restrita de Kerberos padrão ou baseada em recursos](#decide-on-resource-based-or-standard-kerberos-constrained-delegation).

    Se não existir um separador **Delegação**, na caixa de diálogo **Propriedades**, pode criar manualmente um SPN nessa conta para o ativar. Utilize a [ferramenta setspn](https://technet.microsoft.com/library/cc731241.aspx) fornecida com o Windows (precisa de direitos de administrador de domínio para criar o SPN).

    Por exemplo, imagine que a conta do serviço de gateway é **Contoso\GatewaySvc** e que o nome do computador em que o serviço de gateway é executado é **MyGatewayMachine**. Para definir o SPN para a conta do serviço de gateway, pode executar o seguinte comando:

    ![Imagem de definição de comando do SPN](media/service-gateway-sso-kerberos/set-spn.png)

    Também pode definir o SPN com o snap-in da MMC (Consola de Gestão da Microsoft) de Utilizadores e Computadores do Active Directory.

### <a name="decide-on-resource-based-or-standard-kerberos-constrained-delegation"></a>Escolher uma delegação restrita de Kerberos padrão ou baseada em recursos

As definições de delegação podem ser configuradas _quer_ para a delegação restrita de Kerberos baseada em recursos quer para a delegação restrita de Kerberos padrão. Utilize a delegação baseada em recursos se a origem de dados pertencer a um domínio diferente do gateway, mas tenha em atenção que essa abordagem exige o Windows Server 2012 ou posterior. Veja a [página de visão geral da delegação restrita de Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para obter mais informações sobre as diferenças entre as duas abordagens à delegação.

 Após escolher a abordagem que quer utilizar, avance _para_ a secção [Configurar a conta do serviço de gateway para a delegação restrita de Kerberos padrão](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation) _ou_ para a secção [Configurar a conta do serviço de gateway para a delegação restrita de Kerberos baseada em recursos](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation). Opte apenas por uma das subsecções.

## <a name="configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation"></a>Configurar a conta do serviço de gateway para a delegação restrita de Kerberos padrão

> [!NOTE]
> Conclua os passos nesta secção caso queira ativar a delegação restrita de Kerberos padrão. Caso prefira ativar a delegação restrita de Kerberos baseada em recursos, conclua os passos da subsecção [Configurar a conta do serviço de gateway para a delegação restrita de Kerberos baseada em recursos](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation).

Vamos configurar agora as definições de delegação para a conta do serviço de gateway. Pode utilizar várias ferramentas existentes para executar estes passos. Aqui, vamos utilizar o Utilizadores e Computadores do Active Directory, que é um snap-in da Consola de Gestão da Microsoft (MMC), para administrar e publicar informações no diretório. Está disponível nos controladores de domínio por predefinição, mas também o pode ativar através da configuração de Funcionalidades do Windows noutros computadores.

Precisamos de configurar a delegação restrita de Kerberos com trânsito de protocolo. Com a delegação restrita, tem de ser explícito relativamente aos serviços aos quais o gateway pode apresentar credenciais delegadas. Por exemplo, apenas o SQL Server ou o seu servidor SAP HANA aceita chamadas de delegação da conta do serviço de gateway.

Esta secção pressupõe que já configurou os SPNs para as origens de dados subjacentes (como o SQL Server, SAP HANA, SAP BW, Teradata ou Apache Spark). Para saber como configurar esses SPNs do servidor de origem de dados, consulte a documentação técnica do respetivo servidor de bases de dados. Também pode ver o título *What SPN does your app require?* (De que SPN precisa a sua aplicação?) na mensagem [My Kerberos Checklist](https://techcommunity.microsoft.com/t5/SQL-Server-Support/My-Kerberos-Checklist-8230/ba-p/316160) (A Minha Lista de Verificação do Kerberos) do blogue.

Nos passos seguintes, utilizamos um ambiente no local com dois computadores no mesmo domínio: um computador do gateway e um servidor de base de dados com o SQL Server já configurado para o SSO baseado no Kerberos. Os passos podem ser adotados para uma das outras origens de dados suportadas, desde que a origem de dados já tenha sido configurada para o início de sessão único baseado no Kerberos. Para efeitos deste exemplo, vamos utilizar os seguintes nomes e definições:

* Domínio do Active Directory (NetBIOS): **Contoso**
* Nome do computador do gateway: **MyGatewayMachine**
* Conta do serviço de gateway: **Contoso\GatewaySvc**
* Nome do computador da origem de dados do SQL Server: **TestSQLServer**
* Conta do serviço da origem de dados do SQL Server: **Contoso\SQLService**

Eis como configurar as definições de delegação:

1. Com direitos de administrador de domínio, abra o **Utilizadores e Computadores do Active Directory**.

2. Clique com o botão direito do rato na conta do serviço de gateway (**Contoso\GatewaySvc**) e selecione **Propriedades**.

3. Selecione o separador **Delegação**.

4. Selecione **Confiar neste computador apenas para delegação para serviços especificados** > **Utilizar qualquer protocolo de autenticação**.

5. Em **Serviços aos quais esta conta pode apresentar credenciais delegadas**, selecione **Adicionar**.

6. Na nova caixa de diálogo, selecione **Users or Computers** (Utilizadores ou Computadores).

7. Introduza a conta de serviço da origem de dados. Por exemplo, uma origem de dados do SQL Server poderá ter a conta de serviço **Contoso\SQLService**. Já devia ter definido um SPN adequado para a origem de dados nesta conta. Depois de adicionar a conta, selecione **OK**.

8. Selecione o SPN que criou para o servidor de bases de dados. No nosso exemplo, o SPN começa com **MSSQLSvc**. Se adicionou o FQDN e o SPN NetBIOS para o serviço de base de dados, irá selecionar ambos. Poderá ver apenas um.

9. Selecione **OK**. Agora, deve ver o SPN na lista de serviços em que a conta de serviço de gateway pode apresentar credenciais delegadas.

    ![Captura de ecrã a mostrar a caixa de diálogo Propriedades do Conector do Gateway](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

Agora, avance para [Conceder os direitos da política local da conta de serviço de gateway no computador do gateway](#grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine) para continuar o processo de configuração.

## <a name="configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation"></a>Configurar a conta do serviço de gateway para a delegação restrita de Kerberos baseada em recursos

> [!NOTE]
> Conclua os passos nesta secção caso prefira ativar a delegação restrita de Kerberos baseada em recursos. Caso prefira ativar a delegação restrita de Kerberos padrão, conclua os passos da subsecção [Configurar a conta do serviço de gateway para a delegação restrita de Kerberos padrão](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation).

Utilize a [delegação restrita de Kerberos baseada em recursos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) para ativar a conectividade de início de sessão único para o Windows Server 2012 e versões posteriores, ao permitir serviços de front-end e back-end para estar em domínios diferentes. Para funcionar, o domínio do serviço de back-end tem de confiar no domínio do serviço de front-end.

Nos passos seguintes, utilizamos um ambiente no local com dois computadores em diferentes domínios: um computador do gateway e um servidor de base de dados com o SQL Server já configurado para o SSO baseado no Kerberos. Os passos podem ser adotados para uma das outras origens de dados suportadas, desde que a origem de dados já tenha sido configurada para o início de sessão único baseado no Kerberos. Para efeitos deste exemplo, vamos utilizar os seguintes nomes e definições:

* Domínio de front-end do Active Directory (NetBIOS): **ContosoFrontEnd**
* Domínio de back-end do Active Directory (NetBIOS): **ContosoBackEnd**
* Nome do computador do gateway: **MyGatewayMachine**
* Conta do serviço de gateway: **ContosoFrontEnd\GatewaySvc**
* Nome do computador da origem de dados do SQL Server: **TestSQLServer**
* Conta do serviço da origem de dados do SQL Server: **ContosoBackEnd\SQLService**

Considerando estes nomes e definições de exemplo, conclua os seguintes passos de configuração:

1. No controlador do domínio **ContosoFrontEnd**, confirme que não são aplicadas definições de delegação para a conta do serviço de gateway ao utilizar **Utilizadores e Computadores do Active Directory**, um snap-in da Consola de Gestão da Microsoft (MMC).

    ![Propriedades do Gateway Connector](media/service-gateway-sso-kerberos-resource/gateway-connector-properties.png)

2. Ao utilizar **Utilizadores e Computadores do Active Directory** no controlador do domínio **ContosoBackEnd**, confirme que não são aplicadas definições de delegação para a conta do serviço de back-end.

    ![Propriedades do serviço SQL](media/service-gateway-sso-kerberos-resource/sql-service-properties.png)

3. Confirme também que o atributo **msDS-AllowedToActOnBehalfOfOtherIdentity** desta conta também não está definido. Pode encontrar este atributo no **Editor de Atributos**, conforme mostrado na imagem seguinte:

    ![Atributos do serviço SQL](media/service-gateway-sso-kerberos-resource/sql-service-attributes.png)

4. Crie um grupo em **Utilizadores e Computadores do Active Directory**, no controlador do domínio **ContosoBackEnd**. Adicione a conta do serviço de gateway a este grupo, conforme mostrado na imagem seguinte. A imagem mostra um novo grupo denominado _ResourceDelGroup_ e a conta do serviço de gateway **GatewaySvc** adicionada a este grupo.

    ![Propriedades do grupo](media/service-gateway-sso-kerberos-resource/group-properties.png)

5. Abra uma linha de comandos e execute os seguintes comandos no controlador do domínio **ContosoBackEnd** para atualizar o atributo **msDS-AllowedToActOnBehalfOfOtherIdentity** da conta do serviço de back-end:

    ```powershell
    $c = Get-ADGroup ResourceDelGroup
    Set-ADUser SQLService -PrincipalsAllowedToDelegateToAccount $c
    ```

6. Pode verificar que a atualização é refletida no separador “Editor de Atributos” nas propriedades da conta do serviço de back-end em **Utilizadores e Computadores do Active Directory**. O atributo **msDS-AllowedToActOnBehalfOfOtherIdentity** deverá agora estar definido.

## <a name="grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine"></a>Conceder os direitos da política local da conta de serviço de gateway no computador do gateway

Por fim, no computador que executa o serviço de gateway (**MyGatewayMachine** no nosso exemplo), tem de conceder à conta do serviço de gateway as políticas locais **Representar um cliente após autenticação** e **Atuar como parte do sistema operativo (SeTcbPrivilege)** . Pode efetuar e verificar esta configuração com o Editor de Políticas de Grupo Local (**gpedit**).

1. Na máquina do gateway, execute: *gpedit.msc*.

2. Aceda a **Política de Computador Local** &gt; **Configuração de Computador** &gt; **Definições do Windows** &gt; **Definições de Segurança** &gt; **Políticas Locais** &gt; **Atribuição de Direitos de Utilizadores**.

    ![Captura de ecrã a mostrar a estrutura de pastas da Política do Computador Local](media/service-gateway-sso-kerberos/user-rights-assignment.png)

3. Em **Atribuição de Direitos de Utilizadores**, na lista de políticas, selecione **Representar um cliente após autenticação**.

    ![Captura de ecrã a mostrar a política Representar um cliente após autenticação](media/service-gateway-sso-kerberos/impersonate-client.png)

    Clique com o botão direito do rato e abra as **Propriedades**. Verifique a lista de contas. Esta tem de incluir a conta do serviço de gateway (**Contoso\GatewaySvc** ou **ContosoFrontEnd\GatewaySvc**, conforme o tipo de delegação restrita).

4. Em **Atribuição de Direitos de Utilizadores**, na lista de políticas, selecione **Atuar como parte do sistema operativo (SeTcbPrivilege)** . Certifique-se de que a conta do serviço de gateway também está incluída na lista de contas.

5. Reinicie o processo do serviço de **Gateway de dados no local**.

### <a name="set-user-mapping-configuration-parameters-on-the-gateway-machine-if-required"></a>Definir parâmetros de configuração do mapeamento de utilizador no computador do gateway, se necessário

Se não tiver o Azure AD Connect configurado, siga estes passos para mapear um utilizador do serviço Power BI para um utilizador do Active Directory local. Cada utilizador do Active Directory mapeado deste modo necessita de ter permissões SSO para a origem de dados. Para obter mais informações, assista a este [vídeo Guy in a Cube](https://www.youtube.com/watch?v=NG05PG9aiRw).

1. Abra o ficheiro de configuração de gateway principal, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Por predefinição, este ficheiro está armazenado em C:\Programas\On-premises data gateway.

1. Defina **ADUserNameLookupProperty** como um atributo do Active Directory não utilizado. Vamos assumir que `msDS-cloudExtensionAttribute1` é utilizado nos passos a seguir, embora este atributo esteja disponível apenas no Windows Server 2012 e posterior. Defina **ADUserNameReplacementProperty** como `SAMAccountName`. Guarde o ficheiro de configuração.

1. No separador **Serviços** do Gestor de Tarefas, clique com o botão direito do rato no serviço de gateway e selecione **Reiniciar**.

    ![Captura de ecrã a mostrar o separador Serviços no Gestor de Tarefas](media/service-gateway-sso-kerberos/restart-gateway.png)

1. Para cada utilizador do serviço Power BI para o qual quer ativar o SSO do Kerberos, defina a propriedade `msDS-cloudExtensionAttribute1` de um utilizador do Active Directory local (com permissão SSO para a origem de dados) com o nome de utilizador completo (ou seja, o UPN) do utilizador do serviço Power BI. Por exemplo, caso inicie sessão no serviço Power BI como `test@contoso.com` e queira mapear este utilizador para um utilizador do Active Directory local com permissões SSO, digamos `test@LOCALDOMAIN.COM`, defina o atributo `msDS-cloudExtensionAttribute1` de `test@LOCALDOMAIN.COM` como `test@contoso.com`.

    Pode definir a propriedade `msDS-cloudExtensionAttribute1` com o snap-in Utilizadores e Computadores do Active Directory da Consola de Gestão da Microsoft (MMC):
    
    1. Como administrador de domínio, inicie o snap-in Utilizadores e Computadores do Active Directory.
    
    1. Clique com o botão direito do rato no domínio, selecione Localizar e escreva o nome da conta do utilizador do Active Directory local para a qual quer mapear.
    
    1. Selecione o separador **Attribute Editor** (Editor de Atributos).
    
        Localize a propriedade `msDS-cloudExtensionAttribute1` e faça duplo clique na mesma. Defina o valor para o nome de utilizador completo (ou seja, o UPN) que utiliza para iniciar sessão no serviço Power BI.
    
    1. Selecione **OK**.
    
        ![Captura de ecrã a mostrar a caixa de diálogo Editor de Atributos de Cadeia](media/service-gateway-sso-kerberos/edit-attribute.png)
    
    1. Selecione **Aplicar**. Verifique se o valor correto foi configurado na coluna **Valor**.

## <a name="complete-data-source-specific-configuration-steps"></a>Concluir os passos de configuração específicos da origem de dados

O SAP HANA e o SAP BW têm pré-requisitos e requisitos de configuração específicos da origem de dados adicionais que devem ser cumpridos para poder estabelecer uma ligação SSO através do gateway com estas origens de dados. Veja a [página de configuração do SAP HANA](service-gateway-sso-kerberos-sap-hana.md) e a [página de configuração do SAP BW – CommonCryptoLib (sapcrypto.dll)](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) para obter detalhes. Também é possível [configurar o SAP BW para utilização com a biblioteca SNC gx64krb5](service-gateway-sso-kerberos-sap-bw-gx64krb.md), mas esta biblioteca não é recomendada pela Microsoft por já não ser suportada pelo SAP. Deve utilizar CommonCryptoLib _ou_ gx64krb5 como a biblioteca SNC. Não conclua os passos de configuração para ambas as bibliotecas.

> [!NOTE]
> Outras bibliotecas SNC também podem funcionar para o SSO de BW, contudo, não são oficialmente suportadas pela Microsoft.

## <a name="run-a-power-bi-report"></a>Executar um relatório do Power BI

Depois de concluir todos os passos de configuração, pode utilizar a página **Gerir Gateway** no Power BI para configurar a origem de dados que utilizará para o SSO. Se tiver vários gateways, confirme que seleciona o gateway que configurou para o SSO do Kerberos. Nas **Definições Avançadas** da origem de dados, confirme que a caixa de verificação **Utilizar SSO através de Kerberos para consultas de DirectQuery** está selecionada.

![Captura de ecrã a mostrar a opção Definições Avançadas](media/service-gateway-sso-kerberos/advanced-settings.png)

 Publique um relatório **baseado no DirectQuery** a partir do Power BI Desktop. Este relatório tem de utilizar dados que possam ser acedidos pelo utilizador mapeado para o utilizador do (Azure) Active Directory que inicia sessão no serviço Power BI. Tem de utilizar o DirectQuery em vez da importação, devido à forma como a atualização funciona. Ao atualizar os relatórios baseados em importações, o gateway utiliza as credenciais que introduziu nos campos **Nome de utilizador** e **Palavra-passe** no momento em que criou a origem de dados. Por outras palavras, o SSO do Kerberos **não** é utilizado. Além disso, no momento da publicação, confirme que seleciona o gateway que configurou para o SSO, se tiver vários gateways. Já deverá conseguir atualizar o relatório no serviço Power BI ou criar um novo relatório com base no conjunto de dados publicado.

Esta configuração funciona na maioria dos casos. No entanto, com o Kerberos podem existir configurações diferentes, dependendo do seu ambiente. Se, ainda assim, o relatório não carregar, contacte o administrador do domínio para uma investigação mais aprofundada. Se a origem de dados for o SAP BW, também poderá consultar as secções de resolução de problemas das páginas de configuração específicas da origem para a [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md#troubleshooting) e a [gx64krb5/gsskrb5](service-gateway-sso-kerberos-sap-bw-gx64krb.md#troubleshooting), conforme a biblioteca SNC que escolheu.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o **gateway de dados no local** e o **DirectQuery**, consulte os seguintes recursos:

* [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-onprem) (O que é um gateway de dados no local?)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
