---
title: Melhores práticas para o desempenho do Power BI Embedded
description: Este artigo fornece recomendações de melhores práticas para a análise incorporada
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: ba0a85958fad500bd27f4697a7f46961ca430f49
ms.sourcegitcommit: 0b1e96de184caf2371adedcc3ee43bcb88048187
ms.contentlocale: pt-PT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85299578"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Melhores práticas para o desempenho do Power BI Embedded

Este artigo fornece recomendações para uma composição mais rápida de relatórios, dashboards e mosaicos na sua aplicação.

> [!Note]
> Lembre-se de que o tempo de carregamento depende principalmente dos elementos relevantes para o relatório e os próprios dados, incluindo elementos visuais, o tamanho dos dados e a complexidade das consultas e das medidas. Para obter mais informações, veja o [Guia de otimização do Power BI](../../guidance/power-bi-optimization.md).

## <a name="update-tools-and-sdk-packages"></a>Ferramentas de atualização e pacotes SDK

Mantenha as ferramentas e os pacotes SDK atualizados.

* Utilize sempre a versão mais recente do [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Instale a versão mais recente do [cliente SDK do Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Lançamos continuamente mais melhorias, por isso, volte de vez em quando.

## <a name="embed-parameters"></a>Parâmetros de incorporação

O método `powerbi.embed(element, config)` recebe um elemento e um parâmetro config. O parâmetro config inclui campos que apresentam implicações de desempenho.

### <a name="embed-url"></a>URL de Incorporação

Evite gerar o seu próprio URL de incorporação. Em vez disso, certifique-se de que obtém o URL de Incorporação ao chamar a API [Obter relatórios](/rest/api/power-bi/reports/getreportsingroup), [Obter dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup) ou [Obter mosaicos](/rest/api/power-bi/dashboards/gettilesingroup). Adicionámos um novo parâmetro ao URL, chamado **_config_**, que serve para melhorar o desempenho.

### <a name="permissions"></a>Permissões

Conceda permissões **Ver** se não tencionar incorporar um relatório no modo de edição. Desta forma, o código incorporado não inicializa os componentes, que são utilizados no modo de edição.

### <a name="filters-bookmarks-and-slicers"></a>Filtros, marcadores e segmentações

Normalmente, os elementos visuais de relatórios são guardados com dados em cache. Os dados em cache são utilizados para fornecer o desempenho percetível. Os relatórios compõem os dados em cache enquanto as consultas são executadas. Se forem fornecidos filtros, marcadores ou segmentações de dados, os dados em cache não são relevantes e os elementos visuais são compostos apenas após o fim da consulta visual.

Se incorporar relatórios com os mesmos filtros, marcadores e segmentações de dados, para melhorar seu desempenho, guarde o relatório com os filtros, marcadores e segmentações de dados já aplicados. Esta ação compõe o relatório com os dados em cache, o que inclui os filtros, os marcadores e as segmentações de dados.

## <a name="switching-between-reports"></a>Alternar entre relatórios

Quando incorporar vários relatórios no mesmo iframe, não gere um novo iframe para cada relatório. Em vez disso, utilize `powerbi.embed(element, config)` com uma configuração diferente para incorporar o novo relatório.

> [!NOTE]
> Alternar entre relatórios ao incorporar para os clientes (também conhecido como cenário “os dados pertencem à aplicação”) requer a utilização de um token de incorporação com permissões para todos os relatórios e conjuntos de dados. Para obter mais informações, veja [Gerar a API de tokens](https://docs.microsoft.com/rest/api/power-bi/embedtoken/generatetoken).

## <a name="query-caching"></a>Colocação de consultas em cache

As organizações com a capacidade Power BI Premium ou a capacidade Power BI Embedded podem tirar partido da colocação em cache de consultas para acelerar os relatórios associados a um conjunto de dados.

[Saiba mais sobre a colocação em cache de consultas no Power BI](../../connect-data/power-bi-query-caching.md).

## <a name="preload"></a>Preload

Utilize `powerbi.preload()` para melhorar o desempenho para o utilizador final. O método `powerbi.preload()` transfere ficheiros CSS, JavaScript e outros artefactos, que são utilizados posteriormente para incorporar um relatório.

Chame `powerbi.preload()` se não pretender incorporar o relatório de imediato. Por exemplo, se o conteúdo incorporado do Power BI não aparecer na home page, utilize `powerbi.preload()` para transferir e colocar em cache os artefactos utilizados para incorporar o conteúdo.

## <a name="bootstrapping-the-iframe"></a>Bootstrapping do iframe

> [!NOTE]
> A versão 2.9 do [SDK de cliente do Power BI](https://github.com/Microsoft/PowerBI-JavaScript) é obrigatória para efetuar o bootstrap do iframe.

`powerbi.bootstrap(element, config)` permite que comece a incorporar antes que todos os parâmetros necessários estejam disponíveis. A API de bootstrap prepara e inicializa o iframe.
Ao utilizar a API de bootstrap, continua a ser necessário chamar `powerbi.embed(element, config)` no mesmo elemento HTML.

Por exemplo, um dos casos de utilização desta funcionalidade consiste em executar em paralelo o bootstrap do iframe e as chamadas de back-end para a incorporação.
> [!TIP]
> Utilize a API de bootstrap quando for possível gerar o iframe antes que fique visível para o utilizador final.

[Saiba mais sobre o bootstraping do iframe](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Medição do desempenho

### <a name="performance-events"></a>Eventos de desempenho

Para medir o desempenho incorporado, pode usar dois eventos:

1. Evento carregado: o tempo até que o relatório seja inicializado (o logótipo do Power BI desaparecerá quando o carregamento estiver concluído).
2. Evento de composição: o tempo até o relatório ser completamente composto com os dados reais. O evento de composição é acionado sempre que o relatório é composto novamente (por exemplo, após aplicar filtros). Para medir um relatório, certifique-se de que faz os cálculos no primeiro evento gerado.

Os dados em cache são compostos quando disponíveis, mas nenhum evento adicional é gerado.

[Saiba mais sobre o processamento de eventos](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Analisador de Desempenho

Para examinar o desempenho dos elementos do relatório, pode usar o Analisador de Desempenho no Power BI Desktop.
O Analisador de Desempenho permitirá que veja e crie registos que medem o desempenho de cada um dos elementos do relatório.

[Saiba mais sobre o Analisador de Desempenho](../../create-reports/desktop-performance-analyzer.md).

> [!NOTE]
> Lembre-se sempre de comparar o desempenho do relatório incorporado com o desempenho em powerbi.com. Tal pode ajudá-lo a compreender a origem dos seus problemas de desempenho

## <a name="next-steps"></a>Próximos passos

* [Guia de otimização do Power BI](../../guidance/power-bi-optimization.md)
* [Como resolver problemas do Power BI Embedded](embedded-troubleshoot.md)
* [FAQ do Power BI Embedded](embedded-faq.md)
