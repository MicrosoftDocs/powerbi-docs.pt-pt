---
title: Gráficos de funil
description: Gráficos de funil no Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: qKRZPBnaUXM
ms.custom: video-qKRZPBnaUXM
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/05/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 38b33ad06123b64dd049dbae6ee67d6452da806e
ms.sourcegitcommit: 8250187368d3de48663eb516a816ff701119b579
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96998375"
---
# <a name="create-and-use-funnel-charts"></a>Criar e utilizar gráficos de funil

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Um gráfico de funil ajuda-o a visualizar um processo linear com fases ligadas de forma sequencial. Por exemplo, um funil de vendas que controla os clientes por fases: Oportunidade Potencial \> Oportunidade Potencial Qualificada \> Potencial Interessado \> Contrato \> Fecho.  Num relance, a forma do funil transmite a integridade do processo que está a controlar.

Cada fase do funil representa um ponto percentual do total. Portanto, na maioria dos casos, um gráfico de funil tem a forma de um funil – com a primeiro fase, sendo a maior e cada fase subsequente menor do que a antecessor.  Um funil em forma de pêra também é útil - pode identificar um problema no processo.  Mas, em geral, a primeira fase, a fase de "entrada", é a maior.

![funil azul de exemplo](media/power-bi-visualization-funnel-charts/funnelplain.png)

> [!NOTE]
> Para partilhar o seu relatório com outro utilizador do Power BI, é necessário que ambos tenham licenças individuais do Power BI Pro ou que o relatório seja guardado numa capacidade Premium.    

## <a name="when-to-use-a-funnel-chart"></a>Quando usar um gráfico de funil
Os gráficos de funil são uma ótima opção:

* Quando os dados são sequenciais e movimentam-se em pelo menos 4 fases.
* Quando o número de "itens" na primeira for maior que o número na fase final.
* calcular o potencial (receita de vendas/negociações/etc.) por fases.
* calcular e controlar as taxas de conversão e retenção.
* revelar afunilamentos num processo linear.
* controlar o fluxo de trabalho do carrinho de compras.
* acompanhar o progresso e o sucesso das campanhas de publicidade/marketing.

## <a name="working-with-funnel-charts"></a>Trabalhando com gráficos de funil
Gráficos de funil:

* Podem ser ordenados.
* Vários suportes.
* Podem ser destacados e cruzados por outras visualizações na mesma página de relatório.
* Podem ser utilizados para destacar e cruzar outras visualizações na mesma página de relatório.
   > [!NOTE]
   > Veja este vídeo para ver o Will a criar um gráfico de funil através do exemplo Vendas e Marketing. Depois, siga os passos abaixo do vídeo para experimentar por si próprio, com o exemplo de PBIX de Análise de Oportunidade
   > 
   > 
## <a name="prerequisite"></a>Pré-requisito

Este tutorial utiliza o [ficheiro PBIX do Exemplo de Análise de Oportunidade](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix
).

1. Na secção superior esquerda da barra de menus, selecione **Ficheiro** > **Abrir**
   
2. Procure a sua cópia do **ficheiro PBIX do Exemplo de Análise de Oportunidade**

1. Abra o **Ficheiro PBIX do Exemplo de Análise de Oportunidade** na vista de relatório ![Captura de ecrã a mostrar o ícone da vista de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de ecrã do separador amarelo.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.


## <a name="create-a-basic-funnel-chart"></a>Criar um gráfico de funil básico
Veja este vídeo para ver o Will a criar um gráfico de funil através do exemplo Vendas e Marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Agra crie o seu próprio gráfico de funil que mostra o número de oportunidades que temos em cada uma das nossas fases de vendas.

1. Comece numa página de relatório em branco e selecione o campo **SalesStage** \> **Sales Stage** (Fase de Venda).
   
    ![selecionar Fase de Vendas](media/power-bi-visualization-funnel-charts/funnelselectfield-new.png)

1. Selecione o ícone de funil ![ícone do gráfico de funil](media/power-bi-visualization-funnel-charts/power-bi-funnel-icon.png) para converter o gráfico de colunas num gráfico de funil.

2. No painel **Campos**, selecione **Facto** \> **Contagem de Oportunidades**.
   
    ![criação do gráfico de funil](media/power-bi-visualization-funnel-charts/power-bi-funnel-2.png)
4. Passar o rato por cima de uma barra mostra uma variedade de informações.
   
   * O nome da fase
   * Número de oportunidades no momento desta fase
   * Taxa de conversão geral (% do cliente potencial) 
   * Passo a passo (também conhecido como Taxa de Eliminação) que é % da fase anterior (nesse caso, Fase de Proposta/Fase de Solução)
     
     ![detalhes da barra de proposta](media/power-bi-visualization-funnel-charts/funnelhover-new.png)

6. [Guarde o relatório](../create-reports/service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Destaque e filtragem cruzada
Para obter informações sobre como utilizar o painel Filtros, veja [Adicionar um filtro a um relatório](../create-reports/power-bi-report-add-filter.md).

Realçar uma barra em um funil cruza os filtros de outras visualizações na página do relatório e vice-versa. Para acompanhar, adicione mais alguns elementos visuais à página do relatório que contém o gráfico de funil.

1. No funil, selecione a barra **Proposta**. Isso destaca de forma cruzada as outras visualizações na página. Utilize CTRL para selecionar vários.
   
   ![pequeno vídeo que mostra as interações visuais](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. Para definir preferências de como os elementos visuais são destacados e filtrados de forma cruzada entre si, veja [Interações visuais no Power BI](../create-reports/service-reports-visual-interactions.md)

## <a name="next-steps"></a>Próximos passos

[Medidores no Power BI](power-bi-visualization-radial-gauge-charts.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)



