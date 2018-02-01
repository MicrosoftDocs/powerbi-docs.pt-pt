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
ms.date: 12/21/2017
ms.author: mihart
ms.openlocfilehash: 3750d733967301f952fd092d2d1d0a2b9d1b2238
ms.sourcegitcommit: 6ea8291cbfcb7847a8d7bc4e2b6abce7eddcd0ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/21/2017
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


Para ver as linhas de referência dinâmicas disponíveis para um visual, siga estes passos:

1. Selecione ou crie um visual e, em seguida, selecione o ícone **Análise** ![](media/service-analytics-pane/power-bi-analytics-icon.png)no painel **Visualizações**.

2. Selecione a seta para baixo do tipo de linha que pretende criar para expandir as respetivas opções. Neste caso, vamos selecionar **Linha Média**.
   
   ![adicionar a linha média](media/service-analytics-pane/power-bi-add.png)

3. Para criar uma nova linha, selecione **+ Adicionar** e decida qual a medida que será utilizada para criar a linha.  A lista pendente **Medida** é automaticamente preenchida com os dados disponíveis da visualização selecionada. Vamos utilizar **Contagem de arquivos abertos**.

5. Tem diversos tipos de opções para a linha, como a cor, a transparência, o estilo e a posição (relativamente aos elementos de dados do elemento visual). Se quiser uma etiqueta na linha, atribua-lhe um título e, em seguida, mova o controlo de deslize **Etiqueta de dados** para **Ativo**.  Neste caso, vamos atribuir-lhe a etiqueta *N.º Médio de Arquivos Abertos* e personalizar algumas das outras opções, conforme mostrado abaixo.
   
   ![personalizar a Análise da média de linhas](media/service-analytics-pane/power-bi-average-line2.png)

1. Repare no número apresentado junto ao item **Linha média** no painel **Análise**. Isto indica-lhe quantas linhas dinâmicas, e de que tipo, tem atualmente no seu visual. Se adicionarmos uma **Linha constante** como um objetivo de 9 para contagem de lojas, pode ver que o painel **Análise** demonstra que temos também uma linha de referência **Linha constante** aplicada a este visual.
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   

Existem diversas informações interessantes que pode destacar ao criar linhas de referência dinâmicas com o painel **Análise**.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

Se o visual que selecionou não pode ter linhas de referência dinâmicas aplicadas (neste caso, um visual de **Mapa**), irá ver o seguinte quando selecionar o painel **Análise**.
   
![a análise não está disponível](media/service-analytics-pane/power-bi-no-lines.png)

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
