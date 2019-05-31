---
title: Origens de dados do Power BI
description: Origens de dados do Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/02/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 26c7c1b428f513fe2b79a3377085004506412604
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61235402"
---
# <a name="data-sources-for-the-power-bi-service"></a>Origens de dados para o serviço Power BI
Os dados são o coração do Power BI. Sempre que está a explorar dados, a criar gráficos e dashboards, a fazer perguntas com Perguntas e Respostas, todas as visualizações e respostas que vê estão, na verdade, a extrair os dados subjacentes de um conjunto de dados. Mas de onde vem esse conjunto de dados? Bem, de uma origem de dados.

Neste artigo, vamos falar sobre os diferentes tipos de origens de dados aos quais se pode ligar através do serviço Power BI. Tenha em consideração que há muitos outros tipos de origens de dados a aprtir dos quais pode obter dados. No entanto, essas origens podem exigir primeiro a utilização do Power BI Desktop ou da consulta avançada de dados e recursos de modelação do Excel. Veremos mais detalhes posteriormente. Por enquanto, vamos examinar os diferentes tipos de origens de dados aos quais se pode ligar diretamente a partir do site do serviço Power BI.

Pode obter dados de qualquer uma destas origens de dados no Power BI ao clicar em **A Minha Área de Trabalho** > **Obter Dados**.

![](media/service-get-data/pbi_getdata_startscreen.png)

## <a name="files"></a>Ficheiros
![](media/service-get-data/pbi_getdata_files.png)

**Excel** (.xlsx, .xlsm) – o Excel é único no sentido em que um livro pode ter dados introduzidos por si em folhas de cálculo ou pode consultar e carregar dados de origens de dados externas através do Power Query (Obter e Transformar no Excel 2016) ou do Power Pivot. Pode importar dados em tabelas nas folhas de cálculo (os dados *têm* de estar numa tabela) ou importar dados carregados para um modelo de dados. Para saber mais, veja [Obter dados do Excel](service-get-data-from-files.md).

**Power BI Desktop** (.pbix) – Pode utilizar o Power BI Desktop para consultar e carregar dados a partir de origens de dados externas, expandir o modelo de dados com medidas e relações, e criar relatórios. Pode importar o fichiero do Power BI Desktop para o site do Power BI. O Power BI Desktop é melhor para utilizadores mais avançados que tenham uma boa compreensão dos conceitos de origens de dados, consulta e transformação de dados e modelação de dados. Para saber mais, veja [Ligar-se a dados no Power BI Desktop](desktop-connect-to-data.md).

**Valores Separados por Vírgula** (.csv) – são ficheiros de texto simples com linhas de dados. Cada linha pode conter um ou mais valores, cada um separado por uma vírgula. Por exemplo, um .csv que contém dados de nome e endereço pode ter um número de linhas em que cada linha tem valores para nome, sobrenome, endereço, cidade, estado e assim sucessivamente. Não é possível importar dados para um ficheiro .csv, mas muitas aplicações, como o Excel, podem guardar dados de tabela simples como um ficheiro .csv.

Para outros tipos de ficheiro, como tabela XML (.xml) ou ficheiros de texto (.txt), pode usar Obter e Transformar para consultar, transformar e carregar dados num ficheiro do Excel ou do Power BI Desktop. Pode importar o ficheiro do Excel ou do Power BI Desktop para o Power BI.

O local onde armazena os ficheiros também faz uma diferença significativa. O OneDrive para Empresas fornece maior nível de flexibilidade e integração com o Power BI. Se mantiver os ficheiros na unidade local não haverá qualquer problema, mas se precisar de atualizar os dados, serão necessários alguns passos adicionais. Serão fornecidos mais detalhes nos artigos ligados.

## <a name="content-packs"></a>Pacotes de conteúdo
![](media/service-get-data/pbi_getdata_contentpacks.png)

Os pacotes de conteúdo contêm todos os dados e relatórios de que precisa já preparados. No Power BI, há dois tipos de pacotes de conteúdo; os de serviços, como o Google Analytics, Marketo ou Salesforce, e os criados e partilhados por outros utilizadores na organização.

**Serviços** – existem dezenas de serviços com pacotes de conteúdo para o Power BI e estamos sempre a adicionar mais. A maioria dos serviços exigem que tenha uma conta. Para saber mais, veja [Ligar-se a serviços](service-connect-to-services.md).

