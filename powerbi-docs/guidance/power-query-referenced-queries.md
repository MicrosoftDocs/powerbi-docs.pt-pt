---
title: Referencing Power Query queries (Referenciar consultas do Power Query)
description: Orientação para referenciar consultas do Power Query.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 49601798ae920d956441c5580079625bf7408e07
ms.sourcegitcommit: b59ec11a4a0a3d5be2e4d91548d637d31b3491f8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78290582"
---
# <a name="referencing-power-query-queries"></a>Referencing Power Query queries (Referenciar consultas do Power Query)

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Fornece-lhe a orientação ao definir as consultas do Power Query que fazem referência a outras consultas.

Vamos clarificar o que isto significa: _Quando uma consulta faz referência a uma segunda consulta, é como se os passos na segunda consulta fossem combinados e executados antes dos passos na primeira consulta._

Considere diversas consultas: a **Consulta1** extrai os dados de um serviço Web e a carga é desativada. **Consulta2**, **Consulta3**e **Consulta4** referenciam todas a **Consulta1** e as saídas destas consultas são carregadas no modelo de dados.

![Vista das Dependências das Consultas a apresentar as consultas descritas no parágrafo anterior.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Quando o modelo de dados é atualizado, é geralmente assumido que o Power Query recupera o resultado da **Consulta1** e este é reutilizado pelas consultas referenciadas. Esta lógica está incorreta. Na realidade, o Power Query executa a **Consulta2**, a **Consulta3**e a **Consulta4** separadamente.

Pode considerar que a **Consulta2** tem os passos da **Consulta1** incorporados na mesma. Este é o caso da **Consulta3** e da **Consulta4**. O diagrama que se segue apresenta uma visão mais clara de como as consultas são executadas.

![Uma versão modificada da vista das Dependências das Consultas a apresentar a Consulta 2, a Consulta 3 e a Consulta 4. Cada uma das três consultas tem a Consulta 1 incorporada.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

A **Consulta1** é executada três vezes. As várias execuções podem resultar numa atualização de dados lenta e num impacto negativo sobre a origem de dados.

A utilização da função [Table.Buffer](/powerquery-m/table-buffer) na **Consulta1** não eliminará a obtenção de dados adicionais. Esta função coloca uma tabela em memória intermédia. E, a tabela em memória intermédia só pode ser utilizada na mesma execução da consulta. Assim, no exemplo, se a **Consulta1** for colocada em memória intermédia quando a **Consulta2** é executada, os dados em memória intermédia não poderão ser utilizados quando a **Consulta3** e a **Consulta4** são executadas. Elas próprias colocam os dados em memória intermédia mais duas vezes (este resultado poderia, de facto, compor o desempenho negativo, pois a tabela será armazenada em memória intermédia por cada consulta de referenciada).

> [!NOTE]
> A arquitetura de colocação em cache do Power Query é complexa e não é o foco deste artigo. O Power Query pode colocar em cache os dados obtidos de uma origem de dados. No entanto, quando executa uma consulta, este pode obter os dados da origem de dados mais de uma vez.

## <a name="recommendations"></a>Recomendações

No geral, recomendamos que faça referência às consultas para evitar a duplicação da lógica entre as consultas. No entanto, conforme descrito neste artigo, esta abordagem de conceção pode contribuir para atualizações de dados lentas e origens de dados sobrecarregadas.

Recomenda-se crie em alternativa um [fluxo de dados](../service-dataflows-overview.md). A utilização de um fluxo de dados pode melhorar o tempo de atualização de dados e reduzir o impacto sobre as origens de dados.

Pode criar um fluxo de dados para encapsular a origem dos dados e as transformações. Dado que o fluxo de dados é um arquivo de dados persistente no serviço Power BI, a sua obtenção de dados é rápida. Assim, mesmo quando o referenciar de consultas resultar em vários pedidos para o fluxo de dados, os tempos de atualização de dados podem ser melhorados.

No exemplo, se a **Consulta1** for reformulada como uma entidade de fluxo de dados, a **Consulta2**, a **Consulta3** e a **Consulta4** poderão ser utilizadas como uma origem de dados. Com este design, a entidade originada na **Consulta1** será avaliada apenas uma vez.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Preparação personalizada de dados no Power BI](../service-dataflows-overview.md)
- [Criar e utilizar fluxos de dados no Power BI](../service-dataflows-create-use.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
