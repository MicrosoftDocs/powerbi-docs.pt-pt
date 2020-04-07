---
title: Using enhanced dataset metadata in Power BI Desktop (preview) (Utilizar conjuntos de dados otimizados no Power BI Desktop [pré-visualização])
description: Este artigo explica como utilizar metadados de conjuntos de dados otimizados no Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 54c3622b0a4dd6c690c2f22a0b93aed39e9d2799
ms.sourcegitcommit: 3c51431d85793b71f378c4b0b74483dfdd8411b3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/31/2020
ms.locfileid: "80464626"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Using enhanced dataset metadata (preview) (Utilizar metadados de conjuntos de dados otimizados [pré-visualização])

Quando o Power BI Desktop cria relatórios, também cria conjuntos de dados nos ficheiros PBIX e PBIT correspondentes. Anteriormente, os metadados eram armazenados num formato específico do Power BI Desktop. Utilizavam expressões M com codificação base 64 e origens de dados, e eram efetuados pressupostos sobre a forma como os metadados eram armazenados.

Com o lançamento da funcionalidade **metadados de conjuntos de dados otimizados**, muitas destas limitações desapareceram. Com a funcionalidade **metadados de conjuntos de dados otimizados** ativada, os metadados criados pelo Power BI Desktop utilizam um formato semelhante ao utilizado para modelos em tabela do Analysis Services, com base no [Modelo de Objeto em Tabela](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


A funcionalidade **metadados de conjuntos de dados otimizados** é estratégica e fundamental, uma vez que as futuras funcionalidades do Power BI serão criadas com base nos respetivos metadados. Algumas funcionalidades adicionais que tiram partido dos metadados de conjuntos de dados otimizados incluem a [leitura/escrita de XMLA](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) para gestão de conjuntos de dados do Power BI e a migração de cargas de trabalho do Analysis Services para o Power BI que tira partido de funcionalidades de próxima geração.



## <a name="enable-enhanced-dataset-metadata"></a>Ativar a funcionalidade metadados de conjuntos de dados otimizados

De momento, a funcionalidade **metadados de conjuntos de dados otimizados** está em pré-visualização. Para ativar a funcionalidade metadados de conjuntos de dados otimizados, no Power BI Desktop, selecione **Ficheiro > Opções e definições > opções > funcionalidades de pré-visualização** e, em seguida, selecione a caixa de verificação **Armazenar conjuntos de dados com formato de metadados melhorados**, conforme apresentado na seguinte imagem. 

![Ativar a funcionalidade de pré-visualização](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Ser-lhe-á pedido que reinicie o Power BI Desktop.

![Mensagem de reinício](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Assim que a funcionalidade de pré-visualização é ativada, o Power BI Desktop tenta atualizar os ficheiros PBIX e PBIT que utilizam o formato de metadados anterior. 

> [!IMPORTANT]
> A ativação da funcionalidade **metadados de conjuntos de dados otimizados** resulta numa atualização irreversível dos relatórios. Todos os relatórios do Power BI carregados ou criados no Power BI Desktop, uma vez ativados os **metadados de conjuntos de dados otimizados**, são irreversivelmente convertidos para o formato de metadados de conjuntos de dados otimizados.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Na versão anterior, aplicam-se as seguintes limitações quando a funcionalidade de pré-visualização está ativa.

Após abrir um ficheiro PBIX ou PBIT existente que não foi atualizado, a atualização irá falhar se o conjunto de dados tiver qualquer um dos seguintes conectores ou funcionalidades. Se esta falha ocorrer, em princípio, não haverá impacto imediato na experiência de utilizador e o Power BI Desktop irá continuar a utilizar o formato de metadados anterior.

* Scripts de Python
* Conectores personalizados
* Azure DevOps Server
* Conector BI
* Denodo
* Dremio
* Exasol
* Indexima
* ÍRIS
* ODBC da Jethro
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* Expressões M com determinadas combinações de carateres como "\\n" em nomes de colunas
* Ao utilizar conjuntos de dados com a funcionalidade **metadados de conjuntos de dados otimizados** ativa, as origens de dados de Início de Sessão Único (SSO) não podem ser configuradas no serviço Power BI

Além disso, os ficheiros PBIX e PBIT que já foram atualizados com êxito para utilizar **metadados de conjuntos de dados otimizados** *não podem* utilizar os conectores ou funcionalidades anteriormente referidos na versão atual.


## <a name="next-steps"></a>Próximos passos

Pode fazer todo o tipo de coisas com o Power BI Desktop. Para obter mais informações sobre as suas capacidades, veja os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Quais são as novidades no Power BI Desktop?](desktop-latest-update.md)
* [Descrição geral das Consultas no Power BI Desktop](desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)

