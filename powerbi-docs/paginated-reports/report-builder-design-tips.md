---
title: Sugestões de estrutura de relatórios no Report Builder do Power BI
description: Utilize as seguintes sugestões para ajudar a estruturar os relatórios paginados no Report Builder do Power BI.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 13b9e37d4a64493dfdcac02d9df86a1e19a1c24b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921177"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Sugestões de estrutura de relatórios no Report Builder do Power BI
  Utilize as seguintes sugestões para ajudar a estruturar os relatórios paginados no Report Builder do Power BI.  
  
   
  
##  <a name="designing-reports"></a><a name="DesigningReports"></a> Estruturação de relatórios  
  
-   Um relatório bem estruturado transmite informações que conduzem à ação. Identifique as perguntas a que o relatório ajuda a responder. Tenha essas perguntas em mente quando estruturar o relatório.  
  
-   Para estruturar visualizações de dados eficazes, pense numa forma de apresentação de informações que seja fácil para o utilizador de relatórios compreender. Escolha uma região de dados que seja adequada para os dados que pretende visualizar. Por exemplo, um gráfico transmite eficazmente resumos e informações agregadas melhor do que uma tabela que ocupa várias páginas de informações detalhadas. Pode visualizar dados a partir de um conjunto de dados em qualquer região de dados, que inclua gráficos, mapas, indicadores, gráficos sparkline, barras de dados e dados tabulares em vários esquemas de grelha com base num tablix. 
  
-   Se quiser entregar o relatório num formato de exportação específico, teste o formato de exportação antecipadamente na sua estrutura. O suporte de funcionalidades varia com base no compositor que escolher.  
  
-   Ao criar esquemas complexos, crie o esquema por fases. Pode utilizar retângulos como contentores para organizar os itens de relatório. Pode criar regiões de dados diretamente na superfície da estrutura de modo a maximizar a sua área de trabalho e, à medida que conclui cada uma delas, arrastá-la para o contentor retangular. Ao utilizar retângulos como contentores, pode posicionar todos os conteúdos num único passo. Os retângulos também ajudam a controlar a forma como os itens de relatório são compostos em cada página.  
  
-   De modo a reduzir a desorganização num relatório, considere a utilização de visibilidade condicional para itens de relatório específicos e permita que o utilizador selecione se quer apresentar os itens. Pode definir a visibilidade com base num parâmetro ou numa alternância de caixa de texto. Pode adicionar caixas de texto condicionalmente ocultas para mostrar os resultados de expressão provisórios. Quando um relatório apresenta dados inesperados, pode mostrar esses resultados provisórios para ajudar a depurar as expressões.  
  
-   Ao trabalhar com itens aninhados em células ou retângulos de tablix, pode definir diferentes cores de fundo para o contentor e itens contidos. Por predefinição, a cor de fundo é **Sem cor**. Os itens com uma cor de fundo específica transparecem através de itens com uma cor de fundo definida como **Sem cor**. Esta técnica pode ajudá-lo a selecionar o item correto para definir as propriedades de visualização, como a visibilidade do limite em células de tablix.  
  
 Para obter mais informações sobre o que deve ter em consideração ao estruturar o seu relatório, veja [Planear um Relatório no Report Builder](report-builder-planning-report.md)).  
  
##  <a name="naming-conventions-for-reports-data-sources-and-datasets"></a><a name="NamingConventions"></a> Convenções de nomenclatura para relatórios, origens de dados e conjuntos de dados  
  
-   Utilize as convenções de nomenclatura para origens de dados e conjuntos de dados que documentem a origem dos dados.  
  
    1.  **Origens de dados.** Se não quiser utilizar um servidor ou base de dados real por motivos de segurança, utilize um alias que indique ao utilizador qual a origem dos dados.  
  
    2.  **Conjuntos de dados.** Utilize um nome que indique a origem de dados em que se baseia.  
  
##  <a name="working-with-data"></a><a name="Data"></a>Trabalhar com dados  
  
-   Em primeiro lugar, faça com que todos os dados com que pretende trabalhar apareçam no painel Dados do Relatório. Ao refinar as perguntas para as quais o relatório foi estruturado para responder, pense em como limitar os dados nos conjuntos de dados de relatórios para apenas os que são necessários.  
  
-   Em geral, inclua apenas os dados que irá apresentar num relatório. Utilize variáveis de consulta nas suas consultas de conjuntos de dados para permitir que o utilizador selecione quais os dados que pretende ver no relatório. Se estiver a criar conjuntos de dados partilhados, forneça filtros com base nos parâmetros de relatório para fornecer a mesma funcionalidade.  
  
-   Se for um autor de consultas experiente, compreenda que, para quantidades de dados intermédias, poderá ser aconselhável agrupar os dados no relatório e não na consulta. Se fizer todos os agrupamentos na consulta, o relatório tende a ser uma apresentação do conjunto de resultados da consulta. Por outro lado, para apresentar valores agregados para grandes quantidades de dados num gráfico ou matriz, não é necessário incluir dados detalhados.  
  
