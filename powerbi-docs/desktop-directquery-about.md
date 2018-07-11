---
title: Utilizar o DirectQuery no Power BI
description: Compreender a utilização do DirectQuery com o Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ed9ab95aace7ab1ff0774732241bdd4a7fffcb15
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37600995"
---
# <a name="using-directquery-in-power-bi"></a>Utilizar o DirectQuery no Power BI
Pode ligar a todos os diversos tipos de origens de dados quando utiliza o **Power BI Desktop** ou o **serviço Power BI** e pode efetuar essas ligações de dados de formas diferentes. Pode *importar* dados para o Power BI, que é a forma mais comum de obtê-los ou pode ligar-se diretamente aos dados no respetivo repositório de origem original, o que é conhecido como **DirectQuery**. Este artigo descreve o **DirectQuery** e respetivas capacidades, incluindo os seguintes tópicos:

* Diferentes opções de conectividade para o DirectQuery
* Orientações para quando deve considerar a utilização do DirectQuery em vez da importação
* Desvantagens da utilização do DirectQuery
* Melhor prática para a utilização do DirectQuery

Em suma, a melhor prática para utilizar a importação face ao DirectQuery é a seguinte:

* Deve **importar** os dados para o Power BI sempre que possível. A importação tira partido do motor de consultas de elevado desempenho do Power BI e proporciona uma experiência de utilização dos dados altamente interativa e avançada.
* Se os objetivos não puderem ser alcançados através da importação de dados, considere utilizar o **DirectQuery**. Por exemplo, se os dados são alterados muitas vezes e os relatórios têm de refletir os mais recentes, o DirectQuery poderá ser a melhor opção. No entanto, a utilização do DirectQuery só é, geralmente, exequível se a origem de dados subjacente puder fornecer consultas interativas (menos de 5 segundos) para as consultas de agregação típicas e conseguir lidar com a carga de consultas que será gerada. Além disso, a lista de limitações que acompanham a utilização do DirectQuery deve ser analisada cuidadosamente, para garantir que os seus objetivos ainda podem ser cumpridos.

O conjunto de capacidades que o Power BI oferece nos dois modos de conectividade – importação e DirectQuery – vai evoluir ao longo do tempo. Estas capacidades incluem a disponibilização de mais flexibilidade na utilização dos dados importados, para que a importação possa ser utilizada em mais casos, bem como a eliminação de algumas das desvantagens do DirectQuery. Independentemente dos melhoramentos, quando utiliza o DirectQuery, o desempenho da origem de dados subjacente será sempre uma das principais considerações. Se a origem de dados subjacente estiver lenta, a utilização do DirectQuery nessa origem continuará a ser pouco exequível.

