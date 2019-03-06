---
title: Tutorial de visualizações de influenciadores principais
description: Tutorial – criar uma visualização de influenciadores principais no Power BI
author: mihart
manager: kvivek
ms.reviewer: juluczni
ms.service: powerbi
ms.component: powerbi-service
ms.topic: tutorial
ms.date: 02/12/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 1f55a12e306af8a28e297e9feab2f2c0ae0cd60b
ms.sourcegitcommit: 87e81ba92f3d1d65c26f9fc007bf106f96f37bfd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57461678"
---
# <a name="key-influencers-visualization"></a>Visualização de influenciadores principais
O elemento visual de influenciadores principais ajuda a compreender os fatores que estão por trás de uma métrica que seja do seu interesse. Este analisa os seus dados, classifica os fatores que são importantes e apresenta-os como influenciadores principais. Por exemplo, imaginemos que gostaria de descobrir o que influencia a rotatividade dos colaboradores. Um dos fatores pode ser a duração dos contratos de trabalho e outro a idade dos colaboradores. 
 
## <a name="when-to-use-key-influencers"></a>Quando devem ser utilizados os influenciadores principais? 
O elemento visual de influenciadores principais é uma ótima escolha: 
- Para ver quais os fatores que afetam a métrica sob análise.

- Para contrastar a importância relativa destes fatores. Por exemplo, os contratos a curto prazo têm maior impacto sobre a rotatividade do que os contratos a longo prazo? 

## <a name="key-influencer-requirements"></a>Requisitos dos influenciadores principais 
A métrica que está a analisar tem de ser um campo categórico.    


## <a name="features-of-the-key-influencer-visual"></a>Funcionalidades do elemento visual de influenciadores principais

![numeração das funcionalidades](media/power-bi-visualization-influencers/power-bi-ki-numbers-new.png)    

1. ***Separadores*** – selecione um separador para alternar entre vistas. Os influenciadores principais mostram os contribuidores principais para o valor de métrica selecionado. Os segmentos superiores mostram os principais segmentos que contribuem para o valor de métrica selecionado. Um *segmento* é composto por uma combinação de valores.  Por exemplo, um segmento pode ser um conjunto de consumidores que são clientes há pelo menos vinte anos e que vivem na região oeste. 

2. ***Lista pendente*** – o valor da métrica que está a ser investigada. Neste exemplo, podemos observar a **classificação** da métrica e que o valor selecionado é **baixa**.    

3. ***Revisão*** – ajuda-nos a interpretar o elemento visual no painel esquerdo. 

4. ***Painel esquerdo*** – o painel esquerdo contém um elemento visual.  Neste caso, o painel esquerdo mostra-nos uma lista dos influenciadores principais.

5. ***Revisão*** – ajuda-nos a interpretar o elemento visual no painel direito.

6. ***Painel direito*** – o painel direito contém um elemento visual. Neste caso, o gráfico de colunas apresenta todos os valores do **influenciador principal**, o **Tema**, que está selecionado no painel esquerdo. O valor específico (**Usabilidade**) do painel esquerdo está a verde e todos os outros valores de **Tema** estão a preto.

7. ***Linha média*** – a média é calculada para todos os outros valores possíveis de **Tema**, à exceção de **Usabilidade**. Deste modo, o cálculo aplica-se a todos os valores a preto. A média indica-nos a percentagem de outros **Temas** que devolveram uma classificação baixa. Por outras palavras, quando uma classificação é atribuída por um cliente, este também descreve o motivo ou o **tema** da classificação. Alguns dos temas podem ser a utilização, velocidade, segurança, etc. O **Tema** **Usabilidade** é o segundo maior influenciador principal na atribuição de uma classificação baixa, de acordo com o elemento visual no painel esquerdo. Se estabelecermos uma média de todos os outros temas e da respetiva contribuição para uma classificação **baixa**, o resultado será apresentado aqui a vermelho. De todos os outros temas indicados, apenas 11,35% são superiores à **usabilidade**. 

8. ***Caixa de verificação*** – só mostra os valores que são influenciadores.

## <a name="create-a-key-influencers-visual"></a>Criar um elemento visual de influenciadores principais 
 
