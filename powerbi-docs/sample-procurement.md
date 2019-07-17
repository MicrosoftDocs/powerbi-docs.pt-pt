---
title: 'Exemplo de Análise de Aprovisionamento: veja uma apresentação'
description: 'Exemplo de Análise de Aprovisionamento do Power BI: veja uma apresentação'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 17a4a3770cb2c3e2adff2bcce64c3e101688e002
ms.sourcegitcommit: 1789815c87e306b1427a5838655d30d3b9ba1d29
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67791873"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Aprovisionamento do Power BI: veja uma apresentação

O pacote de conteúdos do exemplo da Análise de Aprovisionamento contém um dashboard, um relatório e um conjunto de dados que analisa os gastos de uma empresa industrial nos fornecedores por categoria e local. No exemplo, exploraremos estas áreas:

* Quem são os principais fornecedores
* Em que categorias ocorrem a maioria dos gastos
* Que fornecedores nos oferecem o desconto mais alto e quando

![Dashboard para o exemplo de Análise de Aprovisionamento](media/sample-procurement/procurement1.png)

Este exemplo faz parte de uma série que mostra como pode utilizar o Power BI com dados, relatórios e dashboards orientados para negócios. Foi criado com dados reais da [obviEnce](http://www.obvience.com/), que foram mantidos anónimos. Os dados estão disponíveis em vários formatos: pacote de conteúdos, ficheiro .pbix do Power BI Desktop ou livro do Excel. Veja [Exemplos do Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdos do exemplo da Análise de Aprovisionamento no serviço Power BI. Uma vez que a experiência do relatório é semelhante no Power BI Desktop e no serviço, também pode acompanhar com o ficheiro .pbix de exemplo no Power BI Desktop. 

Não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho no serviço Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

Para poder utilizar o exemplo, primeiro tem de transferi-lo como um [pacote de conteúdos](#get-the-content-pack-for-this-sample), um [ficheiro .pbix](#get-the-pbix-file-for-this-sample) ou um [livro do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdos para este exemplo

1. Abra o serviço Power BI (app.powerbi.com), inicie sessão e abra a área de trabalho onde quer guardar o exemplo. 

    Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.

    ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** apresentada, selecione **Exemplos**.

4. Selecione **Exemplo de Análise de Aprovisionamento** e, em seguida, escolha **Ligar**.  
  
   ![Ligar ao exemplo](media/sample-procurement/procurement1a.png)
   
5. O Power BI importa o pacote de conteúdos e adiciona um novo dashboard, um relatório e um conjunto de dados à área de trabalho atual.
   
   ![Entrada do Exemplo de Análise de Aprovisionamento](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o ficheiro .pbix para este exemplo

Em alternativa, pode transferir o exemplo de Análise de Aprovisionamento como um [ficheiro .pbix](http://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix), concebido para utilização com o Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter o livro do Excel para este exemplo

Se quiser ver a origem de dados deste exemplo, também está disponível como um [livro do Excel](http://go.microsoft.com/fwlink/?LinkId=529784). O livro contém as folhas do Power View que pode ver e modificar. Para ver os dados não processados, ative os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerir**. Para ativar os suplementos Power View e Power Pivot, veja [Observe os exemplos de Excel a partir do interior do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.


## <a name="spending-trends"></a>Tendências de gastos
Primeiro, vamos analisar as tendências de gastos por categoria e local.  

1. Na área de trabalho onde guardou o exemplo, abra o separador **Dashboards** e, em seguida, localize o dashboard **Exemplo de Análise de Aprovisionamento** e selecione-o. 
2. Selecione o mosaico de dashboard **Total da Fatura por País/Região**, que é aberto na página **Descrição Geral de Gastos** do relatório **Exemplo de Análise de Aprovisionamento**.

    ![Página Descrição Geral de Gastos](media/sample-procurement/procurement2.png)

Repare nos seguintes detalhes:

* No gráfico de linhas **Total da fatura por mês e categoria**, a categoria **Direta** apresenta gastos consistentes, a categoria **Logística** apresenta um pico em dezembro e a categoria **Outros** apresenta um aumento em fevereiro.
* No mapa **Total da Fatura por País/Região**, a maioria dos nossos gastos dá-se nos Estados Unidos.
* No gráfico de colunas **Total da Fatura por Subcategoria**, **Hardware** e **Serviços e Produtos Indiretos** são as categorias que apresentam os maiores gastos.
* No gráfico de barras **Total da Fatura por Camada**, a maioria dos nossos negócios é feita com os nossos fornecedores da camada 1 (os 10 primeiros). Tal permite-nos gerir melhores relações com fornecedores.

## <a name="spending-in-mexico"></a>Gastos no México
Vamos explorar as áreas de gastos no México.

1. No mapa **Total da Fatura por País/Região**, selecione a bolha **México**. Note que, no gráfico de colunas **Total da Fatura por Subcategoria**, a maior parte dos gastos está concentrada na subcategoria **Serviços e Produtos Indiretos**.

   ![Selecionar México na página de Descrição Geral de Gastos](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Desagregue a coluna **Serviços e produtos indiretos**:

   * No gráfico **Total da Fatura por Subcategoria**, selecione a seta de busca detalhada ![Seta de busca detalhada](media/sample-procurement/pbi_drilldown_icon.png) no canto superior direito do gráfico.
   * Selecione a coluna **Serviços e produtos indiretos**.

      Como pode ver, por uma grande margem de diferença, os maiores gastos são na subcategoria **Vendas e Marketing**.
   * Selecione **México** no mapa novamente.

      Para o México, os maiores gastos são na subcategoria **Manutenção e Reparação**.

      ![Serviços e Produtos Indiretos desagregados para México](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Selecione a seta para cima no canto superior esquerdo do gráfico para voltar para cima.
4. Selecione a seta de busca detalhada novamente para desativar os detalhes.  
5. Na barra de navegação superior, selecione **IT Spend Analysis Sample** (Exemplo de Análise de Gastos de TI) para regressar ao dashboard.

## <a name="evaluate-different-cities"></a>Avaliar cidades diferentes
Podemos utilizar o realce para avaliar cidades diferentes.

1. Selecione o mosaico de dashboard **Total da Fatura, % Desconto por Mês**, que é aberto na página **Análise de Descontos** do relatório **Exemplo de Análise de Aprovisionamento**.
2. No mapa de árvore **Total da Fatura por Cidade**, selecione cada cidade à vez para ver a comparação entre elas. Note que quase todas as faturas de Miami são provenientes de fornecedores da camada 1.

   ![Cidade versus % de desconto por camada](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Descontos de fornecedores
Também vamos explorar os descontos disponíveis de fornecedores e os períodos de tempo quando obtemos a maioria dos descontos:
* Os descontos são diferentes em cada mês ou permanecem iguais?
* Algumas cidades têm mais descontos do que outras?

![Página de análise de descontos](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>Desconto por mês
Se observar o gráfico de combinação **Total da fatura e % de desconto por mês**, podemos ver que fevereiro é o mês mais movimentado e que setembro é o menos movimentado. 

Examine a percentagem de desconto durante estes meses: quando o volume aumenta, o desconto diminui e quando o volume é baixo, o desconto aumenta. Quanto mais precisarmos de desconto, pior é a negociação.

![Gráfico de Total de Fatura e % Desconto por Mês](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Desconto por cidade
Outra área a explorar é o desconto por cidade. Selecione cada cidade à vez no mapa de árvore e veja como os outros gráficos são alterados:

* St. Louis tinha um grande aumento no total da fatura em fevereiro e bastantes poupanças de descontos em abril.
* A Cidade do México tem a maior percentagem de desconto (11,05%) e Atlanta tem a mais pequena (0,08%).

![Gráficos de descontos para a Cidade do México](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Editar o relatório
Selecione **Editar relatório** no canto superior esquerdo e explore em Vista de edição:

* Veja como as páginas são feitas.
* Adicione páginas e gráficos com base nos mesmos dados.
* Altere o tipo de visualização de um gráfico, por exemplo, altere o mapa de árvore para um gráfico em anel.
* Afixe os gráficos no seu dashboard.

## <a name="next-steps-connect-to-your-data"></a>Próximos passos: Ligar aos seus dados
Aqui pode explorar à vontade, pois pode optar por não guardar as alterações. No entanto, se as guardar, pode sempre aceder a **Obter Dados** para obter uma nova cópia deste exemplo.

Esperamos que esta apresentação tenha mostrado como os dashboards, as Perguntas e Respostas e os relatórios do Power BI podem fornecer informações sobre os dados do exemplo. Agora, é a sua vez: ligue-se aos seus próprios dados. Com o Power BI, pode ligar-se a uma grande variedade de origens de dados. Para saber mais, veja [Introdução ao serviço Power BI](service-get-started.md).

