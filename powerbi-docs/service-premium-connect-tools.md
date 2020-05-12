---
title: Conectividade e gestão dos conjuntos de dados com o ponto final XMLA no Power BI Premium (Pré-visualização)
description: Descreve como ligar aos conjuntos de dados no Power BI Premium a partir de ferramentas e aplicações cliente.
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/26/2020
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 776ef09de58c2bb3b47a6d55ae5e8cf2be0cf228
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82613688"
---
# <a name="dataset-connectivity-with-the-xmla-endpoint-preview"></a>Dataset connectivity with the XMLA endpoint (Preview) (Conectividade de conjuntos de dados com o ponto final de XMLA [Pré-visualização])

As áreas de trabalho e os conjuntos de dados do Power BI Premium ao nível de compatibilidade de 1500 e superior suportam a conectividade de plataforma aberta da Microsoft e aplicações e ferramentas de cliente de terceiros através de um *ponto final XMLA*.

> [!NOTE]
> Esta funcionalidade está em **Pré-visualização**. As funcionalidades em Pré-visualização não devem ser utilizadas num ambiente de produção. Algumas funcionalidades, o suporte e a documentação são limitados.  Veja os [Termos do Microsoft Online Services (OST)](https://www.microsoft.com/licensing/product-licensing/products?rtc=1) para obter mais detalhes.

## <a name="whats-an-xmla-endpoint"></a>O que é um ponto final XMLA?

O Power BI Premium utiliza o protocolo [XML for Analysis](https://docs.microsoft.com/analysis-services/xmla/xml-for-analysis-xmla-reference?view=power-bi-premium-current) (XMLA) para comunicações entre as aplicações cliente e o motor que gere as áreas de trabalho e os conjuntos de dados do Power BI. Estas comunicações são geralmente feitas através daquilo a que chamamos pontos finais XMLA. O XMLA é o mesmo protocolo de comunicação utilizado pelo motor da Microsoft Analysis Services que, nos bastidores, executa a modelagem semântica, a governação, o ciclo de vida e a gestão de dados do Power BI.

Por predefinição, a conectividade *só de leitura* através do ponto final está ativada para a **carga de trabalho dos Conjunto de dados** numa capacidade. Com permissão só de leitura, as aplicações e ferramentas de visualização de dados podem consultar dados de modelos de conjuntos de dados, metadados, eventos e esquemas. As operações de *leitura/escrita* com o ponto final podem ser ativadas para permitir gestão de conjuntos de dados, governação, modelação semântica avançada, depuração e monitorização adicionais. Com as operações de leitura/escrita ativas, os conjuntos de dados do Power BI Premium têm maior paridade com as ferramentas e os processos de modelação tabular de nível empresarial do Azure Analysis Services e do SQL Server Analysis Services.

## <a name="data-modeling-and-management-tools"></a>Ferramentas de modelação e gestão de dados

Estas são algumas das ferramentas mais comuns utilizadas com o Azure Analysis Services e o SQL Server Analysis Services, agora suportadas por conjuntos de dados do Power BI Premium:

**Visual Studio com projetos do Analysis Services**  – também conhecido como SQL Server Data Tools, ou simplesmente **SSDT**, esta é uma ferramenta de criação de modelos de nível empresarial para modelos tabulares do Analysis Services. As extensões dos projetos do Analysis Services são suportadas em todas as edições do Visual Studio 2017 e posteriores, incluindo a Community Edition gratuita. É necessária a extensão com a versão 2.9.6 ou superior para implementar os modelos tabulares numa área de trabalho Premium. Ao implementar numa área de trabalho Premium, o modelo tem de estar no nível de compatibilidade de 1500 ou superior. A leitura/escrita XMLA é necessária na carga de trabalho dos conjuntos de dados. Para obter mais informações, veja [Tools for Analysis Services](https://docs.microsoft.com/analysis-services/tools-and-applications-used-in-analysis-services?view=power-bi-premium-current) (Ferramentas do Analysis Services).

**SQL Server Management Studio (SSMS)**   – suporta consultas DAX, MDX, XMLA. Execute operações de atualização detalhadas e scripting de metadados de conjuntos de dados com a [Tabular Model Scripting Language](https://docs.microsoft.com/analysis-services/tmsl/tabular-model-scripting-language-tmsl-reference) (Linguagem TMSL). É necessária a permissão só de leitura para as operações de consulta. É necessária a permissão de leitura/escrita para o scripting de metadados. É necessário o SSMS com a versão 18.4 ou superior. Faça o download  [aqui](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

**SQL Server Profiler**  – instalado com o SSMS, esta ferramenta permite o rastreio e a depuração de eventos de conjuntos de dados. Embora oficialmente preterido para o SQL Server, o Profiler continua a ser incluído no SSMS e continua a ser suportado para o Analysis Services e o Power BI Premium. É necessária a permissão só de leitura XMLA. Para obter mais informações, veja  [SQL Server Profiler for Analysis Services](https://docs.microsoft.com/analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services?view=power-bi-premium-current) (SQL Server Profiler para o Analysis Services).

**Assistente de Implementação do Analysis Services**  – instalado com o SSMS, esta ferramenta permite a implementação de projetos de modelos tabulares criados pelo Visual Studio nas áreas de trabalho do Analysis Services e do Power BI Premium. Pode ser executado interativamente ou na linha de comandos da automatização. É necessária a permissão de escrita/leitura XMLA. Para obter mais informações, veja [Analysis Services Deployment Wizard](https://docs.microsoft.com/analysis-services/deployment/deploy-model-solutions-using-the-deployment-wizard?view=power-bi-premium-current) (Assistente de Implementação do Analysis Services).

**cmdlets do PowerShell**  – os cmdlets de Analysis Services podem ser utilizados para automatizar as tarefas de gestão dos conjuntos de dados como operações de atualização. É necessária a permissão de escrita/leitura XMLA. É necessária a versão **21.1.18221** ou superior do [módulo PowerShell SqlServer](https://www.powershellgallery.com/packages/SqlServer/). Os cmdlets do Azure Analysis Services no módulo Az.AnalysisServices não são suportados no Power BI Premium. Para obter mais informações, veja [Analysis Services PowerShell Reference](https://docs.microsoft.com/analysis-services/powershell/analysis-services-powershell-reference?view=power-bi-premium-current) (Referências do PowerShell do Analysis Services).

**Report Builder do Power BI**  – uma ferramenta para criar relatórios paginados. Crie uma definição de relatório que especifica os dados a obter, o local de obtenção e a forma como estes são apresentados. Pode pré-visualizar o relatório no Report Builder e, em seguida, publicá-lo no serviço Power BI. É necessária a permissão só de leitura XMLA. Para obter mais informações, veja  [Power BI Report Builder](https://docs.microsoft.com/power-bi/report-builder-power-bi).

**Tabular Editor** – uma ferramenta open-source para criar, manter e gerir modelos tabulares com um editor intuitivo e leve. Uma vista hierárquica mostra todos os objetos no modelo tabular. Os objetos são organizados por pastas de apresentação com suporte para edição de propriedades de seleção múltipla e realce da sintaxe DAX. É necessária a permissão só de leitura XMLA para as operações de consulta. É necessária a permissão de leitura/escrita para as operações de metadados. Para obter mais informações, veja [tabulareditor.github.io](https://tabulareditor.github.io/).

**DAX Studio**  – uma ferramenta open-source para a criação, o diagnóstico, a otimização do desempenho e a análise DAX. As funcionalidades incluem navegação de objetos, rastreio integrado, discriminações de execução de consultas com estatísticas detalhadas, realce da sintaxe e formatação DAX. É necessária a permissão só de leitura XMLA para as operações de consulta. Para obter mais informações, veja  [daxstudio.org](https://daxstudio.org/).

**ALM Toolkit** – uma ferramenta de comparação de esquemas open-source para conjuntos de dados do Power BI, mais frequentemente utilizada para cenários de gestão de ciclos de vida das aplicações (ALM). Execute a implementação em vários ambientes e retenha dados históricos de atualizações incrementais. Diferencie e intercale ficheiros, ramos e repositórios de metadados. Reutilize definições comuns entre conjuntos de dados. É necessária a permissão só de leitura para as operações de consulta. É necessária a permissão de leitura/escrita para as operações de metadados. Para obter mais informações, veja  [alm-toolkit.com](http://alm-toolkit.com/).

**Microsoft Excel**  – as Tabelas Dinâmicas do Excel são uma das ferramentas mais comuns utilizadas para resumir, analisar, explorar e apresentar dados de resumo dos conjuntos de dados do Power BI. É necessária a permissão só de leitura para as operações de consulta. É necessária a versão “Clique-e-Use” do Office 16.0.11326.10000 ou superior.

**Terceiros**  – inclui aplicações e ferramentas de visualização de dados cliente que se podem ligara conjuntos de dados, consultá-los e consumi-los no Power BI Premium. A maioria das ferramentas exige as versões mais recentes das bibliotecas de cliente MSOLAP, mas alguns podem utilizar ADOMD. O Ponto final XMLA só de leitura ou de leitura/escrita está dependente das operações.

### <a name="client-libraries"></a>Bibliotecas de cliente

As aplicações cliente não comunicam diretamente com o ponto final XMLA. Em vez disso, utilizam *bibliotecas de cliente* como camada de abstração. Estas são as mesmas bibliotecas de cliente que as aplicações utilizam para ligar ao Analysis Services e ao SQL Server Analysis Services. As aplicações da Microsoft, como o Excel, o SQL Server Management Studio (SSMS) e a extensão de projetos do Analysis Services para o Visual Studio instalam as três bibliotecas de cliente e atualizam-nas juntamente com as atualizações habituais de aplicações e extensões. Os programadores também podem utilizar as bibliotecas de cliente para criar aplicações personalizadas. Em alguns casos, especialmente com aplicações de terceiros, caso não sejam instaladas com a aplicação, poderá ter de instalar as versões mais recentes das bibliotecas de cliente. As bibliotecas de cliente são atualizadas mensalmente. Para obter mais informações, veja  [Bibliotecas de cliente para ligar ao Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="supported-write-operations"></a>Operações de escrita suportadas

Os metadados de conjuntos de dados são expostos através das bibliotecas de cliente com base no Modelo de Objeto em Tabela (TOM) para os programadores criarem aplicações personalizadas. Tal permite ativar o Visual Studio e as ferramentas da comunidade open-source, como o Tabular Editor, para permitir capacidades de modelação e implementação de dados adicionais suportadas pelo motor do Analysis Services, mas ainda não suportadas no Power BI Desktop. As funcionalidades adicionais de modelação de dados incluem:

- Os [Calculation groups](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups?view=power-bi-premium-current) (Grupos de cálculo) para a reutilização de cálculos e o consumo simplificado de modelos complexos.

- As [Metadata translations](https://docs.microsoft.com/analysis-services/tabular-models/translations-in-tabular-models-analysis-services?view=power-bi-premium-current) (Traduções de metadados) para suportar relatórios e conjuntos de dados com vários idiomas.

- As [Perspectives](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular?view=power-bi-premium-current) (Perspetivas) para definir vistas específicas focadas e específicas do domínio empresarial dos metadados dos conjuntos de dados.

A segurança ao nível do objeto (OLS) ainda não é suportada nos conjuntos de dados do Power BI Premium.

## <a name="optimize-datasets-for-write-operations"></a>Otimizar conjuntos de dados para operações de escrita

Ao utilizar o ponto final XMLA para a gestão de conjuntos de dados com operações de escrita, recomenda-se que ative o conjunto de dados para modelos grandes, o que reduz a sobrecarga das operações de escrita e torná-las consideravelmente mais rápidas. Para conjuntos de dados com mais de 1 GB de tamanho (após a compressão), a diferença pode ser significativa. Para obter mais informações, veja [Modelos grandes no Power BI Premium](service-premium-large-models.md).

## <a name="enable-xmla-read-write"></a>Ativar a leitura/escrita XMLA

Por predefinição, uma capacidade Premium tem a definição da propriedade Ponto final XMLA ativada para só de leitura. Tal significa que as aplicações só podem consultar o conjunto de dados. Para que as aplicações possam realizar operações de escrita, a propriedade Ponto final XMLA tem de ser ativada para leitura/escrita. A definição da propriedade Ponto final XMLA para uma capacidade é configurada na **carga de trabalho de Conjuntos de dados**. A definição Ponto final XMLA aplica-se a *todas as áreas de trabalho e conjuntos de dados* atribuídos à capacidade.

### <a name="to-enable-read-write-for-a-capacity"></a>Para permitir a leitura/escrita para uma capacidade

1. No Portal de administração, clique em **Definições de capacidades** > **Power BI Premium** > nome da capacidade.
2. Expanda as **Cargas de trabalho**. Na definição **Ponto final XMLA**, selecione **Leitura/Escrita**.

    ![Ativar o ponto final XMLA](media/service-premium-connect-tools/xmla-endpoint-enable.png)

## <a name="connecting-to-a-premium-workspace"></a>Ligar a uma área de trabalho Premium

As áreas de trabalho atribuídas a uma capacidade dedicada têm uma cadeia de ligação no formato URL como esta, `powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]`.

As aplicações que se ligam à área de trabalho utilizam o URL como se se tratasse de um nome de servidor do Analysis Services. Por exemplo, `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`.

Os utilizadores com UPNs no mesmo inquilino (não B2B) podem substituir o nome do inquilino por `myorg`. Por exemplo,  `powerbi://api.powerbi.com/v1.0/myorg/Sales Workspace`.

### <a name="to-get-the-workspace-connection-url"></a>Para obter o URL de ligação da área de trabalho

Em **Definições** > **Premium** > **Ligação da Área de Trabalho** da área de trabalho, clique em **Copiar**.

![Cadeia de ligação de área de trabalho](media/service-premium-connect-tools/xmla-endpoint-workspace-connection.png)

## <a name="connection-requirements"></a>Requisitos de ligação

### <a name="initial-catalog"></a>Catálogo inicial

Com algumas ferramentas, como o SQL Server Profiler, pode ter de especificar um *Catálogo Inicial*. Especifique um conjunto de dados (base de dados) na sua área de trabalho. Na caixa de diálogo **Ligar ao Servidor**, clique em **Opções** > **Propriedades da Ligação** > **Ligar à base de dados** e introduza o nome do conjunto de dados.

### <a name="duplicate-workspace-names"></a>Duplicar nomes da área de trabalho

As [novas áreas de trabalho](service-new-workspaces.md) (criadas com a nova experiência da área de trabalho) no Power BI impõem a validação para não permitir a criação ou alteração de nome de áreas de trabalho com nomes duplicados. As áreas de trabalho que não tenham sido migradas podem resultar em nomes duplicados. Ao ligar a uma área de trabalho com o mesmo nome de outra área de trabalho, poderá ocorrer o seguinte erro:

**Não é possível ligar a powerbi://api.powerbi.com/v1.0/[nome do inquilino]/[nome da área de trabalho].**

Para contornar este erro, além do nome de área de trabalho, especifique o ObjectIDGuid, que pode ser copiado do objectID da área de trabalho no URL. Anexe o objectID ao URL de ligação. Por exemplo,  
“powerbi://api.powerbi.com/v1.0/myorg/Contoso Sales - 9d83d204-82a9-4b36-98f2-a40099093830”.

### <a name="duplicate-dataset-name"></a>Duplicar o nome do conjunto de dados

Ao ligar a um conjunto de dados com o mesmo nome de outro conjunto de dados na mesma área de trabalho, anexe o GUID de conjunto de dados ao nome do conjunto de dados. Pode obter o nome do conjunto de dados e o GUID quando estiver ligado à área de trabalho no SSMS.

### <a name="delay-in-datasets-shown"></a>Atraso nos conjuntos de dados apresentados

Ao ligar-se a uma área de trabalho, as alterações dos conjuntos de dados novos, eliminados e renomeados podem demorar alguns minutos a aparecer.

### <a name="unsupported-datasets"></a>Conjuntos de dados não suportados

Os seguintes conjuntos de dados não estão acessíveis pelo ponto final XMLA. Estes conjuntos de dados não serão apresentados na área de trabalho no SSMS ou noutras ferramentas:

- Os conjuntos de dados com base numa ligação em direto a um modelo do Azure Analysis Services ou do SQL Server Analysis Services. 
- Conjuntos de dados com base numa ligação em direto a um conjunto de dados do Power BI noutra área de trabalho. Para obter mais informações, veja [Introdução aos conjuntos de dados em áreas de trabalho](service-datasets-across-workspaces.md).
- Conjuntos de dados com envio de dados via Push através da API REST.
- Conjuntos de dados de livros do Excel.

## <a name="security"></a>Segurança

Além da propriedade Ponto final XMLA estar ativada como leitura/escrita pelo administrador da capacidade, a definição **Exportar dados** ao nível do inquilino no Portal de Administração do Power BI, também necessária para a Análise do Excel, tem de estar ativada.

![Ativar Exportar dados](media/service-premium-connect-tools/xmla-endpoint-export-data.png)

O acesso através do ponto final XMLA irá respeitar a associação do grupo de segurança definida ao nível da área de trabalho/aplicação.

Os contribuidores da área de trabalho (e acima) têm acesso de escrita ao conjunto de dados e, portanto, são equivalentes aos administradores da base de dados do Analysis Services. Podem implementar novos conjuntos de dados do Visual Studio e executar scripts TMSL no SSMS.

Atualmente, as operações que requerem permissões de administrador do servidor do Analysis Services (em vez de administrador de base de dados), tais como rastreios ao nível do servidor e representação de utilizador através da propriedade cadeia-ligação [EffectiveUserName](https://docs.microsoft.com/analysis-services/instances/connection-string-properties-analysis-services?view=power-bi-premium-current#bkmk_auth), não são suportadas no Power BI Premium.

Outros utilizadores que tenham [permissão de Criação](service-datasets-build-permissions.md) num conjunto de dados são equivalentes aos leitores de bases de dados do Analysis Services. Podem ligar-se e navegar por conjuntos de dados para o consumo e visualização de dados. As regras de segurança ao nível da linha (RLS) são respeitadas e não conseguem ver metadados de conjuntos de dados internos.

### <a name="model-roles"></a>Funções de modelo

Os metadados de conjuntos de dados através do ponto final XMLA podem criar, modificar ou eliminar funções de modelo de um conjunto de dados, incluindo a definição de filtros de segurança ao nível da linha (RLS). As funções de modelo no Power BI são utilizadas apenas para RLS. Utilize o modelo de segurança do Power BI para controlar as permissões além da RLS.

As seguintes limitações aplicam-se ao trabalhar com funções de conjuntos de dados através do ponto final XMLA:

- **Durante a pré-visualização pública, não pode especificar as associações de funções de um conjunto de dados através do ponto final XMLA**. Em vez disso, especifique os membros da função na página Segurança ao Nível da Linha de um conjunto de dados no serviço Power BI.
- A única permissão para uma função que pode ser definida para conjuntos de dados do Power BI é a permissão de Leitura. É necessária a autorização de criação para um conjunto de dados para o acesso de leitura através do ponto final XMLA, independentemente da existência de funções de conjunto de dados. Utilize o modelo de segurança do Power BI para controlar as permissões além da RLS.
- As regras de segurança ao nível do objeto (OLS) não são atualmente suportadas no Power BI.

### <a name="setting-data-source-credentials"></a>Definir credenciais de origem de dados

Os metadados especificados através do ponto final XMLA podem criar ligações a origens de dados, mas não podem definir credenciais de origem de dados. Em vez disso, as credenciais podem ser definidas na página de definições de conjuntos de dados no Serviço Power BI.

### <a name="service-principals"></a>Principais de serviço

Durante a pré-visualização pública, a ligação com o ponto final XMLA através de um [principal de serviço](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals) para cenários de automatização ainda não é suportada.

## <a name="deploy-model-projects-from-visual-studio-ssdt"></a>Implementar projetos de modelos do Visual Studio (SSDT)

Implementar um projeto de modelo tabular no Visual Studio para uma área de trabalho do Power BI Premium é praticamente o mesmo que implementar para um Analysis Services do Azure ou do SQL Server. As únicas diferenças estão na propriedade Servidor de Implementação especificada para o projeto e a forma como as credenciais de origem de dados são especificadas para que as operações de processamento possam importar dados de origens de dados para o novo conjunto de dados na área de trabalho.

> [!IMPORTANT]
> Durante a pré-visualização pública, as associações de funções não podem ser especificadas pelas ferramentas com o ponto final XMLA. Se o projeto de modelo não for implementado, confirme que não existem utilizadores especificados nas funções. Depois de o modelo ter sido implementado com sucesso, especifique os utilizadores para as funções de conjunto de dados no serviço Power BI. Para obter mais informações, veja [Funções de modelo](#model-roles) mais acima neste artigo.

Para implementar um projeto de modelo tabular criado no Visual Studio, tem primeiro de definir o URL de ligação da área de trabalho na propriedade **Servidor de Implementação** do projeto. No Visual Studio, em **Explorador de Soluções**, clique com o botão direito do rato no projeto > **Propriedades**. Na propriedade **Servidor**, cole o URL da ligação da área de trabalho.

![Propriedade de implementação](media/service-premium-connect-tools/xmla-endpoint-ssdt-deploy-property.png)

Quando a propriedade Servidor de Implementação tiver sido especificada, o projeto poderá ser implementado.

**Quando implementado pela primeira vez**, é criado um conjunto de dados na área de trabalho com metadados do model.bim. Como parte da operação de implementação, após a criação do conjunto de dados na área de trabalho a partir dos metadados de modelo, o processamento para carregar os dados para o conjunto de dados a partir de origens de dados falhará.

O processamento falha porque, ao contrário da implementação numa instância do Analysis Server do Azure ou do SQL Server, onde as credenciais de origem de dados são solicitadas como parte da operação de implementação, quando é realizada a implementação numa área de trabalho Premium, as credenciais da origem de dados não podem ser especificadas como parte da operação de implementação. Em vez disso, após a implementação de metadados ter sido bem sucedida e o conjunto de dados ter sido criado, as credenciais da origem de dados são especificadas no Serviço Power BI nas definições dos conjuntos de dados. Na área de trabalho, clique em **Conjuntos de dados** > **Definições** > **Credenciais da origem de dados** > **Editar credenciais**.

![Credenciais da origem de dados](media/service-premium-connect-tools/xmla-endpoint-datasource-credentials.png)

Quando as credenciais da origem de dados forem especificadas, poderá atualizar o conjunto de dados no serviço Power BI, configurar o agendamento de atualizações ou processar (atualizar) a partir do SQL Server Management Studio para carregar dados para o conjunto de dados.

Observa-se a implementação da propriedade **Opção de Processamento** especificada no projeto do Visual Studio. No entanto, se uma origem de dados ainda não tiver credenciais especificadas no serviço Power BI, mesmo que a implementação de metadados seja bem sucedida, o processamento falhará. Pode configurar a propriedade para **Não Processar**, o que impedirá uma tentativa de processamento como parte da implementação, mas aconselhamos a que defina a propriedade novamente como **Padrão**, pois uma vez especificadas as credenciais da origem de dados nas definições da origem de dados para o novo conjunto de dados, o processamento como parte das operações de implementação subsequentes terá êxito.

## <a name="connect-with-ssms"></a>Ligar com o SSMS

Utilizar o SSMS para se ligar a uma área de trabalho é semelhante a ligar-se a um servidor do Analysis Services do Azure ou do SQL Server. A única diferença é que especifica o URL da área de trabalho no nome do servidor e tem de utilizar a autenticação **Active Directory – Universal com MFA**.

### <a name="connect-to-a-workspace-by-using-ssms"></a>Ligar-se a uma área de trabalho com o SSMS

1. No SQL Server Management Studio, clique em **Ligar** > **Ligar ao Servidor**.

2. Em **Tipo de Servidor**, selecione **Analysis Services**. Em **Nome do servidor**, introduza o URL da área de trabalho. Em **Autenticação**, selecione **Active Directory – Universal com MFA** e, em seguida, em **Nome de utilizador**, introduza o ID do utilizador organizacional.

    ![Ligar-se a um servidor no SSMS](media/service-premium-connect-tools/xmla-endpoint-connect-server.png)

Uma vez estabelecida a ligação, a área de trabalho será apresentada como um servidor do Analysis Services e os conjuntos de dados na área de trabalho serão apresentados como bases de dados.  

![SSMS](media/service-premium-connect-tools/xmla-endpoint-ssms.png)

Para saber mais sobre a utilização do SSMS para executar scripts para metadados, veja [Create Analysis Services scripts](https://docs.microsoft.com/analysis-services/instances/create-analysis-services-scripts-in-management-studio?view=power-bi-premium-current) (Criar scripts do Analysis Services) e [Tabular Model Scripting Language (TMSL)](https://docs.microsoft.com/analysis-services/tmsl/tabular-model-scripting-language-tmsl-reference?view=power-bi-premium-current) (Linguagem TMSL).

## <a name="dataset-refresh"></a>Atualização do conjunto de dados

O ponto final XMLA permite um vasto leque de cenários para capacidades de atualização detalhada através do SSMS, automatização com o PowerShell, [Automatização do Azure](https://docs.microsoft.com/azure/automation/automation-intro) e [Funções do Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview) com o modelo TOM. Pode, por exemplo, atualizar certas partições históricas de [atualização incremental](service-premium-incremental-refresh.md) sem ter de recarregar todos os dados históricos.

Ao contrário da configuração de atualização no serviço Power BI, as operações de atualização através do ponto final XMLA não se limitam a 48 atualizações por dia e o [horário de atualização programado](refresh-troubleshooting-refresh-scenarios.md#scheduled-refresh-timeout) não é imposto.

## <a name="dynamic-management-views-dmv"></a>Vistas de Gestão Dinâmica (DMV)

As [DMVs](https://docs.microsoft.com/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) do Analysis Services proporcionam a visibilidade dos metadados, linhagem e utilização de recursos dos conjuntos de dados. As DMVs disponíveis para consulta no Power BI através do ponto final XMLA estão limitadas, no máximo, às que requerem permissões de administração de base de dados. Algumas DMVs, por exemplo, não estão acessíveis porque requerem permissões de administrador de servidor do Analysis Services.

## <a name="power-bi-desktop-authored-datasets"></a>Conjuntos de dados criados no Power BI Desktop

### <a name="enhanced-metadata"></a>Metadados melhorados

As operações de escrita XMLA nos conjuntos de dados criados no Power BI Desktop e publicados numa área de trabalho Premium requerem a ativação da opção de metadados melhorados. Para obter mais informações, veja [Metadados de conjuntos de dados otimizados](desktop-enhanced-dataset-metadata.md).

> [!CAUTION]
> De momento, a operação de escrita num conjunto de dados criado no Power BI Desktop impedirá que sejam transferidos como um ficheiro PBIX. Confirme que mantém o ficheiro PBIX original.

### <a name="data-source-declaration"></a>Declaração de origem de dados

Ao ligar-se a origens de dados e dados de consulta, o Power BI Desktop utiliza expressões do Power Query M como declarações de origem de dados inline. Embora suportado em áreas de trabalho do Power BI Premium, a declaração de origem de dados inline do Power Query M não é suportada pelo Azure Analysis Services nem pelo SQL Server Analysis Services. Em vez disso, as ferramentas de modelação de dados do Analysis Services como o Visual Studio criam metadados através de declarações de origem de dados *estruturadas* e/ou de *fornecedor*. Com o ponto final XMLA, o Power BI Premium também suporta origens de dados estruturadas e de fornecedor, mas não como parte das declarações de origem de dados inline do Power Query M nos modelos do Power BI Desktop. Para obter mais informações, veja [Compreender os fornecedores](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource#understanding-providers).

### <a name="power-bi-desktop-in-live-connect-mode"></a>Power BI Desktop no modo de ligação em direto

O Power BI Desktop pode ligar-se a um conjunto de dados Power BI Premium com uma ligação em direto. Ao utilizar uma ligação em direto, os dados não têm de ser replicados localmente, o que torna mais fácil para os utilizadores consumir modelos semânticos. Existem duas formas de os utilizadores se ligarem:

Ao selecionar **Conjuntos de dados do Power BI** e, em seguida, selecionar um conjunto de dados para criar um relatório. Esta é a forma **recomendada** de os utilizadores se ligarem em direto aos conjuntos. Este método constitui uma experiência de descoberta otimizada, que mostra o nível de recomendação dos conjuntos de dados. Os utilizadores não têm de localizar e acompanhar os URLs de áreas de trabalho. Para encontrar um conjunto de dados, os utilizadores precisam apenas de escrever o nome do conjunto de dados ou percorrer para localizar o conjunto de dados que procuram.

![Ligar em direto ao conjunto de dados](media/service-premium-connect-tools/dataset-live-connect.png)

A outra forma de os utilizadores se ligarem é através da opção **Obter Dados** > **Analysis Services**. Especifique uma área de trabalho Power BI Premium como URL, selecione **Ligar em direto** e, no Navegador, selecione um conjunto de dados. Neste caso, o Power BI Desktop utiliza o ponto final XMLA para ligar em direto ao conjunto de dados como se fosse um modelo de dados do Analysis Services. 

![Ligar em direto ao conjunto de dados do Analysis Services](media/service-premium-connect-tools/as-live-connect.png)

As organizações com relatórios existentes ligados em direto aos modelos de dados do Analysis Services com intenção de os migrarem para os conjuntos de dados do Power BI Premium precisam apenas de alterar o URL do nome de servidor em **Transformar dados** > **Definições de origens de dados**.

> [!NOTE]
> Durante a pré-visualização pública de leitura/escrita do XMLA, ao utilizar o Power BI Desktop para ligar a um conjunto de dados Power BI Premium com **Obter Dados** > **Analysis Services** e selecionar a opção **Ligar em direto**, publicar um relatório no serviço Power BI ainda não é suportado.

## <a name="audit-logs"></a>Registos de auditoria

Quando as aplicações se ligam a uma área de trabalho, o acesso através de pontos finais XMLA é registado nos registos de auditoria do Power BI com as seguintes operações:

|Nome amigável da operação   |Nome da operação   |
|---------|---------|
|Ligado ao conjunto de dados do Power BI a partir de uma aplicação externa      |  ConnectFromExternalApplication        |
|Atualização do conjunto de dados do Power BI pedida a partir de uma aplicação externa      | RefreshDatasetFromExternalApplication        |
|Conjunto de dados do Power BI criado a partir de uma aplicação externa      |  CreateDatasetFromExternalApplication        |
|Conjunto de dados do Power BI editado a partir de uma aplicação externa     |  EditDatasetFromExternalApplication        |
|Conjunto de dados do Power BI eliminado a partir de uma aplicação externa      |  DeleteDatasetFromExternalApplication        |

Para obter mais informações, veja  [Auditoria do Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Veja também

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
