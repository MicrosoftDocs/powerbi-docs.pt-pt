---
title: Gráfico de combinação no Power BI
description: Este tutorial sobre gráficos de combinação explica quando utilizá-los e como criá-los no serviço Power BI e no Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/23/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e4b7b4b336b376f6ccec0bc0fe56de107ab8bd09
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67124169"
---
# <a name="combo-chart-in-power-bi"></a>Gráfico de combinação no Power BI

No Power BI, um gráfico de combinação é uma visualização única que combina um gráfico de linhas e um gráfico de colunas. Combinar os dois gráficos em um, permite-lhe fazer uma comparação rápida dos dados.

Os gráficos de combinação podem ter um ou dois eixos Y.

## <a name="when-to-use-a-combo-chart"></a>Quando utilizar um gráfico de combinação

Os gráficos de combinação são uma ótima opção:

* Quando tem um gráfico de linhas e um gráfico de colunas com o mesmo eixo X.

* Para comparar várias medidas com intervalos de valores diferentes.

* Para ilustrar a correlação entre duas medidas numa visualização.

* Para verificar se uma medida está em conformidade com o alvo definido pela outra medida.

* Para conservar espaço da tela.

## <a name="prerequisites"></a>Pré-requisitos

Os Gráficos de combinação estão disponíveis no serviço Power BI e no Power BI Desktop. Este tutorial utiliza o serviço Power BI para criar um gráfico de combinação. Confirme que tem as credenciais de utilizador para iniciar sessão no Power BI.

Veja o Will a criar um gráfico de combinação através do exemplo Vendas e Marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

## <a name="create-a-basic-single-axis-combo-chart"></a>Criar um gráfico de combinação básico e de eixo único

Para acompanhar, abra o serviço Power BI e ligue ao **exemplo de Análise de Revenda**. Para criar o seu próprio gráfico de combinação, inicie sessão no serviço Power BI e selecione **Obter Dados** > **Exemplos** > **Exemplo de Análise de Revenda** > **Ligar**. O dashboard **Exemplo de Análise de Revenda** é apresentado.

1. No dashboard “Exemplo de Análise de Revenda”, selecione o mosaico **Total de Lojas** para abrir o relatório **Descrição Geral das Vendas de Lojas**.

1. Selecione **Editar Relatório** para abrir o relatório na Vista de Edição.

1. Na parte inferior da página, selecione **+** para adicionar uma nova página de relatório.

1. Crie um gráfico de colunas que apresente as vendas deste ano e a margem bruta por mês.

    1. No painel Campos, selecione **Vendas** \> **Vendas do Último Ano** > **Valor**.

    1. Arraste **Vendas** \> **Margem Bruta Deste Ano** para o painel **Valor**.

    1. Selecione **Hora** \> **MêsFiscal** para adicionar este campo ao painel **Eixo**.

        ![Captura de ecrã do gráfico de colunas recém-criado.](media/power-bi-visualization-combo-chart/combotutorial1new.png)

1. Selecione as reticências no canto superior direito da visualização e selecione **Ordenar por > MêsFiscal**. Para alterar a sequência de ordenação, selecione as reticências novamente e selecione **Ordenação ascendente** ou **Ordenação descendente**.

1. Converta o gráfico de colunas num gráfico de combinação. Estão disponíveis dois gráficos de combinação: **Coluna de linhas e empilhada** e **Coluna de linhas e em cluster**. Com o gráfico de colunas selecionado, no painel **Visualizações**, selecione **Gráfico de linhas e de colunas agrupadas**.

    ![Captura de ecrã do painel Visualizações, com a opção Gráfico de linhas e de colunas agrupadas destacada.](media/power-bi-visualization-combo-chart/converttocombo_new2.png)

