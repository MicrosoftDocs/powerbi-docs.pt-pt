---
title: Utilizar modelos compostos no Power BI Desktop
description: Criar modelos de dados com várias ligações de dados e relações muitos para muitos no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 01/19/2021
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 0601760392b9bac549ff683f4460a3681da16119
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570020"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>Utilizar modelos compostos no Power BI Desktop

Anteriormente, no Power BI Desktop, quando utilizava um DirectQuery num relatório, não era permitida nenhuma outra ligação de dados, DirectQuery ou Importação, nesse relatório. Com os modelos compostos, essa restrição deixa de existir. Um relatório pode incluir de forma perfeita ligações de dados de mais do que uma ligação de dados DirectQuery ou de importação, em qualquer combinação que escolher.

A capacidade de modelos compostos no Power BI Desktop consiste em três funcionalidades relacionadas:

* **Modelos compostos**: Permite que um relatório tenha duas ou mais ligações de dados de grupos de origens diferentes, como uma ou mais ligações do DirectQuery e uma ligação de importação, duas ou mais ligações do DirectQuery ou qualquer combinação das mesmas. Este artigo descreve os modelos compostos de forma detalhada.

* **Relações muitos para muitos**: Com os modelos compostos, pode estabelecer *relações muitos para muitos* entre tabelas. Esta abordagem remove os requisitos de valores exclusivos nas tabelas. Também remove soluções anteriores como, por exemplo, apresentar novas tabelas apenas para estabelecer relações. Para obter mais informações, veja [Aplicar relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md).

* **Modo de armazenamento**: Agora, pode especificar que elementos visuais fazem consultas às origens de dados de back-end. Os elementos visuais que não precisam de uma consulta são importados, mesmo que sejam baseados no DirectQuery. Esta funcionalidade ajuda a melhorar o desempenho e a reduzir a carga de back-end. Anteriormente, até os elementos visuais simples, como as segmentações, iniciavam consultas para origens de back-end. Para obter mais informações, veja [Gerir o modo de armazenamento no Power BI Desktop](desktop-storage-mode.md).

## <a name="use-composite-models"></a>Utilizar modelos compostos

Com os modelos compostos, pode ligar-se a tipos diferentes de origens de dados quando utiliza o Power BI Desktop ou o serviço Power BI. Pode criar essas ligações de dados de várias formas:

* Ao importar dados para o Power BI, que é a forma mais comum de obter dados.
* Ao ligar-se diretamente aos dados no seu repositório de origem original através do DirectQuery. Para obter mais informações sobre o DirectQuery, veja [Utilizar o DirectQuery no Power BI](../connect-data/desktop-directquery-about.md).

Quando utiliza o DirectQuery, os modelos compostos permitem criar um modelo do Power BI (por exemplo, um único ficheiro *.pbix* do Power BI Desktop) que faz as seguintes ações:

* Combina dados a partir de uma ou mais origens do DirectQuery.
* Combina dados de origens do DirectQuery e dados da importação.

Por exemplo, ao utilizar os modelos compostos, pode criar um modelo que combina os seguintes tipos de dados:

* Dados de vendas de um armazém de dados empresarial.
* Dados dos objetivos de vendas de uma base de dados do SQL Server departamental.
* Dados importados de uma folha de cálculo.

Um modelo que combina dados de mais de uma origem do DirectQuery ou combina o DirectQuery com dados da importação é designado por modelo composto.

Pode criar relações entre tabelas como sempre fez, mesmo quando essas tabelas têm origens diferentes. Todas as relações de origem cruzada são criadas com uma cardinalidade de muitos para muitos, independentemente da cardinalidade real. Pode alterá-las para um-para-muitos, muitos-para-um ou um-para-um. Qualquer que seja a cardinalidade que definiu, as relações de origem cruzada têm um comportamento diferente. Não pode utilizar funções DAX (Data Analysis Expressions) para recuperar valores no lado `one` a partir do lado `many`. Também poderá ver um impacto no desempenho em comparação com as relações muitos-para-muitos na mesma origem.

> [!NOTE]
> Dentro do contexto dos modelos compostos, todas as tabelas importadas são, efetivamente, uma única origem, independentemente da origem de dados real subjacente.

## <a name="example-of-a-composite-model"></a>Exemplo de modelo composto

Para obter um exemplo de um modelo composto, considere um relatório que tenha ligado a um armazém de dados da empresa no SQL Server com o DirectQuery. Neste caso, o armazém de dados contém os dados **Vendas por País**, **Trimestre** e **Bicicleta (Produto)** , conforme mostrado na imagem seguinte:

![Vista das relações dos modelos compostos](media/desktop-composite-models/composite-models_04.png)

