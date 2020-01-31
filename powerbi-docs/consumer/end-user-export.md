---
title: Exportar dados de um visual do Power BI
description: Exporte dados de um elemento visual de relatório e de um elemento visual de dashboard e veja-os no Excel.
author: mihart
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 27128618fc594a8b7259a3de3862c6766eaecd86
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76537523"
---
# <a name="export-data-from-a-visual"></a>Exportar dados de um visual

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Se quiser ver os dados que são utilizados para criar um elemento visual, [poderá apresentar os dados no Power BI](end-user-show-data.md) ou exportar esses dados para o Excel. A opção para exportar os dados requer um certo tipo de licença ou permissões de edição para o conteúdo. Se não conseguir exportar, contacte o administrador do Power BI. 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>A partir de um elemento visual num dashboard do Power BI

1. Comece num dashboard do Power BI. Aqui estamos a utilizar o dashboard da aplicação de ***exemplo Marketing e vendas***. Pode [transferir esta aplicação em AppSource.com](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282).

    ![Dashboard da aplicação](media/end-user-export/power-bi-dashboards.png)

2. Paire o cursor sobre um elemento visual para ver **Mais opções** (...) e clique para apresentar o menu de ação.

    ![Menu que aparece quando seleciona as reticências](media/end-user-export/power-bi-options-menu.png)

3. Selecione **Exportar para .csv**.

4. O que acontece a seguir depende do browser que estiver a utilizar. Poderá ser-lhe solicitado que guarde o ficheiro ou pode ver uma ligação para o ficheiro exportado na parte inferior do browser. 

    ![O Chrome a mostrar a ligação do ficheiro exportado](media/end-user-export/power-bi-dashboard-exports.png)

5. Abra o ficheiro no Excel. 

    > [!NOTE]
    > Se não tiver permissões para os dados, não poderá exportar ou abrir no Excel.  

    ![Total de Unidades Ano Até à Data no Excel](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>A partir de um elemento visual num relatório
Pode exportar dados de um elemento visual num um relatório com o formato .csv ou .xlsx (Excel). 

1. Num dashboard, selecione um mosaico para abrir o relatório subjacente.  Neste exemplo, estamos a selecionar o mesmo elemento visual de acima, *Total de Unidades Ano Até à Data % Var*. 

    ![Mosaico do dashboard realçado](media/end-user-export/power-bi-export-reports.png)

    Dado que este mosaico foi criado no relatório *Exemplo de Vendas e Marketing*, é este relatório que é aberto. O relatório é aberto na página que contém o elemento visual do mosaico selecionado. 

2. Selecione o elemento visual no relatório. Repare no painel **Filtros** à direita. Este elemento visual tem filtros aplicados. Para saber mais sobre os filtros, veja [Utilizar filtros num relatório](end-user-report-filter.md).

    ![Painel Filtro selecionado](media/end-user-export/power-bi-export-filter.png)


3. Selecione **Mais opções (...)** no canto superior direito da visualização. Escolha **Exportar dados**.

    ![Exportar dados selecionados na lista pendente](media/end-user-export/power-bi-export-report.png)

4. Verá as opções para exportar Dados resumidos ou Dados subjacentes. Se estiver a utilizar a aplicação *Exemplo de Vendas e marketing*, os **Dados subjacentes** estarão desativados. Mas pode encontrar relatórios onde ambas as opções estejam ativadas. Eis uma explicação da diferença.

    **Dados resumidos**: selecione esta opção se quiser exportar dados do que vê atualmente no elemento visual.  Este tipo de exportação mostra-lhe apenas os dados que foram utilizados para criar o estado atual do elemento visual. Se o elemento visual tiver filtros aplicados, os dados exportados também serão filtrados. Por exemplo, para este elemento visual, a sua exportação incluirá apenas os dados para 2014 e para a região central, e apenas os dados para quatro dos fabricantes: VanArsdel, Natura, Aliqui e Pirum. Se o seu elemento visual tiver agregações (soma, média, entre outros), a exportação também será agregada. 
  

    **Dados subjacentes**: selecione esta opção se desejar exportar dados para o que vê no elemento visual **além** de dados adicionais do conjunto de dados subjacente.  Tal pode incluir dados contidos no conjunto de dados, mas não utilizados no elemento visual. Se o elemento visual tiver filtros aplicados, os dados exportados também serão filtrados.  Se o seu elemento visual tiver agregações (soma, média, entre outros), a exportação irá remover a agregação, simplificando os dados. 

    ![Menu no qual escolhe os dados subjacentes ou resumidos](media/end-user-export/power-bi-export-underlying.png)

5. O que acontece a seguir depende do browser que estiver a utilizar. Poderá ser-lhe solicitado que guarde o ficheiro ou pode ver uma ligação para o ficheiro exportado na parte inferior do browser. 

    ![Ficheiro exportado apresentado no Microsoft Edge](media/end-user-export/power-bi-export-edge-browser.png)

    > [!NOTE]
    > Se não tiver permissões para os dados, não poderá exportar ou abrir no Excel.  


6. Abra o ficheiro no Excel. Compare a quantidade de dados exportados com os dados que exportámos a partir do mesmo elemento visual no dashboard. A diferença é que esta exportação inclui **Dados subjacentes**. 

    ![Exemplo de Excel](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>Próximos passos

[Apresentar os dados utilizados para criar um elemento visual](end-user-show-data.md)