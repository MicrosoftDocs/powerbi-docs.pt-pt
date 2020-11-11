---
title: Limitações, restrições, conectores suportados e funcionalidades dos fluxos de dados
description: Descrição geral de todas as capacidades dos fluxos de dados
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 89de77e65d8eb675d9e80c3b2497f39af7c32d33
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396593"
---
# <a name="dataflows-limitations-and-considerations"></a>Limitações e considerações dos fluxo de dados

Os fluxos de dados têm algumas limitações relativas à criação, atualização e gestão de capacidades que os utilizadores devem ter em mente, como descrito nas seguintes secções.

## <a name="dataflow-authoring"></a>Criação de Fluxos de Dados

Ao criar fluxos de dados, os utilizadores devem ter em consideração o seguinte:

* A criação em fluxos de dados é realizada no ambiente do Power Query Online (PQO); veja as limitações descritas no artigo [Limites do Power Query](/power-query/power-query-online-limits).
Como a criação de fluxos de dados é realizada no ambiente do Power Query Online (PQO), as novas versões aplicadas nas configurações de cargas de trabalho de fluxos de dados só afetam as atualizações e não terão impacto na experiência de criação

* Os fluxos de dados só podem ser modificados pelos respetivos proprietários

* Os fluxos de dados não estão disponíveis na secção *A Minha Área de Trabalho*

* Os fluxos de dados que utilizam origens de dados de gateway não suportam múltiplas credenciais para a mesma origem de dados

* A utilização do conector Web.Page requer um gateway

## <a name="api-considerations"></a>Considerações sobre a API

Pode encontrar mais informações sobre as APIs REST de Fluxos de Dados suportadas na [referência da API REST](/rest/api/power-bi/dataflows). Eis algumas considerações a ter em mente:

* Exportar e importar um fluxo de dados atribui um novo ID ao mesmo

* Importar fluxos de dados que contenham entidades ligadas não corrige as referências existentes no fluxo de dados (estas consultas devem ser corrigidas manualmente antes de importar o fluxo de dados)

* Os fluxos de dados podem ser substituídos com o parâmetro *CreateOrOverwrite* , caso tenham sido inicialmente criados com a API de importação

## <a name="dataflows-in-shared"></a>Fluxos de Dados em Capacidades Partilhadas

Os fluxos de dados em capacidades partilhadas têm limitações:

* Ao atualizar fluxos de dados, os tempos limite dos recursos partilhados são de 2 horas por entidade e de 3 horas por fluxo de dados
* Não podem ser criadas entidades ligadas em fluxos de dados partilhados, embora essas entidades possam existir no fluxo de dados (desde que a propriedade *Load Enabled* na consulta esteja desativada)
* Não podem ser criadas entidades calculadas em fluxos de dados partilhados
* Os serviços Cognitivos e AutoML não estão disponíveis em fluxos de dados partilhados
* A atualização incremental não funciona em fluxos de dados partilhados

## <a name="dataflows-in-premium"></a>Fluxos de Dados em Capacidades Premium

Os fluxos de dados existentes em Capacidades Premium têm as seguintes limitações e considerações.

**Considerações de dados e atualizações:**

* Ao atualizar fluxos de dados, os tempos limite são de 24 horas (não existe distinção para entidades e/ou fluxos de dados)

* Alterar um fluxo de dados de uma política de atualização incremental para uma atualização normal ou vice-versa removerá todos os dados

* Modificar o esquema de um fluxo de dados removerá todos os dados

**Entidades Calculadas e Ligadas:**

* As entidades ligadas podem ter até 32 referências

* As dependências cíclicas de entidades associadas não são permitidas

* Uma entidade ligada não pode ser associada a uma entidade normal que obtém os seus dados a partir de uma origem de dados no local

* Quando uma consulta (consulta *A* , por exemplo) é utilizada no cálculo de outra consulta (consulta *B* ) nos fluxos de dados, a consulta *B* torna-se uma entidade calculada. As entidades calculadas não podem fazer referência a origens no local.


**Motor de Computação:**

* Ao utilizar o motor de computação, existe um aumento inicial aproximado de 10% ou 20% no tempo de ingestão de dados.

  1. Isto só se aplica ao primeiro fluxo de dados que está no motor de computação e lê os dados a partir da origem de dados
  2. Os fluxos de dados subsequentes que utilizem a origem não registarão a mesma penalização

* Apenas determinadas operações tiram partido do motor de computação e apenas quando são efetuadas através de uma entidade ligada ou como uma entidade calculada. [Esta publicação de blogue](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html) inclui uma lista completa das operações.


**Gestão de Capacidades:**

* Por predefinição, as Capacidades Premium do Power BI têm um gestor de recursos interno que limita as cargas de trabalho de formas diferentes quando a capacidade é executada em condições de memória reduzida.

  1. Quando se trata de fluxos de dados, esta pressão de limitação reduz o número de Contentores M disponíveis
  2. A memória dos fluxos de dados pode ser definida como 100%, com um contentor de tamanho adequado para os tamanhos dos seus dados. Além disso, a carga de trabalho irá gerir o número de contentores adequadamente

* O número aproximado de contentores pode ser determinado ao dividir o total de memória alocada à carga de trabalho pelo montante de memória alocada a um contentor

## <a name="dataflow-usage-in-datasets"></a>Utilização de fluxos de dados em conjuntos de dados

* Ao criar um conjunto de dados no Power BI Desktop e ao publicá-lo posteriormente no serviço Power BI, certifique-se de que as credenciais utilizadas no Power BI Desktop para a origem de dados dos fluxos de dados são as mesmas que são utilizadas ao publicar o conjunto de dados no serviço.
  1. Se não forem utilizadas as mesmas credenciais, será apresentado um erro *Chave não encontrada* ao atualizar o conjunto de dados

## <a name="next-steps"></a>Passos seguintes
Os seguintes artigos fornecem mais informações sobre os fluxos de dados e o Power BI:

* [Introdução aos fluxos de dados e à preparação personalizada de dados](dataflows-introduction-self-service.md)
* [Criar um fluxo de dados](dataflows-create.md)
* [Configurar e consumir um fluxo de dados](dataflows-configure-consume.md)
* [Configurar o armazenamento de fluxos de dados para utilizar o Azure Data Lake Gen2](dataflows-azure-data-lake-storage-integration.md)
* [Funcionalidades Premium do fluxo de dados](dataflows-premium-features.md)
* [IA com fluxos de dados](dataflows-machine-learning-integration.md)