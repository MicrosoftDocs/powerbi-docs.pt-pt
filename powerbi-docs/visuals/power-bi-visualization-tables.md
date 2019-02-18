---
title: Visualizações de tabela em relatórios e dashboards do Power BI
description: Tutorial para trabalhar com visualizações de tabela em relatórios e dashboards do Power BI, incluindo como redimensionar a largura das colunas.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0106c59c5fc4d122205a144d85a6e7f643c5a429
ms.sourcegitcommit: 80961ace38ff9dac6699f81fcee0f7d88a51edf4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56223404"
---
# <a name="tables-in-power-bi-reports-and-dashboards"></a>Tabelas em relatórios e dashboards do Power BI
Uma tabela é uma grelha que contém dados relacionados numa série lógica de linhas e colunas. Também pode conter cabeçalhos e uma linha para totais. As tabelas funcionam bem com comparações quantitativas, onde pode observar vários valores para uma única categoria. Por exemplo, esta tabela apresenta 5 medidas diferentes para **Categoria**.

![](media/power-bi-visualization-tables/table.png)

Crie tabelas em relatórios e realça de forma cruzada os elementos na tabela com outros elementos visuais na mesma página do relatório.  Além disso, pode selecionar linhas, colunas, células individuais e realces cruzados. Pode copiar e colar células individuais e múltiplas seleções de célula noutras aplicações.

## <a name="when-to-use-a-table"></a>Quando utilizar uma tabela
As tabelas são uma excelente opção:

* para ver e comparar dados detalhados e valores exatos (em vez de representações visuais)
* para apresentar dados num formato tabular
* para apresentar dados numéricos por categorias   

> [!NOTE]
> Se uma tabela tiver demasiados valores, considere convertê-la numa matriz e/ou utilizar desagregação. O máximo de pontos de dados que a tabela irá apresentar é 3500.

## <a name="prerequisites"></a>Pré-requisitos
- Serviço Power BI ou Power BI Desktop
- Exemplo de Análise de Revenda

## <a name="create-a-table"></a>Criar uma tabela
Vamos criar a tabela ilustrada acima para apresentar os valores de vendas por categoria de item. Para acompanhar, inicie sessão no serviço Power BI, selecione **Obter Dados \> Exemplos \> Exemplo de Análise de Revenda > Ligar** e selecione **Ir para o dashboard**. A criação de uma visualização exige permissões de edição para o conjunto de dados e para o relatório. Felizmente, todos os exemplos do Power BI são editáveis. Se um relatório tiver sido partilhado consigo, não poderá criar visualizações nos relatórios.

1. No painel de navegação esquerdo, selecione **Áreas de trabalho > A minha área de trabalho**.    
2. Selecione o separador Conjuntos de dados e desloque o ecrã para baixo até ao conjunto de dados Exemplo de Análise de Revenda que acabou de adicionar.  Selecione o ícone **Criar relatório**.

    ![ícone a apontar para o relatório](media/power-bi-visualization-tables/power-bi-create-report.png)
2. No editor de relatórios, selecione **Item** > **Categoria**.  O Power BI cria automaticamente uma tabela que apresenta uma lista de todas as categorias.

    ![resultado da adição de categoria](media/power-bi-visualization-tables/power-bi-table1.png)
3. Selecione **Vendas > Preço Unitário Médio** e **Vendas > Vendas do Último Ano** e **Vendas > Vendas Deste Ano** e escolha todas as 3 opções (Valor, Objetivo, Estado).   
4. No painel Visualizações, localize a área **Valores** e arraste e largue os valores até que a ordem das colunas do gráfico corresponda à primeira imagem desta página.  A área Valores deverá ser semelhante à seguinte.

    ![Área valores](media/power-bi-visualization-tables/power-bi-table2.png)
5. Afixe a tabela ao dashboard, selecionando o ícone de pin  

     ![pionés](media/power-bi-visualization-tables/pbi_pintile.png)

## <a name="format-the-table"></a>Formatar a tabela
Existem várias formas de formatar uma tabela e vamos apenas abordar algumas delas aqui. Uma excelente forma de saber mais sobre as outras opções de formatação é abrir o painel de Formatação (ícone de rolo de pintura ![rolo de pintura](media/power-bi-visualization-tables/power-bi-format.png)) e explorar.

* Experimente formatar a grelha da tabela. Aqui, adicionámos uma grelha vertical azul, adicionámos espaço às linhas, aumentámos um pouco o contorno e o tamanho do texto.

    ![Cartão de grelha](media/power-bi-visualization-tables/power-bi-table-gridnew.png)

    ![tabela a mostrar resultados](media/power-bi-visualization-tables/power-bi-table-grid3.png)
