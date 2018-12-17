---
title: Conjuntos de dados de grande dimensão, limites de pontos de dados e estratégias de dados
description: Limites de dados para elementos visuais e estratégias de redução de dados
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 125787bab3892f2e9616866a9d5487837131d0ed
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2018
ms.locfileid: "52981497"
---
# <a name="data-point-limits-and-strategies-by-visual-type"></a>Limites de pontos de dados e estratégias por tipo de elemento visual

Quando um elemento visual é composto no Power BI, a visualização tem de ser rápida e precisa. Isso implica algoritmos subjacentes configurados para cada tipo de elemento visual. Os elementos visuais no Power BI têm de ser suficientemente flexíveis para lidar com diferentes tamanhos de conjuntos de dados. Alguns conjuntos de dados têm apenas alguns pontos de dados, enquanto outros têm petabytes. Este artigo explica as estratégias utilizadas pelo Power BI para compor as visualizações.

## <a name="data-reduction-strategies"></a>Estratégias de redução de dados
Cada elemento visual emprega uma ou mais *estratégias de redução de dados* para processar os volumes de dados potencialmente grandes a ser analisados. Até mesmo uma simples tabela emprega uma estratégia para evitar o carregamento do conjunto de dados completo no cliente.  A estratégia de redução utilizada varia consoante o tipo de elemento visual. Cada elemento visual seleciona uma das *estratégias de redução de dados* suportadas como parte do processo de geração do pedido de dados enviado para o servidor. 

Cada elemento visual controla os parâmetros dessas estratégias de modo a influenciar o volume de dados global.   

## <a name="strategies"></a>Estratégias
Para cada estratégia, existem predefinições com base na forma e no tipo de dados que estão a ser visualizados. No entanto, as predefinições podem ser substituídas, no painel de Formatação do Power BI, para proporcionar a experiência de utilizador certa. 

* **Apresentação de Dados em Janelas** (Segmentação): Permitir que os utilizadores percorram os dados num elemento visual ao carregar progressivamente fragmentos do conjunto de dados global.
* **TopN**: Mostrar apenas os primeiros X itens.
* **Amostra Simples**: Mostrar o primeiro, o último e X itens uniformemente distribuídos pelo meio.
* **BottomN**: Mostrar apenas os últimos X itens.  Útil na monitorização de dados atualizados com frequência.
* **Amostragem de elevada densidade** - Um algoritmo de amostragem melhorado que respeita melhor os valores atípicos e/ou a forma de uma curva.
    * **Amostragem de linhas posicionadas** - Pontos de dados de exemplo baseados em valores atípicos presentes em posições ao longo de um eixo
    * **Amostragem de pontos sobrepostos** - Pontos de dados de exemplo baseados em valores sobrepostos para preservar valores atípicos

## <a name="statistics"></a>Estatísticas
Certos modelos podem fornecer estatísticas sobre o número de valores de determinadas colunas. Quando essas informações existem, é possível tirar partido delas para proporcionar um melhor equilíbrio entre as várias hierarquias, se um elemento visual não substituir explicitamente o número de valores de uma estratégia.

