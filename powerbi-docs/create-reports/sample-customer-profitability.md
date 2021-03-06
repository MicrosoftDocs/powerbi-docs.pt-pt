---
title: 'Exemplo de Rentabilidade do Cliente do Power BI: veja uma apresentação'
description: 'Exemplo de Rentabilidade do Cliente do Power BI: veja uma apresentação'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/05/2019
LocalizationGroup: Samples
ms.openlocfilehash: adc642d5366949e547e0115badd5e800ffa04bb0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415111"
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Exemplo de Rentabilidade do Cliente do Power BI: veja uma apresentação

O pacote de conteúdos de exemplo Rentabilidade do Cliente contém um dashboard, um relatório e um conjunto de dados para uma empresa que fabrica materiais de marketing. Este dashboard foi criado por uma diretora financeira para ver as principais métricas sobre os seus cinco gestores (executivos) de unidade de negócio, produtos, clientes e margens brutas (GM). Desta forma, podem ver rapidamente que fatores têm impacto na rentabilidade.

![Dashboard do exemplo de Rentabilidade do Cliente](media/sample-customer-profitability/power-bi-dash.png)

Este exemplo faz parte de uma série que mostra como pode utilizar o Power BI com dados, relatórios e dashboards orientados para negócios. Foi criado com dados reais da [obviEnce](http://www.obvience.com/), que foram mantidos anónimos. Os dados estão disponíveis em vários formatos: pacote de conteúdos, ficheiro .pbix do Power BI Desktop ou livro do Excel. Veja [Exemplos do Power BI](sample-datasets.md). 

Este tutorial explora o pacote de conteúdos de exemplo Rentabilidade do Cliente no serviço Power BI. Uma vez que a experiência do relatório é semelhante no Power BI Desktop e no serviço, também pode acompanhar com o ficheiro .pbix de exemplo no Power BI Desktop. 

Não precisa de uma licença do Power BI para explorar os exemplos no Power BI Desktop. Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho no serviço Power BI. 

## <a name="get-the-sample"></a>Obter o Exemplo

Para poder utilizar o exemplo, primeiro tem de transferi-lo como um [pacote de conteúdos](#get-the-content-pack-for-this-sample), um [ficheiro .pbix](#get-the-pbix-file-for-this-sample) ou um [livro do Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Obter o pacote de conteúdos para este exemplo

1. Abra o serviço Power BI (app.powerbi.com), inicie sessão e abra a área de trabalho onde quer guardar o exemplo.

   Se não tiver uma licença do Power BI Pro, pode guardar o exemplo em A Minha Área de Trabalho.

2. No canto inferior esquerdo, selecione **Obter Dados**.

   ![Selecionar Obter Dados](media/sample-datasets/power-bi-get-data.png)
3. Na página **Obter Dados** apresentada, selecione **Exemplos**.

4. Selecione **Exemplo de Rentabilidade do Cliente** e, em seguida, **Ligar**.  

    ![Ligar ao exemplo](media/sample-customer-profitability/get-supplier-sample.png)
5. O Power BI importa o pacote de conteúdos e adiciona um novo dashboard, um relatório e um conjunto de dados à área de trabalho atual.

    ![Entrada do Exemplo de Rentabilidade do Cliente](media/sample-customer-profitability/customer-profitability-sample-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Obter o ficheiro .pbix para este exemplo

Em alternativa, pode transferir o exemplo Rentabilidade do Cliente como um [ficheiro .pbix](https://download.microsoft.com/download/6/A/9/6A93FD6E-CBA5-40BD-B42E-4DCAE8CDD059/Customer%20Profitability%20Sample%20PBIX.pbix), que foi concebido para ser utilizado com o Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Obter o livro do Excel para este exemplo

Se quiser ver a origem de dados deste exemplo, também está disponível como um [livro do Excel](https://go.microsoft.com/fwlink/?LinkId=529781). O livro contém as folhas do Power View que pode ver e modificar. Para ver os dados não processados, ative os suplementos de Análise de Dados e, em seguida, selecione **Power Pivot > Gerir**. Para ativar os suplementos do Power View e do Power Pivot, veja [Explorar os exemplos do Excel](sample-datasets.md#explore-excel-samples-inside-excel) para obter detalhes.

## <a name="what-is-our-dashboard-telling-us"></a>O que nos diz o nosso dashboard?

Na área de trabalho onde guardou o exemplo, procure o dashboard Rentabilidade do Cliente e selecione-o:

![Dashboard do exemplo de Rentabilidade do Cliente](media/sample-customer-profitability/power-bi-dash.png)

### <a name="company-wide-dashboard-tiles"></a>Mosaicos de dashboard de toda a empresa
1. Abra o dashboard no serviço Power BI. Os mosaicos do dashboard dão à nossa diretora financeira as métricas da empresa de alto nível que ela considera importantes. Quando vê algo interessante, pode selecionar um mosaico para examinar os dados.

2. Consulte os mosaicos à esquerda do dashboard.

    ![Mosaicos para gestores](media/sample-customer-profitability/power-bi-manager.png)

   Repare nos seguintes detalhes:
   - A margem bruta da empresa é de 42,5%.
   - Tem 80 clientes.
   - Vende cinco produtos diferentes.
   - Teve a menor % de variação da receita do orçamento em fevereiro, seguida da mais alta em março.
   - A maioria da nossa receita é proveniente das regiões leste e norte. A margem bruta nunca excedeu o orçamento, com as unidades de negócio ER-0 e MA-0 a exigirem mais investigação.
   - A receita total para o ano é quase o orçamento.

### <a name="manager-specific-dashboard-tiles"></a>Mosaicos do dashboard específico do gerente
Os mosaicos à direita do dashboard fornecem uma tabela de indicadores da equipa. A diretora financeira necessita de manter o controlo dos seus gestores e estes mosaicos apresentam uma descrição geral resumida do lucro ao utilizar a % GM. Se a tendência de % GM for inesperada para qualquer gestor, poderá investigar mais.

![% GM para gestores](media/sample-customer-profitability/power-bi-manager2.png)

Ao analisar os mosaicos do dashboard específicos dos gestores, podemos fazer as seguintes observações:

- Todos os executivos, exceto Carlos, já excederam os objetivos de vendas. Contudo, as vendas reais de Carlos apresentam o valor mais elevado.
- A % de Margem Bruta de Annelie é a mais baixa, mas podemos ver um aumento gradual desde março.
- A Valery, por outro lado, teve uma queda significativa na % GM.
- Andrew teve um ano volátil.

## <a name="explore-the-dashboards-underlying-data"></a>Explorar os dados subjacentes do dashboard
Este dashboard possui mosaicos com ligação a um relatório e a um livro do Excel.

### <a name="open-the-excel-online-data-source"></a>Abrir a origem de dados do Excel Online
Dois mosaicos neste dashboard, **Target vs Actual** (Objetivo vs. Real) e **Year Over Year Revenue Growth** (Crescimento da Receita ao Longo dos Anos), foram afixados a partir de um livro do Excel. Ao selecionar um destes mosaicos, o Power BI abre a origem de dados, neste caso, o Excel Online.

![Excel online](media/sample-customer-profitability/power-bi-excel-online.png)

1. Selecione um dos mosaicos afixados a partir do Excel. O Excel Online é aberto no serviço Power BI.
2. Tenha em atenção que o livro tem três separadores de dados. Abra **Revenue** (Receita).
3. Vejamos porque é que Carlos ainda não atingiu o objetivo:  

    a. No controlo de deslize **Executive** (Executivo), selecione **Carlos Grilo**.   

    b. A primeira tabela dinâmica indica-nos que o crescimento da receita do Carlos referente ao produto principal, Primus, é 152% inferior ao do ano anterior. O gráfico **YoY Revenue Variance** (Variação da Receita ao Longo dos Anos) mostra-nos que o Carlos esteve abaixo do orçamento na maioria dos meses.  

    ![Tabela Dinâmica](media/sample-customer-profitability/power-bi-pivotchart.png)

    ![Resultados para Carlos](media/sample-customer-profitability/power-bi-carlos.png)

4. Continue a explorar. Se encontrar algo interessante, selecione **Afixar** ![ícone de afixar](media/sample-customer-profitability/power-bi-excel-pin.png), no canto superior direito, para o [afixar num dashboard](service-dashboard-pin-tile-from-excel.md).

5. Utilize a seta para trás do browser para regressar ao dashboard.

### <a name="open-the-underlying-power-bi-report"></a>Abrir o relatório subjacente do Power BI
Muitos dos mosaicos no dashboard no exemplo de Rentabilidade do Cliente foram afixados do relatório de exemplo Rentabilidade do Cliente subjacente.

1. Selecione um destes mosaicos para abrir o relatório na Vista de leitura.

   Se o mosaico tiver sido criado em Perguntas e Respostas, selecioná-lo irá abrir a janela Perguntas e Respostas. Selecione **Sair das Perguntas e Respostas** para voltar ao dashboard e experimentar um mosaico diferente.

2. O relatório tem três páginas. Cada separador na parte inferior do relatório representa uma página diferente.

    ![Três separadores na parte inferior](media/sample-customer-profitability/power-bi-report-tabs.png)

    * **Team Scorecard** (Tabela de Indicadores da Equipa) centra-se no desempenho dos cinco gestores e dos respetivos livros de negócio.
    * **Industry Margin Analysis** (Análise de Margem do Setor) fornece uma forma de analisar a rentabilidade em comparação com o que se passa em todo o setor.
    * **Executive Scorecard** (Tabela de Indicadores de Executivos) fornece uma vista de cada um dos gestores num formato de tamanho de página personalizado.

### <a name="team-scorecard-page"></a>Página de pontuação da equipa
![Página do relatório da pontuação da equipa](media/sample-customer-profitability/customer2.png)

Vejamos dois dos membros da equipa ao detalhe e que informações podem ser obtidas: 

1. Na segmentação de dados **Executive** (Executivos) à esquerda, selecione o nome do Andrew para filtrar a página do relatório e ver apenas os dados dele:

   * Para um KPI rápido, analise o **Estado da Receita (Total do Ano)** de Andrew. É apresentado a verde, o que significa que Andrew está a ter um bom desempenho.
   * O gráfico **Revenue % Variance to Budget by Month and Executive** (% de Variação da Receita do Orçamento por Mês e Executivo) mostra que, com exceção de uma queda em fevereiro, Andrew está a ter um bom desempenho. A região dominante do Andrew é o Leste, que inclui 49 clientes e cinco de sete produtos. A % GM do Andrew não é a mais alta nem a mais baixa.
   * O gráfico **RevenueTY and Revenue % Var to Budget by Month** (Total da Receita do Ano e % de Variação da Receita do Orçamento por Mês) mostra um histórico de lucros contínuo e equilibrado. No entanto, se filtrar ao selecionar o quadrado para **Central** no mapa de árvore da região, irá descobrir que Andrew só tem receitas em Março e no Indiana. É uma tendência intencional ou é algo que tem de ser analisado?

2. Agora, com Valery. Na segmentação de dados **Executivos**, selecione o nome da Valery para filtrar a página de relatório e ver apenas os dados dela. 

   ![Dados de Valery](media/sample-customer-profitability/customer3.png)

   * Observe o KPI a vermelho para **Revenue Status (Total Year)** (Estado da Receita [Total do Ano]). Este item necessita definitivamente de mais investigação.
   * A variação da receita da Valery também revela algo preocupante: ela não está a atingir as margens de receita definidas.
   * Valery só tem nove clientes, lida apenas com dois produtos e trabalha quase exclusivamente com clientes na região norte. Esta especialização poderá explicar as grandes oscilações nas métricas.
   * Se selecionar o quadrado **Norte** no gráfico treemap, este mostrará que a margem bruta da Valery na região norte é consistente com a margem geral.
   * Ao selecionar cada um dos outros quadrados **Total Revenue by Region** (Receita Total por Região), vemos dados interessantes: a % GM varia entre 23% e 79%. Os números de receita da Valery em todas as regiões, exceto na região norte, são extremamente sazonais.

3. Continue a explorar para descobrir porque é que a área de Valery não apresenta um bom desempenho. Analise as regiões, as outras unidades de negócios e a próxima página do relatório: **Análise de Margem do Setor**.

### <a name="industry-margin-analysis"></a>Análise de Margem da Indústria
Esta página de relatório fornece uma secção diferente dos dados. Examina a margem bruta para todo o setor, dividido por segmento. A diretora financeira utiliza esta página para comparar as métricas das unidades de negócio e da empresa com as métricas do setor para ajudar a explicar tendências e lucro. Poderá estar a questionar-se por que motivo o gráfico **Gross Margin % by Month and Executive** (Margem Bruta por Mês e Executivo) está nesta página, uma vez que é específico de uma equipa. Tê-lo aqui permite-nos filtrar a página pelo gerente da unidade de negócios.  

![Página do relatório de análise de margem do setor](media/sample-customer-profitability/customer6.png)

1. Como varia o lucro por setor? Como se os produtos e clientes dividem por setor? Para responder a estas perguntas, selecione um ou mais setores no canto superior esquerdo (comece com o setor de CPG). Para limpar o filtro, selecione o ícone de borracha.

2. No gráfico de bolhas **Revenue Var % to Budget, GM%, and RevenueTY by Industry** (% de Variação da Receita do Orçamento, % de GM e Total da Receita do Ano por Setor), a diretora financeira procura as bolhas maiores, uma vez que têm o maior impacto na receita. Para ver facilmente o impacto de cada gestor por segmento do setor, filtre a página ao selecionar o nome de cada gestor no gráfico de área.

3. À medida que seleciona cada gestor no gráfico, repare nos seguintes detalhes:
   * A área de influência de Andrew abrange vários setores diferentes com diferentes amplamente % GM (a maioria do lado positivo) e % Var.
   * O gráfico da Annelie é semelhante, mas ela concentra-se somente em alguns segmentos do setor, com um foco no segmento Federal e outro no produto Gladius.
   * Carlos tem um foco claro no segmento de serviços, com um bom lucro. O Carlos aumentou bastante a % de variação para o segmento Alta Tecnologia, e um novo segmento, o Industrial, teve um excelente desempenho em relação ao orçamento.
   * A Tina trabalha com alguns segmentos e tem a % GM mais alta, mas o tamanho geralmente pequeno das suas bolhas mostra que o impacto sobre o resultado da empresa é mínimo.
   * Valery, que é responsável por apenas um produto, só trabalha com cinco segmentos do setor. A influência da Valery no setor é sazonal, mas produz sempre uma grande bolha, o que indica que há um impacto significativo sobre o resultado da empresa. Os segmentos do setor explicam o desempenho negativo?

### <a name="executive-scorecard"></a>Tabela de indicadores executiva
Esta página tem um formato de tamanho de página personalizado.

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Investigue os dados fazendo perguntas em Perguntas e Respostas
Para a nossa análise, poderá ser útil determinar que setor gera a maior parte da receita para Valery. Vamos utilizar as Perguntas e Respostas.

1. Selecione **Editar relatório** para abrir o relatório na Vista de edição. A vista de Edição só está disponível se for proprietário do relatório. Esta vista é por vezes denominada modo de *criador*. Se, em vez disso, este relatório for partilhado apenas consigo, não poderá abri-lo na vista de Edição.

2.  Na parte superior do dashboard, selecione **Colocar uma questão** para abrir a caixa de Perguntas e Respostas.

    ![Colocar uma questão sobre os dados](media/sample-customer-profitability/power-bi-ask-question.png)

3. Escreva *receita total por setor de Valery* na caixa de perguntas. Veja como a visualização é atualizada à medida que escreve a pergunta.

    ![Escrever uma pergunta na caixa de perguntas](media/sample-customer-profitability/power-bi-qna.png)

   Como pode ver, o setor de Distribuição é a maior área de receita de Valery.

### <a name="dig-deeper-by-adding-filters"></a>Aprofunde adicionando filtros
Analisemos o setor de Distribuição.  

1. Abra a página do relatório **Industry Margin Analysis** (Análise de Margem do Setor).
2. Sem selecionar nenhuma visualização na página de relatório, expanda o painel de filtros à direita (se ainda não estiver expandido). O painel **Filters** (Filtros) deverá apresentar apenas **Page level filters** (Filtros ao nível da página).  

   ![Filtros de nível de página](media/sample-customer-profitability/power-bi-filters.png)
3. Localize o filtro para **Setor** e selecione a seta para expandir a lista. Vamos adicionar um filtro de página para o setor de Distribuição. Primeiro, desmarque todas as seleções ao desmarcar a caixa de seleção **Selecionar Tudo**. Em seguida, selecione apenas **Distribuição**.  

   ![filtro para Distribuição](media/sample-customer-profitability/customer7.png)
4. O gráfico **Gross Margin % by Month and Executive** (% de Margem Bruta por Mês e Executivo) indica-nos que apenas Valery e Tina têm clientes neste setor, e que Valery trabalhou com este setor apenas de junho a novembro.   
5. Selecione **Tina** e **Valery** na legenda do gráfico **Gross Margin by Month and Executive** (Margem Bruta por Mês e Executivo). Repare que a parte de Tina do gráfico **Total Revenue by Product** (Receita Total por Produto) é pequena em comparação com a de Valery.
6. Para ver a receita real, selecione a caixa Perguntas e Respostas no dashboard e introduza a *receita total para distribuição por cenário* .  

     ![Escrever perguntas na caixa Perguntas e Respostas](media/sample-customer-profitability/power-bi-qna2.png)

    Podemos explorar de forma semelhante a outros setores e até mesmo adicionar clientes aos nossos visuais para compreender as causas para o desempenho de Valery.

## <a name="next-steps-connect-to-your-data"></a>Next steps: Ligar aos seus dados
Aqui pode explorar à vontade, pois pode optar por não guardar as alterações. No entanto, se as guardar, pode sempre aceder a **Obter Dados** para obter uma nova cópia deste exemplo.

Esperamos que esta apresentação tenha mostrado como os dashboards, as Perguntas e Respostas e os relatórios do Power BI podem fornecer informações sobre os dados do exemplo. Agora, é a sua vez: ligue-se aos seus próprios dados. Com o Power BI, pode ligar-se a uma grande variedade de origens de dados. Para saber mais, veja [Introdução ao serviço Power BI](../fundamentals/service-get-started.md).
