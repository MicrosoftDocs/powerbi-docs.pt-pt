---
title: Utilizar o Modo de Armazenamento no Power BI Desktop (Pré-visualização)
description: Utilizar o Modo de Armazenamento para controlar se os dados estão em cache na memória para os relatórios do Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/23/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 15580cd43e4bb2d286310868a8e853daff04f280
ms.sourcegitcommit: 6faeb642721ee5abb41c04a8b729880c01c4d40e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39211812"
---
# <a name="storage-mode-in-power-bi-desktop-preview"></a>Modo de armazenamento no Power BI Desktop (Pré-visualização)

No **Power BI Desktop**, pode especificar o **modo de armazenamento** das tabelas, o que lhe dá controlo sobre se os dados da tabela estão em cache na memória para os relatórios. 

![Modo de armazenamento no Power BI Desktop](media/desktop-storage-mode/storage-mode_01.png)

A definição do **modo de armazenamento** oferece muitas vantagens. Pode definir o **modo de armazenamento** de cada tabela individualmente no seu modelo, o que permitirá que um único conjunto de dados tire partido de uma ou várias das vantagens seguintes:

* **Desempenho de consultas** – dado que os utilizadores interagem com elementos visuais nos relatórios do Power BI, as consultas DAX são submetidas ao conjunto de dados. A colocação em cache dos dados na memória ao definir corretamente o **modo de armazenamento** pode aumentar o desempenho das consultas e a interatividade dos relatórios.
* **Conjuntos de dados de grandes dimensões** – as tabelas que não estão em cache não consomem memória para fins de colocação em cache. Pode ativar a análise interativa para os conjuntos de dados de grandes dimensões que são muito grandes ou caros para colocar completamente em cache na memória. Pode escolher que tabelas valem a pena colocar em cache e que tabelas não valem a pena.
* **Otimização da atualização de dados** – as tabelas que não estão em cache não precisam de ser atualizadas. Pode reduzir os tempos de atualização ao colocar em cache apenas os dados necessários para cumprir os contratos de nível de serviço e os seus requisitos empresariais.
* **Requisitos de tempo quase real** – as tabelas com requisitos de tempo quase real podem beneficiar de não serem colocadas em cache, para reduzir a latência dos dados.
* **Repetição de escrita** – a repetição de escrita permite que os utilizadores empresariais explorem os cenários hipotético ao alterar os valores das células. As aplicações personalizadas podem aplicar alterações à origem dos dados. As tabelas que não são colocados em cache podem refletir as alterações imediatamente, o que permite uma análise instantânea dos efeitos.

A definição **modo de armazenamento** no **Power BI Desktop** é uma das três funcionalidades relacionadas:

* **Modelos compostos** – permite que um relatório tenha várias ligações de dados, incluindo ligações DirectQuery ou de importação, em qualquer combinação.
* **Relações muitos para muitos** – com os **modelos compostos**, pode estabelecer **relações muitos para muitos** entre as tabelas, ao remover requisitos de valores exclusivos nas tabelas e ao remover soluções alternativas anteriores, como a introdução de novas tabelas apenas para estabelecer relações. 
* **Modo de armazenamento** – agora pode especificar que elementos visuais necessitam de uma consulta às origens de dados de back-end e aqueles que não o exigem serão importados mesmo se se basearem no DirectQuery, o que melhora o desempenho e reduz a carga de back-end. Anteriormente, mesmo os elementos visuais simples como as consultas iniciadas pelas segmentações eram enviadas para as origens de back-end. 

Os três recursos relacionados dos **modelos compostos** desta coleção são descritos em artigos separados:

* Os **modelos compostos** são descritos detalhadamente no seu próprio artigo: [Modelos compostos no Power BI Desktop (Pré-visualização)](desktop-composite-models.md).
* As **relações muitos para muitos** são descritas no seu próprio artigo: [Relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md).
* O **modo de armazenamento** é descrito em detalhe neste artigo.

## <a name="enabling-the-storage-mode-preview-feature"></a>Ativar a funcionalidade de pré-visualização do modo de armazenamento

