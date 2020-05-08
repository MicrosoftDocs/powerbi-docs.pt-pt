---
title: Orientação relativa à dobragem de consultas no Power BI Desktop
description: Orientação para efetuar dobragem de consultas do Power Query no Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: e8123bba9f68305e1944dbfb280b5255e4fb9b48
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75622143"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Orientação relativa à dobragem de consultas no Power BI Desktop

Este artigo destina-se aos modeladores de dados que criam modelos no Power BI Desktop. Fornece boas práticas sobre quando e como pode efetuar dobragem de consultas do Power Query.

A _dobragem de consultas_ é a capacidade de uma consulta do Power Query gerar uma única instrução de consulta que obtém e transforma dados de origem. Para obter mais informações, veja [Dobragem de consultas do Power Query](/power-query/power-query-folding).

## <a name="guidance"></a>Orientação

A orientação relativa à dobragem de consultas difere em função do modo de modelo.

Para uma tabela de modo de armazenamento **DirectQuery** ou **Dual**, a consulta do Power Query tem de efetuar a dobragem de consultas.

Para uma tabela **Importar**, poderá ser possível efetuar dobragem de consultas. Quando a consulta se baseia numa origem relacional e for possível construir uma instrução SELECT individual, alcança o _melhor desempenho de atualização de dados_ ao garantir que a dobragem de consultas é efetuada. Se o motor de mashup do Power Query ainda for necessário para processar transformações, deve tentar minimizar o trabalho que é necessário, especialmente em conjuntos de dados grandes.

A lista com marcas que se segue fornece orientações específicas.

- **Delegue à origem de dados o máximo possível de processamento**: Quando nem todos os passos de uma consulta do Power Query puderem ser dobrados, descubra qual é o passo que impede a dobragem de consultas. Quando for possível, mova os passos posteriores para uma fase anterior da sequência, para que possam ser tidos em conta na dobragem de consultas. Tenha em atenção que o motor de mashup do Power Query pode ser suficientemente inteligente para reordenar os passos da sua consulta quando gerar a consulta de origem.

    Numa origem de dados relacional, se o passo que impede a dobragem de consultas puder ser efetuado numa única instrução SELECT, ou na lógica processual de um procedimento armazenado, considere a utilização de uma consulta SQL nativa, como se descreve a seguir.

- **Utilize uma consulta SQL nativa:** quando uma consulta do Power Query obtiver dados de uma origem relacional, é possível utilizar uma consulta SQL nativa para algumas origens. A consulta pode de facto ser qualquer instrução válida, incluindo uma execução de procedimento armazenado. Se a instrução produzir múltiplos resultados, apenas o primeiro será devolvido. Os parâmetros podem ser declarados na instrução e recomendamos que utilize a função M [Value.NativeQuery](/powerquery-m/value-nativequery). Esta função foi concebida para transmitir valores de parâmetros de forma segura e conveniente. É importante compreender que o motor de mashup do Power Query não pode dobrar passos de consulta posteriores, pelo que deve incluir toda (ou o máximo possível) a lógica de transformação na instrução de consulta nativa.

    Existem duas considerações importantes que tem de ter em conta quando utilizar consultas SQL nativas:

    - Para uma tabela de modelo DirectQuery, a consulta tem de ser uma instrução SELECT e não pode utilizar Expressões de Tabelas Comuns (CTEs) ou um procedimento armazenado.
    - A atualização incremental não pode utilizar uma consulta SQL nativa. Por conseguinte, forçaria o motor de mashup do Power Query a obter todas as linhas de origem e, em seguida, a aplicar filtros para determinar mudanças incrementais.

    > [!IMPORTANT]
    > Uma consulta SQL nativa pode potencialmente fazer mais do que obter dados. Qualquer instrução válida pode ser executada (e possivelmente mais do que uma vez), incluindo uma que modifique ou elimine dados. É importante que aplique o princípio de privilégio mínimo para garantir que a conta utilizada para aceder à base de dados apenas tem permissões de leitura para os dados necessários.

- **Preparação e dados de transformação na origem:** quando identificar que determinados passos de consultas do Power Query não podem ser dobrados, poderá ser possível aplicar as transformações na origem de dados. As transformações podem ser conseguidas ao escrever uma vista de base de dados que transforme de forma lógica os dados de origem. Em alternativa, podem ser conseguidas ao preparar e materializar os dados fisicamente, antes de o Power BI os consultar. Um armazém de dados relacional é um excelente exemplo de dados preparados, que normalmente consiste em origens pré-integradas de dados organizacionais.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- Artigo concetual relativo à [dobragem de consultas](/power-query/power-query-folding) do Power Query
- [Atualização incremental no Power BI Premium](../service-premium-incremental-refresh.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
