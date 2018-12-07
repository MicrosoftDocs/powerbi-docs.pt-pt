---
title: Publicar um relatório paginado no serviço Power BI (Pré-visualização)
description: Neste tutorial, vai aprender a publicar um relatório paginado no serviço Power BI ao carregá-lo do computador local.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: 1114f1949c68e4bebf2d636906bf754e7de77273
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900273"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service-preview"></a>Publicar um relatório paginado no serviço Power BI (Pré-visualização)

Neste artigo, vai aprender a publicar um relatório paginado no serviço Power BI ao carregá-lo do computador local. Pode carregar os relatórios paginados em A Minha Área de Trabalho ou em qualquer outra área de trabalho, desde que a área de trabalho esteja numa capacidade Premium. Procure o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto ao nome da área de trabalho. 

Se a sua origem de dados do relatório estiver no local, precisará de [criar um gateway](#create-a-gateway-to-an-on-premises-data-source) depois de carregar o relatório.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Adicionar uma área de trabalho a uma capacidade Premium

Se a área de trabalho não tiver o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto ao nome, terá de adicionar a área de trabalho a uma capacidade Premium. 

1. Selecione **Áreas de trabalho**, selecione as reticências (**…**) junto ao nome da área de trabalho e, em seguida, selecione **Editar área de trabalho**.

    ![Selecionar Editar área de trabalho](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Na caixa de diálogo **Editar área de trabalho**, expanda **Avançado** e, em seguida, deslize **Capacidade dedicada** para **Ativa**.

    ![Selecionar Capacidade dedicada](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Poderá não conseguir alterá-la. Se não conseguir, contacte o seu administrador de capacidade do Power BI Premium para que tenha direitos de atribuição para adicionar a sua área de trabalho a uma capacidade Premium.


## <a name="upload-a-paginated-report"></a>Carregar um relatório paginado

1. Crie o relatório paginado no Report Builder e guarde-o no computador local.

1. Abra o serviço Power BI num browser e navegue para a área de trabalho Premium onde quer publicar o relatório. Repare no ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto do nome. 

1. Selecione **Obter Dados**.

    ![Obter Dados no Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Na caixa **Ficheiros** , selecione **Obter**.

    ![Obter Ficheiros no Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Selecione **Ficheiro local** > navegue para o relatório paginado > **Abrir**.

    ![Selecionar Ficheiro Local](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Selecione **Continuar** > **Editar credenciais**.

    ![Selecionar Editar credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configure as suas credenciais > **Iniciar sessão**.

    ![Editar credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Pode ver o relatório na lista de relatórios.

    ![Relatório paginado na Lista de relatórios](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecione-o para o abrir no serviço Power BI. Se tiver parâmetros, precisará de os selecionar para poder ver o relatório.
 
    ![Selecionar parâmetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Criar um gateway

Tal como qualquer outro relatório do Power BI, se a origem de dados do relatório for no local, terá de criar ou ligar a um gateway para aceder aos dados.

1. Junto ao nome do relatório, selecione **Gerir**.

   ![Gerir o relatório paginado](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Veja o artigo do serviço Power BI [Instalar um gateway](service-gateway-install.md) para obter os detalhes e os passos seguintes.

### <a name="gateway-limitations"></a>Limitações do gateway

Atualmente, os gateways não suportam parâmetros de valor múltiplo.


## <a name="next-steps"></a>Próximos passos

- [Ver um relatório paginado no serviço Power BI](paginated-reports-view-power-bi-service.md)
- [O que são relatórios paginados no Power BI Premium? (Pré-visualização)](paginated-reports-report-builder-power-bi.md)

