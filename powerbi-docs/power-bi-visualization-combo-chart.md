---
title: "Gráfico de Combinação no Power BI (Tutorial)"
description: "Esta documentação é um tutorial (com vídeo) que lhe mostra por quê e como criar um Gráfico de Combinação no Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: lnv66cTZ5ho
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: c00ba74501a411743036c4514750bccbbae3eb00
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="combo-chart-in-power--tutorial"></a>Gráfico de Combinação no Power BI (Tutorial)
No Power BI, um gráfico de combinação é uma visualização única que combina um gráfico de linhas e um gráfico de colunas. Combinar os 2 gráficos em um, permite-lhe fazer uma comparação rápida dos dados.

Os gráficos de combinação podem ter um ou dois eixos Y.

## <a name="when-to-use-a-combo-chart"></a>Quando utilizar um Gráfico de Combinação
Os gráficos de combinação são uma ótima opção:

* quando tem um gráfico de linhas e um gráfico de colunas com o mesmo eixo X.
* para comparar várias medidas com intervalos de valores diferentes.
* para ilustrar a correlação entre duas medidas numa visualização.
* para verificar se uma medida atende o destino definido pela outra medida
* para conservar o espaço da tela.

## <a name="create-a-basic-single-axis-combo-chart"></a>Criar um Gráfico de Combinação básico de eixo único
Veja o Will a criar um gráfico de combinação através do exemplo Vendas e Marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Para criar o seu próprio gráfico de combinação, inicie sessão no Power BI e selecione **Obter Dados \> Exemplos \> Exemplo de Análise de Revenda**. 

1. No dashboard "Exemplo de Análise de Retalho", selecione o mosaico **Armazenamentos Totais** para abrir o relatório "Exemplo de Análise de Retalho".
2. Selecione **Editar Relatório** para abrir o relatório no modo de Vista de Edição.
3. [Adicione uma nova página do relatório](power-bi-report-add-page.md).
4. Crie um gráfico de coluna que apresenta as vendas deste ano e a margem bruta por mês.
   
    a.  No painel Campos, selecione **Vendas** \> **Vendas do Último Ano** > **Valor**.
   
    b.  Arraste **Vendas** \> **Margem Bruta Deste Ano** para o painel **Valor**.
   
    c.  Selecione **Hora** \> **MêsFiscal** para adicionar este campo ao painel **Eixo**. 
   
    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Selecione as reticências (…) no canto superior direito da visualização e selecione **Ordenar por MêsFiscal**.
6. Converta o gráfico de colunas num gráfico de combinação. Com o gráfico de colunas selecionado, no painel **Visualizações**, selecione **Gráfico de linhas e de colunas agrupadas**.
   
    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. No painel **Campos**, arraste **Vendas** \> **Vendas do Ano Passado** até ao registo **Valores de Linha**.
   
   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)
   
   O gráfico de combinação deve ter esta aparência:
   
   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Criar um gráfico de combinação com dois eixos
Nesta tarefa, vamos comparar as vendas e a margem bruta.

1. Crie um novo gráfico de linhas que acompanha a % de Margem Bruta do ano passado por Mês.  Em janeiro, a % de Margem Bruta foi de 35%, alcançou o seu máximo de 45% em abril, caiu em julho e regressou ao máximo novamente em agosto. Será que vamos ver um padrão semelhante nas vendas do ano passado e deste ano?
   
   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Adicione **Vendas Deste Ano > Valor** e **Vendas do Ano Passado** ao gráfico de linhas. A escala de **% de Margem Bruta do Ano Passado** é muito inferior à escala de **Vendas**, o que dificulta a comparação.      
   
   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Para tornar o elemento visual mais fácil de ler e interpretar, converta o gráfico de linhas num Gráfico de Linhas e Coluna Empilhada.
   
   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Arraste a **% de Margem Bruta do Ano Passado** dos **Valores da Coluna** para os **Valores da Linha**. O Power BI cria dois eixos, o que permite que os conjuntos de dados sejam escalados de modo diferente: o eixo à esquerda calcula dólares e o eixo à direita calcula a percentagem.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-combochart.png)    

## <a name="add-titles-to-the-axes"></a>Adicionar títulos aos eixos
1. Selecione o ícone de rolo de tinta ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) para abrir o painel Formatar.
2. Selecione a seta para baixo para expandir as opções do **eixo Y** .
3. Para **Eixo Y (Coluna)**, defina **Posição** como **Esquerda**, **Título** como **Ativado**, **Estilo** como **Mostrar apenas título** e **Apresentar** como **Milhões**.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-y-axis-column.png)
4. Em **Eixo Y (Coluna)**, certifique-se de que **Mostrar Secundário** também está definido como **Ativado**. Esta ação apresenta as opções de formatação da parte do gráfico de linhas do gráfico de combinação.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-show-secondary.png)
5. Para **Eixo Y (Linha)**, deixe **Posição** como **Direita**, **Título** como **Ativado** e defina **Estilo** como **Mostrar apenas título**.
   
   O gráfico de combinação apresenta agora eixos duplos, ambos com títulos.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

Aqui poderá:

* [Adicionar o gráfico de combinação como um mosaico do dashboard](service-dashboard-tiles.md).
* [Guarde o relatório](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Destaque e filtragem cruzada
Para obter informações sobre como utilizar o painel Filtros, veja [Add a filter to a report (Adicionar um filtro a um relatório)](power-bi-report-add-filter.md).

Realçar uma coluna ou linha num gráfico de combinação filtra as outras visualizações na página de relatório e vice-versa.

## <a name="next-steps"></a>Próximos passos
[Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)

[Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

[Experimente – é gratuito!](https://powerbi.com/)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

