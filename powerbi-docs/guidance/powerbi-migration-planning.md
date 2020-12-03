---
title: Planear a implementação para migrar para o Power BI
description: Orientação sobre como planear a implementação ao migrar para o Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: f161819b6e26c197bacc5534b5abfb426d612624
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419228"
---
# <a name="plan-deployment-to-migrate-to-power-bi"></a>Planear a implementação para migrar para o Power BI

Este artigo descreve a **Fase 2**, que diz respeito ao planeamento da migração para uma solução do Power BI única.

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Imagem a mostrar as fases de uma migração do Power BI. A Fase 2 está realçada neste artigo.":::

> [!NOTE]
> Para obter uma explicação completa da imagem acima, veja o artigo [Power BI migration overview](powerbi-migration-overview.md) (Descrição geral da migração do Power BI).

O foco da Fase 2 consiste em definir como os requisitos definidos na Fase 1 são utilizados para migrar uma solução para o Power BI.

O resultado da Fase 2 inclui o máximo possível de decisões específicas para orientar o processo de implementação.

A tomada de decisões desta natureza é um processo iterativo e não linear. Já terá ocorrido algum planeamento nos [passos de pré-migração](powerbi-migration-pre-migration-steps.md). As aprendizagens obtidas a partir de uma prova de conceito (descrita na [Fase 3](powerbi-migration-proof-of-concept.md)) podem ocorrer em paralelo com o planeamento de implementação. Mesmo durante a criação da solução (descrito na [Fase 4](powerbi-migration-create-validate-content.md)), podem surgir informações adicionais que influenciam as decisões de implementação.

> [!IMPORTANT]
> As Fases 1 a 5 representam atividades relacionadas com uma solução específica. Existem decisões e atividades ao nível organizacional/de inquilino que afetam o processo ao nível da solução. Algumas dessas atividades de planeamento de nível superior são abordadas no artigo [Descrição geral da migração do Power BI](powerbi-migration-overview.md). Quando adequado, adie para as decisões de nível organizacional para obter eficiência e consistência.

> [!TIP]
> Os tópicos analisados neste artigo também se aplicam a um projeto de implementação do Power BI padrão.

## <a name="choose-power-bi-product"></a>Escolher o produto Power BI

Uma das primeiras decisões é escolher o produto Power BI. É uma decisão entre o [serviço Power BI](../fundamentals/power-bi-service-overview.md) ou o [Power BI Report Server](../report-server/get-started.md). Depois de o conteúdo ser publicado, ficarão disponíveis muitas opções adicionais como a incorporação, a entrega móvel e as subscrições de e-mail.

Para obter mais informações sobre considerações de arquitetura, veja a **Fase 3** do [documento técnico sobre planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP).

> [!CAUTION]
> Se quiser confiar na utilização dos ficheiros do Power BI Desktop armazenados num sistema de ficheiros, tenha em atenção que não é uma abordagem ideal. A utilização do serviço Power BI (ou Power BI Report Server) tem vantagens significativas para a segurança, a distribuição de conteúdos e a colaboração. A capacidade de auditar e monitorizar atividades também é ativada pelo serviço Power BI.

## <a name="decide-on-workspace-management-approach"></a>Decidir sobre a abordagem de gestão de áreas de trabalho

As [áreas de trabalho](../collaborate-share/service-new-workspaces.md) são um conceito central do serviço Power BI, o que torna a gestão de áreas de trabalho um aspeto importante do planeamento. Eis algumas questões a colocar:

