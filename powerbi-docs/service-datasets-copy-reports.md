---
title: Copiar relatórios de outras áreas de trabalho (Pré-visualização) – Power BI
description: Aprenda a partilhar um conjunto de dados com utilizadores na organização. Em seguida, estes poderão criar relatórios com base no seu conjunto de dados nas suas próprias áreas de trabalho.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461471"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Copiar relatórios de outras áreas de trabalho (Pré-visualização)

Aprenda a copiar um relatório de uma área de trabalho e guardá-lo numa área de trabalho diferente. Em seguida, poderá modificar esse relatório ao adicionar ou eliminar elementos visuais e outros elementos.

Quando encontrar um relatório do seu agrado, numa área de trabalho ou numa aplicação, poderá fazer uma cópia do mesmo e, em seguida, modificá-lo para que este se ajuste às suas necessidades. Não tem de se preocupar com a criação do modelo de dados. Já terá sido criado automaticamente. Além disso, é muito mais fácil modificar um relatório existente do que começar do zero.

## <a name="save-a-copy-of-a-report"></a>Guardar uma cópia de um relatório

1. Numa aplicação ou área de trabalho, aceda à vista Lista de relatórios.

1. Em **Ações**, selecione **Guardar uma cópia**.

    ![Guardar uma cópia de um relatório](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    O ícone **Guardar uma cópia** só será apresentado se o relatório estiver numa nova experiência de área de trabalho e se tiver [Permissões de compilação](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Mesmo com acesso à área de trabalho, terá de ter Permissões de compilação para o conjunto de dados.

3. Em **Guardar uma cópia deste relatório**, dê um nome ao relatório e selecione a área de trabalho de destino.

    ![Caixa de diálogo Guardar uma cópia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Pode guardar o relatório na área de trabalho atual ou numa diferente, no serviço Power BI. Só serão apresentadas novas experiências de áreas de trabalho das quais é membro.
  
4. Selecione **Guardar**.

    Quando guardar uma cópia do relatório, irá criar uma ligação em direto ao conjunto de dados e poderá abrir a experiência de criação de relatórios com todo o conjunto de dados disponível. Se não tiver feito uma cópia do conjunto de dados, este irá permanecer na sua localização original. Pode utilizar todas as tabelas e medidas presentes no conjunto de dados no seu próprio relatório. As restrições de segurança ao nível da linha (RLS) no conjunto de dados estarão em vigor, para que apenas sejam apresentados dados que tem permissão para ver, com base na sua função de RLS.

    O Power BI irá criar automaticamente uma entrada na lista de conjuntos de dados, se o relatório for baseado num conjunto de dados fora da área de trabalho. O ícone deste conjunto de dados é diferente do ícone dos conjuntos de dados na área de trabalho: ![Ícone Conjunto de dados partilhado](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    Desta forma, os membros da área de trabalho podem perceber quais os relatórios e dashboards que utilizam conjuntos de dados fora da mesma. A entrada apresenta informações sobre o conjunto de dados e algumas ações de seleção.

    ![Ações de conjuntos de dados](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Ver conjuntos de dados relacionados

Quando tiver um relatório na sua área de trabalho, poderá ter de saber em que conjunto de dados este se baseia.

1. Na vista Lista de relatórios, selecione **Ver relacionados**.

    ![ícone Ver relacionados](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. A caixa de diálogo **Conteúdos relacionados** apresenta todos os itens relacionados. Nesta lista, o conjunto de dados tem um aspeto semelhante a qualquer outro. Não é possível perceber que reside numa área de trabalho diferente. Este problema é conhecido.
 
    ![Caixa de diálogo Conteúdos relacionados](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>Próximos passos

- [Use datasets across workspaces (Preview)](service-datasets-across-workspaces.md) (Utilizar conjuntos de dados em áreas de trabalho [Pré-visualização])
- Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