Neste momento, pode criar elementos visuais simples com os campos desta origem. A imagem seguinte mostra a quantidade total de vendas por *Nome do Produto*, num trimestre selecionado.

![Elemento visual com base nos dados](media/desktop-composite-models/composite-models_05.png)

Mas, e se tiver dados numa folha de cálculo do Office Excel sobre o gestor de produtos que está atribuído a cada produto, juntamente com a prioridade de marketing? Se desejar ver o **Valor de Vendas** por **Gestor de Produtos**, poderá não ser possível adicionar estes dados locais ao armazém de dados da empresa. Ou poderá demorar meses, na melhor das hipóteses.

É possível importar esses dados de vendas do armazém de dados, em vez de utilizar o DirectQuery. E os dados de vendas, em seguida, podem ser combinados com os dados que importou da folha de cálculo. No entanto, essa abordagem não é razoável, pelos motivos que levaram a utilizar o DirectQuery em primeiro lugar. Os motivos podem incluir:

* Alguma combinação das regras de segurança impostas na origem subjacente.
* A necessidade de poder ver os dados mais recentes.
* A enorme escala dos dados.

É aqui que entram os modelos compostos. Os modelos compostos permitem que se ligue ao armazém de dados através do DirectQuery e, em seguida, que utilize **Obter dados** para origens adicionais. Neste exemplo, vamos primeiro estabelecer a ligação DirectQuery ao armazém de dados da empresa. Utilizamos **Obter dados**, escolhemos **Excel** e, em seguida, navegamos para a folha de cálculo que contém os nossos dados locais. Por fim, importamos a folha de cálculo que contém os *Nomes de Produtos*, o **Gestor de Vendas** atribuído e a **Prioridade**.  

![Janela Navegador](media/desktop-composite-models/composite-models_06.png)

Na lista **Campos**, pode ver duas tabelas: a tabela **Bicicletas** original do SQL Server e uma nova tabela **Gestores de Produtos**. A nova tabela contém os dados que são importados do Excel.

![vista Campos das tabelas](media/desktop-composite-models/composite-models_07.png)

Da mesma forma, na vista **Relações** no Power BI Desktop, agora vemos uma tabela adicional chamada **Gestores de Produtos**.

![Vista das relações das tabelas](media/desktop-composite-models/composite-models_08.png)

Agora, precisamos de relacionar essas tabelas com as outras tabelas no modelo. Como sempre, criamos uma relação entre a tabela **Bicicletas** do SQL Server e a tabela **Gestores de Produtos** importada. Ou seja, a relação é entre **Bicicletas[ProductName]** e **Gestores de Produtos[ProductName]** . Conforme foi abordado anteriormente, todas as relações que passam pela origem têm a cardinalidade predefinida muitos para muitos.

![Janela “Criar relação”](media/desktop-composite-models/composite-models_09.png)

Depois de estabelecer esta relação, ela é apresentada na vista **Relações** no Power BI Desktop, conforme esperado.

![Nova vista Relações](media/desktop-composite-models/composite-models_10.png)

Agora, podemos criar elementos visuais com qualquer um dos campos na lista **Campos**. Esta abordagem combina de forma totalmente integrada os dados de várias origens. Por exemplo, o *Valor de Vendas* total de cada *Gestor de Produtos* é apresentado na imagem seguinte:

![O painel Campos](media/desktop-composite-models/composite-models_11.png)

O seguinte exemplo apresenta um caso comum de uma tabela de *dimensões* como **Produto** ou **Cliente**, que é expandida com alguns dados adicionais importados de outro lugar. As tabelas também podem utilizar o DirectQuery para se ligar a várias origens. Para continuarmos com o nosso exemplo, imagine que os **Objetivos de Vendas** por **País** e **Período** são armazenados numa base de dados departamental separada. Como habitualmente, pode utilizar **Obter dados** para se ligar aos dados, conforme ilustrado na imagem seguinte:

![Janela Navegador](media/desktop-composite-models/composite-models_12.png)

À semelhança do fizemos anteriormente, podemos criar relações entre a nova tabela e as outras tabelas no modelo e, em seguida, criar elementos visuais que combinem os dados das tabelas. Vamos observar novamente a vista **Relações**, em que estabelecemos as novas relações:

![Vista Relações com muitas tabelas](media/desktop-composite-models/composite-models_13.png)

A imagem seguinte baseia-se nos novos dados e nas relações que criámos. O elemento visual na parte inferior esquerda mostra o *Valor de Vendas* total versus *Objetivo* e o cálculo da variação mostra a diferença. Os dados de **Valor de Vendas** e de **Objetivo** são provenientes de duas bases de dados diferentes do SQL Server.

