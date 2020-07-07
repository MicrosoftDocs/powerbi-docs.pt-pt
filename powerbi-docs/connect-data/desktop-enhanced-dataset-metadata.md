---
title: Using enhanced dataset metadata in Power BI Desktop (preview) (Utilizar conjuntos de dados otimizados no Power BI Desktop [pré-visualização])
description: Este artigo explica como utilizar metadados de conjuntos de dados otimizados no Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0a09311c5fdb1a8b2e008996d993015f33ee9b5f
ms.sourcegitcommit: a07fa723bb459494c60cf6d749b4554af723482a
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2020
ms.locfileid: "84739259"
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

## <a name="report-backup-files"></a>Ficheiros de cópia de segurança de relatórios

A atualização de um relatório para utilizar a funcionalidade **metadados de conjuntos de dados otimizados** é irreversível. No entanto, durante a atualização, é criado um ficheiro de cópia de segurança do relatório para guardar uma versão do relatório no formato original (pré-atualização). O ficheiro de cópia de segurança é removido após 30 dias. 

Para localizar o ficheiro de relatório de cópia de segurança, faça o seguinte:

1. Navegue para a seguinte localização: ```C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\TempSaves\Backup```. Se utilizar a versão da Microsoft Store do Power BI Desktop, utilize a seguinte localização: ```C:\Users\<user>\Microsoft\Power BI Desktop Store App\TempSaves\Backups``` 

2. Localize uma cópia do relatório nesse local com o nome e o carimbo data/hora do ficheiro original.

3. Copie o ficheiro para uma localização à sua escolha, para o preservar.

4. Confirme que a funcionalidade de pré-visualização **formato de metadados otimizados** está desativada no Power BI Desktop caso opte por abrir ou utilizar o ficheiro original. 

O ficheiro de cópia de segurança é criado quando o relatório é atualizado, pelo que quaisquer alterações realizadas após a atualização não são incluídas. Os novos relatórios criados quando a funcionalidade **formato de metadados otimizados** está ativada não têm nenhum ficheiro de cópia de segurança.


## <a name="considerations-and-limitations"></a>Considerações e limitações

Na versão anterior, aplicam-se as seguintes limitações quando a funcionalidade de pré-visualização está ativa.

### <a name="unsupported-features-and-connectors"></a>Funcionalidades e conectores não suportados

Aplicam-se as seguintes limitações:

Após abrir um ficheiro PBIX ou PBIT existente que não foi atualizado, a atualização irá falhar se o conjunto de dados tiver qualquer um dos seguintes conectores ou funcionalidades. Se esta falha ocorrer, em princípio, não haverá impacto imediato na experiência de utilizador e o Power BI Desktop irá continuar a utilizar o formato de metadados anterior.

* Todos os conectores personalizados (limitação da versão de maio de 2020)
* Scripts de Python
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

Se estiver a utilizar a versão de **junho de 2020** do Power BI Desktop (ou posterior), todos os conectores personalizados e incorporados *serão* suportados para o Power BI Desktop e o serviço Power BI. Durante o processo de publicação, quando utilizar a versão de junho de 2020 ou posterior, se o gateway encontrar problemas, o conjunto de dados será publicado com êxito, mas os utilizadores terão de publicar novamente o relatório para atualizar os dados. A caixa de diálogo **Definições da origem de dados** é o único indicador da ocorrência de problemas no processo de publicação.

Os relatórios que utilizarem conectores não suportados não serão atualizados para o novo formato. Os relatórios que já foram atualizados, ou que foram criados posteriormente para permitir esta nova funcionalidade, não suportarão a adição das funcionalidades ou dos conectores não suportados listados. 

As consultas com origens de dados dinâmicas não são suportadas. Os relatórios com origens de dados dinâmicas não serão atualizados para o novo formato e os relatórios que já foram atualizados ou foram recentemente criados com a funcionalidade ativada não suportarão a adição de origens de dados dinâmicas. Uma consulta terá uma origem de dados dinâmica se a origem mudar consoante um parâmetro, uma entrada de função ou uma função volátil. 

As consultas com erros nos passos ou ramos a montante não são suportadas. 

Além disso, os ficheiros PBIX e PBIT que já foram atualizados com êxito para utilizar **metadados de conjuntos de dados otimizados** *não podem* utilizar as funcionalidades acima (ou quaisquer conectores não suportados).

### <a name="lineage-view"></a>Vista de linhagem
Os conjuntos de dados que utilizam o novo formato de metadados não apresentam atualmente ligações para fluxos de dados na vista de linhagem do serviço Power BI.

## <a name="next-steps"></a>Próximos passos

Pode fazer todo o tipo de coisas com o Power BI Desktop. Para obter mais informações sobre as suas capacidades, veja os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Quais são as novidades no Power BI Desktop?](../fundamentals/desktop-latest-update.md)
* [Descrição geral das Consultas no Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de dados no Power BI Desktop](desktop-data-types.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
