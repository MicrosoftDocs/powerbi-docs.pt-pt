---
title: Migrar os relatórios do SQL Server Reporting Services para o Power BI
description: Orientações para o ajudar a migrar os seus relatórios do SQL Server Reporting Services (SSRS) para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: cf11b98d7eacd7b1e245fb0aed62d0f14e7f4c4c
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79041332"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Migrar os relatórios do SQL Server Reporting Services para o Power BI

Este artigo destina-se a autores de relatórios do SQL Server Reporting Services (SSRS) e administradores do Power BI. Fornece instruções para o ajudar a migrar os seus relatórios em [Report Definition Language (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) para o Power BI.

> [!NOTE]
> Só é possível migrar relatórios RDL. No Power BI, os relatórios RDL denominam-se _relatórios paginados_.

A orientação encontra-se dividida em quatro fases. Recomendamos que leia todo o artigo antes de migrar os seus relatórios.

1. [Antes de começar](#before-you-start)
1. [Fase de pré-migração](#pre-migration-stage)
1. [Fase de migração](#migration-stage)
1. [Fase de pós-migração](#post-migration-stage)

Pode conseguir a migração sem tempo de inatividade nos seus servidores SSRS ou interrupções para os seus utilizadores de relatórios. É importante ter em conta que não precisam de ser removidos dados ou relatórios. Ou seja, pode manter o seu ambiente atual em funções até que esteja pronto para ser descontinuado.

## <a name="before-you-start"></a>Antes de começar

Antes de iniciar a migração, deve verificar se o seu ambiente cumpre determinados pré-requisitos. Iremos descrever estes pré-requisitos e apresentar uma ferramenta de migração bastante útil.

### <a name="preparing-for-migration"></a>Preparação para migração

Ao preparar-se para migrar os seus relatórios para o Power BI, comece por verificar se a sua organização tem uma subscrição do [Power BI Premium](../service-premium-what-is.md). Esta subscrição é necessária para alojar e executar os seus relatórios paginados do Power BI.

### <a name="supported-versions"></a>Versões suportadas

Pode migrar as instâncias do SSRS em execução no local ou em Máquinas Virtuais alojadas por fornecedores de cloud como o Azure.

A seguinte lista descreve as versões do SQL Server suportadas para migração para o Power BI:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

Também é possível migrar do Power BI Report Server.

### <a name="migration-tool"></a>Ferramenta de migração

Recomendamos que utilize a [Ferramenta de Migração de RDL](https://github.com/microsoft/RdlMigration) para ajudar a preparar e migrar os seus relatórios. Essa ferramenta foi desenvolvida pela Microsoft para ajudar os clientes a migrar relatórios RDL dos seus servidores do SSRS para o Power BI. Está disponível no GitHub e inclui um guia ponto a ponto do cenário de migração.

A ferramenta automatiza as seguintes tarefas:

* Verifica se existem [origens de dados não suportadas](../paginated-reports/paginated-reports-data-sources.md) e [funcionalidades de relatórios não suportadas](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
* Converte eventuais recursos _partilhados_ em recursos _incorporados_:
  * As **origens de dados** partilhadas tornam-se origens de dados partilhadas
  * Os **conjuntos de dados** partilhados tornam-se conjuntos de dados incorporados
* Publica relatórios (que passam verificações) como relatórios paginados numa área de trabalho especificada do Power BI (numa capacidade Premium)

Não modifica nem remove os seus relatórios existentes. Ao concluir, a ferramenta produz um resumo de todas as ações concluídas, com ou sem êxito.

Ao longo do tempo, a ferramenta poderá ser otimizada pela Microsoft. Encorajamos igualmente a comunidade a contribuir para ajudar a melhorá-la.

## <a name="pre-migration-stage"></a>Fase de pré-migração

Depois de verificar se a sua organização cumpre os pré-requisitos, está pronto para iniciar a fase de _Pré-migração_. Esta fase tem três etapas:

1. Descobrir
1. Avaliar
1. Preparação

### <a name="discover"></a>Descobrir

O objetivo da etapa _Descobrir_ é identificar as suas instâncias existentes do SSRS. Este processo envolve analisar a rede para identificar todas as instâncias do SQL Server na sua organização.

Pode utilizar o [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826). Também conhecido como "MAP Toolkit", deteta e reporta as suas versões, funcionalidades instaladas e instâncias do SQL Server. Trata-se de uma poderosa ferramenta de inventário, avaliação e relatórios que pode simplificar o processo de planeamento da migração.

### <a name="assess"></a>Avaliar

Após detetar as suas instâncias do SSRS, o objetivo da etapa _Avaliar_ é conhecer quais os relatórios do SSRS (ou itens de servidor) que não podem ser migrados.

Apenas os relatórios RDL podem ser migrados dos seus servidores do SSRS para o Power BI. Cada relatório RDL migrado torna-se um relatório paginado do Power BI.

No entanto, os seguintes tipos de itens do SSRS não podem ser migrados para o Power BI:

- Origens de dados partilhadas <sup>1</sup>
- Conjuntos de dados partilhados <sup>1</sup>
- Recursos como ficheiros de imagem
- KPIs (SSRS 2016 ou posterior, apenas Enterprise Edition)
- Relatórios móveis (SSRS 2016 ou posterior, apenas Enterprise Edition)
- Modelos de relatórios (preterido)
- Peças de relatórios (preterido)

<sup>1</sup> A [Ferramenta de Migração de RDL](https://github.com/microsoft/RdlMigration) converte automaticamente conjuntos de dados e origens de dados partilhados, desde que utilizem origens de dados suportadas.

Se os seus relatórios RDL utilizam funcionalidades [ainda não suportadas pelos relatórios paginados do Power BI](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), pode planear recriá-los como [relatórios do Power BI](../consumer/end-user-reports.md). Mesmo se não conseguir migrar os seus relatórios RDL, recomendamos que considere modernizá-los como relatórios do Power BI, quando for pertinente.

Se os relatórios RDL precisarem de recuperar dados de _origens de dados no local_, não poderão utilizar o início de sessão único (SSO). Atualmente, toda a obtenção de dados destas origens de dados será feita através do contexto de segurança da _conta de utilizador da origem de dados do gateway_. O SQL Server Analysis Services (SSAS) não poderá impor a segurança ao nível da linha (RLS) por utilizador.

Regra geral, os relatórios paginados do Power BI são otimizados para **impressão**ou **geração de PDFs**. Os relatórios do Power BI estão otimizados para a **exploração e a interatividade**. Para obter mais informações, veja [Quando utilizar os relatórios paginados no Power BI](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Preparação

O objetivo da etapa _Preparação_ consiste em preparar tudo. Inclui configurar o ambiente do Power BI, planear como vai proteger e publicar os seus relatórios e ideias sobre como recriar itens do SSRS que não migrar.

1. Certifique-se de que a [carga de trabalho de Relatórios Paginados](../service-admin-premium-workloads.md#paginated-reports) está ativada na sua capacidade do Power BI Premium e de que tem memória suficiente.
1. Verifique o suporte para as [origens de dados](../paginated-reports/paginated-reports-data-sources.md) dos seus relatórios e configure um [Gateway do Power BI](../service-gateway-onprem.md) para permitir a ligação a origens de dados no local.
1. Conheça a segurança do Power BI e planeie [como irá reproduzir as suas pastas e permissões do SSRS](/sql/reporting-services/security/secure-folders) com as [áreas de trabalho e funções de áreas de trabalho do Power BI](../service-new-workspaces.md).
1. Conheça a partilha no Power BI e planeie como irá distribuir conteúdos ao publicar [aplicações do Power BI](../service-create-distribute-apps.md).
1. Considere utilizar [conjuntos de dados partilhados do Power BI](../service-datasets-build-permissions.md) em vez das suas origens de dados partilhadas do SSRS.
1. Utilize o [Power BI Desktop](../desktop-what-is-desktop.md) para criar relatórios otimizados para dispositivos móveis, possivelmente com o [elemento visual personalizado do Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) em vez dos KPIs e relatórios móveis do SSRS.
1. Reavalie a utilização do campo incorporado **UserID** nos relatórios. Se utilizar o **UserID** para proteger os dados do relatório, deverá compreender que, para os relatórios paginados (quando alojados no serviço Power BI), será devolvido o Nome Principal de Utilizador (UPN). Assim, em vez de devolver o nome da conta NT, por exemplo, _AW\mblythe_, o campo incorporado devolverá algo como _m.blythe&commat;adventureworks.com_. Terá de rever as definições dos conjuntos de dados e, possivelmente, os dados de origem. Uma vez revistos e publicados, recomendamos que teste cuidadosamente os relatórios para garantir que as permissões dos dados funcionam conforme o esperado.
1. Reavalie a utilização do campo incorporado **ExecutionTime** nos relatórios. Para os relatórios paginados (quando alojados no serviço Power BI), o campo incorporado devolve a data/hora na _Hora Universal Coordenada (ou UTC)_ . Pode afetar os valores predefinidos dos parâmetros do relatório e as etiquetas da hora de execução do relatório (normalmente, adicionadas aos rodapés do relatório).
1. Se a sua origem de dados for o SQL Server (no local), verifique se os relatórios não estão a utilizar visualizações de mapas. A visualização de mapa depende dos tipos de dados espaciais do SQL Server e estes não são suportados pelo gateway. Para obter mais informações, veja [Orientação para a obtenção de dados para relatórios paginados (tipos de dados complexos do SQL Server)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Certifique-se de que os seus autores de relatórios têm o [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md) instalado e de que as versões posteriores poderão ser facilmente distribuídas em toda a sua organização.

## <a name="migration-stage"></a>Fase de migração

Depois de preparar o ambiente e os relatórios do Power BI, está pronto para a fase de _Migração_.

Existem duas opções de migração: _manual_ e _automática_. A migração manual é adequada para um pequeno número de relatórios ou para relatórios que necessitem de modificações antes da migração. A migração automática é adequada para migrar um grande número de relatórios.

### <a name="manual-migration"></a>Migração manual

Qualquer pessoa com permissão para aceder à instância do SSRS e à área de trabalho do Power BI pode migrar relatórios para o Power BI manualmente. Eis os passos a seguir:

1. Abra o portal do SSRS que contém os relatórios que pretende migrar.
1. Transfira cada definição de relatório e guarde os ficheiros .rdl localmente.
1. Abra _a versão mais recente_ do Power BI Report Builder e ligue ao serviço Power BI com as suas credenciais do Azure AD.
1. Abra cada relatório no Power BI Report Builder e, em seguida:
   1. Verifique se todas as origens de dados e conjuntos de dados estão incorporados na definição de relatório e se são [origens de dados suportadas](../paginated-reports/paginated-reports-data-sources.md).
   1. Pré-visualize o relatório para garantir que é composto corretamente.
   1. Selecione _Guardar Como_ e, em seguida, selecione _serviço Power BI_.
   1. Selecione a área de trabalho que conterá o relatório.
   1. Confirme se o relatório é guardado. Se algumas funcionalidades na estrutura do seu relatório ainda não forem suportadas, não será possível guardar. Será notificado dos motivos. Terá depois de rever o design do relatório e tentar guardá-lo novamente.

### <a name="automated-migration"></a>Migração automatizada

Existem duas opções de migração automatizada. Pode utilizar:

- A Ferramenta de Migração de RDL
- As APIs disponíveis publicamente para SSRS e Power BI

A [Ferramenta de Migração de RDL](#migration-tool) já foi descrita neste artigo.

Também pode utilizar as APIs publicamente disponíveis para SSRS e Power BI para automatizar a migração dos seus conteúdos. Apesar de a Ferramenta de Migração de RDL já utilizar estas APIs, pode desenvolver uma ferramenta personalizada em função dos seus requisitos próprios.

Para obter mais informações sobre as APIs, veja:

- [Referência da API REST do Power BI](../developer/automation/rest-api-reference.md)
- [APIs REST do SQL Server Reporting Services](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Fase de pós-migração

Depois de efetuar a migração com êxito, estará pronto para a fase de _Pós-migração_. Esta fase consiste em efetuar uma série de tarefas pós-migração para garantir que tudo funciona correta e eficientemente.

### <a name="configure-data-sources"></a>Configurar origens de dados

Após os relatórios serem migrados para o Power BI, terá de garantir que as respetivas origens de dados estão corretamente configuradas. Pode implicar a atribuição a origens de dados de gateway e [o armazenamento seguro de credenciais de origens de dados](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication). Essas ações não são efetuadas pela Ferramenta de Migração de RDL.

### <a name="review-report-performance"></a>Rever o desempenho dos relatórios

Recomendamos vivamente que conclua as seguintes ações para garantir a melhor experiência possível para os utilizadores de relatórios:

1. Teste os relatórios em cada [browser suportado pelo Power BI](../power-bi-browsers.md) para confirmar se o relatório é composto corretamente.
1. Execute testes para comparar os tempos de composição dos relatórios no SSRS e no Power BI. Verifique se os relatórios do Power BI são compostos dentro de um tempo que seja aceitável.
1. Se os relatórios do Power BI não forem carregados devido a memória insuficiente, aloque [recursos adicionais à capacidade Premium do Power BI](../service-admin-premium-workloads.md#paginated-reports).
1. Para relatórios com tempos de composição prolongados, considere fazer com que o Power BI os entregue aos utilizadores de relatórios como [subscrições de e-mail com anexos de relatórios](../consumer/paginated-reports-subscriptions.md).
1. Para relatórios do Power BI baseados em conjuntos de dados do Power BI, reveja as estruturas dos modelos para garantir que estão totalmente otimizados.

### <a name="reconcile-issues"></a>Reconciliar problemas

A fase de Pós-migração é crucial para reconciliar eventuais problemas e dar resposta a questões de desempenho. Adicionar a carga de trabalho de relatórios paginados a uma capacidade pode contribuir para um desempenho mais lento, para relatórios paginados _e outros conteúdos_ armazenados na capacidade.

Para obter mais informações sobre estes problemas, incluindo passos específicos para os compreender e mitigar, veja os seguintes artigos:

- [Otimizar as capacidades Premium](../service-premium-capacity-optimize.md)
- [Monitorizar as capacidades Premium com a aplicação](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [O que são relatórios paginados no Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Orientação para a obtenção de dados para relatórios paginados](report-paginated-data-retrieval.md)
- [Quando utilizar os relatórios paginados no Power BI](report-paginated-or-power-bi.md)
- [Relatórios paginados no Power BI: Perguntas Frequentes](../paginated-reports/paginated-reports-faq.md)
- [Perguntas Frequentes do Power BI Premium](../service-premium-faq.md)
- [Ferramenta de Migração de RDL](https://github.com/microsoft/RdlMigration)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)

Os parceiros do Power BI estão disponíveis para ajudar a sua organização a efetuar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
