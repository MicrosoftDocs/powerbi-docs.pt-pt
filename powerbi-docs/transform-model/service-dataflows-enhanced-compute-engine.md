---
title: Utilizar o motor de computação melhorado com fluxos de dados
description: Saiba como utilizar o motor de computação melhorado no Power BI Premium com fluxos de dados
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 06/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: f003a62fb8e2b3495dee8dac7b553a2ff72bd6b1
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240010"
---
# <a name="the-enhanced-compute-engine"></a>O motor de computação melhorado

O motor de computação melhorado no Power BI permite que os subscritores do Power BI Premium utilizem as suas capacidades para otimizar a utilização de fluxos de dados. A utilização do motor de computação melhorado proporciona as seguintes vantagens:

* Reduz drasticamente o tempo de atualização necessário para passos de ETL de execução longa em entidades calculadas, como a execução de *associações*, *distinto*, *filtros* e *agrupar por*
* Executa consultas do DirectQuery em entidades (em fevereiro de 2020)

As seguintes secções descrevem como ativar o motor de computação melhorado e como responder a perguntas comuns.


## <a name="using-the-enhanced-compute-engine"></a>Utilizar o motor de computação melhorado

O motor de computação melhorado é ativado na página **Definições de Capacidade** no serviço Power BI, na secção de **fluxos de dados**. Por predefinição, o motor de computação melhorado está **Desativado**. Para o ativar, desloque o botão de alternar para **Ativado**, conforme apresentado na seguinte imagem, e guarde as definições. 

![Ativar o motor de computação melhorado](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

> [!IMPORTANT]
> O motor de computação melhorado funciona apenas para as capacidades A3 e superiores do Power BI.

Depois de ativar o motor de computação melhorado, regresse à secção de fluxos de dados e deverá observar uma melhoria no desempenho em qualquer entidade calculada que execute operações complexas, como as operações *associações* ou *agrupar por* para fluxos de dados criados com base em entidades associadas existentes na mesma capacidade. 

Para utilizar o motor de computação da melhor forma, deve dividir a fase de ETL em dois fluxos de dados em separados da seguinte forma:

* **Fluxo de dados 1** – este fluxo de dados deve apenas ingerir tudo o que for necessário de uma origem de dados e colocar tudo isso no Fluxo de dados 2.
* **Fluxo de dados 2** – execute todas as operações de ETL neste segundo fluxo de dados, mas certifique-se de que está a fazer referência ao Fluxo de dados 1, que deve estar na mesma capacidade. Além disso, certifique-se de que executa primeiro operações que podem efetuar divisões (filtrar, agrupar por, distinto, associar) antes de qualquer outra operação, para garantir que o motor de computação é utilizado.

## <a name="common-questions-and-answers"></a>Perguntas comuns e respostas

**Pergunta:** Ativei o motor de computação melhorado, mas as minhas atualizações estão mais lentas. Porquê?

**Resposta:** Se ativar o motor de computação melhorado, existem duas explicações possíveis que podem levar a tempos de atualização mais lentos:

 - Quando o motor de computação melhorado está ativado, exige alguma memória para funcionar corretamente. Assim, a memória disponível para executar uma atualização é reduzida e, por conseguinte, a probabilidade de as atualizações serem colocadas em fila de espera aumenta, o que, por sua vez, reduz o número de fluxos de dados que podem ser atualizados em simultâneo. Para resolver o problema, ao ativar o mecanismo de computação, aumente a memória atribuída aos fluxos de dados para garantir que a memória disponível para as atualizações de dados em simultâneo permanece a mesma.

 - Outro motivo para as atualizações mais lentas é que o motor de computação funciona apenas sobre entidades existentes. Se o fluxo de dados fizer referência a uma origem de dados que não é um fluxo de dados, não irá observar uma melhoria. Não haverá um aumento do desempenho, pois, em alguns cenários de macrodados, a leitura inicial de uma origem de dados será mais lenta porque os dados precisam de ser transmitidos para o motor de computação melhorado.  

**Pergunta:** Não consigo ver o botão de alternar do motor de computação. Porquê?

**Resposta:** O motor de computação melhorado está a ser lançado por fases em regiões em todo o mundo. Prevemos que todas as regiões terão suporte no fim de 2020.

**Pergunta:** Quais são os tipos de dados suportados para o motor de computação?

**Resposta:** O motor de computação melhorado e os fluxos de dados suportam atualmente os seguintes tipos de dados. Se o fluxo de dados não utilizar um dos seguintes tipos de dados, ocorrerá um erro durante a atualização:

* Data/Hora
* Número Decimal
* Texto
* Número inteiro
* Data/Hora/Zona
* Verdadeiro/Falso
* Data
* Hora

## <a name="next-steps"></a>Próximos passos

Este artigo forneceu informações sobre como utilizar o motor de computação melhorado para fluxos de dados. Os seguintes artigos também poderão ser úteis:

* [Preparação personalizada de dados com fluxos de dados](service-dataflows-overview.md)
* [Criar e utilizar fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Utilizar entidades calculadas no Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Recursos para programadores para fluxos de dados do Power BI](service-dataflows-developer-resources.md)

Para obter mais informações sobre o Power Query e a atualização agendada, pode ler estes artigos:
* [Descrição geral das consultas no Power BI Desktop](desktop-query-overview.md)
* [Configurar a atualização agendada](../connect-data/refresh-scheduled-refresh.md)

Para obter mais informações sobre o Common Data Service, pode ler o seguinte artigo de descrição geral:
* [Common Data Service – descrição geral](https://docs.microsoft.com/powerapps/common-data-model/overview)
