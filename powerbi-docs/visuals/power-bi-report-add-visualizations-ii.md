---
title: Parte 2, Adicionar visualizações a um relatório do Power BI
description: Parte 2, Adicionar visualizações a um relatório do Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/06/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 6ddee012d01c64e0f35ac491d2b20ba362f2da90
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412466"
---
# <a name="add-visuals-to-a-power-bi-report-part-2"></a>Adicionar elementos visuais a um relatório do Power BI (parte 2)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Na [Parte 1](power-bi-report-add-visualizations-i.md), criou uma visualização básica marcando as caixas de seleção ao lado dos nomes de campo.  Na Parte 2, aprenderá a utilizar a funcionalidade de arrastar e largar e a utilizar de forma integral os painéis **Campos** e **Visualizações** para criar e modificar as visualizações.


## <a name="create-a-new-visualization"></a>Criar uma nova visualização
Neste tutorial, vamos examinar o nosso conjunto de dados de Análise de Revenda e criar algumas visualizações chave.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial utiliza o [ficheiro PBIX de Exemplo de análise de revenda](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Na secção superior esquerda da barra de menus do Power BI Desktop, selecione **Ficheiro** > **Abrir**
   
2. Procure a sua cópia do **ficheiro PBIX do Exemplo de Análise de Revenda**

1. Abra o **Ficheiro PBIX do Exemplo de Análise de Revenda** na vista de relatório ![Captura de ecrã a mostrar o ícone da vista de relatório](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de ecrã do separador amarelo.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.

## <a name="add-visualizations-to-the-report"></a>Adicione visualizações ao relatório

Crie uma visualização selecionando um campo no painel **Campos**. O tipo de visualização criado dependerá do tipo de campo selecionado. O Power BI utiliza o tipo de dados para determinar qual a visualização a utilizar para mostrar os resultados. Pode alterar facilmente a visualização utilizada ao selecionar um ícone diferente no painel Visualizações. Tenha em conta que nem todas as visualizações podem mostrar os seus dados. Por exemplo, os dados geográficos não são devidamente mostrados num gráfico de funil ou gráfico de linhas. 


### <a name="add-an-area-chart-that-looks-at-this-years-sales-compared-to-last-year"></a>Adicionar um gráfico de área que analise as vendas deste ano em comparação com o ano passado

1. Na tabela **Vendas**, selecione **Vendas Deste Ano** > **Valor** e **Vendas do Ano Passado**. O Power BI cria um gráfico de colunas.  Este gráfico é interessante e quer investigar melhor. O que torna as vendas semelhantes por mês?  
   
   ![Captura de ecrã a mostrar um gráfico de colunas](media/power-bi-report-add-visualizations-ii/power-bi-start.png)

2. Na tabela Time (Hora), arraste **FiscalMonth** (MêsFiscal) para a área **Axis** (Eixo).  
   ![Captura de ecrã a mostrar um gráfico de colunas com FiscalMonth (Mês Fiscal) como eixo](media/power-bi-report-add-visualizations-ii/power-bi-fiscalmonth.png)

3. [Mude a visualização](power-bi-report-change-visualization-type.md) para um gráfico de área.  Há muitos tipos de visualização à escolha. Veja [descrições de cada uma, dicas de práticas recomendadas e tutoriais](power-bi-visualization-types-for-reports-and-q-and-a.md) para decidir que tipo utilizar. No painel Visualizações, selecione o ícone do gráfico de área ![ícone de gráfico de área do painel Visualizações](media/power-bi-report-add-visualizations-ii/power-bi-area-chart.png).

4. Ordene a visualização ao selecionar **Mais ações** (...) e selecionar **Ordenar por** >  **FiscalMonth** (Mês Fiscal).

5. [Redimensione a visualização](power-bi-visualization-move-and-resize.md)selecionando a visualização, pegando um dos círculos da estrutura de tópicos e arrastando. Torne-a grande o suficiente para eliminar a barra de deslocamento e pequena o suficiente para termos espaço para adicionar outra visualização.
   
   ![captura de ecrã do elemento visual do gráfico de área](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Guarde o relatório](../create-reports/service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Adicionar uma visualização de mapa que analise as vendas por local

1. Na tabela **Arquivo** selecione **Território**. Arraste **Arquivos Totais** na área de Valores. O Power BI reconhece que Território é um local e cria uma visualização de mapa.  
   ![Gráfico de área](media/power-bi-report-add-visualizations-ii/power-bi-map1.png)

2. Adicione uma legenda.  Para ver os dados pelo nome da loja, arraste **Store** (Loja) > **Chain** (Cadeia) para a área Legenda.  
   ![tela de relatórios com uma seta a apontar da Cadeia na lista de campos para a Cadeia no registo Legenda](media/power-bi-report-add-visualizations-ii/power-bi-chain.png)

> [!NOTE]
> Para partilhar o seu relatório com outro utilizador do Power BI, é necessário que ambos tenham licenças individuais do Power BI Pro ou que o relatório seja guardado numa capacidade Premium. Veja [partilhar relatórios](../collaborate-share/service-share-reports.md).

## <a name="next-steps"></a>Próximos passos
* Mais sobre [Visualizações nos relatórios do Power BI](power-bi-report-visualizations.md).  
* Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

