---
title: "Utilizar um Endereço de E-mail alternativo"
description: "Utilizar um Endereço de E-mail alternativo"
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
ms.date: 08/09/2017
ms.author: maghan
ms.openlocfilehash: dd9e146b22c95d8c915ea653ee287bb7a51e6b06
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="using-an-alternate-email-address"></a>Utilizar um Endereço de E-mail alternativo
Por predefinição, o endereço de e-mail utilizado na inscrição no Power BI é usado para enviar atualizações sobre a atividade no Power BI.  Por exemplo, um convite de partilha é enviado para este endereço.

Por vezes, pode querer que estes e-mails sejam entregues num endereço de e-mail alternativo em vez do utilizado originalmente para se inscrever no Power BI.

## <a name="updating-through-office-365-personal-info-page"></a>Atualizar através da página de informações pessoais do Office 365
1. Aceda à sua [página de informações pessoais do Office 365](https://portal.office.com/account/#personalinfo).  Se lhe for pedido, inicie sessão com o endereço de e-mail e a palavra-passe que utiliza no Power BI.
2. Clique na ligação de edição na secção Detalhes de contacto.  
   
   > [!NOTE]
   > Se não vir uma ligação Editar, significa que o endereço de e-mail é gerido pelo administrador do Office 365 e tem de contactá-lo para atualizar o seu endereço de e-mail.
   > 
   > 
   
   ![](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)
3. No campo E-mail Alternativo, introduza o endereço de e-mail para o qual quer que sejam enviadas as atualizações do Power BI.

> [!NOTE]
> A alteração desta definição não afetará o endereço de e-mail utilizado para enviar atualizações do serviço, newsletters e outras comunicações promocionais.  Estas serão sempre enviadas para o endereço de e-mail utilizado originalmente no registo no Power BI.
> 
> 

## <a name="updating-with-powershell"></a>Atualizar com o PowerShell
Em alternativa, pode atualizar o endereço de e-mail alternativo através do PowerShell para o Azure Active Directory. Deve fazê-lo com o comando [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser).

```
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

Para obter mais informações, consulte [Azure Active Directory PowerShell Versão 2](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2).

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

