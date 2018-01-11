---
title: Treemaps no Power BI (Tutorial)
description: 'Tutorial: Treemaps no Power BI'
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: IkJda4O7oGs
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: 5e5bc8eaa4e710e6564ee6f1d3ea1bfcf7f28127
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="treemaps-in-power-bi-tutorial"></a>Treemaps no Power BI (Tutorial)
Os treemaps apresentam dados hierárquicos, como um conjunto de retângulos aninhados.  Cada nível da hierarquia é representado por um retângulo colorido (muitas vezes chamado um "ramo") que contém outros retângulos ("folhas").  O espaço dentro de cada retângulo é alocado com base no valor quantitativo que está a ser medido, os retângulos organizados por tamanho da parte superior esquerda (maior) para a parte inferior direita (mais pequena).

![](media/power-bi-visualization-treemaps/pbi-nancy_viz_treemap.png)

Por exemplo, se estiver a analisar as minhas vendas, posso ter retângulos de nível superior (ramos) para as categorias de vestuário: **Urbano**, **Rural**, **Jovem** e **Combinado**.  Os retângulos da categoria contêm retângulos mais pequenos (folhas) para fabricantes de vestuário nessa categoria e estes retângulos mais pequenos seriam dimensionados e sombreados com base no número vendido.  No ramo **Urbano** acima, muito vestuário Maximus foi vendido, menos do que Natura e Fama e muito pouco Leo.  Assim, o ramo **Urbana** do meu Treemap teria o retângulo maior para Maximus (no canto superior esquerdo), um retângulo um pouco menor para Natura e Fama, muitos outros retângulos a representar todo o vestuário vendido e um pequeno retângulo para Leo.  Posso comparar o número de artigos vendidos noutros grupos de vestuário ao comparar o tamanho e o sombreado de nó de folha: quanto maior o retângulo e quanto mais escuro for o sombreado, maior será o valor.

## <a name="when-to-use-a-treemap"></a>Quando utilizar um Treemap
Os treemaps são uma ótima opção:

* para apresentar grandes quantidades de dados hierárquicos.
* quando um gráfico de barras não puder lidar efetivamente com um grande número de valores.
* para mostrar as proporções entre cada parte e o todo.
* para mostrar o padrão da distribuição da medida em cada nível das categorias na hierarquia.
* para mostrar atributos com a codificação de cor e tamanho.
* para identificar padrões, valores atípicos, colaboradores mais importantes e exceções.

## <a name="create-a-basic-treemap"></a>Criar um treemap básico
Quer ver alguém criar primeiro um treemap?  Avance para 2:10 neste vídeo para ver a Amanda criar um treemap.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

Em alternativa, crie o seu próprio treemap. Essas instruções utilizam o Exemplo de Análise de Revenda. Para acompanhar, [transfira o exemplo](sample-datasets.md), inicie sessão no Power BI e selecione **Obter Dados \> Livro do Excel \> Ligar \> Exemplo de Análise de Revenda**.**xlsx**.

1. Comece no [Modo de Edição](service-interact-with-a-report-in-editing-view.md) e selecione a medida **Vendas** > **Vendas do Ano Passado**.   
   ![](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)
2. Converta o gráfico num treemap.  
   ![](media/power-bi-visualization-treemaps/treemapconvertto_new.png)
3. Arraste **Item** > **Categoria** para o painel **Grupo**. O Power BI cria um treemap no qual o tamanho dos retângulos reflete o total de vendas e a cor representa a categoria.  No fundo, criou uma hierarquia que descreve visualmente o tamanho relativo do total de vendas por categoria.  A categoria **Mens** tem as vendas mais altas e a categoria **Hosiery** tem as mais baixas.
   ![](media/power-bi-visualization-treemaps/treemapcomplete_new.png)
4. Arraste **Loja** > **Cadeia** para o painel **Detalhes** para concluir o treemap. Agora pode comparar as vendas do ano passado por categoria e cadeia.   
   ![](media/power-bi-visualization-treemaps/treemap_addgroup_new.png)
   
   > [!NOTE]
   > Os campos Saturação de Cor e Detalhes não podem ser utilizados em simultâneo.
   > 
   > 
5. Coloque o cursor sobre uma área **Cadeia** para revelar a descrição dessa parte da **Categoria**.  Por exemplo, se colocar o cursor sobre **Lindseys** no retângulo **040-Juniors**, revela a descrição da parte Lindsey da categoria Juniors.  
   ![](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)
6. [Adicione o treemap como um mosaico de dashboard (afixar o elemento visual)](service-dashboard-tiles.md). 
7. [Guarde o relatório](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Destaque e filtragem cruzada
Para obter informações sobre como utilizar o painel Filtros, veja [Add a filter to a report (Adicionar um filtro a um relatório)](power-bi-report-add-filter.md).

Realçar uma Categoria ou Detalhes num treemap filtra e destaca de forma cruzada as outras visualizações na página de relatório e vice-versa. Para acompanhar, adicione alguns elementos visuais à mesma página ou copie/cole o treemap numa página de relatório que já tenha outros elementos visuais.

1. No treemap, selecione uma Categoria ou uma Cadeia numa Categoria.  Isto destaca de forma cruzada as outras visualizações na página. Por exemplo, se selecionar **050-Shoes**, é indicado que as vendas do ano passado de sapatos foram de 3 640 471 $, sendo 2 174 185 $ proveniente da Fashions Direct.  
   ![](media/power-bi-visualization-treemaps/treemaphiliting.png)
2. No gráfico circular **Vendas do Ano Passado por Cadeia**, selecione o setor **Fashions Direct**.  
   ![](media/power-bi-visualization-treemaps/treemapnoowl.gif)
3. Para gerir a forma como os gráficos se destacam e filtram entre si de forma cruzada, veja [Interações de visualização num relatório do Power BI](service-reports-visual-interactions.md)

## <a name="next-steps"></a>Próximos passos
[Relatórios no Power BI](service-reports.md)  
[Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)  
[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) 
[ Afixar uma visualização a um dashboard](service-dashboard-pin-tile-from-report.md)  
[Power BI - Conceitos Básicos](service-basic-concepts.md)  
[Experimente – é gratuito!](https://powerbi.com/)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)  

