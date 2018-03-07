---
title: "Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure AD B2B"
description: "O Power BI integra-se no Azure Active Directory Business-to-business (Azure AD B2B) para permitir uma distribuição segura de conteúdos do Power BI para utilizadores convidados fora da organização."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/07/2017
ms.author: maghan
LocalizationGroup: Administration
ms.openlocfilehash: 09bd3064c7a694355255cb3cca29ade02986d42e
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir conteúdos do Power BI para utilizadores convidados externos com o Azure AD B2B

O Power BI integra-se no Azure Active Directory Business-to-business (Azure AD B2B) para permitir uma distribuição segura de conteúdos do Power BI para utilizadores convidados fora da organização, mantendo o controlo sobre os dados internos.

> [!VIDEO https://www.youtube.com/embed/xxQWEQ1NnlY]

> [!NOTE]
> Esta funcionalidade não está atualmente disponível com as aplicações móveis do Power BI. Num dispositivo móvel, poderá ver o conteúdo partilhado do Power BI com o Azure AD B2B num browser. 

## <a name="invite-guest-users"></a>Convidar utilizadores

Existem duas formas de convidar utilizadores para o seu inquilino do Power BI: convites planeados ou convites ad-hoc. Os convites só são necessários da primeira vez que um utilizador externo for convidado para a sua organização.

### <a name="planned-invites"></a>Convites planeados

Um convite planeado é executado no Portal do Microsoft Azure, no Azure AD ou através do PowerShell. Esta é a opção a utilizar se souber que utilizadores têm de ser convidados. 

**Criar os utilizadores convidados no portal do Azure AD requer que seja um administrador inquilino.**

1. Navegue para o [Portal do Azure](https://portal.azure.com) e selecione **Azure Active Directory**.

2. Navegue para **Utilizadores e grupos** > **Todos os utilizadores** > **Novo utilizador convidado**.

    ![Portal do Azure AD - Novo utilizador convidado](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

3. Introduza o **endereço de e-mail** e uma **mensagem pessoal**.

    ![Portal do Azure AD - Mensagem de convite ao novo utilizador convidado](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

4. Selecione **Convidar**.

Para convidar mais do que um utilizador convidado, utilize o PowerShell. Para obter mais informações, consulte [Código de colaboração do Azure Active Directory B2B e exemplos do PowerShell](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-code-samples).

O utilizador convidado tem de selecionar **Começar** no convite por e-mail que receber. Ao fazê-lo, o utilizador convidado é adicionado ao inquilino.

![Convite por e-mail ao utilizador convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Convites ad-hoc

Para efetuar um convite a qualquer altura, adicione o utilizador externo à lista de acesso de uma aplicação ao publicá-la.

![Utilizador externo adicionado à lista de acesso da aplicação](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

O utilizador convidado irá receber um e-mail a indicar que a aplicação foi partilhada com o mesmo.

![E-mail a indicar a partilha da aplicação com o utilizador convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

O utilizador convidado terá de iniciar sessão com o respetivo endereço de e-mail da organização. Ser-lhe-á pedido que aceite o convite após iniciar sessão. Após iniciar sessão, o utilizador convidado é redirecionado para o conteúdo da aplicação. Para regressar à aplicação, adicione a ligação aos marcadores ou guarde o e-mail.

## <a name="licensing"></a>Licenças

O utilizador convidado terá de ter as devidas licenças para ver a aplicação que foi partilhada. Existem três opções para o fazer.

### <a name="use-power-bi-premium"></a>Utilizar o Power BI Premium

Atribuir a área de trabalho de aplicação à capacidade Power BI Premium permitirá que o utilizador convidado utilize a aplicação sem precisar de uma licença do Power BI Pro. O Power BI Premium também permite que as aplicações tirem partido de outras capacidades, como um aumento nas taxas de atualização, capacidade dedicada e tamanhos de modelos grandes.

![Utilizar o Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-power-bi-pro-license-to-guest-user"></a>Atribuir licença do Power BI Pro a utilizador convidado

Atribuir uma licença do Power BI Pro ao utilizador convidado, no seu inquilino, permite que esse utilizador convidado veja o conteúdo.

> [!NOTE]
> Uma licença do Power BI Pro do seu inquilino aplica-se a utilizadores convidados apenas quando estes acedem a conteúdos no seu inquilino.

![Atribuir licença Pro do seu inquilino](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>O utilizador convidado traz a sua própria licença do Power BI Pro

O utilizador convidado já tem uma licença do Power BI Pro atribuída no respetivo inquilino.

![O utilizador convidado traz a sua própria licença](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="limitations"></a>Limitações

* Os convidados B2B externos estão limitados apenas ao consumo de conteúdos. Os convidados B2B externos podem ver aplicações, dashboards, relatórios, exportar dados e criar subscrições de e-mail para dashboards e relatórios. Não podem aceder a áreas de trabalho nem publicar os seus próprios conteúdos.
* Esta funcionalidade não está atualmente disponível com as aplicações móveis do Power BI. Num dispositivo móvel, poderá ver o conteúdo partilhado do Power BI com o Azure AD B2B num browser.
* A utilização de utilizadores convidados com o Power BI não é suportada nas clouds soberanas (governo).

## <a name="next-steps"></a>Próximos passos

Para obter informações mais detalhadas, incluindo sobre o funcionamento da segurança ao nível de linha, consulte o [documento técnico](https://aka.ms/powerbi-b2b-whitepaper).

Para informações relativas ao Azure Active Directory B2B, consulte [O que é a colaboração do Azure AD B2B?](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)