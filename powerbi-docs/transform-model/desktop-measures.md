---
title: Medidas no Power BI Desktop
description: Criar e utilizar medidas no Power BI Desktop, incluindo medidas rápidas e sintaxe DAX
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 809f0ec23dd0b7c1ef4cd41dde27fd0c8fdefd33
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83324500"
---
# <a name="create-measures-for-data-analysis-in-power-bi-desktop"></a>Criar medidas para análise de dados no Power BI Desktop

O Power BI Desktop ajuda-o a criar informações sobre os seus dados com apenas alguns cliques. Por vezes, estes dados simplesmente não incluem tudo o que precisa para responder a algumas das suas perguntas mais importantes. As medidas podem ajudá-lo a conseguir isso.

As medidas são utilizadas em algumas das análises de dados mais comuns. Resumos simples, como somas, médias, mínimo, máximo e contagens, podem ser definidos através da secção **Campos**. Os resultados calculados das medidas estão sempre a mudar em resposta à sua interação com os relatórios, o que permite uma exploração de dados ad-hoc rápida e dinâmica. Vamos ver isso mais de perto. Para obter mais informações, veja [Criar medidas calculadas](/learn/modules/model-data-power-bi/4b-create-calculated-measures).

## <a name="understanding-measures"></a>Noções básicas sobre medidas

No Power BI Desktop, as medidas são criadas e apresentadas na *Vista de Relatório* ou na *Vista de Dados*. As medidas que cria são apresentadas na lista **Campos** com um ícone de Calculadora. Pode atribuir um nome às medidas como quiser e adicioná-las a uma visualização nova ou existente, tal como qualquer outro campo.

