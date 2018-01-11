---
title: "Exemplo de Rentabilidade do Cliente para o Power BI: faça um tour"
description: "Exemplo de Rentabilidade do Cliente para o Power BI: faça um tour"
services: powerbi
documentationcenter: 
author: amandacofsky
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/29/2017
ms.author: mihart
ms.openlocfilehash: 9a100b7d13c11a8bd066b72a570f45d0c2bc08be
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Exemplo de Rentabilidade do Cliente para o Power BI: faça um tour
O pacote de conteúdo "Exemplo de Lucro do Cliente" contém um dashboard, o relatório e o conjunto de dados para uma empresa que fabrica materiais de marketing. Este dashboard foi criado por um diretor financeiro para ver as métricas chave sobre os 5 gerentes de unidade comercial (também conhecidos como executivos), produtos, clientes e margens brutas (GM). Ela pode ver rapidamente que fatores têm impacto sobre o lucro.

Este exemplo faz parte de uma série de exemplos que ilustra como o Power BI pode ser usado com dados, relatórios e dashoards orientados aos negócios. Os exemplos são dados reais de obviEnce ([www.obvience.com](http://www.obvience.com/)) que foram mantidos anónimos.

Também pode [transferir apenas o conjunto de dados (livro do Excel) para este exemplo](http://go.microsoft.com/fwlink/?LinkId=529781).  
![](media/sample-customer-profitability/power-bi-dash.png)

## <a name="what-is-our-dashboard-telling-us"></a>O que nos diz o nosso dashboard?
### <a name="company-wide-dashboard-tiles"></a>Mosaicos de dashboard de toda a empresa
Esses mosaicos dão ao nosso diretor financeiro métricas de empresa de alto nível importante para ela.  Quando ela vê algo interessante, pode selecionar um mosaico para examinar os dados.

1. A margem bruta da nossa empresa é de 42,5%.
2. Temos 80 clientes.
3. Vendemos 5 produtos diferentes.
4. Tivemos nossa menor % de variação de receita para o orçamento de fevereiro, seguida da nossa maior alta em março.
5. A maioria da nossa receita é proveniente das regiões leste e norte. A margem bruta nunca excedeu o orçamento, com ER-0 e MA-0 exigindo mais investigações.
6. A receita total para o ano é quase o orçamento.

### <a name="manager-specific-dashboard-tiles"></a>Mosaicos do dashboard específico do gerente
Esses mosaicos fornem uma pontuação da equipa. O diretor financeiro deve manter o controlo dos gerentes e esses mosaicos apresentam uma visão geral de alto nível do lucro – utilizando GM %. Se a tendência de % GM é inesperada para qualquer gestor, poderá investigar mais.

A % de Margem Bruta de Annelie é a mais baixa, mas podemos ver um aumento gradual desde março. Valery, por outro lado, teve uma queda na % de GM significante. E Andrew teve um ano volátil. Clique em qualquer um dos mosaicos específicos de gerente para abrir o relatório subjacente. O relatório tem 3 páginas e abre a página "Análise de Margem do Setor".

## <a name="explore-the-pages-in-the-report"></a>Explore outras páginas no relatório
O nosso relatório tem 3 páginas:

* "Tabela de Indicadores da Equipa" centra-se no desempenho dos 5 gestores e dos respetivos "livros de negócio".
* "Análise de Margem do Setor" fornece uma forma de analisar a rentabilidade em comparação com o que se passa em todo o setor.
* "Tabela de Indicadores de Executivos" fornece uma vista de cada um dos gestores formatada para visualização no Cortana.

### <a name="team-scorecard-page"></a>Página de pontuação da equipa
![](media/sample-customer-profitability/customer2.png)

Vejamos os dois membros da equipa em detalhes e que informações podem ser obtidas. Na segmentação à esquerda, selecione o nome de Andrew para filtrar a página de relatório para apresentar apenas os dados dele.

* Para um KPI rápido, veja o **Estado da Receita** de Andrew; está verde. Está a ter um bom desempenho.
* O gráfico de área "% de Variação da Receita do Orçamento por Mês” mostra a exceção para uma queda em fevereiro e Andrew está a ter um desempenho global muito bom. A região dominante é leste e ele manipula 49 clientes e 5 (de 7) produtos. A % de Margem Bruta não é a mais alta nem a mais baixa.
* O "Total da Receita e % de Variação da Receita do Orçamento por Mês" mostra um histórico de lucros estável, mas ao filtrar ao clicar no quadrado **Central** na região treemap, vemos que Andrew apenas tem receita em março e no Indiana. Isto é intencional ou é algo que temos de examinar?

Agora, com Valery. Na segmentação, selecione o nome de Valery para filtrar a página do relatório para exibir apenas os dados sobre ela.  
![](media/sample-customer-profitability/customer3.png)

* Observe o KPI vermelho para **Estado do Total da Receita**. Isto necessita, definitivamente, mais investigação.
* A variação de receita também pinta uma imagem preocupante – ela não atende as margens de receita.
* Valery tem apenas 9 clientes, manipula apenas 2 produtos e funciona quase exclusivamente com os clientes da região norte. Esta especialização poderia explicar as amplas flutuações na métrica.
* Ao selecionar o quadrado **Norte** no treemap mostra que a margem bruta de Valery na região norte é consistente com a respetiva margem geral.
* Ao selecionar os outros quadrados **Região** vemos uma história interessante: a % de Margem Bruta varia entre 23% e 79% e os números de receita, em todas as regiões, exceto no Norte, são extremamente sazonais.

Continue a ler para descobrir por que a área de Valery não apresenta um bom desempenho. Examine as regiões, unidades de negócios e a próxima página do relatório – "Análise de Margem do Setor".

### <a name="industry-margin-analysis"></a>Análise de Margem do Setor
Esta página de relatório fornece uma secção diferente dos dados. Examina a margem bruta para todo o setor, dividido por segmento. O diretor financeiro utiliza essa página para comparar as métricas de unidade da empresa e comercial para métricas do setor para ajudar a explicar tendências e lucro. Deve estar a imaginar por que o gráfico de área "Margem Bruta por Mês e Nome de Executivo” está nesta página, já que é específico de uma equipa. Tê-lo aqui permite-nos filtrar a página pelo gerente da unidade de negócios.  
![](media/sample-customer-profitability/customer6.png)

Como varia o lucro por setor? Como se os produtos e clientes dividem por setor? Selecione um ou mais setores na parte superior esquerda. (iniciar no setor CPG) Para limpar o filtro, selecione o ícone de borracha.

No gráfico de bolhas, o CFO procura as bolhas maiores visto que são as que têm o maior impacto na receita. Filtrar a página por gerente clicando nos nomes no gráfico de área torna fácil ver cada impacto de gerente por segmento do setor.

* A área de influência de Andrew abrange vários setores diferentes com diferentes amplamente % GM (a maioria do lado positivo) e % Var. 
* O gráfico de Annelie é semelhante, exceto que ela apenas se concentra em alguns segmentos de mercado com um foco no segmento Federal e um foco no produto Gladius. 
* Carlos tem um foco claro no segmento de serviços, com bom lucro. Ele aumentou bastante a % de variação para o segmento de Alta Tecnologia e um novo segmento para ele, Industrial, executado muito bem em relação ao orçamento. 
* Tina trabalha com alguns segmentos e tem % GM mais alta, mas o tamanho pequeno em grande parte das suas bolhas mostra que o impacto sobre o resultado da empresa é mínimo. 
* Valery, que é responsável por apenas um produto, trabalha apenas com 5 segmentos de mercado. A influência do setor é sazonal, mas produz sempre uma grande bolha, que indicta um impacto significativo sobre o resultado da empresa. O setor explicar o desempenho negativo?

### <a name="executive-scorecard"></a>Tabela de Indicadores de Executivos
Esta página está formatada como um Cartão de Resposta do Cortana. Para obter mais informações, veja [Criar Cartões de Resposta do Cortana](service-cortana-answer-cards.md)

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Investigue os dados fazendo perguntas em Perguntas e Respostas
Para a nossa análise, seria útil determinar que setor gera a maior parte da receita para Valery. Vamos usar Perguntas e Respostas.

1. Selecione **Power BI** na barra de navegação superior para voltar ao dashboard.
2. Selecione a caixa de pergunta de Perguntas e Respostas na parte superior do dashboard.
   
    ![](media/sample-customer-profitability/customer4.png)
3. Introduza **receita total por setor de Valery**. Observe como a visualização é atualizada conforme digita a pergunta.
   
    ![](media/sample-customer-profitability/customer5.png)
   
   A distribuição é a maior área de receita para Valery.

### <a name="dig-deeper-by-adding-filters"></a>Aprofunde adicionando filtros
Vamos analisar o setor de *Distribuição*.  

1. Volte ao dashboard e selecione o gráfico de área de Andrew de Tendência de Margem Bruta. Isto abre o relatório para a página de "Análise de margem do setor".
2. Sem selecionar nenhuma visualização na página de relatório, expanda o painel de filtro à direita. O painel Filtros deve apresentar apenas filtros ao nível da página.  
   
   ![](media/sample-customer-profitability/power-bi-filters.png)
3. Localize o filtro para **Setor** e selecione a seta para expandir a lista. Vamos adicionar um filtro de página para o setor de Distribuição. Primeiro, desmarque todas as seleções ao desmarcar a caixa de seleção**Selecionar Tudo**. Em seguida, selecione **Distribuição**.  
   
   ![](media/sample-customer-profitability/customer7.png)
4. O gráfico de área "Margem bruta por Mês e o Nome do Executivo" informa que apenas Valery e Tina têm clientes neste setor e Valery só trabalhou com o setor de junho a novembro.   
5. Selecione **Tina** e **Valery** na legenda do gráfico de área "Margem Bruta por Mês e Executivo". Observe a parte de Tina "Receita Total por Produto" é muito pequeno se comparada a Valery. 
6. Para ver a receita real, volte ao dashboard e utilize as Perguntas e Respostas para pedir a **receita total para distribuição por cenário e executivo**.  
   
   ![](media/sample-customer-profitability/customer8.png)

Podemos explorar de forma semelhante a outros setores e até mesmo adicionar clientes aos nossos visuais para compreender as causas para o desempenho de Valery.

Este é um ambiente seguro para experimentar. Pode optar por não guardar as alterações. Mas se as guardar, pode sempre aceder a **Obter Dados** para obter uma nova cópia deste exemplo.

## <a name="next-steps-connect-to-your-data"></a>Próximas etapas: ligar-se aos seus dados
Esperamos que esta tour tenha mostrado como os dashoards do Power BI, perguntas e respostas, e os relatórios podem fornecer informações sobre dados do cliente. Agora é a sua vez, ligue-se aos seus próprios dados. Com o Power BI, é possível ligar-se a uma grande variedade de origens de dados. Saiba mais sobre como [começar a utilizar o Power BI](service-get-started.md).

[Voltar aos Exemplos no Power BI](sample-datasets.md)  