- É necessária uma nova área de trabalho para esta nova solução?
- Será necessário separar as áreas de trabalho para acomodar o desenvolvimento, o teste e a produção?
- As áreas de trabalho separadas serão utilizadas para dados e relatórios ou será suficiente uma área de trabalho única? As áreas de trabalho separadas têm várias vantagens, especialmente para proteger os conjuntos de dados. Quando necessário, podem ser geridas separadamente dos utilizadores que publicam relatórios.
- Quais são os requisitos de segurança para a área de trabalho? Influencia o planeamento de [funções da área de trabalho](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Se uma aplicação for utilizada por consumidores de conteúdos, as [permissões para a aplicação](../collaborate-share/service-create-distribute-apps.md#publish-your-app) serão geridas separadamente da área de trabalho. Diferentes permissões para visualizadores de aplicações permitem flexibilidade adicional para atender aos requisitos de segurança para consumidores só de leitura de relatórios ou dashboards.
- Os grupos existentes podem ser utilizados para proteger o novo conteúdo? São suportados grupos do Microsoft 365 e do Azure Active Directory. Quando alinhada com os processos existentes, a utilização de grupos torna a gestão de permissões mais fácil do que as atribuições a utilizadores individuais.
- Existem considerações de segurança relacionadas com utilizadores convidados externos? Poderá ser necessário trabalhar com o seu administrador do Azure Active Directory e do Power BI para configurar o [acesso de utilizador convidado](../admin/service-admin-azure-ad-b2b.md).

> [!TIP]
> Considere criar uma área de trabalho para uma atividade ou projeto empresarial específico. Poderá querer começar a estruturar áreas de trabalho com base na sua estrutura organizacional (como uma área de trabalho por departamento), mas esta abordagem costuma tornar-se demasiado extensa.

## <a name="determine-how-content-will-be-consumed"></a>Determinar como o conteúdo será consumido

É útil compreender como os consumidores de uma solução preferem ver relatórios e dashboards. Eis algumas questões a colocar:

- Uma [aplicação Power BI](../consumer/end-user-apps.md) (que é composta por relatórios e dashboards de uma área de trabalho única) é a melhor forma de fornecer conteúdos aos consumidores ou o acesso direto a uma área de trabalho é suficiente para os visualizadores de conteúdos?
- Determinados relatórios e dashboards serão incorporados noutro local, como o [Teams](../collaborate-share/service-embed-report-microsoft-teams.md), o [SharePoint Online](../collaborate-share/service-embed-report-spo.md) ou um [ site ou portal seguro](../collaborate-share/service-embed-secure.md)?
- Os consumidores irão aceder ao conteúdo através de [dispositivos móveis](../consumer/mobile/mobile-apps-for-mobile-devices.md)? Os requisitos para entregar relatórios a dispositivos com fator de forma pequeno irão influenciar as [decisões de estrutura do relatório](../create-reports/desktop-create-phone-report.md).

## <a name="decide-if-other-content-may-be-created"></a>Decidir se outro conteúdo pode ser criado

Existem várias decisões importantes para tomar sobre permitir que os consumidores criem novos conteúdos, como:

- Os consumidores terão permissão para criar novos relatórios a partir do conjunto de dados publicado? Esta capacidade pode ser ativada ao atribuir a [permissão de criação](../connect-data/service-datasets-build-permissions.md) de conjuntos de dados a um utilizador.
- Se os consumidores quiserem personalizar um relatório, poderão [guardar uma cópia](../connect-data/service-datasets-copy-reports.md) do mesmo e personalizá-lo para dar resposta às respetivas necessidades?

> [!CAUTION]
> Embora a funcionalidade _Guardar uma cópia_ seja útil, deverá ser utilizada com cuidado quando o relatório incluir determinadas mensagens de gráficos ou de cabeçalho/rodapé. Como os logótipos, os ícones e as mensagens textuais estão frequentemente relacionados com requisitos de imagem corporativa ou conformidade regulamentar, é importante controlar cuidadosamente como são entregues e distribuídos. Se a funcionalidade _Guardar uma cópia_ for utilizada, mas as mensagens de gráficos ou de cabeçalho/rodapé originais permanecerem inalteradas pelo novo autor, isso poderá resultar em confusão sobre quem produziu o relatório. Também pode reduzir o significado da imagem corporativa.

## <a name="evaluate-needs-for-premium-capacity"></a>Avaliar as necessidades da capacidade Premium

Estão disponíveis capacidades adicionais quando uma área de trabalho é armazenada numa [capacidade Premium](../admin/service-premium-what-is.md). Eis diversos motivos pelos quais as áreas de trabalho na capacidade Premium podem ser vantajosas:

- O conteúdo pode ser acedido por consumidores que não têm uma licença do Power BI Pro.
- Suporte para grandes conjuntos de dados.
- Suporte para atualizações de dados mais frequentes.
- Suporte à utilização do conjunto de funcionalidades dos fluxos de dados completo.
- Funcionalidades empresariais, incluindo pipelines de implementação e o ponto final XMLA.
- Suporte para relatórios paginados (quando a carga de trabalho está ativada).

## <a name="determine-data-acquisition-method"></a>Determinar o método de aquisição de dados

Os dados exigidos por um relatório podem influenciar várias decisões. Eis algumas questões a colocar:

- É possível utilizar um [conjunto de dados partilhado](../connect-data/service-datasets-share.md) do Power BI existente ou a criação de um novo conjunto de dados de Power BI é adequada para esta solução?
- Um conjunto de dados partilhado existente precisa de ser aumentado com novos dados ou medidas para dar resposta às necessidades adicionais?
- Que [modo de armazenamento de dados](../transform-model/desktop-storage-mode.md) será mais adequado? As opções incluem a Importação, o DirectQuery, o Modelo Composto ou a Ligação em Direto.
- As [agregações](../transform-model/desktop-aggregations.md) devem ser utilizadas para melhorar o desempenho de consultas?
- Será a criação de um [fluxo de dados](../transform-model/dataflows/dataflows-introduction-self-service.md) útil e poderá servir como origem para vários conjuntos de dados?
- Será necessário registar uma nova [origem de dados de gateway](../connect-data/service-gateway-data-sources.md)?

## <a name="decide-where-original-content-will-be-stored"></a>Decidir onde o conteúdo original será armazenado

Além de planear o destino de implementação de destino, também é importante planear onde o conteúdo original (ou origem) será armazenado, como:

- Especificar uma localização aprovada para armazenar os ficheiros do Power BI Desktop (.pbix) originais. O ideal é que esta localização esteja disponível apenas para as pessoas que editam o conteúdo. Deve estar alinhada com a forma como a segurança é configurada no serviço Power BI.
- Utilizar uma localização para os ficheiros do Power BI Desktop originais que inclua o histórico de controlo de versões ou o controlo de origem. O controlo de versões permite que o autor do conteúdo reverta para uma versão anterior do ficheiro, se for necessário. O OneDrive para Empresas ou o SharePoint funcionam bem para esta finalidade.
- Especificar uma localização aprovada para armazenar dados de origens não centralizadas, como ficheiros simples ou ficheiros do Excel. Deverá ser um caminho a que qualquer um dos autores do conjunto de dados poderá aceder sem erros e com uma cópia de segurança criada regularmente.
- Especificar uma localização aprovada para os conteúdos exportados do serviço Power BI. O objetivo é garantir que a segurança definida no serviço Power BI não é inadvertidamente contornada.

> [!IMPORTANT]
> Especificar uma localização protegida para ficheiros do Power BI Desktop originais é particularmente importante quando estes contêm dados importados.

## <a name="assess-the-level-of-effort"></a>Avaliar o nível de esforço

Quando existem informações suficientes disponíveis nos requisitos (que foram descritos na [Fase 1](powerbi-migration-requirements.md)) e no processo de planeamento da implementação da solução, é possível avaliar o nível de esforço. Assim, é possível formular um plano de projeto com tarefas, linha cronológica e responsabilidade.

> [!TIP]
> Os custos de mão de obra (salários) estão normalmente entre as despesas mais altas na maioria das organizações. Embora possa ser difícil estimar com precisão, as melhorias de produtividade têm um excelente retorno sobre o investimento (ROI).

## <a name="next-steps"></a>Passos seguintes

No [próximo artigo desta série de migração do Power BI](powerbi-migration-proof-of-concept.md), saiba mais sobre a Fase 3, que consiste na realização de uma prova de conceito para atenuar o risco e abordar problemas desconhecidos o mais cedo possível ao migrar para o Power BI.

Outros recursos úteis incluem:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Estão disponíveis parceiros do Power BI experientes para ajudar a sua organização a efetuar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).