Veja este vídeo para saber como criar um elemento visual de influenciadores principais e, em seguida, siga os passos abaixo para criar um por si. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/fDb5zZ3xmxU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

O nosso Gestor de Produtos quer descobrir quais são os fatores que levam os clientes a tecer críticas negativas sobre o nosso serviço cloud.  Para acompanhar, abra o [ficheiro PBIX Customer Feedback](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.pbix) (Feedback dos Clientes) no Power BI Desktop. Também pode transferir o [ficheiro do Excel Customer Feedback (Feedback dos Clientes) para o serviço Power BI ou para o Power BI Desktop](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.xlsx). 

> [!NOTE]
> O conjunto de dados Customer Feedback é baseado em [Moro et al., 2014] S. Moro, P. Cortez e P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, junho de 2014 

1. Abra o relatório e selecione o ícone de influenciadores principais.  

    ![No painel Visualizações, selecione o modelo Influenciadores principais](media/power-bi-visualization-influencers/power-bi-template-new.png)

2. Arraste a métrica que pretende investigar para o campo **Analisar**. O campo **Analisar** só suporta variáveis categóricas (não contínuas). Uma vez que temos interesse em observar o que leva os clientes a classificar a qualidade do nosso serviço como **Baixa**, vamos selecionar **Tabela de Clientes** > **Classificação**.    
3. Em seguida, arraste os campos que acredita que podem influenciar a **Classificação** em **Explicar Por**. Pode arrastar os campos que quiser. Neste caso, vamos começar com os seguintes campos: 
    - País/Região 
    - Função na Organização 
    - Tipo de Subscrição 
    - Tamanho da Empresa 
    - Tema     
4. Uma vez que temos interesse nas classificações negativas, selecione **Baixa** no menu pendente em **O que influencia Classificação para que seja**.  

    ![selecionar Baixa no menu pendente](media/power-bi-visualization-influencers/power-bi-key-influencers.png)

A análise é executada ao nível da tabela do campo que está a ser analisado. Neste caso, o nosso interesse está na métrica **Classificação**, que foi definida ao nível do cliente (cada cliente atribuiu uma classificação alta ou baixa). Todos os fatores explicativos têm de ser definidos ao nível do cliente para que o elemento visual os possa utilizar. 

No exemplo acima, todos os fatores explicativos têm uma relação um-para-um ou muitos-para-um com a métrica. Por exemplo, cada classificação tem exatamente um tema associado a si (o tema principal da crítica do cliente). Do mesmo modo, os clientes são provenientes de um país, têm um tipo de subscrição e uma função na respetiva organização. Por conseguinte, estes fatores explicativos já representam os atributos de um cliente e não necessitam de qualquer transformação – o elemento visual pode utilizá-los de imediato. 

Mais adiante neste tutorial, veremos exemplos mais complexos onde nos serão apresentadas relações um-para-muitos. Nesses casos, as colunas têm de ser agregadas ao nível do cliente antes de a análise poder ser executada.  

As medidas e agregações utilizadas como fatores explicativos também são avaliadas ao nível da tabela da métrica **Analisar**. Veremos alguns exemplos mais adiante neste artigo. 

## <a name="interpreting-categorical-key-influencers"></a>Interpretar as categorias de influenciadores principais 
Vejamos os nossos influenciadores principais para classificações baixas. 

### <a name="top-single-factor-influencing-likelihood-of-a-low-rating"></a>Principal fator que influencia a probabilidade de atribuir uma classificação baixa

Na nossa organização, temos três funções: consumidores, administradores e editores. Podemos ver que os consumidores são o principal fator que está a contribuir para a atribuição de classificações baixas. 

![selecionar Função na Organização é consumidor](media/power-bi-visualization-influencers/power-bi-role-consumer.png)


Mais precisamente, existe uma probabilidade 2,57 vezes maior de os nossos clientes nos atribuírem uma classificação negativa. O gráfico de influenciadores principais indica que **Função na Organização é consumidor** está em primeiro lugar na lista à esquerda. Ao selecionar **Função na Organização é consumidor**, o Power BI mostra detalhes adicionais no painel à direita-– a comparação do impacto de cada **função** sobre a probabilidade de uma classificação baixa.
  