![Imagem que mostra mais dados](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>Definir o modo de armazenamento

Cada tabela num modelo composto tem um modo de armazenamento que indica se a tabela se baseia no DirectQuery ou na importação. O modo de armazenamento pode ser visto e modificado no painel **Propriedade**. Para apresentar o modo de armazenamento, clique com o botão direito do rato numa tabela na lista **Campos** e, em seguida, selecione **Propriedades**. A imagem seguinte mostra o modo de armazenamento da tabela **Objetivos de Vendas**.

O modo de armazenamento também pode ser visto na descrição de cada tabela.

![Descrição que mostra o modo de armazenamento](media/desktop-composite-models/composite-models_16.png)

Para qualquer ficheiro do Power BI Desktop (um ficheiro *.pbix*) que contém algumas tabelas do DirectQuery e algumas tabelas de importação, a barra de estado apresenta um modo de armazenamento chamado **Misto**. Pode clicar nesse termo na barra de estado e mudar facilmente todas as tabelas para importação.

Para obter mais informações sobre o modo de armazenamento, veja [Gerir o modo de armazenamento no Power BI Desktop](desktop-storage-mode.md).  

> [!NOTE]
> Pode utilizar o modo de armazenamento *Misto* no Power BI Desktop e no serviço Power BI.

## <a name="calculated-tables"></a>Tabelas calculadas

Pode adicionar tabelas calculadas a um modelo que utilize o DirectQuery. O Data Analysis Expressions (DAX) que define a tabela calculada pode fazer referência a tabelas do DirectQuery, a tabelas importadas ou a uma combinação das duas.

As tabelas calculadas são sempre importadas e os dados delas são atualizados quando atualiza as tabelas. Se uma tabela calculada fizer referência a uma tabela do DirectQuery, os elementos visuais que fazem referência à tabela do DirectQuery mostrarão sempre os valores mais recentes na origem subjacente. Em alternativa, os elementos visuais que fazem referência à tabela calculada mostram os valores contidos no momento em que a tabela calculada foi atualizada pela última vez.

## <a name="security-implications"></a>Implicações de segurança

Os modelos compostos têm algumas implicações de segurança. Uma consulta enviada para uma origem de dados pode incluir valores de dados que foram obtidos de outra origem. No exemplo anterior, o elemento visual que mostra **(Valor de Vendas)** por **Gestor de Produtos** envia uma consulta SQL à base de dados relacional de Vendas. Essa consulta SQL pode conter os nomes dos Gestores de Produtos e os Produtos associados.

![Script que mostra as implicações de segurança](media/desktop-composite-models/composite-models_17.png)

Consequentemente, as informações armazenadas na folha de cálculo estão agora incluídas numa consulta enviada à base de dados relacional. Se estas informações forem confidenciais, deverá ter em consideração as implicações de segurança. Em particular, considere os seguintes pontos:

* Qualquer administrador da base de dados que pode ver os rastreios ou os registos de auditoria pode ver estas informações, mesmo sem permissões para aceder aos dados na sua fonte original. Neste exemplo, o administrador precisaria permissões para aceder ao ficheiro Excel.

* As definições de encriptação de cada origem devem ser tidas em consideração. Vai querer evitar a obtenção de informações de uma origem através de uma ligação encriptada e, em seguida, inadvertidamente, incluí-la numa consulta que é enviada a outra origem através de uma ligação não encriptada.

Para permitir a confirmação de que todas as implicações de segurança foram consideradas, o Power BI Desktop mostra uma mensagem de aviso quando está a criar um modelo composto.  

Além disso, se um autor adicionar *Table1* a partir do *Modelo A* a um Modelo Composto (*Modelo C* para efeitos de referência), um utilizador que esteja a ver um relatório baseado no *Modelo C* pode consultar **qualquer tabela** no *Modelo A* que não seja protegido pelo RLS.

Por motivos semelhantes, tem de ser cuidadoso ao abrir um ficheiro do Power BI Desktop enviado de uma origem não fidedigna. Se o ficheiro contiver modelos compostos, as informações que alguém obtém de uma origem com as credenciais do utilizador que abre o ficheiro serão enviadas a outra origem de dados como parte da consulta. As informações podem ser visualizadas pelo autor mal intencionado do ficheiro do Power BI Desktop. Quando abre inicialmente um ficheiro do Power BI Desktop que contém várias origens de dados, o Power BI Desktop apresenta um aviso. O aviso é parecido com o aviso apresentado quando abre um ficheiro que contém consultas SQL nativas.  

## <a name="performance-implications"></a>Implicações de desempenho  

Quando utilizar o DirectQuery, deve sempre considerar o desempenho, principalmente para garantir que a origem de back-end tem recursos suficientes para proporcionar uma boa experiência aos utilizadores. Uma boa experiência implica que a os elementos visuais sejam atualizados em cinco segundos ou menos. Para obter mais conselhos sobre o desempenho, veja [Acerca de utilizar o DirectQuery no Power BI](../connect-data/desktop-directquery-about.md).

A utilização de modelos compostos implica mais considerações de desempenho. Um único elemento visual pode resultar no envio de consultas para múltiplas origens de dados, que muitas vezes transmitem os resultados de uma consulta para uma segunda origem. Esta situação pode resultar nas seguintes formas de execução:

* **Uma consulta SQL que inclui um grande número de valores literais**: por exemplo, um elemento visual que pede o **Valor de Vendas** total de um conjunto de **Gestores de Produtos** selecionados, primeiro, tem de descobrir quais são os **Produtos** geridos por esses gestores de produtos. Esta sequência tem de ocorrer antes de o elemento visual enviar uma consulta SQL que inclui todos os IDs dos produtos numa cláusula `WHERE`.

* **Uma consulta SQL que consulta a um nível granularidade inferior, com os dados a serem posteriormente agregados localmente**: Com o número de **Produtos** que cumprem os critérios do filtro em **Gestores de Produtos** a aumentar bastante, pode não ser eficiente ou exequível incluir todos os produtos numa cláusula `WHERE`. Em vez disso, pode consultar a origem relacional no nível mais baixo de **Produtos** e, em seguida, agregar localmente os resultados. Se a cardinalidade de **Produtos** exceder o limite de um milhão, a consulta falhará.

* **Várias consultas SQL, uma por grupo e por valor**: Quando a agregação utiliza **ContagemDistinta** e é agrupada por uma coluna de outra origem, e se a origem externa não suportar a passagem eficiente de muitos valores literais que definem o agrupamento, será necessário enviar uma consulta SQL por grupo e por valor.

   Um elemento visual que pede uma contagem distinta do **NúmeroContaCliente** na tabela do SQL Server por **Gestor de Produtos** importada de uma folha de cálculo teria de passar os detalhes da tabela **Gestor de Produtos** na consulta enviada ao SQL Server. Noutras origens, por exemplo, Redshift, esta ação não é exequível. Em vez disso, haveria uma consulta SQL enviada por **Gestor de Vendas**, até um limite prático, altura em que a consulta falharia.

Cada um destes casos tem as suas próprias implicações no desempenho e os detalhes exatos variam para cada origem de dados. Embora a cardinalidade das colunas utilizadas na relação de associação de duas origens continue a ser baixa, alguns milhares, o desempenho não deve ser afetado. À medida que aumenta esta cardinalidade, deve prestar mais atenção ao impacto no desempenho resultante.

Além disso, a utilização de relações muitos para muitos significa que as consultas separadas têm de ser enviadas para a origem subjacente de cada nível de total ou subtotal, em vez de agregar os valores detalhados localmente. Um elemento visual de tabela simples com totais enviaria duas consultas SQL, em vez de uma.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações nesta versão dos modelos compostos:

Atualmente, a [atualização incremental](../admin/service-premium-incremental-refresh.md) só é suportada em modelos compostos que ligam a origens de dados do SQL, Oracle e Teradata.

As seguintes origens multidimensionais do Live Connect não podem ser utilizadas com modelos compostos:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI
* Azure Analysis Services

Quando se liga a estas origens multidimensionais através do DirectQuery, não se pode ligar a outra origem do DirectQuery nem combinar a mesma com os dados da importação.

As limitações existentes do DirectQuery ainda se aplicam quando utiliza os modelos compostos. Muitas destas limitações são agora por tabela, de acordo com o modo de armazenamento da tabela. Por exemplo, uma coluna calculada numa tabela de importação pode referir-se a outras tabelas, mas uma coluna calculada numa tabela do DirectQuery ainda pode referir-se apenas às colunas na mesma tabela. As outras limitações aplicar-se-ão ao modelo como um todo se qualquer uma das tabelas no modelo for DirectQuery. Por exemplo, a funcionalidade QuickInsights não está disponível num modelo se alguma das tabelas dentro dela tiver um modo de armazenamento de DirectQuery.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre os modelos compostos e o DirectQuery, veja os artigos seguintes:

* [Relações muitos para muitos no Power BI Desktop](desktop-many-to-many-relationships.md)
* [Modo de armazenamento no Power BI Desktop](desktop-storage-mode.md)
* [Utilizar o DirectQuery no Power BI](../connect-data/desktop-directquery-about.md)
* [Origens de dados suportadas pelo DirectQuery no Power BI](../connect-data/power-bi-data-sources.md)
* [Utilizar o DirectQuery para conjuntos de dados do Power BI e para o Azure Analysis Services (pré-visualização)](../connect-data/desktop-directquery-datasets-azure-analysis-services.md)
