---
title: Medidas no Power BI Desktop
description: Medidas no Power BI Desktop
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 2e1aed189f858bee3b1d110df5b91caed88f479b
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="measures-in-power-bi-desktop"></a>Medidas no Power BI Desktop
O **Power BI Desktop** ajuda-o a criar informações sobre os seus dados com apenas alguns cliques. Por vezes, estes dados simplesmente não incluem tudo o que precisa para responder a algumas das suas perguntas mais importantes. As medidas podem ajudá-lo a conseguir isso.

As medidas são utilizadas em algumas das análises de dados mais comuns; por exemplo, somas, médias, valores mínimos ou máximos, contagens ou cálculos mais avançados que cria através de uma fórmula DAX. Os resultados calculados das medidas estão sempre a mudar em resposta à sua interação com os relatórios, o que permite uma exploração de dados ad-hoc rápida e dinâmica. Vamos ver isso mais de perto.

## <a name="understanding-measures"></a>Noções básicas sobre medidas
No **Power BI Desktop**, as medidas são criadas e utilizadas na **Vista de Relatório** ou na **Vista de Dados**. As medidas que cria são apresentadas na lista Campos com um ícone de Calculadora. Pode atribuir um nome às medidas como quiser e adicioná-las a uma visualização nova ou existente, tal como qualquer outro campo.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Pode também ter interesse nas **medidas rápidas**, que são medidas já preparadas que pode selecionar a partir das caixas de diálogo. São uma boa forma para criar medidas rapidamente, bem como aprender a sintaxe de DAX, dado que as fórmulas DAX automaticamente criadas estão disponíveis para revisão. Consulte o artigo: [medidas rápidas](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis Expressions
As medidas calculam um resultado através de uma fórmula de expressão. Ao criar as suas próprias medidas, vai utilizar a linguagem de fórmulas [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX). O DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores e fornece uma enorme flexibilidade na criação de medidas para calcular os resultados de praticamente qualquer análise de dados necessária.

As fórmulas DAX são muito semelhantes às fórmulas do Excel. O DAX tem até muitas das mesmas funções, como DATA, SOMA e ESQUERDA. As funções do DAX, no entanto, devem funcionar com dados relacionais, como os que temos no Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo
Júlia é gestora de vendas da Contoso. Foi-lhe pedido para fornecer projeções de vendas de revendedores para o próximo ano fiscal. Decide basear as suas estimativas nos valores de vendas do ano anterior, com um aumento anual de 6% resultante de várias promoções agendadas para os próximos seis meses.

Para reportar as estimativas, importa os dados de vendas do ano anterior para o Power BI Desktop. Localiza o campo SalesAmount na tabela Reseller Sales. Como os dados que importou contêm apenas valores de vendas para o último ano, muda o nome do campo SalesAmount para Last Years Sales. Em seguida, arrasta Last Years Sales para a tela de relatórios. Aparece numa visualização de gráfico como um valor único, que é a soma de todas as vendas dos revendedores do ano anterior.

Repara que um cálculo foi fornecido automaticamente, embora não tenha especificado nenhum. O Power BI Desktop criou a sua própria medida ao somar todos os valores em Last Years Sales.

No entanto, Júlia precisa de uma medida para calcular as projeções de vendas para o próximo ano, que serão baseadas nas vendas do ano anterior multiplicadas por 1,06, para considerar o aumento de 6% esperado no negócio. Para este cálculo, criará a sua própria medida. Ao utilizar a funcionalidade Nova Medida, cria uma nova medida e, em seguida, introduz a seguinte fórmula DAX:

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Em seguida, Júlia arrasta a nova medida Projected Sales para o gráfico.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Muito rapidamente e com o mínimo esforço, Júlia tem agora uma medida para calcular as vendas projetadas. Também pode analisar as suas projeções ao filtrar revendedores específicos ou ao adicionar outros campos ao relatório.

## <a name="learn-more"></a>Saiba mais
Fornecemos aqui apenas uma rápida introdução às medidas, mas há muito mais conteúdo para ajudá-lo a criar as suas próprias. Certifique-se de que vê o [Tutorial: criar as suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md), onde pode transferir um ficheiro de exemplo e ver lições passo-a-passo sobre como criar mais medidas.  

Para saber mais sobre DAX, certifique-se de que consulta [Bases de DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). A [Referência das Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) fornece artigos detalhes sobre cada das funções, sintaxe, operadores e convenções de nomenclatura. O DAX já existe há muitos anos no Power Pivot no Excel e no SQL Server Analysis Services, pelo que existem muitos outros recursos excelentes disponíveis. Certifique-se de que vê o [Wiki do Centro de Recursos do DAX](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), onde os membros influentes da comunidade de BI partilham os seus conhecimentos de DAX.



