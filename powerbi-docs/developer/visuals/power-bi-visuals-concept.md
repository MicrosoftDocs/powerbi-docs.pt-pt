---
title: Conceito de elemento visual do Power BI
description: O artigo descreve como o elemento visual se integra com o Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700852"
---
# <a name="power-bi-visual-concept"></a>Conceito de elemento visual do Power BI

O artigo explica como um utilizador e um elemento visual interagem com o Power BI e como um utilizador interage com o elemento visual do Power BI. No diagrama, vê que ações influenciam diretamente o elemento visual ou através do Power BI (por exemplo, o utilizador seleciona marcadores).

![Elemento visual do Power BI](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>O elemento visual obtém a atualização do Power BI

O elemento visual tem o método `update` e este método contém normalmente a lógica principal do elemento visual e é responsável pela composição do gráfico ou visualização dos dados.

Mais atualizações são implementadas com o método `update`.

### <a name="user-interacts-with-visual-through-power-bi"></a>O utilizador interage com o elemento visual através do Power BI

* O utilizador abre o painel de propriedades do elemento visual.

    O Power BI obtém os objetos e propriedades suportados do elemento visual `capabilities.json` e, para receber os valores reais das propriedades, o Power BI chama o `enumerateObjectInstances` método do elemento visual.

    O elemento visual tem de devolver valores reais de propriedades.

    Para obter mais informações, [leia sobre os recursos visuais](capabilities.md).

* [O utilizador altera a propriedade do elemento visual](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) no painel de formatação.

    Após alterar o valor de uma propriedade, o Power BI chama o método `update` do elemento visual e passa para o método de atualização o novo `options` com novos valores dos objetos.

    Para obter mais informações, [leia sobre os objetos e propriedades do elemento visual](objects-properties.md).

* O utilizador redimensiona o elemento visual.

    Quando um utilizador altera o tamanho do elemento visual, o Power BI chama o método `update` com o novo objeto `option`. As opções aninharam o objeto `viewport` com a nova largura e altura do elemento visual.

* O utilizador aplica o filtro de relatório, página ou nível de elemento visual.

    O Power BI filtra os dados de acordo com as condições do filtro e chama o método `update` do elemento visual para fornecer novos dados ao elemento visual.

    O elemento visual obtém a nova atualização de `options` com novos dados num dos objetos aninhados. Depende da configuração do mapeamento de vista de dados do elemento visual.

    Para obter mais informações, [leia sobre os mapeamentos de vista de dados](dataview-mappings.md).

* O utilizador seleciona o ponto de dados noutro elemento visual do relatório.

    O Power BI filtra ou destaca os pontos de dados selecionados e chama o método `update` do elemento visual.

    O elemento visual recebe novos dados filtrados ou os mesmos dados com a matriz de destaques.

    Para obter mais informações, [leia sobre como destacar dados em elementos visuais](highlight.md).

* O utilizador seleciona o marcador no painel marcadores do relatório.

    Podem ocorrer duas ações:

    1. O Power BI chama a função transmitida registada pelo método `registerOnSelectionCallback` e a função de retorno obtém matrizes de seleções para o marcador correspondente.

    2. O Power BI chama o método `update` com o objeto de filtro correspondente dentro de `options`.

    Em ambos os casos, o elemento visual tem de mudar o estado de visualização de acordo com as seleções recebidas ou o objeto de filtro.

    Para obter mais informações sobre marcadores, [leia como ligar com marcadores](filter-api.md).

    Para obter mais informações sobre filtros, [leia sobre como os elementos visuais do Power BI conseguem filtrar dados noutros elementos visuais](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>O utilizador interage diretamente com o elemento visual

* O utilizador paira o rato sobre o elemento de dados

    O elemento visual pode apresentar informações adicionais sobre o ponto de dados através da API de Descrições do Power BI.
    O utilizador paira o rato sobre a imagem que o elemento visual consegue processar eventos e apresenta os dados no elemento da descrição.

    O elemento visual pode apresentar a descrição padrão ou descrição de página de relatório.

    Para obter mais informações, leia o guia [como adicionar descrições](add-tooltips.md).

* O utilizador altera as propriedades do elemento visual (por exemplo, o utilizador expande a árvore e o elemento visual guarda o estado nas propriedades)

    O elemento visual consegue guardar os valores de propriedades através da API do Power BI. Por exemplo, quando o utilizador interage com o elemento visual. E o elemento visual tem de guardar ou atualizar valores de propriedades. O elemento visual pode chamar o método `presistProperties` para tal.

* O utilizador clica na ligação de URL.

    Por predefinição, o elemento visual não consegue abrir o URL. Para abrir o URL no novo separador, o elemento visual deve chamar o método `launchURL` e transmitir o URL como parâmetro.

    Para obter mais informações, veja [iniciar API de URL](launch-url.md).

* O utilizador aplica filtros através do elemento visual

    O utilizador chama `applyJSONFilter` e transmite as condições dos filtros para filtrar dados noutro elemento visual.

    O elemento visual pode utilizar vários tipos de filtros, por exemplo, o filtro básico, filtro avançado e filtro da cadeia de identificação.

    Para obter mais informações sobre filtros, [leia sobre como os elementos visuais do Power BI conseguem filtrar dados noutros elementos visuais](filter-api.md).

* O utilizador clica/seleciona os elementos no elemento visual.

    Para obter mais informações sobre seleções, [leia como o elemento visual interage](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>O elemento visual interage com o Power BI

* O elemento visual pede mais dados do Power BI.

    O elemento visual consegue processar dados por partes. O método da AI FetchMoreData pede o próximo fragmento de conjunto de dados.

    Para obter mais informações sobre `fetchMoreData`, [leia sobre como obter mais dados do Power BI](fetch-more-data.md)

* Serviço de eventos

    O Power BI pode exportar relatórios para PDF ou enviá-los por e-mail (só estão suportados os elementos visuais certificados). Para notificar o Power BI de que a composição está concluída e pronta para capturar o PDF/e-mail, o elemento visual deve chamar a API de Eventos de Composição.

    Para obter mais informações, [leia sobre como exportar relatórios do Power BI para PDF](../../consumer/end-user-pdf.md)

    Encontre mais [informações sobre o Serviço de Eventos](event-service.md)

## <a name="next-steps"></a>Próximos passos

É um programador Web e está interessado em criar as suas próprias visualizações e adicioná-las ao AppSource? Veja [Desenvolver um elemento visual do Power BI](./custom-visual-develop-tutorial.md) e saiba como [publicar elementos visuais do Power BI no AppSource](../office-store.md).
