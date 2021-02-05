---
title: Ativar a autenticação do principal de serviço para as APIs de administração só de leitura (pré-visualização)
description: Saiba como ativar a autenticação do principal de serviço para permitir a utilização das APIs de administração só de leitura.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 02/04/2021
ms.author: painbar
ms.custom: ''
LocalizationGroup: Administration
ms.openlocfilehash: e255fbef8b29422ea7736e43adaa5e4197a6338f
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99569951"
---
# <a name="enable-service-principal-authentication-for-read-only-admin-apis-preview"></a>Ativar a autenticação do principal de serviço para as APIs de administração só de leitura (pré-visualização)

O principal de serviço é um método de autenticação que pode ser utilizado para permitir que uma aplicação do Azure Active Directory (AAD) aceda aos conteúdos e às APIs do serviço Power BI.
Quando cria uma aplicação do AAD, é criado um [objeto do principal de serviço](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). O objeto do principal de serviço, também conhecido como principal de serviço, permite que o AAD autentifique a aplicação. Uma vez autenticada, a aplicação pode aceder aos recursos do inquilino do AAD.

## <a name="method"></a>Método

Para ativar a autenticação do principal de serviço para as APIs só de leitura do Power BI, siga estes passos:

1. [Crie uma aplicação do AAD](/azure/active-directory/develop/howto-create-service-principal-portal). Se já tiver uma aplicação do AAD, poderá ignorar este passo. Anote o ID da aplicação para utilizar em passos posteriores. 
2. Crie um novo **Grupo de Segurança** no Azure Active Directory. [Leia mais sobre como criar um grupo básico e adicionar membros com o Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). Se já tiver um grupo de segurança, poderá ignorar este passo.
    Confirme que seleciona **Segurança** como o Tipo de grupo.

    ![Captura de ecrã a mostrar a caixa de diálogo de criação do novo grupo no portal do Azure.](media/read-only-apis-service-principal-auth/azure-portal-new-group-dialog.png)

3. Adicione o ID da aplicação como membro do grupo de segurança que criou. Para tal:
    1. Aceda ao **portal do Azure > Azure Active Directory > Grupos** e escolha o grupo de segurança criado no Passo 2.
    1. Selecione **Adicionar membros**.
    Nota: confirme que a aplicação que utiliza não tem nenhuma função de administrador do Power BI definida no portal do Azure. Para verificar isto: 
       * Inicie sessão no **portal do Azure** como Administrador Global, Administrador de Aplicações ou Administrador de Aplicações de Cloud. 
        * Selecione **Azure Active Directory** e, em seguida, **Aplicações empresariais**. 
        * Selecione a aplicação à qual quer conceder acesso ao Power BI. 
        * Selecione **Permissões**. Confirme que não existem permissões que exijam o consentimento do administrador do Power BI definidas nesta aplicação. Veja [Gerir o consentimento a aplicações e avaliar os pedidos de consentimento](/azure/active-directory/manage-apps/manage-consent-requests) para obter mais informações. 
4. Ative as definições de administração do serviço Power BI. Para efetuar este procedimento:
    1. Inicie sessão no portal de administração do Power BI. Tem de ser administrador do Power BI para ver a página de definições de inquilino.
    1. Em **Definições da API de administração**, verá **Permitir que os principais de serviço utilizem as APIs de administração só de leitura do Power BI (pré-visualização)** . Mova o botão para Ativado e, em seguida, selecione o botão de opção **Grupos de segurança específicos** e adicione o grupo de segurança que criou no Passo 2 no campo de texto que aparece abaixo, conforme mostrado na imagem abaixo.

        ![Captura de ecrã a mostrar a definição de inquilino para permitir principais de serviço.](media/read-only-apis-service-principal-auth/allow-service-principals-tenant-setting.png)

 5. Comece a utilizar as APIs de administração só de leitura. Veja a lista de APIs suportadas abaixo.

    >[!IMPORTANT]
    >Assim que ativar o principal de serviço a ser utilizado com o Power BI, as permissões do AAD da aplicação deixarão de ter efeito. Em seguida, as permissões da aplicação serão geridas através do portal de administração do Power BI.

## <a name="supported-apis"></a>APIs suportadas

Atualmente, o principal de serviço suporta as APIs seguintes:
* [GetGroupsAsAdmin](/rest/api/power-bi/admin/groups_getgroupsasadmin) com $expand para dashboards, conjuntos de dados, relatórios e fluxos de dados 
* [GetDashboardsAsAdmin](/rest/api/power-bi/admin/dashboards_getdashboardsasadmin) com mosaicos $expand
* [GetDatasourcesAsAdmin](/rest/api/power-bi/admin/datasets_getdatasourcesasadmin) 
* [GetDatasetToDataflowsLinksAsAdmin](/rest/api/power-bi/admin/datasets_getdatasettodataflowslinksingroupasadmin)
* [GetDataflowDatasourcesAsAdmin](/rest/api/power-bi/admin/dataflows_getdataflowdatasourcesasadmin) 
* [GetDataflowUpstreamDataflowsAsAdmin](/rest/api/power-bi/admin/dataflows_getupstreamdataflowsingroupasadmin) 
* [GetCapacitiesAsAdmin](/rest/api/power-bi/admin/getcapacitiesasadmin)
* [GetActivityLog](/rest/api/power-bi/admin/getactivityevents)
* [GetModifiedWorkspaces](/rest/api/power-bi/admin/workspaceinfo_getmodifiedworkspaces)
* [WorkspaceGetInfo](/rest/api/power-bi/admin/workspaceinfo_postworkspaceinfo)
* [WorkspaceScanStatus](/rest/api/power-bi/admin/workspaceinfo_getscanstatus)
* [WorkspaceScanResult](/rest/api/power-bi/admin/workspaceinfo_getscanresult)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Não pode iniciar sessão no portal do Power BI com o principal de serviço.
* São necessários direitos de administrador do Power BI para ativar o principal de serviço nas definições da API de Administração no portal de administração do Power BI.