- 14,93% dos consumidores atribuem uma classificação baixa  
- Em média, todas as outras funções atribuem uma classificação baixa 5,78% das vezes 
- Assim sendo, os consumidores demonstram uma probabilidade 2,57 vezes maior de atribuírem uma classificação baixa em comparação com as restantes funções (a diferença entre a barra verde e a linha pontilhada a vermelho) 

### <a name="second-single-factor-influencing-likelihood-of-a-low-rating"></a>Segundo maior fator que influencia a probabilidade de atribuir uma classificação baixa

O elemento visual de influenciadores principais consegue comparar e classificar fatores de diversas variáveis diferentes.  O nosso segundo influenciador não tem nenhuma relação com **Função na Organização**.  Selecione o segundo influenciador na lista: **Tema é usabilidade**. 

![selecionar Tema é usabilidade](media/power-bi-visualization-influencers/power-bi-theme.png)

Aqui podemos ver que o segundo fator mais importante está relacionado com o tema da crítica do cliente. Os clientes que comentaram sobre a *usabilidade* do produto apresentaram uma probabilidade 2,21 vezes maior de atribuir uma classificação baixa em comparação com os clientes que comentaram sobre outros temas, como a fiabilidade, design ou velocidade. 

É possível ver que, entre os elementos visuais, a média (linha pontilhada a vermelho) mudou de 5,78% para 11,34%. A média é dinâmica, dado que se baseia no resultado médio de todos os outros valores. No caso do primeiro influenciador, a média excluiu a função de cliente, enquanto no do segundo influenciador excluiu o tema de usabilidade. 
 
Selecionar a caixa na parte inferior do elemento visual fará com que este filtre apenas os valores mais influentes (neste caso, as funções que levam a atribuir uma classificação baixa). Deste modo, dos 12 temas passamos a ver apenas os quatro que o Power BI identificou como responsáveis por promover classificações baixas. 

![selecionar caixa de verificação](media/power-bi-visualization-influencers/power-bi-only-show.png)

## <a name="interacting-with-other-visuals"></a>Interagir com outros elementos visuais 
 
Sempre que um utilizador clicar numa segmentação de dados, filtro ou noutro elemento visual na tela, o elemento visual de influenciadores principais volta a executar a respetiva análise na nova parcela de dados. Por exemplo, vamos arrastar o campo Tamanho da Empresa para o relatório e utilizá-lo como uma segmentação de dados. Queremos ver se os influenciadores principais dos nossos clientes empresariais (o tamanho da empresa é superior a 50 000 pessoas) são diferentes dos da população geral.  
 
Ao selecionar **>50 000**, a análise é executada novamente e podemos ver que os influenciadores mudaram. Para grandes clientes empresariais, o principal influenciador para a atribuição de classificações baixas é um **Tema** relacionado com **segurança**. Podemos investigá-lo mais detalhadamente para ver se existem funcionalidades de segurança específicas com que os nossos clientes de grande dimensão estão insatisfeitos. 

![segmentação por tamanho da empresa](media/power-bi-visualization-influencers/power-bi-filter.png)

## <a name="interpreting-continuous-key-influencers"></a>Interpretar influenciadores principais contínuos 
 
Até agora, utilizámos o elemento visual para explorar como os diversos campos categóricos influenciam a atribuição de classificações baixas. Também é possível mover fatores contínuos (por exemplo, idade, altura, preço) para o campo "Explicar por". Vejamos o que acontece se largarmos o campo "Antiguidade" da tabela Cliente em "Explicar por". A Antiguidade descreve há quanto tempo o cliente tem estado a utilizar o serviço. 
 
Podemos concluir que, à medida que a **Antiguidade** aumenta, a probabilidade de receber uma classificação mais baixa também cresce. Esta tendência sugere que, na verdade, a probabilidade de os nossos clientes de longa duração atribuírem uma classificação negativa é maior. Esta é uma informação interessante e que poderá ser útil abordar mais tarde.  
 
