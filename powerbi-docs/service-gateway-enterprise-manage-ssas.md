---
title: Gerir a sua origem de dados – Analysis Services
description: Como gerir o gateway de dados no local e as origens de dados que pertencem a esse gateway. Isto aplica-se ao Analysis Services no modo Multidimensional e de Tabela.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93475f6476f8baad73229473bd3ce60db68a320b
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271618"
---
# <a name="manage-your-data-source---analysis-services"></a>Gerir a sua origem de dados – Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Depois de [instalar o gateway de dados no local](/data-integration/gateway/service-gateway-install), terá de [adicionar as origens de dados](service-gateway-data-sources.md#add-a-data-source) que podem ser utilizadas com o gateway. Este artigo aborda como trabalhar com gateways e origens de dados do Analysis Services que são utilizados para uma atualização agendada ou ligações em direto.

Para saber mais sobre como configurar uma ligação em direto ao Analysis Services, [veja este vídeo.](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be)

> [!NOTE]
> Se tiver uma origem de dados do Analysis Services, terá de instalar o gateway num computador associado ao mesmo domínio que o seu servidor do Analysis Services.

## <a name="add-a-data-source"></a>Adicionar uma origem de dados

Para obter informações sobre como adicionar uma origem de dados, veja [Adicionar uma origem de dados](service-gateway-data-sources.md#add-a-data-source). Se estiver a ligar a um servidor Multidimensional ou Tabular, selecione o Analysis Services para o **Tipo de Origem de Dados**.

![Adicionar a origem de dados do Analysis Services](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Em seguida, é necessário preencher as informações sobre a origem de dados, que incluem o **Servidor** e a **Base de Dados**. O **Nome de Utilizador** e a **Palavra-passe** que inserir serão utilizados pelo gateway para ligar à instância do Analysis Services.

> [!NOTE]
> A conta do Windows inserida deve ter permissões de Administrador do Servidor para a instância à qual está a ligar. Se a palavra-passe desta conta estiver configurada para expirar, os utilizadores poderão receber um erro de ligação se a palavra-passe não estiver atualizada para a origem de dados. Para saber mais sobre a forma como as credenciais são armazenadas, veja [Armazenar credenciais encriptadas na cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Preenchimento das definições de origem de dados](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Selecione **Adicionar** depois de preencher tudo. Agora, pode utilizar esta origem de dados para atualização agendada ou ligações em direto numa instância no local do Analysis Services. Verá *Ligação Com Êxito* se tiver êxito.

![Apresentar o estado da ligação](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Definições avançadas

Opcionalmente, pode configurar o nível de privacidade da sua origem de dados. Isto controla a forma como os dados podem ser combinados. É utilizado apenas para atualização agendada. Não é aplicável às ligações em direto. Para saber mais sobre os níveis de privacidade da sua origem de dados, veja [Níveis de privacidade (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Definir o nível de privacidade](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Nomes de Utilizador com o Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Sempre que um utilizador interage com um relatório ligado ao Analysis Services, o nome do utilizador efetivo é passado para o gateway e, em seguida, para o seu servidor no local do Analysis Services. O endereço de e-mail com o qual inicia sessão no Power BI é aquele que transmitiremos ao Analysis Services como sendo o utilizador efetivo. Isto é transmitido na propriedade de ligação [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth). Este endereço de e-mail deve corresponder a um nome principal de utilizador (UPN) definido dentro do Domínio do Active Directory local. O UPN é uma propriedade de uma conta do Active Directory. Essa conta do Windows deverá, então, estar presente numa função do Analysis Services. Se não for encontrada nenhuma correspondência no Active Directory, o início de sessão não será bem-sucedido. Para saber mais sobre o Active Directory e a nomenclatura de utilizador, veja [Atributos de Nomenclatura de Utilizador](https://msdn.microsoft.com/library/ms677605.aspx).

Também pode [mapear o seu nome de início de sessão do Power BI com um UPN de diretório local](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources).

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mapeamento de nomes de utilizador para origens de dados do Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

O Power BI permite o mapeamento de nomes de utilizador para origens de dados do Analysis Services. Pode configurar regras para mapear um nome de utilizador com sessão iniciada no Power BI para um nome transmitido para o EffectiveUserName na ligação do Analysis Services. A funcionalidade de mapeamento nomes de utilizador é uma excelente forma de contornar o problema quando o seu nome de utilizador no AAD não corresponde a um UPN no Active Directory local. Por exemplo, se o seu endereço de e-mail for nancy@contoso.onmicrsoft.com, pode mapeá-lo para nancy@contoso.com, e esse valor será transmitido ao gateway.

Pode mapear os nomes de utilizador para o Analysis Services de duas formas diferentes:

* Remapeamento manual de utilizador
* Pesquisa de Propriedade no Local do Active Directory para remapear UPNs do AAD para utilizadores do Active Directory (mapeamento de pesquisa do AD)

Embora seja possível proceder ao mapeamento manual com recurso à segunda abordagem, este processo seria moroso e difícil de manter. É especialmente difícil fazê-lo quando a correspondência de padrões não é suficiente, por exemplo, quando os nomes de domínio do AAD são diferentes dos do AD no local ou quando os nomes de contas de utilizadores do AAD diferem dos do AD. Como tal, o mapeamento manual com a segunda abordagem não é recomendado.

Iremos descrever estas duas abordagens, por ordem, nas duas secções seguintes.

### <a name="manual-user-name-re-mapping"></a>Remapeamento manual do nome de utilizador

Para origens de dados do Analysis Services, pode configurar regras personalizadas do Nome Principal de Utilizador (UPN). Isto irá ajudá-lo, se os nomes de início de sessão do serviço Power BI não corresponderem ao UPN no diretório local. Por exemplo, se iniciar sessão no Power BI com john@contoso.com, mas o seu diretório UPN local for john@contoso.local, pode configurar uma regra de mapeamento para que john@contoso.local seja transmitido ao Analysis Services.

Para aceder ao ecrã de Mapeamento de UPN, efetue o seguinte.

1. Vá para o **Ícone de engrenagem** e selecione **Gerir Gateways**.
2. Expanda o gateway que contém a origem de dados do Analysis Services. Em alternativa, se ainda não tiver criado a origem de dados do Analysis Services, pode fazê-lo neste momento.
3. Selecione a origem de dados e selecione o separador **Utilizadores**.
4. Selecione **Mapear nomes de utilizador**.

    ![Ecrã de mapeamento de UPN](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Verá as opções para adicionar regras, bem como de teste para um determinado utilizador.

> [!NOTE]
> Poderá, inadvertidamente, alterar um utilizador. Por exemplo, se **Substituir (valor original)** for <em>@contoso.com</em> e **Por (Novo nome)** for <em>@contoso.local</em>, todos os utilizadores com um início de sessão que contenha <em>@contoso.com</em> serão então substituídos por <em>@contoso.local</em>. Por exemplo, se **Substituir (valor original)** for <em>dave@contoso.com</em> e **Por (Novo nome)** for <em>dave@contoso.local</em>, um utilizador com o início de sessão de v-dave@contoso.com seria enviado como v-dave<em>@contoso.local</em>.

### <a name="ad-lookup-mapping"></a>Mapeamento de pesquisa do AD

Para executar uma pesquisa de propriedade do AD no local para remapear UPNs do AAD para utilizadores do Active Directory, siga os passos nesta secção. Para começar, vamos rever como funciona.

No **serviço Power BI** ocorre o seguinte:

* Para cada consulta por um utilizador do AAD do Power BI para um servidor SSAS no local, uma cadeia UPN é transmitida, tal como:      firstName.lastName@contoso.com

> [!NOTE]
> Quaisquer mapeamentos manuais de utilizadores de UPN definidos na configuração da origem de dados do Power BI continuam a ser aplicados *antes* do envio da cadeia do nome de utilizador para o gateway de dados no local.

No gateway de dados no local com o Mapeamento de Utilizador Personalizado configurável, efetue o seguinte:

1. Localize o Active Directory para pesquisa (automática ou configurável).
2. Procure o atributo da Pessoa do AD (como *E-mail*) com base na cadeia UPN recebida ("firstName.lastName@contoso.com") do **serviço Power BI**.
3. Se a Pesquisa do AD falhar, este tenta utilizar o UPN transmitido juntamente como o EffectiveUser do SSAS.
4. Se a Pesquisa do AD for bem-sucedida, obtém o *UserPrincipalName* dessa Pessoa do AD.
5. Transmite o e-mail do *UserPrincipalName* como *EffectiveUser* para o SSAS, tal como <em>Alias@corp.on-prem.contoso</em>.

Para configurar o gateway de forma a efetuar a Pesquisa do AD:

1. [Transfira e instale o gateway mais recente](/data-integration/gateway/service-gateway-install).

2. No gateway, terá de alterar o **serviço de gateway de dados no local** para que seja executado com uma conta de domínio (em vez de uma conta de serviço local – caso contrário, a Pesquisa do AD não irá funcionar corretamente no tempo de execução). Aceda à [aplicação do gateway de dados no local](/data-integration/gateway/service-gateway-app) no seu computador e, em seguida, aceda a **Definições de serviço > Alterar conta do serviço**. Certifique-se de que tem a chave de recuperação deste gateway, uma vez que terá de restaurá-lo na mesma máquina, a menos que pretenda criar um novo gateway em vez disso. Terá de reiniciar o serviço de gateway para a alteração produzir efeito.

3. Navegue até à pasta de instalação do gateway, *C:\Program Files\On-premises data gateway* como administrador, para ter a certeza de que tem permissões de escrita, e abra o ficheiro *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Edite os seguintes dois valores de configuração, em conformidade com as *suas* configurações de atributo do Active Directory para os seus utilizadores do AD. Os valores de configuração apresentados abaixo são apenas exemplos – é necessário especificá-los com base na configuração do Active Directory. Estas configurações são sensíveis às maiúsculas e minúsculas, por isso certifique-se de que correspondem aos valores no Active Directory.

    ![Definições do Azure Active Directory](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Se não for fornecido nenhum valor para a configuração de ADServerPath, o gateway utilizará o Catálogo Global predefinido. Também pode especificar múltiplos valores para o ADServerPath. Cada valor tem de ser separado por um ponto e vírgula, tal como no seguinte exemplo.

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    O gateway analisa os valores para ADServerPath da esquerda para a direita até encontrar uma correspondência. Se não for encontrada nenhuma correspondência, será utilizado o UPN original. Certifique-se de que a conta que executa o serviço de gateway (PBIEgwService) tem permissões de consulta para todos os servidores do AD que especificou no ADServerPath.

    O gateway suporta dois tipos de ADServerPath, tal como nos seguintes exemplos.

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Reinicie o serviço **gateway de dados no local** para que a alteração da configuração produza efeito.

### <a name="working-with-mapping-rules"></a>Trabalhar com regras de mapeamento

Para criar uma regra de mapeamento, introduza um valor para **Nome original** e **Novo Nome** e, em seguida, selecione **Adicionar**.

| Campo | Descrição |
| --- | --- |
| Substituir (Nome original) |O endereço de e-mail com o qual iniciou sessão no Power BI. |
| Por (Novo Nome) |O valor pelo qual pretende substituí-lo. O resultado da substituição é o que será transmitido à propriedade *EffectiveUserName* para a ligação do Analysis Services. |

![Criar uma regra de mapeamento](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Quando seleciona um item na lista, pode optar por reordená-la com os **ícones de divisa** ou **Eliminar** a entrada.

![Reordenar um item na lista](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>Utilizar caráter universal (*)

Pode utilizar um caráter universal para a sua cadeia **Substituir (Nome original)** . Só pode ser utilizado isoladamente e não com qualquer outra parte da cadeia. Isto irá permitir aceitar todos os utilizadores e transmitirá um valor único à origem de dados. Isto é útil quando pretende que todos os utilizadores na sua organização utilizem o mesmo utilizador no seu ambiente local.

### <a name="test-a-mapping-rule"></a>Testar uma regra de mapeamento

Pode confirmar o nome pelo qual o nome será substituído ao introduzir um valor para **Nome original** e selecionando **Testar regra**.

![Testar uma regra de mapeamento](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> O serviço demora alguns minutos para começar a utilizar as regras que foram guardadas. No browser, a regra irá funcionar imediatamente.

### <a name="limitations-for-mapping-rules"></a>Limitações das regras de mapeamento

O mapeamento destina-se à origem de dados específica que está a ser configurada. Não é uma definição global. Se tiver múltiplas origens de dados do Analysis Services, terá de mapear os utilizadores a cada origem de dados.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autenticação numa origem de dados dinâmicos do Analysis Services

Sempre que um utilizador interage com o Analysis Services, o nome de utilizador efetivo é transmitido ao gateway e, em seguida, ao servidor do Analysis Services no local. O nome principal de utilizador (UPN), que é normalmente o endereço de e-mail com que inicia sessão na cloud, é o que transmitimos ao Analysis Services como utilizador efetivo. O UPN é transmitido na propriedade de ligação EffectiveUserName. Este endereço de e-mail deve corresponder a um UPN definido no domínio do Active Directory local. O UPN é uma propriedade de uma conta do Active Directory. Essa conta do Windows deverá estar presente numa função do Analysis Services para ter acesso ao servidor. O início de sessão não será efetuado com êxito se não for encontrada nenhuma correspondência no Active Directory.

O Analysis Services também pode fornecer a filtragem com base nesta conta. A filtragem pode ocorrer com segurança baseada em funções ou segurança ao nível da linha.

## <a name="role-based-security"></a>Segurança baseada em funções

Os modelos fornecem uma segurança baseada nas funções de utilizadores. As funções são definidas para um determinado projeto modelo durante a criação de conteúdos no SQL Server Data Tools – Business Intelligence (SSDT-BI) ou após a implementação de um modelo com o SQL Server Management Studio (SSMS). As funções contêm membros por nome de utilizador do Windows ou grupo do Windows. As funções definem as permissões que um utilizador tem para consultar ou realizar ações no modelo. A maioria dos utilizadores irá pertencer a uma função com permissões de Leitura. As outras funções são destinadas a administradores com permissões para processar itens, gerir bases de dados e gerir outras funções.

## <a name="row-level-security"></a>Row-level security

A segurança ao nível da linha é específica do Analysis Services. Os modelos podem fornecer uma segurança dinâmica ao nível da linha. A segurança dinâmica não é necessária num modelo tabular, ao contrário do que acontece quando existe pelo menos uma função à qual os utilizadores pertencem. Num nível elevado, a segurança dinâmica define o acesso de leitura de um utilizador aos dados diretamente para uma linha específica numa determinada tabela. De forma semelhante às funções, a segurança ao nível da linha depende do nome de utilizador do Windows de um utilizador.

A capacidade de um utilizador consultar e ver dados de modelo é determinada, primeiro, pelas funções das quais a conta de utilizador do Windows é membro e, em segundo lugar, pela segurança ao nível da linha dinâmica, se estiver configurada.

A implementação de segurança baseada em funções e a segurança ao nível da linha dinâmica em modelos ultrapassa o âmbito deste artigo. Pode saver mais em [Funções (SSAS Tabular)](https://msdn.microsoft.com/library/hh213165.aspx) e [Funções de Segurança (Analysis Services - Dados Multidimensionais)](https://msdn.microsoft.com/library/ms174840.aspx) no MSDN. Além disso, para compreender mais detalhadamente a segurança do modelo tabular, transfira e leia o documento técnico [Proteger o Modelo Semântico Tabular do BI](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>E o Azure Active Directory?

Os serviços cloud da Microsoft utilizam o [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) para lidar com os utilizadores que estão a efetuar a autenticação. O Azure Active Directory é o inquilino que contém nomes de utilizador e grupos de segurança. Normalmente, o endereço de e-mail de início de sessão de um utilizador é o mesmo que o UPN da conta.

Qual é a minha função local do Active Directory?

Para o Analysis Services determinar se um utilizador que esteja a ligar ao mesmo pertence a uma função com permissões para leitura de dados, o servidor tem de converter o nome de utilizador efetivo transmitido do AAD para o gateway e, em seguida, para o servidor do Analysis Services. O servidor do Analysis Services transmite o nome de utilizador efetivo a um controlador de domínio (DC) do Windows Active Directory. Em seguida, o DC do Active Directory valida o nome de utilizador efetivo como um UPN válido numa conta local e devolve esse nome de utilizador do Windows ao servidor do Analysis Services.

Não é possível utilizar EffectiveUserName num servidor do Analysis Services não associado a um domínio. O servidor do Analysis Services tem de estar associado a um domínio para evitar erros de início de sessão.

### <a name="how-do-i-tell-what-my-upn-is"></a>Como posso saber qual é o meu UPN?

Pode não saber qual é o seu UPN nem ser um administrador do domínio. Pode utilizar o seguinte comando da sua estação de trabalho para descobrir o UPN da sua conta.

    whoami /upn

O resultado será semelhante a um endereço de e-mail, mas trata-se do UPN que está na sua conta de domínio. Se estiver a utilizar uma origem de dados do Analysis Services para ligações em direto e se a mesma não corresponder ao endereço de e-mail com o qual iniciou sessão no Power BI, é recomendado que veja como [mapear nomes de utilizador](#mapping-usernames-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Sincronizar uma conta do Active Directory no local com o Azure Active Directory

As contas do Active Directory local devem corresponder ao Azure Active Directory se utilizar ligações em direto do Analysis Services. Tal como o UPN tem de corresponder entre as contas.

Os serviços cloud apenas conhecem as contas no Azure Active Directory. É irrelevante se adicionou uma conta no Active Directory local; se esta não existir no AAD, não pode ser utilizada. Existem várias formas de corresponder as contas do Active Directory local ao Azure Active Directory.

1. Pode adicionar contas manualmente ao Azure Active Directory.

   Pode criar uma conta no portal do Azure ou no centro de administração do Microsoft 365 e o nome da conta tem de corresponder ao UPN da conta do Active Directory local.

2. Pode utilizar a ferramenta [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) para sincronizar as contas locais no inquilino do Azure Active Directory.

   A ferramenta Azure AD Connect fornece opções para a sincronização de diretórios e a configuração da autenticação, incluindo a sincronização de hash da palavra-passe, autenticação pass-through e federação. Se não for administrador de inquilinos ou administrador do domínio local, terá de contactar o administrador de TI para efetuar esta configuração.

A utilização do Azure AD Connect assegura que o UPN terá correspondência entre o AAD e o Active Directory local.

> [!NOTE]
> A sincronização de contas com a ferramenta Azure AD Connect criará novas contas no inquilino do AAD.

## <a name="using-the-data-source"></a>Utilizar a origem de dados

Depois de criar a origem de dados, esta ficará disponível para utilização com qualquer uma das ligações em direto ou através da atualização agendada.

> [!NOTE]
> Os nomes do servidor e da base de dados no Power BI Desktop e na origem de dados do gateway de dados no local têm de corresponder.

A ligação entre o conjunto de dados e a origem de dados no gateway é baseada no nome do servidor e no nome da base de dados. Estes têm de corresponder. Por exemplo, se fornecer um Endereço IP ao nome do servidor no Power BI Desktop, terá de utilizar o Endereço IP para a origem de dados na configuração do gateway. Se utilizar *SERVIDOR\INSTÂNCIA* no Power BI Desktop, terá de utilizar o mesmo na origem de dados configurada para o gateway.

Isto aplica-se tanto às ligações em direto como à atualização agendada.

### <a name="using-the-data-source-with-live-connections"></a>Utilizar a origem de dados com ligações em direto

Terá de se certificar de que os nomes do servidor e da base de dados no Power BI Desktop e na origem de dados configurada para o gateway correspondem. Também terá de se certificar de que o utilizador está listado no separador **Utilizadores** da origem de dados para poder publicar conjuntos de dados de ligação em direto. Para ligações em direto, a seleção ocorre no Power BI Desktop quando importa dados pela primeira vez.

Depois de publicar, a partir do Power BI Desktop ou de **Obter Dados**, os seus relatórios devem começar a funcionar. Poderá demorar vários minutos, depois de criar a origem de dados dentro do gateway, para a ligação ser utilizável.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Utilizar a origem de dados com a atualização agendada

Se estiver listado no separador **Utilizadores** da origem de dados configurada no gateway e o nome do servidor e da base de dados corresponderem, irá ver o gateway como uma opção a utilizar com a atualização agendada.

![Apresentar os utilizadores](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Limitações das ligações em direto do Analysis Services

Pode utilizar uma ligação em direto para instâncias em tabela ou multidimensionais.

| **Versão do servidor** | **SKU necessário** |
| --- | --- |
| 2012 SP1 CU4 ou posterior |Business Intelligence e SKU Enterprise |
| 2014 |Business Intelligence e SKU Enterprise |
| 2016 |SKU Standard ou superior |

* As funcionalidades de conversão e Formatação ao nível da célula não são suportadas.
* As Ações e os Conjuntos com Nome não são expostos ao Power BI, mas pode ligar a cubos multidimensionais que também contêm Ações ou Conjuntos com Nome e criar elementos visuais e relatórios.

## <a name="next-steps"></a>Próximos passos

* [Resolução de problemas do gateway de dados no local](/data-integration/gateway/service-gateway-tshoot)
* [Resolver problemas de gateways – Power BI](service-gateway-onprem-tshoot.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