![Campos de medidas em Campos](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Pode também ter interesse nas *medidas rápidas*, que são medidas já preparadas que pode selecionar a partir das caixas de diálogo. São uma boa forma para criar medidas rapidamente, bem como aprender a sintaxe do DAX (Data Analysis Expressions), dado que as fórmulas DAX automaticamente criadas estão disponíveis para revisão. Para obter mais informações, veja [medidas rápidas](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis Expressions

As medidas calculam um resultado através de uma fórmula de expressão. Ao criar as suas próprias medidas, vai utilizar a linguagem de fórmulas [Data Analysis Expressions](/dax/) (DAX). O DAX inclui uma biblioteca de mais de 200 funções, operadores e construtores. Esta fornece uma enorme flexibilidade na criação de medidas para calcular os resultados de praticamente qualquer análise de dados necessária.

As fórmulas DAX são muito semelhantes às fórmulas do Excel. O DAX tem até muitas das mesmas funções do Excel, como `DATE`, `SUM` e `LEFT`. As funções do DAX, no entanto, devem funcionar com dados relacionais, como os que temos no Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Vejamos um exemplo

Júlia é gestora de vendas da Contoso. Foi-lhe pedido para fornecer projeções de vendas de revendedores para o próximo ano fiscal. Júlia decide basear as estimativas nos valores de vendas do ano anterior, com um aumento anual de 6% resultante de várias promoções agendadas para os próximos seis meses.

Para criar um relatório das estimativas, Júlia importa os dados de vendas do ano anterior para o Power BI Desktop. Localiza o campo **SalesAmount** (MontanteDeVendas) na tabela **Reseller Sales** (Vendas dos Revendedores). Como os dados que importou contêm apenas os valores de vendas do último ano, Júlia muda o nome do campo **SalesAmount** (MontanteDeVendas) para *Last Years Sales* (Vendas do Ano Passado). Em seguida, arrasta **Last Years Sales** (Vendas do Ano Passado) para a tela de relatórios. Aparece numa visualização de gráfico como um valor único, que é a soma de todas as vendas dos revendedores do ano anterior.

Júlia repara que foi fornecido automaticamente um cálculo, embora não tenha especificado nenhum. O Power BI Desktop criou a sua própria medida ao somar todos os valores em **Last Years Sales** (Vendas do Ano Passado).

No entanto, Júlia precisa de uma medida para calcular as projeções de vendas para o próximo ano, que serão baseadas nas vendas do ano anterior multiplicadas por 1,06, para considerar o aumento de 6% esperado no negócio. Para este cálculo, Júlia criará uma medida. Ao utilizar a funcionalidade *Nova Medida*, cria uma nova medida e, em seguida, introduz a seguinte fórmula DAX:

```dax
    Projected Sales = SUM('Sales'[Last Years Sales])*1.06
```

Em seguida, Júlia arrasta a nova medida Projected Sales (Vendas Projetadas) para o gráfico.

![Elemento visual New Projected Sales](media/desktop-measures/measuresinpbid_lastyearsales.png)

Rapidamente e com o mínimo esforço, Júlia tem agora uma medida para calcular as vendas projetadas. Júlia também pode analisar as projeções ao filtrar revendedores específicos ou ao adicionar outros campos ao relatório.

## <a name="data-categories-for-measures"></a>Categorias de dados para medidas

Também pode selecionar categorias de dados para medidas.

As categorias de dados permitem-lhe, entre outras coisas, utilizar medidas para criar URLs dinamicamente e marcar a categoria de dados como um URL da Web.

Pode criar tabelas que apresentam as medidas como URLs da Web e pode clicar no URL criado com base na sua seleção. Esta abordagem é particularmente útil quando quer ligar a outros relatórios do Power BI com [parâmetros de filtro de URL](../collaborate-share/service-url-filters.md).

## <a name="organizing-your-measures"></a>Organizar as medidas

As medidas têm uma tabela *Principal* que define onde se encontram na lista de campos. Pode alterar a localização das medidas ao escolher uma localização nas tabelas no modelo.

![Selecionar uma tabela para a medida](media/desktop-measures/measures-03.png)

Também pode organizar os campos numa tabela nas *Pastas de Apresentação*. Selecione **Modelo** na extremidade esquerda do Power BI Desktop. No painel **Propriedades**, selecione o campo que pretende mover da lista de campos disponíveis. Introduza um nome para uma nova pasta na **Pasta de apresentação** para criar uma pasta. A criação de uma pasta move o campo selecionado para essa pasta.

![Criar um campo para as medidas](media/desktop-measures/measures-04.gif)

Pode criar subpastas com um caráter de barra invertida. Por exemplo, *Finanças\Moedas* cria uma pasta *Finanças* e, dentro, uma pasta *Moedas*.

Pode fazer com que um campo apareça em várias pastas com um ponto e vírgula para separar os nomes das pastas. Por exemplo, *Produtos\Nomes;Departamentos* faz com que o campo apareça numa pasta *Departamentos*, assim como uma pasta *Nomes* dentro de uma pasta *Produtos*.

Pode criar uma tabela especial que contenha apenas medidas. Esta tabela surge sempre na parte superior dos **Campos**. Para tal, crie uma tabela com apenas uma coluna. Pode utilizar **Introduzir Dados** para criar essa tabela. Em seguida, mova as medidas para essa tabela. Por fim, oculte a coluna (não a tabela) que criou. Selecione a seta na parte superior de **Campos** para fechar e reabrir a lista de campos, para ver as suas alterações.

![Organizar as medidas para as manter na parte superior da Lista de Campos](media/desktop-measures/measures-05.png)

## <a name="learn-more"></a>Saiba mais

Fornecemos apenas uma rápida introdução às medidas. Há muito mais para ajudá-lo a aprender como criar as suas. Para obter mais informações, veja [Tutorial: Criar as suas próprias medidas no Power BI Desktop](desktop-tutorial-create-measures.md). Pode transferir um ficheiro de exemplo e ver lições passo-a-passo sobre como criar mais medidas.  

Para saber mais sobre o DAX, consulte [Noções básicas do DAX no Power BI Desktop](desktop-quickstart-learn-dax-basics.md). A [Referência das Data Analysis Expressions](/dax/) fornece artigos detalhes sobre cada das funções, sintaxe, operadores e convenções de nomenclatura. O DAX já existe há muitos anos no Power Pivot no Excel e no SQL Server Analysis Services. Existem muitos outros excelentes recursos disponíveis. Certifique-se de que vê o [Wiki do Centro de Recursos do DAX](https://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), onde os membros influentes da comunidade de BI partilham os seus conhecimentos de DAX.
