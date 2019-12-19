---
title: Utilizar o Kerberos para início de sessão único (SSO) no SAP BW com gx64krb5
description: Configurar o seu servidor SAP BW para ativar o SSO a partir do serviço Power BI com gx64krb5
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c8b62cf798d2fbbd09dab0603d216448d04487c
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000141"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Utilizar o Kerberos para início de sessão único (SSO) no SAP BW com gx64krb5

Este artigo descreve como configurar a sua origem de dados do SAP BW para ativar o SSO a partir do serviço Power BI com a gx64krb5.

> [!NOTE]
> Pode concluir os passos neste artigo, além dos passos em [Configurar o SSO do Kerberos](service-gateway-sso-kerberos.md), para ativar a atualização baseada em SSO para relatórios baseados em Servidor de Aplicações SAP BW no serviço Power BI. No entanto, a Microsoft recomenda a utilização da CommonCryptoLib, e não do gx64krb5, como a sua biblioteca SNC. O SAP já não suporta a gx64krb5 e os passos necessários para a configurar para o gateway são significativamente mais complexos em comparação com a CommonCryptoLib. Para obter mais informações sobre como configurar o SSO com a CommonCryptoLib, veja como [Configurar o SAP BW para SSO através da biblioteca CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md). Deve utilizar CommonCryptoLib _ou_ gx64krb5 como a biblioteca SNC. Não conclua os passos de configuração para ambas as bibliotecas.

Este guia é abrangente. Se já tiver concluído alguns dos passos descritos, poderá ignorá-los. Por exemplo, já poderá ter configurado o seu servidor do SAP BW para o SSO com o gx64krb5.

## <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>Configurar o gx64krb5 nos computadores de gateway e no servidor do SAP BW

> [!NOTE]
> A biblioteca gx64krb5 já não é suportada pelo SAP. Para obter mais informações, veja [SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295) (Nota SAP 352295). Repare que a gx64krb5 não permite ligações de SSO do gateway de dados para os Servidores de Mensagens do SAP BW; apenas são possíveis ligações aos Servidores de Aplicações do SAP BW. Esta restrição não existe se utilizar [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) como a sua biblioteca SNC. Embora outras bibliotecas SNC também possam funcionar para o SSO do BW, não são oficialmente suportadas pela Microsoft.

A biblioteca gx64krb5 tem de ser utilizada pelo cliente e pelo servidor para estabelecer uma ligação SSO através do gateway. Ou seja, tanto o cliente como o servidor devem estar a utilizar a mesma biblioteca SNC.

