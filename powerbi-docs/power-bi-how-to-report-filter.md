---
title: Fazer uma visita do painel Filtros do Power BI
description: "Como utilizar filtros de relatório"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/29/2017
ms.author: mihart
ms.openlocfilehash: da3d4359fab37d1c5ee5f9d214cc5dba0fa9b680
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2018
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Fazer uma visita do painel Filtros
Este artigo analisa de forma aprofundada o painel Filtros de relatórios. Irá ver o painel na Vista de Edição e na Vista de Leitura para relatórios do Power BI.

Existem diversas formas de filtrar dados no Power BI e recomendamos que comece por ler [Sobre os filtros e o realce](power-bi-reports-filters-and-highlighting.md).

## <a name="working-with-filters"></a>Trabalhar com filtros
Os relatórios podem ser abertos na [Vista de edição ou Vista de leitura](service-reading-view-and-editing-view.md). Na vista de Edição, os proprietários de relatórios podem [adicionar filtros a um relatório](power-bi-report-add-filter.md) e esses filtros serão guardados com o relatório. As pessoas que visualizam o relatório na Vista de leitura podem interagir com os filtros, mas não podem guardar as alterações de filtros no relatório.

## <a name="filters-in-reading-view"></a>Filtros na Vista de Leitura
Quando um relatório é aberto na Vista de Leitura, o painel Filtros é apresentado no lado direito da tela de relatório. Se não vir o painel, selecione a seta no canto superior direito para expandi-la.

Neste exemplo selecionámos um visual com 6 filtros. A página de relatórios também tem filtros, listados no cabeçalho **Filtros de nível de página**. Há um [Filtro de pormenorização](power-bi-report-add-filter.md) e o relatório completo tem também um filtro: **FiscalYear** is 2013 or 2014 (Ano Fiscal é 2013 ou 2014).

![](media/power-bi-how-to-report-filter/power-bi-filter-list.png)

Alguns dos filtros têm a palavra **Tudo** junto aos mesmos, o que significa que todos os valores estão incluídos no filtro.  Por exemplo, na captura de ecrã abaixo, **Chain(All)** indica-nos que esta página de relatório inclui dados sobre todas as cadeias de lojas.  Por outro lado, o filtro ao nível de relatório de **FiscalYear is 2013 or 2014** indica que o relatório inclui apenas dados correspondentes aos anos fiscais de 2013 e 2014.

Qualquer pessoa a ver este relatório pode interagir com estes filtros.

* ver os detalhes do filtro ao passar o cursor e selecionar a seta junto ao filtro.
  
   ![](media/power-bi-how-to-report-filter/power-bi-expan-filter.png)
* alterar o filtro, por exemplo, alterar **Lindseys** para **Fashions Direct**.
  
     ![](media/power-bi-how-to-report-filter/power-bi-filter-chain.png)
* eliminar o filtro ao selecionar o **x** junto ao nome do filtro.
  
  Eliminar um filtro remove-o da lista, mas não elimina os dados do relatório.  Por exemplo, se eliminar **FiscalYear is 2013 or 2014** (Ano Fiscal é 2013 ou 2014), os dados do ano fiscal permanecerão no relatório, mas já não serão filtrados para mostrar apenas 2013 e 2014; irão mostrar todos os anos fiscais que os dados contêm.  No entanto, após eliminar o filtro, não poderá modificá-lo novamente, uma vez que foi removido da lista. Uma opção melhor é limpar o filtro ao selecionar o ícone da borracha ![](media/power-bi-how-to-report-filter/power-bi-eraser-icon.png).
  
  ![](media/power-bi-how-to-report-filter/power-bi-delete-filter.png)

## <a name="filters-in-editing-view"></a>Filtros na Vista de Edição
Quando um relatório é aberto na Vista de Edição, o painel Filtros é apresentado no lado direito da tela de relatório na metade inferior do **painel Visualização**. Se não vir o painel, selecione a seta no canto superior direito para expandi-la.

![](media/power-bi-how-to-report-filter/power-bi-all-filters.png).  

Se nenhum visual for selecionado na tela, o painel de Filtros mostra apenas os filtros que se aplicam a toda página de relatório e eventuais filtros de pormenorização (se tiverem sido definidos). No exemplo abaixo, nenhum visual é selecionado e não existem filtros de nível de página ou pormenorização, mas existe um filtro de nível de relatório.  

![](media/power-bi-how-to-report-filter/power-bi-no-visual.png)  

Se um elemento visual for selecionado na tela, também verá os filtros que se aplicam apenas àquele elemento visual:   

![](media/power-bi-how-to-report-filter/power-bi-visual-filters.png)

Para mostrar opções para um filtro específico, selecione a seta para baixo junto ao nome do filtro.  No exemplo abaixo, o filtro de nível de relatório está definido para 2013 e 2014. Este é um exemplo de **filtragem básica**.  Para mostrar as opções avançadas, selecione **Filtragem Avançada**.

