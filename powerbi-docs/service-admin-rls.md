---
title: "Segurança ao nível da linha (RLS) com o Power BI"
description: "Como configurar a segurança ao nível da linha para conjuntos de dados importados, e DirectQuery, no serviço Power BI."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 08/11/2017
ms.author: asaxton
ms.openlocfilehash: ea51308d533dc97af9d06855d004b5bacc376247
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="row-level-security-rls-with-power-bi"></a>Segurança ao nível da linha (RLS) com o Power BI
<iframe width="560" height="315" src="https://www.youtube.com/embed/67fK0GoVQ80?showinfo=0" frameborder="0" allowfullscreen></iframe>

A segurança ao nível da linha (RLS) com o Power BI pode ser utilizada para restringir o acesso a dados para determinados utilizadores. Os filtros restringem os dados ao nível da linha. Pode definir filtros em funções.

Pode configurar a RLS para modelos de dados importados para o Power BI com o Power BI Desktop. Também pode configurar a RLS em conjuntos de dados que utilizem o DirectQuery, como o SQL Server. Anteriormente, só era possível implementar a RLS em modelos dos Analysis Services no local fora do Power BI. Para as ligações em direto dos Analysis Services, configura a segurança ao nível da linha no modelo no local. A opção de segurança não será apresentada para conjuntos de dados de ligação em direto.

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Gerir a segurança no modelo
Para gerir a segurança no modelo de dados, é necessário fazer o seguinte.

1. Selecione as **reticências (...)** para um conjunto de dados.
2. Selecione **Segurança**.
   
   ![](media/service-admin-rls/rls-security.png)

Esta ação leva-o para a página RLS para adicionar membros a uma função que criou no Power BI Desktop. Apenas os proprietários do conjunto de dados verão a opção Segurança disponível. Se o conjunto de dados estiver num Grupo, apenas os Administradores do grupo verão a opção de segurança. 

Só poderá criar ou modificar funções dentro do Power BI Desktop.

## <a name="working-with-members"></a>Trabalhar com membros
### <a name="add-members"></a>Adicionar membros
Pode adicionar um membro à função ao introduzir o endereço de e-mail ou o nome do utilizador, grupo de segurança ou lista de distribuição que pretende adicionar. Este membro tem de estar na sua organização. Não é possível adicionar Grupos criados no Power BI.

![](media/service-admin-rls/rls-add-member.png)

Também pode ver quantos membros fazem parte da função pelo número entre parênteses ao lado do nome da função ou ao lado de Membros.

![](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Remover membros
É possível remover membros selecionando o X ao lado do nome. 

![](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validar a função no serviço Power BI
Pode validar que a função que definiu está a funcionar corretamente ao testar a função. 

1. Selecione as **reticências (...)** junto à função.
2. Selecione **Testar dados como função**

![](media/service-admin-rls/rls-test-role.png)

Em seguida, irá ver os relatórios que estão disponíveis para esta função. Os dashboards não são apresentados nesta vista. Na barra azul acima, verá o que está a ser aplicado.

![](media/service-admin-rls/rls-test-role2.png)

Pode testar outras funções ou combinação de funções, selecionando **A ver agora como**.

![](media/service-admin-rls/rls-test-role3.png)

Pode optar por ver os dados como uma pessoa específica ou pode selecionar uma combinação de funções disponíveis para validar que estão a funcionar. 

Para voltar à visualização normal, selecione **Voltar à Segurança de Nível de Linha**.

[!INCLUDE [include-short-name](./includes/rls-usernames.md)]

## <a name="using-rls-with-app-workspaces-in-power-bi"></a>Utilizar a RLS com áreas de trabalho de aplicação no Power BI
Se publicar o relatório do Power BI Desktop numa área de trabalho de aplicação no serviço Power BI, as funções serão aplicadas aos membros só de leitura. Terá de indicar que os membros só podem ver o conteúdo do Power BI nas definições de área de trabalho da aplicação.

> [!WARNING]
> Se tiver configurado a área de trabalho de aplicação para que os membros tenham permissões de edição, as funções de RLS não serão aplicadas às mesmas. Os utilizadores poderão ver todos os dados.
> 
> 

![](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Próximos passos
[Segurança ao nível da linha (RLS) com o Power BI Desktop](desktop-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