* Para os cabeçalhos de coluna, alterámos a cor de fundo, adicionámos um contorno e aumentámos o tamanho do tipo de letra. 

    ![Cartão de cabeçalhos de coluna](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

    ![formatação de cabeçalhos na tabela](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Pode até aplicar a formatação em colunas individuais e em cabeçalhos de coluna. Comece por expandir **Formatação de campo** e selecionar, na lista pendente, a coluna a formatar. Consoante os valores da coluna, a opção Formatação de campo permite definir coisas como: as unidades de apresentação, a cor do tipo de letra, o número de casas decimais, o fundo, o alinhamento e muito mais. Assim que tiver ajustado as definições, decida se pretende aplicar essas definições também ao cabeçalho e à linha de totais.

    ![Formatação de campos para vendas deste ano](media/power-bi-visualization-tables/power-bi-field-formatting.png)

* E, após alguma formatação adicional, eis a nosso tabela final. Uma vez que existem muitas opções de formatação, a melhor forma de aprender é começar com a formatação predefinida. Para tal, abra o painel Formatação ![](media/power-bi-visualization-tables/power-bi-format.png) e comece a explorar. 

    ![tabela com toda a formatação até ao momento](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Formatação condicional
Um tipo de formatação é chamado *formatação condicional* e é aplicado aos campos na área **Valores** do painel **Visualizações** no serviço Power BI ou no Desktop. 

Com a formatação condicional para tabelas, pode especificar cores de fundo de célula personalizadas e cores de tipo de letra com base nos valores de célula, incluindo a utilização de cores da gradação. 

1. No painel **Visualizações** no serviço Power BI ou no Desktop, selecione a seta para baixo junto ao valor na área **Valores** que pretende formatar (ou clique com o botão direito do rato no campo). Só pode gerir a formatação condicional para os campos na área **Valores** da área **Campos**.

    ![caminho para Escalas de cores de fundo](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)
2. Selecione **Escalas de cores de fundo**. Na caixa de diálogo que aparece, pode configurar a cor, bem como os valores *Mínimo* e *Máximo*. Se selecionar a caixa **Divergente**, também pode configurar um valor de *Centro* opcional.

    ![Ecrã Escalas de cores de fundo](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)

    Vamos aplicar alguma formatação personalizada aos nossos valores de Preço Unitário Médio. Selecione **Divergente**, adicione algumas cores e escolha **OK**. 

    ![tabela que mostra cores divergentes](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
3. Adicione um novo campo à tabela que tem valores positivos e negativos.  Selecione **Vendas > Desvio de Vendas Total**. 

    ![mostra um novo campo na extremidade direita](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)
4. Adicione formatação condicional à barra de dados, selecionando a seta para baixo junto a **Desvio de Vendas Total** e escolhendo **Formatação condicional > Barras de dados**.

    ![caminho para selecionar Barras de dados](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)
5. Na caixa de diálogo que aparece, defina as cores para **Barra positiva**, **Barra negativa**, coloque uma marca de verificação junto a **Mostrar apenas a barra** e faça outras alterações que pretender.

    ![marca de verificação para Mostrar apenas a barra](media/power-bi-visualization-tables/power-bi-data-bars.png)

    Quando seleciona **OK**, as barras de dados substituem os valores numéricos na tabela, facilitando a análise da mesma.

    ![a mesma tabela, mas com barras na última coluna](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)
6. Para remover a formatação condicional de uma visualização, clique novamente no campo com o botão direito do rato e selecione **Remover Formatação Condicional**.

> [!TIP]
> A formatação condicional também está disponível a partir do painel de Formatação (ícone de rolo de pintura). Selecione o valor a formatar e, em seguida, defina **Escalas de cores** ou **Barras de dados** como **Ativo** para aplicar as predefinições ou, para personalizar as definições, selecione **Controlos avançados**.
> 
## <a name="copy-values-from-power-bi-tables-for-use-in-other-applications"></a>Copie os valores das tabelas do Power BI para utilizar noutras aplicações

A tabela ou a matriz pode ter conteúdos que quer utilizar noutras aplicações, como o Dynamics CRM, o Excel e até mesmo noutros relatórios do Power BI. Ao clicar com o botão direito do rato no Power BI, pode copiar uma única célula ou uma seleção de células para a área de transferência e colar noutra aplicação.


* Para copiar o valor de uma única célula, selecione a célula, clique com o botão direito do rato e escolha **Copiar valor**. Com o valor da célula não formatado na área de transferência, pode agora colá-lo noutra aplicação.

    ![opções de cópia](media/power-bi-visualization-tables/power-bi-copy-value.png)

* Para copiar mais do que uma célula, selecione um intervalo de células ou utilize CTRL para selecionar uma ou mais células. A cópia incluirá os cabeçalhos de coluna e de linha.

    ![opções de cópia](media/power-bi-visualization-tables/power-bi-copy-selection.png)

    A cópia inclui os cabeçalhos de coluna e de linha.

    ![colar no Excel](media/power-bi-visualization-tables/power-bi-paste-selection.png)

## <a name="adjust-the-column-width-of-a-table"></a>Ajustar a largura da coluna de uma tabela
Por vezes, o Power BI trunca o cabeçalho de uma coluna num relatório e num dashboard. Para mostrar o nome completo da coluna, paire sobre o espaço à direita do cabeçalho para revelar as setas duplas, selecione e arraste.

![grande plano do vídeo de redimensionamento da coluna](media/power-bi-visualization-tables/resizetable.gif)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Ao aplicar a formatação de colunas, apenas pode escolher uma opção de alinhamento por coluna: Auto, Left, Center, Right. Normalmente, uma coluna contém só texto ou só números e não uma combinação de ambos. No entanto, quando uma coluna tiver números e texto, a opção de alinhamento **Automático** alinhará o texto à esquerda e os números à direita. Este comportamento suporta idiomas que se leem da esquerda para a direita.   

## <a name="next-steps"></a>Próximos passos

[Treemaps no Power BI](power-bi-visualization-treemaps.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)