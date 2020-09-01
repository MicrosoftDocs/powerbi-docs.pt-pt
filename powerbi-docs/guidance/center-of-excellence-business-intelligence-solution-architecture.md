---
title: Arquitetura da solução de BI no Centro de Excelência
description: Saiba o que ter em conta ao conceber e desenvolver uma plataforma de BI robusta.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: v-pemyer
ms.openlocfilehash: fe55c789f5af644a802bc5c5f648315744a074be
ms.sourcegitcommit: f73ea4b9116ad186817ec5cc5d5f487d49cc0cb0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/20/2020
ms.locfileid: "88638675"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>Arquitetura da solução de BI no Centro de Excelência

Este artigo destina-se a profissionais e gestores de TI. Irá saber mais sobre a arquitetura da solução de BI no COE, bem como as diferentes tecnologias utilizadas. As tecnologias incluem o Azure, Power BI e Excel. Pode tirar partido de todas essas tecnologias para criar uma plataforma de BI na cloud dimensionável e baseada em dados.

Conceber uma plataforma de BI robusta é um pouco como construir uma ponte que liga dados de origem transformados e melhorados aos consumidores de dados. A conceção de uma estrutura tão complexa requer uma mentalidade de engenheiro, embora possa ser uma das arquiteturas de TI mais criativas e gratificantes que pode conceber. Numa grande organização, uma arquitetura da solução de BI pode consistir em:

- Origens de dados
- Ingestão de dados
- Macrodados/preparação de dados
- Armazém de dados
- Modelos semânticos de BI
- Relatórios

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="Diagrama a mostrar o diagrama da arquitetura da plataforma de BI, desde origens de dados à ingestão de dados, macrodados, arquivo, armazém de dados, modelos semânticos de BI, relatórios e aprendizagem automática.":::

A plataforma tem de suportar exigências específicas. Mais especificamente, tem de ter a capacidade de dimensionamento e desempenho necessária para cumprir as expectativas dos serviços empresariais e dos consumidores de dados. Além disso, tem de ser totalmente segura. Tem de ser suficientemente resiliente para se adaptar à mudança, pois é certo que, eventualmente, será necessário colocar online novos dados e áreas de assunto.

## <a name="frameworks"></a>Estruturas

Na Microsoft, adotámos desde o início uma abordagem baseada em sistemas, ao investir no desenvolvimento de estruturas. As estruturas técnicas e empresariais aumentam a reutilização do design e da lógica e fornecem um resultado consistente. Também oferecem flexibilidade no aproveitamento da arquitetura de muitas tecnologias. Além disso, simplificam e reduzem os custos de engenharia através de processos repetíveis.

Aprendemos que as estruturas bem concebidas aumentam a visibilidade da linhagem de dados, análise de impacto, manutenção da lógica de negócio, gestão da taxonomia e simplificação da governação. Adicionalmente, o desenvolvimento tornou-se mais rápido e a colaboração em grandes equipas tornou-se mais reativa e eficaz.

Iremos descrever várias estruturas neste artigo.

## <a name="data-models"></a>Modelos de dados

Os modelos de dados permitem-lhe controlar a estrutura e o acesso aos dados. Para os serviços empresariais e consumidores de dados, os modelos de dados são a interface da plataforma de BI.

Uma plataforma de BI pode fornecer três tipos de modelos:

- Modelos empresariais
- Modelos semânticos de BI
- Modelos de Machine Learning (ML)

### <a name="enterprise-models"></a>Modelos empresariais

Os **modelos empresariais** são compilados e mantidos por arquitetos de TI. Por vezes, são denominados modelos dimensionais ou data marts. Normalmente, os dados são armazenados no formato relacional como tabelas de dimensões e factos. Essas tabelas armazenam dados limpos e melhorados consolidados a partir de muitos sistemas. Além disso, representam uma origem autoritativa de relatórios e análises.

Os modelos empresariais oferecem uma origem de dados de relatórios de BI única e consistente. São compilados uma vez e partilhados como o padrão da empresa. As políticas de governação garantem que os dados estão protegidos, logo o acesso a conjunto de dados confidenciais, como informações ou dados financeiros dos clientes, é limitado com base na necessidade. As políticas adotam convenções de nomenclatura que garantem a consistência e reforçam a credibilidade e a qualidade dos dados.