-   Dependendo dos requisitos, pode apresentar os nomes e localizações das origens de dados de relatório, o texto do comando de consulta do conjunto de dados e os valores de parâmetros no relatório. A primeira pergunta colocada por muitos novos utilizadores tem a ver com a origem dos dados. De modo a reduzir a desorganização no relatório, pode ocultar condicionalmente as caixas de texto com este tipo de informações e permitir que os utilizadores escolham se querem vê-las. Experimente adicionar estas informações na última página do relatório. Defina a visibilidade da caixa de texto com base num parâmetro que o utilizador possa alterar.  
  
##  <a name="interacting-with-the-report-design-surface"></a><a name="DesignSurface"></a> Interagir com a superfície da estrutura do relatório  
 A superfície da estrutura do relatório não é WYSIWIG. Ao colocar os itens de relatório na superfície da estrutura, a sua localização relativa afeta a forma como os itens são apresentados na página de relatório composto. O espaço em branco é preservado.  
  
-   Utilize botões de esquema e linhas de ajuste para alinhar e organizar os itens na superfície da estrutura do relatório. Por exemplo, pode alinhar as margens superiores ou margens de itens selecionados, expandir um item de acordo com o tamanho de outro item ou ajustar o espaçamento entre itens.  
  
-   Utilize as teclas de seta para ajustar a posição e o tamanho dos itens selecionados na superfície da estrutura. Por exemplo, as seguintes combinações de teclas são muito úteis:  
  
    -   **Teclas de Seta** Mover o item de relatório selecionado.  
  
    -   **Ctrl+Teclas de Seta** Deslocar o item de relatório selecionado.  
  
    -   **Ctrl+Shift+Teclas de Seta** Aumentar ou diminuir o tamanho do item de relatório selecionado.  
  
-   Para adicionar um item a um retângulo, utilize a extremidade superior esquerda do rato para apontar para a localização inicial do item no contentor do retângulo. Utilize atalhos de teclado para ajudar a posicionar os objetos selecionados. O retângulo expande-se automaticamente para acomodar o tamanho dos itens contidos.  
  
-   Para adicionar múltiplos itens a uma célula de tablix, primeiro adicione um retângulo e, em seguida, adicione os itens.  
  
     Por predefinição, cada célula de tablix contém uma caixa de texto. Quando adiciona um retângulo a uma célula, o retângulo substitui a caixa de texto. Por exemplo, coloque indicadores aninhados num retângulo numa célula de tablix para ajudar a controlar a forma como o tamanho de um gráfico ou um indicador se expande à medida que altera a altura da linha onde se encontra a célula.  
  
-   Utilize o controlo de **Zoom** para ajustar a sua visualização da superfície da estrutura. Pode trabalhar com a página inteira ou com secções menores da página.  
  
-   Para arrastar campos do painel Dados do Relatório para o painel Agrupamento, evite arrastar o campo por outros itens de relatório na superfície da estrutura, uma vez que isto seleciona os outros itens e desseleciona a região de dados de tablix. Arraste o campo para baixo no painel Dados do Relatório e, em seguida, para o painel Agrupamento.  
  
###  <a name="selecting-items"></a><a name="Selecting"></a> Selecionar itens  
 Para ajudar a selecionar o objeto que pretende na superfície da estrutura do relatório, utilize a tecla Esc, o menu de contexto, o painel Propriedades e o painel Agrupamento.  
  
-   -   Prima Esc para percorrer a pilha de itens de relatório que ocupam o mesmo espaço na superfície da estrutura.  
  
    -   Em alguns itens de relatório, experimente utilizar o menu de contexto para selecionar o item de relatório ou a parte do item de relatório que pretende.  
  
    -   O painel Propriedades mostra as propriedades da seleção atual.  
  
    -   Para trabalhar com grupos de linhas e grupos de colunas numa região de dados de tablix, selecione o grupo a partir do painel Agrupamento.  

  
##  <a name="working-with-specific-types-of-report-items"></a><a name="ReportItems"></a> Trabalhar com tipos específicos de itens de relatório  
  
###  <a name="working-with-parameters"></a><a name="Parameters"></a> Trabalhar com parâmetros  
  
-   A principal finalidade dos parâmetros de relatórios é filtrar os dados na origem de dados e recuperar apenas o que é necessário para efeitos de relatório.  
  
-   Para os parâmetros de relatório, encontre um equilíbrio entre permitir a interatividade e ajudar um utilizador a obter os resultados que pretende. Por exemplo, pode definir valores predefinidos para um parâmetro para valores que sabe que são populares.  
  
###  <a name="working-with-text"></a><a name="Text"></a> Trabalhar com texto  
  
-   Ao colar várias linhas numa caixa de texto, o texto é adicionado como uma execução de texto. Cada execução de texto só pode ser formatada como uma unidade. Para formatar cada linha de forma independente, insira uma nova linha ao premir Enter na execução de texto, conforme necessário. Em seguida, pode aplicar estilos e formatação a cada linha de texto independente na caixa de texto.  
  
