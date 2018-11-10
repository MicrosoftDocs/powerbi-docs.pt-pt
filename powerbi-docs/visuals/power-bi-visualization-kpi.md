---
title: Elementos visuais do KPI
description: Criar elementos visuais do KPI no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: aec8bc2d7faa8d3c4b9c7b4eb69ed9a930cfbcd1
ms.sourcegitcommit: ce8332a71d4d205a1f005b703da4a390d79c98b6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/27/2018
ms.locfileid: "47417240"
---
# <a name="kpi-visuals"></a>Elementos visuais do KPI
Um KPI (Indicador Chave de Desempenho) é uma indicação visual que comunica a quantidade de progresso feito em relação a uma meta mensurável. Para obter mais informações sobre KPIs, consulte [Microsoft Developer Network](https://msdn.microsoft.com/library/hh272050).

Se não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos
* [O Power BI Desktop é gratuito!](https://powerbi.microsoft.com/en-us/get-started/)
* [O ficheiro PBIX de exemplo de Retail Analysis (Análise de Revenda)](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="when-to-use-a-kpi"></a>Quando usar um KPI
Os KPIs são uma ótima opção:

* para medir o progresso (em que estou adiantado ou atrasado?)
* para medir a distância de um objetivo (quão adiantado ou atrasado estou?)   

## <a name="kpi-requirements"></a>Requisitos do KPI
Um KPI baseia-se numa medida específica e é projetado para ajudá-lo a avaliar o estado e o valor atual de uma métrica em relação a um objetivo definido. Por conseguinte, um elemento visual de KPI requer uma medida *base* que é avaliada como um valor e um valor ou uma medida de *destino* e um *limiar* ou *objetivo*.

Atualmente, um conjunto de dados de KPI deve conter valores de objetivo para um KPI. Se o seu conjunto de dados não contiver um valor, pode criar objetivos adicionando uma folha do Excel com objetivos ao seu modelo de dados ou ficheiro PBIX.


## <a name="how-to-create-a-kpi"></a>Como criar um KPI
Para acompanhar, abra o [ficheiro .PBIX de Retail Analysis](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) (Análise de Revenda) no Power BI Desktop. Vamos criar um KPI que mede o progresso realizado para atingir um objetivo de vendas.

Ou deixe que o Will lhe mostre como criar elementos visuais de métrica única: medidores, cartões e KPIs.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Abra o relatório na vista Relatório e [selecione o separador amarelo para adicionar uma nova página](../power-bi-report-add-page.md).    
2. No painel Campos, selecione **Sales > Total Units This Year** (Vendas > Total de Unidades deste Ano).  Este será o indicador.
3. Adicione **Time > FiscalMonth** (Tempo > MêsFiscal).  Isto representará a tendência.
4. IMPORTANTE: ordene o gráfico por **FiscalMonth** (MêsFiscal). Depois de converter a visualização para um KPI, já não tem a opção de ordenar.

    ![](media/power-bi-visualization-kpi/power-bi-chart.png)
5. Converta o visual para um KPI selecionando o ícone do KPI do painel de Visualização.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-template.png)
6. Adicione uma meta. Adicione as vendas do último ano como o objetivo. Arraste **Total de Unidades do Último Ano** para o campo **Objetivos-alvo**.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-done.png)
7. Opcionalmente, formate o KPI selecionando o ícone do rolo de tinta para abrir o painel de Formatação.
   
   * **Indicador**: controla as unidades de apresentação do indicador e casas decimais.
   * **Eixo da tendência**: quando definido como **Ativado**, o eixo de tendência é apresentado como plano de fundo do visual do KPI.  
   * **Metas**: quando definido como **Ativado**, o elemento visual apresenta o objetivo e a distância do objetivo como uma percentagem.
   * **Codificação de cores > Direção**: alguns KPIs são considerados *melhores* para valores mais altos e alguns são considerados *melhores* para valores mais baixos. Por exemplo, ganhos vs. tempo de espera. Normalmente, um valor mais alto de ganhos é melhor em comparação com um valor mais alto de tempo de espera. Selecione **alto é melhor** e, opcionalmente, altere as definições de cor.


Os KPIs também estão disponíveis no serviço Power BI e nos dispositivos móveis, mantendo-o sempre ligado ao heartbeat do seu negócio.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Se o seu KPI não se parecer com o acima, poderá ser porque tem de ordenar por mêsfiscal. Uma vez que os KPIs não têm uma opção de ordenação, terá de os ordenar por mêsfiscal *antes* de converter a visualização num KPI.

## <a name="next-steps"></a>Passos seguintes

[Mapas básicos no Power BI](power-bi-map-tips-and-tricks.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)