1. No painel **Campos**, arraste **Vendas** > **Vendas do Ano Passado** para a caixa **Valores de Linha**.

    ![Captura de ecrã da caixa Valores de Linha com Vendas do Ano Passado na caixa.](media/power-bi-visualization-combo-chart/linevaluebucket.png)

    O gráfico de combinação deve ter esta aparência:

    ![Captura de ecrã do gráfico de colunas com o valor de linha de Vendas do Ano Passado adicionado.](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Criar um gráfico de combinação com dois eixos

Nesta tarefa, vamos comparar as vendas e a margem bruta.

1. Crie um novo gráfico de linhas que acompanha a **% da Margem Bruta do ano passado**  por **Mês**. Selecione as reticências para ordenar por **Mês** e **Ascendente**.

    ![Captura de ecrã do novo gráfico de linhas.](media/power-bi-visualization-combo-chart/combo1_new.png)

     Em janeiro, a percentagem de Margem Bruta foi de 35%, chegando ao máximo de 45% em abril, caindo em julho e chegando ao máximo novamente em agosto. Será que vamos ver um padrão semelhante nas vendas do ano passado e deste ano?

1. Adicione **Vendas Deste Ano** > **Valor** e **Vendas do Ano Passado** ao gráfico de linhas. A escala de **% de Margem Bruta do Ano Passado** é muito inferior à escala de **Vendas**. Desta forma, é difícil comparar.

    ![Captura de ecrã do gráfico de linhas com as opções Valor e Vendas do Ano Passado adicionadas.](media/power-bi-visualization-combo-chart/flatline_new.png)

1. Para tornar o elemento visual mais fácil de ler e interpretar, converta o gráfico de linhas num gráfico de Linhas e Colunas Empilhadas.

    ![Captura de ecrã do painel Visualizações com a opção Gráfico de linhas e colunas empilhadas destacada.](media/power-bi-visualization-combo-chart/converttocombo_new.png)

1. Arraste **% de Margem Bruta no Ano Passado** de **Valores de Coluna** para **Valores de Linha**. 

    ![Captura de ecrã do Gráfico de linhas e colunas empilhadas](media/power-bi-visualization-combo-chart/power-bi-combochart.png)

    O Power BI cria dois eixos que permitem que o serviço dimensione os conjuntos de dados de modo diferente. O esquerdo avalia os dólares de vendas e o direito avalia a percentagem. Além disso, podemos ver a resposta à nossa pergunta: Sim, vemos um padrão semelhante.

## <a name="add-titles-to-the-axes"></a>Adicionar títulos aos eixos

1. Selecione o ícone de rolo de pintura ![Captura de ecrã do ícone de rolo de pintura.](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) para abrir o painel Formatação.

1. Selecione a seta para baixo para expandir as opções do **eixo Y** .

1. Para **Eixo Y (Coluna)** , selecione estas opções:

    | Definições | Valor |
    | ------- | ----- |
    | Posição | Selecione **Esquerdo**. |
    | Mostrar unidades | Selecione **Milhões**. |
    | Título | Mova o controlo de deslize para **Ativado**. |
    | Estilo | Selecione **Mostrar apenas título**. |
    | Mostrar secundário | Mova o controlo de deslize para **Ativado**.  Esta ação mostra as opções de formatação da parte do gráfico de linhas do gráfico de combinação. |

1. Para **Eixo Y (Linha)** , selecione estas opções:

    | Definições | Valor |
    | ------- | ----- |
    | Posição | Selecione **Direito**. |
    | Título | Mova o controlo de deslize para **Ativado**. |
    | Estilo | Selecione **Mostrar apenas título**. |

    O gráfico de combinação apresenta agora eixos duplos, ambos com títulos.

    ![Captura de ecrã do Gráfico de linhas e colunas empilhadas com os títulos ativados.](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

1. Opcionalmente, altere o tipo de letra, o tamanho e a cor do texto e defina outras opções de formatação para melhorar o ecrã e a facilidade de leitura do gráfico.

Aqui poderá:

* [Adicionar o gráfico de combinação como um mosaico do dashboard](../service-dashboard-tiles.md).

* [Guarde o relatório](../service-report-save.md).

* [Tornar o relatório mais acessível para pessoas portadoras de deficiência](../desktop-accessibility.md).

## <a name="cross-highlighting-and-cross-filtering"></a>Destaque e filtragem cruzada

Realçar uma coluna ou linha num gráfico de combinação destaca e filtra de forma cruzada as outras visualizações na página de relatório. Para alterar este comportamento padrão, utilize as [interações visuais](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Próximos passos

[Gráficos em anel no Power BI](power-bi-visualization-doughnut-charts.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)