Este tópico abrange o DirectQuery com o Power BI, mas não com o SQL Server Analysis Services. O DirectQuery também é uma funcionalidade do **SQL Server Analysis Services** e, embora muitos dos detalhes descritos abaixo se apliquem à sua utilização, também existem diferenças importantes. Para obter informações sobre como utilizar o DirectQuery com o SQL Server Analysis Services, veja [o documento técnico que mostra em pormenor o DirectQuery no SQL Server Analysis Services 2016](http://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).  

Este artigo debruça-se sobre o fluxo de trabalho recomendado para o DirectQuery, no qual o relatório é criado no **Power BI Desktop**, mas também explica como ligar diretamente no **serviço Power BI**.

## <a name="power-bi-connectivity-modes"></a>Modos de conectividade do Power BI
O Power BI liga-se a um grande número de diferentes origens de dados, que incluem:

* Serviços online (Salesforce, Dynamics 365, entre outros)
* Bases de dados (SQL Server, Access, Amazon Redshift, entre outros)
* Ficheiros simples (Excel, JSON, entre outros)
* Outras origens de dados (Spark, Web sites, Microsoft Exchange, entre outros)

Normalmente, nestas origens de dados, é possível importar os dados para o Power BI. Em algumas, também é possível ligar com o DirectQuery. O conjunto exato de origens que suportam o DirectQuery está descrito no artigo [Data Sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origens de Dados que o DirectQuery suporta). Serão disponibilizadas mais origens compatíveis com o DirectQuery no futuro, com especial atenção àquelas que se espera que consigam proporcionar um bom desempenho de consultas interativas.

O **SQL Server Analysis Services** é um caso especial. Ao ligar ao SQL Server Analysis Services, pode optar por importar os dados ou utilizar uma *ligação em direto*.  As *ligações em direto* são semelhantes ao DirectQuery, no sentido em que não são importados dados e que a origem de dados subjacente é sempre consultada para atualizar um elemento visual, mas são diferentes em muitos outros aspetos, pelo que é utilizado um termo diferente (*em direto* versus *DirectQuery*).

Estas três opções para ligar aos dados – **importação**, **DirectQuery** e **ligação em direto** – são explicados em detalhe nas secções seguintes.

### <a name="import-connections"></a>Importar ligações
Quando utiliza **Obter Dados** no **Power BI Desktop** para se ligar a uma origem de dados, como o SQL Server, e escolhe **Importar**, essa ligação tem o comportamento seguinte:

* Durante a experiência de **Obter Dados** inicial, cada uma das tabelas do conjunto de tabelas selecionado define uma consulta que devolve um conjunto de dados (estas consultas podem ser editadas antes de os dados serem carregados, para, por exemplo, aplicar filtros, agregar os dados ou unir tabelas diferentes).
* Após o carregamento, todos os dados definidos por essas consultas serão importados para a cache do Power BI.
* A seguir à criação de um elemento visual no **Power BI Desktop**, os dados importados serão consultados. O arquivo do Power BI garante que as consultas serão muito rápidas, pelo que todas as alterações ao elemento visual se refletiram de imediato.
* Quaisquer alterações aos dados subjacentes não serão refletidas em nenhum elemento visual. É necessário *Atualizar*, o que faz com que os dados sejam importados novamente.
* Após a publicação do relatório (o ficheiro .pbix) para o **serviço Power BI**, é criado e carregado um conjunto de dados para o serviço Power BI.  Os dados importados estão incluídos nesse conjunto de dados. Em seguida, é possível configurar a atualização agendada desses dados, para, por exemplo, voltar a importá-los todos os dias. Consoante a localização da origem de dados original, poderá ser necessário configurar um Gateway de dados no local.
* Quando abrir um relatório já existente no **serviço Power BI** ou criar um novo, os dados importados são consultados outra vez, garantindo a interatividade.
* Os elementos visuais, bem como as páginas de relatórios inteiras, podem ser afixados como mosaicos do dashboard. Os mosaicos serão atualizados automaticamente sempre que o conjunto de dados subjacente o for.  

### <a name="directquery-connections"></a>Ligações DirectQuery
Quando utiliza **Obter Dados** no **Power BI Desktop** para se ligar a uma origem de dados e escolhe **DirectQuery**, essa ligação tem o comportamento seguinte:

* Durante a experiência de **Obter Dados** inicial, a origem é selecionada. Para origens relacionais, isto significa que é selecionado um conjunto de tabelas, sendo que cada tabela define uma consulta que devolve um conjunto de dados logicamente. Para origens multidimensionais, como SAP BW, só é selecionada a origem.
* No entanto, após o carregamento, não são efetivamente importados dados para o arquivo do Power BI. Em vez disso, após a criação de um elemento visual no **Power BI Desktop**, as consultas serão enviadas para a origem de dados subjacente, para obter os dados necessários. O tempo decorrido para atualizar o elemento visual dependerá do desempenho da origem de dados subjacente.
* Quaisquer alterações aos dados subjacentes não serão refletidas imediatamente em nenhum elemento visual. Continua a ser necessário Atualizar, o que faz com que as consultas necessárias sejam reenviadas para cada elemento visual, os quais são atualizados conforme necessário.
* Após a publicação do relatório para o **serviço Power BI**, gerará novamente um Conjunto de Dados no serviço Power BI, tal como sucede com a importação. Contudo, esse conjunto de dados *não* incluirá dados.
* Quando abrir um relatório já existente no **serviço Power BI** ou criar um novo, a origem de dados subjacente é consultada novamente para obter os dados necessários. Consoante a localização da origem de dados original, poderá ser necessário configurar um Gateway de dados no local, tal como é preciso para o modo Importação se os dados forem atualizados.
* Os elementos visuais, bem como as páginas de relatórios inteiras, podem ser afixados como mosaicos do dashboard. Para garantir que a abertura dos dashboards será rápida, os mosaicos são atualizados automaticamente com base numa agenda (por exemplo, a cada hora). A frequência desta atualização pode ser controlada para refletir a frequência com que os dados são alterados e a importância de ver os dados mais recentes. Assim, ao abrir um dashboard, os mosaicos irão refletir os dados a partir do momento da última atualização e não necessariamente as últimas alterações feitas à origem subjacente. Os dashboards abertos podem sempre ser Atualizados para garantir que mostram os dados mais recentes.    

### <a name="live-connections"></a>Ligações em direto
Ao ligar ao **SQL Server Analysis Services** (SSAS), há uma opção para importar os dados ou ligar-se em direto ao modelo de dados selecionado. Se selecionar **importar**, vai definir uma consulta nessa origem SSAS externa e os dados são importados normalmente. Se escolher **ligar em direto**, não é definida qualquer consulta e todo o modelo externo é apresentado na lista de campos. Se optar pelo **DirectQuery**, à medida que são criados elementos visuais, as consultas são enviadas para a origem SSAS externa. No entanto, ao contrário do DirectQuery, não faz sentido criar um *modelo* novo; por outras palavras, não é possível definir colunas calculadas novas, hierarquias, relações, etc. Em vez disso, vai simplesmente ligar de forma direta ao modelo SSAS externo.

A situação descrita no parágrafo anterior aplica-se igualmente à ligação às seguintes origens, exceto que não há nenhuma opção para importar os dados:

* Conjuntos de dados do Power BI (por exemplo, ao ligar a um conjunto de dados do Power BI que foi criado anteriormente e publicado no serviço, para criar um relatório novo com base no mesmo)
* Common Data Services

O comportamento dos relatórios no SSAS, após a publicação no **serviço Power BI**, tem as seguintes semelhanças com os relatórios do DirectQuery:

* Quando abrir um relatório já existe no **serviço Power BI** ou criar um novo, a origem SSAS subjacente é consultada (o que, possivelmente, requer um Gateway de dados no local)
* Os mosaicos do dashboard são atualizados automaticamente com base numa agenda (como a cada hora ou outra frequência qualquer que seja definida)

No entanto, também existem diferenças importantes, incluindo o facto de que, nas ligações em direto, a identidade do utilizador que está a abrir o relatório será sempre transmitida à origem SSAS subjacente.

Uma vez abordadas estas comparações, o resto do artigo vai dedicar-se apenas ao **DirectQuery**.

## <a name="when-is-directquery-useful"></a>Em que casos é útil utilizar o DirectQuery?
A tabela abaixo descreve os cenários em que ligar com o DirectQuery pode ser especialmente útil, incluindo casos em que se consideraria benéfico deixar os dados na origem original. A descrição inclui um tópico sobre se o cenário especificado está disponível no Power BI.

| Limitação | Descrição |
| --- | --- |
| Os dados mudam frequentemente e são necessários relatórios quase em “tempo real” |Os modelos com dados importados podem ser atualizados uma vez por hora, no máximo. Desta forma, se os dados forem alterados constantemente e os relatórios tiverem de mostrar os dados mais recentes, a utilização de Importar com a atualização agendada poderá simplesmente não satisfazer aquelas necessidades. Tenha em atenção que também é possível transmitir dados em fluxo diretamente para o Power BI, embora haja limites para os volumes de dados suportados neste caso. <br/> <br/> Por outro lado, a utilização do DirectQuery significa que abrir ou atualizar um relatório ou dashboard mostrará sempre os dados mais recentes da origem. Além disso, os mosaicos do dashboard podem ser atualizados com mais frequência (como de 15 em 15 minutos). |
| Os dados são muito grandes |Se os dados forem muito grandes, não será certamente exequível importá-los todos. Por outro lado, o DirectQuery não exige transferências de dados volumas, uma vez que é consultado no local. <br/> <br/> Contudo, os dados grandes também podem significar que o desempenho das consultas executadas nessa origem subjacente é demasiado lento (conforme descrito na secção *Implicações da utilização do DirectQuery*, mais adiante neste artigo). E, obviamente nem sempre é necessário importar os dados detalhados completos. Em vez disso, os dados podem ser pré-agregados durante a importação (e o **Query Editor** permite-lhe fazer isto facilmente). Em último caso, seria possível importar exatamente os dados agregados necessários para cada elemento visual. Assim, embora o DirectQuery seja a abordagem mais simples para dados volumosos, deve ter sempre em conta que a importação dos dados agregados pode ser uma solução nos casos em que a origem subjacente esteja demasiado lenta. |
| As regras de segurança são definidas na origem subjacente |Quando os dados são importados, o Power BI irá ligar à origem de dados com as credenciais atuais do utilizador (a partir do Power BI Desktop) ou com as credenciais definidas como parte da configuração da atualização agendada (a partir do serviço Power BI). Assim, na publicação e partilha de um relatório deste tipo, deve ter cuidado para partilhar apenas com utilizadores que tenham permissão para ver os mesmos dados ou para definir a Segurança ao Nível da Linha como parte do conjunto de dados. <br/> <br/> Idealmente, uma vez que o DirectQuery consulta sempre a origem subjacente, isto permitira que fosse aplicada qualquer segurança nessa origem. No entanto, atualmente, o Power BI vai ligar-se sempre à origem subjacente com as mesmas credenciais que seriam utilizadas para Importar. <br/> <br/> Deste modo, enquanto o Power BI não permitir que a identidade do consumidor do relatório seja transmitida para a origem subjacente, o DirectQuery não oferece nenhuma vantagem relativamente à segurança das origens de dados. |
| Aplicam-se restrições de soberania de dados |Algumas organizações têm políticas relativamente à soberania de dados, o que significa que os dados não podem deixar as instalações. Uma solução baseada na importação apresentaria claramente limitações. Em contrapartida, com o DirectQuery, os dados permanecem na origem subjacente. <br/> <br/> No entanto, é de salientar que, mesmo com o DirectQuery, são retidas no serviço Power BI algumas caches de dados ao nível do elemento visual (devido à atualização agendada dos mosaicos). |
| A origem de dados subjacente é uma origem OLAP que contém medidas |Se a origem de dados subjacente contiver *medidas* (como SAP HANA ou SAP Business Warehouse), a importação dos dados acarreta outros problemas. Significa que os dados importados estão num determinado nível de agregação, conforme definido pela consulta. Por exemplo, vamos medir VendasTotais por Classe, Ano e Cidade. Assim, se for criado um elemento visual que peça dados num nível agregado superior (como VendasTotais por Ano), haverá uma agregação adicional do valor agregado. Esta situação funciona para medidas de adição (como Soma ou Mín), mas não para as outras (como Média ou ContagemDistinta). <br/> <br/> Para facilitar a obtenção dos dados agregados corretos (conforme necessários para o elemento visual específico) diretamente a partir da origem, será preciso enviar consultas por elemento visual, tal como no DirectQuery. <br/> <br/> Ao ligar ao SAP Business Warehouse (BW), escolher o DirectQuery permite este tratamento das medidas. O suporte para o SAP BW é abordado mais detalhadamente em [DirectQuery and SAP BW](desktop-directquery-sap-bw.md) (DirectQuery e SAP BW). <br/> <br/> No entanto, atualmente, o DirectQuery no SAP HANA trata estas ligações como origens relacionais, pelo que proporciona um comportamento semelhante para a importação. Este tópico é abordado mais detalhadamente em [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA). |

Assim, em resumo, dadas as capacidades atuais do DirectQuery no Power BI, os cenários em que oferece benefícios são os seguintes:

* Os dados mudam frequentemente e são necessários relatórios quase em “tempo real”
* Processamento de dados muito grandes, sem a necessidade de pré-agregar
* Aplicam-se restrições de soberania de dados
* A origem é uma origem multidimensional que contém medidas (como o SAP BW)

Tenha em atenção que os detalhes da lista anterior estão relacionados com a utilização do Power BI individualmente. Existe sempre a opção de, em alternativa, utilizar um modelo externo do SQL Server Analysis Server (ou dos Serviços de Análise do Azure) para importar os dados e, depois, utilizar o Power BI para ligar a esse modelo. Embora esta abordagem exija mais conhecimentos, proporciona maior flexibilidade. Por exemplo, podem ser importados volumes muito maiores de dados e não existem restrições quanto à frequência com que estes podem ser atualizados.

## <a name="implications-of-using-directquery"></a>Implicações da utilização do DirectQuery
A utilização do **DirectQuery** tem implicações potencialmente negativas, conforme detalhado nesta secção. Algumas destas limitações são ligeiramente diferentes consoante a origem exata que esteja a ser utilizada. Estas limitações serão mencionadas sempre que aplicável e as origens que sejam substancialmente diferentes são abordadas em tópicos separados.  

### <a name="performance-and-load-on-the-underlying-source"></a>Desempenho e carga na origem subjacente
Quando utiliza o **DirectQuery**, a experiência global depende muito do desempenho da origem de dados subjacente. Se a atualização de cada elemento visual (por exemplo, após mudar o valor de uma segmentação de dados) demorar alguns segundos (menos de cinco segundos), a experiência será razoável, embora possa, ainda assim, parecer lenta em comparação com a resposta imediata a que estamos habituados quando importados os dados para o Power BI. Se, pelo contrário, a lentidão da origem significar que os elementos visuais individuais demoram mais tempo do que isso (dezenas de segundos), a experiência torna-se muito má, possivelmente ao ponto de as consultas excederem o tempo limite.

Juntamente com o desempenho da origem subjacente, é preciso ter em conta a carga que vai ser colocada na mesma (que, obviamente, afeta muitas vezes o desempenho). Tal como referido mais abaixo, cada utilizador que abra um relatório partilhado e cada mosaico de dashboard que seja atualizado periodicamente enviará, pelo menos, uma consulta por elemento visual à origem subjacente. Este facto exige que a origem consiga lidar com esta carga de consultas, mantendo, ao mesmo tempo, um desempenho razoável.

### <a name="limited-to-a-single-source"></a>Limitado a uma única origem
Ao importar dados, é possível combinar dados de várias origens num único modelo para, por exemplo, associar facilmente alguns dados de uma base de dados empresarial do SQL Server a alguns dados locais presentes num ficheiro do Excel. Isto não é possível se for utilizado o DirectQuery. Se selecionar o DirectQuery para uma origem, só será possível utilizar dados dessa origem individual (como uma base de dados do SQL Server individual).

### <a name="limited-data-transformations"></a>Transformações de dados limitadas
Da mesma forma, existem limitações nas transformações de dados que podem ser aplicadas no **Editor de Consultas**. Com os dados importados, pode ser facilmente aplicado um conjunto sofisticado de transformações para limpar e reformatar os dados antes de utilizá-los para criar elementos visuais (como analisar documentos JSON ou deslocar dados de formulários orientados em coluna para formulários orientado por linhas). Estas transformações mais são limitadas no DirectQuery. Em primeiro lugar, ao ligar a uma origem OLAP, como o SAP Business Warehouse, não é possível definir nenhuma transformação e todo o “modelo” externo é obtido a partir da origem. Nas origens relacionais, como o SQL Server, continua a ser possível definir um conjunto de transformações por consulta, mas estas são limitadas por motivos de desempenho. Qualquer uma destas transformações terá de ser aplicada a todas as consultas feitas na origem subjacente e não apenas uma vez na atualização dos dados, pelo que estão limitadas às transformações que podem ser razoavelmente traduzida numa única consulta nativa. Se utilizar uma transformação demasiado complexa, receberá um erro que diz que tem de ser eliminada ou que o modelo tem de ser alterado para o modo Importar.

Além disso, a consulta que resulta da caixa de diálogo **Obter Dados** ou do **Editor de Consultas** será utilizada numa sub-seleção dentro das consultas geradas e enviadas para obter os dados necessários para os elementos visuais. Por este motivo, a consulta definida no Editor de Consultas tem de ser válida dentro deste contexto. Mais concretamente, isto significa que não é possível utilizar consultas com Expressões de Tabela Comuns nem consultas que invoquem Procedimentos Armazenados.

### <a name="modeling-limitations"></a>Limitações de modelação
Neste contexto, o termo *modelação* refere-se à ação de refinar e enriquecer os dados não processados, como parte da criação de relatórios que os utilizam. Os exemplos incluem:

* Definir relações entre tabelas
* Adicionar cálculos novo (colunas calculadas e medidas)
* Mudar o nome e ocultar colunas e medidas
* Definir hierarquias
* Definir a formatação, o resumo predefinido e a ordenação de colunas
* Agrupar ou criar clusters de valores

Quando utiliza o **DirectQuery**, continua a ser possível fazer muitas destas melhorias aos modelos e aplica-se, certamente, o princípio de que os dados não processados estão a ser enriquecidos, de modo a melhorar o posterior consumo. No entanto, algumas capacidades de modelação não estão disponíveis ou são limitadas ao utilizar o DirectQuery. Geralmente, as limitações são aplicadas para evitar problemas de desempenho. O conjunto de limitações que são comuns a todas as origens do DirectQuery está listado na lista com marcas abaixo. Podem aplicar-se limitações adicionais a origens individuais, conforme descrito em *Detalhes de origens de dados específicas*, perto do fim deste artigo.

* **Sem hierarquia de data incorporada:** ao importar dados, por predefinição, todas as colunas de data/data e hora terão também uma hierarquia de data incorporada disponível. Por exemplo, se importar uma tabela de ordens de vendas que inclua uma coluna OrderDate, então, se utilizar OrderDate num elemento visual, será possível escolher o nível adequado (Ano, Mês, Dia) a utilizar. Esta hierarquia de dados incorporada não está disponível se o modo DirectQuery estiver a ser utilizado. Contudo, tenha em atenção que se a tabela Data estiver disponível na origem subjacente (o que é comum em muitos armazéns de dados), as funções DAX de Análise de Tempo podem ser utilizadas normalmente.
* **Limitações nas colunas calculadas:** as colunas calculadas estão limitadas a ser intra-linhas, no sentido em que só podem referenciar valores de outras colunas da mesma tabela sem utilizar qualquer função de agregação. Além disso, as funções escalares DAX (como LEFT()) permitidas estarão limitadas às que podem simplesmente ser enviadas para a origem subjacente, pelo que variarão consoante as capacidades exatas da origem. As funções que não são suportadas não serão listadas na conclusão automática durante a criação do DAX para uma coluna calculada e, se forem utilizadas, resultarão em erro.
* **Sem suporte para funções DAX principal-subordinado:** no modelo DirectQuery, não é possível utilizar a família de funções DAX PATH(), as quais, geralmente, processam as estruturas Principal-Subordinado (como um gráfico de clientes ou hierarquias de funcionários).
* **Limitações (por predefinição) para medidas:** por predefinição, as funções e expressões DAX que podem ser utilizadas nas medidas são restritas. Mais uma vez, a conclusão automática irá restringir as funções listadas e, se for utilizada uma função ou expressão inválida, ocorrerá um erro. O motivo é simplesmente garantir que, por predefinição, as medidas estão restritas a medidas simples que, por si só, tenham poucas probabilidades de provocar problemas de desempenho. Os utilizadores avançados podem optar por ignorar esta limitação ao selecionar **Ficheiro > Opções e definições > Opções** e, em seguida, **DirectQuery** e ao selecionar a opção *Permitir medidas não restritas no modo DirectQuery*. Quando essa opção for selecionada, qualquer expressão DAX válida para uma medida poderá ser utilizada. No entanto, os utilizadores devem estar cientes de que algumas expressões que funcionam muito bem quando os dados são importados podem resultar em consultas muito lentas à origem de back-end no modo DirectQuery.
  
  * Por exemplo, por predefinição:
    
    * Seria possível criar uma medida que somasse simplesmente o montante das vendas:
      
          SalesAmount = SUMX(Web_Sales, [ws_sales_price]* [ws_quantity])
    * *Não* seria possível criar uma medida que, depois, calculasse a média do valor SalesAmount de todos os Artigos:
      
          AverageItemSalesAmount = AVERAGEX('Item', [SalesAmount])
    
    O motivo é que esta medida pode resultar num fraco desempenho caso haja um grande número de artigos.
* **As tabelas calculadas não são suportadas:** a capacidade de definir uma tabela calculada com uma expressão DAX não é suportada no modo DirectQuery.
* **A filtragem de relação está limitada a um único sentido:** ao utilizar o DirectQuery, não é possível definir o sentido do Filtro Cruzado numa relação como “Ambos”. Por exemplo, com as três tabelas abaixo, não seria possível criar um elemento visual que mostrasse cada Customer[Gender] e o número de Product[Category] que cada um comprou. A utilização desta filtragem bidirecional está descrita [neste documento técnico detalhado](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) (o documento apresenta exemplos no contexto do SQL Server Analysis Services, mas os pontos fundamentais aplicam-se igualmente ao Power BI).
  
  ![](media/desktop-directquery-about/directquery-about_01.png)
  
  Mais uma vez, a limitação é imposta devido às implicações no desempenho. Uma aplicação particularmente importante desta situação é quando definir a Segurança ao Nível da Linha como parte do relatório, pois um padrão comum consiste em ter uma relação de muitos para muitos entre os utilizadores e as entidades às quais aqueles podem aceder e é necessário utilizar a filtragem bidirecional para impor essa relação. No entanto, a utilização da filtragem bidirecional em modelos do DirectQuery deve ser utilizada com cuidado, dando especial atenção a eventuais impactos negativos no desempenho.  
* **Sem clustering:** ao utilizar o DirectQuery, não é possível utilizar a capacidade de Clustering para encontrar grupos automaticamente.

### <a name="reporting-limitations"></a>Limitações de relatórios
Quase todas as capacidades dos relatórios são suportadas nos modelos do DirectQuery. Como tal, desde que a origem subjacente ofereça um nível adequado de desempenho, pode ser utilizado o mesmo conjunto de visualizações. No entanto, existem algumas limitações importantes em algumas das outras funcionalidades que o **serviço Power BI** oferece após a publicação de um relatório, conforme descrito na lista com marcas abaixo:

* **Quick Insights não é suportado:** o Power BI Quick Insights procura diferentes subconjuntos do seu conjunto de dados enquanto aplica um grupo de algoritmos sofisticados para detetar informações potencialmente interessantes. Tendo em conta a necessidade de consultas de desempenho muito alto, esta capacidade não está disponível em conjuntos de dados que utilize o DirectQuery.
* **Q&A não é suportado:** o Power BI Q&A permite-lhe explorar os seus dados com capacidades de linguagem natural e intuitiva e receber respostas na forma de gráficos e quadros. No entanto, não é atualmente suportado em conjuntos de dados que utilizem o DirectQuery.
* **Utilizar o Explorador no Excel resultará, provavelmente, num desempenho pior:** é possível explorar os seus dados com a capacidade “Explorar no Excel” nos conjuntos de dados. Desta forma, será possível criar Tabelas Dinâmicas e Gráficos Dinâmicos. Embora esta capacidade seja suportada em conjuntos de dados que utilizem o DirectQuery, o desempenho é, geralmente, mais lento do que criar elementos visuais no Power BI, pelo que, se a utilização do Excel for importante para os seus cenários, deve ter em conta este facto quando decidir se vai utilizar o DirectQuery.

### <a name="security"></a>Segurança
Tal como já foi abordado anteriormente neste artigo, os relatórios que utilizem o **DirectQuery** utilizarão sempre as mesmas credenciais para se ligarem à origem de dados subjacente, após a publicação no **serviço Power BI**. Mais uma vez, realça-se que este aspeto se refere especificamente ao DirectQuery e não a ligações em direto ao SQL Server Analysis Services, que é diferente quanto a este aspeto. Por conseguinte, imediatamente após a publicação de um relatório do DirectQuery, é necessário configurar as credenciais do utilizador que serão utilizadas. Enquanto não o fizer, abrir o relatório no serviço Power BI resultará em erro.

As credenciais serão utilizadas assim que forem disponibilizadas, *independentemente do utilizador que abra o relatório*. Neste aspeto, é exatamente igual aos dados importados, em que cada utilizador irá ver os mesmos dados, a menos que a Segurança ao Nível da Linha tenha sido definida como parte do relatório. Por este motivo, também é preciso ter atenção à partilha do relatório, caso haja regras de segurança definidas na origem subjacente.

### <a name="behavior-in-the-power-bi-service"></a>Comportamento no serviço Power BI
Esta secção descreve o comportamento de um relatório do **DirectQuery** no **serviço Power BI**, essencialmente para podermos compreender o grau de carregamento que vai ser colocado na origem de dados de back-end, dado o número de utilizadores com que o relatório e o dashboard vão ser partilhados, a complexidade do relatório e se a Segurança ao Nível da Linha foi definida no mesmo.

#### <a name="reports--opening-interacting-with-editing"></a>Relatórios – abrir, interagir e editar
Quando é aberto um relatório, todos os elementos visuais na página atualmente visível são atualizados. Geralmente, cada elemento visual precisará de, pelo menos, uma consulta à origem de dados subjacente. Alguns elementos visuais poderão exigir mais de uma consulta (por exemplo, se mostrarem valores agregados de duas tabelas de factos diferentes ou contiverem uma medida mais complexa ou totais de medidas não aditivas, como Count Distinct). Mover para uma página nova resultará na atualização desses elementos visuais, o que produz um conjunto de consultas novas à origem subjacente.

Cada interação do utilizador no relatório poderá resultar na atualização dos elementos visuais. Por exemplo, selecionar um valor diferente numa segmentação de dados exigirá o envio de um conjunto de consultas novas para atualizar todos os elementos visuais afetados. O mesmo se aplica ao clicar num elemento visual para fazer uma seleção cruzada de outros elementos ou ao alterar um filtro.  

Do mesmo modo, obviamente, editar um relatório novo exigirá o envio de consultas para cada passo do caminho, de modo a produzir o elemento visual pretendido.

Há um certo tipo de colocação dos resultados em cache, para que a atualização de um elemento visual seja imediata caso já tenham sido obtidos recentemente os mesmos resultados. Se estiver definida alguma Segurança ao Nível da Linha como parte do relatório, estas caches não são partilhadas entre os utilizadores.

#### <a name="dashboard-refresh"></a>Atualização do Dashboard
Os elementos visuais, bem como as páginas inteiras, podem ser afixados ao dashboard como mosaicos. Os mosaicos com base nos conjuntos de dados do **DirectQuery** são, depois, atualizados de forma automática, de acordo com uma agenda, o que faz com que as consultas sejam enviadas para a origem de dados de back-end. Por predefinição, a atualização ocorre de hora a hora, mas o intervalo pode ser configurado nas definições do Conjunto de Dados para ser semanal ou de 15 em 15 minutos.

Se não estiver definida nenhuma Segurança ao Nível da Linha no modelo, o mesmo significa que cada mosaico será atualizado uma vez e os resultados partilhados com todos os utilizadores. Se estiver definida, pode ocorrer um efeito multiplicador grande – cada mosaico requer o envio de consultas separadas por utilizador para a origem subjacente.  

Assim, um dashboard com dez mosaicos, partilhado com cem utilizadores, criado num conjunto de dados que utiliza o **DirectQuery** com a Segurança ao Nível da Linha e configurado para ser atualizado de 15 em 15 minutos resultará no envio de, pelo menos, mil consultas, a cada 15 minutos, para a origem de dados de back-end.

Consequentemente, é preciso ter cuidado ao utilizar a Segurança ao Nível da Linha e ao configurar a agenda de atualização.

#### <a name="timeouts"></a>Tempos limite
É aplicado um tempo limite de quatro minutos às consultas individuais no **serviço Power BI** e as que demorem mais tempo irão, simplesmente, falhar. Como já foi referido anteriormente, recomenda-se a utilização do DirectQuery para origens que proporcionem um desempenho de consultas quase interativo, pelo que este limite tem como objetivo evitar problemas provocados por tempos de execução demasiado longos.

### <a name="other-implications"></a>Outras implicações
Pode ver abaixo algumas das outras implicações gerais relativas à utilização do **DirectQuery**:

* **Se os dados forem alterados, é necessário Atualizar para garantir que são mostrados os mais recentes:** devido à utilização de caches, não é garantido que o elemento visual mostre sempre os últimos dados. Por exemplo, um elemento visual poderá mostrar as transações no último dia. Então, devido à alteração de uma segmentação de dados, pode ser atualizado para mostrar as transações dos dois últimos dias, incluindo algumas muito recentes acabadas de chegar. Devolver a segmentação de dados ao valor original faz com que volte a mostrar novamente o valor em cache obtido anteriormente, o qual não inclui a transação acabada de chegar que vimos antes.
  
  Selecionar Atualizar limpa todas as caches e atualiza todos os elementos visuais na página, de modo a que mostrem os dados mais recentes.
* **Se os dados forem alterados, a consistência entre os elementos visuais não é garantida:** diferentes elementos visuais, quer estejam na mesma página ou em diferentes, podem ser atualizados em momentos distintos. Assim, se os dados na origem subjacente estiverem a ser alterados, não é garantido que cada elemento visual mostre os dados exatamente no mesmo ponto no tempo. De facto, dado que, por vezes, é necessária mais de uma consulta para um elemento visual individual (por exemplo, para obter os detalhes e os totais), nem a consistência dentro de elementos individuais é garantida. Para garantir essa consistência, seria preciso a sobrecarga de atualizar todos os elementos visuais sempre for atualizado um elemento visual, juntamente com a utilização de funcionalidades caras, como o Isolamento de Instantâneos, na origem de dados subjacente.
  
  Este problema pode ser grandemente mitigado ao selecionar de novo Atualizar, o que atualiza todos os elementos visuais na página. E é de salientar que, mesmo que seja utilizado o modo Importar, existe um problema semelhante para garantir a consistência, se forem importados dados de mais de uma tabela.
* **É necessário Atualizar no Power BI Desktop para refletir eventuais alterações aos metadados:** após a publicação de um relatório, Atualizar irá simplesmente atualizar os elementos visuais no relatório. Se o esquema da origem subjacente tiver sido alterado, essas alterações não são aplicadas automaticamente para alterar os campos disponíveis na lista de campos. Deste modo, se as tabelas ou colunas tiverem sido removidas da origem subjacente, poderá resultar numa falha da consulta após a atualização. Abrir o relatório no Power BI Desktop e escolher Atualizar atualiza os campos no modelo, de forma a refletir as alterações.
* **Limite de um milhão de linhas devolvidas em qualquer consulta:** é aplicado um limite fixo de um milhão de linhas ao número de linhas que podem ser devolvidas em qualquer consulta individual à origem subjacente. Geralmente, este limite não tem implicações práticas nem os elementos visuais vão apresentar assim tantos pontos. No entanto, o limite pode ocorrer em casos em que o Power BI não esteja a otimizar totalmente as consultas enviadas e em que estejam a ser pedidos resultados intermédios que excedem o limite. Também pode ocorrer durante a criação de um elemento visual, no caminho para um estado final mais razoável. Por exemplo, a inclusão de Cliente e TotalSalesQuantity atingiria este limite se houvesse mais de um milhão de clientes, até que fosse aplicado um filtro.
  
  O erro devolvido seria “O conjunto de resultados de uma consulta à origem de dados externa excedeu o tamanho máximo permitido de «1 000 000» linhas”.
* **Não é possível alterar do modo Importar para DirectQuery:** tenha em conta que, embora regra geral seja possível mudar um modelo do modo DirectQuery para Importar, isso significa que é preciso importar todos os dados necessários. Também não é possível reverter a mudança (sobretudo devido ao conjunto de funcionalidades que o modo DirectQuery não suporta). Os modelos do DirectQuery em origens multidimensionais, como o SAP BW, também não podem ser revertidos de DirectQuery para Importar, devido ao tratamento completamente diferente das medidas externas.

## <a name="directquery-in-the-power-bi-service"></a>O DirectQuery no serviço Power BI
São suportadas todas as origens a partir do **Power BI Desktop**. Algumas origens também estão disponíveis diretamente a partir do **serviço Power BI**. Por exemplo, um utilizador empresarial pode utilizar o Power BI para se ligar aos respetivos dados no Salesforce e obter imediatamente um dashboard sem utilizar o **Power BI Desktop**.

Apenas duas das origens compatíveis com o DirectQuery estão disponíveis diretamente no serviço:

* Spark
* Azure SQL Data Warehouse

No entanto, é vivamente recomendado que qualquer utilização do **DirectQuery** numa destas duas origens tenha início no **Power BI Desktop**. Isto deve-se ao facto de que, quando a ligação é feita inicialmente no **serviço Power BI**, se aplicam muitas limitações importantes, o que significa que, ao passo que o ponto de partida tenha sido fácil (iniciar no serviço Power BI), existem limitações quanto à realização de mais otimizações do relatório resultante (por exemplo, deixa de ser possível criar cálculos, utilizar muitas funcionalidades analíticas ou inclusivamente atualizar os metadados para refletir eventuais alterações ao esquema subjacente).   

## <a name="guidance-for-using-directquery-successfully"></a>Orientações para a utilização do DirectQuery com êxito
Se pretender utilizar o **DirectQuery**, esta secção disponibiliza-lhe algumas orientações de alto nível para garantir a máxima eficácia. As orientações nesta secção derivam das implicações da utilização do DirectQuery que foram descritas neste artigo.

### <a name="backend-data-source-performance"></a>Desempenho da origem de dados de back-end
Recomenda-se vivamente confirmar que os elementos visuais simples podem ser atualizados num período de tempo aceitável. Esse período de tempo deve ser de cinco segundos, de modo a proporcionar uma experiência interativa razoável. Se os elementos visuais demorarem mais de 30 segundos, é certo que haverá grandes probabilidades de ocorrerem mais problemas a seguir à publicação do relatório, o que fará com que a solução deixe de ser exequível.

Se as consultas estiverem lentas, a primeira coisa a investigar são as consultas que estão a ser enviadas para a origem subjacente e o motivo que leva ao desempenho observado. Este tópico não abrange a vasta gama de melhores práticas de otimização de bases de dados no conjunto completo das potenciais origens subjacentes, mas aplica-se às práticas padrão de bases de dados comuns a quase todas as situações:

* Geralmente, as relações com base em colunas de números inteiros têm um desempenho melhor do que as associações em colunas de outros tipos de dados.
* Devem ser criados os índices apropriados, o que, normalmente, significa a utilização de índices de arquivo de colunas nas origens que os suportam (por exemplo, o SQL Server).
* Eventuais estatísticas necessárias na origem devem ser atualizadas

### <a name="model-design-guidance"></a>Orientação para o Design de Modelos
Ao definir o modelo, considere fazer o seguinte:

* **Evite consultas complexas no Editor de Consultas.** A consulta definida no Editor de Consultas será traduzida numa consulta individual do SQL, que será depois incluída na sub-seleção de todas as consultas enviadas para essa tabela. Se essa consulta for complexa, poderá resultar em problemas de desempenho em todas as consultas enviadas. A consulta SQL real para um conjunto de passos pode ser obtida ao selecionar o último passo no Editor de Consultas e escolher *Ver Consulta Nativa*, no menu de contexto.
* **Mantenha as medidas simples.** Pelo menos inicialmente, recomenda-se limitar as medidas a agregados simples. Em seguida, se tiverem um desempenho satisfatório, podem ser definidas medidas mais complexas, mas tendo atenção ao desempenho de cada uma.
* **Evite relações em colunas calculadas.** Isto é especialmente relevante para as bases de dados em que é necessário fazer associações de várias colunas. Atualmente, o Power BI não permite que as relações se baseiem em várias colunas como a chave externa/chave primária. Uma solução comum é utilizar uma coluna calculada para concatenar as colunas e basear a associação na mesma. Embora esta solução seja razoável para os dados importados, no caso do **DirectQuery** resulta numa associação numa expressão, o que normalmente impede a utilização de índices e leva a um fraco desempenho. A única solução é realmente materializar as várias colunas numa única coluna na base de dados subjacente.
* **Evite relações em colunas uniqueidentifier.** O Power BI não suporta, de forma nativa, os tipos de dados de uniqueidentifier. Por este motivo, definir uma relação entre colunas deste tipo resultará numa consulta com uma associação que envolve uma conversão. Mais uma vez, isto leva geralmente a um fraco desempenho. Enquanto este caso não esteja especificamente otimizado, a única solução é materializar as colunas de um tipo alternativo na base de dado subjacente.
* **Oculte a coluna *para* nas relações.** A coluna *para* nas relações (normalmente, a chave primária na tabela *para*) deve ser ocultada, para que não apareça na lista de campos e, por conseguinte, não possa ser utilizada nos elementos visuais. Muitas vezes, as colunas nas quais as relações de baseiam são de facto *colunas de sistema* (por exemplo, chaves de substituição num armazém de dados) e ocultá-las é, de qualquer modo, uma boa prática. Se a coluna tiver significado, introduza uma coluna calculada que esteja visível e que tenha uma expressão simples que seja igual à chave primária. Por exemplo:
  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  
  O motivo para o fazer é para simplesmente evitar problemas de desempenho que podem ocorrer se um elemento visual incluir a coluna de chave primária.
* **Examine todas as utilizações das colunas calculadas e alterações de tipos de dados.** A utilização destas capacidades não é necessariamente prejudicial, pois fazem com que as consultas sejam enviadas para a origem subjacente que contém expressões em vez de simples referências às colunas, o que, mais uma vez, pode resultar na não utilização de índices.  
* **Evite utilizar a filtragem cruzada bidirecional (pré-visualização) nas relações.**
* **Experimente a definição *Assumir integridade referencial*.** A definição *Assumir Integridade Referencial* nas relações permite que as consultas utilizem instruções ASSOCIAÇÃO EXTERNA em vez de ASSOCIAÇÃO EXTERNA. Geralmente, esta definição melhora o desempenho das consultas, embora dependa das especificidades da origem de dados.
* **Não utilize a filtragem por data relativa no Editor de Consultas.** É possível definir a filtragem de data relativa no Editor de Consultas. Por exemplo, para filtrar pelas linhas nas quais a data está nos últimos 14 dias.
  
  ![](media/desktop-directquery-about/directquery-about_02.png)
  
  No entanto, esta filtragem é convertida num filtro baseado na data fixa, à hora a que a consulta foi criada. Esta data pode ser vista na consulta nativa.
  
  ![](media/desktop-directquery-about/directquery-about_03.png)
  
  Quase de certeza que não era este o resultado que se pretendia. Para garantir que o filtro é aplicado com base na data na hora em que o relatório é executado, aplique o filtro no relatório como um Filtro de Relatório. Atualmente, isto seria feito mediante a criação de uma coluna calculada que calculasse o número de dias no passado (com a função DAX DATE()) e, depois, utilizando-a num filtro.

### <a name="report-design-guidance"></a>Orientação para o Design de Relatórios
Quando criar um relatório com uma ligação do DirectQuery, siga as orientações abaixo:

* **Considere a utilização das opções de Redução de Consulta:** o Power BI dispõe de opções no relatório para enviar menos consultas e para desativar certas interações que resultarão numa experiência fraca se as consultas resultantes demorarem muito tempo a serem executadas. Para aceder a estas opções no **Power BI Desktop**, aceda a **Ficheiro > Opções e definições > Opções** e selecione **Redução de consulta**. 

   ![](media/desktop-directquery-about/directquery-about_03b.png)

    As seleções da caixa de verificação na **Redução de consulta** permitem-lhe desativar o realce cruzado em todo o relatório. Também pode apresentar um botão *Aplicar* para as seleções de filtros e/ou segmentações de dados, o que lhe permite, em seguida, realizar muitas seleções de filtros e segmentações de dados antes de as aplicar, o que não permite enviar qualquer consulta enquanto não selecionar o botão **Aplicar** na segmentação de dados. As suas seleções podem ser utilizadas para filtrar os dados.

    Estas opções serão aplicadas ao relatório enquanto interage com ele no **Power BI Desktop**, bem como quando os utilizadores consomem o relatório no **serviço Power BI**.

* **Aplique filtros primeiros:** aplique sempre todos os filtros aplicáveis no início da criação de um elemento visual. Por exemplo, em vez de arrastar TotalSalesAmount e ProductName e filtrar por um determinado ano, aplique o filtro em Ano, logo no início. Isto deve-se ao facto de que cada passo da criação de elementos visuais envia uma consulta e, embora seja possível fazer outras alterações antes da conclusão da primeira consulta, continua a haver uma carga desnecessária na origem subjacente. Normalmente, a aplicação de filtros logo no início faz com que estas consultas intermédias sejam menos dispendiosas. Além disso, a não aplicação dos filtros atempada pode fazer com que seja atingido o limite de um milhão de linhas mencionado anteriormente.
* **Limite o número de elementos visuais nas páginas:** quando é aberta uma página (ou é alterada uma segmentação de dados ou um filtro ao nível da página), todos os elementos visuais na mesma são atualizados. Também existe um limite ao número de consultas que são enviadas em paralelo, pelo que, à medida que o número de elementos visuais aumenta, alguns destes são atualizados em série, o que aumenta o tempo que demora a atualizar a página inteira. Por este motivo, recomenda-se limitar a quantidade de elementos visuais em cada página e, em alternativa, criar mais páginas simples.
* **Considere desativar a interação entre elementos visuais:** por predefinição, as visualizações nas páginas dos relatórios podem ser utilizadas para fazer filtragem e seleção cruzada das outras visualizações na página. Por exemplo, se selecionar “1999” no gráfico circular, o gráfico de colunas é selecionado de forma cruzada para mostrar as vendas por categoria para “1999”.                                                                  
  
  ![](media/desktop-directquery-about/directquery-about_04.png)
  
  No DirectQuery, a filtragem e o realce cruzados requerem a submissão de consultas para a origem subjacente, pelo que a interação deve ser desativada se o tempo necessário para responder às seleções dos utilizadores for excessivamente longo. No entanto, esta interação pode ser desativada para o relatório completo (conforme descrito acima para as *Opções de redução de consultas*) ou numa base caso a caso, conforme descrito [neste artigo](service-reports-visual-interactions.md).

Além da lista acima das sugestões, tenha em atenção que cada uma das seguintes capacidades de relatórios pode causar problemas de desempenho:

* **Filtros de medidas:** os elementos visuais que contêm medidas (ou agregados de colunas) podem conter filtros nas mesmas. Por exemplo, o elemento visual abaixo mostra SalesAmount por categoria, mas inclui apenas as Categorias com mais de 20 milhão em vendas.
  
  ![](media/desktop-directquery-about/directquery-about_05.png)
  
  Esta ação resulta no envio de duas consultas para a origem subjacente:
  
  * A primeira consulta irá obter as Categorias que cumprem a condição (Vendas > 20 milhões)
  * A segunda consulta irá obter os dados necessários para o elemento visual, incluindo as Categorias que cumprem a condição na cláusula WHERE.  
  
  Geralmente, estes filtros funcionam bem se houver centenas ou milhares de categorias, como no nosso exemplo. O desempenho pode deteriorar-se se o número de categorias for muito superior (e, de facto, a consulta falhará se existirem mais de um milhão de categorias que cumpram a condição, devido ao limite de um milhão de linhas abordado anteriormente).
* **Filtros TopN:** podem ser definidos filtros avançados para filtrar apenas os N valores mais altos (ou mais baixos) classificados por uma medida qualquer, como, por exemplo, para incluir as 10 Principais Categorias do elemento visual acima. Esta ação resulta, novamente, no envio de duas consultas para a origem subjacente. No entanto, a primeira consulta devolverá todas as categorias da origem subjacente e os valores de TopN são determinados com base nos resultados devolvidos. Consoante a cardinalidade da coluna envolvida, esta funcionalidade pode originar problemas de desempenho (ou falhas nas consultas, devido ao limite de um milhão de linhas).
* **Median:** geralmente, qualquer agregação (Sum, Count Distinct, etc.) é enviada para a origem subjacente. No entanto, isto não se aplica a Median, pois, regra geral, a origem subjacente não suporta esta agregação. Nestes casos, os dados de detalhe são obtidos a partir da origem subjacente e Median é calculada a partir dos resultados devolvidos. Esta abordagem é sensata se a mediana for calculada sobre um número relativamente pequeno de resultados, mas ocorrerão problemas de desempenho (ou falhas de consultas, devido ao limite de um milhão de linhas), caso a cardinalidade seja grande.  Por exemplo, um valor mediano da população de um país poderá ser razoável, mas um valor mediano de preço de vendas não.
* **Filtros de texto avançados (“contém” e semelhantes):** ao filtrar numa coluna de texto, a filtragem avançada permite filtros como “contém”, “começa com”, etc. Estes filtros podem, certamente, resultar num desempenho pior em algumas origens de dados. Em particular, o filtro predefinido “contém” não deve ser utilizado se o que é realmente necessário é uma correspondência exata (“é” ou “não é”). Embora os resultados possam ser os mesmos, dependendo dos dados reais, o desempenho pode ser significativamente diferente devido à utilização de índices.
* **Segmentações de dados com seleções múltiplas:** por predefinição, as segmentações de dados só permitem fazer uma única seleção. Permitir a seleção múltipla em filtros pode causar alguns problemas de desempenho, porque, à medida que o utilizador seleciona um conjunto de itens da segmentação de dados (por exemplo, os dez produtos em que está interessado), cada seleção nova resultará no envio de consultas para a origem de back-end. Embora o utilizador possa selecionar o item seguinte antes de a consulta ser concluída, tal resulta numa carga adicional na origem subjacente.

* **Considere desativar os totais nos elementos visuais:** por predefinição, as tabelas e as matrizes apresentam totais e subtotais. Em muitos casos, tem de enviar consultas separadas para a origem subjacente para obter os valores para esses totais. Tal aplica-se sempre que utilizar a agregação *DistinctCount* ou em todos os casos quando utilizar o DirectQuery através de SAP BW ou SAP HANA. Esses totais deverão ser desativados (através do painel **Formato**) se não forem precisos. 

### <a name="diagnosing-performance-issues"></a>Diagnosticar problemas de desempenho
Esta secção descreve como diagnosticar problemas de desempenho ou como obter informações mais detalhadas para permitir a otimização dos relatórios.

Recomenda-se vivamente que qualquer diagnóstico de problemas de desempenho seja iniciado no **Power BI Desktop** em vez de no **serviço Power BI**. Em muitos casos, os problemas de desempenho têm por base simplesmente o nível de desempenho da origem subjacente e são mais facilmente identificados e diagnosticados no ambiente muito mais isolado do **Power BI Desktop**, que elimina inicialmente alguns componentes (como o gateway do Power BI). Só se não forem encontrados problemas de desempenho no Power BI Desktop é que a investigação se deve concentrar nas especificidades dos relatórios no serviço Power BI.

Da mesma forma, recomenda-se tentar primeiro isolar problemas num elemento visual individual em vez de em muitos elementos numa página.

Assim, vamos supor que aqueles passos (nos parágrafos anteriores desta secção) foram seguidos. Temos agora um único elemento visual numa página no **Power BI Desktop** que ainda está lenta. Para determinar as consultas que o Power BI Desktop envia para a origem subjacente, é possível ver informações de rastreio/diagnóstico que essa origem pode emitir. Estes rastreios também podem conter informações úteis relativamente aos detalhes de execução das consultas e como pode ser melhorada.

Além disso, mesmo que estes rastreios da origem não estejam disponíveis, é possível ver as consultas que o Power BI envia, juntamente com os tempos de execução, conforme descrito a seguir.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Determinar as consultas que o Power BI Desktop envia
Por predefinição, o **Power BI Desktop** regista os eventos durante uma determinada sessão num ficheiro de rastreio com o nome FlightRecorderCurrent.trc.

Em algumas origens do **DirectQuery**, este registo inclui todas as consultas enviadas para a origem de dados subjacente (as restantes origens do DirectQuery serão incluídas no futuro). As origens que enviam consultas para o registo são os seguintes:

* SQL Server
* Base de Dados SQL do Azure
* Azure SQL Data warehouse
* Oracle
* Teradata
* SAP HANA

O ficheiro de rastreio está disponível na pasta **AppData** do utilizador atual:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces

Uma forma fácil de chegar a esta página é, no **Power BI Desktop**, selecionar **Ficheiro > Opções e definições > Opções** e, em seguida, **Diagnósticos**. É apresentada a janela da caixa de diálogo abaixo:

![](media/desktop-directquery-about/directquery-about_06.png)

Quando selecionar a ligação *Abrir pasta de rastreios*, em **Opções de Diagnóstico**, é aberta a pasta seguinte:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\Traces

Navegar para a pasta principal dessa pasta mostra a pasta que contém *AnalysisServicesWorkspaces*, a qual vai conter uma subpasta de área de trabalho para cada instância aberta do **Power BI Desktop**. Estas subpastas incluem no nome um sufixo de número inteiro, como *AnalysisServicesWorkspace2058279583*.

Dentro dessa pasta está uma subpasta *\\Data*, que contém o ficheiro de rastreio FlightRecorderCurrent.trc da sessão atual do Power BI. A pasta de área de trabalho correspondente é eliminada quando a sessão do Power BI Desktop associada é terminada.

Os ficheiros de rastreio podem ser lidos com a ferramenta **SQL Server Profiler**, que está disponível como transferência gratuita como parte do **SQL Server Management Studio**. Pode obtê-lo [nesta localização](https://msdn.microsoft.com/library/mt238290.aspx).

Depois de transferir e instalar o **SQL Server Management Studio**, execute o **SQL Server Profiler**.

![](media/desktop-directquery-about/directquery-about_07.png)

Para abrir o ficheiro de rastreio, siga os passos abaixo:

1. No **SQL Server Profiler**, selecione**File (Ficheiro) > Open (Abrir) > Trace file (Ficheiro de rastreio)**
2. Introduza o caminho para o ficheiro de rastreio da sessão do Power BI atualmente iniciada, tal como:
   
         C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data
3. Abra FilghtRecorderCurrent.trc

São apresentados todos os eventos da sessão atual. É mostrado um exemplo anotado abaixo, que destaca grupos de eventos. Cada grupo tem:

* Um evento de *Início de Consulta* e de *Fim de Consulta*, os quais representam o início e o fim de uma consulta DAX gerada pela IU (por exemplo, a partir de um elemento visual ou do preenchimento de uma lista de valores na IU do filtro)
* Um ou mais pares de eventos *Início do DirectQuery* e de *Fim do DirectQuery*, que representam uma consulta enviada para a origem de dados subjacente como parte da avaliação da consulta DAX.

Tenha em conta que podem ser executadas várias consultas DAX em paralelo, pelo que é possível intercalar eventos de grupos diferentes. O valor de ActivityID pode ser utilizado para determinar que eventos pertencem ao mesmo grupo.

![](media/desktop-directquery-about/directquery-about_08.png)

Outras colunas de interesse incluem:

* **TextData:** o detalhe textual do evento. Em eventos “Início/Fim de Consulta”, será a consulta DAX. Em eventos “Início/Fim do DirectQuery”, será a consulta SQL enviada à origem subjacente. TextData para o evento selecionado atualmente também é apresentado na área na parte inferior.
* **EndTime:** quando o evento foi concluído.
* **Duration:** a duração, em milissegundos, que demorou a executar a consulta DAX ou SQL.
* **Error:** indica se ocorreu um erro (caso em que o evento também é apresentado a vermelho).

Repare que, na imagem acima, algumas das colunas menos interessantes foram reduzidas, de modo a permitir ver mais facilmente as colunas de interesse.

A abordagem recomendada para capturar um rastreio que ajude a diagnosticar potenciais problemas de desempenho é a seguinte:

* Abra uma sessão única do **Power BI Desktop** (para evitar confusões de ter várias pastas de áreas de trabalho).
* Execute o conjunto de ações de interesse no **Power BI Desktop**. Inclua algumas ações adicionais para além dessas, para garantir que são enviados para o ficheiro de rastreio todos os eventos de interesse.
* Abra o **SQL Server Profiler** e examine o rastreio, conforme descrito anteriormente. Lembre-se de que o ficheiro de rastreio vai ser eliminado depois de fechar o **Power BI Desktop**. Além disso, não aparecerão imediatamente mais ações feitas no Power BI Desktop – o ficheiro de rastreio deve ser fechado e reaberto para ver os eventos novos.
* Mantenha as sessões individuais razoavelmente pequenas (dez segundos de ações em vez de centenas de segundos), para que seja mais fácil interpretar o ficheiro de rastreio (e, uma vez que há um limite quanto ao tamanho deste ficheiro, é possível que em sessões muito longas os primeiros eventos sejam eliminados).

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Compreender a forma de consultas que o Power BI Desktop envia
O formato geral das consultas que o **Power BI Desktop** cria e envia utilizam subseleções para cada uma das tabelas referenciadas, em que as subseleções são definidas pela consulta defina no **Editor de Consultas**. Por exemplo, imaginemos as seguintes tabelas TPC-DS no SQL Server:

![](media/desktop-directquery-about/directquery-about_09.png)

Considere a consulta seguinte:

![](media/desktop-directquery-about/directquery-about_10.png)

Esta consulta resulta no elemento visual seguinte:

![](media/desktop-directquery-about/directquery-about_11.png)

Atualizar este elemento visual resultará na consulta SQL mostrada abaixo do parágrafo seguinte. Como podemos ver, há três subseleções para Web Sales, Item e Date_dim, sendo que cada uma devolve todas as colunas na respetiva tabela, apesar de o elemento visual só referenciar, efetivamente, quatro colunas. Estas consultas nas subseleções (estão sombreadas) são exatamente o resultado das consultas definidas no **Editor de Consultas**. Não se registaram impactos no desempenho resultantes desta utilização das subseleções nas origens de dados que o DirectQuery suporta até à data. As origens de dados, como o SQL Server, simplesmente otimizam as referências às outras colunas.

Um motivo que leva o Power BI a empregar este padrão é o facto de a consulta SQL utilizada poder ser fornecida diretamente pelo analista, pelo que é utilizada “tal como é fornecida”, sem que se tente reescrevê-la.

![](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Passos seguintes
Este artigo descreve os aspetos do **DirectQuery** que são comuns a todas as origens de dados. Existem determinados detalhes que são específicos de origens individuais. Veja os tópicos seguintes que cobrem origens específicas:

* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery and SAP HANA](desktop-directquery-sap-bw.md) (DirectQuery e SAP HANA)

Para obter mais informações sobre o **DirectQuery**, veja os recursos seguintes:

* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origens de Dados que o DirectQuery suporta)

