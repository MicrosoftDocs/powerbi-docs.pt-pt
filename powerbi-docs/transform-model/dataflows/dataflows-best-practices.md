---
title: Melhores práticas dos fluxos de dados
description: Uma coleção de orientações e ligações de melhores práticas para fluxos de dados
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/13/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5adfcc3d4ff7d78335f250b92b856bcd14d64c0a
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674757"
---
# <a name="dataflows-best-practices"></a>Melhores práticas dos fluxos de dados

Os **fluxos de dados** do Power BI são uma solução de preparação de dados focada para empresas, permitindo um ecossistema de dados prontos para consumo, reutilização e integração. Este artigo disponibiliza uma lista de melhores práticas, com ligações para artigos e outras informações que o poderão ajudar a compreender e tirar partido de todo o potencial dos fluxos de dados.


## <a name="dataflows-best-practices-table-and-links"></a>Tabela e ligações de melhores práticas para fluxos de dados

A seguinte tabela fornece uma coleção de ligações para artigos que descrevem melhores práticas para a criação ou utilização de fluxos de dados. As ligações incluem informações sobre o desenvolvimento de lógica de negócio, o desenvolvimento de fluxos de dados complexos, a reutilização de fluxos de dados e como alcançar o nível empresarial com os seus fluxos de dados.


|**Tópico**  |**Área de orientações**  |**Ligação para artigo ou conteúdo**  |
|---------|---------|---------|
|Power Query     | Sugestões e truques para tirar o máximo partido da experiência de data wrangling        |[Melhores práticas do Power Query](https://docs.microsoft.com/power-query/best-practices)        |
|Tirar Partido de Entidades Calculadas     |A utilização de entidades calculadas num fluxo de dados fornece benefícios de desempenho         |[Cenários de Entidades Calculadas](https://docs.microsoft.com/power-query/dataflows/computed-entities-scenarios)         |
|Desenvolver fluxos de dados complexos     |Padrões para desenvolver fluxos de dados em grande escala e com elevado desempenho         |[Fluxos de dados complexos](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|Reutilizar fluxos de dados     |Padrões, orientações e casos de utilização         |[Reutilizar fluxos de dados](https://docs.microsoft.com/power-query/dataflows/best-practices-reusing-dataflows)         |
|Implementações em grande escala     |Orientações e utilização em grande escala para complementar a arquitetura empresarial         |[Armazenamento de dados ao utilizar fluxos de dados](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|Tirar Partido da Computação Melhorada     |Melhorar potencialmente o desempenho dos fluxos de dados até 25 vezes         |[Motor de Computação Melhorado](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|Otimizar as definições de carga de trabalho     |Tire o máximo partido da sua infraestrutura de fluxos de dados ao compreender as configurações que permitem maximizar o desempenho         |[Configuração da carga de trabalho de fluxos de dados](dataflows-premium-workload-configuration.md)         |
|Intercalar e expandir tabelas     |Criar associações de elevado desempenho         |[Otimizar as operações de expansão de tabelas](https://docs.microsoft.com/power-query/optimize-expanding-table-columns)         |
|Orientações para a dobragem de consultas     |Acelerar as transformações através do sistema de origem         |[Dobragem de consultas](https://docs.microsoft.com/power-query/power-query-folding)         |
|Utilizar a criação de perfis de dados     |Compreender o perfil, a distribuição e a qualidade das colunas         |[Ferramentas de criação de perfis de dados](https://docs.microsoft.com/power-query/data-profiling-tools)         |
|Implementar o processamento de erros     |Desenvolver fluxos de dados robustos que sejam resilientes a erros de atualização, com sugestões         |[Padrões de erros comuns](https://docs.microsoft.com/power-query/dealing-with-errors)  </br> [Processamento de erros complexos](https://docs.microsoft.com/power-query/error-handling)      |
|Utilizar a Vista de esquema      |Melhore a experiência de criação ao trabalhar com tabelas largas e executar operações ao nível do esquema         |[Vista de esquema](https://docs.microsoft.com/power-query/schema-view)         |
|||


        
## <a name="next-steps"></a>Passos seguintes

Os seguintes artigos fornecem mais informações sobre as fluxos de dados e o Power BI:

* [Introdução aos fluxos de dados e à preparação personalizada de dados](dataflows-introduction-self-service.md)
* [Criar um fluxo de dados](dataflows-create.md)
* [Configurar e consumir um fluxo de dados](dataflows-configure-consume.md)
* [Funcionalidades Premium do fluxo de dados](dataflows-premium-features.md)
* [Configurar o armazenamento do fluxo de dados para utilizar o Azure Data Lake Gen2](dataflows-azure-data-lake-storage-integration.md)
* [IA com fluxos de dados](dataflows-machine-learning-integration.md)
* [Limitações e considerações dos fluxo de dados](dataflows-features-limitations.md)