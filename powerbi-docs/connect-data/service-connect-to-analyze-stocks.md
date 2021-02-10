---
title: Analisar Stocks Populares com Power BI
description: Analisar Stocks Populares com Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 02/09/2021
LocalizationGroup: Connect to services
ms.openlocfilehash: 934451c06927237fd252d60102e2e5db73e31bc1
ms.sourcegitcommit: de3b45cad5ae21c77692ce4490e21de01d21e6f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/10/2021
ms.locfileid: "100082899"
---
# <a name="analyze-popular-stocks-with-power-bi"></a>Analise stocks populares com Power BI

A aplicação da bolsa de valores mostra-lhe vários KPI's para iniciar a sua jornada de análise no Power BI. Você pode usá-lo para acompanhar cotações de fim de dia, bem como tendências semanais, mensais ou anual para stocks populares e ETFs. A aplicação mostra-lhe Power BI em ação, com rastreio de máximos e baixos de stock, médias móveis, distribuição em termos sectoriais, bandas Bollinger e até comparações de desempenho para stocks populares ao longo do tempo.

A aplicação apresenta quatro dashboards:
* **Painel ETF**: Mostra-lhe tendências de fecho para quatro principais índices. 
* **Ações e ETFs Comparação**: Fornece gráficos normalizados facilitam a comparação de ações e EFTs.
* **Análise de Desempenho do Stock**: Permite uma análise detalhada de stocks selecionados com visuais para tendências de fecho, volume, OHLC e bandas Bollinger.
* **Distribuição sectorial : Permite-lhe** quebrar o desempenho do stock por sector.

Pode navegar entre os tabliers utilizando o painel lateral de navegação ou as setas para a frente e para trás no topo direito da página.

![Screenshot da aplicação de stocks.](media/service-connect-to-analyze-stocks/stocks-app.png)

## <a name="etf-dashboard"></a>Painel ETF

O painel de instrumentos da ETF tem visuais que mostram as tendências de fecho de quatro grandes índices. 
* **Nasdaq**: O Índice Composto NASDAQ mede a variação em mais de 3.000 ações negociadas na bolsa da NASDAQ.
* **S&P 500**: S&P 500 é considerado o melhor bitola de ações americanas de grande capital.
* **Dow Jones**: O Dow Jones mostra-lhe o crescimento do mercado de líderes da indústria de TI, como a Microsoft. A tendência de fecho do Dow Jones significa em que tendência tem as ações deste índice encerradas até ao final do dia.
* **Russell 2000**: Russel 2000 é a referência mais comum para os fundos mútuos. O Russell 2000 visuais de tendência de encerramento podem ser usados fornecendo orientação de investimento sobre mais de 2000 stocks de baixa gama.

Uma faixa de corrida no topo do painel de instrumentos mostra-lhe o fecho do dia atual e a variação de preço dos dias anteriores fecha para os quatro índices mostrados na página.

A vista padrão - vista de gráfico - ajuda-o a entender como drasticamente a tendência mudou ao longo do tempo. Pode utilizar os botões de escala de tempo na parte superior esquerda do tablier para escolher ver a tendência durante uma semana, mês ou um ano. Passe o ponteiro sobre a tabela para obter o ponto de dados exato de um dia específico.

![Screenshot da vista do gráfico do painel ETF.](media/service-connect-to-analyze-stocks/etf-dashboard-graph.png)  

No eixo x vê-se o período de tempo e no eixo y vê-se o valor de fecho.

Também pode mudar para um gráfico de castiçais clicando no interruptor de alternação no canto superior direito do painel. Na vista para o castiçal pode ver os preços abertos, altos, baixos e próximos para cada ponto de dados. Passe o ponteiro sobre a tabela para obter o ponto de dados exato de um dia específico.

![Screenshot da vista do castiçal do painel ETF.](media/service-connect-to-analyze-stocks/etf-dashboard-candlestick.png)

## <a name="stocks-and-etfs-comparison"></a>Comparação de existências e ETFs

O painel de comparação de stocks e ETFs mostra-lhe dois gráficos normalizados que facilitam a comparação de ações selecionadas e ETFs.

![Screenshot do painel de comparação de stock selecionar botão.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard.png)

