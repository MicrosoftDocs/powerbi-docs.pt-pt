---
title: "Painel Análise no serviço Power BI"
description: "Criar linhas de referência dinâmicas para visuais no serviço Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2017
ms.author: mihart
ms.openlocfilehash: 30fc0731f819f063aa04e856e8acc75a69f64a59
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="analytics-pane-in-power-bi-service"></a>Painel Análise no serviço Power BI
Com o painel **Análise** no **serviço Power BI**, pode adicionar *linhas de referência* dinâmicas a visualizações e dar foco a tendências ou informações importantes.

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> O painel **Análise** aparece apenas quando seleciona um visual na tela de relatório.
> 
> 

## <a name="using-the-analytics-pane"></a>Utilizar o painel Análise
Com o painel **Análise**, pode criar os seguintes tipos de linhas de referência dinâmica (nem todas as linhas estão disponíveis para todos os tipos de visuais):

* Linha constante do Eixo X
* Linha constante do Eixo Y
* Linha Mín
* Linha Máx
* Linha Média
* Linha Mediana
* Linha de Percentil

As seguintes secções mostram como pode utilizar o painel **Análise** e linhas de referência dinâmicas nas suas visualizações.

Para ver as linhas de referência dinâmicas disponíveis para um visual, siga estes passos:

1. Selecione ou crie um visual e, em seguida, selecione o ícone **Análise** ![](media/service-analytics-pane/power-bi-analytics-icon.png)no painel **Visualizações**.
2. Selecione a seta para baixo do tipo de linha que pretende criar para expandir as respetivas opções. Neste caso, vamos selecionar **Linha Média**.
   
   ![](media/service-analytics-pane/power-bi-add.png)
3. Para criar uma nova linha, selecione **+ Adicionar**. Depois, pode especificar um nome para a linha ao fazer duplo clique na caixa de texto e, em seguida, escrever o seu nome.
   
   Tem diversos tipos de opções para a sua linha, como selecionar a *cor*, *transparência*, *estilo* e *posição* (relativamente aos elementos de dados do visual) e se pretende incluir a etiqueta. Um aspeto importante: pode selecionar qual a **Medida** no visual na qual pretende que a sua linha se baseie ao selecionar o menu pendente **Medida**, o qual é automaticamente preenchido com elementos de dados do visual. Neste caso, vamos selecionar *Open store count* (Contagem de lojas abertas) como medida, dar-lhe a etiqueta de *Avg # Open Stores* (N.º Médio de Lojas Abertas) e personalizar algumas das restantes opções, conforme mostrado abaixo.
   
   ![](media/service-analytics-pane/power-bi-average-line.png)
4. Se pretender que apareça uma etiqueta de dados, ative o controlo de deslize **Etiqueta de dados**. Quando o fizer, receberá uma série de opções adicionais para a sua etiqueta de dados.
5. Repare no número apresentado junto ao item **Linha média** no painel **Análise**. Isto indica-lhe quantas linhas dinâmicas, e de que tipo, tem atualmente no seu visual. Se adicionarmos uma **Linha constante** como um objetivo de 9 para contagem de lojas, pode ver que o painel **Análise** demonstra que temos também uma linha de referência **Linha constante** aplicada a este visual.
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   
   Se o visual que selecionou não pode ter linhas de referência dinâmicas aplicadas (neste caso, um visual de **Mapa**), irá ver o seguinte quando selecionar o painel **Análise**.
   
   ![](media/service-analytics-pane/power-bi-no-lines.png)

Existem diversas informações interessantes que pode destacar ao criar linhas de referência dinâmicas com o painel **Análise**.

Estamos a planear mais funcionalidades e capacidades, incluindo expandir que visuais podem ter linhas de referência dinâmicas aplicadas, pelo que recomendamos que consulte esta secção com frequência para estar a par das novidades.

## <a name="limitations"></a>Limitações
A capacidade de utilizar linhas de referência dinâmicas baseia-se no tipo de visual utilizado. A lista seguinte mostra quais as linhas dinâmicas que estão atualmente disponíveis para cada visual:

Utilização integral de linhas dinâmicas disponível nos seguintes visuais:

* Gráfico de área
* Gráfico de linhas
* Gráfico de dispersão
* Gráfico de Colunas agrupadas
* Gráfico de barras agrupadas

Os seguintes visuais só podem utilizar uma *linha constante* no painel **Análise**:

* Áreas Empilhadas
* Barras Empilhadas
* Colunas Empilhadas
* Barras Empilhadas a 100%
* Colunas Empilhadas a 100%

Para os seguintes visuais, a única opção atualmente disponível é uma *linha de tendência*:

* Linhas Não Empilhadas
* Gráfico de Colunas agrupadas

Finalmente, os visuais não Cartesianos não podem atualmente aplicar linhas dinâmicas do painel **Análise**, nomeadamente:

* Matriz
* Gráfico circular
* Anel
* Tabela

## <a name="next-steps"></a>Próximos passos
[Painel Análise no Power BI Desktop](desktop-analytics-pane.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

