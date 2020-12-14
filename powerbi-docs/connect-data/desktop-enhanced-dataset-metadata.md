---
title: Utilizar metadados de conjuntos de dados otimizados no Power BI Desktop
description: Este artigo explica como utilizar metadados de conjuntos de dados otimizados no Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906988"
---
# <a name="using-enhanced-dataset-metadata"></a>Utilizar metadados de conjuntos de dados otimizados

Quando o Power BI Desktop cria relatórios, também cria conjuntos de dados nos ficheiros PBIX e PBIT correspondentes. Anteriormente, os metadados eram armazenados num formato específico do Power BI Desktop. Os metadados utilizaram origens de dados e expressões M com codificação base 64. O Power BI fez suposições sobre como os metadados foram armazenados.

Com o lançamento da funcionalidade **metadados de conjuntos de dados otimizados**, muitas destas limitações desapareceram. Os ficheiros PBIX são atualizados automaticamente para os metadados otimizados durante a abertura do ficheiro. Com os **metadados de conjuntos de dados otimizados**, os metadados criados pelo Power BI Desktop utilizam um formato semelhante ao utilizado para os modelos em tabela do Analysis Services, com base no [Modelo de Objeto em Tabela](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


A funcionalidade **metadados de conjuntos de dados otimizados** é estratégica e fundamental. As futuras funcionalidades do Power BI serão criadas com base nos respetivos metadados. Estas outras funcionalidades tiram partido dos metadados de conjuntos de dados otimizados:

- [Leitura/escrita de XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) para gestão de conjuntos de dados do Power BI.
- Migração de cargas de trabalho do Analysis Services para o Power BI, para tirar partido de funcionalidades de próxima geração.

## <a name="limitations"></a>Limitações
Antes do suporte de metadados otimizados, o Power BI Desktop adicionava uma consulta nativa ao modelo de dados para o SQL Server, Oracle, Teradata e ligações HANA legadas. Esta consulta é utilizada pelos modelos de dados do Serviço Power BI. Com o suporte de metadados otimizados, o modelo de dados do serviço Power BI regenera a consulta nativa no runtime. Não utiliza a consulta que o Power BI Desktop criou. Na maioria dos casos, esta obtenção resolve-se corretamente, mas algumas transformações não funcionarão sem ler os dados subjacentes. Pode ver alguns erros nos relatórios em que trabalhou anteriormente. Por exemplo, o erro indicará: 

"Não é possível converter uma consulta M na tabela "Dimension City" numa consulta de origem nativa. Tente novamente mais tarde ou contacte o suporte. Se contactar o suporte, indique estes detalhes." 

Pode corrigir as suas consultas em três locais diferentes no Power BI Desktop:

- Quando aplicar as alterações ou realizar uma atualização.
- Numa barra de aviso no Editor do Power Query a indicar que não foi possível dobrar a expressão à origem de dados.
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="Captura de ecrã a mostrar a mensagem Aplicar alterações de consulta: Não foi possível dobrar a expressão à origem de dados.":::
- Quando executa avaliações ou abre um relatório para verificar se existem consultas não suportadas. A execução destas avaliações pode ter implicações no desempenho.


## <a name="next-steps"></a>Próximos passos

Pode fazer todo o tipo de coisas com o Power BI Desktop. Para obter mais informações sobre as suas capacidades, veja os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Quais são as novidades no Power BI Desktop?](../fundamentals/desktop-latest-update.md)
* [Descrição geral das Consultas no Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