A visualização indica-nos que sempre que a antiguidade sobe para 13,44 meses, a probabilidade de receber uma classificação baixa torna-se 1,23 vezes superior em média. Neste caso, o valor de 13,44 meses descreve o desvio-padrão da antiguidade. Por isso, a informação que obtivemos analisa a forma como o aumento da antiguidade numa quantidade padrão (o desvio-padrão da antiguidade) afeta a probabilidade de receber uma classificação baixa. 
 
O gráfico de dispersão do lado direito mostra a percentagem média de classificações baixas para cada valor de antiguidade e inclui uma linha de tendência que realça o declive.  


![gráfico de dispersão do valor Antiguidade](media/power-bi-visualization-influencers/power-bi-tenure.png)

## <a name="interpreting-measuresaggregate-as-key-influencers"></a>Interpretar medidas/agregações como influenciadores 
 
Por fim, os utilizadores também podem utilizar medidas e agregações como fatores explicativos nas respetivas análises. Por exemplo, podemos querer ver o impacto que o número de pedidos de suporte dos clientes ou a duração média de um pedido em aberto têm sobre a classificação que recebemos. 
 
Neste caso, queremos ver se o número de pedidos de suporte de um cliente tem influência sobre a classificação que o mesmo nos atribui. Vamos incluir o ID de pedido de suporte da tabela Pedido de Suporte. Visto que um cliente pode ter múltiplos pedidos de suporte, temos de agregar o ID ao nível do cliente. Esta agregação é importante, dado que estamos a executar a análise ao nível do cliente e, por isso, todos os controladores têm de ser definidos para esse mesmo nível de granularidade. 
 
Vamos analisar a contagem de IDs (para que seja associada uma contagem de pedidos de suporte a cada linha de cliente). Neste caso, podemos ver que, à medida que a contagem de pedidos de suporte aumenta, a probabilidade de as classificações serem baixas torna-se 5,51 vezes superior. O elemento visual do lado direito mostra-nos o número médio de pedidos de suporte segundo diferentes valores de Classificação (avaliado ao nível do cliente). 

![influência do ID de Pedido de Suporte](media/power-bi-visualization-influencers/power-bi-support-ticket.png)



## <a name="interpreting-the-results-top-segments"></a>Interpretar os resultados: segmentos superiores 
 
Embora o separador "Influenciadores principais" permita que os utilizadores avaliem cada fator individualmente, estes podem mudar para "Segmentos superiores" para verem como uma combinação de fatores afeta a métrica que estão a analisar. 
 
Inicialmente, os segmentos superiores mostram uma descrição geral de todos os segmentos detetados pelo Power BI. No exemplo abaixo, podemos ver que foram detetados seis segmentos. Estes segmentos são ordenados segundo a percentagem de classificações baixas em cada segmento. Por exemplo, o segmento 1 possui 74,3% das classificações baixas atribuídas pelos clientes.  Quanto maior for a bolha, maior será a proporção de classificações baixas. O tamanho da bolha do lado oposto representa a quantidade de clientes que se encontram no segmento. 

![selecionar o separador Segmentos Superiores](media/power-bi-visualization-influencers/power-bi-top-segments-tab.png)

Ao selecionar uma bolha, os detalhes do segmento em questão são apresentados. Por exemplo, se selecionarmos o Segmento 1, podemos ver que este é composto por clientes já relativamente estabelecidos (estão connosco há 29 meses) com um número elevado de pedidos de suporte (mais de 4 pedidos). Por fim, não são editores (por isso, tratam-se de consumidores ou administradores).  
 
Neste grupo, 74,3% das pessoas atribuiu uma classificação baixa. O cliente comum atribui uma classificação baixa 11,7% das vezes, pelo que este segmento mostra uma proporção de classificações baixas significativamente maior (63% superior). Podemos ver também que o segmento 1 contém aproximadamente 2,2% dos dados, representando uma parte considerável da população. 

