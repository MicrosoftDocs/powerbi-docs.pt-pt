---
title: Administrar o Power BI – perguntas mais frequentes (FAQ)
description: Saiba as respostas às perguntas mais frequentes sobre a inscrição, a gestão de inquilinos e outras tarefas administrativas do Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 0c9d346017dc3b18abd6a56d0d3a62e1305e6575
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "74698745"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Administrar o Power BI – perguntas mais frequentes (FAQ)

Este artigo aborda perguntas mais frequentes relativas à administração do Power BI. Para ver uma descrição geral da administração do Power BI, veja [O que é administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md)

## <a name="whats-in-this-article"></a>Neste artigo

### <a name="sign-up-for-power-bi-section"></a>Secção Inscrever-se no Power BI

* [Utilizar o PowerShell](#using-powershell)
* [Como é que os utilizadores se inscrevem no Power BI?](#how-do-users-sign-up-for-power-bi)
* [Como é que os utilizadores individuais na minha organização se inscrevem?](#how-do-individual-users-in-my-organization-sign-up)
* [Como posso impedir que os utilizadores se associem ao inquilino existente do Office 365?](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [Como posso permitir que os utilizadores se associem ao inquilino existente do Office 365?](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [Como posso verificar se tenho o bloqueio ativado no meu inquilino?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Como posso impedir que os utilizadores existentes comecem a utilizar o Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Como posso permitir que os utilizadores se inscrevam no Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Secção Administração do Power BI

* [Como isto mudará a minha forma de gerir as identidades dos utilizadores na minha organização hoje em dia?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Como gerir o Power BI?](#how-do-we-manage-power-bi)
* [Qual é o processo para gerir um inquilino criado pela Microsoft para os meus utilizadores?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Se tiver múltiplos domínios, posso controlar o inquilino do Microsoft 365 ao qual os utilizadores são adicionados?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [Como posso remover o Power BI para os utilizadores já inscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Como posso saber quando são associados novos utilizadores ao inquilino?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Devo preparar-me para outras questões?](#are-there-any-additional-things-i-should-prepare-for)
* [Onde está localizado o meu inquilino do Power BI?](#where-is-my-power-bi-tenant-located)
* [O que é o SLA (Contrato de Nível de Serviço) do Power BI?](#what-is-the-power-bi-sla)
* [Como é que o Power BI lida com cenários de elevada disponibilidade e de ativação pós-falha?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Secção Segurança no Power BI

* [O Power BI cumpre requisitos de conformidade nacionais, regionais e específicos da indústria?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Como funciona a segurança no Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Inscrever-se no Power BI

### <a name="using-powershell"></a>Utilizar o PowerShell

Alguns dos procedimentos nesta secção requerem scripts do Windows PowerShell. Se não estiver familiarizado com o PowerShell, recomendamos o [guia de introdução ao PowerShell ](https://go.microsoft.com/fwlink/p/?LinkID=286814). Para executar os scripts, primeiro instale a mais recente versão de 64 bits do [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>Como é que os utilizadores se inscrevem no Power BI?

Enquanto administrador do Microsoft 365, pode inscrever-se no Power BI através do [site do Power BI](https://powerbi.microsoft.com) ou na página [Comprar serviços](https://admin.microsoft.com/AdminPortal/Home#/catalog) no centro de administração do Microsoft 365. Quando um administrador do Microsoft 365 se inscreve no Power BI, pode atribuir licenças aos utilizadores que devem ter acesso.

Além disso, os utilizadores individuais na sua organização podem inscrever-se no Power BI através do [site do Power BI](https://powerbi.microsoft.com). Quando um utilizador na sua organização se inscreve no Power BI, o serviço atribui automaticamente uma licença do Power BI a esse utilizador. Para obter mais informações, veja [Inscrever-se no Power BI como um indivíduo](service-self-service-signup-for-power-bi.md) e [Licenciamento do Power BI na sua organização](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Como é que os utilizadores individuais na minha organização se inscrevem?

Há três cenários que podem aplicar-se aos utilizadores na sua organização:

* **Cenário 1**: a sua organização já tem um ambiente existente do Microsoft 365 e o utilizador que está a inscrever-se no Power BI já tem uma conta do Microsoft 365.
    Neste cenário, se um utilizador já tiver uma conta profissional ou escolar no inquilino (por exemplo, contoso.com), mas ainda não tiver o Power BI, a Microsoft simplesmente ativará o plano (gratuito) do Power BI para essa conta. O utilizador é automaticamente notificado e recebe informações sobre como utilizar o serviço Power BI.

* **Cenário 2**: a sua organização tem um ambiente existente do Microsoft 365, mas o utilizador que está a inscrever-se no Power BI não tem uma conta do Microsoft 365.
    Neste cenário, o utilizador tem um endereço de e-mail no domínio da organização (por exemplo, contoso.com), mas ainda não tem uma conta do Microsoft 365. Neste caso, o utilizador pode inscrever-se no Power BI e é-lhe atribuída uma conta automaticamente. Esta ação permite ao utilizador aceder ao serviço Power BI. Por exemplo, se uma colaboradora chamada Nancy utilizar o seu endereço de e-mail de trabalho (por exemplo, nancy@contoso.com) para se inscrever, a Microsoft vai adicioná-la automaticamente como utilizador no ambiente do Microsoft 365 da Contoso e ativar o Power BI para essa conta.

* **Cenário 3**: a sua organização não tem um ambiente do Microsoft 365 ligado ao domínio de e-mail.
    A sua organização não tem de efetuar ações administrativas para tirar partido do Power BI. O serviço adiciona utilizadores a um novo diretório de utilizador apenas na cloud. Também pode optar por assumir o comando como administrador global do Microsoft 365 para os inquilinos e geri-los.

> [!IMPORTANT]
> Se a sua organização tiver vários domínios de e-mail e preferir que todas as extensões dos endereços de e-mail estejam no mesmo inquilino, adicione todos os endereços de e-mail a um inquilino do Azure Active Directory antes de os utilizadores se inscreverem. Depois de criar utilizadores, não existe nenhum mecanismo automatizado para os mover entre inquilinos. Para obter mais informações acerca deste processo, veja [Se tiver múltiplos domínios, posso controlar o inquilino do Microsoft 365 ao qual os utilizadores são adicionados?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to) mais adiante neste artigo e [Adicionar um domínio ao Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>Como posso impedir que os utilizadores se associem ao inquilino existente do Microsoft 365?

Existem passos que pode seguir, como administrador global do Microsoft 365, para impedir os utilizadores de se associarem ao inquilino existente do Microsoft 365. Se bloquear esta ação, as tentativas dos utilizadores para se inscreverem falharão e aparecerá uma mensagem a instruí-los para contactar o administrador da organização. Não terá de repetir este processo se já tiver desativado a distribuição de licenças automática (por exemplo, Office 365 para Educação para Estudantes, para Corpo Docente e para Docentes).

Utilize o seguinte script do PowerShell para impedir que os utilizadores novos se associem a um inquilino gerido. ([Saiba mais acerca do PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> O bloqueio de acesso impede que os novos utilizadores na sua organização se inscrevam no Power BI. Os utilizadores que se inscreverem no Power BI antes da desativação das novas inscrições na organização mantêm as licenças. Para remover um utilizador, veja [Como posso remover o Power BI para os utilizadores já inscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) mais adiante neste artigo.

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>Como posso permitir que os utilizadores se associem ao inquilino existente do Microsoft 365?

Utilize o seguinte script do PowerShell para permitir que os novos utilizadores se associem a um inquilino gerido. ([Saiba mais acerca do PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Como posso verificar se tenho o bloqueio ativado no meu inquilino?

Execute o seguinte script do PowerShell para verificar as definições. *AllowEmailVerifiedUsers* deve ser falso. ([Saiba mais acerca do PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Como posso impedir que os utilizadores existentes comecem a utilizar o Power BI?

A definição do Microsoft Azure AD que controla isto é **AllowAdHocSubscriptions**. A maioria dos inquilinos tem esta opção definida como *verdadeiro*, o que significa que está ativada. Se tiver adquirido o Power BI através de um parceiro, a opção poderá estar definida como *falso*, o que significa que está desativada.

Utilize o seguinte script do PowerShell para desativar as subscrições ad hoc. ([Saiba mais sobre o PowerShell][1].)

1. Inicie sessão no Azure Active Directory com as suas credenciais do Microsoft 365. A primeira linha do seguinte script do PowerShell pede-lhe as suas credenciais. Na segunda linha, será ligado ao Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Captura de ecrã a mostrar o início de sessão no Azure Active Directory através do PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Depois de iniciar sessão, execute o seguinte comando para ver como é que o seu inquilino está atualmente configurado.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Execute o seguinte comando para ativar (`$true`) ou desativar (`$false`) o **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Utilize o sinalizador **AllowAdHocSubscriptions** para controlar várias capacidades dos utilizadores na organização, incluindo a capacidade de se inscreverem no Azure Rights Management Service. A alteração deste sinalizador afeta todas estas capacidades. Com uma configuração de *falso*, os utilizadores ainda se podem inscrever numa avaliação individual do Power BI Pro.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Como posso permitir que os utilizadores se inscrevam no Power BI?

Para permitir que os utilizadores se inscrevam no Power BI, execute o comando listado na pergunta acima, mas utilize `$true` em vez de `$false` no último passo.

## <a name="administration-of-power-bi"></a>Administração do Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>De que forma isto irá alterar a forma como faço a gestão de identidades dos utilizadores na minha organização hoje em dia?

Há três cenários que podem aplicar-se aos utilizadores na sua organização:

* **Cenário 1**: se a sua organização já tiver um ambiente existente do Microsoft 365 e todos os utilizadores na organização tiverem contas do Microsoft 365, não há nenhuma alteração na forma como gere as identidades.

* **Cenário 2**: se a sua organização já tiver um ambiente existente do Microsoft 365, mas nem todos os utilizadores na organização tiverem contas do Microsoft 365, iremos criar um utilizador no inquilino e atribuir licenças com base no endereço de e-mail escolar ou profissional do utilizador.

    Por conseguinte, o número de utilizadores que está a gerir em qualquer momento aumenta à medida que os utilizadores na sua organização se inscrevem no serviço.

* **Cenário 3**: se a sua organização não tiver um ambiente do Microsoft 365 ligado ao domínio de e-mail, não há nenhuma alteração na forma como gere as identidades.

    O serviço adiciona utilizadores a um diretório de utilizadores novo apenas na cloud, que pode optar por controlar como administrador global do Microsoft 365 e geri-los.

### <a name="how-do-we-manage-power-bi"></a>Como gerir o Power BI?

O Power BI fornece um portal de administração do Power BI para utilizadores na função de Administrador Global do Microsoft 365 e utilizadores na função de Administrador do Serviço Power BI. Para utilizar o portal de administração do Power BI, tem de marcar a sua conta como **Administrador Global** no Microsoft 365 ou no Azure Active Directory, ou alguém tem de atribuir a função de administrador do serviço Power BI à sua conta de utilizador. Para obter mais informações, veja [Compreender a função de administrador do Power BI](service-admin-role.md) e [Portal de Administração do Power BI](service-admin-portal.md). O portal oferece a capacidade de controlar as definições do inquilino, ver as estatísticas de utilização do Power BI e uma ligação para o centro de administração do Microsoft 365 para gerir utilizadores e grupos.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Qual é o processo para gerir um inquilino criado pela Microsoft para os meus utilizadores?

Quando um utilizador self-service se inscreve num serviço cloud que utiliza o Azure AD, o serviço adiciona esse utilizador a um diretório não gerido do Azure AD com base no respetivo domínio de e-mail. Pode reclamar e gerir um inquilino que alguém criou com um processo conhecido como *obtenção de controlo administrativo*. Para obter mais informações, veja [Obter o controlo de um diretório não gerido como administrador no Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover). O tipo de obtenção de controlo que realiza está dependente de existir um inquilino gerido associado ao seu domínio:

* O Power BI suporta a obtenção de controlo administrativo interno. Quando executa uma obtenção de controlo administrativo _interno_ de um diretório do Azure não gerido, é adicionado como o administrador global do diretório não gerido. Nenhum utilizador, domínio ou plano de serviço é migrado para qualquer outro diretório administrado por si.

* O Power BI já não suporta a obtenção de controlo administrativo externo. Quando executa uma obtenção de controlo administrativo _externo_ de um diretório do Azure não gerido, adiciona o nome de domínio DNS do diretório não gerido ao seu diretório gerido do Azure. A obtenção de controlo externo resultará numa perda de acesso a todo o conteúdo do Power BI no inquilino não gerido original. Os relatórios do Power BI terão de ser republicados no novo inquilino e os dashboards e aplicações do Power BI terão de ser recriados no novo inquilino.

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>Se tiver múltiplos domínios, posso controlar o inquilino do Microsoft 365 ao qual os utilizadores são adicionados?

Se não realizar nenhuma ação, o serviço criará um inquilino para cada domínio e subdomínio de e-mail do utilizador. Se pretender que todos os utilizadores estejam no mesmo inquilino, independentemente das respetivas extensões de endereço de e-mail: Crie um inquilino de destino com antecedência ou utilize um inquilino existente. Em seguida, adicione todos os domínios e subdomínios existentes que pretende que sejam consolidados nesse inquilino. Todos os utilizadores com endereços de e-mail que terminem nesses domínios e subdomínios são automaticamente associados ao inquilino de destino quando se inscreverem.

> [!IMPORTANT]
> Depois de criar utilizadores, não existe nenhum mecanismo automatizado suportado para os mover entre inquilinos. Para saber mais sobre como adicionar domínios a um único inquilino do Microsoft 365, veja [Adicionar os utilizadores e o domínio ao Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Como posso remover o Power BI para os utilizadores já inscritos?

Se um utilizador for inscrito no Power BI, mas já não quiser que este tenha acesso ao Power BI, poderá remover a licença do Power BI desse utilizador.

1. Aceda ao [centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. No painel de navegação, selecione **Utilizadores** > **Utilizadores Ativos**.

1. Localize o utilizador a quem quer remover a licença e, em seguida, selecione o seu nome.

    Também pode efetuar gestão de licenças em massa para os utilizadores. Para tal, selecione vários utilizadores e selecione **Editar licenças de produtos**.

1. Na página de detalhes de utilizador, junto a **Licenças de produtos**, selecione **Editar**.

1. Consoante a licença que aplicou à conta deles, defina **Power BI (gratuito)** ou **Power BI Pro** como **Desligado**.

1. Selecione **Guardar**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Como posso saber quando são associados novos utilizadores ao inquilino?

Os utilizadores que se tiverem associado ao seu inquilino através de inscrição de gestão personalizada receberão uma licença exclusiva, que poderá filtrar no painel do utilizador ativo, no dashboard do administrador. Para criar esta nova vista, siga estes passos.

1. Navegue para o [centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. No painel de navegação, selecione **Utilizadores** > **Utilizadores Ativos**.

1. No menu **Vistas**, selecione **Adicionar vista personalizada**.

1. Atribua um nome à nova vista e, em **Licença de produto atribuída**, selecione **Power BI (gratuito)** ou **Power BI Pro**.

    Apenas pode ter uma licença selecionada por vista. Se tiver licenças do **Power BI (gratuito)** e do **Power BI Pro** na sua organização, poderá criar duas vistas.

1. Introduza quaisquer outras condições que pretenda e selecione **Adicionar**.

1. Depois de criar a nova vista, pode vê-la no menu **Vistas**.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Devo preparar-me para outras questões?

Pode ocorrer um aumento de pedidos de reposição da palavra-passe. Para obter informações sobre este processo, veja [Repor a palavra-passe de um utilizador](/office365/admin/add-users/reset-passwords).

Pode remover um utilizador do seu inquilino através do processo padrão no centro de administração do Microsoft 365. No entanto, se o utilizador ainda tiver um endereço de e-mail ativo da sua organização, poderá voltar a associar-se, a menos que bloqueie a associação de todos os utilizadores.

### <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado o meu inquilino do Power BI?

Para obter informações acerca da região de dados na qual está o seu inquilino do Power BI, veja [Onde está localizado o meu inquilino do Power BI?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>O que é o SLA do Power BI?

Para obter informações acerca do SLA (Contrato de Nível de Serviço) do Power BI, veja o artigo [Documentação e Termos de Licenciamento](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) na secção **Licenciamento** do site de Licenciamento da Microsoft.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Como é que o Power BI lida com cenários de elevada disponibilidade e de ativação pós-falha?

Para obter informações sobre cenários de elevada disponibilidade e de ativação pós-falha, veja [FAQ sobre elevada disponibilidade, ativação pós-falha e recuperação após desastre do Power BI](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Segurança no Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>O Power BI cumpre requisitos de conformidade nacionais, regionais e específicos da indústria?

Para saber mais sobre a conformidade do Power BI, veja o [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Como funciona a segurança no Power BI?

A Microsoft criou o Power BI com base no Microsoft 365 que, por sua vez, se baseia nos serviços do Azure como o Azure Active Directory. Para obter uma descrição geral da arquitetura do Power BI, veja [Segurança do Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Próximos passos

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

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview
