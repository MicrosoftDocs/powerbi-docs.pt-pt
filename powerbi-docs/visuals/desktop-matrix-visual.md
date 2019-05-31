---
title: Utilizar o elemento visual Matriz no Power BI
description: Saiba como o elemento visual de matriz ativa esquemas graduais e realces granulares no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6ad8900e5a95148b3f8333aa1953cc939d56f0e6
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375480"
---
# <a name="use-the-matrix-visual-in-power-bi"></a>Utilizar o elemento visual Matriz no Power BI
O **matriz** visual é semelhante a um **tabela**.  Uma tabela suporta 2 dimensões e os dados são simples, valores duplicados do significado são apresentados e não agregados. Uma matriz torna mais fácil exibir dados de forma significativa em várias dimensões--ele oferece suporte a um esquema gradual. A matriz automaticamente agrega os dados e permite a exploração de baixo. 

Pode criar elementos visuais de matriz no **Power BI Desktop** e **serviço Power BI** relatórios e elementos de realce cruzado na matriz com outros elementos visuais nessa página de relatório. Por exemplo, pode selecionar linhas, colunas e células individuais e realce cruzado. Além disso, células individuais e múltiplas seleções de célula podem ser copiadas e coladas noutras aplicações. 

![cross matriz realçado e o gráfico em anel](media/desktop-matrix-visual/matrix-visual_2a.png)

Existem muitas funcionalidades associadas à matriz e vamos analisá-las nas secções seguintes deste artigo.


## <a name="understanding-how-power-bi-calculates-totals"></a>Compreender como o Power BI calcula os totais

Antes de avançar para a utilização do elemento visual **Matriz**, é importante compreender como o Power BI calcula os valores total e subtotal em tabelas e matrizes. Para as linhas total e subtotal, a medida é avaliada através de todas as linhas de dados subjacentes – *não* é apenas uma adição simples dos valores nas linhas visíveis ou apresentadas. Tal significa que pode ter valores diferentes do esperado na linha total. 

Veja os seguintes visuais de matriz. 

![compara as tabelas e matrizes](media/desktop-matrix-visual/matrix-visual_3.png)

Neste exemplo, cada linha da matriz visual mais à direita mostra a *quantidade* para cada combinação de data/vendedor. No entanto, uma vez que um representante de vendas é apresentado em várias datas, os números podem aparecer mais do que uma vez. Deste modo, o total exato dos dados subjacentes e uma simples adição de valores visíveis não são equivalentes. Trata-se de um padrão comum quando o valor que está a somar está de “um” lado de uma relação de um para muitos.

Quando observar totais e subtotais, lembre-se de que esses valores são baseados nos dados subjacentes e não apenas nos valores visíveis. 

<!-- use Nov blog post video

## Expanding and collapsing row headers
There are two ways you can expand row headers. The first is through the right-click menu. You’ll see options to expand the specific row header you clicked on, the entire level or everything down to the very last level of the hierarchy. You have similar options for collapsing row headers as well.

![](media/desktop-matrix-visual/power-bi-expand1.png)

You can also add +/- buttons to the row headers through the formatting pane under the row headers card. By default, the icons will match the formatting of the row header, but you can customize the icons’ color and size separately if you want. 
Once the icons are turned on, they work similarly to the icons from PivotTables in Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

The expansion state of the matrix will save with your report. It can be pinned to dashboards as well, but consumers will need to open up the report to change the state. Conditional formatting will only apply to the inner most visible level of the hierarchy. Note that this expand/collapse experience is not currently supported when connecting to AS servers older than 2016 or MD servers.

![](media/desktop-matrix-visual/power-bi-expand3.png)

Watch the following video to learn more about expand/collapse in the matrix:

-->
## <a name="using-drill-down-with-the-matrix-visual"></a>Usando o teste de para baixo com o elemento visual de matriz
Com o elemento visual de matriz, pode fazer todos os tipos de desagregação interessante de atividades que não estavam disponíveis anteriormente. Isto inclui a capacidade de desagregar com linhas, colunas e até em células e secções individuais. Vamos ver como funciona cada uma.

### <a name="drill-down-on-row-headers"></a>Desagregação em cabeçalhos de linha
No painel **Visualizações**, quando adicionar vários campos à secção **Linhas** de **Campos**, ativa a desagregação nas linhas do elemento visual de matriz. Isto é semelhante à criação de uma hierarquia que lhe permite desagregar (e, em seguida, efetuar cópias de segurança) através dessa hierarquia e analisar os dados em cada nível.

Na imagem seguinte, o **linhas** secção contém *fase de vendas* e *tamanho da oportunidade*, criar um agrupamento (ou hierarquia) nas linhas que podemos explorar.

![Cartão de filtros que mostra que linhas são escolhidas](media/desktop-matrix-visual/power-bi-rows-matrix.png)

