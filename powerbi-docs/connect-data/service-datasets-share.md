---
title: Partilhar um conjunto de dados
description: Enquanto proprietário de conjuntos de dados, pode criar e partilhar os seus conjuntos de dados, para que outras pessoas possam utilizá-los. Saiba como os pode partilhar.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 6a1fd2ee46edd2447e7cf5096307f9d4947168a6
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236726"
---
# <a name="share-a-dataset"></a>Partilhar um conjunto de dados

Enquanto criador de *modelos de dados* no Power BI Desktop, está a criar *conjuntos de dados* que pode distribuir no serviço Power BI. Em seguida, outros criadores de relatórios podem utilizar os seus conjuntos de dados como base para os seus próprios relatórios. Neste artigo, ficará a saber como partilhar os conjuntos de dados. Para saber como conceder e remover acesso aos conjuntos de dados partilhados, leia sobre a [Permissão de compilação](service-datasets-build-permissions.md).

## <a name="steps-to-sharing-your-dataset"></a>Passos para partilhar o seu conjunto de dados

1. Comece por criar um ficheiro .pbix com um modelo de dados no Power BI Desktop. Se planear dar este conjunto de dados a outras pessoas para compilarem relatórios, não terá de criar um relatório no ficheiro .pbix.

    A melhor prática é guardar o ficheiro .pbix num grupo do Microsoft 365.

1. Publique o ficheiro .pbix numa [nova experiência de área de trabalho](../collaborate-share/service-create-the-new-workspaces.md) no serviço Power BI.
    
    Assim, outros membros desta área de trabalho poderão criar relatórios noutras áreas de trabalho, com base neste conjunto de dados. Utilize a opção Gerir Permissões no conjunto de dados na lista de conteúdos da área de trabalho para dar acesso ao conjunto de dados a utilizadores adicionais. 

1. Também pode [publicar uma aplicação](../collaborate-share/service-create-distribute-apps.md) a partir desta área de trabalho. Quando o fizer, irá especificar quem tem permissões e o que estas pessoas podem fazer na página **Permissões**.

    > [!NOTE]
    > Se selecionar **Toda a organização**, nenhuma pessoa na organização terá Permissão de compilação. Este problema já é conhecido. Em vez disto, especifique os endereços de e-mail em **Pessoas ou grupos específicos**.  Se quiser que toda a organização tenha Permissão de compilação, especifique um alias de e-mail para toda a organização.

    ![Definir as permissões da aplicação](media/service-datasets-build-permissions/power-bi-dataset-app-permission-new-look.png)

1. Selecione **Publicar aplicação** ou **Atualizar aplicação**, se a aplicação já estiver publicada.

## <a name="track-your-dataset-usage"></a>Controlar a utilização do seu conjunto de dados

Quando tiver um conjunto de dados partilhado na sua área de trabalho, poderá ter de saber que relatórios noutras áreas de trabalho se baseiam no mesmo.

1. Na vista de lista Conjuntos de dados, selecione **Ver relacionados**.

    ![ícone Ver relacionados](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. A caixa de diálogo **Conteúdo relacionado** apresenta todos os itens relacionados. Nesta lista, são apresentados os itens relacionados nesta área de trabalho e em **Outras áreas de trabalho**.
 
    ![Caixa de diálogo Conteúdo relacionado](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações
Elementos a ter em conta sobre a partilha de conjuntos de dados:

* Quando partilha um conjunto de dados através das permissões de gestão, ao partilhar relatórios ou dashboards ou ao publicar uma aplicação, está a conceder acesso a todo o conjunto de dados, a menos que a [segurança ao nível de linha (RLS)](../admin/service-admin-rls.md) limite o seu acesso. Os autores de relatórios podem utilizar capacidades que personalizem as experiências de utilizadores ao ver ou interagir com relatórios, por exemplo ao ocultar colunas, limitar as ações em elementos visuais, entre outros. Estas experiências de utilizador personalizadas não restringem aquilo a que os utilizadores de dados podem aceder no conjunto de dados. Utilize a [segurança ao nível de linha (RLS)](../admin/service-admin-rls.md) no conjunto de dados para que as credenciais de cada pessoa determinem a que dados esta pode aceder.

## <a name="next-steps"></a>Próximos passos

- [Utilizar conjuntos de dados em áreas de trabalho](service-datasets-across-workspaces.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
