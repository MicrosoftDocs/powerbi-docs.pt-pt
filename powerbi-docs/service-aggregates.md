---
title: "Agregações (soma, média, máximo, etc.) no Power BI"
description: "Alterar a agregação em um gráfico (soma, média, máximo, etc.) no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: modifying
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/23/2017
ms.author: mihart
ms.openlocfilehash: c1b926e129e8d82edd9c329a51623908c4e7c9e0
ms.sourcegitcommit: 8f72ce6b35aa25979090a05e3827d4937dce6a0d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2017
---
# <a name="aggregates-in-power-bi"></a>Agregações no Power BI
## <a name="what-is-an-aggregate"></a>O que é uma agregação?
Por vezes, pode querer combinar matematicamente os valores das linhas numa coluna. A operação matemática pode ser uma soma, média, máximo, contagem, etc. A operação de combinar o valor dos dados em linhas numa coluna denomina-se agregar. O resultado dessa operação matemática é um *agregado*. 

Um campo numérico é um valor que será agregado (somado ou cuja média será obtida, por exemplo) num campo categórico.  Por exemplo, "montante de vendas por produto" e "número de defeitos por região". Normalmente, os campos numéricos são denominados **medidas**. Na lista Campos, a medidas são mostradas com o símbolo ∑. Para obter mais informações, veja [O editor de relatório... Faça um tour](service-the-report-editor-take-a-tour.md).

Por vezes, uma *medida* é na verdade uma *medida calculada*. As medidas calculadas no Power BI são importadas com os dados (definidos no modelo de dados no qual o relatório se baseia). Cada medida calculada tem a sua própria fórmula codificada. Não é possível alterar a agregação utilizada; por exemplo, se for uma soma, esta só poderá ser uma soma. Na lista de Campos, as *medidas calculadas* são mostradas com o símbolo de calculadora. Para obter mais informações sobre como as medidas calculadas são criadas, consulte [Medidas no Power BI Desktop](desktop-measures.md).

Os campos categóricos não são numéricos, mas podem, ainda assim, ser agregados.  Quando os campos categóricos forem colocados num registo *exclusivamente numérico* como **Valores** ou **Descrições**, o Power BI pode contar as ocorrências de cada categoria ou contar as ocorrências diferentes de cada categoria.  Para cadeias e datas, o Power BI tem mais algumas opções de agregados: mais antigos, mais recentes, primeiros e últimos.  

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Por que é que os agregados não funcionam da forma que pretendo?
Trabalhar com agregados no serviço Power BI pode ser confuso; poderá ter um campo numérico e o Power BI não permitirá que altere a agregação. Pode também ter um campo, como um ano, que não pretenda agregar, mas apenas contar o número de ocorrências.

Na maioria das vezes, a origem do problema é a forma como o campo foi categorizado no conjunto de dados do Power BI. Talvez o campo esteja categorizado como texto, o que explica não se poder calcular a soma ou a média. Infelizmente, [apenas o proprietário do conjunto de dados pode alterar a forma como um campo é categorizado](desktop-measures.md).  

Para ajudá-lo a navegar nestes aspetos mais confusos, temos uma secção especial no final deste artigo, intitulada **Sugestões e resolução de problemas**.  Se não encontrar resposta aqui, publique a sua pergunta no [fórum de Comunidade do Power BI](http://community.powerbi.com) para obter uma resposta rápida diretamente da equipa do Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Mudar a forma como um campo numérico é agregado
Digamos que você tenha um gráfico que resume is dados de vendas de regiões diferentes, mas você prefere a média. 

1. Na vista de Edição do relatório, adicione a medida a uma visualização.
2. Encontre o campo no painel de visualizações, clique com o botão direito do mouse e selecione o tipo de agregação que você precisa. Se não vir a agregação de que precisa, contacte o proprietário do conjunto de dados. Pode haver um problema na forma como o campo foi categorizado pelo proprietário.  
   
   ![](media/service-aggregates/aggregate_new.png)
   
   > [!NOTE]
   > As opções disponíveis no menu pendente variam de acordo com 1) o campo selecionado e 2) a forma como esse campo foi categorizado pelo mesmo proprietário do conjunto de dados.
   > 
   > 

Algumas das opções que podem estar disponíveis para um campo de agregação:

* **Não resumir**. Com essa opção escolhida, cada valor nesse campo é tratada separadamente e não resumida. Isso geralmente é usado se você tiver uma coluna de ID numérica que não deve ser somada.
* **Soma**. Isso adiciona todos os valores nesse campo para cima.
* **Média**. Usa uma média aritmética dos valores.
* **Mínimo**. Mostra o menor valor.
* **Máximo**. Mostra o maior valor.
* **Contagem (Não em Branco).** Isso conta o número de valores no campo que não está em branco.
* **Contagem (Distinta).** Isso conta o número de valores diferentes no campo.
* **Desvio-padrão.**
* **Variação**.
* **Mediana**.  Mostra o valor mediano (meio). Esse é o valor que tem o mesmo número de itens acima e abaixo.  Se houver duas medianas, o Power BI obterá suas médias.

