---
title: Novidades no Power BI Report Server
description: Saiba mais sobre as novidades no Power BI Report Server. Esta secção abrange áreas de funcionalidades importantes e é atualizada à medida que são lançados novos itens.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 04/19/2018
ms.author: maggies
ms.openlocfilehash: 391edc8a2187f9a4af43b93f0713d40e41f6e943
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34295428"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novidades no Power BI Report Server
Saiba mais sobre as novidades no Power BI Report Server. Esta secção abrange áreas de funcionalidades importantes e é atualizada à medida que são lançados novos itens.

Para transferir o Power BI Report Server e o Power BI Desktop otimizado para o Power BI Report Server, aceda a [Relatórios no local com o Power BI Report Server](https://powerbi.microsoft.com/report-server/).

Verifique também estas origens para se manter atualizado relativamente a novas funcionalidades no Power BI Report Server.

* [Blogue do Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blogue de Equipa do SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Canal do YouTube Guy in a Cube](https://aka.ms/guyinacube)

Para obter informações sobre “Novidades” do Power BI relacionadas, veja:

* [Novidades do serviço Power BI](../service-whats-new.md)
* [Novidades no Power BI Desktop](../desktop-latest-update.md)
* [Novidades em aplicativos móveis para o Power BI](../mobile-whats-new-in-the-mobile-apps.md)

## <a name="march-2018-release"></a>Lançamento de março de 2018

Março de 2018 é um mês de inúmeras novas funcionalidades adicionadas à versão do Power BI Desktop otimizada para o Power BI Report Server. Aqui estão elas, divididas por área: 
- [Elementos Visuais](#visuals-updates)
- [Relatórios](#reporting)
- [Análise](#analytics)
- [Desempenho](#performance)
- [Servidor de relatórios](#report-server)
- [Outros](#other-improvements)

### <a name="highlights-of-this-release"></a>Destaques desta versão

Na longa lista de novas funcionalidades, as seguintes destacam-se por serem particularmente interessantes.

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Formatação condicional baseada em regras para tabelas e matrizes](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)
 
Crie regras para colorir condicionalmente a cor do tipo de letra ou o fundo de uma coluna com base numa determinada lógica empresarial na sua tabela ou matriz.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Mostrar e ocultar páginas](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Pretende que os leitores tenham acesso ao seu relatório, mas algumas páginas não estão concluídas. Agora pode ocultá-las até que estejam prontas. Em alternativa, pode ocultar páginas da navegação normal e os leitores podem aceder às mesmas através de marcadores ou pormenorização.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Marcadores](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Pode criar marcadores para contar uma história com os dados do seu relatório.

- [Realce cruzado para marcadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): os marcadores mantêm e apresentam o estado de realce cruzado da página do relatório no momento da criação do marcador.
- [Maior flexibilidade de marcadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): os marcadores refletem as propriedades definidas no seu relatório e só são aplicados aos elementos visuais que selecionar.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Seleção múltipla de pontos de dados em vários gráficos](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selecione múltiplos pontos de dados em vários gráficos e aplique a filtragem cruzada a toda a página.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Segmentações de dados de sincronização em múltiplas páginas do seu relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Pode aplicar uma segmentação de dados a uma ou mais páginas de um relatório.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Medidas rápidas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Crie novas medidas com base em medidas existentes e colunas numéricas numa tabela.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[Desagregar filtra outros elementos visuais](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Ao desagregar numa determinada categoria de um elemento visual, pode fazer com que sejam filtrados todos os elementos visuais na página com a mesma categoria.

### <a name="visuals-updates"></a>Atualizações de elementos visuais

- [Alinhamento de células para tabelas e matrizes](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Unidades de apresentação e controlo de precisão para as colunas de tabelas e de matrizes](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Etiquetas de dados com capacidade excedida para gráficos de barras e colunas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Controlar a cor de fundo de etiquetas de dados para elementos visuais de mapas e cartesianos](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Controlar o preenchimento de barras/colunas](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Aumentar a área utilizada para etiquetas de eixos em gráficos](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Elemento visual de dispersão de agrupamentos de eixos X e Y](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Amostragem de alta densidade para mapas com base na latitude e longitude](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Segmentações de dados reativas](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Adicionar uma data de âncora para uma segmentação de dados relativa](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Relatórios

- [Desativar o cabeçalho visual no modo de leitura de um relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Opções de relatório para origens de dados lentas](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Colocação predefinida de elementos visuais melhorada](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Controlar a ordenação dos elementos visuais através do painel de seleção](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Bloquear objetos no seu relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Pesquisa nos painéis Formatação e Análise](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Painel de propriedades de campo e descrições de campo](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Análise

- [UTCNOW() e UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Definir tabelas de datas personalizadas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [A pormenorização filtra outros elementos visuais](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formatação ao nível de células para modelos AS multidimensionais para o cartão de linhas múltiplas](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)
 
### <a name="performance"></a>Desempenho

- [Melhorias de desempenho da filtragem](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Melhorias de desempenho no DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Melhorias de desempenho das ações Abrir e Guardar](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Melhorias da opção "Mostrar itens sem dados"](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)
 
### <a name="report-server"></a>Servidor de Relatórios 

#### <a name="export-to-accessible-pdf"></a>Exportar para PDF acessível

Ao exportar um relatório paginado (RDL) para PDF, agora pode obter um ficheiro PDF acessível/etiquetado. Este tipo de ficheiro ocupa mais espaço, mas facilita a leitura e navegação para leitores de ecrã e outras tecnologias de apoio. Pode ativar o formato PDF acessível ao definir a opção de informações do dispositivo **AccessiblePDF** para **Verdadeiro**. Veja [PDF Device Information Settings (Definições de Informações do Dispositivo PDF)](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) e [Changing Device Information Settings (Alterar as Definições de Informações do Dispositivo)](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).


### <a name="other-improvements"></a>Outras melhorias

- [Add Column From Examples improvements](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples) (Melhorias do painel Adicionar Coluna a Partir dos Exemplos)
- [Consulting Services quick link](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices) (Ligação rápida aos Serviços de Consultoria)
- [Improved error reporting](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors) (Relatórios de erros melhorados)
- [View previous errors you’ve encountered](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors) (Ver os erros anteriores com que se deparou)

 
## <a name="october-2017-release"></a>Versão de outubro de 2017
### <a name="power-bi-report-data-sources"></a>Origens de dados de relatórios do Power BI
Os relatórios do Power BI no Power BI Report Server podem ligar-se a diversas origens de dados. Pode importar dados e agendar atualizações de dados ou consultá-los diretamente através do DirectQuery ou de uma ligação em direto ao SQL Server Analysis Services. Consulte a lista de origens de dados que suportam atualizações agendadas e as que suportam o DirectQuery em "Origens de dados de relatórios do Power BI no Power BI Report Server".

### <a name="scheduled-data-refresh-for-imported-data"></a>Atualização de dados agendada para dados importados
No Power BI Report Server, pode configurar atualizações de dados agendadas para manter os dados atualizados em relatórios do Power BI com um modelo incorporado em vez de uma ligação em direto ou do DirectQuery. Importe os dados com um modelo incorporado, para que seja desassociado da origem de dados original. Este precisa de ser atualizado para manter os dados em dia, o que se consegue através da atualização agendada. Obtenha mais informações sobre a "atualização agendada para relatórios do Power BI no Power BI Report Server".

### <a name="editing-power-bi-reports-from-the-server"></a>Editar relatórios do Power BI a partir do servidor
Pode abrir e editar ficheiros de relatório do Power BI (.pbix) a partir do servidor, mas pode recuperar o ficheiro original que carregou.  Isto significa que, **se os dados tiverem sido atualizados pelo servidor, os dados não serão atualizados quando abrir o ficheiro pela primeira vez**. Precisa de atualizá-lo localmente, de forma manual, para ver a alteração.

### <a name="large-file-uploaddownload"></a>Carregar/transferir ficheiros grandes
Pode carregar ficheiros com um tamanho máximo de 2 GB mas, por predefinição, este limite é de 1 GB nas definições do Report Server no SQL Server Management Studio (SSMS).  Estes ficheiros são armazenados na base de dados, tal como são no caso do SharePoint, e não é necessária uma configuração especial para o catálogo do SQL Server.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Aceder a conjuntos de dados partilhados como feeds do OData
Pode aceder a conjuntos de dados partilhados a partir do Power BI Desktop com um feed do OData. Para obter mais informações, consulte [Aceder a conjuntos de dados partilhados como feeds do OData no Power BI Report Server](access-dataset-odata.md).

### <a name="scale-out"></a>Aumentar
Esta versão suporta o aumento. Utilize um balanceador de carga e defina a afinidade de servidor para uma experiência otimizada. Note que o cenário ainda não está otimizado para aumento, pelo que irá ver modelos potencialmente replicados em múltiplos nós. O cenário funciona sem o Balanceador de Carga em Rede e sessões fixas. No entanto, não só irá ver uma utilização aumentada de memória nos nós à medida que o modelo é carregado N vezes, mas também haverá um abrandamento de desempenho entre ligações, pois o modelo é transmitido à medida que atinge um novo nó entre pedidos.  

### <a name="administrator-settings"></a>Definições de administrador
Os administradores podem definir as seguintes propriedades nas Propriedades Avançadas do SSMS para o farm do servidor:

* EnableCustomVisuals: True/False
* EnablePowerBIReportEmbeddedModels: True/False
* EnablePowerBIReportExportData: True/False
* MaxFileSizeMb: Agora, a predefinição é 1000
* ModelCleanupCycleMinutes: Frequência com que verifica modelos para expulsar da memória
* ModelExpirationMinutes: Quantidade de tempo até o modelo expirar e ser expulso, com base na última vez em que foi utilizado
* ScheduleRefreshTimeoutMinutes: Quanto tempo a atualização de dados pode demorar para um modelo. Por predefinição, são duas horas.  Não existe um limite superior fixo.

**Ficheiro de configuração rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API para Programadores
A API para programadores (API REST) apresentada para o SSRS 2017 foi alargada para dar ao Power BI Report Server compatibilidade com ficheiros Excel e ficheiros .pbix. Um potencial caso de utilização é transferir ficheiros programaticamente do servidor, atualizá-los e, em seguida, voltar a publicá-los. Esta é a única forma de atualizar livros do Excel para modelos do PowerPivot, por exemplo.

Note que existe uma nova API separada para ficheiros grandes, que será atualizada na versão Power BI Report Server do Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) e o tamanho de memória do Power BI Report Server
Agora, o Power BI Report Server aloja o SQL Server Analysis Services (SSAS) internamente. Não é uma situação específica de uma atualização agendada. Alojar o SSAS pode expandir bastante o tamanho de memória do servidor de relatório. O ficheiro de configuração AS.ini está disponível nos nós de servidor, pelo que, se estiver familiarizado com o SSAS, poderá querer atualizar as definições, incluindo o limite máximo de memória e a colocação em cache do disco, etc. Consulte [Server properties in Analysis Services (Propriedades de servidor no Analysis Services - em inglês)](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) para obter detalhes.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Ver e interagir com livros do Excel
O Excel e o Power BI contêm um portefólio de ferramentas sem igual na indústria. Em conjunto, permitem que os analistas empresariais consigam mais facilmente recolher, moldar, analisar e explorar visualmente os dados. Além de ver relatórios do Power BI no portal Web, os utilizadores empresariais podem agora fazer o mesmo com livros do Excel no Power BI Report Server, dando-lhes um único local para publicarem e verem conteúdos self-service do Microsoft BI.

Publicámos uma [explicação passo a passo sobre como adicionar o Office Online Server (OOS) ao seu ambiente de pré-visualização do Power BI Report Server](excel-oos.md). Os clientes com uma conta de Licenciamento de Volume podem transferir o OOS do Centro de Serviço de Licenciamento de Volume gratuitamente, e terão funcionalidade só de visualização. Após a configuração, os utilizadores podem ver e interagir com os livros do Excel que:

* Não têm dependências de origens de dados externas
* Têm uma ligação em direto a uma origem de dados do SQL Server Analysis Services
* Têm um modelo de dados PowerPivot

### <a name="support-for-new-table-and-matrix-visuals"></a>Suporte para novos visuais de tabelas e matrizes
Agora, o Power BI Report Server suporta os novos visuais de tabelas e matrizes do Power BI. Para criar relatórios com estes visuais, precisará de uma versão do Power BI Desktop atualizada para a versão de outubro de 2017. Não pode ser instalada paralelamente com a versão do Power BI Desktop (junho de 2017). Para obter a versão mais recente do Power BI Desktop, na [página de transferência do Power BI Report Server](https://powerbi.microsoft.com/report-server/), selecione **Opções de transferência avançadas**.

## <a name="june-2017"></a>Junho de 2017
* O Power BI Report Server está agora normalmente disponível (GA).

## <a name="may-2017"></a>Maio de 2017
* Pré-visualização do Power BI Report Server disponibilizada
* Capacidade de publicar relatórios do Power BI no local
  * Suporte para visuais personalizados
  * Suporte apenas para ligações em direto ao Analysis Services, com mais origens de dados brevemente disponíveis.
  * Aplicação móvel Power BI Mobile atualizada para mostrar relatórios do Power BI armazenados no Power BI Report Server
* Colaboração melhorada em relatórios com comentários

## <a name="next-steps"></a>Próximos passos
[Manual do utilizador](user-handbook-overview.md)  
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Power BI Report Server](install-report-server.md)  
[Instalar o Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

