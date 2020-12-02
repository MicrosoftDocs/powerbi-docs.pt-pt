---
title: Utilizar metadados de conjuntos de dados otimizados no Power BI Desktop
description: Este artigo explica como utilizar metadados de conjuntos de dados otimizados no Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 09/22/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 2c5e465026f1ba7564bda18ad3b005b024a663a7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404991"
---
# <a name="using-enhanced-dataset-metadata"></a>Utilizar metadados de conjuntos de dados otimizados

Quando o Power BI Desktop cria relatórios, também cria conjuntos de dados nos ficheiros PBIX e PBIT correspondentes. Anteriormente, os metadados eram armazenados num formato específico do Power BI Desktop. Utilizavam expressões M com codificação base 64 e origens de dados, e eram efetuados pressupostos sobre a forma como os metadados eram armazenados.

Com o lançamento da funcionalidade **metadados de conjuntos de dados otimizados**, muitas destas limitações desapareceram. Os ficheiros PBIX são atualizados automaticamente para os metadados otimizados durante a abertura do ficheiro. Com os **metadados de conjuntos de dados otimizados**, os metadados criados pelo Power BI Desktop utilizam um formato semelhante ao utilizado para os modelos em tabela do Analysis Services, com base no [Modelo de Objeto em Tabela](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


A funcionalidade **metadados de conjuntos de dados otimizados** é estratégica e fundamental, uma vez que as futuras funcionalidades do Power BI serão criadas com base nos respetivos metadados. Algumas funcionalidades adicionais que tiram partido dos metadados de conjuntos de dados otimizados incluem a [leitura/escrita de XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) para gestão de conjuntos de dados do Power BI e a migração de cargas de trabalho do Analysis Services para o Power BI que tira partido de funcionalidades de próxima geração.


## <a name="next-steps"></a>Próximos passos

Pode fazer todo o tipo de coisas com o Power BI Desktop. Para obter mais informações sobre as suas capacidades, veja os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Quais são as novidades no Power BI Desktop?](../fundamentals/desktop-latest-update.md)
* [Descrição geral das Consultas no Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](../transform-model/desktop-common-query-tasks.md)