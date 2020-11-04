---
title: Publicar um relatório paginado no serviço Power BI
description: Neste tutorial, vai aprender a publicar um relatório paginado no serviço Power BI ao carregá-lo do computador local.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 05/04/2020
ms.openlocfilehash: 28058161672de9db0cac5093e652e1d551f6a80a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297314"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Publicar um relatório paginado no serviço Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Neste artigo, vai aprender a publicar um relatório paginado no serviço Power BI ao carregá-lo do computador local. Pode carregar os relatórios paginados em A Minha Área de Trabalho ou em qualquer outra área de trabalho, desde que a área de trabalho esteja numa capacidade Premium. Procure o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto ao nome da área de trabalho. 

Se a sua origem de dados do relatório estiver no local, precisará de criar um gateway depois de carregar o relatório. Consulte a secção [Criar um gateway](#create-a-gateway) mais à frente neste artigo.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Adicionar uma área de trabalho a uma capacidade Premium

Se a área de trabalho não tiver o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto ao nome, terá de adicionar a área de trabalho a uma capacidade Premium. 

1. Selecione **Áreas de trabalho** , selecione as reticências ( **…** ) junto ao nome da área de trabalho e, em seguida, selecione **Editar área de trabalho**.

    ![Selecionar Editar área de trabalho](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Na caixa de diálogo **Editar área de trabalho** , expanda **Avançado** e, em seguida, deslize **Capacidade dedicada** para **Ativa**.

    ![Selecionar Capacidade dedicada](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Poderá não conseguir alterá-la. Se não conseguir, contacte o seu administrador de capacidade do Power BI Premium para que tenha direitos de atribuição para adicionar a sua área de trabalho a uma capacidade Premium.

## <a name="from-report-builder-publish-a-paginated-report"></a>Publicar um relatório paginado no Report Builder

1. Crie o relatório paginado no Report Builder e guarde-o no computador local.

1. No menu **Ficheiro** do Report Builder, selecione **Guardar como**.

    ![Menu Ficheiro > Guardar > Guardar como](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Se ainda não tiver sessão iniciada no Power BI, terá de iniciar sessão ou criar uma conta agora. No canto superior direito do Report Builder, selecione **Iniciar sessão** e conclua os passos.

2. Na lista de áreas de trabalho à esquerda, selecione uma área de trabalho com o ícone de losango ![Ícone de losango da funcionalidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto ao respetivo nome. Escreva um **Nome de ficheiro** na caixa > **Guardar**. 

    ![Selecionar uma área de trabalho do Power BI Premium](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Abra o serviço Power BI num browser e navegue até à área de trabalho do Power BI Premium onde publicou o relatório paginado. No separador **Relatórios** , é apresentado o seu relatório.

    ![Relatório paginado na Lista de relatórios](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Selecione o relatório paginado para o abrir no serviço Power BI. Se tiver parâmetros, precisará de os selecionar para poder ver o relatório.

    ![Selecionar parâmetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Se a sua origem de dados do relatório estiver no local, saiba como [criar um gateway](#create-a-gateway) neste artigo para aceder à origem de dados.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Carregar um relatório paginado no serviço Power BI

Também pode começar no serviço Power BI e carregar um relatório paginado.

1. Crie o relatório paginado no Report Builder e guarde-o no computador local.

1. Abra o serviço Power BI num browser e navegue para a área de trabalho Premium onde quer publicar o relatório. Repare no ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto do nome. 

1. Selecione **Obter Dados**.

    ![Obter Dados do Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Na caixa **Ficheiros** , selecione **Obter**.

    ![Obter Ficheiros no Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Selecione **Ficheiro local** > navegue para o relatório paginado > **Abrir**.

    ![Selecionar Ficheiro Local](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Selecione **Continuar** > **Editar credenciais**.

    ![Selecionar Editar credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configure as suas credenciais > **Iniciar sessão**.

    ![Editar credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   No separador **Relatórios** , é apresentado o seu relatório.

    ![Relatório paginado na Lista de relatórios](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecione-o para o abrir no serviço Power BI. Se tiver parâmetros, precisará de os selecionar para poder ver o relatório.
 
    ![Selecionar parâmetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Se a sua origem de dados do relatório estiver no local, saiba como [criar um gateway](#create-a-gateway) neste artigo para aceder à origem de dados.

## <a name="create-a-gateway"></a>Criar um gateway

Tal como qualquer outro relatório do Power BI, se a origem de dados do relatório for no local, terá de criar ou ligar a um gateway para aceder aos dados.

1. Junto ao nome do relatório, selecione **Gerir**.

   ![Gerir o relatório paginado](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Veja o artigo do serviço Power BI [O que é um gateway de dados no local](../connect-data/service-gateway-onprem.md) para obter detalhes e os passos seguintes.



## <a name="next-steps"></a>Próximas etapas

- [Ver um relatório paginado no serviço Power BI](../consumer/paginated-reports-view-power-bi-service.md)
- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Tutorial: Incorporar relatórios paginados do Power BI numa aplicação para os clientes](../developer/embedded/embed-paginated-reports-customers.md)
