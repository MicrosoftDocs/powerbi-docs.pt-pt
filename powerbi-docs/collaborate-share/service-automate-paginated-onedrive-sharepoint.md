---
title: Guardar um relatório paginado no OneDrive para Empresas ou no SharePoint Online
description: Neste artigo, vai utilizar o Power Automate para automatizar a ação de guardar um relatório paginado do Power BI numa pasta do OneDrive para Empresas ou do SharePoint Online.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 6aaad48fb3e97aa6c1b4fc51834ee593a49a8192
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097737"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>Guardar um relatório paginado no OneDrive para Empresas ou no SharePoint Online

Com o [Power Automate](/power-automate/getting-started), pode automatizar a exportação e a distribuição de relatórios paginados do Power BI para vários cenários e formatos suportados. Neste artigo, vai utilizar o Power Automate para automatizar a ação de guardar um relatório paginado do Power BI numa pasta do OneDrive para Empresas ou do SharePoint Online.


:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="Captura de ecrã a mostrar o fluxo do Power Automate para guardar um relatório paginado no OneDrive ou no SharePoint Online":::

Procura outros modelos do Power Automate para os relatórios paginados do Power BI? Veja [Exportar relatórios paginados do Power BI com o Power Automate](service-automate-paginated-integration.md). 

## <a name="prerequisites"></a>Pré-requisitos  

Para acompanhar, confirme que tem:

- Pelo menos, uma área de trabalho no inquilino do Power BI apoiado por uma capacidade reservada. Esta capacidade pode ser qualquer uma das SKUs A4/P1 – A6/P3. Leia mais sobre as [capacidades reservadas dos relatórios paginados no Power BI Premium](../admin/service-premium-what-is.md#paginated-reports)
- Acesso aos conectores padrão no Power Automate, incluído em qualquer subscrição do Office 365.

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>Guardar um relatório paginado numa pasta do OneDrive para Empresas ou do SharePoint Online 

Com qualquer um destes modelos, vai configurar exportações recorrentes de um relatório paginado num formato desejado para uma pasta do OneDrive para Empresas ou do SharePoint Online. Veja os pré-requisitos se esta for a primeira vez que utiliza a ação Exportar para Ficheiro para os Relatórios Paginados num fluxo do Power Automate. 

> [!NOTE]
> Os passos e imagens seguintes mostram a configuração de um fluxo com o modelo **Guardar um relatório paginado do Power BI no OneDrive para Empresas**. Siga os mesmos passos para criar um fluxo com o modelo **Guardar um relatório paginado do Power BI numa pasta do OneDrive para Empresas**. Ao selecionar para onde quer exportar o relatório paginado, selecione uma pasta do SharePoint Online em vez de uma pasta do OneDrive para Empresas. 

1. Inicie sessão no Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Selecione **Modelos** e procure  **relatórios paginados**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Captura de ecrã a mostrar os modelos do Power Automate para os relatórios paginados do Power BI.":::

1. Selecione **Guardar um relatório paginado do Power BI no OneDrive para Empresas** ou **Guardar um relatório paginado do Power BI numa pasta do OneDrive para Empresas**. Verifique se tem sessão iniciada no Power BI e no OneDrive para Empresas ou no SharePoint Online.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="Captura de ecrã a mostrar a seleção do modelo do Power BI e do OneDrive para Empresas.":::
1. Selecione **Continuar**.  


1. Para definir a **Recorrência** do fluxo, selecione uma opção em **Frequência** e introduza o valor do **Intervalo** desejado.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="Selecionar a recorrência do fluxo.":::

1. (Opcional) Selecione **Mostrar opções avançadas** para definir os parâmetros de **Recorrência** adicionais, incluindo **Fuso horário**, **Hora de início**, **Nestes dias**, **Nestas horas** e **Nestes minutos**.  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="A mostrar as opções avançadas da recorrência.":::

1. Na caixa **Área de Trabalho**, selecione uma área de trabalho com uma capacidade reservada. Na caixa **Relatório**, selecione o relatório paginado na área de trabalho selecionada que quer exportar. Na caixa **Exportar Formato**, selecione o formato de exportação desejado. Opcionalmente, pode especificar os parâmetros do relatório paginado. Encontre descrições detalhadas dos parâmetros na [referência do conector da API Rest do Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="Selecionar o relatório paginado, a área de trabalho e o formato de exportação.":::

1. Em **Caminho da Pasta**, selecione a pasta do OneDrive para Empresas ou do SharePoint Online para onde quer exportar o relatório paginado.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="Selecionar o destino e criar o ficheiro.":::

1. O Power Automate gera automaticamente um **Nome de Ficheiro** e o **Conteúdo do Ficheiro**. Pode alterar o nome do ficheiro, mas manter o valor do **Conteúdo de Ficheiro** gerado dinamicamente. 

1. Quando tiver terminado, selecione  **Passo seguinte**  ou **Guardar**. O Power Automate cria e avalia o fluxo e informa-o se encontrar erros. 

1. Se existirem erros, selecione **Editar fluxo**  para os corrigir. Caso contrário, selecione a seta **Para trás** para ver os detalhes do fluxo e executar o novo fluxo. 

    Quando executa o fluxo, o Power Automate exporta um relatório paginado no formato especificado para o OneDrive para Empresas ou SharePoint Online.  

## <a name="next-steps"></a>Passos seguintes

- [Exportar relatórios paginados do Power BI com o Power Automate](service-automate-paginated-integration.md)
- [Introdução ao Power Automate](/power-automate/getting-started/)
- Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
