---
title: Gráficos de linhas no Power BI
description: Gráficos de linhas no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0654dccf55b1e13f26d8ecaabee0349f0e56afc6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65535796"
---
# <a name="line-charts-in-power-bi"></a>Gráficos de linhas no Power BI
Um gráfico de linhas é uma série de pontos de dados que são representados por pontos e ligados por linhas retas. Um gráfico de linhas pode ter uma ou várias linhas. Gráficos de linhas de ter um X e um eixo Y. 

![gráfico de linhas simples](media/power-bi-line-charts/power-bi-line.png)

## <a name="create-a-line-chart"></a>Criar um gráfico de linhas
Estas instruções de utilização de vendas e a aplicação de exemplo de Marketing para criar um gráfico de linhas que mostre as vendas deste ano por categoria. Para acompanhar, obtenha a aplicação de exemplo de appsource.com.

1. Comece numa página de relatório em branco. Se estiver a utilizar o serviço Power BI, garanta que abre o relatório na [Vista de edição](../service-interact-with-a-report-in-editing-view.md).

2. No painel campos, selecione **SalesFact** \> **Total de unidades**e selecione **data** > **mês**.  Power BI cria um gráfico de colunas na tela de relatórios.

    ![Selecione a partir do painel de campos](media/power-bi-line-charts/power-bi-step1.png)

4. Converta para um gráfico de linhas ao selecionar o modelo de gráfico de linha a partir do painel de visualizações. 

    ![converter em gráfico de linhas](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filtre o gráfico de linhas para mostrar dados nos anos 2014 de 2012. Se o painel filtros é fechada, expanda-o agora. No painel campos, selecione **data** \> **ano** e arraste-o para o painel filtros. Solte-o sob o cabeçalho **filtros neste elemento visual**. 
     
    ![linha junto ao painel de campos](media/power-bi-line-charts/power-bi-year-filter.png)

    Alteração **filtros avançados** ao **filtros básicos** e selecione **2012**, **2013** e **2014**.

    ![Filtro para o ano](media/power-bi-line-charts/power-bi-filter-year.png)

6. Opcionalmente, [ajuste o tamanho e a cor do texto do gráfico](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Aumentar o tamanho da fonte e altere Y axisfont](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Adicionar linhas adicionais ao gráfico
Gráficos de linhas podem ter muitas linhas diferentes. E, em alguns casos, os valores nas linhas podem ser tão divergentes que não forem apresentados bem em conjunto. Vamos dar uma olhada na adição de linhas adicionais para nosso atual do gráfico e, em seguida, saiba como formatar o nosso gráfico quando os valores representados pelas linhas são muito diferentes. 

### <a name="add-additional-lines"></a>Adicionar linhas adicionais
Em vez de olhar o total de unidades para todas as regiões como uma única linha no gráfico, vamos dividir o total de unidades por região. Adicionar linhas adicionais ao arrastar **Geo** > **região** para o bem de legenda.

   ![Uma linha para cada região](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Utilizar dois eixos Y
E se deseja examinar o total de vendas e total de unidades no mesmo gráfico? Números de vendas são muito superiores aos números de unidade, tornando o gráfico de linhas não utilizável. Na verdade, a linha vermelha para total de unidades é apresentado como zero.

   ![altamente diverging valores](media/power-bi-line-charts/power-bi-diverging.png)

Para exibir a valores divergentes altamente num gráfico, use um gráfico de combinação. Pode aprender tudo sobre os gráficos de combinação lendo [gráficos de combinação no Power BI](power-bi-visualization-combo-chart.md). No nosso exemplo a seguir, podemos exibir vendas e total de unidades em conjunto num gráfico, adicionando um segundo eixo Y. 

   ![altamente diverging valores](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Um gráfico de linhas não pode ter eixos duplos de Y.  Precisará usar um gráfico de combinação em vez disso.
* Nos exemplos acima, os gráficos foram formatados para aumentar o tamanho da fonte, alterar a cor da fonte, adicionar os títulos dos eixos, center o título do gráfico e uma legenda, iniciar ambos os eixos em zero e muito mais. O painel de formatação (ícone de rolo de pintura) tem um conjunto aparentemente interminável de opções para fazer a forma como pretende que a sua aparência de gráficos. A melhor forma de aprender é abrir o painel Formatting e explorar.

## <a name="next-steps"></a>Próximos passos

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


