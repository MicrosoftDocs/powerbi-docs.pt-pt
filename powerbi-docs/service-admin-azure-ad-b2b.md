---
title: Distribuir conteúdos para utilizadores convidados externos com o Azure AD B2B
description: O Power BI integra-se no Azure Active Directory Business-to-business (Azure AD B2B) para permitir uma distribuição segura de conteúdos do Power BI para utilizadores convidados fora da organização.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0eba54212ff9349ed75d9d9fb18878b39d5cd29a
ms.sourcegitcommit: 378265939126fd7c96cb9334dac587fc80291e97
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57580203"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure AD B2B

O Power BI integra-se no Azure Active Directory business-to-business (Azure AD B2B) para permitir uma distribuição segura de conteúdos do Power BI para utilizadores convidados fora da sua organização, enquanto mantém o controlo sobre os dados internos.  

Além disso, pode permitir que os utilizadores convidados fora da sua organização editem e façam a gestão de conteúdos na sua organização.

## <a name="enable-access"></a>Ativar acesso

Confirme que a funcionalidade [Partilhar conteúdo com utilizadores externos](service-admin-portal.md#export-and-sharing-settings) está ativada no portal de administração do Power BI antes de enviar convites para utilizadores.

Além disso, a funcionalidade [Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](service-admin-portal.md#export-and-sharing-settings) permite-lhe selecionar que utilizador convidado pode ver e criar conteúdo em áreas de trabalho, incluindo navegar pelo Power BI da sua organização.

## <a name="who-can-you-invite"></a>Quem pode convidar?

Pode enviar convites para utilizadores convidados com qualquer endereço de e-mail, incluindo contas pessoais, como gmail.com, outlook.com ou hotmail.com. No Azure AD B2B, estes endereços são denominados *identidades sociais*.

## <a name="invite-guest-users"></a>Convidar utilizadores

Os convites só são necessários da primeira vez que um utilizador convidado externo for convidado para a sua organização. Existem duas formas de convidar utilizadores: convites planeados e convites ad hoc.

### <a name="planned-invites"></a>Convites planeados

Utilize um convite planeado caso saiba quais os utilizadores a convidar. Pode enviar o convite através do portal do Azure ou do PowerShell. Tem de ser um administrador de inquilinos para convidar pessoas.

Siga estes passos para enviar um convite no portal do Azure.

1. No [portal do Azure](https://portal.azure.com), selecione **Azure Active Directory**.

1. Em **Gerir**, aceda a **Utilizadores** > **Todos os utilizadores** > **Novo utilizador convidado**.

    ![Portal do Azure AD - Novo utilizador convidado](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. Introduza um **endereço de e-mail** e uma **mensagem pessoal**.

    ![Portal do Azure AD - Mensagem de convite ao novo utilizador convidado](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. Selecione **Convidar**.

Para convidar mais do que um utilizador convidado, utilize o PowerShell. Para obter mais informações, veja [Exemplos do PowerShell e de código de colaboração do Azure AD B2B](/azure/active-directory/b2b/code-samples/).

O utilizador convidado tem de selecionar **Começar** no convite por e-mail que receber. Ao fazê-lo, o utilizador convidado é adicionado ao inquilino.

![Convite por e-mail ao utilizador convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Convites ad-hoc

Para enviar um convite em qualquer altura, adicione o utilizador externo ao seu dashboard ou relatório através da IU de partilha ou à sua aplicação através da página de acesso. Eis um exemplo do que deve fazer ao convidar um utilizador externo para utilizar uma aplicação.

![Utilizador externo adicionado à lista de acesso da aplicação](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

O utilizador convidado receberá um e-mail a indicar que a aplicação foi partilhada com ele.

![E-mail a indicar a partilha da aplicação com o utilizador convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

O utilizador convidado terá de iniciar sessão com o respetivo endereço de e-mail da organização. Ser-lhe-á pedido que aceite o convite após iniciar sessão. Após iniciar sessão, o utilizador convidado é redirecionado para o conteúdo da aplicação. Para regressar à aplicação, o utilizador convidado adicionar a ligação aos marcadores ou guardar o e-mail.

## <a name="licensing"></a>Licensing

O utilizador convidado tem de ter as devidas licenças para ver o conteúdo que foi partilhado. Existem três opções para o efeito: utilizar o Power BI Premium; atribuir uma licença do Power BI Pro; ou utilizar a licença do Power BI Pro do convidado.

Ao utilizar a funcionalidade [Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](service-admin-portal.md#export-and-sharing-settings), os utilizadores convidados que contribuem com conteúdo para as áreas de trabalho ou partilham conteúdo com outros utilizadores têm de ter uma licença do Power BI Pro.

### <a name="use-power-bi-premium"></a>Utilizar o Power BI Premium

Atribuir a área de trabalho de aplicação à [capacidade Premium do Power BI](service-premium.md) permite que o utilizador convidado utilize a aplicação sem precisar de uma licença do Power BI Pro. O Power BI Premium também permite que as aplicações tirem partido de outras capacidades, como um aumento nas taxas de atualização, capacidade dedicada e tamanhos de modelos grandes.

![Utilizar o Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Atribuir uma licença do Power BI Pro ao utilizador convidado

Atribuir uma licença do Power BI Pro ao utilizador convidado, no seu inquilino, permite que esse utilizador convidado veja o conteúdo no inquilino.

![Atribuir licença Pro do seu inquilino](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>O utilizador convidado traz a sua própria licença do Power BI Pro

O utilizador convidado já tem uma licença do Power BI Pro atribuída no respetivo inquilino.

![O utilizador convidado traz a sua própria licença](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Utilizadores convidados que podem editar e gerir conteúdo 

Ao utilizar a funcionalidade [Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](service-admin-portal.md#export-and-sharing-settings), os utilizadores convidados especificados obtêm acesso ao Power BI da sua organização e conseguem ver todos os conteúdos para os quais têm permissão. Podem aceder à Home Page, navegar em áreas de trabalho, instalar aplicações diretamente a partir da lista de acesso e contribuir com conteúdos para áreas de trabalho. Podem criar ou ter o cargo de Administrador de áreas de trabalho que utilizem a nova experiência de área de trabalho. Aplicam-se algumas limitações e as mesmas estão indicadas na secção Considerações e Limitações.

Para ajudar estes utilizadores a iniciar sessão no Power BI, forneça-lhes o URL de Inquilino. Para encontrar o URL de inquilino, siga estes passos:

1. No serviço Power BI, no menu superior, selecione ajuda (**?**) e, em seguida, **Acerca do Power BI**.

2. Procure o valor junto a **URL de Inquilino**. Este é o URL de inquilino que pode partilhar com os utilizadores convidados.

![URL de inquilino de utilizador convidado](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considerações e Limitações

* Por predefinição, os convidados B2B externos estão limitados apenas ao consumo de conteúdos. Os convidados B2B externos podem ver aplicações, dashboards, relatórios, exportar dados e criar subscrições de e-mail para dashboards e relatórios. Não podem aceder a áreas de trabalho nem publicar os seus próprios conteúdos. No entanto, estas restrições não se aplicam a utilizadores convidados com permissão através da definição de inquilino [Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](service-admin-portal.md#export-and-sharing-settings).

* Algumas experiências não estão disponíveis para os utilizadores convidados com permissão através da definição de inquilino [Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](service-admin-portal.md#export-and-sharing-settings). Para atualizar ou publicar relatórios, precisam de utilizar a IU da Web do serviço Power BI, incluindo Obter Dados para carregar ficheiros do Power BI Desktop.  As seguintes experiências não são suportadas:
    * A publicação direta do Power BI Desktop para o serviço Power BI
    * Os utilizadores convidados não podem utilizar o Power BI Desktop para ligar a conjuntos de dados de serviço no serviço Power BI
    * Áreas de trabalho clássicas associadas a Grupos do Office 365: o utilizador convidado não pode criar ou ter a função de Administrador destas áreas de trabalho. No entanto, pode ser membro.
    * O envio de convites ad-hoc não é suportado para listas de acesso de áreas de trabalho
    * O Power BI Publisher para Excel não é suportado para utilizadores convidados
    * Os utilizadores convidados não podem instalar o Power BI Gateway e ligá-lo à sua organização
    * Os utilizadores convidados não podem instalar aplicações de publicações para toda a organização
    * Os utilizadores convidados não podem utilizar, criar, atualizar ou instalar pacotes de conteúdos organizacionais
    * Os utilizadores convidados não podem utilizar a funcionalidade Analisar no Excel
    * Os utilizadores convidados não podem ser @mentioned em comentários
    * Os utilizadores convidados não podem utilizar subscrições
    * Os utilizadores convidados que utilizem esta funcionalidade devem ter uma conta escolar ou profissional. Os utilizadores convidados que utilizem contas pessoais terão mais limitações devido a restrições de início de sessão.

* Esta funcionalidade não está atualmente disponível com a peça Web de relatórios do Power BI para SharePoint Online.

* Existem Definições do Active Directory Domain Services que podem limitar as ações que os utilizadores externos convidados podem realizar em toda a sua organização e isso também se aplica ao seu ambiente do Power BI. A seguinte documentação aborda as definições:
    * [Gerir Definições de Colaboração Externa](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Permitir ou bloquear convites para utilizadores B2B de organizações específicas](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Próximos passos

Para obter informações mais detalhadas, incluindo sobre o funcionamento da segurança ao nível de linha, veja o documento técnico: [Distribute Power BI content to external guest users using Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper) (Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure AD B2B).

Para obter informações relativas ao Azure AD B2B, veja [O que é a colaboração do Azure AD B2B?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