A funcionalidade **modo de armazenamento** está em Pré-visualização e tem ser ativada no **Power BI Desktop**. Para ativar o **modo de armazenamento**, selecione **Ficheiro > Opções e Definições > Opções > Funcionalidades de Pré-visualização** e, em seguida, selecione a caixa de verificação **modelos compostos**. 

![ativar as funcionalidades de pré-visualização](media/desktop-composite-models/composite-models_02.png)

Terá de reiniciar o **Power BI Desktop** para que a funcionalidade seja ativada.

![reinício necessário para que as alterações entrem em vigor](media/desktop-composite-models/composite-models_03.png)


## <a name="using-the-storage-mode-property"></a>Utilizar a propriedade do modo de armazenamento

O **modo de armazenamento** é uma propriedade que pode ser definida em cada tabela no modelo. Para definir o **modo de armazenamento**, selecione a tabela no painel **Campos** e, em seguida, clique no botão direito do rato para abrir o menu de contexto. No menu de contexto, selecione **Propriedades**.

![Selecionar Propriedades no menu de contexto](media/desktop-storage-mode/storage-mode_02.png)

A seleção do **modo de armazenamento** é mostrada no painel **Propriedades do campo** da tabela. Nesse painel, pode visualizar o **modo de armazenamento** atual ou modificá-lo.

![Definir o modo de armazenamento de uma tabela](media/desktop-storage-mode/storage-mode_03.png)

Há três valores para o **modo de armazenamento**:

* **Importação** – Quando definido como **Importação**, as tabelas importadas são colocadas em cache. As consultas submetidas ao conjunto de dados do Power BI, que devolvem os dados das tabelas, só podem ser preenchidas com os dados em cache.
* **DirectQuery** – Com esta definição, as tabelas DirectQuery não são colocadas em cache. As consultas submetidas ao conjunto de dados do Power BI (por exemplo, as consultas DAX), que devolvem dados de tabelas DirectQuery só podem ser preenchidas com a execução de consultas a pedido na origem dos dados. As consultas submetidas à origem de dados utilizam a linguagem de consulta dessa origem de dados (por exemplo, SQL).
* **Dual** – As tabelas duplas podem atuar como sendo colocadas em cache ou não, o que depende do contexto da consulta enviada para o conjunto de dados do Power BI. Em alguns casos, as consultas são preenchidas com dados em cache; noutros casos, as consultas são preenchidas pela execução de uma consulta a pedido na origem dos dados.

Alterar uma tabela para Importação é uma operação *irreversível*; não é possível alterar novamente para o DirectQuery ou para Dual.

## <a name="constraints-on-directquery-and-dual-tables"></a>Restrições às tabelas DirectQuery e Dual

