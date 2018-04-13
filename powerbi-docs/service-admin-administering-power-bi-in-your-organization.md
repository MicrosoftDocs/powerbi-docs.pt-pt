---
title: Administrar o Power BI na sua organização
description: Administrar o Power BI na sua organização
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 64dd0239026d3529129924b8d89eb5cc2642a9af
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2018
---
# <a name="administering-power-bi-in-your-organization"></a>Administrar o Power BI na sua organização
O Microsoft Power BI permite aos utilizadores visualizar dados, partilhar descobertas e colaborar de novas formas intuitivas. Para saber mais, veja [Introdução ao Power BI](service-get-started.md).

A administração do Power BI pode ocorrer em várias localizações. Seguem-se duas localizações comuns.

> [!NOTE]
> A conta tem de estar marcada como **Administrador Global**, no Office 365 ou no Azure Active Directory, ou ter sido atribuída a função de administrador do serviço Power BI, para obter acesso ao portal de administração do Power BI. Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).
> 
> 

* [Portal de administração do Power BI](https://app.powerbi.com/admin-portal)
* [Centro de Administração do Office 365](https://portal.office.com/adminportal/home)

Para obter mais informações sobre a função de administrador do serviço Power BI, veja [Noções básicas sobre a função de administrador do Power BI](service-admin-role.md).

## <a name="whats-in-this-article"></a>Neste artigo
**Inscrever-se no Power BI**

* [Como é que os utilizadores se inscrevem no Power BI?](#how-do-users-sign-up-for-power-bi)
* [Como é que os utilizadores individuais na minha organização se inscrevem?](#how-do-individual-users-in-my-organization-sign-up)
* [Como posso impedir que os utilizadores se associem ao inquilino existente do Office 365?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Como posso permitir que os utilizadores sejam adicionados ao meu inquilino existente do Office 365?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Como posso verificar se tenho o bloqueio ativado no meu inquilino?](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [Como posso impedir que os utilizadores existentes comecem a utilizar o Power BI?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Como posso permitir que os utilizadores se inscrevam no Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

**Administração do Power BI**

* [De que forma isto irá alterar a forma como faço a gestão de identidades dos utilizadores na minha organização hoje em dia?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Como gerir o Power BI?](#how-do-we-manage-power-bi)
* [Qual é o processo para gerir um inquilino criado pela Microsoft para os meus utilizadores?](#what-is-the-process-to-manage-a-tenant-created-by-Microsoft-for-my-users)
* [Se tiver vários domínios, posso controlar os utilizadores que são adicionados ao inquilino do Office 365?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [Como posso remover o Power BI para os utilizadores já inscritos?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Como posso saber quando são associados novos utilizadores ao inquilino?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Devo estar preparado para outras questões?](#are-there-any-additional-things-i-should-be-prepared-for)
* [É gratuito? Estas licenças serão cobradas?](#is-this-free-will-i-be-charged-for-these-licenses)
* [Onde está localizado o meu inquilino do Power BI?](#where-is-my-power-bi-tenant-located)
* [O que é o SLA (Contrato de Nível de Serviço) do Power BI?](#what-is-the-power-bi-sla)

**Segurança no Power BI**

* [O Power BI cumpre requisitos de conformidade nacionais, regionais e específicos da indústria?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Como funciona a segurança no Power BI?](#how-does-security-work-in-power-bi?)

## <a name="sign-up-for-power-bi"></a>Inscrever-se no Power BI
### <a name="how-do-users-sign-up-for-power-bi"></a>Como é que os utilizadores se inscrevem no Power BI?
Pode inscrever-se no Power BI através do [site do Power BI](https://powerbi.microsoft.com). Também se pode inscrever na página dos serviços de compra no centro de administração do Office 365. Quando um administrador se inscreve no Power BI, pode atribuir licenças aos utilizadores que devem ter acesso.

Além disso, os utilizadores individuais na sua organização podem inscrever-se no Power BI através do [site do Power BI](https://powerbi.microsoft.com). Quando um utilizador na sua organização se inscreve no Power BI, é atribuída automaticamente uma licença do Power BI a esse utilizador. [Saiba mais](service-self-service-signup-for-power-bi.md)

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Como é que os utilizadores individuais na minha organização se inscrevem?
Há três cenários que podem aplicar-se aos utilizadores na sua organização:

Cenário 1: a sua organização já tem um ambiente existente do Office 365 e o utilizador que está a inscrever-se no Power BI já tem uma conta do Office 365.
Neste cenário, se um utilizador já tiver uma conta profissional ou escolar no inquilino (por exemplo, contoso.com), mas ainda não tiver o Power BI, a Microsoft simplesmente ativará o plano para essa conta e o utilizador será notificado automaticamente sobre como utilizar o serviço Power BI.

Cenário 2: a sua organização tem um ambiente existente do Office 365 e o utilizador que está a inscrever-se no Power BI não tem uma conta do Office 365.
Neste cenário, o utilizador tem um endereço de e-mail no domínio da organização (por exemplo, contoso.com), mas ainda não tem uma conta do Office 365. Neste caso, o utilizador pode inscrever-se no Power BI e ser-lhe-á atribuída uma conta automaticamente. Isto permite ao utilizador aceder ao serviço Power BI. Por exemplo, se uma colaboradora chamada Nancy utilizar o seu endereço de e-mail profissional (por exemplo, Nancy@contoso.com) para se inscrever, a Microsoft irá adicioná-la automaticamente como utilizador no ambiente do Office 365 da Contoso e ativar o Power BI para essa conta.

Cenário 3: a sua organização não tem um ambiente do Office 365 ligado ao seu domínio de e-mail.
A sua organização não tem de efetuar ações administrativas para tirar partido do Power BI. Os utilizadores serão adicionados a um novo diretório de utilizador apenas na cloud e terá a opção de assumir o controlo enquanto administrador do inquilino e geri-los.

> [!IMPORTANT]
> Se a sua organização tiver vários domínios de e-mail e preferir que todas as extensões dos endereços de e-mail estejam no mesmo inquilino, adicione todos os endereços de e-mail a um inquilino do Azure Active Directory antes de os utilizadores se inscreverem. Não existe nenhum mecanismo automatizado para mover os utilizadores entre inquilinos depois de terem sido criados. Para obter mais informações sobre este processo, veja [Se tiver vários domínios, posso controlar os utilizadores que são adicionados ao inquilino do Office 365?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to) mais adiante neste artigo e [Adicionar o domínio ao Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611) online.
> 
> 

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Como posso impedir que os utilizadores se associem ao inquilino existente do Office 365?
Existem passos que pode seguir, como administrador, para impedir os utilizadores de se associarem ao inquilino existente do Office 365. Se bloquear esta ação, as tentativas dos utilizadores se inscreverem falharão e serão direcionados para contactar o respetivo administrador da organização. Não tem de repetir este processo se já tiver desativado a distribuição de licenças automática (por exemplo, Office 365 para Educação para Alunos, Docentes e Funcionários).

Estes passos requerem a utilização do Windows PowerShell. Para começar com o Windows PowerShell, veja o [guia de introdução ao PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814).

Para efetuar os passos seguintes, tem de instalar a versão de 64 bits mais recente do [Módulo Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

Depois de selecionar a ligação, selecione **Executar** para executar o pacote de instalação.

**Desativar a associação automática ao inquilino**: utilize este comando do Windows PowerShell para impedir que sejam associados novos utilizadores a um inquilino gerido:

* Para desativar a associação automática ao inquilino para novos utilizadores:
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
* Para ativar a associação automática ao inquilino para novos utilizadores:
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

> [!NOTE]
> Este bloqueio impede os novos utilizadores na organização de se inscreverem no Power BI. Os utilizadores que se inscreverem no Power BI antes da desativação de novas inscrições para a sua organização manterão as respetivas licenças. Veja a secção [Como Posso Remover Licenças?] para obter instruções sobre como remover o acesso ao Power BI para os utilizadores inscritos anteriormente no serviço.
> 
> 

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Como posso permitir que os utilizadores sejam adicionados ao meu inquilino existente do Office 365?
Para permitir que os utilizadores se associem ao inquilino, execute o comando oposto, conforme descrito na pergunta acima.

Para efetuar os passos seguintes, tem de instalar a versão de 64 bits mais recente do [Módulo Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Como posso verificar se tenho o bloqueio ativado no meu inquilino?
Execute o script do PowerShell seguinte.

Para efetuar os passos seguintes, tem de instalar a versão de 64 bits mais recente do [Módulo Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Get-MsolCompanyInformation | fl allow*

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Como posso impedir que os utilizadores existentes comecem a utilizar o Power BI?
Existem passos que pode seguir, como administrador, para impedir os utilizadores de se inscreverem no Power BI. Se bloquear esta ação, as tentativas dos utilizadores se inscreverem falharão e serão direcionados para contactar o respetivo administrador da organização. Não tem de repetir este processo se já tiver desativado a distribuição de licenças automática (por exemplo, Office 365 para Educação para Alunos, Docentes e Funcionários). [Saiba mais](service-admin-service-free-in-your-organization.md#enable-or-disable-individual-user-sign-up-in-azure-active-directory)

A definição do AAD que controla isto é **AllowAdHocSubscriptions**. A maioria dos inquilinos terá essa definição como true, o que significa que está ativada. Se adquiriu o Power BI através de um parceiro, pode estar predefinida como false, o que significa que está desativada.

Para efetuar os passos seguintes, tem de instalar a versão de 64 bits mais recente do [Módulo Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. Em primeiro lugar, tem de iniciar sessão no Azure Active Directory com a sua credencial do Office 365. Na primeira linha serão solicitadas as suas credenciais. Na segunda linha, será ligado ao Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Uma vez ligado, pode emitir o comando a seguir de modo a ver para que é que o seu inquilino está atualmente configurado.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. Pode usar este comando para ativar ($true) ou desativar ($false) o AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> O sinalizador AllowAdHocSubscriptions é utilizado para controlar várias capacidades dos utilizadores na organização, incluindo a inscrição no Azure Rights Management Service. A alteração deste sinalizador afetará todas estas capacidades.
> 
> 

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Como posso permitir que os utilizadores se inscrevam no Power BI?
Para permitir que os utilizadores se inscrevam no Power BI, execute o comando listado na pergunta acima, mas use true em vez de false.

Para efetuar os passos seguintes, tem de instalar a versão de 64 bits mais recente do [Módulo Azure Active Directory para Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=236297).

1. Em primeiro lugar, tem de iniciar sessão no Azure Active Directory com a sua credencial do Office 365. Na primeira linha serão solicitadas as suas credenciais. Na segunda linha, será ligado ao Azure Active Directory.
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. Uma vez ligado, pode emitir o comando a seguir de modo a ver para que é que o seu inquilino está atualmente configurado.
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. Pode usar este comando para ativar ($true) ou desativar ($false) o AllowAdHocSubscriptions.
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> O sinalizador AllowAdHocSubscriptions é utilizado para controlar várias capacidades dos utilizadores na organização, incluindo a inscrição no Azure Rights Management Service. A alteração deste sinalizador afetará todas estas capacidades.
> 
> 

## <a name="administration-of-power-bi"></a>Administração do Power BI
### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>De que forma isto irá alterar a forma como faço a gestão de identidades dos utilizadores na minha organização hoje em dia?
Se sua organização já tiver um ambiente existente do Office 365, e todos os utilizadores na organização tiverem contas do Office 365, a gestão de identidades não será alterada.

Se a sua organização já tem um ambiente existente do Office 365, mas nem todos os utilizadores na sua organização têm contas do Office 365, vamos criar um utilizador no inquilino e atribuir licenças com base no endereço de e-mail escolar ou profissional do utilizador. Isto significa que o número de utilizadores que está a gerir a qualquer momento irá aumentar, à medida que os utilizadores na sua organização se inscrevem no serviço.

Se estiver a gerir o seu diretório no local e utilizar os Serviços de Federação do Active Directory (AD FS), a Microsoft não adicionará utilizadores ao seu inquilino, e os utilizadores que tentarem associar-se ao inquilino receberão uma mensagem para contactar o administrador da organização.

Se a sua organização não tem um ambiente do Office 365 ligado ao seu domínio de e-mail, não existirá nenhuma alteração na forma como gere a identidade. Os utilizadores serão adicionados a um novo diretório de utilizador apenas na cloud e terá a opção de assumir o controlo enquanto administrador do inquilino e geri-los.

### <a name="how-do-we-manage-power-bi"></a>Como gerir o Power BI?
O Power BI fornece um portal de administração que lhe permite ver as estatísticas de utilização, fornece uma ligação para o centro de administração do Office 365 para gerir utilizadores e grupos, e a capacidade de controlar as definições do inquilino. 

> [!NOTE]
> A conta tem de estar marcada como **Administrador Global**, no Office 365 ou no Azure Active Directory, para obter acesso ao portal de administração do Power BI.
> 
> 

Para obter mais informações, veja [Portal de Administração do Power BI](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Qual é o processo para gerir um inquilino criado pela Microsoft para os meus utilizadores?
Se um inquilino tiver sido criado pela Microsoft, poderá reclamar e gerir esse inquilino através dos seguintes passos:

1. Associe o inquilino ao inscrever-se no Power BI através de um domínio de endereço de e-mail que corresponde ao domínio do inquilino que quer gerir. Por exemplo, se a Microsoft tiver criado o inquilino contoso.com, terá de associar o inquilino a um endereço de e-mail que termine em @contoso.com.
2. Reclame o controlo de administração ao verificar a propriedade de domínio: assim que estiver no inquilino, pode promover-se para a função *Administrador Global* ao verificar a propriedade do domínio. Para o fazer, siga estes passos:
   
   1. Aceda a [https://portal.office.com](https://portal.office.com).
   2. Selecione o ícone do iniciador de aplicações na parte superior esquerda e selecione **Administrador**.
   3. Leia as instruções na página **Tornar-se o administrador** e, em seguida, selecione **Sim, pretendo ser o administrador**.
      
      > [!NOTE]
      > Se esta opção não aparecer, já existe um administrador do Office 365.
      > 
      > 

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Se tiver vários domínios, posso controlar os utilizadores que são adicionados ao inquilino do Office 365?
Se não realizar nenhuma ação, será criado um inquilino para cada domínio e o subdomínio de e-mail do utilizador.

Se pretender que todos os utilizadores estejam no mesmo inquilino, independentemente das respetivas extensões de endereço de e-mail:

* Crie um inquilino de destino antecipadamente ou utilize um inquilino existente e adicione todos os domínios existentes e os subdomínios que quer que sejam consolidados nesse inquilino. Em seguida, todos os utilizadores com endereços de e-mail que terminem nesses domínios e subdomínios serão automaticamente associados ao inquilino de destino quando se inscreverem.

> [!IMPORTANT]
> Não existe nenhum mecanismo automatizado suportado para mover os utilizadores entre inquilinos depois de terem sido criados. Para saber mais sobre como adicionar domínios a um único inquilino do Office 365, veja [Adicionar os utilizadores e o domínio ao Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).
> 
> 

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Como posso remover o Power BI para os utilizadores já inscritos?
Se um utilizador se inscrever no Power BI, mas já não quiser que este tenha acesso ao Power BI, pode remover a licença do Power BI desse utilizador.

1. Navegue até ao centro de administração do Office 365.
2. Na barra de navegação esquerda, selecione **Utilizadores** > **Utilizadores Ativos**.
3. Encontre o utilizador a quem quer remover a licença e, em seguida, selecione o respetivo nome > **Editar**.
4. Na página de detalhes do utilizador, selecione **Licenças** na barra de navegação esquerda.
5. Desmarque **Power BI (gratuito)** ou **Power BI Pro**, consoante a licença aplicada à respetiva conta.
6. Selecione **Guardar**.

> [!NOTE]
> Também pode efetuar gestão de licenças em massa para os utilizadores. Para tal, selecione vários utilizadores e selecione **Editar**.
> 
> 

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Como posso saber quando são associados novos utilizadores ao inquilino?
Os utilizadores que se tiverem associado ao seu inquilino como parte deste programa receberão uma licença exclusiva, que poderá filtrar no painel do utilizador ativo, no painel do administrador.

Para criar esta nova vista, no centro de administração do Office 365, aceda a **Utilizadores** > **Utilizadores Ativos** e, no menu **Selecionar uma Vista**, selecione **Nova Vista**. Atribua um nome à nova vista e, em **Licença atribuída**, selecione **Power BI (gratuito)** ou **Power BI Pro**. Apenas pode ter uma licença selecionada por vista. Se tiver licenças do **Power BI (gratuito)** e do **Power BI Pro** na sua organização, terá de criar duas vistas. Depois de a nova vista ter sido criada, poderá ver todos os utilizadores no inquilino que se inscreveram neste programa.

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Devo estar preparado para outras questões?
Pode ocorrer um aumento de pedidos de reposição da palavra-passe. Para obter informações sobre este processo, veja [Repor a palavra-passe de um utilizador](https://support.office.com/article/Reset-a-users-password-7a5d073b-7fae-4aa5-8f96-9ecd041aba9c).

Pode remover um utilizador do seu inquilino através do processo padrão no centro de administração do Office 365. No entanto, se o utilizador ainda tiver um endereço de e-mail ativo da sua organização, poderá voltar a associar-se, a menos que bloqueie a associação de todos os utilizadores.

### <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>É gratuito? Estas licenças serão cobradas?
As licenças do **Power BI (gratuito)** destinam-se à versão gratuita do Power BI. Se tiver interesse em capacidades adicionais, consulte a [versão Power BI Pro](service-premium.md).

### <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado o meu inquilino do Power BI?
Para saber como localizar o seu inquilino do Power BI, também conhecido como região de dados, veja [Onde está localizado o meu inquilino do Power BI?](service-admin-where-is-my-tenant-located.md)

### <a name="what-is-the-power-bi-sla"></a>O que é o SLA do Power BI?
Para obter informações sobre o SLA (Contrato de Nível de Serviço) do Power BI, veja o artigo [Licensing Terms and Documentation (Documentação e Termos de Licenciamento)](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) na secção **Licenciamento** do site de Licenciamento da Microsoft.

## <a name="security-in-power-bi"></a>Segurança no Power BI
### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>O Power BI cumpre requisitos de conformidade nacionais, regionais e específicos da indústria?
Para saber mais sobre a conformidade do Power BI, veja o [Microsoft Trust Center](http://go.microsoft.com/fwlink/?LinkId=785324).

### <a name="how-does-security-work-in-power-bi"></a>Como funciona a segurança no Power BI?
O Power BI foi criado de acordo com a base do Office 365 que, por sua vez, baseia-se nos serviços do Azure, como o Azure Active Directory. Para obter uma descrição geral da arquitetura do Power BI, veja [Segurança do Power BI](service-admin-power-bi-security.md). 

## <a name="next-steps"></a>Passos seguintes
[Portal de administração do Power BI](service-admin-portal.md)  
[Compreender a função de administrador do Power BI](service-admin-role.md)  
[Inscrição de self-service no Power BI](service-self-service-signup-for-power-bi.md)  
[Power BI (gratuito) na sua organização](service-admin-service-free-in-your-organization.md)  
[Comprar o Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Power BI Premium – o que é?](service-premium.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[Gestão de contas de utilizador do Office 365](https://technet.microsoft.com/library/office-365-user-account-management.aspx)  
[Gestão de grupos do Office 365](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)  
[Gerir o seu grupo no Power BI e no Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Documento técnico do Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

