---
title: Ligar a conjuntos de dados do Power BI Premium com aplicações de cliente e ferramentas (pré-visualização)
description: Descreve como ligar a conjuntos de dados no Power BI Premium, a partir de aplicações de cliente e ferramentas.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 063f43cb2345ccb3d1fec5c414100beb8ccde451
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941521"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Ligar a conjuntos de dados com aplicações de cliente e ferramentas (pré-visualização)

Suporte de áreas de trabalho e conjuntos de dados de BI Premium do Power *só de leitura* ligações da Microsoft e de aplicativos cliente de terceiros e de ferramentas. 

> [!NOTE]
> Este artigo destina-se apenas ao introduzir a conectividade só de leitura para áreas de trabalho do Power BI Premium e conjuntos de dados. Ele *není* o objetivo de fornecer informações aprofundadas sobre programação, ferramentas específicas e aplicativos, arquitetura e gerenciamento de área de trabalho e o conjunto de dados. Assuntos descritos aqui requerem uma compreensão sólida da arquitetura de base de dados de modelo em tabela do Analysis Services e administração.

## <a name="protocol"></a>Protocolo

Power BI Premium utiliza o [XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) protocolo (XMLA) para comunicações entre os aplicativos de cliente e o mecanismo que gerencia seus espaços de trabalho e os conjuntos de dados. Essas comunicações são o que são normalmente chamados de como pontos finais XMLA. XMLA é o mesmo protocolo de comunicação utilizado pelo motor da Microsoft Analysis Services, que, nos bastidores, executa a gestão de modelagem, governação, ciclo de vida e dados semântica no Power BI. 

A grande maioria das ferramentas e as aplicações de cliente não explicitamente comunicam com o mecanismo ao utilizar pontos finais XMLA. Em vez disso, eles usam bibliotecas de cliente como MSOLAP, AMO e ADOMD, como um intermediário entre a aplicação de cliente e o mecanismo, o que comunica-se exclusivamente ao uso do XMLA.


## <a name="supported-tools"></a>Ferramentas suportadas

Estas ferramentas oferecem suporte a acesso só de leitura para áreas de trabalho do Power BI Premium e conjuntos de dados:

