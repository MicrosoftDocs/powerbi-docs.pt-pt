---
title: Criação da aplicação do principal de serviço
description: Criação da aplicação do principal de serviço
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 10/15/2020
ms.custom: include file
ms.openlocfilehash: 0f6c74ddc5a7decc8c1a6444568de44d3adbbc68
ms.sourcegitcommit: 8561902ef0ad63b0881187a22f25d1aa1ec3bcbc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/20/2020
ms.locfileid: "92210766"
---
## <a name="step-2---create-an-azure-ad-security-group"></a>Passo 2 – Criar um grupo de segurança do AAD

O principal de serviço não tem acesso a nenhum dos conteúdos e APIs do Power BI. Para dar acesso ao principal de serviço, crie um grupo de segurança no AAD e adicione o principal de serviço que criou a esse grupo de segurança.

Há duas formas para criar um grupo de segurança do AAD:
* Manualmente (no Azure)
* Utilizar o PowerShell

### <a name="create-a-security-group-manually"></a>Criar um grupo de segurança manualmente

Para criar manualmente um grupo de segurança do Azure, siga as instruções no artigo [Criar um grupo básico e adicionar membros com o Azure Ative Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Criar um grupo de segurança com o PowerShell

Abaixo encontra-se um script de exemplo para criar um novo grupo de segurança e adicionar uma aplicação ao mesmo.

>[!NOTE]
>Se quiser ativar o acesso do principal de serviço para toda a organização, ignore este passo.

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>Passo 3 – Ativar as definições de administração do serviço Power BI

Para que uma aplicação do AAD possa aceder aos conteúdos e APIs do Power BI, o administrador do Power BI tem de permitir o acesso do principal de serviço no portal de administração do Power BI.

Adicione o grupo de segurança que criou no AAD à secção específica de grupos de segurança nas **Definições de programador** .

>[!IMPORTANT]
>Os principais de serviço têm acesso a todas as configurações de inquilino para os quais são ativados. Dependendo das suas definições de administração, tal pode incluir grupos de segurança específicos ou toda a organização.
>
>Para restringir o acesso do principal de serviço a configurações específicas de inquilino, permita o acesso apenas a grupos de segurança específicos. Em alternativa, pode criar um grupo de segurança dedicado para os principais de serviço e excluí-lo das configurações de inquilino pretendidas.

>[!div class="mx-imgBorder"]
>:::image type="content" source="../developer/embedded/media/embed-service-principal/admin-portal.png" alt-text="Captura de ecrã a mostrar as definições do programador nas opções de administrador no portal do Power BI.":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Passo 4 – Adicionar o principal de serviço à área de trabalho

Para permitir que a aplicação do AAD aceda a artefactos como relatórios, dashboards e conjuntos de dados no serviço Power BI, adicione a entidade do principal de serviço como membro ou administrador à área de trabalho.

>[!NOTE]
>Esta secção apresenta as instruções da IU. Também pode adicionar um principal de serviço a uma área de trabalho com a [API Groups – add group user](/rest/api/power-bi/groups/addgroupuser) (Grupos – adicionar utilizador de grupo).

1. Navegue para a área de trabalho à qual quer permitir o acesso e, no menu **Mais** , selecione **Acesso à área de trabalho** .

    :::image type="content" source="../developer/embedded/media/embed-service-principal/workspace-access.png" alt-text="Captura de ecrã a mostrar as definições do programador nas opções de administrador no portal do Power BI.":::

2. Adicione o principal de serviço como **Administrador** ou **Membro** à área de trabalho.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/add-service-principal-in-the-UI.png" alt-text="Captura de ecrã a mostrar as definições do programador nas opções de administrador no portal do Power BI.":::