As tabelas Dual são sujeitas às mesmas restrições que as tabelas DirectQuery. Estas incluem transformações M limitadas e funções DAX restritas nas colunas calculadas. Veja [Implicações da utilização do DirectQuery](desktop-directquery-about.md#implications-of-using-directquery) para obter mais informações.

## <a name="relationship-rules-on-tables-with-different-storage-modes"></a>Regras de relação em tabelas com modos de armazenamento diferentes

As relações devem estar em conformidade com as regras com base no **modo de armazenamento** das tabelas relacionadas. Esta secção fornece exemplos de combinações válidas. Veja [Relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md) para obter informações completas.

Num conjunto de dados com uma única origem de dados, são válidas as seguintes combinações de relação **1 para muitos**:

| Tabela no lado **muitos** | Tabela no lado **1** |
| ------------- |----------------------| 
| Dual          | Dual                 | 
| Importar        | Importação ou Dual       | 
| DirectQuery   | DirectQuery ou Dual  | 

## <a name="propagation-of-dual"></a>Propagação da Dual
Vejamos um exemplo. Considere o seguinte modelo simples, em que todas as tabelas têm uma origem única que suporta a Importação e o DirectQuery.

![Vista de relação de exemplo do modo de armazenamento](media/desktop-storage-mode/storage-mode_04.png)

Digamos que à partida todas as tabelas neste modelo são DirectQuery. Se, em seguida, alterarmos o **modo de armazenamento** da tabela *SurveyResponse* para Importação, é mostrado o seguinte pedido:

![Caixa de diálogo de aviso do modo de armazenamento](media/desktop-storage-mode/storage-mode_05.png)

As tabelas de dimensão (*Cliente*, *Data* e *Geografia*) têm de ser definidas como **Dual** para estar em conformidade com as regras de relação descritas anteriormente. Em vez de exigir que essas tabelas sejam definidas como **Dual** antes do tempo, elas podem ser definidas numa única operação.

A lógica de propagação foi concebida para ajudar nos modelos que incluam muitas tabelas. Digamos que tem um modelo com 50 tabelas e apenas determinadas tabelas de factos (transacionais) precisam de ser colocadas em cache. A lógica no **Power BI Desktop** detecta o conjunto mínimo de tabelas de dimensão que têm de ser definidas como **Dual**, por isso, não precisa de fazê-lo.

A lógica de propagação passa apenas para um lado das relações **1 para-muitos**.

* A alteração da tabela *Cliente* para **Importação** (em vez de alterar *SurveyResponse*) não é permitida devido às suas relações com as tabelas DirectQuery *Vendas* e *SurveyResponse*.
* É permitida a alteração da tabela*Cliente* para **Dual** (em vez de alterar *SurveyResponse*). A lógica de propagação define a tabela *Geografia* também como **Dual**.

## <a name="storage-mode-usage-example"></a>Exemplo de utilização do modo de armazenamento
Vamos continuar com o exemplo da secção anterior e imaginar que aplicamos as seguintes configurações de propriedade do **modo de armazenamento**:

| Tabela                   | Modo de armazenamento         |
| ----------------------- |----------------------| 
| *Vendas*                 | DirectQuery          | 
| *SurveyResponse*        | Importar               | 
| *Data*                  | Dual                 | 
| *Cliente*              | Dual                 | 
| *Geografia*             | Dual                 | 


A definição dessas propriedades do modo de armazenamento tem como resultado os seguintes comportamentos, supondo que a tabela *Vendas* tem um volume de dados significativo.
* As tabelas de dimensão (*Data*, *Cliente* e *Geografia*) são colocadas em cache, pelo que os tempos iniciais de carregamento do relatório devem ser rápidos ao obter os valores de segmentação dos dados a apresentar.
* Não colocar em cache a tabela *Vendas* terá os seguintes resultados:
    * Os tempos de atualização dos dados são melhorados e o consumo de memória é reduzido
    * As consultas dos relatórios baseadas na tabela *Vendas* são executadas no modo DirectQuery, o que pode demorar mais, mas está mais próximo do tempo real porque não é introduzida nenhuma latência de colocação em cache

* As consultas dos relatórios baseadas na tabela *SurveyResponse* são devolvidas da cache na memória e, portanto, devem ser relativamente rápidas.

## <a name="queries-that-hit-or-miss-the-cache"></a>Consultas com acerto ou falha de acerto na cache

Ao ligar o **SQL Profiler** à porta de diagnóstico do **Power BI Desktop**, pode ver as consultas com acerto ou falha de acerto na cache de memória interna ao executar um rastreio com base nos seguintes eventos:

* Eventos de Consultas\Iniciar Consulta
* Processamento de Consultas\Iniciar Consulta Vertipaq SE
* Processamento de Consultas\Iniciar DirectQuery

Para cada evento *Iniciar Consulta*, consulte os outros eventos com o mesmo *ActivityID*. Por exemplo, se não existir um evento *Iniciar DirectQuery*, mas existir um evento*Iniciar Consulta Vertipaq SE*, significa que a consulta foi respondida a partir da cache.

As consultas que fazem referência a tabelas de modo **Dual** retornam dados da cache, se possível. Caso contrário, revertem para o DirectQuery.

Continuando o exemplo anterior, a seguinte consulta refere-se apenas a uma coluna da tabela *Data*, que está no modo **Dual**. Por isso, a mesma deve acertar na cache.

![Script do diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode_06.png)

A seguinte consulta refere-se apenas a uma coluna da tabela *Vendas*, que está no modo **DirectQuery**. Por isso, a mesma *não* deve acertar na cache.

![Script do diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode_07.png)

A seguinte consulta é interessante porque combina as duas colunas. Esta consulta não deve acertar na cache. No início pode esperar obter os valores *CalendarYear* da cache e os valores *SalesAmount* da origem e, em seguida, combinar os resultados, mas isso seria menos eficaz do que a operação SUM/GROUP BY para o sistema de origem. Se a operação estiver a ser enviada para a origem, o número de linhas devolvidas provavelmente será muito menor. 

![Script do diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode_08.png)

> [!NOTE]
> Este comportamento é diferente das [relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md) ao combinar tabelas em cache e tabelas que não estão em cache.

## <a name="caches-should-be-kept-in-sync"></a>As caches devem ser mantidas sincronizadas

As consultas apresentadas na secção anterior mostram que as tabelas **Dual** por vezes acertam na cache e, às vezes, não acertam na cache. Por este motivo, se a cache estiver desatualizada, poderão ser devolvidos valores diferentes. A execução da consulta não tentará dissimular os problemas de dados quando, por exemplo, filtra os resultados do DirectQuery para corresponder aos valores da cache. É da sua responsabilidade conhecer os seus fluxos de dados e criá-los em conformidade. Existem técnicas estabelecidas para lidar com esses casos na origem, se necessário.

O modo de armazenamento **Dual** é uma otimização de desempenho. Só deverá ser utilizado de maneiras que não comprometa a capacidade de satisfazer os requisitos da empresa. Para um comportamento alternativo, considere utilizar as técnicas descritas no artigo [Relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md).

## <a name="data-view"></a>Vista de dados
Se, pelo menos, uma tabela no conjunto de dados tiver o seu **modo de armazenamento** definido como Importação ou Dual, será apresentado o separador **Vista de dados**.

![Vista de dados no Power BI Desktop](media/desktop-storage-mode/storage-mode_09.png)

Quando selecionadas na * Vista de dados**, as tabelas **Dual** e **Importação** apresentam os dados em cache. As tabelas DirectQuery não mostram dados e é apresentada uma mensagem que diz que não é possível apresentar tabelas DirectQuery.


## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações para esta versão do **modo de armazenamento** e a sua correlação com os **modelos compostos**.

As seguintes origens multidimensionais não podem ser utilizadas com **modelos compostos**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI

Ao ligar-se a essas origens multidimensionais através do DirectQuery, também não poderá ligar-se à outra origem do DirectQuery nem combinar com dados importados.

As limitações existentes da utilização do DirectQuery ainda se aplicam ao utilizar os **modelos compostos**. Muitas destas limitações são agora por tabela, de acordo com o **modo de armazenamento** da tabela. Por exemplo, uma coluna calculada numa tabela importada pode referir-se a outras tabelas, mas uma coluna calculada numa tabela DirectQuery está restrita a referir-se apenas às colunas na mesma tabela. As outras limitações aplicar-se-ão ao modelo como um todo se qualquer uma das tabelas no modelo for DirectQuery. Por exemplo, as funcionalidades **QuickInsights** e **Perguntas e Respostas** não estarão disponíveis nos modelos se qualquer uma das tabelas dentro dos mesmos tiverem um **modo de armazenamento** do DirectQuery. 

## <a name="next-steps"></a>Próximos passos

Os artigos seguintes descrevem de forma mais detalhada os modelos compostos e o DirectQuery.

* [Modelos compostos no Power BI Desktop (Pré-visualização)](desktop-composite-models.md)
* [Relações muitos para muitos no Power BI Desktop (Pré-visualização)](desktop-many-to-many-relationships.md)

Artigos do DirectQuery:

* [Utilizar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery no Power BI](desktop-directquery-data-sources.md)