Numa plataforma de BI na cloud, os modelos empresariais podem ser implementados num [conjunto do Synapse SQL no Azure Synapse](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse). Assim, o conjunto do Synapse SQL torna-se uma versão única dos dados que a organização pode utilizar para obter informações rápidas e robustas.

### <a name="bi-semantic-models"></a>Modelos semânticos de BI

Os **modelos semânticos de BI** representam uma camada semântica dos modelos empresariais. São compilados e mantidos por programadores e utilizadores empresariais de BI. Os programadores de BI criam modelos semânticos de BI que obtêm dados a partir de modelos empresariais. Os utilizadores empresariais podem criar modelos independentes em pequena escala ou expandir os modelos semânticos de BI com origens departamentais ou externas. Por norma, os modelos semânticos de BI focam-se numa única área de assunto e são, muitas vezes, amplamente partilhados.

Além de serem ativadas por dados, as capacidades empresariais utilizam modelos semânticos de BI que descrevem conceitos, relações, regras e padrões. Assim, representam estruturas simples e intuitivas que definem relações de dados e englobam regras de negócio como cálculos. Também podem aplicar permissões de dados detalhadas e garantir que as pessoas certas têm acesso aos dados certos. Além disso, aceleram o desempenho das consultas e fornecem análises interativas extremamente responsivas, mesmo com terabytes de dados. Tal como os modelos empresariais, os modelos semânticos de BI utilizam convenções de nomenclatura para garantir a consistência.

