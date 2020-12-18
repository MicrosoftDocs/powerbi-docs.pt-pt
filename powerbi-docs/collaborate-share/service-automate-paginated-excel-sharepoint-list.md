---
title: Exportar um relatório paginado para cada linha numa tabela do Excel Online ou numa lista do SharePoint
description: Neste artigo, vai utilizar o Power Automate para automatizar a exportação de um relatório paginado para cada linha numa tabela do Excel Online ou numa lista do SharePoint Online.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: 7a48a9a594364de4261aa66de48c1a4262392364
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097852"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>Exportar um relatório paginado para cada linha numa tabela do Excel Online ou numa lista do SharePoint

Com o [Power Automate](/power-automate/getting-started), pode automatizar a exportação e a distribuição de relatórios paginados do Power BI para vários cenários e formatos suportados. Neste artigo, vai utilizar um modelo do Power Automate para automatizar a configuração de exportações recorrentes de um ou de vários relatórios paginados. Vai exporta-los no formato desejado para cada linha, numa tabela do Excel Online ou numa lista do SharePoint Online. Pode distribuir o relatório paginado exportado para o OneDrive para Empresas ou para um site do SharePoint Online ou enviá-lo por email através do Outlook do Office 365.

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="Exportar um relatório paginado com uma tabela do Excel Online.":::

Cada linha na tabela do Excel Online ou na lista do SharePoint Online pode representar um único utilizador para receber um relatório paginado numa base de subscrição. Ou, em alternativa, cada linha pode representar um relatório paginado exclusivo que quer distribuir. A tabela ou lista exige uma coluna para especificar como distribuir um relatório, seja o OneDrive, o SharePoint Online ou o Outlook. O fluxo do Power Automate utiliza esta coluna na instrução Switch.