**Organizacional** – se você e outros utilizadores na sua organização tiverem numa conta do Power BI Pro, podem criar, partilhar e utilizar pacotes de conteúdo. Para saber mais, veja [Pacotes de conteúdo organizacional](service-organizational-content-pack-introduction.md).

## <a name="databases"></a>Bases de Dados
![](media/service-get-data/pbi_getdata_databases.png)

**Bases de dados na cloud** – a partir do serviço Power BI, pode ligar-se à Base de Dados SQL do Azure, SQL Data Warehouse do Azure, Spark no Azure HD Insight e SQL Server Analysis Services através do DirectQuery. As ligações do Power BI a estas bases de dados ocorrem em tempo real, ou seja, ao ligar-se, por exemplo, a uma Base de Dados SQL do Azure e começar a explorar os dados ao criar relatórios no Power BI, quando secciona os dados ou adiciona outro campo a uma visualização, é feita uma consulta diretamente na base de dados. Para saber mais, veja [Azure e Power BI](service-azure-and-power-bi.md).

**Bases de dados locais** – a partir do serviço Power BI, pode ligar-se diretamente às bases de dados de modelo de tabela do SQL Server Analysis Services. É necessário um gateway do Power BI Enterprise. Se não tiver a certeza sobre como ligar-se à base de dados modelo em tabela da organização, consulte o seu administrador ou departamento de TI. Para saber mais, veja [Dados de Tabela do SQL Server Analysis Services no Power BI](sql-server-analysis-services-tabular-data.md).

Para outros tipos de bases de dados na organização, primeiro terá de utilizar o Power BI Desktop ou o Excel para ligar-se, consultar e carregar dados para um modelo de dados. Pode importar o ficheiro para o Power BI, onde um conjunto de dados é criado. Se configurar a atualização agendada, o Power BI utilizará as informações de ligação do ficheiro juntamente com as configurações de atualização definidas para se ligar diretamente à origem de dados e consultar atualizações. Essas atualizações serão, então, carregadas no conjunto de dados no Power BI. Para saber mais, veja [Ligar-se a dados no Power BI Desktop](desktop-connect-to-data.md).

## <a name="what-if-my-data-comes-from-a-different-source"></a>E se os dados vierem de uma origem diferente?
Há, literalmente, centenas de origens de dados diferentes que pode usar com o Power BI. Mas, independentemente de onde obtém os dados, os dados devem estar num formato que o serviço Power BI possa usar para criar relatórios e dashboards, responder a perguntas com Perguntas e Respostas e assim sucessivamente.

Algumas origens de dados já têm os dados num formato pronto para o serviço Power BI, como pacotes de conteúdo de fornecedores de serviços como o Google Analytics e o Twilio. As bases de dados de modelos de tabela do SQL Server Analysis Services também estão prontos. E é possível ligar-se em tempo real a bases de dados na cloud, como a Base de Dados SQL do Azure e o Spark no HDInsight.

Noutros casos, pode ser necessário consultar e carregar os dados num ficheiro. Por exemplo, imaginemos que tem dados de logística numa base de dados do armazém de dados num servidor na sua organização. No serviço Power BI, não pode ligar-se diretamente a essa base de dados e começar a explorar os dados do mesmo (a menos que se trate de uma base de dados de modelo de tabela). No entanto, é possível utilizar o Power BI Desktop ou o Excel para consultar e carregar dados de logística num modelo de dados que guarda como um ficheiro. Depois, pode importar esse ficheiro para o Power BI, onde um conjunto de dados é criado.

Deve estar a pensar: "Mas os dados de logística dessa base de dados são alterados diariamente. Como garanto que o conjunto de dados no Power BI é atualizado?" As informações de ligação do ficheiro do Power BI Desktop ou do Excel são importadas para um conjunto de dados juntamente com os dados. Se configurar a atualização agendada ou fizer uma atualização manual do conjunto de dados, o Power BI utilizará as informações de ligação do conjunto de dados, juntamente com outras configurações, para ligar diretamente à base de dados, consultar atualizações e carregar essas atualizações no conjunto de dados. Provavelmente será necessário um gateway do Power BI para proteger qualquer transferência de dados entre o servidor no local e o Power BI. Quaisquer visualizações de relatórios e dashboards são atualizadas automaticamente.

Só porque não pode ligar-se à origem de dados diretamente a partir do serviço Power BI, não significa que não possa inserir dados no Power BI. Simplesmente serão necessários alguns passos a mais e, talvez, alguma ajuda do departamento de TI. Veja [Origens de dados no Power BI Desktop](desktop-data-sources.md) para saber mais.