Por exemplo, esses dados:

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

* **Não resumir**: cada valor é exibido separadamente
* **Soma**: 750
* **Média**: 125
* **Máximo**: 150
* **Mínimo**: 100
* **Contagem (não em branco):** 6
* **Contagem (distinta):** 4
* **Desvio padrão:** 20.4124145...
* **Variação:** 416.666...
* **Mediana:** 125

## <a name="use-a-non-aggregated-field-as-a-numeric-field"></a>Usar um campo não agregado como um campo numérico
Você também pode usar um campo não agregado como um campo numérico. Por exemplo, se tiver um campo Nome do Produto, você poderá adicioná-lo como um valor e defini-lo como **Contagem** ou **Contagem distinta**. 

1. Por exemplo, se você selecionar **Loja > Rede**.
   
   ![](media/service-aggregates/count-of-chain-do_not_summarize.png)
2. E se você alterar a agregação do padrão **Não resumir** para **Contagem (Distinta)**, o Power BI contará o número de diferentes cadeias. Nesse caso, existem 2: Fashions Direct e Lindseys.
   
   ![](media/service-aggregates/aggregates_count.png)
3. Se você alterar a agregação para **Contagem**, o Power BI contará o número total. Nesse caso, há 104 entradas para **Cadeia**. Adicionando **Cadeia** como filtro, você pode ver que há 37 linhas para Fashions Direct e 67 para Lindseys.  
   
   ![](media/service-aggregates/count_of_chain_104.png)

## <a name="tips-and-troubleshooting"></a>Sugestões e Resolução de Problemas
P:  Por que não tenho uma opção de **Não resumir**?

R: Provavelmente, o campo que selecionou é uma medida calculada. Lembre-se de que cada medida calculada tem a sua própria fórmula codificada. Não pode alterar o cálculo.

P:  O meu campo **é** numérico, por que é que só tenho as opções de **Contagem** e **Contagem distinta**?

R: Provavelmente, tal acontece porque o proprietário do conjunto de dados, acidental ou intencionalmente, *não* classificou o campo como um número. Por exemplo, se um conjunto de dados for um campo de **ano**, o proprietário do conjunto de dados poderá categorizá-lo como texto porque é mais provável que o campo **ano** seja contabilizado (por exemplo, número de pessoas nascidas em 1974) e que não seja calculada a sua soma ou média. Se for proprietário, pode abrir o conjunto de dados no Power BI Desktop e utilizar o separador **Modelação** para alterar o tipo de dados.  

R: Também é possível que tenha deixado o campo num *registo* que apenas permite valores categóricos.  Nesse caso, as suas únicas opções serão a contagem e a contagem distinta.

R: A terceira hipótese é estar a utilizar o campo para um eixo. No eixo de um gráfico de barras, por exemplo, o Power BI mostra uma barra para cada valor distinto; não agrega os valores dos campos. 

>[!NOTE]
>A exceção a esta regra são os gráficos de dispersão, que *requerem* valores agregados para os eixos X e Y.


P: Tenho um diagrama de dispersão e quero que o meu campo *não* agregue.  Como o posso fazer?

R: Adicione o campo ao registo **Detalhes** e não aos registos dos eixos X e Y.

P: Quando adiciono campos numéricos a uma visualização, a maioria dos mesmos ficam predefinidos como soma, mas outros ficam predefinidos como média, contagem ou outra agregação.  Por que é que a agregação predefinida não é sempre a mesma?

R: Os proprietários de conjuntos de dados têm a opção de predefinir o resumo para cada campo. Se for um proprietário de conjunto de dados, altere o resumo predefinido no separador **Modelação** do Power BI Desktop.

P: O meu campo **é** numérico, por que não tenho opções de agregados no menu pendente?

R: Se o campo tiver um ícone de calculadora, significa que é uma *medida calculada* e cada medida calculada tem a sua própria fórmula codificada que não pode ser alterada no serviço Power BI. O cálculo utilizado pode ser uma agregação simples, como uma soma ou uma média, mas pode também ser algo mais complicado, como uma "percentagem de contributo para categoria principal" ou um "total desde início do ano". O Power BI não vai calcular a soma ou a média dos resultados; vai recalcular (com a fórmula codificada) para cada ponto de dados.

P: Sou um proprietário de conjunto de dados e quero garantir que um campo nunca é agregado.

R: No Power BI Desktop, no separador **Modelação**, defina **Tipo de dados** como **Texto**.

P: Não vejo a opção **Não resumir** no meu menu pendente.

R: Experimente remover o campo e voltar a adicioná-lo.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