Procura outros modelos do Power Automate para os relatórios paginados do Power BI? Veja [Exportar relatórios paginados do Power BI com o Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Pré-requisitos  

Para acompanhar, confirme que tem:

- Pelo menos, uma área de trabalho no inquilino do Power BI apoiado por uma capacidade reservada. Esta capacidade pode ser qualquer uma das SKUs A4/P1 – A6/P3. Leia mais sobre as [capacidades reservadas dos relatórios paginados no Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Acesso aos conectores padrão no Power Automate, incluído em qualquer subscrição do Office 365.
- Se estiver a utilizar uma tabela do Excel Online, esta precisará de ser formatada como uma tabela no Excel. Veja [Criar uma tabela](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) para saber como.

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>Exportar um relatório paginado para cada linha numa tabela ou lista

> [!NOTE]
> Os passos e imagens seguintes mostram a configuração de um fluxo com o modelo **Exportar um relatório paginado do Power BI para cada linha numa tabela do Excel Online**. Pode seguir os mesmos passos para criar um fluxo com o modelo **Exportar um relatório paginado do Power BI para os itens numa lista do SharePoint Online**. Em vez de uma tabela do Excel Online, a lista do SharePoint Online conterá as informações sobre como exportar o relatório paginado.  

1. Inicie sessão no Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Selecione **Modelos** e procure  **relatórios paginados**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Captura de ecrã a mostrar os modelos do Power Automate para os relatórios paginados do Power BI.":::

1. Selecione o modelo **Exportar um relatório paginado do Power BI para cada linha numa tabela do Excel Online** ou **Exportar um relatório paginado do Power BI para os itens numa lista do SharePoint Online**. Verifique se tem sessão iniciada no Excel Online, Power BI, OneDrive para Empresas, SharePoint Online e Outlook do Office 365. Selecione **Continuar**.  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="Exportar um relatório paginado do Power BI para cada linha numa tabela do Excel Online":::.

1. Para definir a **Recorrência** do fluxo, selecione uma opção em **Frequência** e introduza o valor do **Intervalo** desejado.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="Selecionar a recorrência do fluxo.":::

1. (Opcional) Selecione **Mostrar opções avançadas** para definir os parâmetros de **Recorrência** adicionais, incluindo **Fuso horário**, **Hora de início**, **Nestes dias**, **Nestas horas** e **Nestes minutos**.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="Opcional, selecionar as opções de recorrência avançadas.":::

1. Na caixa **Localização**, selecione OneDrive para Empresas ou o site do SharePoint Online onde a tabela do Excel Online ou a lista do SharePoint Online foi guardada. Em seguida, selecione a **Biblioteca de Documentos** na lista pendente.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="Selecionar a localização da tabela do Excel Online.":::

1. Selecione o ficheiro do Excel Online ou a lista do SharePoint Online na caixa **Ficheiro**. Selecione o nome da tabela ou lista na lista pendente na caixa **Tabela**. 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="Selecionar o ficheiro do Excel Online e o nome da tabela.":::

    > [!TIP]
    > Veja [Criar uma tabela](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) para saber como formatar os dados como uma tabela no Excel. 

1. Inicialize uma variável para utilizar como nome do ficheiro. Pode manter ou modificar os valores predefinidos de **Nome** e **Valor**, mas deixar **Tipo** igual à **Cadeia de Carateres**.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="Preencher o Nome e Valor e manter Tipo igual à Cadeia de Carateres.":::

1. Em **Aplicar a Cada**, a caixa **Selecionar uma saída do passo anterior** está definida como **valor** por predefinição. Esta definição itera através das ações contidas em **Aplicar a Cada** para cada linha na tabela do Excel Online ou na lista do SharePoint Online.  

1. Na caixa **Área de Trabalho**, selecione uma área de trabalho com uma capacidade reservada. Na caixa **Relatório**, selecione o relatório paginado na área de trabalho selecionada que quer exportar. Se definiu **Introduzir um valor personalizado** na lista pendente, poderá definir **Área de Trabalho** e **Relatório** para serem iguais a uma coluna na tabela do Excel Online ou na lista do SharePoint Online. Estas colunas devem conter os IDs da Área de Trabalho e os IDs de Relatório, respetivamente.  

1. Selecione um **Formato de Exportação** na lista suspensa ou defina-o para ser igual a uma coluna na tabela do Excel Online que contém os formatos de exportação desejados, por exemplo, PDF, DOCX ou PPTX. Opcionalmente, pode especificar os parâmetros do relatório paginado. Encontre descrições detalhadas dos parâmetros na [referência do conector da API REST do Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="Preencher Exportar para Ficheiro para Relatórios Paginados.":::

1. Na caixa **Valor**, introduza um nome para o relatório paginado após ter sido exportado. Confirme que introduz a extensão de ficheiro. Pode defini-la estaticamente, por exemplo, .pdf, .docx ou .pptx. Ou defini-la dinamicamente ao selecionar a coluna na tabela do Excel correspondente ao formato de exportação desejado. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="Selecionar o nome do relatório e uma extensão de ficheiro.":::

1. Na ação **Mudar**, preencha a caixa **Ligado** com a coluna na tabela do Excel Online que corresponde ao método de entrega desejado: **OneDrive**, **SharePoint** ou **E-mail**. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="Em Mudar, povoe a caixa Ligado com a coluna na tabela do Excel Online.":::

1. Em **Caso**, **Caso 2** e **Caso 3**, introduza os valores presentes na coluna da tabela do Excel Online selecionada no passo anterior.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="Introduzir os valores para Caso, Caso 2 e Caso 3.":::

1. Se guardar o relatório paginado no OneDrive, selecione o **Caminho da Pasta** onde deve ser guardado.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="Se guardar no OneDrive.":::

1. Se guardar o relatório paginado no SharePoint Online, introduza o **Endereço do Site** e o **Caminho da Pasta** onde deve ser guardado. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="Se guardar o relatório paginado no SharePoint Online.":::

1. Se estiver a enviar o relatório paginado como um e-mail através do Outlook, preencha as caixas **Para**, **Assunto** e **Corpo**. Estas caixas podem conter conteúdos estáticos ou conteúdos dinâmicos da tabela do Excel Online ou da lista do SharePoint Online. O Power Automate anexa automaticamente o relatório paginado a este e-mail.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="Se estiver a enviar o relatório paginado como um e-mail através do Outlook.":::

1. Quando tiver terminado, selecione  **Passo seguinte**  ou **Guardar**. O Power Automate cria e avalia o fluxo e informa-o se encontrar erros. 

1. Se existirem erros, selecione **Editar fluxo**  para os corrigir. Caso contrário, selecione a seta **Para trás** para ver os detalhes do fluxo e executar o novo fluxo. 


## <a name="next-steps"></a>Passos seguintes

- [Exportar relatórios paginados do Power BI com o Power Automate](service-automate-paginated-integration.md)
- [Introdução ao Power Automate](/power-automate/getting-started/)
- Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

