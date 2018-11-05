---
title: Novidades no Power BI Report Server
description: Saiba mais sobre as novidades no Power BI Report Server. Esta secção abrange áreas de funcionalidades importantes e é atualizada à medida que são lançados novos itens.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 08/16/2018
ms.openlocfilehash: a365cab0420fdf373d62f5b1774a4d86985adfe3
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50101261"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novidades no Power BI Report Server

Saiba mais sobre as novidades no Power BI Report Server. Este artigo abrange áreas de funcionalidades importantes e é atualizada à medida que são lançados novos itens.

Para transferir o Power BI Report Server e o Power BI Desktop otimizado para o Power BI Report Server, aceda a [Relatórios no local com o Power BI Report Server](https://powerbi.microsoft.com/report-server/).

Verifique também estas origens para se manter atualizado relativamente a novas funcionalidades no Power BI Report Server.

* [Blogue do Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blogue de Equipa do SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Canal do YouTube Guy in a Cube](https://aka.ms/guyinacube)

Para obter informações sobre “Novidades” do Power BI relacionadas, veja:

* [Novidades do serviço Power BI](../service-whats-new.md)
* [Novidades no Power BI Desktop](../desktop-latest-update.md)
* [Novidades em aplicativos móveis para o Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="august-2018"></a>Agosto de 2018

Agosto de 2018 é um mês de inúmeras novas funcionalidades adicionadas à versão do Power BI Desktop otimizada para o Power BI Report Server. Aqui estão elas, divididas por área:

- [Relatórios](#reporting)
- [Análise](#analytics)
- [Modelação](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Destaques do lançamento de agosto de 2018

Na longa lista de novas funcionalidades, as seguintes destacam-se por serem particularmente interessantes. Para obter mais informações, veja a nossa [mensagem de blogue](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/).

#### <a name="report-theming"></a>Personalização de relatórios

A personalização de relatórios foi adicionada ao lançamento de agosto de 2018 do Power BI Report Server. Esta funcionalidade permite-lhe colorir rapidamente todo o seu relatório para corresponder a um tema ou imagem corporativa. Ao importar um tema, todos os seus gráficos serão atualizados automaticamente para utilizarem as cores do tema e terá acesso às cores do tema na paleta de cores. Pode carregar um ficheiro de tema através da opção **Importar Tema** abaixo do botão **Mudar tema**.

Um ficheiro de tema é um ficheiro JSON que inclui todas as cores que pretende utilizar no seu relatório juntamente com a formatação predefinida que pretenda aplicar aos elementos visuais.
Eis um tema JSON de exemplo simples que apenas atualiza as cores predefinidas do relatório:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Formatação condicional por um campo diferente

A capacidade de formatar uma coluna por um campo diferente no seu modelo é uma das melhorias significativas à formatação condicional.

#### <a name="conditional-formatting-by-values"></a>Formatação condicional por valores

Outro novo tipo de formatação condicional é o valor **Formatar por campo**. O valor Formatar por campo permite-lhe utilizar uma medida ou coluna que especifique uma cor, através de um nome ou código hexadecimal, e aplicar essa cor ao tipo de letra ou fundo.

#### <a name="report-page-tooltips"></a>Descrições de página do relatório

A funcionalidade Descrições de página do relatório está incluída na atualização de agosto de 2018 do Power BI Report Server. Esta funcionalidade permite-lhe criar uma página de relatório para ser utilizada como descrição personalizada para outros elementos visuais no seu relatório.

#### <a name="log-axis-improvements"></a>Melhorias no eixo de registo

Melhorámos bastante o eixo de registo nos seus gráficos cartesianos. Agora deverá conseguir selecionar uma escala logarítmica para o eixo numérico de gráficos cartesianos, incluindo gráficos de combinação, caso tenha dados totalmente positivos ou totalmente negativos.

#### <a name="sap-hana-sso-direct-query"></a>DirectQuery SSO SAP HANA

Agora os Relatórios do Power BI suportam o DirectQuery SSO SAP HANA.

>[!Note]
>Este cenário só é suportado quando o SAP HANA é tratado como uma origem de dados relacional com relatórios criados no Power BI Desktop.  Para ativar esta funcionalidade no Power BI Desktop, no menu DirectQuery, em Opções, selecione a opção "Tratar o SAP HANA como uma origem relacional" e clique em OK.

#### <a name="custom-visuals"></a>Elementos Visuais Personalizados

- A versão da API fornecida com este lançamento é a 1.13.0.

- Agora os elementos visuais personalizados podem ser revertidos para uma versão anterior compatível com a versão atual da API do servidor (caso compatível).

### <a name="reporting"></a>Relatórios 

- [Report Theming](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming) (Personalização de relatórios)
- [Buttons to trigger actions](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons) (Botões para acionar ações)
- [Combo chart line styles](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines) (Estilos de linhas de gráficos de combinação)
- [Improved default sort for visuals](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort) (Ordenação predefinida melhorada para elementos visuais)
- [Numeric slicer](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer) (Segmentação de dados numérica)
- [Advanced slicer syncing](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync) (Sincronização avançada de segmentações de dados)
- [Log axis improvements](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis) (Melhorias no eixo de registo)
- [Data label options for funnel chart](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart) (Opções de etiquetas de dados para gráfico de funil)
- [Set line stroke width to zero](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke) (Definir a largura do traço para zero)
- [High contrast support for reports](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast) (Suporte de alto contraste para relatórios)
- [Donut radius control](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius) (Controlo do raio do anel)
- [Pie and donut detail labels position control](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels) (Controlo de posição das etiquetas de detalhe circulares e de anel)
- [Format data labels separately for each measure in a combo chart](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels) (Formatação de etiquetas de dados em separado para cada medida num gráfico de combinação)
- [New visual header with more flexibility and formatting](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader) (Novo cabeçalho de elemento visual com mais flexibilidade e formatação)
- [Wallpaper formatting](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper) (Formatação do padrão de fundo)
- [Tooltips for table & matrix](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips) (Descrições para tabelas e matrizes)
- [Turn tooltips off for visuals](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips) (Desativar descrições para elementos visuais)
- [Slicer accessibility](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility) (Acessibilidade de segmentação de dados)
- [Formatting pane improvements](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane) (Melhorias do painel de formatação)
- [Stepped line support for line and combo charts](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine) (Suporte da linha de subtotal para gráficos de linhas e de combinação)
- [Sorting experience improvement](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting) (Melhoria da experiência de ordenação)
- [Print reports through Export to PDF (in Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print) (Imprimir relatórios através de Exportar para PDF no Power BI Desktop)
- [Create bookmark groups](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks) (Criar grupos de marcadores)
- [Slicer restatement](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer) (Reformulação da segmentação de dados)
- [Report page tooltips](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips) (Descrições de página do relatório)

### <a name="analytics"></a>Análise

- [New DAX function: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues) [Nova função DAX: COMBINEVALUES()]
- [Measure drillthrough](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough) (Medir pormenorização)
- [Conditional formatting by a different field](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField) (Formatação condicional por um campo diferente)
- [Conditional formatting by values](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue) (Formatação condicional por valores)

### <a name="modeling"></a>Modelação

- [Filtering and sorting in data view](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort) (Filtrar e ordenar na vista de dados)
- [Improved locale formatting](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale) (Melhoria da formatação de regiões)
- [Data categories for measures](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory) (Categorias de dados para medidas)
- [Statistical DAX functions](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax) (Funções DAX de estatística)

## <a name="may-2018"></a>May 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Configurar remotamente as aplicações para iOS do Power BI para servidores de relatórios

Como administrador de TI, pode agora utilizar a ferramenta MDM da sua organização para configurar remotamente o acesso da aplicação móvel do Power BI para iOS a um servidor de relatórios. Veja [Configurar o acesso da aplicação móvel do Power BI para iOS a um servidor de relatórios remotamente](configure-powerbi-mobile-apps-remote.md) para obter detalhes.

## <a name="march-2018"></a>Março de 2018

Março de 2018 é um mês de inúmeras novas funcionalidades adicionadas à versão do Power BI Desktop otimizada para o Power BI Report Server. Aqui estão elas, divididas por área:

- [Elementos Visuais](#visuals-updates)
- [Relatórios](#reporting)
- [Análise](#analytics)
- [Desempenho](#performance)
- [Servidor de relatórios](#report-server)
- [Outros](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Destaques do lançamento de março de 2018

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

## <a name="october-2017"></a>Outubro de 2017

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
  * Suporte para elementos visuais personalizados
  * Suporte apenas para **ligações em direto ao Analysis Services**, com mais origens de dados brevemente disponíveis.
  * Aplicação móvel Power BI Mobile atualizada para mostrar relatórios do Power BI armazenados no Power BI Report Server
* Colaboração melhorada em relatórios com comentários

## <a name="next-steps"></a>Próximos passos

[O que é o Power BI Report Server?](get-started.md) 
[Manual do administrador](admin-handbook-overview.md)  
[Instalar o Power BI Report Server](install-report-server.md)  
[Transferir o Report Builder](https://www.microsoft.com/download/details.aspx?id=53613)  
[Transferir o SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)