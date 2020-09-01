---
title: Implementar no Power BI
description: Orientações sobre a implementação, o suporte e a monitorização de conteúdo ao migrar para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 58eb9af4975c0afeb12a71a880711ddd73e64d50
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803496"
---
# <a name="deploy-to-power-bi"></a>Implementar no Power BI

Este artigo descreve a **Fase 5**, que diz respeito à implementação, ao suporte e à monitorização de conteúdo ao migrar para o Power BI.

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Imagem a mostrar as fases de uma migração do Power BI. A Fase 5 está realçada neste artigo.":::

> [!NOTE]
> Para obter uma explicação completa sobre o gráfico acima, veja [Descrição geral da migração do Power BI](powerbi-migration-overview.md).

O foco principal da Fase 5 é implementar a nova solução de Power BI na produção.

O resultado desta fase é uma solução de produção pronta para ser utilizada pela empresa. Ao trabalhar com um método ágil, é aceitável ter algumas melhorias planeadas que serão entregues numa iteração futura. O suporte e a monitorização também são importantes nesta fase e de forma contínua.

> [!TIP]
> Exceto para a execução em paralelo e a desativação dos relatórios legados, que são discutidos abaixo, os tópicos abordados neste artigo também se aplicam aos projetos de implementação do Power BI padrão.

## <a name="deploy-to-test-environment"></a>Implementar no ambiente de teste

Geralmente, existe um ambiente de teste para soluções geridas pela equipa de TI ou soluções que são essenciais para a produtividade do negócio. O ambiente de teste encontra-se entre o desenvolvimento e a produção, e não é necessário para todas as soluções do Power BI. Uma área de trabalho de teste pode servir como uma localização estável separada do desenvolvimento, para que o teste de aceitação do utilizadores (UAT) ocorra antes da versão para produção.

Se o conteúdo tiver sido publicado numa área de trabalho com capacidade Premium, os [pipelines de implementação](../create-reports/deployment-pipelines-overview.md) poderão simplificar o processo de implementação em áreas de trabalho de desenvolvimento, teste e produção. Como alternativa, a publicação pode ser feita manualmente ou com [scripts do PowerShell](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/).

### <a name="deploy-to-test-workspace"></a>Implementar na área de trabalho de teste

As principais atividades durante uma implementação na área de trabalho de teste normalmente incluem:

- **Cadeias de ligação e parâmetros:** ajuste as cadeias de ligação dos conjuntos de dados se a origem de dados for diferente entre o desenvolvimento e o teste. Pode utilizar a [parametrização](../connect-data/service-parameters.md) para gerir efetivamente as cadeias de ligação.
- **Conteúdo da área de trabalho:** publique conjuntos de dados e relatórios na área de trabalho de teste e crie dashboards.
- **Aplicação:** publique uma [aplicação](../consumer/end-user-apps.md) ao utilizar o conteúdo da área de trabalho de teste, se fizer parte do processo do UAT. Normalmente, as permissões para a aplicação são restringidas a um pequeno número de pessoas envolvidas no UAT.
- **Atualização de dados:** [agende a atualização](../connect-data/refresh-scheduled-refresh.md) de qualquer conjunto de dados de Importação para o período em que o UAT está a decorrer ativamente.
- **Segurança:** atualize ou verifique as [funções da área de trabalho](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). O teste do acesso à área de trabalho inclui um pequeno número de pessoas que estão envolvidas no UAT.

> [!NOTE]
> Para obter mais informações sobre as opções de implementação para desenvolvimento, teste e produção, veja a Secção 9 do [Documento técnico sobre como planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP).

### <a name="conduct-user-acceptance-testing"></a>Realizar testes de aceitação de utilizadores

Normalmente, o UAT envolve utilizadores empresariais especialistas no assunto. Depois procederem à verificação, aprovam o novo conteúdo ao indicar que é preciso, cumpre os requisitos e pode ser implementado para consumo mais amplo por outros utilizadores.

A formalidade deste processo de UAT, incluindo as aprovações escritas, dependerá das práticas de gestão da mudança.

## <a name="deploy-to-production-environment"></a>Implementar num ambiente de produção

Existem várias considerações a ter em conta para a implementação no ambiente de produção.

### <a name="conduct-a-staged-deployment"></a>Realizar uma implementação faseada

Se estiver a tentar minimizar os riscos e a interrupção para os utilizadores ou se tiver outras preocupações, poderá optar por executar uma implementação faseada. A primeira implementação para produção pode envolver um grupo de utilizadores piloto mais pequeno. Com um grupo piloto, pode pedir ativamente feedback a esses utilizadores.

Expanda as permissões na área de trabalho de produção ou na aplicação gradualmente até que todos os utilizadores pretendidos tenham permissão para a nova solução do Power BI.