Para obter mais informações, veja o artigo [Novidades do Analysis Services](https://docs.microsoft.com/en-us/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017)

## <a name="dynamic-limits"></a>Limites dinâmicos
Para além das estratégias mencionadas acima, os elementos visuais com duas hierarquias de colunas de agrupamento (eixo e legenda ou categoria e série) utilizam uma estratégia adicional chamada *limites dinâmicos*.  Os limites dinâmicos foram concebidos para equilibrar melhor os pontos de dados. 

Os limites dinâmicos oferecem uma melhor seleção de pontos para dados dispersos do que os limites estáticos. Por exemplo, é possível configurar um elemento visual para selecionar 100 categorias e 10 séries com um total de 1000 pontos. No entanto, os dados reais têm 50 categorias e 20 séries.  Quando a consulta é executada em runtime, os limites dinâmicos selecionam a totalidade das 20 séries para preencher os 1000 pontos pedidos.

Os limites dinâmicos são aplicados automaticamente quando o servidor tem a capacidade para tal, conforme indicado abaixo:

* No Power BI Desktop com a versão 2016 ou superior do SSAS no Local para [tirar partido das capacidades de SuperDax do servidor](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* No serviço Power BI e de Ambiente de Trabalho ao utilizar um modelo importado, a Consulta Direta, a ligação em direto ao serviço ou a ligação em direto a AS PaaS. 

* No serviço Power BI, quando é estabelecida a ligação através de um gateway no local ao SSAS no local, não é possível utilizar limites dinâmicos. O gateway no local não suporta totalmente a estratégia de limites dinâmicos que devolve uma estrutura de conjuntos de resultados diferente a partir do SSAS no local.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Estratégias e limites de pontos de dados por tipo de elemento visual

### <a name="area-chart"></a>Gráfico de área
Veja [Como funciona a amostragem de linhas](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Gráfico de barras/colunas
- Quando em modo de categorização
    - Categorias: virtualização com utilização de Janela de 500 linhas de cada vez
    - Série: Primeiros 60
    - Quando em modo escalar (pode usar limites dinâmicos)
        - N.º máximo de pontos: 10 000
        - Categorias: Amostra de 500 valores
        - Série: Primeiros 20 valores

### <a name="card-multirow"></a>Cartão (multilinha) 
- Valores: virtualização com utilização de Janela de 200 linhas de cada vez

### <a name="combo-chart"></a>Gráfico de combinação
 Utiliza as mesmas estratégias que o gráfico de colunas. Tenha em atenção que a linha no **gráfico de combinação** não utiliza o algoritmo de elevada densidade utilizado pelo **gráfico de linhas**.

### <a name="custom-visuals"></a>Elementos visuais personalizados
Pode obter até 30.000, mas cabe os autores dos elementos visuais indicar as estratégias a utilizar

### <a name="doughnut"></a>Anel
- N.º máximo de pontos: 3500
- Grupo: Primeiros 500
- Detalhes: Primeiros 20

### <a name="filled-map-choropleth"></a>Coropleto de mapa de manchas 
O mapa de manchas pode utilizar estatísticas ou limites dinâmicos. O Power BI tenta utilizar a redução pela seguinte ordem: limites dinâmicos, estatísticas e, por último, configuração. 
- N.º máximo de pontos: 10 000
- Categorias: Primeiros 500
- Série (quando X e Y estão ambos presentes): Primeiros 20

### <a name="funnel"></a>Funil
- N.º máximo de pontos: 3500
- Categorias: Primeiros 3500

### <a name="kpi"></a>KPI
- Eixo de tendência
- Últimos 3500

### <a name="line-chart"></a>Gráfico de linhas
Veja [Como funciona a amostragem de linhas](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Gráfico de linhas, elevada densidade
Veja [Amostragem de elevada densidade](../desktop-high-density-sampling.md)

### <a name="map"></a>Mapa 
- N.º máximo de pontos: 3500

Dependendo da configuração, um mapa pode ter:
- Localização: Primeiros 3500
- Localização, Tamanho: Primeiros 3500
- Localização, Latitude e Longitude como agregações (Tamanho + /-): Primeiros 3500
- Latitude, Longitude: veja [Dispersão de elevada densidade](desktop-high-density-scatter-charts.md)
- Latitude, Longitude, Tamanho: Primeiros 3500
- Legenda, Latitude, Longitude: veja [Dispersão de elevada densidade](desktop-high-density-scatter-charts.md)
- Legenda, Latitude, Longitude, Tamanho: Primeiras 233 legendas, Primeiras 15 latitudes e longitudes (pode utilizar estatísticas ou limites dinâmicos)
- Localização, Legenda, Latitude, Longitude como agregações (Tamanho + /-): Primeiras 233 localizações, Primeiras 15 legendas (pode utilizar estatísticas ou limites dinâmicos)

### <a name="matrix"></a>Matriz
- Linhas: virtualização com utilização de Janela de 500 linhas de cada vez
- Colunas: Primeiras 100 colunas de agrupamento 
- Valores: valores múltiplos não contam para a redução de dados

### <a name="radial-gauge"></a>Medidor radial
Sem estratégia de redução

### <a name="slicer"></a>Segmentação de Dados
- Valores: virtualização com utilização de Janela de 200 linhas de cada vez

### <a name="scatter-chart-high-density"></a>Gráfico de dispersão (elevada densidade)
Veja [Dispersão de elevada densidade](https://docs.microsoft.com/en-us/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Circular
- N.º máximo de pontos: 3500
- Grupo: Primeiros 500
- Detalhes: Primeiros 20

### <a name="r--python-visuals"></a>Elementos visuais de R e Python
Limitado a 150.000 linhas. Se forem selecionadas mais de 150.000 linhas, apenas as primeiras 150.000 linhas são utilizadas

### <a name="ribbon-chart"></a>Gráfico do friso
- Quando em modo de categorização
    - Categorias: virtualização (apresentação de dados em janelas) com utilização de Janela de 500 linhas de cada vez
    - Série: Primeiros 60
    - Quando em modo escalar (pode usar limites dinâmicos)
        - N.º máximo de pontos: 10 000
        - Categorias: Amostra de 500 valores
        - Série: Primeiros 20 valores

### <a name="shape-map"></a>Mapa de forma
O mapa de manchas pode utilizar estatísticas ou limites dinâmicos. 
- N.º máximo de pontos: 10 000
- Categorias: Primeiros 500
- Série (quando X e Y estão ambos presentes): Primeiros 20

### <a name="table"></a>Tabela
- Valores: virtualização (apresentação de dados em janelas) com utilização de Janela de 500 linhas de cada vez

### <a name="tree-map-this-could-use-statistics-or-dynamic-limits"></a>Mapa de árvore (pode utilizar estatísticas ou limites dinâmicos)
- N.º máximo de pontos: 3500
- Grupo: Primeiros 500
- Detalhes: Primeiros 20

### <a name="waterfall-chart"></a>Gráfico de cascata
- Quando existe apenas o registo de categoria
    - N.º máximo de pontos: 3500
    - Categoria apenas - Primeiros 3500
- Quando categoria e divisão estão ambas presentes
    - Categoria: virtualização (apresentação de dados em janelas) com utilização de Janela de 30 linhas de cada vez
    - Divisão - Primeiros 200 valores


## <a name="next-steps"></a>Próximos passos
[Tipo de visualização](power-bi-report-visualizations.md)
