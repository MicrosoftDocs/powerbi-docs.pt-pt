---
title: Utilizar colunas calculadas no Power BI Desktop
description: Colunas calculadas no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 05/07/2019
LocalizationGroup: Model your data
ms.openlocfilehash: 9c7285f90b963166c643c2bb20f9323eddb7ce85
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415939"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Criar colunas calculadas no Power BI Desktop
Com as colunas calculadas pode adicionar novos dados a uma tabela já presente no seu modelo. No entanto, em vez de consultar e carregar valores para a nova coluna a partir de uma origem de dados, cria uma fórmula DAX (Data Analysis Expressions) que define os valores da coluna. No Power BI Desktop, as colunas calculadas são criadas com a nova funcionalidade de colunas na vista **Relatório**.

Ao contrário das colunas personalizadas criadas como parte de uma consulta através da opção **Adicionar Coluna Personalizada** no Editor de Consultas, as colunas calculadas criadas na vista **Relatório** ou **Dados** são baseadas nos dados que já carregou no modelo. Por exemplo, poderá concatenar os valores de duas colunas diferentes em duas tabelas diferentes mas relacionadas, realizar a adição ou extrair subcadeias.

As colunas calculadas criadas por si aparecem na lista **Campos** como com qualquer outro campo, mas têm um ícone especial que mostra que os respetivos valores são o resultado de uma fórmula. Pode nomear as suas colunas como desejar e adicioná-las a uma visualização de relatório, tal como com outros campos.

![Captura de ecrã a mostrar o Power BI Desktop com colunas calculadas na vista Campos.](media/desktop-calculated-columns/calccolinpbid_fields.png)
 
As colunas calculadas calculam os resultados através de DAX, uma linguagem de fórmula destinada a trabalhar com dados relacionais, como no Power BI Desktop. O DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores. Fornece uma enorme flexibilidade na criação de fórmulas para calcular os resultados de praticamente qualquer análise de dados necessária. Para obter mais informações sobre o DAX, consulte [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

As fórmulas DAX são semelhantes às fórmulas do Excel. Na verdade, o DAX tem muitas das mesmas funções usadas no Excel. As funções DAX, no entanto, destinam-se a trabalhar com dados fracionados interativamente ou filtrados num relatório, como no Power BI Desktop. No Excel, pode ter uma fórmula diferente para cada linha numa tabela. No Power BI, quando criar uma fórmula DAX para uma nova coluna, será calculado um resultado para todas as linhas na tabela. Os valores de coluna são recalculados conforme necessário, como quando os dados subjacentes foram atualizados e os valores mudaram.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo
O João é um gestor de expedição da Contoso e quer criar um relatório que mostre o número de envios para cidades diferentes. O João tem uma tabela **Geografia** com campos separados para cidade e estado. No entanto, ele pretende que os seus relatórios mostrem os valores de cidade e estado como um único valor na mesma linha. De momento, a tabela **Geografia** do João não tem o campo pretendido.

![Captura de ecrã a mostrar o Power BI Desktop com o filtro Geografia na vista Campos.](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Todavia, com uma coluna calculada, ele pode juntar as cidades da coluna **Cidade** com os estados da coluna **Estado**.

O João clica com o botão direito do rato na tabela **Geografia** e, em seguida, seleciona **Nova Coluna**. Em seguida, o João introduz a seguinte fórmula DAX na barra de fórmulas:

![Captura de ecrã a mostrar o Power BI Desktop com a entrada da fórmula DAX.](media/desktop-calculated-columns/calccolinpbid_formula.png)

Esta fórmula cria simplesmente uma nova coluna com o nome **Cidade, Estado**. Para cada linha na tabela **Geografia**, utiliza os valores da coluna **Cidade**, adiciona uma vírgula e um espaço e, em seguida, concatena os valores da coluna **Estado**.

Agora, o João tem o campo pretendido.

![Captura de ecrã a mostrar o Power BI Desktop com a coluna Cidade, Estado marcada no filtro Geografia da vista Campos.](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Agora, pode adicioná-lo à tela de relatório juntamente com o número de envios. De uma forma simples, o João tem agora um campo **Cidade, Estado** que pode adicionar a praticamente qualquer tipo de visualização. Quando o João criar um novo mapa, o Power BI Desktop já sabe como ler os valores de cidade e estado na nova coluna.

![Captura de ecrã a mostrar o Power BI Desktop com dados representados num Mapa.](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>Próximos passos
Demos apenas uma rápida introdução às colunas calculadas. Para obter mais informações, consulte os seguintes recursos:

* Para transferir um ficheiro de exemplo e ver lições passo a passo sobre como criar mais colunas, veja [Tutorial: Criar colunas calculadas no Power BI Desktop](desktop-tutorial-create-calculated-columns.md)

* Para obter mais informações sobre o DAX, consulte [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

* Para saber mais sobre as colunas que cria como parte de uma consulta, veja a secção **Criar colunas personalizadas** em [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md).  

