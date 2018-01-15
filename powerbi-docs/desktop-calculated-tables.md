---
title: Utilizar as tabelas calculadas no Power BI Desktop
description: Tabelas calculadas no Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: bdfbf79f2b261e9246cb406d9ed9c8ebefc1440e
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Utilizar as tabelas calculadas no Power BI Desktop
Com tabelas calculadas, pode adicionar uma nova tabela ao modelo. Mas em vez de consultar e carregar valores nas colunas da sua nova tabela a partir de uma origem de dados, cria uma fórmula DAX (Data Analysis Expressions) que define os valores da tabela. No Power BI Desktop, as tabelas calculadas são criadas através da funcionalidade Nova Tabela na Vista de Relatório ou Vista de Dados.

Na maioria das vezes, importa dados para o seu modelo a partir de uma origem de dados externa. No entanto, as tabelas calculadas oferecem certas vantagens. As tabelas calculadas são geralmente melhores para cálculos intermédios e para dados que pretenda armazenados como parte do modelo, em vez de calculados dinamicamente ou como parte de uma consulta.

Ao contrário das tabelas criadas como parte de uma consulta, as tabelas calculadas criadas na Vista de Relatório ou Vista de Dados são baseadas em dados que já carregou no modelo. Por exemplo, pode optar entre union (união) e cross join (junção cruzada) de duas tabelas.

À semelhança das tabelas normais, as tabelas calculadas podem ter relações com outras tabelas. As colunas na tabela calculada têm tipos de dados, formatação e podem pertencer a uma categoria de dados. Pode nomear as suas colunas como desejar e adicioná-las a uma visualização de relatório, tal como com outros campos. As tabelas calculadas são recalculadas se alguma das tabelas das quais recebem dados por pull for de alguma forma renovada ou atualizada.

As tabelas calculadas calculam os resultados através de [DAX](https://msdn.microsoft.com/library/gg413422.aspx) (Data Analysis Expressions), uma linguagem de fórmula destinada a trabalhar com dados relacionais, como no Power BI Desktop. O DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores, fornecendo enorme flexibilidade na criação de fórmulas para calcular os resultados de praticamente qualquer análise de dados que seja necessária.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo
Jeff, um gstor de projetos da Contoso, tem uma tabela com funcionários no Noroeste e outra tabela com funcionários no Sudoeste. Jeff deseja juntar as duas numa única tabela.

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SoutwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Com uma tabela calculada, é muito fácil unir essas duas tabelas. Embora Jeff possa criar uma tabela calculada na Vista de Relatório ou Vista de Dados, é um pouco mais fácil fazê-lo na Vista de Dados porque assim pode ver de imediato a nova tabela calculada.

Na **Vista de Dados**, no separador **Modelação**, o Jeff clica em **Nova Tabela**. Uma barra de fórmulas é exibida.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff introduz então a seguinte fórmula:

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

É criada uma nova tabela chamada Western Region Employees.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

A nova tabela Western Region Employees de Jeff aparece como qualquer outra tabela na lista de Campos. Ele pode criar relações com outras tabelas, adicionar medidas e colunas calculadas e adicionar qualquer dos seus campos a relatórios, tal como com qualquer outra tabela.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funções para tabelas calculadas
As tabelas calculadas podem ser definidas por qualquer expressão DAX que devolva uma tabela, incluindo uma referência simples a outra tabela. Por exemplo:

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

Pode usar tabelas calculadas com o DAX para solucionar muitos problemas analíticos. Fornecemos apenas uma rápida introdução às tabelas calculadas. Quando começar a trabalhar com tabelas calculadas, veja aqui algumas das funções DAX de tabela mais comuns e que podem ser úteis:

&lt;TABLE&gt; DISTINCT VALUES CROSSJOIN UNION NATURALINNERJOIN NATURALLEFTOUTERJOIN INTERSECT CALENDAR CALENDARAUTO

Consulte a [Referência de Função DAX](https://msdn.microsoft.com/ee634396.aspx) para estas e outras tabelas que devolvam funções DAX.