-   Pode definir propriedades de formato e ações numa caixa de texto ou em texto de marcador de posição na caixa de texto. Se existir apenas uma linha de texto, é mais eficaz definir as propriedades da caixa de texto e não do texto.  
  
###  <a name="working-with-expressions"></a><a name="Expressions"></a> Trabalhar com expressões  
  
-   Compreenda formatos de expressão simples e complexos. Pode escrever o formato de expressão simples diretamente nas caixas de texto, as propriedades no painel Propriedade ou em localizações nas caixas de diálogo que aceitem uma expressão.
  
-   Ao criar uma expressão, esta ajuda a criar cada parte de forma independente e verifica o respetivo valor. Em seguida, pode combinar todas as partes numa expressão final. Uma técnica útil é adicionar uma caixa de texto numa célula de matriz, apresentar cada parte da expressão e definir a visibilidade condicional na caixa de texto. Para controlar o estilo e a cor do limite quando a caixa de texto está oculta, primeiro coloque a caixa de texto num retângulo e, em seguida, defina o estilo e a cor do limite do retângulo de acordo com a matriz.  
  
###  <a name="working-with-indicators"></a><a name="Indicators"></a> Trabalhar com indicadores  
  
-   Por predefinição, um indicador mostra pelo menos três estados. Depois de adicionar um indicador a um relatório, pode configurá-lo ao adicionar ou remover estados. Para facilitar a visualização pelos seus utilizadores, selecione um indicador que varie de acordo com a cor e a forma.  
  
##  <a name="controlling-the-rendering-of-report-items-on-the-report-page"></a><a name="Rendering"></a> Controlar a composição dos itens de relatório na página de relatório  
  
-   Na superfície da estrutura do relatório, os itens de relatório aumentam para acomodar os conteúdos do conjunto de dados, expressão, sub-relatório ou texto associado.  
  
    -   Ao posicionar um item na página de relatório, a distância entre o item e todos os itens que começam à direita desse item torna-se a distância mínima que tem de ser mantida quando um item de relatório aumenta na horizontal. Da mesma forma, a distância entre um item e o item acima torna-se a distância mínima que deve ser mantida à medida que o item superior aumenta na vertical.  
  
    -   Um item num relatório aumenta para acomodar os dados e retira itens semelhantes (itens dentro do mesmo contentor principal) do caminho com as seguintes regras:  
  
    -   Cada item desloca-se para baixo para manter o espaço mínimo entre ele próprio e os itens que terminem acima do mesmo.  
  
    -   Cada item desloca-se para a direita para manter o espaço mínimo entre ele próprio e os itens que terminem à esquerda do mesmo. Para sistemas com esquemas da direita para a esquerda, cada item move-se para a esquerda para manter o espaço mínimo entre ele próprio e os itens que terminem à direita do mesmo.  
  
    -   Os contentores aumentam para acomodar o crescimento de itens subordinados. Para um item selecionado, no painel Propriedades, a propriedade Principal identifica o contentor para o item. Também pode utilizar o painel Contorno do Documento para ver a hierarquia de contenção de itens de relatório.  
  
    -   A barra de ferramentas **Esquema** fornece múltiplos botões para ajudar a alinhar as margens, os centros e o espaçamento para itens de relatório. Para ativar a barra de ferramentas **Esquema**, a partir do menu **Ver**, aponte para **Barras de Ferramentas** e, em seguida, clique em **Esquema**.  
  
-   Se quiser guardar o relatório como um ficheiro .pdf, a largura do relatório tem de ser explicitamente definida como um valor que apresente os resultados que pretende no formato de ficheiro de exportação. Por exemplo, defina a largura da página de relatório para exatamente 7,9375 polegadas e as margens esquerda e direita para 0,5 polegadas.  
  
-   Utilize **Esquema de Impressão** e **Configuração da Página** na barra de ferramentas do visualizador de relatórios para compor um relatório numa vista compatível com a impressão. Para ajudar a remover páginas em branco desnecessárias, faça o seguinte:  
  
    1.  Remova todos os espaços em branco adicionais entre regiões de dados e nas margens do relatório.  
  
    2.  Reduza as margens da página na caixa de diálogo **Propriedades do Relatório**.  
  
    3.  Utilize **Retângulos** como contentores para ajudar a controlar a forma como os itens de relatório são compostos.  
  
    4.  Nos cabeçalhos de coluna, altere a propriedade da caixa de texto WritingMode para utilizar texto vertical.  

 Para obter mais orientações, veja [Avoid blank pages when printing paginated reports](../guidance/report-paginated-blank-page.md) (Evitar páginas em branco ao imprimir relatórios paginados).

 Este comportamento, as propriedades de largura e altura dos itens de relatório, o tamanho do corpo do relatório, a definição de largura e altura da página, as definições de margem do relatório principal e o suporte específico do compositor para paginação combinam-se para determinar que itens de relatório se conjugam numa página composta.
 
## <a name="next-steps"></a>Próximas etapas

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
