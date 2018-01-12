---
title: "Visualizações de tabela em relatórios e dashboards do Power BI (Tutorial)"
description: "Sugestões para trabalhar com visualizações de tabela em relatórios e dashboards do Power BI, incluindo como redimensionar larguras de coluna."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: e4a2e162ca193af756e7182fb118bc7e72d38d28
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="working-with-tables-in-power-bi-reports-and-dashboards-tutorial"></a>Trabalhar com tabelas em relatórios e dashboards do Power BI (Tutorial)
Uma tabela é uma grelha que contém dados relacionados numa série lógica de linhas e colunas. Também pode conter cabeçalhos e uma linha para totais. As tabelas funcionam bem com comparações quantitativas, onde pode observar vários valores para uma única categoria. Por exemplo, esta tabela apresenta 5 medidas diferentes para **Categoria**.

![](media/power-bi-visualization-tables/table.png)

## <a name="when-to-use-a-table"></a>Quando utilizar uma tabela
As tabelas são uma excelente opção:

* para ver e comparar dados detalhados e valores exatos (em vez de representações visuais)
* para apresentar dados num formato tabular
* para apresentar dados numéricos por categorias   

> [!NOTE]
> Se uma tabela tiver demasiados valores, considere convertê-la numa matriz e/ou utilizar desagregação.
> 
> 

## <a name="create-a-table"></a>Criar uma tabela
Para acompanhar, inicie sessão no Power BI e selecione **Obter Dados > Exemplos > Exemplo de Análise de Revenda**. Vamos criar a tabela ilustrada acima para apresentar os valores de vendas por categoria de item.

1. Em **A Minha Área de Trabalho**, selecione o separador Conjuntos de dados e desloque o ecrã para baixo até ao conjunto de dados Exemplo de Análise de Revenda que acabou de adicionar.  Selecione o ícone **Criar relatório**.
   
    ![](media/power-bi-visualization-tables/power-bi-create-report.png)
2. No editor de relatórios, selecione **Item** > **Categoria**.  O Power BI cria automaticamente uma tabela que apresenta uma lista de todas as categorias.
   
    ![](media/power-bi-visualization-tables/power-bi-table1.png)
3. Selecione **Vendas > Preço Unitário Médio** e **Vendas > Vendas do Último Ano** e **Vendas > Vendas Deste Ano** e escolha todas as 3 opções (Valor, Objetivo, Estado).   
4. No painel Visualizações, localize a área **Valores** e arraste e largue os valores até que a ordem das colunas do gráfico correspondam à primeira imagem desta página.  A área Valores deverá ser semelhante à seguinte.
   
    ![](media/power-bi-visualization-tables/power-bi-table2.png)
5. Afixe a tabela ao dashboard, selecionando o ícone de pin  
   
     ![](media/power-bi-visualization-tables/pbi_pintile.png)

## <a name="format-the-table"></a>Formatar a tabela
Existem várias formas de formatar uma tabela e vamos apenas abordar algumas delas aqui. Uma excelente forma de saber mais sobre as outras opções de formatação é abrir o painel de Formatação (ícone de rolo de pintura ![](media/power-bi-visualization-tables/power-bi-format.png)) e explorar.

* Experimente formatar a grelha da tabela. Aqui, adicionámos uma grelha vertical azul, adicionámos espaço às linhas, aumentámos um pouco o contorno e o tamanho do texto.
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid2-new.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid3.png)
* Para os cabeçalhos de coluna, alterámos a cor de fundo, adicionámos um contorno e aumentámos o tamanho do tipo de letra. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-column.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-column2.png)
* E, após alguma formatação adicional, eis a nosso tabela final. Uma vez que existem muitas opções de formatação, a melhor forma de aprender é começar com uma tabela simples, abrir o painel de Formatação ![](media/power-bi-visualization-tables/power-bi-format.png) e começar a explorar. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Formatação condicional
Um tipo de formatação é chamado *formatação condicional* e é aplicado aos campos na área **Valores** do painel **Visualizações** no serviço Power BI ou no Desktop. 

Com a formatação condicional para tabelas, pode especificar cores de fundo de célula personalizadas e cores de tipo de letra com base nos valores de célula, incluindo a utilização de cores da gradação. 

1. No painel **Visualizações** no serviço Power BI ou no Desktop, selecione a seta para baixo junto ao valor na área **Valores** que pretende formatar (ou clique com o botão direito do rato no campo). Só pode gerir a formatação condicional para os campos na área **Valores** da área **Campos**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)
2. Selecione **Escalas de cores de fundo**. Na caixa de diálogo que aparece, pode configurar a cor, bem como os valores *Mínimo* e *Máximo*. Se selecionar a caixa **Divergente**, também pode configurar um valor de *Centro* opcional.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)
   
    Vamos aplicar alguma formatação personalizada aos nossos valores de Preço Unitário Médio. Selecione **Divergente**, adicione algumas cores e escolha **OK**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
3. Adicione um novo campo à tabela que tem valores positivos e negativos.  Selecione **Vendas > Desvio de Vendas Total**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)
4. Adicione formatação condicional à barra de dados, selecionando a seta para baixo junto a **Desvio de Vendas Total** e escolhendo **Formatação condicional > Barras de dados**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)
5. Na caixa de diálogo que aparece, defina as cores para **Barra positiva**, **Barra negativa**, coloque uma marca de verificação junto a **Mostrar apenas a barra** e faça outras alterações que pretender.
   
    ![](media/power-bi-visualization-tables/power-bi-data-bars.png)
   
    Quando seleciona **OK**, as barras de dados substituem os valores numéricos na tabela, facilitando a análise da mesma.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)
6. Para remover a formatação condicional de uma visualização, basta clicar com o botão direito do rato novamente no campo e selecionar **Remover formatação condicional**.

> [!TIP]
> A formatação condicional também está disponível a partir do painel de Formatação (ícone de rolo de pintura). Selecione o valor a formatar e, em seguida, defina **Escalas de cores** ou **Barras de dados** como Ativo para aplicar as predefinições ou, para personalizar as definições, selecione **Controlos avançados**.
> 
> 

## <a name="adjust-the-column-width-of-a-table"></a>Ajustar a largura da coluna de uma tabela
Por vezes, o Power BI trunca o cabeçalho de uma coluna num relatório e num dashboard. Para mostrar o nome completo da coluna, paire sobre o espaço à direita do cabeçalho para revelar as setas duplas, selecione e arraste.

![](media/power-bi-visualization-tables/resizetable.gif)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