> [!TIP]
> Utilize o [Registo de Atividades do Power BI](../admin/service-admin-auditing.md) para entender como os consumidores estão a adotar e a utilizar a nova solução do Power BI.

### <a name="handle-additional-components"></a>Lidar componentes adicionais

Durante o processo de implementação, poderá ter de trabalhar com os administradores do Power BI para abordar outros requisitos necessários para dar suporte a toda a solução, como:

- **Manutenção do gateway:** pode ser necessário o registo de uma [nova origem de dados](../connect-data/service-gateway-data-sources.md) no gateway de dados.
- **Controladores e conectores de gateway:** uma nova origem de dados proprietária pode exigir a instalação de um novo controlador ou conector personalizado em cada servidor no cluster de gateway.
- **Criar uma nova capacidade Premium:** poderá utilizar uma [capacidade Premium](../admin/service-premium-capacity-manage.md) existente. Poderão também existir situações em que uma nova capacidade Premium seja necessária. Poderá ser o caso quando deseja separar propositadamente uma carga de trabalho departamental.
- **Configurar um fluxo de dados do Power BI:** as atividades de preparação de dados podem ser configuradas uma vez no [fluxo de dados do Power BI](../transform-model/service-dataflows-overview.md) com o Power Query Online, que ajuda a evitar a replicação do trabalho de preparação de dados para vários ficheiros diferentes do Power BI Desktop.
- **Registar um novo elemento visual organizacional:** o registo do [elemento visual organizacional](../developer/visuals/power-bi-custom-visuals-organization.md) pode ser feito no portal de administração para os elementos visuais personalizados que não tiveram origem no AppSource.
- **Definir conteúdo em destaque:** existe uma definição de inquilino que controla quem pode [destacar conteúdo](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/) na home page do serviço Power BI.
- **Configurar etiquetas de confidencialidade:** todas as [etiquetas de confidencialidade](../admin/service-security-data-protection-overview.md) estão integradas no Microsoft Information Protection.

### <a name="deploy-to-production-workspace"></a>Implementar numa área de trabalho de produção

As principais atividades durante uma implementação na área de trabalho de produção normalmente incluem:

- **Gestão da mudança:** se necessário, obtenha a aprovação para implementar e comunique a implementação à população de utilizadores que utiliza as práticas de gestão da mudança padrão. Poderá existir um período de gestão da mudança aprovado, durante o qual as implementações de produção são permitidas. Normalmente, aplica-se ao conteúdo gerido pela equipa de TI e, com menor frequência, ao conteúdo de gestão personalizada.
- **Plano de reversão:** com a migração, espera-se que seja a migração de uma nova solução pela primeira vez. Se o conteúdo já existir, será prudente ter um plano para reverter para a versão anterior, caso necessário. Ter versões anteriores de ficheiros do Power BI Desktop (com o controlo de versões do SharePoint ou do OneDrive) funciona bem para esta finalidade.
- **Cadeias de ligação e parâmetros:** ajuste as cadeias de ligação dos conjuntos de dados quando a origem de dados for diferente entre a fase de teste e de produção. Pode utilizar a [parametrização](/connect-data/service-parameters.md) eficazmente para esta finalidade.
- **Atualização de dados:** [Agende a atualização](../connect-data/refresh-scheduled-refresh.md) de qualquer conjunto de dados importado.
- **Conteúdo da área de trabalho:** publique conjuntos de dados e relatórios na área de trabalho de produção e crie dashboards. Se o conteúdo tiver sido publicado em áreas de trabalho com capacidade Premium, os [pipelines de implementação](../create-reports/deployment-pipelines-overview.md) poderão simplificar o processo de implementação em áreas de trabalho de desenvolvimento, teste e produção.
- **Aplicação:** se as aplicações fizerem parte da estratégia de distribuição de conteúdo, publique a [aplicação ](../consumer/end-user-apps.md) com o conteúdo da área de trabalho de produção.
- **Segurança:** atualize e verifique as [funções da área de trabalho](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) com base na estratégia de colaboração e de distribuição conteúdo.
- **Definições dos conjuntos de dados:** atualize e verifique as definições de cada conjunto de dados, incluindo:
  - [Endosso](../connect-data/service-datasets-certify.md) (como certificado ou promovido)
  - Ligação do gateway ou credenciais da origem de dados
  - Atualização agendada
  - [Perguntas das Perguntas e Respostas em destaque](../create-reports/service-q-and-a-create-featured-questions.md)