Numa plataforma de BI da cloud, os programadores de BI podem implementar modelos semânticos de BI no [Azure Analysis Services](/azure/analysis-services/) ou em [capacidades do Power BI Premium](../admin/service-premium-what-is.md#dedicated-capacities). Se a utiliza como camada de relatórios e análise, recomendamos a respetiva implementação no Power BI. Estes produtos suportam vários modos de armazenamento e permitem que as tabelas dos modelos de dados coloquem os respetivos dados em cache ou utilizem o [DirectQuery](directquery-model-guidance.md), que é uma tecnologia que envia consultas para a origem de dados adjacente. O DirectQuery é um modo de armazenamento ideal quando as tabelas dos modelos representam grandes volumes de dados ou quando é necessidade fornecer resultados quase em tempo real. É possível combinar ambos os modos de armazenamento: Os [modelos compostos](composite-model-guidance.md) combinam tabelas que utilizam vários modos de armazenamento num único modelo.

No caso dos modelos com muitas consultas, é possível utilizar o [Balanceador de Carga do Azure](/azure/load-balancer/load-balancer-overview) para distribuir uniformemente a carga das consultas em réplicas de modelos. Tal também lhe permite dimensionar aplicações e criar modelos semânticos de BI de elevada disponibilidade.

### <a name="machine-learning-models"></a>Modelos de Machine Learning

Os [ **modelos de Machine Learning (ML)** ](/windows/ai/windows-ml/what-is-a-machine-learning-model) são compilados e mantidos por cientistas de dados. Tendem a ser desenvolvidos a partir de origens de dados não processadas no data lake.

Os modelos de ML preparados podem revelar padrões nos dados. Em muitas circunstâncias, esses padrões podem ser utilizados para efetuar predições que podem ser utilizadas para melhorar os dados. Por exemplo, o comportamento de compra pode ser utilizado para prever o abandono de clientes ou segmentar os mesmos. Os resultados das predições podem ser adicionados a modelos empresariais para permitir a realização de análises por segmento de clientes.

Numa plataforma de BI na cloud, pode utilizar o [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml) para preparar, implementar, automatizar, gerir e monitorizar modelos de ML.

## <a name="data-warehouse"></a>Armazém de dados

No centro de uma plataforma de BI está o armazém de dados, que aloja os modelos empresariais. É uma origem de dados sancionados (como um sistema de registo e um hub) que cria modelos empresariais de relatórios, de BI e de ciência de dados.

Muitos serviços empresariais, incluindo aplicações de linha de negócio (LOB), podem contar com o armazém de dados como origem de conhecimentos empresariais autoritativa e gerida.

Na Microsoft, o armazém de dados é alojado no [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction) (ADLS Gen2) e no Azure Synapse Analytics.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="Uma imagem que mostra o Azure Synapse Analytics a estabelecer ligação ao Azure Data Lake Storage Gen2.":::

- O **ADLS Gen2** faz do Armazenamento do Azure a base de compilação de data lakes empresariais no Azure. Foi concebido para armazenar múltiplos petabytes de informações e aguentar centenas de gigabits de débito. Além disso, oferece uma capacidade de armazenamento e transações de baixo custo e suporta acesso compatível com o Hadoop, o que lhe permite gerir e aceder a dados tal como faria com um Sistema de Ficheiros Distribuído Hadoop (HDFS). Na verdade, o [Azure HDInsight](/azure/hdinsight/), o [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) e o Azure Synapse Analytics podem aceder a dados armazenados no ADLS Gen2. Numa plataforma de BI, é uma boa ideia armazenar dados de origem não processados, dados semiprocessados ou de teste e dados de produção. Utilizamo-los para armazenar todos os dados empresariais.
- O **Azure Synapse Analytics** é um serviço de análise que combina o armazenamento de dados empresariais e a análise de Macrodados. Dá-lhe a liberdade de consultar dados nos seus termos, através de recursos a pedido ou aprovisionados sem servidor, em escala. O Synapse SQL, que é um componente do Azure Synapse Analytics, suporta análises completas baseadas no T-SQL. Assim, é ideal alojar modelos empresariais com as suas tabelas e dimensões e factos. Pode carregar as tabelas de forma eficiente a partir do ADLS Gen2 através de consultas simples do [Polybase T-SQL](/sql/relational-databases/polybase/polybase-guide). Em seguida, pode utilizar a [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) para executar análises de elevado desempenho.

### <a name="business-rules-engine-framework"></a>Estrutura do Motor de Regras de Negócio

Desenvolvemos uma estrutura do **Motor de Regras de Negócio** (BRE) para catalogar qualquer lógica de negócio que possa ser implementada na camada do armazém de dados. Um BRE pode ser implicar muitas coisas. No entanto, no contexto de um armazém de dados, um BRE é útil para criar colunas calculadas em tabelas relacionais. Por norma, estas colunas calculadas são representadas como cálculos ou expressões matemáticas através de instruções condicionais.

A intenção é separar a lógica de negócio do código de BI. Tradicionalmente, as regras de negócio são transformadas em procedimentos armazenados do SQL. Frequentemente, isto resulta num maior esforço de manutenção quando as necessidades empresariais mudam. Num BRE, as regras de negócio são definidas uma vez e utilizadas múltiplas vezes quando aplicadas a diferentes entidades de armazéns de dados. Se tiver de alterar a lógica de negócio, terá de atualizá-la apenas num único local e não em numerosos procedimentos armazenados. Também existe um benefício secundário. Uma estrutura de BRE promove a transparência e a visibilidade na lógica de negócio, que pode ser exposta através de um conjunto de relatórios que cria documentação de atualização autónoma.

## <a name="data-sources"></a>Origens de dados

Um armazém de dados pode consolidar dados de qualquer origem de dados. Em grande parte, é baseado em origens de dados LOB, que são bases de dados relacionais que armazenam dados específicos de vendas, marketing, finanças, entre outros. Estas bases de dados podem ser alojadas na cloud ou ser guardadas no local. Outras origens de dados podem ser baseadas em ficheiros, especialmente registos Web ou IOT originados através de dados de dispositivos. Além disso, os dados podem ser provenientes de fornecedores de Software como Serviço (SaaS).

Na Microsoft, alguns dos sistemas internos produzem dados operacionais diretamente para o ADLS Gen2 através de formatos de ficheiros não processados. Além do data lake, outros sistemas de origens incluem aplicações LOB relacionais, livros do Excel, outras origens baseadas em ficheiros, Gestão de Dados Globais (MDM) e repositórios de dados personalizados. Os repositórios de MDM permitem-nos gerir os nossos principais dados, de modo a garantir a autoritatividade, a normalização e a validação das versões de dados.

## <a name="data-ingestion"></a>Ingestão de dados

De forma periódica, em conformidade com o ritmo da empresa, os dados são ingeridos através de sistemas de origem e carregados no armazém de dados. Isto pode ocorrer uma vez por dia ou em intervalos mais frequentes. A ingestão de dados está relacionada com a extração, a transformação e o carregamento de dados ou talvez com o oposto: a extração, carregamento e transformação de dados. A diferença resume-se ao local de transformação dos dados. As transformações são aplicadas para limpar, conformar, integrar e normalizar os dados. Para obter mais informações, veja [Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) [Extração, transformação e carregamento (ETL)].

Em última instância, o objetivo é carregar os dados certos para o modelo empresarial da forma mais rápida e eficiente possível.

Na Microsoft, utilizamos o [Azure Data Factory](/azure/data-factory/introduction) (ADF). O serviço é utilizado para agendar e orquestrar validações, transformações e carregamentos de dados em massa a partir de sistemas de origens externos para o nosso data lake. É gerido por estruturas personalizadas que processam dados em paralelo e em escala. Além disso, são criados registos abrangentes para suportar a resolução de problemas e a monitorização do desempenho, bem como acionar notificações de alerta quando são cumpridas certas condições.

Entretanto, o [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) (uma plataforma de análise baseada no Apache Spark otimizada para a plataforma de serviços cloud do Azure) efetua transformações para fins de ciência de dados. Também compila e executa modelos de ML através de blocos de notas do Python. As classificações desses modelos de ML são carregadas no armazém de dados, de modo a integrar predições com aplicações e relatórios empresariais. O Azure Databricks elimina ou minimiza a necessidade de copiar ou adquirir dados, uma vez que acede diretamente aos ficheiros do data lake.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="Uma imagem que mostra o Azure Data Factory a obter e orquestrar pipelines de dados com o Azure Databricks através do Azure Data Lake Storage Gen2.":::

### <a name="ingestion-framework"></a>Estrutura de ingestão de dados

Desenvolvemos uma **estrutura de ingestão de dados** como um conjunto de tabelas e procedimentos de configuração. Esta suporta uma abordagem de aquisição de grandes volumes baseada em dados a alta velocidade e com o mínimo de código. Em suma, esta estrutura simplifica o processo de aquisição de dados para carregar o armazém de dados.

A estrutura depende de tabelas de configuração que armazenam informações relacionadas com a origem e o destino dos dados, como o tipo de origem, o servidor, a base de dados, o esquema e os detalhes referentes à tabela. Esta abordagem significa que não temos de desenvolver pipelines específicos do ADF nem pacotes do [SQL Server Integration Services (SSIS)](/sql/integration-services/sql-server-integration-services). Em vez disso, os procedimentos são escritos numa linguagem escolhida por nós para a criação de pipelines do ADF que são gerados e executados de forma dinâmica. Deste modo, a aquisição de dados torna-se um exercício de configuração facilmente operacionalizado. Tradicionalmente, tal exigiria muitos recursos de desenvolvimento para criar pacotes hard-coded do ADF ou SSIS.

A estrutura de ingestão de dados também foi concebida para simplificar o processo envolvido nas alterações do esquema das origens de dados. Se forem detetadas alterações no esquema, pode atualizar facilmente os dados de configuração de forma manual ou automática para adquirir atributos recentemente adicionados no sistema de origem.

### <a name="orchestration-framework"></a>Estrutura de orquestração

Desenvolvemos uma **estrutura de orquestração** para operacionalizar e orquestrar pipelines de dados. Esta estrutura utiliza um design baseado em dados que depende de um conjunto de tabelas de configuração. Essas tabelas armazenam metadados que descrevem as dependências dos pipelines e os métodos de mapeamento de dados da origem às estruturas de dados. O investimento envolvido no desenvolvimento desta estrutura adaptativa compensou os investimentos, pois os movimentos de dados já não têm de ser hard-coded.

## <a name="data-storage"></a>Armazenamento de dados

Um data lake pode armazenar grandes volumes de dados não processados para utilização futura, juntamente com transformações de dados de teste.

Na Microsoft, o ADLS Gen2 é a única fonte fidedigna. Armazenamos dados não processados juntamente com dados de teste e de produção. Este método fornece uma solução de data lake altamente dimensionável e económica para a análise de macrodados. Ao utilizar um sistema de ficheiros de elevado desempenho em grande escala, o método é otimizado para cargas de trabalho de análise de dados e acelera o tempo de obtenção de informações.

Os ADLS Gen2 fornecem o melhor de dois mundos: o armazenamento de Blobs e um espaço de nomes do sistema de ficheiros de elevado desempenho, que configuramos com permissões de acesso detalhadas.

Em seguida, os dados refinados são armazenados numa base de dados relacional para fornecer um arquivo de dados dimensionável e de elevado desempenho para modelos empresariais. Este arquivo inclui segurança, governação e capacidade de gestão. Os data marts de áreas de assunto específicas são armazenados no Azure Synapse Analytics e carregados por consultas do Azure Databricks ou Polybase T-SQL.

## <a name="data-consumption"></a>Consumo de dados

Na camada dos relatórios, os serviços empresariais consomem dados do armazém de dados. Além disso, acedem diretamente a dados no data lake para a realização de análises ad hoc ou de tarefas de ciência de dados.

São aplicadas permissões detalhadas em todas as camadas: no data lake, nos modelos empresariais e nos modelos semânticos de BI. As permissões garantem que os consumidores de dados só podem ver os dados aos quais têm direitos de acesso.

Na Microsoft, utilizamos relatórios e dashboards do Power BI e [relatórios paginados do Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md). Parte da análise ad hoc e de relatórios é realizada no Excel, especialmente no caso dos relatórios financeiros.

Publicamos dicionários de dados, que fornecem informações de referência sobre os modelos de dados. Disponibilizamo-los aos utilizadores para poderem descobrir informações sobre a plataforma de BI. Os dicionários apresentam designs de modelos e fornecem descrições sobre entidades, formatos, estruturas, linhagens de dados, relações e cálculos. Utilizamos o [Catálogo de Dados do Azure](/azure/data-catalog/overview) para facilitarmos a descoberta e a compreensão das nossas origens de dados.

Normalmente, os padrões de consumo de dados diferem com base na função:

- Os **analistas de dados** ligam-se diretamente aos principais modelos semânticos de BI. Quando os modelos semânticos de BI contêm todos os dados e todas as lógicas necessários, utilizam ligações em direto para criar relatórios e dashboards do Power BI. Quando necessitam de expandir os modelos com dados departamentais, criam [modelos compostos](composite-model-guidance.md) do Power BI. Se forem necessários relatórios com folhas de cálculo, utilizam o Excel para produzir relatórios com base em modelos semânticos de BI ou em modelos semânticos de departamentos de BI.
- Os **programadores de BI** e os criadores de relatórios operacionais ligam-se diretamente a modelos empresariais. Utilizam o Power BI Desktop para criar relatórios de análise de ligações em direto. Também podem criar relatórios operacionais como relatórios paginados do Power BI ao criarem consultas nativas do SQL para acederem a dados dos modelos empresariais do Azure Synapse Analytics através do T-SQL ou modelos semânticos do Power BI através do DAX ou MDX.
- Os **cientistas de dados** ligam-se diretamente aos dados no data lake. Utilizam os blocos de notas do Python e do Azure Databricks para desenvolver modelos de ML, que tendem a ser experimentais e requerem competências especiais para fins de produção.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="Uma imagem a mostrar a utilização do Azure Synapse Analytics com o Power BI, o Excel e o Azure Machine Learning.":::

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [BI Empresarial no Azure com o Azure Synapse Analytics](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

### <a name="professional-services"></a>Serviços profissionais

Os parceiros certificados do Power BI estão disponíveis para ajudar a sua organização a ser bem-sucedida na preparação de um COE. Estes podem proporcionar-lhe uma preparação económica ou uma auditoria dos dados. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).

Também pode interagir com parceiros de consultoria experientes. Estes podem ajudar a [analisar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [avaliar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) ou [implementar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) o Power BI.