1. Transfira a biblioteca gx64krb5.dll da [Nota SAP 2115486](https://launchpad.support.sap.com/) (é necessário um utilizador S do SAP). Certifique-se de que tem, pelo menos, a versão 1.0.11.x. Transfira também a biblioteca gsskrb5.dll (a versão de 32 bits da biblioteca) se quiser testar a ligação SSO na GUI do SAP antes de tentar a ligação SSO através do gateway (recomendado). A versão de 32 bits é obrigatória para testar com a GUI do SAP porque a GUI do SAP só está disponível em 32 bits.

1. Coloque a biblioteca gx64krb5.dll numa localização no seu computador de gateway que seja acessível pelo utilizador de serviço do gateway. Se quiser testar a ligação SSO com a GUI do SAP, coloque também uma cópia da biblioteca gsskrb5.dll no computador e defina a variável do ambiente **SNC_LIB** para apontar para o mesmo. O utilizador de serviço do gateway e os utilizadores do Active Directory (AD) que serão representados pelo utilizador de serviço necessitam de permissões de leitura e execução para a cópia da biblioteca gx64krb5.dll. Recomendamos que conceda permissões no .dll ao grupo Utilizadores Autenticados. Para fins de teste, também pode conceder explicitamente estas permissões ao utilizador de serviço do gateway e ao utilizador do Active Directory que vai utilizar para fazer testes.

1. Se o seu servidor BW ainda não tiver sido configurado para SSO com a biblioteca gx64krb5.dll, coloque outra cópia do .dll no seu computador do servidor do SAP BW num local acessível pelo servidor do SAP BW. 

    Para obter mais informações sobre como configurar a biblioteca gx64krb5.dll para utilização com um servidor do SAP BW, veja a [documentação do SAP](https://launchpad.support.sap.com/#/notes/2115486) (é necessário um utilizador S do SAP).

1. Nos computadores de servidor e cliente, defina as variáveis de ambiente **SNC_LIB** e **SNC_LIB_64**: 
    - Se utilizar a biblioteca gsskrb5.dll, defina a variável **SNC_LIB** como o caminho absoluto. 
    - Se utilizar a biblioteca gx64krb5.dll, defina a variável **SNC_LIB_64** como o caminho absoluto.

## <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>Configurar um utilizador do serviço SAP BW e permitir a comunicação com o SNC no servidor do BW

Conclua esta secção se ainda não tiver configurado o seu servidor do SAP BW para comunicação com o SNC (por exemplo, SSO) através da gx64krb5.

> [!NOTE]
> Esta secção pressupõe que já tenha criado um utilizador de serviço para BW e associado um SPN adequado ao mesmo (ou seja, um nome que comece por *SAP/*).

1. Conceda ao utilizador de serviço acesso ao Servidor Aplicacional do SAP BW:

    1. No computador do servidor do SAP BW, adicione o utilizador de serviço ao grupo Administrador Local. Abra o programa **Gestão de Computadores** e identifique o grupo Administrador Local do seu servidor. 

        ![Programa de Gestão de Computadores](media/service-gateway-sso-kerberos/computer-management.png)

    1. Faça duplo clique no grupo Administrador Local e selecione **Adicionar** para adicionar o seu utilizador de serviço ao grupo. 

    1. Selecione **Verificar Nomes** para garantir que introduziu o nome corretamente e, em seguida, selecione **OK**.

1. Defina o utilizador de serviço do servidor do SAP BW como o utilizador que inicia o serviço do servidor do SAP BW no computador do servidor do SAP BW:

    1. Abra **Executar** e introduza **Services.msc**. 

    1. Localize o serviço correspondente à instância do Servidor de Aplicações do SAP BW, clique com o botão direito do rato no mesmo e selecione **Propriedades**.

        ![Captura de ecrã a mostrar Serviços, com a opção Propriedades realçada](media/service-gateway-sso-kerberos/server-properties.png)

    1. Mude para o separador **Início de sessão** e altere o utilizador para o seu utilizador do serviço SAP BW. 

    1. Introduza a palavra-passe do utilizador e selecione **OK**.

1. No SAP Logon, inicie sessão no seu servidor e defina os parâmetros do seguinte perfil com a transação RZ10:

    1. Defina o parâmetro de perfil **snc/identity/as** para *p:&lt;utilizador do serviço SAP BW que criou&gt;*. Por exemplo, *p:BWServiceUser\@MYDOMAIN.COM*. Observe que *p:* precede o UPN do utilizador do serviço, em oposição a *p:CN=*, que precede o UPN quando utiliza a CommonCryptoLib como biblioteca SNC.

    1. Defina o parâmetro de perfil **snc/gssapi\_lib** como *&lt;caminho para a biblioteca gx64krb5.dll no servidor BW&gt;*. Coloque a biblioteca numa localização à qual o Servidor de Aplicações do SAP BW possa aceder.

    1. Defina os seguintes parâmetros de perfil adicionais, ao alterar os valores conforme exigido para satisfazer as suas necessidades. As últimas cinco opções permitem que os clientes liguem ao servidor do SAP BW com o SAP Logon, sem ser necessário ter o SNC configurado.

        | **Definição** | **Valor** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Defina a propriedade **snc/enable** como 1.

1. Após definir estes parâmetros de perfil, abra a SAP Management Console no computador do servidor e reinicie a instância do SAP BW. 

   Se o servidor não iniciar, verifique que configurou os parâmetros de perfil corretamente. Para obter mais informações sobre as definições de parâmetro de perfil, veja a [documentação do SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Pode também consultar a secção [Resolução de problemas](#troubleshooting) neste artigo.

## <a name="map-an-sap-bw-user-to-an-active-directory-user"></a>Mapear um utilizador do SAP BW a um utilizador do Active Directory

Se ainda não o tiver feito, mapeie um utilizador do Active Directory a um utilizador do Servidor de Aplicações do SAP BW e teste a ligação SSO no SAP Logon.

1. Inicie sessão no seu servidor do SAP BW através do SAP Logon. Execute a transação SU01.

1. Para **User** (Utilizador), introduza o utilizador do SAP BW para o qual pretende ativar a ligação de SSO. Selecione o ícone de caneta **Edit** (Editar) junto ao canto superior esquerdo da janela do SAP Logon.

    ![Ecrã User maintenance (Manutenção de utilizadores) do SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Selecione o separador **SNC**. Na caixa de entrada SNC Name (Nome do SNC), introduza *p:&lt;o seu utilizador do Active Directory&gt;@&lt;o seu domínio&gt;*. Para o nome SNC, *p:* tem de preceder o UPN do utilizador do Active Directory. Repare que o UPN é sensível a maiúsculas e minúsculas.

   O utilizador do Active Directory que especificar deve pertencer à pessoa ou organização para a qual pretende ativar o acesso de SSO ao Servidor Aplicacional do SAP BW. Por exemplo, se quiser ativar o acesso de SSO para o utilizador testuser\@TESTDOMAIN.COM, introduza *p:testuser\@TESTDOMAIN.COM*.

    ![Ecrã Maintain users (Manutenção de utilizadores) do SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Selecione o ícone de disquete **Save** (Guardar) junto ao canto superior esquerdo do ecrã.

## <a name="test-sign-in-via-sso"></a>Testar o início de sessão através do SSO

Verifique se pode iniciar sessão no servidor com o SAP Logon através do SSO enquanto utilizador do Active Directory para o qual ativou o acesso de SSO:

1. Enquanto utilizador do Active Directory para o qual ativou o acesso de SSO, inicie sessão num computador no seu domínio no qual o SAP Logon esteja instalado. Inicie o SAP Logon e crie uma nova ligação.

1. Copie o ficheiro gsskrb5.dll que transferiu anteriormente para uma localização no computador no qual iniciou sessão. Defina a variável de ambiente **SNC_LIB** como o caminho absoluto desta localização.

1. Inicie o SAP Logon e crie uma nova ligação.

1. No ecrã **Create New System Entry** (Criar Nova Entrada do Sistema), selecione **User Specified System** (Sistema Especificado pelo Utilizador) e, em seguida, selecione **Next** (Seguinte).

    ![Ecrã Create New System Entry (Criar Nova Entrada do Sistema)](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Preencha os detalhes adequados no ecrã seguinte, incluindo o servidor da aplicação, número da instância e ID do sistema. Em seguida, selecione **Finish** (Concluir).

1. Clique com o botão direito do rato na nova ligação, selecione **Properties** (Propriedades) e selecione o separador **Network** (Rede). 

1. Na caixa **SNC Name** (Nome do SNC), introduza *p:&lt;UPN do utilizador do serviço SAP BW&gt;*. Por exemplo, *p:BWServiceUser\@MYDOMAIN.COM*. Selecione **OK**.

    ![Ecrã System Entry Properties (Propriedades de Entrada do Sistema)](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Faça duplo clique na ligação que criou para tentar efetuar uma ligação SSO ao servidor do SAP BW. 

   Se a ligação for bem-sucedida, avance para a secção seguinte. Caso contrário, reveja os passos anteriores neste documento para se certificar de que foram concluídos corretamente ou veja a secção [Resolução de problemas](#troubleshooting). Se não conseguir ligar ao servidor do SAP BW através do SSO neste contexto, não poderá fazê-lo no contexto de gateways.

## <a name="add-registry-entries-to-the-gateway-machine"></a>Adicionar entradas de registo ao computador do gateway

Adicione entradas de registo necessárias ao registo do computador no qual o gateway está instalado, bem como em computadores destinados a ligar-se a partir do Power BI Desktop. Para adicionar estas entradas de registo, execute os seguintes comandos:

- ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

- ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

## <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Adicionar uma nova origem de dados do Servidor Aplicacional do SAP BW ao serviço Power BI ou editar uma existente

1. Na janela de configuração da origem de dados, introduza o **Nome do anfitrião**, **Número do Sistema** e **ID de cliente** do Servidor de Aplicações do SAP BW como faria para iniciar sessão no seu servidor do SAP BW a partir do Power BI Desktop.

1. No campo **Nome do Parceiro SNC**, introduza *p:&lt;SPN que mapeou ao utilizador do serviço SAP BW&gt;*. Por exemplo, se o SPN for SAP/BWServiceUser\@MYDOMAIN.COM, introduza *p:SAP/BWServiceUser\@MYDOMAIN.COM* no campo **Nome do Parceiro SNC**.

1. Para a Biblioteca SNC, selecione **SNC\_LIB** ou **SNC\_LIB\_64**. Certifique-se de que **SNC\_LIB\_64** no computador do gateway aponta para gx64krb5.dll. Em alternativa, pode selecionar a opção **Personalizado** e fornecer o caminho absoluto da biblioteca gx64krb5.dll no computador do gateway.

1. Selecione **Utilizar SSO através de Kerberos para consultas do DirectQuery** e selecione **Aplicar**. Se a ligação do teste não for bem-sucedida, verifique se os passos da configuração anterior foram concluídos corretamente.

1. [Executar um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Resolução de problemas

### <a name="troubleshoot-gx64krb5-configuration"></a>Resolver problemas de configuração do gx64krb5

Caso se depare com algum dos seguintes problemas, siga estes passos para resolver o problema da instalação da gx64krb5 e das ligações SSO:

* Encontra erros ao concluir os passos de configuração da gx64krb5. Por exemplo, o servidor do SAP BW não inicia depois de alterar os parâmetros do perfil. Veja os registos de servidor (...work\dev\_w0 no computador do servidor) para resolver estes erros. 

* Não é possível iniciar o serviço SAP BW devido a uma falha de início de sessão. Pode ter fornecido a palavra-passe incorreta ao definir o utilizador de *início de sessão* do SAP BW. Confirme a palavra-passe ao iniciar sessão como utilizador do serviço SAP BW num computador no seu ambiente do Active Directory.

* Caso sejam apresentados erros sobre as credenciais da origem de dados subjacente (por exemplo, o SQL Server) que impeçam o arranque do servidor, verifique se concedeu ao utilizador do serviço acesso à base de dados do SAP BW.

* É apresentada a seguinte mensagem: *(GSS-API) specified target is unknown or unreachable* ([GSS-API] O destino especificado é desconhecido ou não é alcançável). Normalmente, este erro significa que especificou o nome do SNC errado. Certifique-se de que utiliza apenas *p:* e não *p:CN=* para preceder o UPN do utilizador do serviço na aplicação cliente.

* É apresentada a seguinte mensagem: *(GSS-API) An invalid name was supplied* ([GSS-API] Foi fornecido um nome inválido). Certifique-se de que *p:* é o valor do parâmetro de perfil de identidade do SNC do servidor.

* É apresentada a seguinte mensagem: *(SNC error) the specified module could not be found* ([Erro de SNC] Não foi possível encontrar o módulo especificado). Geralmente, este erro é causado pela colocação da biblioteca gx64krb5.dll num local que necessita de privilégios (direitos de administrador) elevados para poder aceder-lhe.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Resolver problemas de conectividade do gateway

1. Verifique os registos do gateway. Abra a aplicação de configuração do gateway e selecione **Diagnóstico** e, em seguida, **Exportar registos**. Os erros mais recentes estão na parte final de qualquer ficheiro de registo que examinar.

    ![Aplicação de gateway de dados no local, com a opção Diagnóstico realçada](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Ative o rastreio do SAP BW e analise os ficheiros de registo gerados. Existem vários tipos diferentes de rastreio do SAP BW disponíveis (por exemplo, o rastreio de CPIC):

   a. para ativar o rastreio de CPIC, defina duas variáveis de ambiente: **CPIC\_TRACE** e **CPIC\_TRACE\_DIR**.

      A primeira variável define o nível de rastreio e a segunda variável define o diretório do ficheiro de rastreio. O diretório tem de ser uma localização na qual os membros do grupo Utilizadores Autenticados possam escrever. 
 
    b. Defina a variável **CPIC\_TRACE** para *3* e a variável **CPIC\_TRACE\_DIR** para o diretório no qual pretende que os ficheiros de rastreio sejam escritos. Por exemplo:

      ![Rastreio de CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    c. Reproduza o problema e certifique-se de que a variável **CPIC\_TRACE\_DIR** contém os ficheiros de rastreio. 
    
    d. Examine os conteúdos dos ficheiros de rastreio para determinar o problema de bloqueio. Por exemplo, poderá verificar que o gx64krb5.dll não foi carregado corretamente ou que um utilizador do Active Directory Domain Services diferente daquele que esperava iniciou a tentativa de ligação SSO.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o gateway de dados no local e o DirectQuery, veja os seguintes recursos:

* [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-onprem) (O que é um gateway de dados no local?)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