- **Definições dos relatórios e dashboards:** atualize e verifique as definições de cada relatório e dashboard. Definições mais importantes:
  - Descrição
  - Pessoa ou grupo contacto
  - [Etiqueta de confidencialidade](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
  - [Conteúdo em destaque](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **Subscrições:** se necessário, configure as subscrições de relatórios.

> [!IMPORTANT]
> Acabou de atingir um grande marco. Comemore o feito ao concluir a migração.

### <a name="communicate-with-users"></a>Comunicar com os utilizadores

Anuncie a nova solução aos consumidores. Indique-lhes onde podem encontrar o conteúdo, a documentação associada, as FAQs e os tutoriais. Para apresentar o novo conteúdo, considere organizar um tipo de sessão de almoço/aprendizagem ou prepare alguns vídeos a pedido.

Confirme que inclui instruções sobre como pedir ajuda, bem como enviar feedback.

### <a name="conduct-a-retrospective"></a>Realizar uma retrospetiva

Considere a realização de uma retrospetiva para examinar o que correu bem com a migração e o que poderia ser melhorado com a próxima migração.

## <a name="run-in-parallel"></a>Executar em paralelo

Em muitas situações, a nova solução será executada em paralelo à solução legada durante um período de tempo predeterminado. Vantagens da execução em paralelo:

- Redução dos riscos, especialmente se os relatórios forem considerados fundamentais para a atividade.
- Permite que os utilizadores tenham tempo de se habituar à nova solução do Power BI.
- Permite que as informações apresentadas no Power BI incluam referências cruzadas para os relatórios legados.

## <a name="decommission-the-legacy-report"></a>Desativar o relatório legado

No futuro, os relatórios migrados para o Power BI terão de ser desativados na plataforma de BI legada. A desativação dos relatórios legados pode ocorrer quando:

- O período de tempo predeterminado para a execução em paralelo, que deveria ter sido comunicado à população de utilizadores, expirar. É, normalmente, de 30 a 90 dias.
- Todos os utilizadores do sistema legado tiverem acesso à nova solução do Power BI.
- Já não existir nenhuma atividade significativa no relatório legado.
- Não ocorrerem problemas na nova solução do Power BI que possam afetar a produtividade do utilizador.

## <a name="monitor-the-solution"></a>Monitorizar a solução

Pode utilizar os eventos do [registo de atividades do Power BI](../admin/service-admin-auditing.md) para entender os padrões de utilização da nova solução (ou do [registo de execução](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view?view=sql-server-ver15) do conteúdo implementado no Power BI Report Server). A análise do registo de atividades pode ajudar a determinar se a utilização real difere das expetativas. Também pode confirmar que a solução tem um suporte adequado.

Veja a seguir algumas perguntas que podem ser respondidas ao examinar o registo de atividades:

- Com que frequência é visto o conteúdo?
- Quem está a ver o conteúdo?
- O conteúdo é normalmente visto através de uma aplicação ou de uma área de trabalho?
- A maioria dos utilizadores está a utilizar um browser ou uma aplicação móvel?
- Estão a ser utilizadas subscrições?
- Estão a ser criados novos relatórios com base nesta solução?
- O conteúdo está a ser atualizado frequentemente?
- Como é que a segurança está definida?
- Estão a ocorrer problemas regularmente, como falhas de atualização de dados?
- Estão a ocorrer atividades que suscitem preocupação (por exemplo, atividade de exportação significativa ou numerosas partilhas de relatórios individuais), o que pode significar a necessidade de formação adicional?

> [!IMPORTANT]
> Garanta que alguém analisa o registo de atividades regularmente. Capturá-lo e armazenar o histórico tem valor para fins de auditoria ou de conformidade. No entanto, o real valor está na execução de uma ação proativa.

## <a name="support-the-solution"></a>Suporte à solução

Embora a migração esteja concluída, o período após a migração é vital para resolver problemas e lidar com quaisquer preocupações relacionadas com o desempenho. Ao longo do tempo, a solução migrada provavelmente sofrerá alterações à medida que as necessidades do negócio evoluem.

O suporte tende a ocorrer de maneira diferente, dependendo de como o BI de gestão personalizada é gerido pela organização. Os utilizadores experientes do Power BI em todas as unidades de negócios geralmente atuam informalmente como suporte de primeira linha. Embora seja uma função informal, é vital e deve ser incentivada.

Ter um processo de suporte formal, formado por uma equipa de TI com pedidos de suporte, também é essencial para lidar com os pedidos de rotina direcionados ao sistema e para fins de escalamento.

Também pode ter um [Centro de Excelência (COE)](center-of-excellence-establish.md) que funcione como consultores internos que dão suporte, instruem e regem o Power BI na organização. Um COE pode ser responsável por gerir o conteúdo do Power BI útil num portal interno.

Por fim, deve ser claro para os consumidores de conteúdo quem devem contactar com perguntas sobre o conteúdo e ter um mecanismo para dar feedback sobre problemas ou melhorias.

## <a name="next-steps"></a>Passos seguintes

No [artigo final desta série](powerbi-migration-learn-from-customers.md), vai aprender com os clientes ao migrar para o Power BI.

Outros recursos úteis:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre como planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Os parceiros do Power BI experientes estão disponíveis para ajudar a sua organização a realizar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
