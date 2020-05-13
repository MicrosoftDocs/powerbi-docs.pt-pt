---
title: Novidades no Power BI Report Server
description: Saiba mais sobre as novidades no Power BI Report Server. Este artigo abrange áreas de funcionalidades importantes e é atualizada à medida que são lançados novos itens.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/27/2020
ms.openlocfilehash: 3ce1ae5207af6f4aaf844679bcd3ae52d2c13819
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348166"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novidades no Power BI Report Server

Conheça as novidades do Power BI Report Server e do Power BI Desktop otimizado para o Power BI Report Server. Este artigo abrange áreas de funcionalidades importantes e é atualizado sempre que são lançadas novas versões.

Transfira o [Power BI Report Server e o Power BI Desktop otimizado para o Power BI Report Server](https://powerbi.microsoft.com/report-server/).

Para obter informações sobre “Novidades” do Power BI relacionadas, veja:

* [Novidades do serviço Power BI](../fundamentals/service-whats-new.md)
* [Novidades do Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Novidades em aplicativos móveis para o Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2020"></a>Janeiro de 2020

Veja a publicação de blogue de janeiro de 2020 do Power BI Report Server para obter mais detalhes.

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop otimizado para o Power BI Report Server

Este lançamento inclui muitas funcionalidades novas, como a formatação condicional para botões, as melhorias na criação de perfis de dados e mais definições de formatação para KPIs e elementos visuais da tabela. Veja a seguir uma lista resumida das atualizações:

**Relatórios**

- Definir um valor de matriz ou coluna de tabela como um URL personalizado
- Definições de formatação dos elementos visuais do KPI
- Atualizações da experiência do painel de filtro

**Análise**

- Formatação condicional dos botões
- Carregar mais para Analisar informações
- Nova função DAX: Trimestre

**Preparação de dados**

- Melhorias na criação de perfis de dados

**Outros**

- Novo formato de ficheiro: .pbids
- Melhorias no desempenho das operações de modelagem

**Relatórios**

*Definir um valor de matriz ou coluna de tabela como um URL personalizado*

Pode definir um valor de matriz ou coluna de tabela como um URL personalizado. Pode encontrar esta nova opção no cartão de formatação condicional do painel de formatação.

*Definições de formatação dos elementos visuais do KPI*

Com o lançamento deste mês, os KPIs apresentam novas opções de formatação:

- Formatação do texto do indicador (família de tipos de letra, cor e alinhamento)
- Transparência do eixo de tendência
- Formatação do texto de objetivo e distância (texto da etiqueta, família de tipos de letra, cor e tamanho)
- Formatação do texto de distância (texto da etiqueta, sentido positivo, família de tipos de letra, cor e tamanho)
- Adição de uma etiqueta de data com formatação (família de tipos de letra, cor e tamanho)

Pode formatar condicionalmente algumas destas novas opções de formatação:

- Cor do tipo de letra do Indicador
- Cor do tipo de letra do Objetivo e cor do tipo de letra da Distância do Objetivo
- Cores dos estados bom/mau/neutro
- Cor do tipo de letra da Data

*Atualizações da experiência do painel de filtro*

Como parte da disponibilidade geral da nova experiência de filtro no [último lançamento](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane), agilizámos o processo de transição dos relatórios atuais para o novo painel. Quando abre o Power BI Report Server pela primeira vez, verá uma caixa de diálogo de atualização automática do painel de filtro. Estas atualizações incluem também faixas no Report Server quando os relatórios precisam de ser migrados para a nova experiência.

**Análise**

*Formatação condicional para botões*

Estas atualizações da formatação condicional estão todas relacionadas com os botões. Agora, pode definir dinamicamente a formatação das seguintes propriedades:

- Cor do tipo de letra do texto do botão
- Texto do botão
- Cor da linha do ícone
- Cor do contorno
- Cor de Preenchimento
- Descrição do botão (no cartão de ação)

*Carregar mais para Analisar informações*

Ao executar a funcionalidade Analisar para encontrar informações nos seus dados, como Explicar o aumento, só executamos os modelos de aprendizagem automática durante um período de tempo definido para lhe mostrar as informações de forma atempada. Se existirem muitos dados para análise, poderá agora escolher continuar a executar a análise após o tempo limite inicial.

*Nova função DAX: Trimestre*

Este mês, temos uma nova função DAX: Trimestre. A função Trimestre devolve o trimestre correspondente a uma data especificada.

**Preparação de dados**

*Melhorias na criação de perfis de dados*

Este mês, vamos introduzir algumas melhorias significativas às nossas capacidades de Criação de Perfis de Dados no Editor do Power Query, incluindo:

- Várias Opções de agrupamento para o elemento visual de distribuição de valor do painel Perfil da Coluna, específico ao tipo de coluna, para além dos critérios “Por Valor” existentes.
- Texto: Por Comprimento de Texto (número de caracteres).
- Número: Por Sinal (positivo/negativo) e por Paridade (par/ímpar).
- Data/DateTime: Por Ano, Mês, Dia, Semana do Ano, Dia da Semana, Hora AM/PM, e Hora num dia.
- E muito mais para outros tipos de dados, por exemplo, o valor Lógico Verdadeiro/Falso.

*Opções de filtragem*

Já conseguia anteriormente utilizar diversos critérios de agrupamento específicos do tipo no painel de distribuição Perfis de Coluna. Agora, também pode filtrar a partir das notas de aviso de cada um dos valores na tabela de distribuição quando os critérios de agrupamento são aplicados. Por exemplo, no painel Perfis de Dados de uma coluna Data/DateTime, pode excluir todos os valores de um determinado Mês.

**Outros**

*Novo formato de ficheiro: .pbids*

Este mês, estamos a lançar um novo formato de ficheiro (.pbids), para simplificar a experiência de “Obter Dados” dos criadores de relatórios na sua organização. Recomendamos que os administradores criem estes ficheiros para ligações frequentemente utilizadas.

Quando um criador de relatório abre um ficheiro .pbids, o Power BI Desktop pede a autenticação para se ligar à origem de dados especificada no ficheiro. Em seguida, o utilizador seleciona as tabelas a carregar no modelo. Poderá também ser necessário selecionar a base de dados se uma não tiver sido especificada no ficheiro. A partir daí, o criador do relatório pode começar a criar visualizações.

Encontre detalhes e exemplos na secção [Utilizar ficheiros .pbids para obter dados](../connect-data/desktop-data-sources.md#using-pbids-files-to-get-data) do artigo “Origem de dados no Power BI Desktop”.

*Melhorias no desempenho das operações de modelagem*

Fizemos uma melhoria no desempenho do motor dos Analysis Services para acelerar as operações de modelação, como adicionar medidas ou colunas calculadas e criar relações. As melhorias que vê dependerão do modelo, mas vimos uma melhoria no desempenho 20 vezes superior em alguns clientes em ações como abrir um ficheiro e adicionar uma medida.

E é tudo para o lançamento de janeiro de 2020 do Power BI Report Server. Continue a enviar os seus comentários e não se esqueça de [votar nas funcionalidades que gostaria de ver no Power BI](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Power BI Report Server

#### <a name="export-to-excel-from-power-bi-reports"></a>Exportar para o Excel a partir dos relatórios do Power BI

Exportar para o Excel a partir de um relatório do Power BI no Power BI Report Server agora funciona da mesma forma que exportar para o Excel a partir de um relatório do Power BI no serviço Power BI. Pode exportar diretamente para o formato .xlsx do Excel. O limite de exportação é de 150 mil linhas.

#### <a name="azure-sql-managed-instance-support"></a>Suporte de Instância Gerida do SQL do Azure

Agora, pode alojar um catálogo da base de dados utilizado para o Power BI Report Server numa Instância Gerida (MI) do SQL do Azure, alojada numa VM ou no datacenter. O suporte está limitado à utilização das credenciais da base de dados para a ligação à MI do SQL.

#### <a name="power-bi-premium-dataset-support"></a>Suporte dos conjuntos de dados do Power BI Premium

Pode ligar-se aos conjuntos de dados do Power BI com o Microsoft Report Builder ou os SQL Server Data Tools (SSDT). Em seguida, pode publicar esses relatórios no Power BI Report Server com a conectividade do SQL Server Analysis Services. Os utilizadores terão de utilizar um nome de utilizador e uma palavra-passe do Windows armazenados para ativar o cenário.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>Suporte do AltText (texto alternativo) para os elementos de relatório

Ao criar relatórios, pode utilizar descrições para especificar texto para cada elemento no relatório. As tecnologias do leitor de ecrã utilizarão estas descrições.

#### <a name="azure-active-directory-application-proxy-support"></a>Suporte do Proxy de Aplicações do Azure Active Directory

Com o Proxy de Aplicações do Azure Active Directory, já não precisa de gerir o seu próprio proxy de aplicações Web para permitir o acesso seguro através da Web ou de aplicações móveis. Veja [Acesso remoto às aplicações no local através do Proxy de Aplicações do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) para obter mais informações.

#### <a name="custom-headers"></a>Cabeçalhos personalizados

Define os valores dos cabeçalhos de todos os URLs que correspondem ao padrão regex especificado. Os utilizadores podem atualizar o valor dos cabeçalhos personalizados com XML válido para definir os valores dos cabeçalhos dos URLs de pedido selecionados. Os administradores podem adicionar qualquer número de cabeçalhos ao XML. Veja [CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders) no artigo **Server Properties Advanced Page** (Página Avançada das Propriedades do Servidor) do Reporting Services para obter mais detalhes.

#### <a name="transparent-database-encryption"></a>Encriptação de Base de Dados Transparente

O Power BI Report Server agora suporta a Encriptação de Base de Dados Transparente da base de dados do catálogo do Power BI Report Server para as edições Enterprise e Standard.

#### <a name="power-bi-visuals-api"></a>API de elementos visuais do Power BI

A versão da API enviada com este lançamento é a 2.6.

#### <a name="microsoft-report-builder-update"></a>Atualização do Microsoft Report Builder

A versão recém-lançada do Report Builder é totalmente compatível com as versões de 2016, 2017 e 2019 do Reporting Services. É também compatível com as versões lançadas e suportadas do Power BI Report Server.

## <a name="september-2019"></a>Setembro de 2019

Veja a mensagem de blogue de [setembro de 2019 do Power BI Report Server](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/) para obter detalhes sobre todas as novas funcionalidades.

A atualização de setembro de 2019 do Power BI Report Server inclui imensas funcionalidades de relatórios do Power BI. Eis alguns dos destaques:

- **Filtros de nível visual para segmentações de dados:** pode adicionar um filtro de nível visual a segmentações de dados. Funcionam da mesma forma que qualquer outro filtro de nível visual, ao filtrar apenas a segmentação de dados e mais nenhum elemento visual. Este filtro é útil para filtrar elementos em branco ou caso queira utilizar filtros de medidas.
- **Conjuntos de ícones para tabelas e matrizes:** com os ícones do KPI, pode configurar regras para mostrar diferentes conjuntos de ícones na sua tabela ou matriz, da mesma forma que os conjuntos de ícones funcionam no Excel.
- **Agrupar elementos visuais:** agora pode agrupar elementos visuais, formas, caixas de texto, imagens e botões numa página de relatório da mesma forma que o faz no PowerPoint. Ao agrupar diferentes objetos, pode mover e redimensioná-los todos em conjunto. Com o agrupamento é mais fácil trabalhar num relatório que tenha vários objetos sobrepostos em cada página.
- **Novos temas predefinidos:** para além das novas opções JSON de temas, atualizámos os temas disponíveis para os relatórios existentes e alterámos o tema predefinido para novos relatórios. O novo tema predefinido ajusta-se melhor ao design da Microsoft e segue as melhores práticas de design de elementos visuais. 
- **Design atualizado dos painéis:** atualizámos uma grande parte da nossa interface. Atualizámos todos os painéis, o rodapé e o alternador de vistas com cores mais claras, espaçamento renovado e novos ícones. O novo design é o primeiro passo da atualização de toda a interface.

Eis a lista completa de funcionalidades. 

### <a name="reporting"></a>Relatórios

- Design atualizado dos painéis
- Filtros de nível visual para segmentações de dados
- Ordenação no painel de análise de desempenho
- Descrições do cabeçalho do elemento visual
- Personalização de etiquetas dos totais de tabelas e matrizes
- Suporte da segmentação de dados de sincronização para segmentações de dados de hierarquia
- Tamanhos de tipos de letra consistentes em todos os elementos visuais
- Conjuntos de ícones para tabelas e matrizes
- Percentagem de suporte para formatação condicional por regras
- O novo painel de filtro já está disponível para o público
- Suporte para cores de dados ao utilizar o eixo de reprodução em gráficos de dispersão
- Melhorias de desempenho na utilização de segmentações de dados de listas pendentes e datas relativas
- Agrupamento de elementos visuais
- Classes de cores e texto em temas
- Novos temas predefinidos

### <a name="analytics"></a>Análise

- Custom format strings (Cadeias de formato personalizado)
- Atualizações às opções de formatação condicional

    - Cores de título e fundo dos elementos visuais
    - Cores de cartões
    - Cores e preenchimento de medidores
    - Texto alternativo
    - Cor dos limites

- Avisos de formatação condicional
- Melhoria na capacidade de deteção da pormenorização
- Novas expressões DAX: REMOVEFILTERS e CONVERT
- Novo operador de comparação DAX: ==

### <a name="data-preparation"></a>Preparação de dados

- Melhorias ao M Intellisense
- Nova Transformação: dividir coluna por posições
- Copiar para a área de transferência a partir da criação de perfil


## <a name="may-2019"></a>Maio de 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop para Power BI Report Server

Veja a mensagem de blogue de [maio de 2019 do Power BI Report Server](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) para obter detalhes sobre todas as novas funcionalidades.

Eis alguns destaques do lançamento:

#### <a name="performance-analyzer"></a>Analisador de desempenho 

Se o desempenho do seu relatório for mais lento do que o esperado, experimente utilizar o Analisador de Desempenho no Power BI Desktop. Ao iniciá-lo, será criado um ficheiro de registo com informações sobre todas as ações efetuadas no relatório. Leia mais sobre o [Analisador de Desempenho](../create-reports/desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Nova vista de modelação

Na nova vista de modelação do Power BI Desktop, pode ver e trabalhar com conjuntos de dados complexos que contenham muitas tabelas. Os destaques incluem múltiplos esquemas de diagramas e a edição em volume de colunas, medidas e tabelas. Leia mais sobre a [Vista de Modelação](../transform-model/desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Interação visual acessível

Agora pode utilizar a navegação através do teclado para aceder a pontos de dados em muitos dos elementos visuais incorporados. Leia mais sobre a [acessibilidade em relatórios do Power BI](../desktop-accessibility.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Títulos de formatação condicional e ações de URLs Web

Os relatórios do Power BI são interativos. Portanto, faz sentido que os títulos de um relatório sejam dinâmicos, de modo a refletir o estado atual do relatório. Pode utilizar a mesma formatação baseada numa expressão para tornar dinâmicos os URLs dos botões, formas e imagens. Leia mais sobre os [títulos baseados em expressões](../create-reports/desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Realce cruzado por etiquetas de eixos

Selecione as etiquetas de categoria de eixo num elemento visual para efetuar o realce cruzado dos outros elementos de uma página, tal como faria a seleção de pontos de dados num elemento visual. Leia mais sobre o [realce cruzado](../create-reports/power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

#### <a name="all-the-new-features"></a>Todas as novas funcionalidades

Eis uma lista de todas as novas funcionalidades:

#### <a name="reporting"></a>Relatórios

- Realce cruzado num único ponto em gráficos de linhas 
- Moldagem do texto em títulos 
- Atualização da interação visual predefinida para a filtragem cruzada
- Cantos arredondados para os limites visuais 
- Segmentação de dados de seleção única  
- Suporte de mapa térmico para mapas Bing  
- Realce cruzado por etiquetas de eixos  
- Formatação de descrições predefinida  
- Suporte de URLs Web estáticos para botões, formas e imagens  
- Opções de alinhamento da página   
- Melhorias ao painel de seleção  
- Interação visual acessível  
- Formatação condicional para títulos de elementos visuais  
- Formatação condicional de ações de URLs Web para botões, formas e imagens
- Painel do Analisador de Desempenho
- Navegação através do teclado em tabelas e matrizes
- Controlo da posição de etiquetas de dados em linhas
- Controlo de tamanho de texto do indicador de elemento visual do KPI

#### <a name="analytics"></a>Análise

- A funcionalidade de mostrar datas como uma hierarquia está agora disponível para o público  

#### <a name="modeling"></a>Modelação

- A nova vista de modelação está agora disponível para o público
- Novas funções do DAX
- Atualização para a função DAX ALLSELECTED
- Desativação das tabelas de data automática nos novos relatórios

### <a name="power-bi-report-server"></a>Power BI Report Server

#### <a name="support-for-trusted-visuals"></a>Suporte para elementos visuais de confiança

Adicionámos suporte para Elementos Visuais de Confiança ao Power BI Report Server. Neste momento, suportamos elementos visuais do Mapbox e PowerOn. O ESRI, o Visio e o PowerApps não são suportados para este lançamento.

#### <a name="improved-security-features"></a>Funcionalidades de segurança melhoradas

A propriedade **RestrictedResourceMimeTypeForUpload**, que os administradores podem utilizar para especificar uma lista separada por vírgulas dos tipos de MIME banidos, por exemplo texto/html.

## <a name="january-2019"></a>Janeiro de 2019

Suporte para estas funcionalidades em relatórios do Power BI:

[**Segurança ao nível da linha**](row-level-security-report-server.md) – a configuração da segurança ao nível da linha (RLS) com o Power BI Report Server pode restringir o acesso a dados para determinados utilizadores. Os filtros restringem o acesso aos dados ao nível da linha e pode definir filtros nas funções.

[**Ações de expandir e fechar em cabeçalhos de linha de matriz**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) – adicionámos a capacidade de expandir e fechar cabeçalhos de linha individuais, uma das funcionalidades mais pedidas para elementos visuais.

[**Copiar e colar entre ficheiros .pbix**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) – pode copiar elementos visuais entre ficheiros .pbix a partir do menu de contexto do elemento visual ou através do atalho de teclado Ctrl+C e colá-lo noutro relatório com o atalho Ctrl+V.

[**Guias de alinhamento inteligentes**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) – verá guias de alinhamento inteligentes ao mover objetos na página do seu relatório, como vê no PowerPoint, para ajudar a alinhar todos os conteúdos na sua página. Verá guias inteligentes sempre que arrastar ou redimensionar conteúdos na página. Ao mover um objeto junto a outro objeto, o mesmo será alinhado com o outro objeto.

**Funcionalidades de acessibilidade** – temos demasiadas funcionalidades de acessibilidade para listar, por exemplo, o [suporte de acessibilidade do painel de lista de campos](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). O painel de lista de campos é totalmente acessível. Pode navegar no painel ao utilizar apenas o seu teclado e um leitor de ecrã juntamente com o menu de contexto para adicionar campos à página do seu relatório.

#### <a name="power-bi-visuals"></a>Elementos Visuais do Power BI

- A versão da API enviada com este lançamento é a 2.3.

### <a name="administrator-settings"></a>Definições de administrador

Os administradores podem definir as seguintes propriedades nas Propriedades Avançadas do SSMS para o farm do servidor:

**AllowedResourceExtensionsForUpload** – defina extensões de recursos que podem ser carregadas para o servidor de relatórios. Não é necessário incluir extensões para tipos de ficheiro incorporados, como &ast;.rdl e &ast;.pbix. As predefinições são: "&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx". 

**SupportedHyperlinkSchemes** – define uma lista separada por vírgulas dos esquemas URI com permissão para serem definidos em ações de Hiperligação com permissão para serem compostas ou "&ast;" para permitir todos os esquemas de hiperligação. Por exemplo, definir “http, https” permitiria hiperligações para “https://www. contoso.com", mas removeria hiperligações para "mailto:bill@contoso.com" ou "javascript:window.open(‘ www.contoso.com’, ‘_blank’)". A predefinição é "&ast;".

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

#### <a name="power-bi-visuals"></a>Elementos Visuais do Power BI

- A versão da API fornecida com este lançamento é a 1.13.0.

- Agora, os elementos visuais do Power BI podem ser revertidos para uma versão anterior compatível com a versão atual da API do servidor (caso esteja disponível).

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
- [Turn off tooltips for visuals](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips) (Desativar as descrições dos elementos visuais)
- [Slicer accessibility](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility) (Acessibilidade de segmentação de dados)
- [Formatting pane improvements](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane) (Melhorias do painel de formatação)
- [Stepped line support for line and combo charts](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine) (Suporte da linha de subtotal para gráficos de linhas e de combinação)
- [Sorting experience improvement](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting) (Melhoria da experiência de ordenação)
- [Print reports through Export to PDF (in Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print) (Imprimir relatórios através de Exportar para PDF no Power BI Desktop)
- [Create bookmark groups](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks) (Criar grupos de marcadores)
- [Slicer restatement](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer) (Reformulação da segmentação de dados)
- [Report page tooltips](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips) (Descrições de página do relatório)

### <a name="analytics"></a>Análise

- [Nova função DAX: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
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

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Formatação condicional baseada em regras para tabelas e matrizes](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Crie regras para colorir condicionalmente a cor do tipo de letra ou o fundo de uma coluna com base numa determinada lógica empresarial na sua tabela ou matriz.

#### <a name="show-and-hide-pages"></a>[Mostrar e ocultar páginas](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Pretende que os leitores tenham acesso ao seu relatório, mas algumas páginas não estão concluídas. Agora pode ocultá-las até que estejam prontas. Em alternativa, pode ocultar páginas da navegação normal e os leitores podem aceder às mesmas através de marcadores ou pormenorização.

#### <a name="bookmarking"></a>[Marcadores](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Pode criar marcadores para contar uma história com os dados do seu relatório.

- [Realce cruzado para marcadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): os marcadores mantêm e apresentam o estado de realce cruzado da página do relatório no momento da criação do marcador.
- [Maior flexibilidade de marcadores](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): os marcadores refletem as propriedades definidas no relatório e só são aplicados aos elementos visuais que selecionar.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Seleção múltipla de pontos de dados em vários gráficos](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selecione múltiplos pontos de dados em vários gráficos e aplique a filtragem cruzada a toda a página.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Segmentações de dados de sincronização em múltiplas páginas do seu relatório](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Pode aplicar uma segmentação de dados a uma ou mais páginas de um relatório.

#### <a name="quick-measures"></a>[Medidas rápidas](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Crie novas medidas com base em medidas existentes e colunas numéricas numa tabela.

#### <a name="drilling-down-filters-other-visuals"></a>[Desagregar filtra outros elementos visuais](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

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

Pode abrir e editar ficheiros de relatório do Power BI (.pbix) a partir do servidor, mas pode recuperar o ficheiro original que carregou. **Se tiverem sido atualizados pelo servidor, os dados não serão atualizados quando abrir o ficheiro pela primeira vez**. Precisa de atualizá-lo localmente, de forma manual, para ver a alteração.

### <a name="large-file-uploaddownload"></a>Carregar/transferir ficheiros grandes

Pode carregar ficheiros com um tamanho máximo de 2 GB mas, por predefinição, este limite é de 1 GB nas definições do Report Server no SQL Server Management Studio (SSMS).  Estes ficheiros são armazenados na base de dados, tal como são no caso do SharePoint, e não é necessária uma configuração especial para o catálogo do SQL Server.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Aceder a conjuntos de dados partilhados como feeds do OData

Pode aceder a conjuntos de dados partilhados a partir do Power BI Desktop com um feed do OData. Para obter mais informações, consulte [Aceder a conjuntos de dados partilhados como feeds do OData no Power BI Report Server](access-dataset-odata.md).

### <a name="scale-out"></a>Aumentar

Esta versão suporta o aumento. Utilize um balanceador de carga e defina a afinidade de servidor para uma experiência otimizada. O cenário ainda não está otimizado para escalamento horizontal, pelo que verá modelos potencialmente replicados em vários nós. O cenário funciona sem o Balanceador de Carga em Rede e sessões fixas. No entanto, não só verá uma utilização aumentada de memória nos nós à medida que o modelo é carregado N vezes como também verificará um abrandamento no desempenho entre as ligações, pois o modelo é transmitido à medida que atinge um novo nó entre pedidos.  

### <a name="administrator-settings"></a>Definições de administrador

Os administradores podem definir as seguintes propriedades nas Propriedades Avançadas do SSMS para o farm do servidor:

* EnableCustomVisuals: Verdadeiro/Falso
* EnablePowerBIReportEmbeddedModels: Verdadeiro/Falso
* EnablePowerBIReportExportData: Verdadeiro/Falso
* MaxFileSizeMb: a predefinição é agora 1000
* ModelCleanupCycleMinutes: frequência com que verifica modelos para expulsar da memória
* ModelExpirationMinutes: quantidade de tempo até o modelo expirar e ser expulso, com base na última vez em que foi utilizado
* ScheduleRefreshTimeoutMinutes: o intervalo de tempo que a atualização de dados pode demorar para um modelo. A predefinição é duas horas.  Não existe um limite superior fixo.

**Ficheiro de configuração rsreportserver.config**

```xml
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

Existe uma nova API separada para ficheiros grandes, que será atualizada na versão do Swagger do Power BI Report Server. 

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
  * suporte para elementos visuais do Power BI
  * Suporte apenas para **ligações em direto ao Analysis Services**, com mais origens de dados brevemente disponíveis.
  * Aplicação móvel Power BI Mobile atualizada para mostrar relatórios do Power BI armazenados no Power BI Report Server
* Colaboração melhorada em relatórios com comentários

## <a name="next-steps"></a>Próximos passos

Veja estas páginas para se manter a par das novas funcionalidades no Power BI Report Server.

* [Blogue do Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Canal do YouTube Guy in a Cube](https://aka.ms/guyinacube)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
