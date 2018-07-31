---
title: Gráfico de Área básico
description: Gráfico de área básico.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/27/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 09322a1ead6ae4c3a00dc42e2b4a642dcc2d6181
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2018
ms.locfileid: "34584145"
---
# <a name="basic-area-chart"></a>Gráfico de Área básico
O gráfico de área básico (também conhecido como gráfico de área em camadas) baseia-se no gráfico de linhas. A área entre o eixo e a linha é preenchida com cores para indicar o volume. 

Os gráficos de área realçam a magnitude da alteração ao longo do tempo e podem ser utilizados para chamar a atenção para o valor total numa tendência. Por exemplo, os dados que representam o lucro ao longo do tempo podem ser representados num gráfico de área para realçar o lucro total.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>Quando utilizar um gráfico de área básico
Os gráficos de área básicos são uma ótima opção:

* para ver e comparar as tendências de volume em série de tempo 
* para as séries individuais que representam um conjunto contável fisicamente

### <a name="prerequisites"></a>Pré-requisitos
 - Serviço Power BI
 - Exemplo de Análise de Revenda

Para acompanhar, inicie sessão no Power BI e selecione **Obter Dados\> Exemplos \> Exemplo de Análise de Revenda > Ligar** e escolha **Ir para o dashboard**. 

## <a name="create-a-basic-area-chart"></a>Criar um gráfico de área básico
 

1. No dashboard "Exemplo de Análise de Revenda", selecione o mosaico **Total de Lojas** para abrir o relatório "Exemplo de Análise de Revenda".
2. Selecione **Editar Relatório** para abrir o relatório na Vista de Edição.
3. Adicione uma nova página de relatório ao selecionar o ícone de mais amarelo (+) na parte inferior do relatório.
4. Crie um novo gráfico de área que mostre as vendas deste ano e do ano passado por mês.
   
   a. No painel CAMPOS, selecione **Vendas \> Vendas do Ano Passado** e **Vendas Deste Ano > Valor**.

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Converta o gráfico para um gráfico de área básico ao selecionar o ícone de gráfico de Área no painel VISUALIZAÇÕES.

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Selecione **Hora \> Mês** para adicioná-lo à área **Eixo**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Para mostrar o gráfico por mês, selecione as reticências (canto superior direito do visual) e selecione **Ordenar por mês**.

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como utilizar o painel FILTROS, veja [Adicionar um filtro a um relatório](power-bi-report-add-filter.md).

Para realçar uma área específica no gráfico, selecione essa área ou o respetivo limite superior.  Ao contrário de outros tipos de visualização, se existirem outras visualizações na mesma página, realçar um gráfico de área básico não realiza a filtragem cruzada de outras visualizações na página do relatório. No entanto, os gráficos de área são um alvo de filtragem cruzada acionado por outras visualizações na página do relatório. Para obter mais informações, veja [Interações visuais nos relatórios](service-reports-visual-interactions.md)


## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas   
* [Tornar o relatório mais acessível para pessoas portadoras de deficiência](desktop-accessibility.md)
* Os gráficos de área básicos não são eficazes para comparar os valores devido à oclusão nas áreas em camadas. O Power BI utiliza transparência para indicar a sobreposição das áreas. No entanto, só funciona corretamente com duas ou três áreas diferentes. Quando precisar comparar tendências para mais de três medidas, tente usar os gráficos de linhas. Quando precisar de comparar volume para mais de três medidas, tente usar os gráficos de linhas.

## <a name="next-steps"></a>Passos seguintes
[Relatórios no Power BI](service-reports.md)  
[Visualizações em relatórios do Power BI](power-bi-report-visualizations.md)  
[Power BI - Conceitos Básicos](service-basic-concepts.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