![selecione o primeiro segmento superior](media/power-bi-visualization-influencers/power-bi-top-segments2.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas 
 
**Quais são as limitações de pré-visualização?** 
 
Atualmente, o elemento visual de influenciadores principais encontra-se no modo de pré-visualização pública e existem várias limitações das quais os utilizadores devem ter conhecimento. As funcionalidades atualmente indisponíveis incluem o seguinte: 
- Análise de métricas que são agregados/medidas 
- Consumo do elemento visual no Power BI Embedded
- Consumo do elemento visual em aplicações móveis do Power BI
- Suporte para RLS 
- Suporte para Consultas Diretas 
- Suporte para Ligações em Direto 
 
**Estou a ver um erro que indica que não foram encontrados influenciadores/segmentos. Porque é que isto acontece?**  

![erro – não foram encontrados influenciadores](media/power-bi-visualization-influencers/power-bi-error1.png)


Este erro ocorre caso tenha incluído campos em **Explicar por** sem terem sido encontrados influenciadores.   
- Incluiu a métrica que analisou em "Analisar" e "Explicar por" (deve removê-la de **Explicar por**) 
- Os seus campos explicativos contêm demasiadas categorias com poucas observações. Isto dificulta a capacidade da visualização de determinar os fatores que são influenciadores, pois é difícil tirar conclusões gerais com base em apenas algumas observações 
- Os seus fatores explicativos têm um número de observações suficiente para produzir generalizações, mas a visualização não encontrou nenhuma correlação significativa a relatar 
 
**Estou a ver um erro que indica que a métrica que estou a analisar não tem dados suficientes para executar a análise. Porque é que isto acontece?**  

![erro – não existem dados suficientes](media/power-bi-visualization-influencers/power-bi-not-enough-data.png)

A visualização funciona através da observação de padrões nos dados de um determinado grupo (por exemplo, os clientes que atribuíram classificações baixas) em comparação com outros grupos (por exemplo, os clientes que atribuíram classificações altas). Se os dados no seu modelo tiverem poucas observações, será difícil encontrar padrões. Se a visualização não tiver dados suficientes para encontrar influenciadores relevantes, indicará que são necessários mais dados para executar a análise. Recomendamos que tenha, no mínimo, 100 observações para o estado selecionado (clientes que abandonam o serviço) e pelo menos 10 observações para os estados que está a utilizar para efeitos de comparação (clientes que não abandonam o serviço).  
 
**Estou a ver um erro que indica que um campo em "Explicar por" não tem uma relação exclusiva com a tabela que contém a métrica que estou a analisar. Porque é que isto acontece?**  
 
A análise é executada ao nível da tabela do campo que está a ser analisado. Por exemplo, se estiver a analisar o feedback dos clientes sobre o seu serviço, poderá ter uma tabela que lhe indica se um cliente atribuiu uma classificação baixa ou alta. Neste caso, a sua análise seria executada ao nível da tabela de clientes. 

Se tiver uma tabela relacionada definida a um nível mais detalhado do que a tabela que contém a sua métrica, irá deparar-se com este erro. Vamos ilustrar este cenário com um exemplo: 
 
- Suponhamos que está a analisar o que leva os seus clientes a atribuírem classificações baixas ao seu serviço 
- Tem interesse em ver se o dispositivo no qual os clientes utilizam o seu serviço tem influência sobre as respetivas críticas 
- Um cliente pode utilizar o serviço de múltiplas formas diferentes   
- No exemplo abaixo, o cliente n.º 10 000 000 utiliza um browser e um tablet para interagir com o serviço 

![erro – se tiver uma tabela relacionada definida a um nível mais detalhado do que a tabela que contém a sua métrica](media/power-bi-visualization-influencers/power-bi-error2.png)

Se tentar utilizar a coluna de dispositivos como um fator explicativo, verá o seguinte erro: 

![error – coluna errada](media/power-bi-visualization-influencers/power-bi-error3.png)

Isto acontece porque o dispositivo não está definido ao nível do cliente, onde este pode utilizar o serviço em múltiplos dispositivos. Para que a visualização possa encontrar padrões, o dispositivo tem de se tornar um atributo do cliente. Neste caso, dispomos de várias soluções consoante a nossa compreensão do negócio: 
 
- Por exemplo, podemos alterar o resumo do dispositivo para contabilizar o número de dispositivos que podem afetar a classificação atribuída por um cliente 
- Podemos dinamizar a coluna de dispositivos para ver se a utilização do serviço num dispositivo específico tem influência sobre a classificação de um cliente  
 
Neste exemplo, dinamizámos os dados de modo a criar novas colunas para "browser", "telemóvel" e "tablet". Agora podemos utilizar estes valores em "Explicar por". Descobrimos que todos os dispositivos são influenciadores e que a utilização de um browser tem o maior impacto sobre a classificação dos clientes. 

Mais precisamente, os clientes que não utilizam o browser para consumir o serviço apresentam uma probabilidade 3,79 vezes maior de atribuir uma classificação do que os utilizam o browser. Podemos ver mais abaixo na lista que, no caso dos telemóveis, se regista o inverso. Os clientes que utilizam a aplicação móvel apresentam maior probabilidade de atribuir uma classificação baixa do que aqueles que não a utilizam.  

![erro – resolvido](media/power-bi-visualization-influencers/power-bi-error3-solution.png)

**Estou a ver um aviso a indicar que as medidas não foram incluídas na minha análise. Porque é que isto acontece?** 

![erro – medidas não incluídas](media/power-bi-visualization-influencers/power-bi-measures-not-included.png)


A análise é executada ao nível da tabela do campo que está a ser analisado. Se estiver a analisar a rotatividade dos clientes, poderá ter uma tabela que lhe indica se um cliente abandonou ou não o serviço. Neste caso, a sua análise seria executada ao nível da tabela de clientes.
 
Por predefinição, as medidas e agregações são analisadas ao nível da tabela. Se tivéssemos uma medida para "Média de gastos mensais", a mesma seria analisada ao nível da tabela de clientes.  

Se a tabela de clientes não tiver um identificador exclusivo, não podemos avaliar a medida e esta é ignorada pela análise. Para evitar esta situação, certifique-se de que a tabela com a sua métrica (neste caso, a tabela de clientes) contém um identificador exclusivo (por exemplo, um ID de cliente). Também é bastante simples adicionar uma coluna de índice através do Power Query.
 
**Estou a ver um aviso a informar que a métrica que estou a analisar contém mais de 10 valores exclusivos e que isto pode afetar a qualidade da minha análise. Porque é que isto acontece?**  

A visualização de IA está otimizada para a análise de categorias (por exemplo, Abandono é "Sim" ou "Não", Satisfação do Cliente é "Alta", "Média" ou "Baixa", etc.) Aumentar o número de categorias a analisar significa que temos menos observações por categoria, tornando mais difícil para a visualização encontrar padrões nos dados. 

Para encontrar influenciadores mais fiáveis, é recomendável agrupar os valores semelhantes numa única unidade. Por exemplo, se tiver uma métrica para o preço, é provável que obtenha melhores resultados ao agrupar preços semelhantes em grupos como "Alto", "Médio", "Baixo", ao invés de utilizar níveis de preço individuais. 

![erro – existem mais de 10 fatores exclusivos](media/power-bi-visualization-influencers/power-bi-error4.png)


**Existem fatores nos meus dados que aparentam tratar-se de influenciadores principais, embora não o sejam. Como é que isto pode acontecer?**

No exemplo abaixo, podemos ver que os clientes que são consumidores contribuem para o número de classificações baixas (14,93% das classificações são baixas). Curiosamente, a função de administrador também mostra uma proporção elevada de classificações baixas (13,42%), embora não seja considerada um influenciador. 

Tal deve-se ao facto de a visualização também ter em consideração o número de pontos de dados ao procurar influenciadores. No exemplo abaixo, temos mais de 29 000 consumidores e um número de administradores 10 vezes menor (cerca de 2900). Além disso, apenas 390 atribuíram uma classificação baixa. Portanto, o elemento visual não tem dados suficientes para determinar se encontrou realmente um padrão com classificações dos administradores ou se apenas detetou uma hipótese.  

![erro – forma como os influenciadores são determinados](media/power-bi-visualization-influencers/power-bi-error5.png)

**Como se calculam os influenciadores principais?**

A visualização de IA utiliza [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) para executar uma regressão logística em segundo plano para calcular os influenciadores principais. Uma regressão logística é um modelo estatístico que compara diferentes grupos entre si. Se examinássemos o que motiva a atribuição de classificação baixas, a regressão logística avaliaria a forma como os clientes que atribuíram uma classificação baixa diferem daqueles que atribuíram uma classificação alta. Se tivéssemos múltiplas categorias (classificação alta, neutra e baixa), passaríamos a analisar a forma como os clientes que atribuíram uma classificação baixa diferem daqueles que não atribuíram uma classificação baixa (como diferem de quem atribuiu uma classificação alta OU uma classificação neutra). 
 
A regressão logística procura padrões nos dados, analisando a forma como os clientes que atribuíram uma classificação baixa podem diferir dos que atribuíram uma classificação alta. Por exemplo, a regressão pode apurar que os clientes com maior número de pedidos de suporte atribuíram uma percentagem de classificações baixas bastante maior do que os clientes com poucos ou nenhum pedido de suporte.
 
A regressão logística também tem em consideração a quantidade de pontos de dados existentes. Se, por exemplo, os clientes com uma função de administrador atribuíssem uma proporção maior de classificações negativas, mas só existisse um número restrito de administradores, tal não seria considerado um fator influente. Tal acontece porque não existem pontos de dados suficientes para deduzir que há um padrão. Um teste estatístico (teste de Wald) é utilizado para determinar se um fator pode ser considerado um influenciador. O elemento visual utiliza um valor-p de 0,05 para determinar o limite. 


**Como se calculam os segmentos?**

A visualização de IA utiliza [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) para executar uma árvore de decisões de forma a detetar subgrupos de interesse. O objetivo da árvore de decisões consiste em obter um subgrupo de pontos de dados relativamente alto na métrica em que estamos interessados (por exemplo, os clientes que atribuíram uma classificação baixa). 

A árvore de decisões analisa cada fator explicativo e tenta determinar qual deles proporciona a melhor "divisão". Por exemplo, se filtrarmos os dados de modo a incluir apenas clientes empresariais de grande dimensão, será que essa ação irá separar os clientes que atribuíram uma classificação alta dos que atribuíram uma classificação baixa? Por outro lado, será melhor filtrar os dados de forma a incluir apenas os clientes que fizeram comentários sobre a segurança? 

Quando a árvore de decisões efetua uma divisão, utiliza esse subgrupo de dados (por exemplo, os clientes que fizeram comentários sobre a segurança) e tenta determinar qual seria a melhor divisão seguinte para esses dados. Depois de cada divisão, a árvore também toma em consideração se tem pontos de dados suficientes que tornem significativo inferir um padrão deste grupo ou se apenas se trata de uma anomalia nos dados e, como tal, não representa um segmento verdadeiro. (É aplicado outro teste estatístico para verificar a significância estatística da condição de divisão, com um valor-p de 0,05). 

Assim que a execução da árvore de decisões terminar, esta reúne todas as divisões (comentários sobre segurança, empresas de grande dimensão) e cria filtros do Power BI. Esta combinação de filtros é agrupada como um segmento no elemento visual. 
 
**Porque é que determinados fatores se tornam influenciadores/deixam de ser influenciadores à medida que arrasto mais campos para "Explicar Por"?**

A visualização avalia todos os fatores explicativos em conjunto. Isto significa que, embora um fator em si possa ser um influenciador, é possível que não o seja ao ser considerado juntamente com outros fatores. Suponha que estamos a analisar o que faz com que o preço de uma casa seja alto, tendo os quartos e o tamanho da casa como fatores explicativos: 
- Por si só, um número de quartos maior pode fazer com que os preços das casas sejam altos 
- A inclusão do tamanho da casa na análise significa que agora estamos a avaliar o que acontece aos quartos ao manter o tamanho da casa constante 
- Se definirmos o tamanho da casa para 139,35 metros quadrados, é improvável que incluir continuamente mais quartos aumente drasticamente o preço da casa. O fator Quartos pode perder a importância que tinha antes de considerarmos o tamanho da casa. 




## <a name="next-steps"></a>Próximos passos
[Gráficos de combinação no Power BI](power-bi-visualization-combo-chart.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
