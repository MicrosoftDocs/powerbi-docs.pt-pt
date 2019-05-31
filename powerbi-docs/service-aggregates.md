---
title: Trabalhar com agregados (soma, média etc.) no serviço Power BI
description: Saiba como alterar a agregação num gráfico (soma, média, máximo e assim por diante.) no serviço Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710716"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Trabalhar com agregados (soma, média etc.) no serviço Power BI

## <a name="what-is-an-aggregate"></a>O que é um agregado?

Por vezes, pode querer combinar matematicamente valores nos seus dados. A operação matemática pode ser soma, média, máximo, contagem e assim por diante. Ao combinar valores nos seus dados, ele é chamado *agregar*. O resultado dessa operação matemática é um *agregado*.

Quando o serviço Power BI e o Power BI Desktop criam visualizações, podem agregar os seus dados. Muitas vezes, a agregação é exatamente aquilo de que precisa, mas outras vezes poderá querer agregar os valores de outra forma.  Por exemplo, uma soma versus uma média. Existem várias formas diferentes de gerir e alterar a agregação que utiliza o Power BI numa visualização.

Em primeiro lugar, vamos dar uma olhada no data *tipos* porque o tipo de dados determina como e se, o Power BI pode agregá-lo.

## <a name="types-of-data"></a>Tipos de dados

A maioria das bases de dados tem mais do que um tipo de dados. Nível mais básico, os dados são numéricos ou de não é. Power BI pode agregar dados numéricos, usando uma soma, média, contagem, mínimo, desvio e muito mais. O serviço pode até mesmo agregar dados textuais, frequentemente denominados *categóricos* dados. Se tentar agregar um campo categórico ao colocá-lo num bucket apenas numéricos, como **valores** ou **descrições**, Power BI irá contar as ocorrências de cada categoria ou contar as ocorrências diferentes de cada categoria. Tipos especiais de dados, como as datas, têm algumas de suas próprias opções de agregados: mais antigo, mais recentes, primeiros e últimos.

No exemplo abaixo:

- **Unidades Vendidas** e **Preço de Fabrico** são colunas que contêm dados numéricos

- **Segmento**, **País**, **Produto**, **Mês** e **Nome do Mês** contêm dados categóricos

   ![Captura de ecrã de um conjunto de dados de exemplo.](media/service-aggregates/power-bi-aggregate-chart.png)

Ao criar uma visualização no Power BI, o serviço vai irá agregar campos numéricos (a predefinição é *soma*) num campo categórico.  Por exemplo, "unidades vendidas ***por produto***", "unidades vendidas ***por mês***" e "preço de fabrico ***por segmento***". Power BI se refere a alguns campos numéricos como **medidas**. É fácil identificar medidas no editor de relatório do Power BI – a **campos** lista mostra medidas com o símbolo ∑ junto a eles. Consulte [o editor de relatórios... Faça uma visita guiada](service-the-report-editor-take-a-tour.md) para obter mais informações.

