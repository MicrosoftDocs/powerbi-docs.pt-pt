---
title: Segurança ao nível da linha (RLS) com o Power BI
description: Como configurar a segurança ao nível da linha para conjuntos de dados importados, e DirectQuery, no serviço Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.author: mblythe
ms.date: 01/02/2018
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: f26d1d394446653764b8b0f7371a44fc178b01e2
ms.sourcegitcommit: d9755602235ba03594c348571b9102c9bf88d732
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490416"
---
# <a name="row-level-security-rls-with-power-bi"></a>Segurança ao nível da linha (RLS) com o Power BI

A segurança ao nível da linha (RLS) com o Power BI pode ser utilizada para restringir o acesso a dados para determinados utilizadores. Os filtros restringem o acesso aos dados ao nível da linha e pode definir filtros nas funções. Tenha em atenção que, no serviço Power BI, os membros de uma área de trabalho têm acesso a conjuntos de dados na área de trabalho. A RLS não restringe este acesso a dados.

Pode configurar a RLS para modelos de dados importados para o Power BI com o Power BI Desktop. Também pode configurar a RLS em conjuntos de dados que utilizem o DirectQuery, como o SQL Server. Anteriormente, só era possível implementar a RLS em modelos dos Analysis Services no local fora do Power BI. Para as ligações em direto dos Analysis Services, configure a segurança ao nível da linha no modelo no local. A opção de segurança não vai ser apresentada para conjuntos de dados de ligação em direto.

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

Por predefinição, a filtragem de segurança ao nível da linha utiliza filtros unidirecionais, independentemente de as relações estarem definidas como unidirecionais ou bidirecionais. Pode ativar manualmente o filtro cruzado bidirecional com segurança ao nível da linha ao selecionar a relação e ao marcar a caixa de verificação**Aplicar filtros de segurança em ambas as direções**. Deve marcar esta caixa ao implementar a [segurança dinâmica ao nível da linha](https://docs.microsoft.com/sql/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters), com a qual obtém segurança ao nível da linha com base no nome de utilizador ou no ID de início de sessão.

Para obter mais informações, veja [Bidirectional cross-filtering using DirectQuery in Power BI Desktop (Filtragem cruzada bidirecional com o DirectQuery no Power BI Desktop)](desktop-bidirectional-filtering.md) e o artigo técnico [Securing the Tabular BI Semantic Model (Proteger o Modelo Semântico Tabular do BI)](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

![Aplicar o Filtro de Segurança](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Gerir a segurança no modelo

Para gerir a segurança no modelo de dados, é necessário fazer o seguinte.

1. Selecione as **reticências (...)** para um conjunto de dados.
2. Selecione **Segurança**.
   
   ![Aplicar filtros de segurança em ambas as direções](media/service-admin-rls/rls-security.png)

Esta ação leva-o para a página RLS para adicionar membros a uma função que criou no Power BI Desktop. Apenas os proprietários do conjunto de dados verão a opção Segurança disponível. Se o conjunto de dados estiver num Grupo, apenas os Administradores do grupo verão a opção de segurança. 

Só poderá criar ou modificar funções dentro do Power BI Desktop.

## <a name="working-with-members"></a>Trabalhar com membros

### <a name="add-members"></a>Adicionar membros

Pode adicionar um membro à função ao introduzir o endereço de e-mail ou o nome do utilizador, grupo de segurança ou lista de distribuição que pretende adicionar. Não é possível adicionar Grupos criados no Power BI. Pode adicionar membros [externos à sua organização](whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Adicionar um membro](media/service-admin-rls/rls-add-member.png)

Também pode ver quantos membros fazem parte da função pelo número entre parênteses ao lado do nome da função ou ao lado de Membros.

![Membros na função](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Remover membros

É possível remover membros selecionando o X ao lado do nome. 

![Remover membro](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validar a função no serviço Power BI

Pode validar que a função que definiu está a funcionar corretamente ao testar a função. 

1. Selecione as **reticências (...)** junto à função.
2. Selecione **Testar dados como função**

![Testar como função](media/service-admin-rls/rls-test-role.png)

Em seguida, irá ver os relatórios que estão disponíveis para esta função. Os dashboards não são apresentados nesta vista. Na barra azul acima, verá o que está a ser aplicado.

![A ver agora como <role>](media/service-admin-rls/rls-test-role2.png)

Pode testar outras funções ou combinação de funções, selecionando **A ver agora como**.

![Testar outras funções](media/service-admin-rls/rls-test-role3.png)

Pode optar por ver os dados como uma pessoa específica ou pode selecionar uma combinação de funções disponíveis para validar que estão a funcionar. 

Para voltar à visualização normal, selecione **Voltar à Segurança de Nível de Linha**.

[!INCLUDE [include-short-name](./includes/rls-usernames.md)]

## <a name="using-rls-with-app-workspaces-in-power-bi"></a>Utilizar a RLS com áreas de trabalho de aplicação no Power BI

Se publicar o relatório do Power BI Desktop numa área de trabalho de aplicação no serviço Power BI, as funções serão aplicadas aos membros só de leitura. Terá de indicar que os membros só podem ver o conteúdo do Power BI nas definições de área de trabalho da aplicação.

> [!WARNING]
> Se tiver configurado a área de trabalho de aplicação para que os membros tenham permissões de edição, as funções de RLS não serão aplicadas às mesmas. Os utilizadores poderão ver todos os dados.

![Definições de grupo](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Próximos passos
[Segurança ao nível da linha (RLS) com o Power BI Desktop](desktop-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
