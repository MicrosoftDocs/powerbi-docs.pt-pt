---
title: Transferir o .rdl para um relatório paginado a partir de um conjunto de dados
description: Neste artigo, irá aprender a criar o .rdl para um relatório paginado do Power BI, ao transferi-lo a partir de um conjunto de dados partilhado no serviço Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 10/15/2020
ms.openlocfilehash: c5c8f61a7253da46529a83276366044560d4f030
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297622"
---
# <a name="download-the-rdl-for-a-power-bi-paginated-report-from-a-dataset"></a>Transferir o .rdl para um relatório paginado do Power BI a partir de um conjunto de dados

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Neste artigo, irá aprender a criar o .rdl para um relatório paginado do Power BI, ao transferi-lo a partir de um conjunto de dados partilhado no serviço Power BI. Os relatórios paginados têm o formato de ficheiro *.rdl*. Pode criar um ficheiro .rdl diretamente a partir de um conjunto de dados no serviço Power BI.

1. Aceda à vista de lista de qualquer área de trabalho, incluindo A Minha Área de Trabalho. 
1. Selecione **Mais opções (...)** de um conjunto de dados e, em seguida, selecione **Transferir o .rdl**.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-download-rdl.png" alt-text="Captura de ecrã a mostrar a opção Transferir o .rdl no serviço Power BI.":::
1. Verá uma mensagem a indicar que precisa de algumas atualizações do Power BI Report Builder. Selecione **Transferir**. 

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-updates.png" alt-text="Captura de ecrã a mostrar a instalação de atualizações do Power BI Report Builder.":::

    Se souber que tem a versão mais recente do Power BI Report Builder, selecione **Já instalei estas atualizações**.

1. Siga o processo de instalação do Power BI Report Builder: 

    1. Selecione **Transferir**.  
    2. Selecione **Abrir ficheiro** e siga os passos do Assistente de Instalação do Power BI Report Builder.

1. Quando a instalação do Report Builder tiver terminado, volte ao serviço Power BI e selecione **Transferir o .rdl**.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-finished-installing.png" alt-text="Captura de ecrã a mostrar a caixa de diálogo Transferir o .rdl.":::

1. Selecione **Abrir ficheiro** na janela do browser.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-open-file.png" alt-text="Captura de ecrã a mostrar a seleção Abrir Ficheiro num browser.":::

1. O Power BI Report Builder é aberto com um título gerado automaticamente e o ficheiro .pbix do conjunto de dados do Power BI na pasta **Origem de Dados**. A origem de dados tem o mesmo nome que o conjunto de dados do Power BI.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-design-canvas.png" alt-text="Captura de ecrã a mostrar o Power BI Report Builder na vista Estrutura.":::

    A superfície de desenho também apresenta uma ligação para o curso em vídeo [Relatórios Paginados do Power BI num Dia](../learning-catalog/paginated-reports-online-course.md). Se a criação de relatórios paginados for novidade para si, o curso será uma boa maneira de se familiarizar.  Poderá eliminá-lo quando começar a criar o relatório.

    Está pronto para começar a criar o relatório paginado.
 
## <a name="next-steps"></a>Próximos passos 

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Tutorial: Criar um relatório paginado e carregá-lo para o serviço Power BI](paginated-reports-quickstart-aw.md)
- [Publicar um relatório paginado no serviço Power BI](paginated-reports-save-to-power-bi-service.md)

