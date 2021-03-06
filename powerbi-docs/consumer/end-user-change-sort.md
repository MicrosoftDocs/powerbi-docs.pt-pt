---
title: Alterar a forma como um gráfico é ordenado num relatório
description: Alterar a forma como um gráfico é ordenado num relatório do Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/03/2020
LocalizationGroup: Reports
ms.openlocfilehash: e211aded069675c02e59004631ea2264be1e0dcc
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96578290"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Alterar a forma como um gráfico é ordenado num relatório do Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]


> [!IMPORTANT]
> **Este artigo destina-se aos utilizadores do Power BI que não tenham permissões de edição no relatório ou no conjunto de dados e que apenas trabalhem na versão online do Power BI (o serviço Power BI). Se for um *designer*, *administrador* ou *proprietário* de relatórios, este artigo poderá não ter toda a informação de que necessita. Em alternativa, leia [Ordenação por coluna no Power BI Desktop](../create-reports/desktop-sort-by-column.md)** .

No serviço Power BI, pode alterar o aspeto de um elemento visual ao ordená-lo por campos de dados diferentes. Ao alterar a forma como ordena um elemento visual, pode destacar as informações que pretende transmitir. Se estiver a utilizar dados numéricos (como o volume de vendas) ou dados de texto (como nomes de estado), poderá ordenar os elementos visuais conforme quiser. O Power BI oferece bastante flexibilidade para ordenação e menus rápidos para utilização. 

Não pode ordenar os elementos visuais num dashboard. No entanto, num relatório do Power BI, pode ordenar a maioria dos elementos visuais com um e, por vezes, dois campos de cada vez. Para determinados tipos de elementos visuais, a ordenação não está disponível: treemaps, medidores, mapas, etc. 

## <a name="get-started"></a>Introdução

Para começar, abra um relatório que tenha sido criado por si ou partilhado consigo. Selecione um elemento visual (que pode ser ordenado) e selecione **Mais ações** (...).  Existem três opções de ordenação: **Ordenação descendente**, **Ordenação ascendente** e **Ordenar por**. 
    

![gráfico de barras ordenado alfabeticamente pelo eixo Y](media/end-user-change-sort/power-bi-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Ordenar alfabética ou numericamente

Os elementos visuais podem ser ordenados alfabeticamente pelos respetivos nomes das categorias ou pelos valores numéricos de cada categoria. Por exemplo, este gráfico está ordenado alfabeticamente pela categoria de eixo X **Store name**.

![gráfico de barras ordenado alfabeticamente pelo eixo X](media/end-user-change-sort/powerbi-sort-category.png)

Para alterar a ordenação de uma categoria (nome de arquivo) para um valor (vendas por metro quadrado), selecione **Mais ações** (...) e escolha **Ordenar por**. Selecione um valor numérico utilizado no elemento visual.  Neste exemplo, selecionámos **Sales Per Sq Ft**.

![Captura de ecrã a mostrar a seleção da opção Ordenar por e, em seguida, um valor](media/end-user-change-sort/power-bi-sort-value.png)

Se for necessário, alterne entre uma sequência de ordenação ascendente e descendente.  Selecione **Mais ações** (...) novamente e selecione **Ordenação descendente** ou **Ordenação ascendente**. O campo que está a ser utilizado na ordenação está a negrito e tem uma barra amarela.

   ![vídeo que mostra a ordem de seleção ascendente e descendente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nem todos os elementos visuais podem ser ordenados. Por exemplo, os seguintes elementos visuais não podem ser ordenados: treemap, mapa, mapa de manchas, dispersão, medidor, cartão, cascata.

## <a name="sorting-by-multiple-columns"></a>Ordenar por várias colunas
Os dados nesta tabela estão ordenados por **Número de clientes**.  Sabemos disso por causa da pequena seta por baixo da palavra *Número*. A seta está a apontar para baixo, o que significa que a coluna está a ser ordenada por ordem *descendente*.

![captura de ecrã a mostrar a primeira coluna a ser utilizada na ordenação](media/end-user-change-sort/power-bi-sort-column.png)


Para adicionar mais colunas à ordenação, prima Shift + clique no cabeçalho da coluna que gostaria de adicionar a seguir na ordenação. Por exemplo, se clicar em **Número de clientes** e, em seguida, premir Shift + clicar em **Receita total**, a tabela será ordenada primeiro por clientes e depois por receita. O contorno vermelho mostra as áreas onde a ordenação mudou.

![captura de ecrã a mostrar a segunda coluna a ser utilizada na ordenação](media/end-user-change-sort/power-bi-sort-second.png)

Se premir Shift + clicar uma segunda vez na mesma coluna, mudará a direção de ordenação (ascendente, descendente) dessa coluna. Além disso, se premir Shift + clicar numa coluna que adicionou anteriormente à ordenação, deslocará essa coluna para a parte de trás da ordenação.


## <a name="saving-changes-you-make-to-sort-order"></a>Guardar as alterações feitas à sequência de ordenação
Os relatórios do Power BI mantêm os filtros, as segmentações, a ordenação e outras alterações que fizer, mesmo que esteja a trabalhar na [Vista de leitura](end-user-reading-view.md). Por isso, se sair de um relatório e regressar mais tarde, as alterações de ordenação serão guardadas.  Se quiser reverter as alterações para as definições do *designer* de relatórios, selecione **Repor para predefinição** na barra de menus superior. 

![Ordenação persistente](media/end-user-change-sort/power-bi-reset.png)

No entanto, se o botão **Repor para predefinição** for apresentado a cinzento, isso significa que o *designer* do relatório desativou a capacidade de guardar (fazer persistir) as suas alterações.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

### <a name="sorting-using-other-criteria"></a>Ordenar através de outros critérios
Por vezes, quer ordenar o elemento visual através de um campo diferente (que não esteja incluído no elemento visual) ou outros critérios.  Por exemplo, talvez queira ordenar de forma sequencial por mês (e não por ordem alfabética) ou por números inteiros em vez de por dígitos (por exemplo, 0, 1, 9, 20 e não 0, 1, 20, 9).  

Apenas a pessoa que criou o relatório pode fazer estas alterações por si. As informações de contacto do *designer* podem ser encontradas ao selecionar o nome do relatório na barra de cabeçalho.

![Lista pendente a mostrar informações de contacto](media/end-user-change-sort/power-bi-heading.png)

Se for um *designer* e tiver permissões de edição no conteúdo, leia [Ordenação por coluna no Power BI Desktop](../create-reports/desktop-sort-by-column.md) para saber como atualizar o conjunto de dados e ativar este tipo de ordenação.

## <a name="next-steps"></a>Próximos passos
Mais sobre [Visualizações em relatórios do Power BI](end-user-visualizations.md).

[Power BI - Conceitos Básicos](end-user-basic-concepts.md)
