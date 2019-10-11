---
title: Utilizar o Kerberos para início de sessão único (SSO) no SAP BW com gx64krb5
description: Configurar o seu servidor SAP BW para ativar o SSO a partir do serviço Power BI com gx64krb5
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4932f00fa7585c6b4f9186c29b65700d7a14fbea
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968728"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Utilizar o Kerberos para início de sessão único (SSO) no SAP BW com gx64krb5

Este artigo descreve como configurar a sua origem de dados SAP BW para ativar o SSO a partir do serviço Power BI com o gx64krb5.

> [!NOTE]
> Pode concluir os passos neste artigo, além dos passos em [Configurar o SSO do Kerberos](service-gateway-sso-kerberos.md), para ativar a atualização baseada em SSO para relatórios baseados em Servidor de Aplicações SAP BW no serviço Power BI. No entanto, a Microsoft recomenda a utilização da CommonCryptoLib, e não do gx64krb5, como a sua biblioteca SNC. O SAP já não oferece suporte para gx64krb5 e os passos necessários para o configurar para utilização com o gateway são significativamente mais complexos em comparação com a CommonCryptoLib. Consulte [Configurar o SAP BW para SSO através da biblioteca CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) para saber como configurar o SSO com a CommonCryptoLib. Deve concluir a configuração para CommonCryptoLib _ou_ gx64krb5. Não conclua os passos de configuração para ambas as bibliotecas.

### <a name="set-up-gx64krb5-on-gateway-machine-and-the-sap-bw-server"></a>Configurar o gx64krb5 nos computadores de gateway e no servidor do SAP BW
Este guia tenta ser tão abrangente quanto possível. Se já tiver concluído alguns destes passos, poderá ignorá-los. Por exemplo, já poderá ter configurado o seu servidor do SAP BW para o SSO com o gx64krb5.

### <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>Configurar o gx64krb5 nos computadores de gateway e no servidor do SAP BW

> [!NOTE]
> A biblioteca `gx64krb5` deixou de ser suportada ativamente pelo SAP. Para obter mais informações, veja [SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295) (Nota SAP 352295). Além disso, tenha em atenção que a biblioteca `gx64krb5` não permite ligações SSO do gateway de dados a Servidores de Mensagens do SAP BW. Apenas são possíveis ligações para Servidores Aplicacionais do SAP BW. Esta restrição apenas de Servidor de Aplicações não existe se utilizar [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) como a sua biblioteca SNC. Outras bibliotecas SNC também podem funcionar para o SSO do BW, contudo, não são oficialmente suportadas pela Microsoft.

A biblioteca `gx64krb5` tem de ser utilizada pelo cliente e pelo servidor para estabelecer uma ligação SSO através do gateway, isto é, o cliente e o servidor têm de utilizar a mesma biblioteca SNC.

