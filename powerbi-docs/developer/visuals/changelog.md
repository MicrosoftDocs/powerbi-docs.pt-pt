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
ms.openlocfilehash: fa8759d7edb519240140263bcd01bfdddd9c7d86
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141057"
---
# <a name="power-bi-visuals-api-changelog"></a>Registo de alterações da API de elementos visuais do Power BI
Esta página contém um resumo rápido das versões da API. As versões aqui listadas são consideradas estáveis e não serão alteradas.

## <a name="api-v26"></a>API v2.6
  * Adiciona **isInFocus** à opção de atualização e o método **switchFocusModeState** ao sistema anfitrião do elemento visual
  * Suporta a personalização de **subtotais**

## <a name="api-v25"></a>API v2.5
  * Suporta o **[Painel de Análise](./analytics-pane.md)**
  * Suporta os métodos `SelectionIdBuilder` **withMatrixNode** e **withTable**
  * Já não suporta a interface `DataRepetitionSelector`, substituída pela interface `data.CustomVisualOpaqueIdentity`

## <a name="api-v23"></a>API v2.3
  * **[API da Página de Destino](./landing-page.md)**
  * **[API de Armazenamento Local](./local-storage.md)**
  * **[API de filtro da cadeia de identificação (filtro de várias colunas)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API de Eventos de Composição](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v22"></a>API v2.2
  * Suporta o **[restauro do Filtro JSON a partir de DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[API de ContextMenu](./context-menu.md)**

## <a name="api-v21"></a>API v2.1
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

## <a name="api-v113"></a>API v1.13
* Suporta a **[Segmentação de Dados de Sincronização](./enable-sync-slicers.md)** ; tenha em atenção que apenas funciona para segmentações de campos individuais devido ao estado do código atual do PBI. [Saiba mais](/power-bi/desktop-slicers).
* Acessibilidade: [suporte de alto contraste](./high-contrast-support.md) 
* Acessibilidade: permitir o sinalizador Foco de Teclado

## <a name="api-v112"></a>API v1.12
* Suporta Temas
* Suporta **[fetchMoreData](./fetch-more-data.md)** ; tenha em atenção que a **API Obter Mais Dados** excede o limite restritivo de 30 mil pontos de dados
* **[API de Descrições de Telas](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v111"></a>API v1.11
* **[API de FilterManager](./filter-api.md)**
* Suporta **[Marcadores](./bookmarks-support.md)** 

## <a name="api-v110"></a>API v1.10
* Adiciona `ILocalizationManager`
* **API de Autenticação**

## <a name="api-v19"></a>API v1.9
* **[API de launchUrl](./launch-url.md)**

## <a name="api-v18"></a>API v1.8
* Suporta o novo tipo de **fillRule** (gradiente) no esquema de capacidades
* Suporta a propriedade **regra** no esquema de capacidades das propriedades de objetos

## <a name="api-v17"></a>API v1.7
* Suporta **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Suporta o **[Modo de edição](./advanced-edit-mode.md)** dos elementos visuais para entrar no modo de edição dos elementos visuais
* Suporta **[Elementos visuais interativos (html) do Power BI baseados em R](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** , com base em html

## <a name="api-v150"></a>API v1.5.0
* Suporta **[Permitir interações](./visuals-interactions.md)** para a interatividade dos elementos visuais

## <a name="api-v140"></a>API v1.4.0
* Suporta **[Localização](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Suporta **[Descrições](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Adiciona **colorPalette** para gerir as cores utilizadas no elemento visual.
* Suporta **Seleção múltipla** – o selectionManager pode aceitar uma matriz de `SelectionId`.
* Suporta **[elementos visuais R](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** com scripts R

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