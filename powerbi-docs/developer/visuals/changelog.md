---
title: Registo de alterações da API de elementos visuais do Power BI
description: Este artigo descreve as principais alterações nas diferentes versões da API de elementos visuais do Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: c43542bc6c2bb0699403062f68024f9718bbbb60
ms.sourcegitcommit: 54e571a10b0fdde5cd6036017eac9ef228de5116
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501955"
---
# <a name="power-bi-visuals-api-changelog"></a>Registo de alterações da API de elementos visuais do Power BI
Esta página contém um resumo rápido das versões da API. As versões aqui listadas são consideradas estáveis e não serão alteradas.


## <a name="api-v340"></a>API v3.4.0
  * `fetchMoreData`: novo parâmetro `aggregateSegments` (predefinição true) para suportar fetchMoreData sem agregação

## <a name="api-v320"></a>API v3.2.0
  * Suporta **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)**

## <a name="api-v260"></a>API v2.6.0
  * Adiciona **isInFocus** à opção de atualização e o método **switchFocusModeState** ao sistema anfitrião do elemento visual
  * Suporta a personalização de **subtotais**

## <a name="api-v250"></a>API v2.5.0
  * Suporta o **[Painel de Análise](./analytics-pane.md)**
  * Suporta os métodos `SelectionIdBuilder` **withMatrixNode** e **withTable**
  * Já não suporta a interface `DataRepetitionSelector`, substituída pela interface `data.CustomVisualOpaqueIdentity`

## <a name="api-v230"></a>API v2.3.0
  * **[API da Página de Destino](./landing-page.md)**
  * **[API de Armazenamento Local](./local-storage.md)**
  * **[API de filtro da cadeia de identificação (filtro de várias colunas)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API de Eventos de Composição](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * Suporta o **[restauro do Filtro JSON a partir de DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[API de ContextMenu](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * Melhorias de desempenho:
    * Tempos de carregamento mais rápidos
    * Quantidade de memória menor
    * Transações de dados e eventos otimizadas  

**Notas de versão**
* As APIs de filtragem refatorizadas estarão disponíveis na API 2.2, mas não são suportadas na API 2.1.
* Os elementos visuais receberão apenas o tipo dataView que foi declarado nas capacidades. Os elementos visuais que utilizaram vários tipos dataView falharão devido a esta atualização.
* Já não suporta a interface `DataViewScopeIdentity`, substituída pela interface `data.DataRepetitionSelector`. Se utilizou a propriedade de chave da interface `DataViewScopeIdentity`, poderá substituí-la por `JSON.stringify(identity)`
* `undefined` é substituído por `null` em dataView. Quando itera através de uma matriz com `var item in myArray`, esta ignora `undefined`, mas não ignora `null`. Os elementos visuais que utilizam este padrão podem falhar com esta atualização. Confirme que procura `null` nas matrizes:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* A propriedade `proto` já não armazena metadados\dados ocultos em dataView. Os elementos visuais que acedem a propriedades através de `proto` podem falhar com esta atualização.

## <a name="api-v1130"></a>API v1.13.0
* Suporta a **[Segmentação de Dados de Sincronização](./enable-sync-slicers.md)** ; tenha em atenção que apenas funciona para segmentações de campos individuais devido ao estado do código atual do PBI. [Saiba mais](../../visuals/power-bi-visualization-slicers.md).
* Acessibilidade: [suporte de alto contraste](./high-contrast-support.md) 
* Acessibilidade: permitir o sinalizador Foco de Teclado

## <a name="api-v1120"></a>API v1.12.0
* Suporta Temas
* Suporta **[fetchMoreData](./fetch-more-data.md)** ; tenha em atenção que a **API Obter Mais Dados** excede o limite restritivo de 30 mil pontos de dados
* **[API de Descrições de Telas](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[API de FilterManager](./filter-api.md)**
* Suporta **[Marcadores](./bookmarks-support.md)** 

## <a name="api-v1100"></a>API v1.10.0
* Adiciona `ILocalizationManager`
* **API de Autenticação**

## <a name="api-v190"></a>API v1.9.0
* **[API de launchUrl](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* Suporta o novo tipo de **fillRule** (gradiente) no esquema de capacidades
* Suporta a propriedade **regra** no esquema de capacidades das propriedades de objetos

## <a name="api-v170"></a>API v1.7.0
* Suporta **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Suporta o **[Modo de edição](./advanced-edit-mode.md)** dos elementos visuais para entrar no modo de edição dos elementos visuais
* Suporta **[Elementos visuais interativos (html) do Power BI baseados em R](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** , com base em html

## <a name="api-v150"></a>API v1.5.0
* Suporta **[Permitir interações](./visuals-interactions.md)** para a interatividade dos elementos visuais

## <a name="api-v140"></a>API v1.4.0
* Suporta **[Localização](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Suporta **[Descrições](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Adiciona **colorPalette** para gerir as cores utilizadas no elemento visual.
* Suporta **Seleção múltipla** – o selectionManager pode aceitar uma matriz de `SelectionId`.
* Suporta **[elementos visuais R](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** com scripts R

## <a name="api-v110"></a>API v1.1.0
* Suporta a depuração de elementos visuais no iFrame
* Adiciona um sandbox simples com uma inicialização mais rápida do iFrame
* Corrige o problema [Capabilities.objects não suporta o tipo “texto”](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)
* Suporta `pbiviz update` para atualizar as definições e o esquema do tipo de API de elementos visuais
* Suporta o sinalizador `--api-version` em `pbiviz new` para criar elementos visuais com uma versão da API específica
* Suporta a versão alfa da API v1.2.0

**Sistema Anfitrião do Elemento Visual**
* Adiciona **createSelectionIdBuilder** para criar identificadores exclusivos utilizados para a seleção de dados
* Adiciona **createSelectionManager** para gerir o estado de seleção do elemento visual e comunica as alterações ao sistema anfitrião do elemento visual
* Adiciona uma variedade de **cores** predefinidas para utilizar nos elementos visuais

## <a name="api-v100"></a>API v1.0.0
* Lançamento da API inicial