Para utilizar esta página, selecione primeiro as ações que pretende comparar. 
1. Clique no botão **Select**  ![ Screenshot das seleções claras do painel de comparação de stocks.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select.png)
1. Na página **Select Stocks** que aparece, clique em **Limpar** para remover quaisquer seleções anteriores e, em seguida, selecione as ações que deseja comparar Screenshot do painel  ![ de comparação de stocks selecionado.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-clear.png)
1. Clique em **Aplicar**

Depois de ter selecionado as ações que lhe interessam, use a seta dropdown para selecionar as ações específicas que deseja comparar.

![Screenshot do painel de comparação de stocks seleciona dropdown.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-dropdown.png)

## <a name="stock-performance-analysis"></a>Análise do Desempenho do Stock

 O dashboard stock Performance Analysis mostra-lhe kPI's importantes sobre stock selecionado, como o fecho, fecho, aberto, alto e baixo do dia anterior. Selecione a descida para escolher o stock que deseja ver entre as ações que selecionou para análise. Verá que o valor muda depois de clicar no stock à sua escolha.

![Screenshot da análise de desempenho de stock selecionado.](media/service-connect-to-analyze-stocks/stocks-performance-select.png)
 
### <a name="closing-trend"></a>Tendência de encerramento

Pode ver a tendência de fecho para o stock selecionado, e pode optar por alterá-lo para visualização mensal ou vista do ano clicando nos botões no canto superior esquerdo da página. Ter uma vista de um ano irá ajudá-lo a ver em que parte do ano o stock ganhou ou perdeu valor.

![Screenshot das tendências de fecho das ações selecionadas](media/service-connect-to-analyze-stocks/stocks-performance-closing-trend.png)  

### <a name="volume"></a>Volume

Pode olhar para o volume de ações selecionadas deslocando-se para o próximo visual. Você pode pairar num intervalo de tempo para ver o volume de stock nessa parte do ano.

![Screenshot do volume de existências selecionadas](media/service-connect-to-analyze-stocks/stocks-performance-volume.png)
 
### <a name="ohlc-chart"></a>Gráfico de OHLC

Os gráficos ohlc são altamente úteis, uma vez que mostram quatro pontos de dados importantes para um dado stock ao mesmo tempo. Assim, no próximo visual da página, verá o visual ohlc que mostra a abertura, o fecho, o alto e o baixo do stock selecionado. Também pode olhar mais profundamente para os dados alterando a média móvel. 

![Screenshot de OHLC](media/service-connect-to-analyze-stocks/stocks-performance-ohlc.png)

### <a name="bollinger-band"></a>Banda Bollinger

As bandas bollinger usam matemática complexa para mostrar as tendências. Você pode ver uma série de KPI's que estavam em OHLC, e junto com isso você pode ver outras três linhas. A linha do meio mostra a média em movimento. A linha de cima é deslocada por um certo número de desvios padrão e a linha de fundo é deslocada para baixo por um desvio padrão.

![Screenshot da banda bollinger.](media/service-connect-to-analyze-stocks/stocks-performance-bollinger.png) 

## <a name="sectorwise-distribution"></a>Distribuição sectorial

Na página de distribuição sectorial, vê-se as várias ações e o mercado a que pertencem. Se clicar em qualquer um dos sectores, as ações são filtradas e as ações pertencentes ao sector selecionado começarão a aparecer. 

![Screenshot da distribuição sectorial.](media/service-connect-to-analyze-stocks/sector-wise-distribution.png)
 
Em seguida, pode pairar sobre o stock para ver os importantes KPI's, tais como close, close anterior e a diferença. A diferença vai ajudá-lo a entender quanto as ações ganharam ou perderam desde ontem.

![Screenshot do detalhe de distribuição em termos sectoriais.](media/service-connect-to-analyze-stocks/sector-wise-distribution-detail.png)

Pode rolar para baixo para ver todas as ações nessa categoria.
 
Para ver a distribuição do mercado para diferentes sectores temos o visual de "distribuição sectorial", que mostra de cima para baixo os sectores com maior diferença no seu preço de fecho desde o último dia.

![Screenshot da distribuição do mercado para diferentes sectores](media/service-connect-to-analyze-stocks/stocks-comparison-based-on-sector.png)


## <a name="next-steps"></a>Passos seguintes

* [O que são aplicações de modelo power BI](service-template-apps-overview.md)
* [Criar uma aplicação de modelo no Power BI](service-template-apps-create.md)
* [Instalar e distribuir aplicações de modelo na sua organização](service-template-apps-install-distribute.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