Quando o elemento visual tem um agrupamento criado na secção **Linhas**, o elemento visual apresenta os ícones *agregar* e *expandir* no canto superior esquerdo do elemento visual.

![matriz de controlos de exploração descritos](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

Semelhante ao comportamento de desagregação e expansão noutros elementos visuais, a seleção desses botões permite-nos desagregar (ou efetuar cópias de segurança) através da hierarquia. Neste caso, podemos desagregar de *fase de vendas* ao *tamanho da oportunidade*, conforme mostrado na imagem seguinte, onde a desagregação no ícone de um nível (a forquilha) foi selecionada.

![matriz com forquilha descrita](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Além de utilizar estes ícones, pode selecionar qualquer um dos cabeçalhos de linha e desagregar ao selecionar o menu apresentado.

![Opções de menu para linhas na matriz](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Tenha em atenção que existem algumas opções no menu apresentado, mas que geram resultados diferentes:

Selecionando **desagregar** expande a matriz para *que* nível de linha e *excluindo* todos os outros cabeçalhos de linha, exceto o cabeçalho de linha que foi selecionado. Na imagem seguinte, **proposta** > **desagregar** tiver sido selecionada. Tenha em atenção que outras linhas de nível superior já não aparecem na matriz. Esta forma de explorar é uma funcionalidade útil e torna-se especialmente útil quando chegamos à secção **realce cruzado**.

![matriz de nível de detalhe para um nível](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Selecione o **agregar** ícone para voltar à vista de nível superior anterior. Se, em seguida, selecione **proposta** > **Mostrar nível seguinte**, obtém uma lista crescente de todos os itens do nível seguinte (neste caso, o *tamanho da oportunidade* campo), sem a categorização da hierarquia de nível superior.

![matriz com o próximo nível de Show](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Selecione o **agregar** ícone no canto superior esquerdo para que a matriz Mostrar todas as categorias de nível superior, em seguida, selecione **proposta** > **expandir para o próximo nível**ao ver todos os valores para ambos os níveis da hierarquia - *fase de vendas* e *tamanho da oportunidade*.

![matriz com o próximo nível de expansão](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

Também pode utilizar o **expandir** item de menu para controlar a exibição ainda mais.  Por exemplo, seleccione **proposta** > **expandir** > **seleção**. O Power BI apresenta uma linha de total para cada *fase de vendas* e todos os a *tamanho da oportunidade* opções de *proposta*.

![Matriz depois de aplicada a proposta de expansão](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Desagregação em cabeçalhos de coluna
Assim como a capacidade de fazer uma busca detalhada nas linhas, pode também desagregar **colunas**. Na imagem seguinte, existem dois campos no **colunas** poço de campo, criação de uma hierarquia semelhante à utilizada para as linhas anteriores neste artigo. Na **colunas** poço de campo, temos *região* e *segmento*. Assim que o segundo campo foi adicionado ao **colunas**, um novo menu pendente apresentado no elemento visual, atualmente mostra **linhas**.

![Matriz após o segundo valor da coluna adicionado](media/desktop-matrix-visual/power-bi-matrix-row.png)

Para fazer uma busca detalhada em colunas, selecione **colunas** partir a *desagregar em* menu que pode ser encontrado no canto superior esquerdo da matriz. Selecione o *Leste* região e escolha **desagregar**.

![menu de desagregação em colunas](media/desktop-matrix-visual/power-bi-matrix-column.png)

Quando seleciona **desagregar**, o próximo nível de hierarquia de coluna para *região > Leste* apresenta, que neste caso é *contagem de oportunidades*. A outra região apresenta, mas estiver a cinzento.

![matriz com coluna desagregar um nível](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

O resto dos itens de menu funcionam em colunas da mesma forma que para linhas (veja a secção anterior, **fazer uma busca detalhada em cabeçalhos de linha**). Pode **Mostrar nível seguinte** e **expandir para o próximo nível** com colunas, assim como com linhas.

> [!NOTE]
> Os ícones de desagregação e agregação na parte superior esquerda do elemento visual de matriz aplicam-se apenas a linhas. Para desagregação em colunas, tem de utilizar o menu de contexto.
> 
> 

## <a name="stepped-layout-with-matrix-visuals"></a>Esquema gradual com elementos visuais de matriz
O elemento visual **Matriz** avança automaticamente as subcategorias numa hierarquia por baixo de cada categoria principal, o que é designado por **Esquema gradual**.

Na versão *original* do elemento visual de matriz, as subcategorias foram mostradas numa coluna completamente diferente, o que ocupa muito mais espaço no elemento visual. A imagem seguinte mostra a tabela no elemento visual **Matriz** original. Repare nas subcategorias numa coluna separada.

![método antigo de formato padrão para matrizes](media/desktop-matrix-visual/matrix-visual_14.png)

Na imagem seguinte, verá um elemento visual **Matriz** com o **Esquema gradual** em ação. Tenha em atenção que a categoria *Computadores* tem as respetivas subcategorias (Acessórios de Computadores, Computadores de Secretária, Computadores Portáteis, Monitores, etc.) ligeiramente avançadas, o que fornece um elemento visual mais limpo e muito mais condensado.

![forma essa matriz formatos de dados atual](media/desktop-matrix-visual/matrix-visual_13.png)

Pode ajustar facilmente as definições do esquema gradual. Com o elemento visual **Matriz** selecionado, na secção **Formatar** (o ícone de rolo) do painel **Visualizações**, expanda a secção **Cabeçalhos de linha**. Tem duas opções: o seletor **Esquema gradual** (que ativa ou desativa) e o botão **Avanço de esquema gradual** (especifica a quantidade de avanço em pixéis).

![Cartão de cabeçalhos de linha a exibição de controle de esquema gradual](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Se desativar **Esquema gradual**, as subcategorias são apresentadas noutra coluna em vez de avanços por baixo da categoria principal.

## <a name="subtotals-with-matrix-visuals"></a>Subtotais com elementos visuais de matriz
Pode ativar ou desativar os subtotais nos elementos visuais de matriz para linhas e colunas. Na imagem seguinte, pode ver que os subtotais da linha estão **ativados**.

![matriz que mostra totais e subtotais](media/desktop-matrix-visual/matrix-visual_20.png)

Na secção **Formatar** do painel **Visualizações**, expanda o cartão **Subtotais** e coloque o controlo de deslize **Subtotais da linha** como **Desativado**. Quando o fizer, os subtotais não são apresentados.

![matriz com subtotais desativado](media/desktop-matrix-visual/matrix-visual_21.png)

É aplicado o mesmo processo aos subtotais da coluna.

## <a name="cross-highlighting-with-matrix-visuals"></a>Realce cruzado com elementos visuais de matriz
Com o elemento visual **Matriz**, pode selecionar quaisquer elementos na matriz como base para o realce cruzado. Selecione uma coluna numa **Matriz** e essa coluna fica realçada, como quaisquer outros elementos visuais na página de relatório. Este tipo de realce cruzado foi uma funcionalidade comum de outros elementos visuais e de seleções de ponto de dados, pelo que, agora o elemento visual **Matriz** oferece a mesma função.

Além disso, a combinação Ctrl+Clique também funciona no realce cruzado. Por exemplo, na imagem seguinte, foi selecionada uma coleção de subcategorias a partir do elemento visual **Matriz**. Repare como os itens que não foram selecionados a partir do elemento visual estão desativados e como os outros elementos visuais na página refletem as seleções efetuadas no elemento visual **Matriz**.

![relatório de página cruzada highighted por uma matriz](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Copiar valores do Power BI para utilizar noutras aplicações

A matriz ou a tabela pode ter conteúdos que quer utilizar noutras aplicações, como o Dynamics CRM, o Excel e até mesmo noutros relatórios do Power BI. Ao clicar com o botão direito do rato no Power BI, pode copiar uma única célula ou uma seleção de células para a área de transferência e colar noutra aplicação.

![opções de cópia](media/desktop-matrix-visual/power-bi-cell-copy.png)

* Para copiar o valor de uma única célula, selecione a célula, clique com o botão direito do rato e escolha **Copiar valor**. Com o valor da célula não formatado na área de transferência, pode agora colá-lo noutra aplicação.

    ![opções de cópia](media/desktop-matrix-visual/power-bi-copy.png)

* Para copiar mais do que uma célula, selecione um intervalo de células ou utilize CTRL para selecionar uma ou mais células. A cópia incluirá os cabeçalhos de coluna e de linha.

    ![colar no Excel](media/desktop-matrix-visual/power-bi-copy-selection.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Sombreado e cores de tipo de letra com elementos visuais de matriz
Com o elemento visual de matriz, pode aplicar **formatação condicional** (cores e barras de dados e sombreado) ao fundo das células na matriz bem como pode aplicar a formatação condicional para o texto e aos valores.

Para aplicar a formatação condicional, selecione a matriz visual e abra o **formato** painel. Expanda a **formatação condicional** cartão e, para **cor de fundo**, **cor da fonte**, ou **barras de dados**, ative o controlo de deslize para **No**. Ativando uma destas opções apresenta uma ligação para o *controlos avançados*, que permite personalizar as cores e os valores para a formatação de cor.
  
  ![Painel de formato mostra o controle de barras de dados](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Selecione *controlos avançados* para exibir uma caixa de diálogo, que lhe permite efetuar ajustes. Este exemplo mostra a caixa de diálogo **barras de dados**.

![Painel de barras de dados](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>Próximos passos

[Gráficos de dispersão e de bolhas no Power BI](power-bi-visualization-scatter.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)