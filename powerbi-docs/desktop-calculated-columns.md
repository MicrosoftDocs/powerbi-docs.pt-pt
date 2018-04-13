---
title: Utilizar colunas calculadas no Power BI Desktop
description: Colunas calculadas no Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 4a47e707969b592ec27c79558699638ce14f8640
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/06/2018
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>Utilizar colunas calculadas no Power BI Desktop
Com as colunas calculadas pode adicionar novos dados a uma tabela já presente no seu modelo. Mas em vez de consultar e carregar valores para a nova coluna a partir de uma origem de dados, cria uma fórmula DAX (Data Analysis Expressions) que define os valores da coluna. No Power BI Desktop, as colunas calculadas são criadas através da funcionalidade Nova Coluna na Vista de Relatório.

Ao contrário das colunas personalizadas criadas como parte de uma consulta com “Adicionar Coluna Personalizada” no Editor de Consultas, as colunas calculadas criadas na Vista de Relatório ou Vista de Dados são baseadas em dados que já carregou no modelo. Por exemplo, poderá concatenar os valores de duas colunas diferentes em duas tabelas diferentes mas relacionadas, realizar a adição ou extrair subcadeias.

As colunas calculadas que cria aparecem na lista de Campos tal como com qualquer outro campo, mas têm um ícone especial que mostra que os seus valores são o resultado de uma fórmula. Pode nomear as suas colunas como desejar e adicioná-las a uma visualização de relatório, tal como com outros campos.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

As colunas calculadas calculam os resultados através de [DAX](https://msdn.microsoft.com/library/gg413422.aspx) (Data Analysis Expressions), uma linguagem de fórmula destinada a trabalhar com dados relacionais, como no Power BI Desktop. O DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores, fornecendo enorme flexibilidade na criação de fórmulas para calcular os resultados de praticamente qualquer análise de dados que seja necessária. Para saber mais sobre o DAX, consulte a secção “Saiba mais” no final deste artigo.

As fórmulas DAX são semelhantes às fórmulas do Excel. Na verdade, o DAX tem muitas das mesmas funções usadas no Excel. As funções DAX, no entanto, destinam-se a trabalhar com dados fracionados interativamente ou filtrados num relatório, como no Power BI Desktop. Ao contrário do Excel, no qual pode ter uma fórmula diferente para cada linha de uma tabela, uma fórmula DAX criada para uma nova coluna calculará um resultado para cada linha na tabela. Os valores de coluna são recalculados conforme necessário, como quando os dados subjacentes foram atualizados e os valores mudaram.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo
O João é um gestor de expedição da Contoso. Pretende criar um relatório que mostre o número de remessas para cidades diferentes. Tem uma tabela Geography com campos separados para cidade e estado. No entanto, o João quer que os seus relatórios mostrem a cidade e o estado como um único valor, na mesma linha. De momento, a tabela Geography do João não tem o campo que ele pretende.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Todavia, com uma coluna calculada, o João pode simplesmente juntar ou concatenar as cidades da coluna City com os estados da coluna State.

O João clica na tabela Geography e, em seguida, clica em Nova Coluna. Depois, introduz a seguinte fórmula DAX na barra de fórmulas:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Esta fórmula simplesmente cria uma nova coluna chamada CityState e, para cada linha na tabela Geography, usa os valores da coluna City, adiciona uma vírgula e um espaço e, em seguida, concatena os valores da coluna State.

Agora, o João tem o campo que pretende.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Pode adicioná-lo à tela de relatório juntamente com o número de remessas. Muito rapidamente e com um mínimo de esforço, o João tem agora um campo "City, State" que pode adicionar a praticamente qualquer tipo de visualização. O João vê que, quando cria uma visualização de mapa, o Power BI Desktop sabe inclusive como ler os valores de "City, State" na sua nova coluna.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>Saiba mais
Fornecemos apenas uma rápida introdução às colunas calculadas. Não deixe de consultar o tutorial [Criar colunas calculadas no Power BI Desktop](desktop-tutorial-create-calculated-columns.md), no qual poderá transferir um ficheiro de exemplo e obter lições passo a passo sobre como criar mais colunas. 

Para obter mais informações sobre o DAX, consulte [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Para saber mais sobre as colunas que cria como parte de uma consulta, consulte a secção "Criar colunas personalizadas" em [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md).  