## <a name="some-more-details"></a>Mais alguns detalhes
Verá os termos utilizados pelo conjunto de dados e origem de dados com muita frequência no Power BI. Geralmente, são utilizados como sinónimos. No entanto, são duas coisas diferentes, embora relacionadas.

Um ***conjunto de dados*** é criado automaticamente no Power BI quando utiliza o recurso Obter Dados para ligar-se a dados e importá-los de um pacote de conteúdo ou ficheiro ou quando se liga a uma origem de dados dinâmica. Um conjunto de dados contém informações sobre as origens de dados, credenciais de origem de dados, e em muitos casos, um subconjunto de dados copiados da origem de dados. Na maioria dos casos, quando cria visualizações em relatórios e dashboards, está a analisar dados no conjunto de dados.

Uma ***origem de dados*** é o local do qual os dados de um conjunto de dados são, de facto, recebidos. Por exemplo, um serviço online, como o Google Analytics ou QuickBooks, uma base de dados na nuvem como base de dados do SQL Azure, ou uma base de dados ou ficheiro num computador local ou servidor na sua própria organização.

### <a name="data-refresh"></a>Atualização de dados
Se guardar os ficheiros na sua unidade local ou numa unidade na sua organização, pode ser necessário um gateway do Power BI para atualizar o conjunto de dados no Power BI. E o computador onde o ficheiro é guardado deve estar ligado quando ocorre uma atualização. Também pode importar novamente o ficheiro ou usar a publicação do Excel ou do Power BI Desktop, mas estes não são processos automatizados.

Se guardar os ficheiros no OneDrive para Empresas ou em Sites de Equipa do SharePoint e se ligar ou os importar para o Power BI, o conjunto de dados, relatórios e dashboard estarão sempre atualizados. Como o OneDrive e o Power BI estão na cloud, o Power BI pode ligar-se diretamente ao ficheiro guardado, uma vez por hora, e verificar se há atualizações. Se alguma for encontrada, o conjunto de dados e quaisquer visualizações são atualizadas automaticamente.

Os pacotes de conteúdo de serviços são atualizados automaticamente. Na maioria dos casos, uma vez por dia. Pode atualizar manualmente, embora a apresentação dos dados atualizados dependa do fornecedor de serviços. Pacotes de conteúdo de outras pessoas na organização dependerão das origens de dados usadas e de como a pessoa que criou o pacote de conteúdo configurou a atualização.

A Base de Dados SQL do Azure, o Azure SQL Data Warehouse e o Spark no Azure HDInsight são únicos no sentido de que são origens de dados na cloud. Como o serviço Power BI também está na cloud, o Power BI pode ligar-se a este em tempo real, utilizando o DirectQuery. O que vê no Power BI está sempre sincronizado e não é necessário configurar a atualização.

O SQL Server Analysis Services é exclusivo na medida em que, quando se liga a ele a partir do Power BI, é uma ligação em tempo real tal como uma base de dados do Azure na cloud, mas a base de dados em si está num servidor na organização. Este tipo de ligação requer um gateway do Power BI, geralmente configurado por um departamento de TI.

A atualização de dados é uma parte muito importante do Power BI e é muito profunda para ser abordada aqui. Se quiser compreendê-la, veja [Atualizar Dados no Power BI](refresh-data.md).

## <a name="considerations-and-limitations"></a>Considerações e Limitações
Para todas as origens de dados utilizadas no serviço Power BI, aplicam-se as seguintes considerações e limitações. Embora existam outras limitações que se aplicam a funcionalidades específicas, a seguinte lista aplica-se ao serviço Power BI no geral:

* **Limite de tamanho do conjunto de dados** – existe um limite de 1 GB para cada conjunto de dados no serviço Power BI.
* **Limite de linhas** – o número máximo de linhas no conjunto de dados (quando não utilizar o DirectQuery) é de 2 mil milhões, com três dessas linhas reservadas (o que resulta num máximo de 1 999 999 997 linhas utilizáveis); o número máximo quando utilizar o DirectQuery é de 1 milhão de linhas.
* **Limite de colunas** – o número máximo de colunas permitido no conjunto de dados, em todas as tabelas, é de 16 000 colunas. Isto aplica-se ao serviço Power BI e aos conjuntos de dados utilizados no Power BI Desktop. O Power BI utiliza uma coluna do número de linhas interna por tabela incluída no conjunto de dados, o que significa que o número máximo de colunas é de 16 000 menos uma para cada tabela utilizada no conjunto de dados.

