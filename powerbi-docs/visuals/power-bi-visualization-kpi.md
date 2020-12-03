---
title: Elementos visuais do Indicador Chave de Desempenho (KPI)
description: Criar elementos visuais do Indicador Chave de Desempenho (KPI) no Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 01/30/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 448115ea6cde6c85a7bd3386890f483d71882ad5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418931"
---
# <a name="create-key-performance-indicator-kpi-visualizations"></a>Criar visualizações do indicador chave de desempenho (KPI)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Um KPI (Indicador Chave de Desempenho) é uma indicação visual que comunica a quantidade de progresso feito em relação a uma meta mensurável. Para obter mais informações sobre os KPIs, veja [Key Performance Indicators (KPIs) in PowerPivot](https://support.office.com/en-us/article/Key-Performance-Indicators-KPIs-in-Power-Pivot-E653EDEF-8A21-40E4-9ECE-83A6C8C306AA) (Indicadores Chave de Desempenho (KPIs) no PowerPivot).


## <a name="when-to-use-a-kpi"></a>Quando usar um KPI

Os KPIs são uma ótima opção:

* Para avaliar o progresso. Responde à pergunta: “Em que estou adiantado ou atrasado?”

* Para avaliar a distância até um objetivo. Responde à pergunta: “Quão adiantado ou atrasado estou?”

## <a name="kpi-requirements"></a>Requisitos do KPI

Um designer baseia um elemento visual do KPI numa medida específica. A intenção do KPI é ajudar a avaliar o valor atual e o estado de uma métrica em relação a um objetivo definido. Um elemento visual do KPI requer uma medida *base*, que é avaliada como um valor, um valor ou uma medida de *destino* e um *limiar* ou *objetivo*.

Um conjunto de dados de KPI deve conter valores de objetivo para um KPI. Se o conjunto de dados não contiver valores de objetivo, poderá criá-los. Para tal, adicione uma folha do Excel com os objetivos ao seu modelo de dados ou ficheiro PBIX.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial utiliza o [ficheiro PBIX do Exemplo de Análise de Revenda](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Na secção superior esquerda da barra de menus, selecione **Ficheiro** > **Abrir**.

1. Procure a sua cópia do **ficheiro PBIX do Exemplo de Análise de Revenda**

1. Abra o **ficheiro PBIX do Exemplo de Análise de Revenda** na vista de relatório. ![Captura de ecrã do ícone de vista de relatório.](media/power-bi-visualization-kpi/power-bi-report-view.png)

1. Selecione **+** para adicionar uma nova página. ![Captura de ecrã do separador amarelo.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png)

> [!NOTE]
> Para partilhar o seu relatório com outro utilizador do Power BI, é necessário que ambos tenham licenças individuais do Power BI Pro ou que o relatório seja guardado numa capacidade Premium.    

## <a name="how-to-create-a-kpi"></a>Como criar um KPI

Neste exemplo, irá criar um KPI que avalia o progresso realizado para atingir um objetivo de vendas.

1. No painel **Campos**, selecione **Vendas > Total de Unidades deste Ano**.  Este valor será o indicador.

1. Adicione **Time > FiscalMonth** (Tempo > MêsFiscal).  Este valor representará a tendência.

1. No canto superior direito do elemento visual, selecione as reticências e verifique se o Power BI ordenou as colunas por ordem ascendente por **MêsFiscal**.

    > [!IMPORTANT]
    > Depois de converter a visualização num KPI, **deixará** de ter a opção de ordenar. Tem de o ordenar corretamente agora.

    ![Captura de ecrã do menu de reticências expandido com Ordenação ascendente e MêsFiscal selecionados.](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    Depois de ordenado corretamente, o elemento visual terá o seguinte aspeto:

    ![Captura de ecrã do elemento visual ordenado corretamente.](media/power-bi-visualization-kpi/power-bi-chart.png)

1. Converta o elemento visual para um KPI ao selecionar o ícone **KPI** no painel **Visualização**.

    ![Captura de ecrã do painel Visualizações com o ícone KPI destacado.](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. Para adicionar um objetivo, arraste **Total de Unidades do Último Ano** para o campo **Objetivos-alvo**.

    ![Captura de ecrã do elemento visual do KPI concluído e o painel Campos com os valores apresentados.](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. Opcionalmente, formate o KPI selecionando o ícone do rolo de tinta para abrir o painel de Formatação.

    * **Indicador**: controla as unidades de apresentação do indicador e casas decimais.

    * **Eixo de tendência**: quando definido como **Ativado**, o elemento visual mostra o eixo de tendência como o fundo do elemento visual do KPI.  

    * **Objetivos**: quando definido como **Ativado**, o elemento visual mostra o objetivo e a distância do objetivo como uma percentagem.

    * **Codificação de cores > Direção**: as pessoas consideram alguns KPIs melhores para valores *mais altos* e consideram outros para valores *mais baixos*. Por exemplo, ganhos vs. tempo de espera. Normalmente, um valor mais alto de ganhos é melhor em comparação com um valor mais alto de tempo de espera. Selecione **alto é melhor** e, opcionalmente, altere as definições de cor.

Os KPIs também estão disponíveis no serviço Power BI e nos dispositivos móveis. Estes oferecem a opção de estar sempre ligado ao heartbeat do seu negócio.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

Se o KPI não se parecer com o apresentado acima, poderá ser porque não ordenou por **MêsFiscal**. Os KPIs não têm uma opção de ordenação. Terá de iniciar novamente e ordenar por **MêsFiscal** *antes* de converter a visualização num KPI.

## <a name="next-steps"></a>Próximos passos

* [Sugestões e Truques para visualizações de Mapas do Power BI](power-bi-map-tips-and-tricks.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
