---
title: 'Exemplo de Análise de Revenda do Power BI: veja uma apresentação'
description: 'Exemplo de Análise de Revenda do Power BI: veja uma apresentação'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 42e3a95e344e17d1ceba11911fc8aa349ebafd0c
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207488"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Exemplo de Análise de Revenda do Power BI: veja uma apresentação

O pacote de conteúdos do exemplo Análise de Revenda contém um dashboard, um relatório e um conjunto de dados que analisa os dados de vendas a retalho dos artigos vendidos em várias lojas e distritos. As métricas comparam o desempenho do ano atual com o ano anterior relativamente a vendas, unidades, margem bruta e desvio, bem como a análise de novas lojas. 

![Dashboard do exemplo de Análise de Revenda](media/sample-retail-analysis/retail1.png)

Este exemplo faz parte de uma série que mostra como pode utilizar o Power BI com dados, relatórios e dashboards orientados para negócios. Foi criado com dados reais da [obviEnce](http://www.obvience.com/), que foram mantidos anónimos. Os dados estão disponíveis em vários formatos: pacote de conteúdos, ficheiro .pbix do Power BI Desktop ou livro do Excel. Veja [Exemplos do Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdos de exemplo de Análise de Revenda no serviço Power BI. Uma vez que a experiência do relatório é semelhante no Power BI Desktop e no serviço, também pode acompanhar com o ficheiro .pbix de exemplo no Power BI Desktop. 

Não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho no serviço Power BI. 

## <a name="get-the-sample"></a>Obter o exemplo

 Para poder utilizar o exemplo, primeiro tem de transferi-lo como um [pacote de conteúdos](#get-the-content-pack-for-this-sample), um [ficheiro .pbix](#get-the-pbix-file-for-this-sample) ou um [livro do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdos para este exemplo

1. Abra o serviço Power BI (app.powerbi.com), inicie sessão e abra a área de trabalho onde quer guardar o exemplo. 

    Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.

    ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** apresentada, selecione **Exemplos**.
   
4. Selecione **Exemplo de Análise de Revenda** e, em seguida, selecione **Ligar**.  
  
   ![Ligar ao exemplo](media/sample-retail-analysis/retail16.png)
   
5. O Power BI importa o pacote de conteúdos e adiciona um novo dashboard, um relatório e um conjunto de dados à área de trabalho atual.
   
   ![Entrada do Exemplo de Análise de Revenda](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Obter o ficheiro .pbix para este exemplo

Em alternativa, pode transferir o exemplo de Análise de Revenda como um [ficheiro .pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix), concebido para utilização com o Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter o livro do Excel para este exemplo

Se quiser ver a origem de dados deste exemplo, também está disponível como um [livro do Excel](https://go.microsoft.com/fwlink/?LinkId=529778). O livro contém as folhas do Power View que pode ver e modificar. Para ver os dados não processados, ative os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerir**. Para ativar os suplementos Power View e Power Pivot, veja [Observe os exemplos de Excel a partir do interior do próprio Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) para obter detalhes.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Iniciar no dashboard e abrir o relatório

1. Na área de trabalho onde guardou o exemplo, abra o separador **Dashboards** e, em seguida, localize o dashboard **Exemplo de Análise de Revenda** e selecione-o. 
2. No dashboard, selecione o mosaico **Lojas Totais Lojas Novas e Existentes**, que é aberto na página **Descrição Geral de Vendas em Loja** no relatório do Exemplo de Análise de Revenda. 

   ![Mosaico Total de Lojas](media/sample-retail-analysis/retail-analysis-7.png)  

   Nesta página de relatório, verá que temos um total de 104 lojas, havendo 10 lojas novas. Temos duas cadeias, Fashions Direct e Lindseys. Em média, as lojas Fashions Direct são maiores.
3. No gráfico circular **Vendas Deste Ano Por Cadeia**, selecione **Fashions Direct**.

   ![Gráfico de Vendas Deste Ano Por Cadeia](media/sample-retail-analysis/retail3.png)  

   Observe o resultado no gráfico de bolhas **% da Variação do Total de Vendas**:

   ![Gráfico da % da Variação do Total de Vendas](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   O distrito **FD-01** tem a maior média de **Vendas por Metro Quadrado** e FD-02 tem a menor **Variação do Total de Vendas** em comparação com o ano passado. FD-03 e FD-04 têm os piores desempenhos gerais.
4. Selecione algumas das bolhas individuais ou outros gráficos para ver o realce cruzado e revelar o impacto das suas seleções.
5. Para regressar ao dashboard, selecione **Exemplo de Análise de Revenda** no painel de navegação superior.

   ![Barra de navegação](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. No dashboard, selecione o mosaico **Vendas de Lojas Novas e Existentes Neste Ano**, o que é equivalente a escrever *Vendas Deste Ano* na caixa de perguntas das Perguntas e Respostas.

   ![Mosaico Vendas Deste Ano](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Os resultados das Perguntas e Respostas são apresentados:

   ![Vendas deste ano nas Perguntas e Respostas](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Rever um mosaico criado com as Perguntas e Respostas do Power BI
Vamos analisar mais detalhadamente.

1. Altere a pergunta para _vendas deste ano **por distrito**_ . Veja o resultado: Perguntas e Respostas coloca a resposta automaticamente num gráfico de barras e sugere outras frases:

   ![Vendas deste ano por distrito no Perguntas e Respostas](media/sample-retail-analysis/retail8.png)
2. Agora, altere a pergunta para _vendas deste ano **por código postal e cadeia**_ .

   Observe como a pergunta é respondida pelo Power BI à medida que escreve e o gráfico adequado é apresentado.
3. Experimente com mais perguntas e veja que tipo de resultados são obtidos.
4. Quando estiver pronto, regresse ao dashboard.

## <a name="dive-deeper-into-the-data"></a>Aprofundar os dados
Agora, vamos explorar num nível mais detalhado e analisar os desempenhos dos distritos.

1. No dashboard, selecione o mosaico **Vendas deste Ano, Vendas do Ano Passado**, que é aberto na página **Vendas Mensais Distritais** do relatório.

   ![Mosaico Vendas Deste Ano, Vendas do Ano Passado](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   No gráfico **% da Variação do Total de Vendas por Mês Fiscal** observe a grande variabilidade na % de variação em comparação com o ano passado, tendo sido janeiro, abril e julho meses especialmente maus.

   ![Gráfico da % da Variação do Total de Vendas por Mês Fiscal](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Vamos ver se podemos chegar até onde os problemas podem estar.
2. No gráfico de bolhas, selecione a bolha **020-Mens**.

   ![Selecionar 020-Mens](media/sample-retail-analysis/retail11.png)  

   Observe que embora a categoria Masculino não tenha sido tão prejudicada em abril como os negócios em geral, janeiro e julho ainda foram meses com problemas.
1. Selecione a bolha **010-Womens**.

   ![Selecionar 010-Womens](media/sample-retail-analysis/retail12.png)

   Observe que a categoria Feminino teve um desempenho muito pior do que os negócios em geral em todos os meses, e em quase todos os meses, em comparação com o ano interior.
1. Selecione a bolha novamente para limpar o filtro.

## <a name="try-out-the-slicer"></a>Experimente a segmentação de dados
Vejamos o desempenho de distritos específicos.

1. Selecione **Artur Gomes** em **Gestor Distrital** na parte superior esquerda da segmentação.

   ![Selecionar Artur Gomes](media/sample-retail-analysis/retail13.png)

   Observe que o distrito de Artur teve um desempenho superior em março e junho, no Ano Passado, em comparação com o ano passado.
2. Com o **Artur Gomes** ainda selecionado, selecione a bolha **Womens-10** no gráfico de bolhas.

   ![Artur Gomes e Womens-10 selecionados](media/sample-retail-analysis/power-bi-allan.png)

   Observe que para a categoria Womens-10, o distrito do Artur não atingiu o volume do ano passado.
3. Explore os outros gestores e categorias de distrito; que outras informações pode encontrar?
4. Quando estiver pronto, volte ao dashboard.

## <a name="what-the-data-says-about-sales-growth-this-year"></a>O que dizem os dados sobre o crescimento das vendas neste ano
A última área que queremos explorar é o nosso crescimento ao examinar as novas lojas abertas este ano.

1. Selecione o mosaico **Lojas Abertas Este Ano Por Mês de Abertura, Cadeia**, que é aberto na página **Análise de Lojas Novas** do relatório.

   ![Página Análise de Lojas Novas](media/sample-retail-analysis/retail15.png)

   Como pode ser visto no mosaico, foram abertas mais lojas Fashion Direct do que Lindseys este ano.
2. Veja o gráfico **Vendas por metros quadrados por Nome**:

   ![Gráfico Vendas por metros quadrados por Nome](media/sample-retail-analysis/retail14.png)

    Repare na diferença nas vendas médias/metro quadrado entre as novas lojas.
3. Selecione o item de legenda **Fashions Direct** no gráfico superior direito **Contagem de Lojas Abertas por Mês de Abertura e Cadeia**. Observe que, mesmo para a mesma cadeia, a melhor loja (Winchester Fashions Direct) tem um desempenho significativamente superior à pior loja (Cincinnati 2 Fashions Direct): 21,22 $ vs. 12,86 $, respetivamente.

   ![Fashions Direct selecionado](media/sample-retail-analysis/power-bi-lindseys.png)
4. Selecione **Winchester Fashions Direct** na segmentação de dados **Nome** e observe o gráfico de linhas. Os primeiros números de vendas foram comunicados em fevereiro.
5. Selecione **Cincinnati 2 Fashions Direct** na segmentação de dados e observe no gráfico de linhas que a loja foi aberta em junho e que parece ser a loja com o pior desempenho.
6. Explore ao selecionar outras barras, linhas e bolhas em todos os gráficos e veja que informações pode descobrir.

## <a name="next-steps-connect-to-your-data"></a>Next steps: Ligar aos seus dados
Aqui pode explorar à vontade, pois pode optar por não guardar as alterações. No entanto, se as guardar, pode sempre aceder a **Obter Dados** para obter uma nova cópia deste exemplo.

Esperamos que esta apresentação tenha mostrado como os dashboards, as Perguntas e Respostas e os relatórios do Power BI podem fornecer informações sobre os dados do exemplo. Agora, é a sua vez: ligue-se aos seus próprios dados. Com o Power BI, pode ligar-se a uma grande variedade de origens de dados. Para saber mais, veja [Introdução ao serviço Power BI](service-get-started.md).
