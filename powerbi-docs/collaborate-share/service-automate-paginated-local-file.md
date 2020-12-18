---
title: Guardar um relatório paginado numa pasta local com o Power Automate
description: Neste artigo, vai utilizar um modelo para configurar as exportações recorrentes de um relatório paginado para o sistema de ficheiros, no formato desejado.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098811"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>Guardar um relatório paginado do Power BI numa pasta local com o Power Automate

Com o [Power Automate](/power-automate/getting-started), pode automatizar a exportação e a distribuição de relatórios paginados do Power BI para vários cenários e formatos suportados. Neste artigo, vai utilizar um modelo para configurar as exportações recorrentes de um relatório paginado para o sistema de ficheiros, no formato desejado. Veja os Pré-requisitos se esta for a primeira vez que utiliza a ação Exportar para Ficheiro dos Relatórios Paginados num fluxo do Power Automate.

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="Configurar as exportações recorrentes de um relatório paginado.":::

Procura outros modelos do Power Automate para os relatórios paginados do Power BI? Veja [Exportar relatórios paginados do Power BI com o Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Pré-requisitos  

Para acompanhar, confirme que tem:

- Pelo menos, uma área de trabalho no inquilino do Power BI apoiado por uma capacidade reservada. Esta capacidade pode ser qualquer uma das SKUs A4/P1 – A6/P3. Leia mais sobre as [capacidades reservadas dos relatórios paginados no Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Acesso aos conectores padrão no Power Automate, incluído em qualquer subscrição do Office 365.

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>Guardar um relatório paginado do Power BI numa pasta local

1. Selecione o modelo **Guardar um relatório paginado do Power BI num sistema de ficheiros local**. Verifique se tem sessão iniciada no Power BI e se está ligado ao sistema de ficheiros local. Selecione **Continuar**. 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="Guardar um relatório paginado do Power BI num sistema de ficheiros local.":::

2. Talvez seja necessário selecionar **Adicionar nova ligação** para se ligar ao sistema de ficheiros. 
1. Introduza o **Nome da Ligação**, o caminho para a **Pasta raiz** desejada e autentique-se ao introduzir o **Nome de utilizador** e a **Palavra-passe**. Se estiver a utilizar um gateway de dados no local, selecione um **gateway** no menu pendente.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="Introduzir o Nome da ligação e a Pasta raiz.":::
 
3. Para definir a frequência de **Periodicidade** do fluxo, selecione uma opção no menu pendente **Frequência** e introduza o valor do **Intervalo** desejado.  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="Definir a frequência de Periodicidade do fluxo.":::

4. Opcionalmente, selecione **Mostrar opções avançadas**. Defina parâmetros de **Recorrência** adicionais, como **Fuso horário**, **Hora de início**, **Nestes dias**, **Nestas horas** e **Nestes minutos**. 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="Definir as opções avançadas da periodicidade.":::

5. Na caixa **Área de Trabalho**, selecione a área de trabalho com capacidade reservada onde se encontra o relatório. Na caixa **Relatório**, selecione o relatório paginado que quer exportar na área de trabalho. Na caixa **Exportar Formato**, selecione o formato de exportação desejado. Opcionalmente, pode especificar os parâmetros do relatório paginado. Veja as descrições detalhadas dos parâmetros na [referência do conector da API REST do Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="Selecionar a área de trabalho e o relatório.":::

6. Na caixa de diálogo **Criar ficheiro**, no **Caminho da Pasta**, selecione a pasta para onde quer exportar o relatório paginado.
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="Selecionar a pasta para onde quer exportar o relatório paginado":::

7. O Power Automate gera automaticamente um **Nome de ficheiro** e o **Conteúdo do ficheiro**. Pode alterar o **Nome do ficheiro**, mas manter o valor de **Conteúdo de ficheiro** gerado dinamicamente.
8. Quando tiver terminado, selecione **Passo seguinte** ou **Guardar**. O Power Automate cria e avalia o fluxo.
9. Se o Power Automate encontrar erros, selecione **Editar fluxo** para os corrigir. Caso contrário, selecione a seta Para trás para ver os detalhes do fluxo e executar o novo fluxo.
10. Quando executa o fluxo, o Power Automate exporta um relatório paginado no formato especificado para a pasta selecionada no sistema de ficheiros.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="O Power Automate exporta um relatório paginado no formato especificado.":::

## <a name="next-steps"></a>Passos seguintes

- [Exportar relatórios paginados do Power BI com o Power Automate](service-automate-paginated-integration.md)
- [Introdução ao Power Automate](/power-automate/getting-started/)
- Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