1. Transfira a biblioteca `gx64krb5` de [SAP Note 2115486](https://launchpad.support.sap.com/) (necessário um utilizador S do SAP). Certifique-se de que tem, pelo menos, a versão 1.0.11.x. Transfira também `gsskrb5` (a versão de 32 bits da biblioteca) se quiser testar a ligação SSO na GUI do SAP antes de tentar a ligação SSO através do gateway (recomendado). A versão de 32 bits é obrigatória para testar com a GUI do SAP porque a GUI do SAP só está disponível em 32 bits.

1. Coloque a biblioteca `gx64krb5` numa localização no seu computador de gateway que seja acessível pelo utilizador de serviço do gateway. Se quiser testar a ligação SSO com o SAP GUI, coloque também uma cópia da biblioteca `gsskrb5` no computador e defina a variável do ambiente **SNC_LIB** a apontar para o mesmo. O Utilizador de Serviço do gateway e os utilizadores do Active Directory (AD) que serão representados pelo Utilizador de Serviço necessitam de permissões de leitura e execução de permissões para a cópia da biblioteca `gx64krb5`. Recomendamos que conceda permissões no .dll ao grupo Utilizadores Autenticados. Para fins de teste, também pode conceder explicitamente estas permissões ao Utilizador de Serviço do gateway e ao utilizador do Active Directory que vai servir fazer testes.

1. Se o seu servidor BW ainda não tiver sido configurado para SSO com o gx64krb5, coloque outra cópia do .dll no seu computador do servidor SAP BW num local acessível pelo servidor do SAP BW. Veja a [documentação do SAP](https://launchpad.support.sap.com/#/notes/2115486) (é necessário um utilizador S) para obter mais informações sobre como configurar o gx64krb5 para utilização com um servidor do SAP BW.

1. Nos computadores de servidor e cliente, defina as variáveis de ambiente `SNC_LIB` e/ou `SNC_LIB_64`. Se usar gsskrb5, defina a variável `SNC_LIB` como o caminho absoluto de gsskrb5.dll. Se usar gx64krb5, defina a variável `SNC_LIB_64` como o caminho absoluto de gx64krb5.dll.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>Configurar um utilizador do serviço SAP BW e permitir a comunicação com o SNC no servidor do BW

Conclua esta secção se ainda não tiver configurado o seu servidor do SAP BW para comunicação com o SNC (por exemplo, SSO) através do gx64krb5.

> [!NOTE]
> Esta seção pressupõe que já tenha criado um Utilizador de Serviço para BW e associado um SPN adequado ao mesmo (por exemplo, algo que comece por `SAP/`).

1. Conceda ao utilizador de serviço acesso ao Servidor Aplicacional do SAP BW:

    1. Na máquina do servidor do SAP BW, adicione o Utilizador de Serviço ao grupo Administrador Local. Abra o programa Gestão de Computadores e identifique o grupo Administrador Local do seu servidor. Por exemplo:

        ![Captura de ecrã a mostrar o programa Gestão de Computadores](media/service-gateway-sso-kerberos/computer-management.png)

    1. Faça duplo clique no grupo Administrador Local e selecione **Adicionar** para adicionar o seu utilizador de serviço ao grupo. Selecione **Verificar Nomes** para garantir que introduziu o nome corretamente. Selecione **OK**.

1. Defina o utilizador de Serviço do Servidor do SAP BW como o utilizador que inicia o serviço do servidor do SAP BW na máquina do servidor do SAP BW.

    1. Abra **Executar** e introduza **Services.msc**. Procure o serviço correspondente à sua instância do Servidor Aplicacional do SAP BW. Clique com o botão direito do rato no mesmo e selecione **Propriedades**.

        ![Captura de ecrã a mostrar Serviços, com a opção Propriedades realçada](media/service-gateway-sso-kerberos/server-properties.png)

    1. Mude para o separador **Início de sessão** e altere o utilizador para o seu utilizador do serviço SAP BW. Introduza a palavra-passe do utilizador e selecione **OK**.

1. Inicie sessão no seu servidor no SAP Logon e defina os parâmetros do seguinte perfil com a transação RZ10:

    1. Defina o parâmetro de perfil **snc/identity/as** como *p:&lt;o utilizador do serviço SAP BW que criou&gt;* , como *p:BWServiceUser\@MYDOMAIN.COM*. Repare no p: que precede o UPN do utilizador de serviço. Não é p:CN= como quando a Common Crypto Library é utilizada como biblioteca SNC.

    1. Defina o parâmetro de perfil **snc/gssapi\_lib** como *&lt;caminho para o gx64krb5.dll no computador do servidor BW&gt;* . Lembre-se de colocar a biblioteca numa localização à qual o Servidor Aplicacional do SAP BW possa aceder.

    1. Além disso, defina os seguintes parâmetros de perfil adicionais, ao alterar os valores conforme exigido para satisfazer as suas necessidades. Tenha em atenção que as últimas cinco opções permitem que os clientes liguem ao servidor do SAP BW com o SAP Logon, sem ser necessário ter o SNC configurado.

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

1. Após definir estes parâmetros de perfil, abra a Consola de Gestão de SAP na máquina do servidor e reinicie a instância do SAP BW. Se o servidor não iniciar, verifique que configurou os parâmetros de perfil corretamente. Para saber mais sobre as definições de parâmetro de perfil, veja a [documentação do SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Também pode consultar as informações de resolução de problemas mais adiante nesta secção se tiver problemas.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Mapear um utilizador do SAP BW a um utilizador do Active Directory

Se ainda não o tiver feito, mapeie um utilizador do Active Directory a um utilizador do Servidor de Aplicações do SAP BW e teste a ligação SSO no SAP Logon.

1. Inicie sessão no seu servidor do SAP BW através do SAP Logon. Execute a transação SU01.

1. Para **User** (Utilizador), introduza o utilizador do SAP BW para o qual pretende ativar as ligações de SSO (a captura de ecrã abaixo mostra a preparação das permissões para BIUSER). Selecione o ícone **Edit** (Editar) (a imagem de uma caneta) junto ao canto superior esquerdo da janela SAP Logon.

    ![Captura de ecrã a mostrar a Gestão de utilizador do SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Selecione o separador **SNC**. Na caixa de entrada SNC Name (Nome do SNC), introduza *p:&lt;o seu utilizador do Active Directory&gt;@&lt;o seu domínio&gt;* . Repare no p: obrigatório que tem de preceder o UPN do utilizador do Active Directory. O utilizador do Active Directory que especificar deve pertencer à pessoa ou organização para a qual pretende ativar o acesso de SSO ao Servidor Aplicacional do SAP BW. Por exemplo, se quiser ativar o acesso de SSO para o utilizador *testuser\@TESTDOMAIN.COM*, introduza *p:testuser\@TESTDOMAIN.COM*.

    ![Captura de ecrã a mostrar a Gestão de utilizadores do SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Selecione o ícone **Guardar** (a imagem de uma disquete) junto ao canto superior esquerdo do ecrã.

### <a name="test-sign-in-via-sso"></a>Testar o início de sessão através do SSO

Verifique se pode iniciar sessão no servidor com o SAP Logon através do SSO enquanto utilizador do Active Directory para o qual ativou o acesso de SSO.

1. Enquanto utilizador do Active Directory para o qual ativou o acesso de SSO, inicie sessão num computador no seu domínio no qual o SAP Logon esteja instalado. Inicie o SAP Logon e crie uma nova ligação.

1. Copie o ficheiro .dll `gsskrb5` que transferiu anteriormente para uma localização no computador no qual iniciou sessão. Defina a variável do ambiente `SNC_LIB` como o caminho absoluto desta localização.

1. Inicie o SAP Logon e crie uma nova ligação.

1. No ecrã **Create New System Entry** (Criar Nova Entrada do Sistema), selecione **User Specified System** (Sistema Especificado pelo Utilizador) e, em seguida, **Next** (Seguinte).

    ![Captura de ecrã a mostrar Create New System Entry (Criar Nova Entrada do Sistema)](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Preencha os detalhes adequados no ecrã seguinte, incluindo o servidor da aplicação, número da instância e ID do sistema. Em seguida, selecione **Finish** (Concluir).

1. Clique com o botão direito do rato na nova ligação e selecione **Properties** (Propriedades). Selecione o separador **Network** (Rede). Na caixa de texto **SNC Name** (Nome do SNC), introduza *p:&lt;o UPN do utilizador do serviço SAP BW&gt;* , como *p:BWServiceUser\@MYDOMAIN.COM*. Em seguida, selecione **OK**.

    ![Captura de ecrã a mostrar System Entry Properties (Propriedades de Entrada do Sistema)](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Faça duplo clique na ligação que criou para tentar efetuar uma ligação SSO ao servidor do SAP BW. Se a ligação for bem-sucedida, avance para o passo seguinte. Caso contrário, reveja os passos anteriores neste documento para se certificar de que estes foram concluídos corretamente ou reveja a secção de resolução de problemas abaixo. Tenha em atenção que se não conseguir ligar ao servidor do SAP BW através do SSO neste contexto, não poderá fazê-lo no contexto de gateways.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Adicionar entradas de registo ao computador do gateway

Adicione entradas de registo necessárias ao registo do computador no qual o gateway está instalado, bem como em computadores destinados a ligar-se a partir do Power BI Desktop. Eis os comandos a executar:

1. ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

1. ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Adicionar uma nova origem de dados do Servidor Aplicacional do SAP BW ao serviço Power BI ou editar uma existente

1. Na janela de configuração da origem de dados, introduza o **Nome do anfitrião**, **Número do Sistema** e **ID de cliente** do Servidor Aplicacional como faria para iniciar sessão no seu servidor do SAP BW a partir do Power BI Desktop.

1. No campo **Nome do Parceiro SNC**, introduza *p:&lt;o SPN que mapeou ao utilizador do serviço SAP BW&gt;* . Por exemplo, se o SPN for **SAP/BWServiceUser\@MYDOMAIN.COM**, deverá introduzir *p:SAP/BWServiceUser\@MYDOMAIN.COM* no campo **Nome do Parceiro SNC**.

1. Para a Biblioteca SNC, selecione **SNC\_LIB** ou **SNC\_LIB\_64**. Certifique-se de que **SNC\_LIB\_64** no computador do gateway aponta para gx64krb5.dll. Como alternativa, pode selecionar a opção "Personalizado" e fornecer o caminho absoluto do gx64krb5.dll (no computador do gateway).

1. Selecione a caixa **Utilizar SSO através de Kerberos para consultas do DirectQuery** e selecione **Aplicar**. Se a ligação do teste não for bem-sucedida, verifique se os passos da configuração anterior foram concluídos corretamente.

1. [Executar um relatório do Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Resolução de problemas

### <a name="troubleshoot-gx64krb5-configuration"></a>Resolver problemas de configuração do gx64krb5

Caso se depare com problemas, siga estes passos para resolver o problema da instalação do gx64krb5 e das ligações SSO.

* Ver os registos do servidor (…work\dev\_w0 no computador do servidor) pode ser útil na resolução de erros com que se depare na conclusão dos passos de configuração do gx64krb5. Isto aplica-se especialmente se o servidor do SAP BW não iniciar após os parâmetros de perfil terem sido alterados.

* Se não conseguir iniciar o serviço SAP BW devido a uma falha de início de sessão, poderá ter fornecido a palavra-passe errada quando configurou o utilizador de início de sessão do SAP BW. Verifique a palavra-passe ao iniciar sessão numa máquina no seu ambiente do Active Directory como um utilizador do serviço SAP BW.

* Caso sejam apresentados erros sobre as credenciais da origem de dados subjacente (como o SQL Server) que impeçam o arranque do servidor, verifique se concedeu ao utilizador do serviço acesso à base de dados do SAP BW.

* Poderá ser apresentada a seguinte mensagem: *(GSS-API) specified target is unknown or unreachable* ([GSS-API] O destino especificado é desconhecido ou não é alcançável). Normalmente significa que especificou o nome do SNC errado. Certifique-se de que utiliza "p:" e não "p:CN=" ou qualquer outra coisa na aplicação cliente sem ser o UPN do utilizador do serviço.

* Poderá ser apresentada a seguinte mensagem: *(GSS-API) An invalid name was supplied* ([GSS-API] Foi fornecido um nome inválido). Certifique-se de que "p:" se encontra no valor do parâmetro de perfil de identidade do SNC do servidor.

* Poderá ser apresentada a seguinte mensagem: *(SNC error) the specified module could not be found* ([Erro de SNC] Não foi possível encontrar o módulo especificado). Normalmente isto acontece quando coloca o `gx64krb5.dll` num local que exige privilégios elevados (direitos de administrador) para aceder.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Resolver problemas de conectividade do gateway

1. Verifique os registos do gateway. Abra a aplicação de configuração do gateway e selecione **Diagnóstico** e, em seguida, **Exportar registos**. Os erros mais recentes estão na parte inferior de qualquer ficheiro de registo que examinar.

    ![Captura de ecrã a mostrar a aplicação Gateway de dados no local, com a opção Diagnóstico realçada](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Ative o rastreio do SAP BW e analise os ficheiros de registo gerados. Existem vários tipos diferentes de rastreio do SAP BW disponíveis (como o rastreio de CPIC). Consulte a documentação do SAP para obter mais informações.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre o **gateway de dados no local** e o **DirectQuery**, consulte os seguintes recursos:

* [What is an on-premises data gateway?](/data-integration/gateway/service-gateway-onprem) (O que é um gateway de dados no local?)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
