---
title: Distribuir conteúdos para utilizadores convidados externos com o Azure AD B2B
description: O Power BI integra-se no Azure Active Directory Business-to-business (Azure AD B2B) para permitir uma distribuição segura de conteúdos do Power BI para utilizadores convidados fora da organização.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2d1e9e32fcec67647bb75ac14ed872e6c51fef96
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101620"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure AD B2B

O Power BI integra-se no Azure Active Directory business-to-business (Azure AD B2B) para permitir uma distribuição segura de conteúdos do Power BI para utilizadores convidados fora da sua organização, enquanto mantém o controlo sobre os dados internos.  

Além disso, pode permitir que os utilizadores convidados fora da sua organização editem e façam a gestão de conteúdos na sua organização.

## <a name="enable-access"></a>Ativar acesso

Certifique-se ativar a [partilhar conteúdo com utilizadores externos](service-admin-portal.md#export-and-sharing-settings) recurso no portal de administração do Power BI antes de convidar utilizadores.

Também pode utilizar o [permitir que os utilizadores convidados externos editar e gerir conteúdos na organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funcionalidade. Permite-lhe selecionar quais o usuário convidado pode ver e criar conteúdo em áreas de trabalho, incluindo a navegação na Power BI sua organização.

## <a name="who-can-you-invite"></a>Quem pode convidar?

Pode convidar utilizadores convidados com qualquer endereço de e-mail, incluindo contas pessoais como gmail.com, outlook.com e hotmail.com. O Azure AD B2B chama estes endereços *identidades sociais*.

## <a name="invite-guest-users"></a>Convidar utilizadores

Os utilizadores convidados apenas exigem convites pela primeira vez que convidá-los à sua organização. Existem duas formas de convidar utilizadores: planeada convites e convites ad hoc.

### <a name="planned-invites"></a>Convites planeados

Utilize um convite planeado caso saiba quais os utilizadores a convidar. Pode enviar o convite através do portal do Azure ou do PowerShell. Tem de ser um administrador de inquilinos para convidar pessoas.

Siga estes passos para enviar um convite no portal do Azure.

1. No [portal do Azure](https://portal.azure.com), selecione **Azure Active Directory**.

1. Sob **Manage**, selecione **utilizadores** > **todos os utilizadores** > **novo utilizador convidado**.

    ![Captura de ecrã do portal do Azure com a opção de utilizador novo convidado chamado.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Introduza um **endereço de e-mail** e uma **mensagem pessoal**.

    ![Captura de ecrã da caixa de diálogo do Azure AD Portal novo utilizador convidado.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Selecione **Convidar**.

Para convidar mais do que um utilizador convidado, utilize o PowerShell. Para obter mais informações, veja [Exemplos do PowerShell e de código de colaboração do Azure AD B2B](/azure/active-directory/b2b/code-samples/).

O utilizador convidado tem de selecionar **Começar** no convite por e-mail que receber. Ao fazê-lo, o utilizador convidado é adicionado ao inquilino.

![Convite de e-mail de utilizador de captura de ecrã do convidado.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Convites ad hoc

Para convidar um utilizador externo em qualquer altura, adicione-os para o seu dashboard ou relatório através da IU de partilha ou à sua aplicação através da página de acesso. Eis um exemplo do que deve fazer ao convidar um utilizador externo para utilizar uma aplicação.

![Utilizador de captura de ecrã do externo adicionado à lista de acesso de aplicação no Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

O utilizador convidado irá receber uma mensagem de e-mail que indica quais partilhou a aplicação com os mesmos.

![Captura de ecrã de E-Mail para a aplicação partilhada com utilizador convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

O utilizador convidado terá de iniciar sessão com o respetivo endereço de e-mail da organização. Estes recebem um pedido para aceitar o convite após iniciar sessão. Após iniciar sessão, a aplicação abre-se para o utilizador convidado. Para regressar à aplicação, o utilizador convidado adicionar a ligação aos marcadores ou guardar o e-mail.

## <a name="licensing"></a>Licensing

O utilizador convidado tem de ter as devidas licenças para ver o conteúdo que partilhou. Existem três formas para se certificar de que o utilizador tem uma licença adequada: utilizar o Power BI Premium, atribuir uma licença do Power BI Pro ou utilizar a licença do Power BI Pro do convidado.

Ao utilizar a funcionalidade [Permitir aos utilizadores externos convidados editarem e gerirem conteúdo na organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization), os utilizadores convidados que contribuem com conteúdo para as áreas de trabalho ou partilham conteúdo com outros utilizadores têm de ter uma licença do Power BI Pro.

### <a name="use-power-bi-premium"></a>Utilizar o Power BI Premium

Atribuir a área de trabalho de aplicação para [capacidade do Power BI Premium](service-premium-what-is.md) permite que o utilizador convidado que utilizar a aplicação sem a necessidade de uma licença do Power BI Pro. O Power BI Premium também permite que aplicações tirar partido de outras capacidades, como taxas de atualização de uma maior capacidade dedicada e tamanhos de modelos grandes.

![Diagrama da experiência do usuário convidado com o Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Atribuir uma licença do Power BI Pro ao utilizador convidado

Atribuir uma licença do Power BI Pro a utilizador convidado, no seu inquilino, permite que esse conteúdo de vista do utilizador convidado no inquilino.

![Diagrama da experiência do usuário convidado com licença atribuir Pro do seu inquilino.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>O utilizador convidado traz a sua própria licença do Power BI Pro

O utilizador convidado já tem uma licença do Power BI Pro atribuída no respetivo inquilino.

![Diagrama da experiência de usuário convidado quando eles traga a sua própria licença.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Utilizadores convidados que podem editar e gerir conteúdo 

Ao utilizar o [permitir que os utilizadores convidados externos editar e gerir conteúdos na organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funcionalidade, os utilizadores convidados especificado obtém acesso ao Power BI da sua organização. Podem ver qualquer conteúdo para os quais tenham permissão. Eles podem acessar a home page, procurar áreas de trabalho, instalar aplicações, enxergar onde estão na lista de acesso e contribuir com conteúdos a áreas de trabalho. Podem criar ou ter o cargo de Administrador de áreas de trabalho que utilizem a nova experiência de área de trabalho. Algumas limitações aplicam-se. A secção de considerações e limitações lista essas restrições.
 
Para ajudar a estes utilizadores iniciar sessão no Power BI, tem de fornecê-los com o URL de inquilino. Para encontrar o URL de inquilino, siga estes passos:

1. No serviço Power BI, no menu superior, selecione ajuda ( **?** ) e, em seguida, **Acerca do Power BI**.

2. Procure o valor junto a **URL de Inquilino**. O valor é o URL de inquilino pode partilhar com os seus utilizadores convidados.

    ![Caixa de diálogo de captura de ecrã de sobre o Power BI com o inquilino do utilizador convidado que URL destacados.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considerações e Limitações

* Por predefinição, o externos do Azure AD B2B limita convidados ao consumo de conteúdos apenas. Convidados do Azure AD B2B externos podem ver aplicações, dashboards, relatórios, exportar os dados e criar subscrições de e-mail para dashboards e relatórios. Não podem aceder a áreas de trabalho nem publicar os seus próprios conteúdos. No entanto, estas restrições não se aplicam aos utilizadores convidados que tem acesso por meio da [permitir que os utilizadores convidados externos editar e gerir conteúdos na organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funcionalidade.

* Para os utilizadores convidados através do [permitir que os utilizadores convidados externos editar e gerir conteúdos na organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) recurso, algumas experiências não estão disponíveis para eles. Para atualizar ou publicar relatórios, precisam de utilizar a IU da Web do serviço Power BI, incluindo Obter Dados para carregar ficheiros do Power BI Desktop.  Não são suportadas as seguintes experiências:
    * A publicação direta do Power BI Desktop para o serviço Power BI
    * Os utilizadores convidados não é possível utilizar o Power BI desktop para ligar a conjuntos de dados do serviço no serviço Power BI
    * Áreas de trabalho clássicas associadas a Grupos do Office 365:
        * Utilizador convidado não é possível criar ou ser administradores desses espaços de trabalho
        * Os utilizadores convidados podem ser membros
    * Enviar convites ad-hoc não é suportada para listas de área de trabalho de acesso
    * Power BI Publisher para Excel não é suportado para os utilizadores convidados
    * Os utilizadores convidados não é possível instalar um do Power BI Gateway e ligá-la à sua organização
    * Os utilizadores convidados não podem instalar aplicações publicar em toda a organização
    * Os utilizadores convidados não é possível utilizar, criar, atualizar ou instalar pacotes de conteúdos organizacionais
    * Os utilizadores convidados não é possível utilizar a funcionalidade Analisar no Excel
    * Os utilizadores convidados não podem ser @mentioned em comentários
    * Os utilizadores convidados não é possível utilizar subscrições
    * Os utilizadores convidados que utilizem esta funcionalidade devem ter uma conta escolar ou profissional. Os utilizadores convidados com contas pessoais experimentará limitações mais devido para iniciar sessão restrições.

* Esta funcionalidade não está atualmente disponível com a web part do relatório do Power BI SharePoint Online.

* Existem definições do Active Directory, que pode limitar o que os utilizadores convidados externos podem fazer dentro da sua organização geral. Que também se aplica ao seu ambiente do Power BI. A seguinte documentação aborda as definições:
    * [Gerir Definições de Colaboração Externa](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Permitir ou bloquear convites para utilizadores B2B de organizações específicas](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Próximos passos

Para informações mais detalhadas, incluindo o nível de linha como funciona a segurança, consulte o White Paper: [Distribute Power BI content to external guest users using Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper) (Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure AD B2B).

Para obter informações sobre o Azure AD B2B, consulte [o que é a colaboração B2B do Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