![](media/power-bi-how-to-report-filter/pbi_filterlistdropdown.jpg)

## <a name="clear-a-filter"></a>Limpar um filtro
 No modo de filtragem avançado ou básico, selecione o ícone de borracha ![](media/power-bi-how-to-report-filter/pbi_erasericon.jpg) para repor o filtro. 

## <a name="add-a-filter"></a>Adicionar um filtro
* Na vista de edição, adicione um filtro a um visual, página, pormenorização ou relatório ao selecionar um campo do painel Campos e arrastá-lo para o well de filtro adequado, onde se veem as palavras **Arrastar campos para aqui**. Após um campo ser adicionado como um filtro, ajuste-o através dos controlos de filtragem Básica e filtragem Avançada (descritos abaixo).

Arrastar um novo campo para a área de filtros de nível Visual não adiciona esse campo ao visual, mas permite-lhe filtrar o visual com este novo campo. No exemplo abaixo, **Chain** (Cadeia) foi adicionado como um novo filtro para o visual. Repare que adicionar simplesmente **Chain** (Cadeia) como filtro não altera o visual até utilizar os controlos de filtragem Básica ou Avançada.

    ![](media/power-bi-how-to-report-filter/power-bi-visual-filter.gif)

* Todos os campos que são utilizados para criar uma visualização também estão disponíveis como filtros. Primeiro, selecione um visual para torná-lo ativo. Os campos utilizados no visual estão listados no painel Visualizações (se estiver na vista de Edição) e no painel Filtros, no cabeçalho **Filtros de nível visual**.
  
   ![](media/power-bi-how-to-report-filter/power-bi-visual-filter.png)  
  
   Ajuste estes campos através dos controlos de filtragem Básica e filtragem Avançada (descritos abaixo).

## <a name="types-of-filters-text-field-filters"></a>Tipos de filtros: filtros de campo de texto
### <a name="list-mode"></a>Modo de lista
Marcar uma caixa de verificação ou seleciona ou deseleciona o valor. A caixa de verificação **Tudo** pode ser utilizada para ativar ou desativar o estado de todas as caixas de verificação. As caixas de verificação representam todos os valores disponíveis para esse campo.  À medida que ajusta o filtro, a reformulação é ajustada para refletir as suas escolhas. 

![](media/power-bi-how-to-report-filter/pbi_restatement.png)

Observe como a reformulação agora diz "é Amarilla ou Carretera"

### <a name="advanced-mode"></a>Modo avançado
Selecione **Filtragem Avançada** para mudar para o modo avançado. Utilize os controlos de lista pendente e as caixas de texto para identificar quais campos serão incluídos. Ao escolher entre **And** (E) e **Or** (Ou), pode criar expressões de filtros complexas. Selecione o botão **Aplicar Filtro** quando tiver definido os valores pretendidos.  

![](media/power-bi-how-to-report-filter/aboutfilters.png)

## <a name="types-of-filters-numeric-field-filters"></a>Tipos de filtros: filtros de campo numérico
### <a name="list-mode"></a>Modo de lista
Se os valores forem finitos, selecionar o nome do campo apresenta uma lista.  Consulte **Filtros de campos de texto** &gt; **Modo de lista** acima para obter ajuda na utilização de caixas de verificação.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores forem infinitos ou representarem um intervalo, selecionar o nome do campo abre o modo de filtro avançado. Utilize a lista pendente e as caixas de texto para especificar o intervalo de valores que pretende ver. 

![](media/power-bi-how-to-report-filter/pbi_dropdown-and-text.png)

Ao escolher entre **And** (E) e **Or** (Ou), pode criar expressões de filtros complexas. Selecione o botão **Aplicar Filtro** quando tiver definido os valores pretendidos.

## <a name="types-of-filters-date-and-time"></a>Tipos de filtros: data e hora
### <a name="list-mode"></a>Modo de lista
Se os valores forem finitos, selecionar o nome do campo apresenta uma lista.  Consulte **Filtros de campos de texto** &gt; **Modo de lista** acima para obter ajuda na utilização de caixas de verificação.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores de campo representarem a data ou hora, pode especificar uma hora de início/fim quando utilizar os filtros de Data/Hora.  

![](media/power-bi-how-to-report-filter/pbi_date-time-filters.png)

## <a name="next-steps"></a>Passos seguintes
[Filtros e realce nos relatórios](power-bi-reports-filters-and-highlighting.md)  
[Interagir com filtros e realce na Vista de Leitura de relatórios](service-reading-view-and-editing-view.md)  
[Criar filtros na Vista de Edição de relatórios](power-bi-report-add-filter.md)  
[Alterar como os elementos visuais de relatórios realizam filtragem cruzada e realce cruzado entre si](service-reports-visual-interactions.md)

Saiba mais sobre os [relatórios no Power BI](service-reports.md)  
[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

