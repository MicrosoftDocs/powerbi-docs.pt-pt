---
title: Resolver problemas de gateways – Power BI
description: Este artigo fornece formas de resolver problemas do gateway de dados no local e do Power BI. Fornece possíveis soluções para problemas conhecidos, bem como as ferramentas para ajudá-lo.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: troubleshooting
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: b420c827df3c18796d0d46514f81170f202eafbd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881561"
---
# <a name="troubleshoot-gateways---power-bi"></a>Resolver problemas de gateways – Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Este artigo aborda alguns problemas comuns ao utilizar o gateway de dados no local com o Power BI. Caso se depare com um problema que não está indicado aqui, pode utilizar o site da [Comunidade](https://community.powerbi.com) do Power BI. Em alternativa, pode criar um [pedido de suporte](https://powerbi.microsoft.com/support).

## <a name="configuration"></a>Configuração

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>Erro: O serviço Power BI reportou o gateway local como inacessível. Reinicie o gateway e tente novamente.

No final da configuração, o serviço Power BI será chamado novamente para validar o gateway. O serviço Power BI não comunica o gateway como dinâmico. Reiniciar o serviço Windows pode permitir que a comunicação seja bem-sucedida. Para obter mais informações, pode recolher e rever os registos conforme descrito na secção [Recolher relatórios da aplicação do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

## <a name="data-sources"></a>Origens de dados

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>Erro: Não é possível ligar. Detalhes: “Credenciais de ligação inválidas”

Em **Mostrar detalhes**, será apresentada a mensagem de erro recebida da origem de dados. Para o SQL Server, verá algo semelhante ao seguinte:

    Login failed for user 'username'.

Verifique se tem o nome de utilizador e a palavra-passe corretos. Verifique também se essas credenciais podem ligar à origem de dados com êxito. Verifique se a conta que está a ser utilizada corresponde ao método de autenticação.

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>Erro: Não é possível ligar. Detalhes: “Não é possível ligar à base de dados”

Conseguimos ligar ao servidor, mas não à base de dados fornecida. Verifique o nome da base de dados e se as credenciais do utilizador têm a permissão adequada para aceder a essa base de dados.

Em **Mostrar detalhes**, será apresentada a mensagem de erro recebida da origem de dados. Para o SQL Server, verá algo semelhante ao seguinte:

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>Erro: Não é possível ligar. Detalhes: “Erro desconhecido no gateway de dados”

Este erro pode ocorrer por diferentes motivos. Não se esqueça de confirmar que pode ligar à origem de dados a partir do computador que aloja o gateway. Esta situação pode ocorrer devido ao facto de o servidor não estar acessível.

Em **Mostrar detalhes**, poderá ver um código de erro de **DM_GWPipeline_UnknownError**.

Também pode observar os **Registos de Eventos** > **Registos de Serviços e Aplicações** > **Serviço de gateway de dados no local** para obter mais informações.

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>Erro: Encontrámos um erro ao tentar ligar ao \<servidor\>. Detalhes: “Acedemos ao gateway de dados, mas o gateway não consegue aceder à origem de dados no local.”

Não é possível ligar à origem de dados especificada. Certifique-se de que valida as informações fornecidas para essa origem de dados.

Em **Mostrar detalhes**, poderá ver um código de erro de **DM_GWPipeline_Gateway_DataSourceAccessError**.

Se a mensagem de erro subjacente for semelhante à seguinte, significa que a conta que está a utilizar para a origem de dados não é um administrador de servidor para essa instância do Analysis Services. Para obter mais informações, veja [Grant server admin rights to an Analysis Services instance](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance) (Conceder direitos de administrador de servidor a uma instância do Analysis Services).

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

Se a mensagem de erro subjacente for semelhante à seguinte, pode significar que o atributo de diretório [token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx) (TGGAU) pode estar em falta na conta de serviço do Analysis Services.

    The username or password is incorrect.

Os domínios com acesso de compatibilidade anterior ao Windows 2000 terão o atributo TGGAU ativado. Os domínios criados mais recentemente não ativarão este atributo por predefinição. Para obter mais informações, veja [Algumas aplicações e APIs requerem acesso a informações de autorização em objetos de conta](https://support.microsoft.com/kb/331951).

Para confirmar se o atributo está ativado, siga estes passos.

1. Ligue à máquina do Analysis Services no SQL Server Management Studio. Nas propriedades de ligação Avançadas, inclua EffectiveUserName para o utilizador em questão e confira se o erro é reproduzido.
2. Pode utilizar a ferramenta dsacls do Active Directory para confirmar se o atributo está listado. Esta ferramenta encontra-se num controlador de domínio. Precisa de saber qual é o nome de domínio único da conta e transmitir esse nome à ferramenta.

        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"

    Pretende ver algo semelhante ao seguinte nos resultados:

            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

Para corrigir este problema, tem de ativar o TGGAU na conta utilizada para o serviço Windows do Analysis Services.

#### <a name="another-possibility-for-the-username-or-password-is-incorrect"></a>Outra possibilidade para "O nome de utilizador ou palavra-passe está incorreto".

Este erro pode também dever-se ao facto de o servidor do Analysis Services estar num domínio diferente do domínio dos utilizadores e não estar estabelecida uma confiança bidirecional.

Trabalhe com os administradores de domínios para verificar a relação de confiança entre os domínios.

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>Não é possível ver as origens de dados do gateway na experiência Obter Dados do Analysis Services a partir do serviço Power BI

Certifique-se de que a sua conta está listada no separador **Utilizadores** da origem de dados na configuração do gateway. Se não tiver acesso ao gateway, consulte o administrador do gateway e peça-lhe para verificar. Apenas as contas na lista **Utilizadores** podem ver a origem de dados listada na lista do Analysis Services.

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>Erro: não tem nenhum gateway instalado ou configurado para as origens de dados neste conjunto de dados.

Certifique-se de que adicionou uma ou mais origens de dados ao gateway, conforme descrito em [Adicionar uma origem de dados](service-gateway-data-sources.md#add-a-data-source). Se o gateway não aparecer no portal de administração em **Gerir gateways**, limpe a cache do browser ou termine e volte a iniciar sessão no serviço.

## <a name="datasets"></a>Conjuntos de Dados

### <a name="error-there-is-not-enough-space-for-this-row"></a>Erro: não existe espaço suficiente para esta linha.

Este erro ocorre se tiver uma única linha com um tamanho superior a 4 MB. Determine qual é a linha que pertence à sua origem de dados e tente filtrá-la ou reduzir o tamanho dessa linha.

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>Erro: o nome do servidor fornecido não corresponde ao nome do servidor no certificado SSL do SQL Server.

Este erro pode ocorrer quando o nome comum do certificado se destina ao nome de domínio completamente qualificado (FQDN) do servidor, mas só tiver fornecido o nome NetBIOS do servidor. Esta situação causa um erro de correspondência do certificado. Para resolver este problema, tem de fazer com que o nome do servidor na origem de dados do gateway e o ficheiro PBIX utilizem o FQDN do servidor.

### <a name="error-you-dont-see-the-on-premises-data-gateway-present-when-you-configure-scheduled-refresh"></a>Erro: não consegue ver o gateway de dados no local ao configurar a atualização agendada.

Alguns cenários diferentes podem ser responsáveis por este erro:

- O nome do servidor e da base dados não correspondem ao que foi introduzido no Power BI Desktop e à origem de dados configurada para o gateway. Os nomes têm de ser os mesmos. Não são sensíveis a maiúsculas e minúsculas.
- A sua conta não está listada no separador **Utilizadores** da origem de dados na configuração do gateway. Tem de ser adicionado a essa lista pelo administrador do gateway.
- O ficheiro do Power BI Desktop inclui múltiplas origens de dados e nem todas foram configuradas com o gateway. Tem de definir cada origem de dados com o gateway, para que este seja apresentado na atualização agendada.

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>Erro: os dados não comprimidos recebidos no cliente do gateway excederam o limite.

A limitação exata é de 10 GB de dados não comprimidos por tabela. Se este problema ocorrer, existem boas opções para otimizar e evitar o mesmo. Em particular, reduzir a utilização de valores de cadeia altamente constantes e longos e, em alternativa, utilizar uma chave normalizada ou remover a coluna (se não estiver a ser utilizada) irá ajudar.

## <a name="reports"></a>Relatórios

### <a name="error-report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>Erro: O relatório não pôde aceder à origem de dados porque não tem acesso aos nossos dados através de um gateway de dados no local.

Geralmente, este erro deve-se a um dos seguintes motivos:

- As informações da origem de dados não correspondem às que estão no conjunto de dados subjacente. O nome do servidor e da base de dados têm de corresponder entre a origem de dados definida no gateway de dados no local e o que fornecer no Power BI Desktop. Se utilizar um endereço IP no Power BI Desktop, a origem de dados do gateway de dados no local terá de utilizar o mesmo endereço IP.
- Não existe nenhuma origem de dados disponível no gateway da organização. Pode configurar a origem de dados num gateway de dados no local novo ou existente.

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>Erro: Erro de acesso à origem de dados. Contacte o administrador do gateway.

Se este relatório utilizar uma ligação em direto do Analysis Services, poderia deparar-se com o problema de um valor transmitido para o EffectiveUserName não ser válido ou não ter permissões no computador do Analysis Services. Normalmente, um problema de autenticação deve-se ao facto de o valor que é transmitido para EffectiveUserName não corresponder a um nome principal de utilizador (UPN) local.

Para confirmar o nome de utilizador em vigor, siga estes passos.

1. Localize o nome do utilizador efetivo nos [registos do gateway](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).
2. Assim que o valor estiver a ser transmitido, confirme se está correto. Se for o seu utilizador, pode utilizar o seguinte comando numa linha de comandos para ver o UPN. O UPN tem o aspeto de um endereço de e-mail.

        whoami /upn

Opcionalmente, pode ver o que o Power BI obtém do Azure Active Directory.

1. Navegue para [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Selecione **Iniciar sessão** no canto superior direito.
3. Execute a consulta seguinte. Verá uma resposta JSON bastante grande.

        https://graph.windows.net/me?api-version=1.5
4. Procure **userPrincipalName**.

Se o UPN do Azure Active Directory não corresponder ao seu UPN local do Azure Active Directory, pode utilizar a funcionalidade [Mapear nomes de utilizador](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources) para substituí-lo por um valor válido. Em alternativa, pode consultar o seu administrador de inquilinos ou administrador do Active Directory local para alterar o seu UPN.

## <a name="kerberos"></a>Kerberos

Se o servidor de bases de dados subjacente e o gateway de dados no local não estiverem configurados corretamente para a [delegação restrita de Kerberos](service-gateway-sso-kerberos.md), ative o [registo verboso](/data-integration/gateway/service-gateway-performance#slow-performing-queries) no gateway. Em seguida, investigue com base nos erros ou rastreios nos ficheiros de registo do gateway como um ponto de partida para a resolução de problemas. Para recolher registos do gateway para visualização, veja a secção [Recolher relatórios da aplicação do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

### <a name="impersonationlevel"></a>ImpersonationLevel

O ImpersonationLevel está relacionado com a configuração do SPN ou a definição da política local.

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**Solução**

Siga estes passos para resolver o problema.

1. Configure um SPN para o gateway no local.
2. Configure a delegação restrita no Active Directory.

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException: Falha ao criar a identidade do Windows para o ID do utilizador

FailedToImpersonateUserException ocorrerá se não conseguir representar em nome de outro utilizador. Este erro também poderá ocorrer se a conta que estiver a tentar representar for de outro domínio que não o domínio de serviço de gateway ativo. Esta é uma limitação.

**Solução**

* Confirme se a configuração está correta de acordo com os passos na secção anterior "ImpersonationLevel".
* Verifique se o ID de utilizador que está a tentar representar é uma conta do Active Directory válida.

### <a name="general-error-1033-error-while-you-parse-the-protocol"></a>Erro geral: erro 1033 ao analisar o protocolo

Será apresentado o erro 1033 quando o seu ID externo configurado no SAP HANA não corresponder ao início de sessão se o utilizador for representado com o UPN (alias@domain.com). Nos registos, verá o "UPN Original alias@domain.com substituído por um UPN novo alias@domain.com" na parte superior dos registos de erros, conforme mostrado aqui:

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**Solução**

* O SAP HANA requer que o utilizador representado utilize o atributo sAMAccountName no Active Directory (alias do utilizador). Se este atributo não estiver correto, será apresentado o erro 1033.

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount.png)

* Nos registos, verá sAMAccountName (alias) e não o UPN, que é o alias seguido do domínio (alias@doimain.com).

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] Falha na ligação de comunicações:-10709 Falha na ligação (RTE:[-1] erro do Kerberos. Sério: "Falha diversa [851968]." Menor: "nenhuma credencial disponível no pacote de segurança."

Será apresentada a mensagem de erro "-10709 Falha na ligação" se a sua delegação não estiver configurada corretamente no Active Directory.

**Solução**

* Certifique-se de que tem o servidor do SAP Hana no separador Delegação no Active Directory da conta do serviço de gateway.

   ![Separador Delegação](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="refresh-history"></a>Histórico de atualizações

Quando utiliza o gateway para uma atualização agendada, o **Histórico de atualizações** pode ajudar a ver que erros ocorreram. Também pode fornecer dados úteis se precisar de criar um pedido de suporte. Pode ver as atualizações agendadas ou a pedido. Os seguintes passos mostram como pode aceder ao histórico de atualizações.

1. No painel de navegação do Power BI, em **Conjuntos de Dados**, selecione um conjunto de dados. Abra o menu e selecione **Agendar atualização**.

    ![Como selecionar Agendar Atualização](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. Em **Definições para...** &gt; **Agendar atualização**, selecione **Histórico de atualizações**.

    ![Selecionar Histórico de Atualizações](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![Aspeto do Histórico de Atualizações](media/service-gateway-onprem-tshoot/refresh-history.png)

Para obter mais informações sobre a resolução de problemas de cenários de atualização, veja [Resolução de problemas de cenários de atualização](refresh-troubleshooting-refresh-scenarios.md).

## <a name="fiddler-trace"></a>Rastreio do Fiddler

[Fiddler](https://www.telerik.com/fiddler) é uma ferramenta gratuita da Telerik que monitoriza o tráfego HTTP. Pode ver as comunicações com o serviço Power BI a partir do computador de cliente. Esta lista de tráfego pode mostrar erros e outras informações relacionadas.

![Utilizar o rastreio do Fiddler](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>Próximos passos

* [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot)
* [Configurar as definições de proxy do gateway de dados no local](/data-integration/gateway/service-gateway-proxy)  
* [Gerir a sua origem de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gerir a sua origem de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gerir a sua origem de dados – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gerir a origem de dados – atualização importada/agendada](service-gateway-enterprise-manage-scheduled-refresh.md)  

Mais perguntas? Experimente perguntar à [Comunidade do Power BI](https://community.powerbi.com/).
