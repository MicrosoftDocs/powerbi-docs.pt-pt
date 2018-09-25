---
title: Alterar a forma como os elementos visuais interagem num relatório
description: Documentação sobre como definir interações visuais num relatório de serviço do Microsoft Power BI e num relatório do Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: N_xYsCbyHPw
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: a70d5ac5265f88a6e407815ecb0fb6ac23e24416
ms.sourcegitcommit: 70192daf070ede3382ac13f6001e0c8b5fb8d934
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46565435"
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interações de visualização num relatório do Power BI
Se tiver permissões de edição para um relatório, pode utilizar as **interações visuais** para alterar a forma como as visualizações têm impacto umas nas outras numa página de relatório. 

Por predefinição, as visualizações numa página de relatório podem ser utilizadas para filtro cruzado e realce cruzado de outras visualizações na página.
Por exemplo, selecionar um estado numa visualização de mapa realça o gráfico de colunas e filtra o gráfico de linhas para mostrar apenas os dados que se aplicam a um estado.
Consulte [Sobre filtragem e realce](../power-bi-reports-filters-and-highlighting.md). Se tiver uma visualização que suporte a [exploração](end-user-drill.md) por predefinição, a exploração de uma visualização não tem impacto nas outras visualizações na página de relatório. No entanto, estes comportamentos predefinidos podem ser substituídos e as interações podem ser definidas individualmente para cada visualização.

Este artigo mostra-lhe como utilizar as **Interações visuais** na [Vista de edição](../service-interact-with-a-report-in-editing-view.md) do serviço Power BI e no Power BI Desktop. Se um relatório foi partilhado consigo, não conseguirá alterar as definições das Interações visuais.

> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são utilizados para distinguir o comportamento descrito aqui do que acontece quando utiliza o painel **Filtros** para filtrar e realçar visualizações.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Selecione a visualização para ativá-la.  
2. Aceda às opções das **Interações Visuais**.
    - No serviço Power BI, selecione o menu pendente na barra de menus do relatório.

       ![Menu pendente Interações visuais](./media/end-user-interactions/power-bi-visual-interaction.png)

    - No Desktop, selecione **Formato > Interações**.

        ![selecionar Formato e, em seguida, Interações](./media/end-user-interactions/pbi-visual-interaction-desktop.png)

3. Para ativar os controlos de interação de visualizações, selecione **Editar interações**. O Power BI adiciona ícones de filtragem cruzada e de realce cruzado a todas as outras visualizações na página de relatório.
   
    ![relatório com a opção Interações visuais ativada](./media/end-user-interactions/power-bi-icons-on.png)
3. Determine o impacto que a visualização selecionada deve ter nas outras visualizações.  Opcionalmente, repita para todas as outras visualizações na página do relatório.
   
   * Se quiser executar o filtro cruzado na visualização, selecione o ícone de **filtragem** ![ícone de filtragem](./media/end-user-interactions/pbi-filter-icon-outlined.png).
   * Se quiser executar o realce cruzado na visualização, selecione o ícone de **realce** ![ícone de realce](./media/end-user-interactions/pbi-highlight-icon-outlined.png).
   * Se não quiser que tenha impacto, selecione o **ícone** sem impacto ![ícone sem impacto](./media/end-user-interactions/pbi-noimpact-icon-outlined.png).

4. Para ativar os controlos de exploração, selecione **A exploração filtra outros elementos visuais**.  Agora, quando agregar ou desagregar numa visualização, as outras visualizações na página de relatório são alteradas para refletir a seleção de exploração atual. 

   ![vídeo sobre a ativação dos controlos de exploração](./media/end-user-interactions/drill2.gif)

### <a name="next-steps"></a>Próximos passos
[Como utilizar filtros de relatório](end-user-report-filter.md)

[Filtros e realce em relatórios](../power-bi-reports-filters-and-highlighting.md)

[Power BI - Conceitos Básicos](end-user-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