**SQL Server Management Studio (SSMS)** -consultas DAX suporta, MDX, XMLA e TraceEvent. Requer versão 18.0. Baixe [aqui](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**SQL Server Profiler** -incluído com o SSMS 18.0 (pré-visualização), essa ferramenta fornece rastreamento e depuração de eventos do servidor. Pode capturar e salvar dados sobre cada evento num arquivo ou uma tabela para analisar mais tarde. Embora oficialmente preteridas para o SQL Server, o Profiler continua a ser incluído no SSMS e continua a ser suportado para o Analysis Services e agora, o Power BI Premium. Para obter mais informações, consulte [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**DAX Studio** - aberto, ferramenta de Comunidade para executar e analisar o DAX consulta no Analysis Services. Requer versão 2.8.2 ou superior. Para obter mais informações, consulte [daxstudio.org](https://daxstudio.org/).

**Tabelas dinâmicas do Excel** -Click-to-Run versão do Office 16.0.11326.10000 ou superior é obrigatório.

**Terceiros** - inclui aplicações de visualização de dados do cliente e ferramentas que se podem ligar, consulta e consumir os conjuntos de dados no Power BI Premium. A maioria das ferramentas exigem as versões mais recentes das bibliotecas de cliente MSOLAP, mas alguns podem utilizar ADOMD.

## <a name="client-libraries"></a>Bibliotecas de cliente

Bibliotecas de cliente são necessárias para aplicativos de cliente e ferramentas ligar a áreas de trabalho do Power BI Premium. As mesmo bibliotecas de cliente utilizadas para ligar ao Analysis Services também são suportadas no Power BI Premium. Aplicações de cliente da Microsoft, como o Excel, o SQL Server Management Studio (SSMS) e o SQL Server Data Tools (SSDT) instale todas as três bibliotecas de cliente e atualização-las juntamente com as atualizações de aplicativo regular. Em alguns casos, especialmente com aplicativos de terceiros e ferramentas, terá de instalar as versões mais recentes das bibliotecas de cliente. Bibliotecas de cliente são atualizadas mensalmente. Para obter mais informações, consulte [bibliotecas de cliente para ligar ao Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>Ligar a uma área de trabalho Premium

Pode ligar a áreas de trabalho atribuídas a capacidades Premium dedicada. Áreas de trabalho atribuídas a uma capacidade dedicada têm uma cadeia de ligação no formato de URL. 

Para obter a cadeia de ligação de área de trabalho, no Power BI, além **definições de área de trabalho**, na **Premium** separador **ligação de área de trabalho**, clique em **copiar**.

![Cadeia de ligação de área de trabalho](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

Ligações de área de trabalho utilizam o formato de URL seguinte para resolver uma área de trabalho, como se fosse um nome de servidor do Analysis Services:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Por exemplo, `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`
> [!NOTE]
> `[workspace name]` é caso confidencial e pode incluir espaços. 

### <a name="to-connect-in-ssms"></a>Para ligar-se no SSMS

Na **ligar ao servidor** > **tipo de servidor**, selecione **Analysis Services**. Na **nome do servidor**, introduza o URL. Na **autenticação**, selecione **Active Directory - Universal com o suporte de MFA**e, em seguida, na **nome de utilizador**, introduza o seu ID organizacional do utilizador. 

Quando estiver ligado, a área de trabalho é mostrada como um servidor do Analysis Services e conjuntos de dados na área de trabalho são apresentados como bases de dados.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Catálogo inicial

Algumas ferramentas, como o SQL Server Profiler, poderá ter de especificar um *catálogo inicial*. Especifique um conjunto de dados (banco de dados) na sua área de trabalho. Na **ligar ao servidor**, clique em **opções**. Na **ligar ao servidor** caixa de diálogo, na **propriedades da ligação** separador **ligar à base de dados**, introduza o nome do conjunto de dados.

### <a name="duplicate-workspace-name"></a>Duplicar nome da área de trabalho

Ao ligar a uma área de trabalho com o mesmo nome que outra área de trabalho, poderá receber o erro seguinte: **Não é possível ligar ao powerbi://api.powerbi.com/v1.0/ [nome do inquilino] / [nome da área de trabalho].**

Para resolver este erro, além do nome de área de trabalho, especifique o ObjectIDGuid, que pode ser copiado do objectID de área de trabalho no URL. Acrescente o objectID para o URL de ligação. Por exemplo, "powerbi://api.powerbi.com/v1.0/myorg/Contoso vendas - 9d83d204-82a9-4b36-98f2-a40099093830'

### <a name="duplicate-dataset-name"></a>Nome do conjunto de dados duplicados

Ao ligar a um conjunto de dados com o mesmo nome que outro conjunto de dados na mesma área de trabalho, anexe o guid de conjunto de dados para o nome do conjunto de dados. Pode obter ambos os nome de conjunto de dados *e* guid quando estiver ligado à área de trabalho no SSMS. 

### <a name="delay-in-datasets-shown"></a>Atraso em conjuntos de dados mostrados

Ao ligar a uma área de trabalho, as alterações de novos, excluídos e nome mudados conjuntos de dados podem demorar até 5 minutos a aparecer. 

### <a name="unsupported-datasets"></a>Conjuntos de dados não suportados

Os seguintes conjuntos de dados não estão acessíveis ao utilizar pontos finais XMLA. Estes conjuntos de dados *não irá* aparecem na área de trabalho no SSMS ou noutras ferramentas: 

- Conjuntos de dados com uma ligação em direto a modelos de Analysis Services. 
- Conjuntos de dados com dados de Push com a API de REST.
- Conjuntos de dados do livro do Excel. 

Os conjuntos de dados seguintes não são suportados no serviço Power BI:   

- Conjuntos de dados com uma ligação em direto para um conjunto de dados do Power BI.

## <a name="audit-logs"></a>Registos de auditoria 

Ao ferramentas e as aplicações cliente ligar a uma área de trabalho, o acesso através de pontos finais XMLA é registado nos registos de auditoria do Power BI no **GetWorkspaces** operação. Para obter mais informações, consulte [auditoria do Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Veja também

[Referências do Analysis Services](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[Protocolo em tabela do SQL Server Analysis Services](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[Vistas de gestão dinâmica (DMVs)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
