---
title: Compreender as funções de administrador do Power BI
description: Este artigo descreve as funções de administrador do serviço Power BI e as funções específicas que fornecem privilégios de administrador.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/8/2021
LocalizationGroup: Administration
ms.openlocfilehash: 1f06986333824ad6a7ad6a1ca38abb164b55ced8
ms.sourcegitcommit: f791eef8e885f18c48997c9af63ab56211f1ceb8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2021
ms.locfileid: "98053380"
---
# <a name="understanding-power-bi-administrator-roles"></a>Compreender as funções de administrador do Power BI

Para administrar o Power BI para a organização, tem de ter uma das seguintes funções: administrador do Power BI, administrador do Power Platform ou administrador global do Microsoft 365. Os administradores de gestão de utilizadores do Microsoft 365 atribuem utilizadores às funções de administrador do Power BI ou administrador do Power Platform no centro de administração do Microsoft 365 ou através de um script do PowerShell. Para obter mais informações, veja [Assign roles to user accounts with PowerShell](/office365/enterprise/powershell/assign-roles-to-user-accounts-with-office-365-powershell) (Atribuir funções a contas de utilizadores com o PowerShell).

Os utilizadores com funções de administrador do Power BI e administrador do Power Platform têm controlo total ao nível da organização sobre as definições e funcionalidades administrativas do Power BI, à exceção do licenciamento. Depois de ser atribuída a função de administrador a um utilizador, este poderá aceder ao [portal de administração do Power BI](service-admin-portal.md). No portal, tem acesso a métricas de utilização ao nível da organização e pode controlar a utilização das funcionalidades do Power BI também ao nível da organização. Estas funções de administrador são ideais para os utilizadores que precisam de ter acesso ao portal de administração do Power BI sem conceder também a esses utilizadores acesso administrativo completo ao Microsoft 365.

> [!NOTE]
> Na documentação do Power BI, "administrador do Power BI" refere-se aos utilizadores com funções de administrador do Power BI ou de administrador do Power Platform. A documentação clarifica quando a função de administrador global do Microsoft 365 é necessária para uma tarefa.

## <a name="limitations-and-considerations"></a>Limitações e considerações

As funções de administrador do Power BI e de administrador do Power Platform não disponibilizam as seguintes capacidades:

* Capacidade de modificar utilizadores e licenças no centro de administração do Microsoft 365.

* Acesso aos registos de auditoria. Para obter mais informações, veja [Controlar as atividades dos utilizadores no Power BI](service-admin-auditing.md).

Estas capacidades exigem atribuições da função de administrador do Microsoft 365.

## <a name="assign-users-to-an-admin-role-in-the-microsoft-365-admin-center"></a>Atribuir uma função de administrador aos utilizadores no centro de administração do Microsoft 365

Para atribuir uma função de administrador aos utilizadores no centro de administração do Microsoft 365, siga estes passos.

1. No [centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage), selecione **Utilizadores** > **Utilizadores Ativos**.

    ![Centro de administração do Microsoft 365](media/service-admin-role/powerbi-admin-users.png)

1. Selecione o utilizador ao qual pretende atribuir a função.

1. Em **Funções**, selecione **Gerir funções**.

    ![Gerir funções](media/service-admin-role/powerbi-admin-edit-roles.png)

1. Expanda **Mostrar tudo por categoria** e, em seguida, selecione **Administrador do Power BI** ou **Administrador do Power Platform**.

    ![Selecionar função de administrador](media/service-admin-role/powerbi-admin-role.png)

1. Selecione **Guardar alterações**.

## <a name="assign-users-to-the-admin-role-with-powershell"></a>Atribuir utilizadores à função de administrador no PowerShell

Também pode atribuir utilizadores às funções com o PowerShell. Os utilizadores são geridos no Microsoft Azure Active Directory (Microsoft Azure AD). Se ainda não tiver o módulo Azure AD PowerShell, [transfira e instale a versão mais recente](https://www.powershellgallery.com/packages/AzureAD/).

1. Ligar ao Azure AD:
   ```
   PS C:\Windows\system32> Connect-AzureAD
   ```

1. Obtenha o **ObjectId** da função **Administrador do Power BI**. Pode executar [Get-AzureADDirectoryRole](/powershell/module/azuread/get-azureaddirectoryrole) para obter o **ObjectId**

    ```
    PS C:\Windows\system32> Get-AzureADDirectoryRole

    ObjectId                             DisplayName                        Description
    --------                             -----------                        -----------
    00f79122-c45d-436d-8d4a-2c0c6ca246bf Power BI Service Administrator     Full access in the Power BI Service.
    250d1222-4bc0-4b4b-8466-5d5765d14af9 Helpdesk Administrator             Helpdesk Administrator has access to perform..
    3ddec257-efdc-423d-9d24-b7cf29e0c86b Directory Synchronization Accounts Directory Synchronization Accounts
    50daa576-896c-4bf3-a84e-1d9d1875c7a7 Company Administrator              Company Administrator role has full access t..
    6a452384-6eb9-4793-8782-f4e7313b4dfd Device Administrators              Device Administrators
    9900b7db-35d9-4e56-a8e3-c5026cac3a11 AdHoc License Administrator        Allows access manage AdHoc license.
    a3631cce-16ce-47a3-bbe1-79b9774a0570 Directory Readers                  Allows access to various read only tasks in ..
    f727e2f3-0829-41a7-8c5c-5af83c37f57b Email Verified User Creator        Allows creation of new email verified users.
    ```

    Neste caso, o **ObjectId** da função é 00f79122-c45d-436d-8d4a-2c0c6ca246bf.

1. Em seguida, obtenha o **ObjectId** do utilizador. Para encontrá-lo, execute [Get-AzureADUser](/powershell/module/azuread/get-azureaduser).

    ```
    PS C:\Windows\system32> Get-AzureADUser -ObjectId 'tim@contoso.com'

    ObjectId                             DisplayName UserPrincipalName      UserType
    --------                             ----------- -----------------      --------
    6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c Tim         tim@contoso.com        Member
    ```

1. Para adicionar o membro à função, execute [Add-AzureADDirectoryRoleMember](/powershell/module/azuread/add-azureaddirectoryrolemember).

    | Parâmetro | Descrição |
    | --- | --- |
    | ObjectId |O ObjectId da Função. |
    | RefObjectId |O ObjectId dos membros. |

    ```powershell
    Add-AzureADDirectoryRoleMember -ObjectId 00f79122-c45d-436d-8d4a-2c0c6ca246bf -RefObjectId 6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c
    ```
Para saber mais sobre a utilização do PowerShell para atribuir funções de administrador, veja [Funções de Diretório do Azure AD](/powershell/module/azuread/#directory-roles).

## <a name="next-steps"></a>Passos seguintes

[Administrar o Power BI na sua organização](service-admin-administering-power-bi-in-your-organization.md)  
[Portal de administração do Power BI](service-admin-portal.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
