---
title: Administrar o Power BI – perguntas mais frequentes (FAQ)
description: Aprenda as respostas às perguntas mais frequentes no Power BI de inscrição, gestão de inquilino e outras tarefas administrativas.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2e51017333a940bd9d7838e6a903c1a66ce2e342
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100799"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administrar o Power BI – perguntas mais frequentes (FAQ)

Este artigo aborda perguntas mais frequentes relativas à administração do Power BI. Para ver uma descrição geral da administração do Power BI, veja [O que é administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md)

## <a name="whats-in-this-article"></a>Neste artigo

### <a name="sign-up-for-power-bi-section"></a>Secção Inscrever-se no Power BI

* [Utilizar o PowerShell](#using-powershell)
* [Como é que os utilizadores se inscrevem no Power BI?](#how-do-users-sign-up-for-power-bi)
* [Como é que os utilizadores individuais na minha organização se inscrevem?](#how-do-individual-users-in-my-organization-sign-up)
* [Como posso impedir que os utilizadores se associem ao inquilino existente do Office 365?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Como posso permitir que os utilizadores se associem ao inquilino existente do Office 365?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Como posso ver se tenho o bloqueio ativado no inquilino?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Como posso impedir que os utilizadores existentes comecem a utilizar o Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Como posso permitir que os utilizadores se inscrevam no Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Secção Administração do Power BI

* [Como isto mudará a minha forma de gerir as identidades dos utilizadores na minha organização hoje em dia?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Como gerir o Power BI?](#how-do-we-manage-power-bi)
* [Qual é o processo para gerir um inquilino criado pela Microsoft para os meus utilizadores?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Se tiver vários domínios, posso controlar o inquilino do Office 365 que os utilizadores são adicionados à?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [Como posso remover o Power BI para os utilizadores já inscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Como posso saber quando são associados novos utilizadores ao inquilino?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Existem outras questões que deve se preparar para?](#are-there-any-additional-things-i-should-prepare-for)
* [Onde está localizado o meu inquilino do Power BI?](#where-is-my-power-bi-tenant-located)
* [O que é o SLA (Contrato de Nível de Serviço) do Power BI?](#what-is-the-power-bi-sla)
* [Como é que o Power BI lida com cenários de elevada disponibilidade e de ativação pós-falha?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Secção Segurança no Power BI

* [O Power BI cumpre requisitos de conformidade nacionais, regionais e específicos da indústria?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Como funciona a segurança no Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Inscrever-se no Power BI

### <a name="using-powershell"></a>Utilizar o PowerShell

Alguns dos procedimentos nesta secção requerem scripts do Windows PowerShell. Se não estiver familiarizado com o PowerShell, recomendamos o [guia de introdução ao PowerShell ](http://go.microsoft.com/fwlink/p/?LinkID=286814). Para executar os scripts, primeiro instale a mais recente versão de 64 bits do [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>Como é que os utilizadores se inscrevem no Power BI?

Como administrador, pode inscrever-se para o Power BI através da [web site do Power BI](https://powerbi.microsoft.com) ou o [comprar serviços](https://admin.microsoft.com/AdminPortal/Home#/catalog) página no Centro de administração do Microsoft 365. Quando um administrador se inscreve no Power BI, podem atribuir licenças de utilizador para os utilizadores que devem ter acesso.

Além disso, os utilizadores individuais na sua organização podem inscrever-se no Power BI através do [site do Power BI](https://powerbi.microsoft.com). Quando um utilizador na sua organização se inscreve no Power BI, o serviço atribui automaticamente uma licença do Power BI para o usuário. Para mais informações, veja [inscrever-se para o Power BI como um indivíduo](service-self-service-signup-for-power-bi.md) e [licenciamento do Power BI na sua organização](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Como é que os utilizadores individuais na minha organização se inscrevem?

Há três cenários que podem aplicar-se aos utilizadores na sua organização:

* **Cenário 1**: a sua organização já tem um ambiente existente do Office 365 e o utilizador que está a inscrever-se no Power BI já tem uma conta do Office 365.
    Neste cenário, se um utilizador já tiver um trabalho ou a conta escolar no inquilino (por exemplo, contoso.com), mas ainda não tem Power BI, o Microsoft simplesmente ativa o plano para essa conta. O utilizador é automaticamente notificado com informações sobre como utilizar o serviço Power BI.

* **Cenário 2**: a sua organização tem um ambiente existente do Office 365, mas o utilizador que está a inscrever-se no Power BI não tem uma conta do Office 365.
    Neste cenário, o utilizador tem um endereço de e-mail no domínio da sua organização (por exemplo, contoso.com), mas ainda não tem uma conta do Office 365. Neste caso, o utilizador pode inscrever-se no Power BI e é-lhe atribuída uma conta automaticamente. Esta ação permite o acesso de utilizador no serviço Power BI. Por exemplo, se uma funcionária chamada Nancy utilizar seu endereço de e-mail profissional (como nancy@contoso.com) para se inscrever, a Microsoft automaticamente adiciona a Matilde como um utilizador no ambiente do Office 365 da Contoso e ativa o Power BI para essa conta.

* **Cenário 3**: Sua organização não tiver um ambiente do Office 365 ligado ao seu domínio de e-mail.
    Não existem não existem ações administrativas necessárias para a sua organização tirar partido do Power BI. O serviço adiciona os utilizadores para um diretório de utilizador novo, apenas na cloud. Também pode optar por assumir o controlo enquanto administrador inquilino e geri-los.

> [!IMPORTANT]
> Se a sua organização tiver vários domínios de e-mail e preferir que todas as extensões dos endereços de e-mail estejam no mesmo inquilino, adicione todos os endereços de e-mail a um inquilino do Azure Active Directory antes de os utilizadores se inscreverem. Depois de criar utilizadores, não existe nenhum mecanismo automatizado para mover utilizadores entre inquilinos. Para mais informações sobre este processo, veja [se tiver vários domínios, posso controlar o inquilino do Office 365 que os utilizadores são adicionados à?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) mais adiante neste artigo e [adicionar um domínio ao Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Como posso impedir que os utilizadores se associem ao inquilino existente do Office 365?

Existem passos que pode seguir, como administrador, para impedir os utilizadores de se associarem ao inquilino existente do Office 365. Se bloquear o acesso, tentativas dos utilizadores para se inscrever falham, e é apresentada uma mensagem que direciona-los para contactar o administrador. da sua organização Não precisa de repetir este processo se já tiver desativado a distribuição de licenças automática (por exemplo, através do Office 365 para educação para estudantes, corpo docente e funcionários).

Utilize o seguinte script do PowerShell para impedir que os utilizadores novos se associem a um inquilino gerido. ([Saiba mais acerca do PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> O bloqueio de acesso impede que os novos utilizadores na sua organização se inscrevam no Power BI. Os utilizadores que se inscreverem no Power BI antes da desativação das novas inscrições na organização mantêm as licenças. Para remover um utilizador, veja [Como posso remover o Power BI para os utilizadores já inscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) mais adiante neste artigo.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Como posso permitir que os utilizadores sejam adicionados ao meu inquilino existente do Office 365?

Utilize o seguinte script do PowerShell para permitir que os utilizadores novos, Junte-se num inquilino gerido. ([Saiba mais acerca do PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Como posso ver se tenho o bloqueio ativado no inquilino?

Utilize o seguinte script do PowerShell para verificar as definições. *AllowEmailVerifiedUsers* deve ser falso. ([Saiba mais acerca do PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Como posso impedir que os utilizadores existentes comecem a utilizar o Power BI?

A definição do Microsoft Azure AD que controla isto é **AllowAdHocSubscriptions**. A maioria dos inquilinos têm esta opção definida como true, o que significa que está ativada. Se tiver adquirido o Power BI através de um parceiro, isso pode ser definido como FALSO, o que significa que está desativada.

Utilize o seguinte script do PowerShell para desativar as subscrições ad hoc. ([Saiba mais acerca do PowerShell][1].)

1. Entre no Azure Active Directory com as suas credenciais do Office 365. A primeira linha do seguinte script do PowerShell pede-lhe as suas credenciais. Na segunda linha, será ligado ao Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Captura de ecrã do Azure Active Directory início de sessão através do PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Uma vez que iniciar sessão, execute o seguinte comando para ver como o seu inquilino está atualmente configurado.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Execute o seguinte comando para ativar (`$true`) ou desativar (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Utilize o **AllowAdHocSubscriptions** sinalizador para controlar várias capacidades dos utilizadores na sua organização, incluindo a capacidade dos utilizadores para se inscrever no serviço Azure Rights Management. A alteração deste sinalizador afeta todas estas capacidades.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Como posso permitir que os utilizadores se inscrevam no Power BI?

Para permitir que os utilizadores existentes para se inscrever no Power BI, execute o comando listado para a pergunta anterior, mas passar `$true` em vez de `$false` no último passo.

## <a name="administration-of-power-bi"></a>Administração do Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>De que forma isto irá alterar a forma como faço a gestão de identidades dos utilizadores na minha organização hoje em dia?

Há três cenários que podem aplicar-se aos utilizadores na sua organização:

* **Cenário 1**: Se sua organização já tem um ambiente existente do Office 365 e todos os utilizadores na sua organização têm contas do Office 365, não há nenhuma alteração na forma como gere a identidade.

* **Cenário 2**: Se sua organização já tem um ambiente existente do Office 365, mas nem todos os utilizadores na sua organização têm contas do Office 365, vamos criar um utilizador no inquilino e atribuir licenças com base no endereço de e-mail escolar ou profissional do utilizador.

    Como resultado, o número de utilizadores que estiver a gerir a qualquer momento cresce à medida que os utilizadores na sua organização Inscreva-se para o serviço.

* **Cenário 3**: Se sua organização não tiver um ambiente do Office 365 ligado ao seu domínio de e-mail, não há nenhuma alteração na forma como gere a identidade.

    O serviço adiciona os utilizadores para um diretório de utilizador novo, apenas na cloud. Além disso, pode optar por assumir o controlo enquanto administrador de inquilino e geri-los.

### <a name="how-do-we-manage-power-bi"></a>Como gerir o Power BI?

O Power BI fornece um portal de administração que lhe permite ver estatísticas de utilização, fornece uma ligação para o Centro de administração do Microsoft 365 para gerir utilizadores e grupos e fornece a capacidade para controlar as definições de ao nível do inquilino.

Para utilizar o portal de administração do Power BI, tem de marcar a sua conta como uma **Administrador Global** no Office 365 ou Azure Active Directory ou alguém tem de atribuir a função de administrador de serviço do Power BI à sua conta de utilizador. Para mais informações, veja [compreender a função de administrador do Power BI](service-admin-role.md) e [Portal de administração do Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Qual é o processo para gerir um inquilino criado pela Microsoft para os meus utilizadores?

Quando um utilizador self-service se inscreve para um serviço cloud que utiliza o Azure AD, o serviço adiciona a um Azure não gerido diretório AD com base no seu domínio de e-mail. Pode reclamar e gerir o inquilino que alguém criado usando um processo conhecido como um *obtenção do controlo administrativo*. O tipo de obtenção de controlo de fazer depende se existe um existente gerido inquilino associado a seu domínio:

* Utilize uma *obtenção de controlo interna* para criar um novo inquilino gerido para o domínio.

* Utilize uma *obtenção de controlo externa* para mover o domínio para um inquilino gerido existente.

Para mais informações, veja [assumir um diretório não gerido como administrador no Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover).

Ao fazer uma obtenção de controlo externa, o serviço coloca Power BI conteúdo que foi criada antes da obtenção de controlo num [área de trabalho do Power BI arquivados](service-admin-power-bi-archived-workspace.md). Tem de migrar manualmente qualquer conteúdo que queira utilizar no novo inquilino.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Se tiver vários domínios, posso controlar o inquilino do Office 365 que os utilizadores são adicionados à?

Se não fazer nada, o serviço cria um inquilino para cada domínio de e-mail do utilizador e o subdomínio. Se pretender que todos os utilizadores estejam no mesmo inquilino, independentemente das respetivas extensões de endereço de e-mail: Criar um inquilino de destino antecipadamente ou utilizar um inquilino existente. Em seguida, adicione todos os domínios existentes e os subdomínios que pretende que sejam consolidados nesse inquilino. Todos os utilizadores com endereços de e-mail que terminem nesses domínios e subdomínios automaticamente associados ao inquilino de destino quando se inscreverem.

> [!IMPORTANT]
> Depois de criar utilizadores, não existe nenhum mecanismo suportado automatizado para mover utilizadores entre inquilinos. Para saber mais sobre como adicionar domínios a um único inquilino do Office 365, veja [Adicionar os utilizadores e o domínio ao Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Como posso remover o Power BI para os utilizadores já inscritos?

Se um utilizador for inscrito no Power BI, mas já não quiser que este tenha acesso ao Power BI, poderá remover a licença do Power BI desse utilizador.

1. Aceda ao [centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Na barra de navegação esquerda, selecione **Utilizadores** > **Utilizadores Ativos**.

1. Localize o utilizador a quem quer remover a licença e, em seguida, selecione o seu nome.

    Também pode efetuar gestão de licenças em massa para os utilizadores. Para tal, selecione vários utilizadores e selecione **Editar licenças de produtos**.

1. Na página de detalhes de utilizador, junto a **Licenças de produtos**, selecione **Editar**.

1. Consoante o que de licença aplicada à respetiva conta, defina **Power BI (gratuito)** ou **Power BI Pro** para **desativar**.

1. Selecione **Guardar**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Como posso saber quando são associados novos utilizadores ao inquilino?

Os utilizadores que são associados ao seu inquilino como parte deste programa obterem atribuídos uma licença exclusiva, que poderá filtrar no painel do utilizador ativo no painel do administrador. Para criar esta nova vista, siga estes passos.

1. Navegue para o [centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Na barra de navegação esquerda, selecione **Utilizadores** > **Utilizadores Ativos**.

1. No menu **Vistas**, selecione **Adicionar vista personalizada**.

1. Atribua um nome à nova vista e, em **Licença de produto atribuída**, selecione **Power BI (gratuito)** ou **Power BI Pro**.

    Apenas pode ter uma licença selecionada por vista. Se tiver licenças do **Power BI (gratuito)** e do **Power BI Pro** na sua organização, poderá criar duas vistas.

1. Introduza quaisquer outras condições que pretenda e selecione **Adicionar**.

1. Depois de criar a nova vista, está disponível a partir da **vistas** menu.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Existem outras questões que deve se preparar para?

Pode ocorrer um aumento de pedidos de reposição da palavra-passe. Para informações sobre este processo, veja [Repor palavra-passe de um utilizador](/office365/admin/add-users/reset-passwords).

Pode remover um utilizador do seu inquilino através do processo padrão no centro de administração do Microsoft 365. No entanto, se o utilizador ainda tiver um endereço de e-mail ativo da sua organização, poderá voltar a associar-se, a menos que bloqueie a associação de todos os utilizadores.

### <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado o meu inquilino do Power BI?

Para informações sobre a região de dados de inquilino do Power BI está em, veja [onde está localizado meu inquilino do Power BI?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>O que é o SLA do Power BI?

Para informações sobre o SLA (contrato de nível de serviço) do Power BI, veja a [termos de licenciamento e a documentação](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) artigo da **licenciamento** seção do site do Microsoft Licensing.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Como é que o Power BI lida com cenários de elevada disponibilidade e de ativação pós-falha?

Para informações sobre a elevada disponibilidade e ativação pós-falha, consulte [Power BI elevada disponibilidade, ativação pós-falha e recuperação de desastres FAQ](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Segurança no Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>O Power BI cumpre requisitos de conformidade nacionais, regionais e específicos da indústria?

Para saber mais sobre a conformidade do Power BI, veja o [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Como funciona a segurança no Power BI?

A Microsoft criou a base do Office 365, que por sua vez baseia-se em serviços do Azure como o Azure Active Directory para o Power BI. Para obter uma descrição geral da arquitetura do Power BI, veja [Segurança do Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Passos seguintes

[Portal de administração do Power BI](service-admin-portal.md)  
[Compreender a função de administrador do Power BI](service-admin-role.md)  
[Inscrição personalizada no Power BI](service-self-service-signup-for-power-bi.md)  
[Comprar o Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[O que é o Power BI Premium?](service-premium-what-is.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[Documento técnico do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Gerir o seu grupo no Power BI e no Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Gestão de contas de utilizador do Office 365](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Gestão de grupos do Office 365](/office365/admin/email/create-edit-or-delete-a-security-group/)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview