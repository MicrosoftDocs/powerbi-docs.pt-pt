---
title: "Segmentações de dados no Power BI (Tutorial)"
description: "Tutorial: segmentações no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/30/2017
ms.author: mihart
ms.openlocfilehash: b6ce0c396f4a189489b97fe5cd86ab5cd8dbcc35
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="slicers-in-power-bi-service-tutorial"></a>Segmentações de dados no serviço Power BI (Tutorial)
O seu RP de Vendas quer ver várias métricas, de todo o departamento e de cada Gestor Regional individual. Pode criar uma página de relatório separada para cada gestor ou utilizar uma segmentação de dados. Uma segmentação de dados restringe a parte do conjunto de dados mostrado nas outras visualizações na página.  As segmentações são uma maneira alternativa de filtragem.

![](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Quando usar uma segmentação
As segmentações são a escolha ideal nas seguintes situações.

* Para apresentar os filtros mais utilizados ou importantes na tela do relatório para facilitar o acesso.
* Para facilitar a apresentação do estado atual filtrado sem ter de abrir uma lista pendente para encontrar os detalhes da filtragem.
* Quando desejar ocultar colunas de que não precisa, mas pretenda poder usá-las para filtrar - isto torna as tabelas mais estreitas e mais limpas.
* Para criar relatórios mais objetivos; como as segmentações de dados são objetos flutuantes, pode colocá-las ao lado da parte interessante do relatório em que quer que os utilizadores se concentrem.

## <a name="create-a-slicer"></a>Criar uma segmentação
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>


1. Abra o [Exemplo de Análise de Revenda](sample-retail-analysis.md) na [Vista de Edição](service-interact-with-a-report-in-editing-view.md) e [adicione uma nova página de relatório](power-bi-report-add-page.md).
2. No painel Campos, selecione **Distrito > Gerente Regional**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_chartfirst.png)
3. Converta a visualização numa segmentação. No painel Visualizações, selecione o ícone de segmentação de dados.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_select.png)

## <a name="format-the-slicer"></a>Formatar a segmentação de dados
1. Com a segmentação de dados selecionada, no painel Visualizações, selecione o ícone de rolo ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) para apresentar as opções Formatar.
2. Selecione **Geral > Cor da estrutura de tópicos**, escolha azul escuro e altere o **Peso** para **6**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_outline2.png)
3. Em **Controlos de Seleção**, por predefinição, **Selecionar Tudo** está **Desativado** e **Seleção Única** está **Ativado**. Isto significa que é preciso usar a tecla CTRL para selecionar mais de um nome ao mesmo tempo. Marque **Selecionar Tudo** como **Ativado** e **Seleção Única** como **Desativado**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_selectioncontrols2.png)
   
   * Tenha em atenção que a segmentação agora tem uma opção **Selecionar Tudo** na parte superior da lista. Ative/desative **Selecionar Tudo** para selecionar todos os nomes ou para não selecionar nenhum nome.
   * Agora, é possível selecionar mais de um nome sem a necessidade de usar a tecla CTRL.
4. Em **Itens**, aumente o tamanho do texto para 14 pt.  Queremos ter a certeza de que os nossos colegas reparam nesta segmentação.
5. Por fim, defina **Cor do Tipo de Letra** como vermelho escuro.  Isto distinguirá os nomes selecionados dos nomes não selecionados na nossa segmentação.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_font2.png)
6. Divirta-se a explorar as outras opções disponíveis para segmentações de dados.

## <a name="use-the-slicer-in-a-report"></a>Usar a segmentação num relatório
1. Adicione algumas visualizações à página de relatório ou abra o [relatório de exemplo Análise de Revenda](sample-retail-analysis.md) e selecione o separador **Vendas Mensais Regionais**.
   
    ![](media/power-bi-visualization-slicers/power-bi-retail-sample.png)
2. Segmente a página de relatório de Carlos. Repare como as outras visualizações são atualizadas para refletir estas seleções.
   
    ![](media/power-bi-visualization-slicers/slicer2.gif)
3. Classifique a segmentação por ordem alfabética pelo apelido do Gerente Regional.  Selecione as reticências (...) no canto superior direito da segmentação e escolha **Gerente Regional**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sort2.png)
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sorted.png)

## <a name="control-what-effect-the-slicer-has-on-other-visuals-on-the-page"></a>Controlar que efeito a segmentação tem noutros elementos visuais na página
Quer que a segmentação de dados filtre apenas alguns dos elementos visuais na página de relatório?  Utilize o controlo **Interações visuais** para configurá-la.

**NOTA**: se não vir **Interações Visuais**, procure o respetivo ícone ![](media/power-bi-visualization-slicers/power-bi-slicer-visual-interactions.png). Se também não vir um, certifique-se de que está na [vista de Edição](service-reading-view-and-editing-view.md) do relatório.

1. Selecione a segmentação de dados para torná-la ativa na barra de menus e selecione **Interações visuais**.
   
    ![](media/power-bi-visualization-slicers/pbi-slicer-interactions.png)
2. Os controlos de filtro serão exibidos acima de todos os outros elementos visuais na página. Se a segmentação de dados deve filtrar um elemento visual, selecione o ícone **Filtro**.  Se a segmentação de dados não deve ter nenhum efeito sobre o elemento visual, selecione o ícone **Nenhum**.
   
    ![](media/power-bi-visualization-slicers/filter-controls.png)

Para obter mais informações, veja [Interações visuais num relatório do Power BI](service-reports-visual-interactions.md).

## <a name="considerations-and-troubleshooting-slicers-in-power-bi"></a>Considerações e resolução de problemas de segmentações de dados no Power BI
Existem algumas limitações na utilização de segmentações de dados no Power BI, que são as seguintes:

1. As segmentações de dados não suportam campos de texto.
2. Não é possível utilizar uma segmentação de dados única num relatório completo. Uma segmentação de dados afeta apenas a página atual.
3. As segmentações de dados não podem ser afixadas a um dashboard.
4. A desagregação não é suportada para segmentações de dados.    
5. As segmentações de dados não suportam filtros ao nível de Elementos Visuais.

Tem ideias sobre como melhorar o Power BI? [Submeter uma ideia](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

## <a name="next-steps"></a>Próximos passos
 [Adicionar uma visualização a um relatório](power-bi-report-add-visualizations-i.md)

 [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

 [Power BI - Conceitos Básicos](service-basic-concepts.md)

[Experimente – é gratuito!](https://powerbi.com/)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