![Captura de ecrã do Power BI com a lista de campos destacada.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Por que é que os agregados não funcionam da forma que pretendo?

Trabalhar com agregados no Power BI service pode ser confuso. Talvez tenha um campo numérico e o Power BI não permitirá que altere a agregação. Pode também ter um campo, como um ano, que não pretenda agregar, mas apenas contar o número de ocorrências.

Normalmente, o problema subjacente é a definição de campo no conjunto de dados. Talvez o proprietário de conjunto de dados definido o campo como texto e que explica por que Power BI não é a soma ou a média-lo. Infelizmente, [apenas o proprietário do conjunto de dados pode alterar a forma como um campo é categorizado](desktop-measures.md). Portanto, se tiver permissões de proprietário do conjunto de dados, na área de trabalho ou o programa utilizado para criar o conjunto de dados (por exemplo, o Excel), pode corrigir este problema. Caso contrário, precisará de contactar o proprietário do conjunto de dados para obter ajuda.  

Existe uma secção especial no final deste artigo, intitulada [ **considerações e resolução de problemas**](#considerations-and-troubleshooting). Ele fornece orientações e sugestões. Se não encontrar resposta aqui, publique a sua pergunta sobre o [fórum da Comunidade do Power BI](http://community.powerbi.com). Obterá uma resposta rápida diretamente da equipa do Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Mudar a forma como um campo numérico é agregado

Suponhamos que tem um gráfico que soma as unidades vendidas de produtos diferentes, mas prefere ter a média.

1. Criar uma **gráfico de colunas agrupadas** que utiliza uma medida e uma categoria. Neste exemplo, estamos a utilizar Unidades Vendidas por Produto.  Por predefinição, o Power BI cria um gráfico que soma as unidades vendidas (arraste a medida para o **valor** bem) para cada produto (arrastar a categoria para o **eixo** bem).

   ![Captura de ecrã do gráfico, o painel de visualizações e lista de campos com soma chamado.](media/service-aggregates/power-bi-aggregate-sum.png)

1. Na **visualizações** painel, clique com o botão direito a medida e selecione o tipo de agregação que necessita. Neste caso, selecionamos **média**. Se não vir a agregação de que precisa, veja a [ **considerações e resolução de problemas** ](#considerations-and-troubleshooting) secção.

   ![Captura de ecrã da lista de agregação com média selecionado e destacados.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > As opções disponíveis na lista pendente variam de acordo com 1) o campo selecionado e 2) a forma como o proprietário de conjunto de dados categorizado esse campo.

1. Agora, a sua visualização está a utilizar a agregação por média.

   ![Captura de ecrã do gráfico agora exibindo a média de unidades vendidas por produto.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Formas de agregar os seus dados

Algumas das opções que podem estar disponíveis para a agregação de um campo:

- **Não resumir**. Com esta opção escolhida, o Power BI trata cada valor nesse campo separadamente e não resumi-los. Utilize esta opção se tiver uma coluna de ID numérica que o serviço não deve somar.

- **Soma**. Adiciona todos os valores nesse campo para cima.

- **Média**. Usa uma média aritmética dos valores.

- **Mínimo**. Mostra o menor valor.

- **Máximo**. Mostra o maior valor.

- **Contagem (Não em Branco).** Conta o número de valores nesse campo que não estão em branco.

- **Contagem (Distinta).** Conta o número de valores diferentes nesse campo.

- **Desvio-padrão.**

- **Desvio**.

- **Mediana**.  Mostra o valor mediano (meio). Este valor tem o mesmo número de itens acima e abaixo.  Se existirem duas medianas, o Power BI obterá a média delas.

Por exemplo, estes dados:

| País | Quantidade |
|:--- |:--- |
| EUA |100 |
| REINO UNIDO |150 |
| Canadá |100 |
| Alemanha |125 |
| França | |
| Japão |125 |
| Austrália |150 |

Daria os seguintes resultados:

- **Não Resumir**: Cada valor é apresentado separadamente

- **Soma**: 750

- **Média**: 125

- **Máximo**:  150

- **Mínimo**: 100

- **Contagem (Não em Branco):** 6

- **Contagem (Distinta):** 4

- **Desvio padrão:** 20,4124145...

- **Desvio:** 416,666...

- **Mediana:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Criar uma agregação com um campo categórico (de texto)

Também pode agregar um campo não numérico. Por exemplo, se tiver um campo com o nome do produto, poderá adicioná-lo como um valor e defini-lo como **Contagem**, **Contagem distinta**, **Primeiro** ou **Último**.

1. Arrastar o **produto** campo para o **valores** bem. O **valores** bem é normalmente utilizado para campos numéricos. O Power BI reconhece que este campo é um campo de texto, define o agregado para **não resumir**e apresenta uma tabela de coluna única.

   ![Captura de ecrã do campo produto os valores bem.](media/service-aggregates/power-bi-aggregate-value.png)

1. Se alterar a agregação da predefinição **não resumir** ao **contagem (distinta)** , Power BI contará o número de produtos diferentes. Neste caso, há quatro.
  
   ![Captura de ecrã da contagem distinta de produtos.](media/service-aggregates/power-bi-aggregate-count.png)

1. Se alterar a agregação para **Contagem**, o Power BI contará o número total. Neste caso, existem sete entradas para **produto**.

   ![Captura de ecrã da contagem de produtos.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Ao arrastar o mesmo campo (neste caso **produto**) para o **valores** bem e deixarmos a agregação predefinida **não resumir**, Power BI divide a contagem por produto.

   ![Captura de ecrã do produto e a contagem de produtos.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e Resolução de Problemas

P:  Por que não tenho uma opção de **Não resumir**?

R:  É possível que o campo que selecionou seja uma medida calculada ou uma medida avançada criada no Excel ou no [Power BI Desktop](desktop-measures.md). Cada medida calculada tem a sua própria fórmula codificada. Não é possível alterar a agregação que utiliza o Power BI. Por exemplo, se for uma soma, só poderá ser uma soma. O **campos** lista mostra *medidas calculadas* com o símbolo de calculadora.

P:  O meu campo **é** numérico, por que é que só tenho as opções de **Contagem** e **Contagem distinta**?

R1:  Provavelmente é o proprietário do conjunto de dados *não* classificou o campo como um número. Por exemplo, se um conjunto de dados tem um **ano** campo, o proprietário de conjunto de dados poderá categorizá-o valor como texto. É mais provável que o Power BI contará o **ano** campo (por exemplo, o número de pessoas nascidas em 1974). É menos provável que o Power BI irá soma ou média-lo. Se for o proprietário, pode abrir o conjunto de dados no Power BI Desktop e utilizar o **modelagem** separador para alterar o tipo de dados.

R2: Se o campo tiver um ícone de calculadora, significa que é um *medida calculada*. Cada medida calculada tem sua própria fórmula codificada que só o proprietário do conjunto de dados pode ser alterado. O cálculo do que Power BI utiliza pode ser uma agregação simple, como uma soma ou média. Também pode ser algo mais complicado, como uma "percentagem de contributo para categoria principal" ou "total desde início do ano". Power BI não irá a soma ou média dos resultados. Em vez disso, ele apenas recalculará (usando a fórmula codificada) para cada ponto de dados.

R3:  Também é possível que tenha deixado o campo num *registo* que apenas permite valores categóricos.  Nesse caso, as suas únicas opções serão a contagem e a contagem distinta.

R4:  E a hipótese de quarta é o que está a utilizar o campo para um eixo. No eixo de um gráfico de barras, por exemplo, o Power BI mostra uma barra para cada valor distinto; não agrega os valores dos campos.

>[!NOTE]
>A exceção a esta regra são os gráficos de dispersão, que *requerem* valores agregados para os eixos X e Y.

P:  Por que motivo não consigo agregar os campos de texto das origens de dados do SQL Server Analysis Services (SSAS)?

R:  As ligações dinâmicas a modelos multidimensionais do SSAS não permitem agregações do lado do cliente, incluindo as seguintes: primeiro, último, média, mínimo, máximo e soma.

P:  Tenho um gráfico de dispersão e quero que o meu campo *não* agregue.  Como posso fazê-lo?

R:  Adicione o campo ao registo **Detalhes** e não aos registos dos eixos X e Y.

P:  Quando adiciono campos numéricos a uma visualização, a maioria dos mesmos ficam predefinidos como soma, mas outros ficam predefinidos como média, contagem ou outra agregação.  Por que é que a agregação predefinida não é sempre a mesma?

R:  Os proprietários de conjunto de dados podem predefinir o resumo para cada campo. Se for um proprietário de conjunto de dados, altere o resumo predefinido no **modelagem** separador do Power BI Desktop.

P:  Sou um proprietário de conjunto de dados e quero garantir que um campo nunca é agregado.

R:  No Power BI Desktop, no separador **Modelação**, defina **Tipo de dados** como **Texto**.

P:  Não vejo **não resumir** como uma opção na minha lista pendente.

R:  Experimente remover o campo e voltar a adicioná-lo.

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)