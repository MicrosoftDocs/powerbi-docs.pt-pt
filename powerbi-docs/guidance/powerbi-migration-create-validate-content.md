---
title: Criar conteúdo para migrar para o Power BI
description: Orientações sobre como criar e validar conteúdo ao migrar para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a12a320b061967e9201e3513e504277a9df586b4
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803507"
---
# <a name="createcontenttomigratetopowerbi"></a>Criar conteúdo para migrar para o Power BI

Este artigo descreve a **Fase 4**, que diz respeito à criação e validação de conteúdo ao migrar para o Power BI.

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Imagem a mostrar as fases de uma migração do Power BI. A Fase 4 está realçada neste artigo.":::

> [!NOTE]
> Para obter uma explicação completa sobre o gráfico acima, veja [Descrição geral da migração do Power BI](powerbi-migration-overview.md).

O foco da Fase 4 é a execução do trabalho em si, para converter a prova de conceito (POC) numa solução pronta para produção.

O resultado desta fase é uma solução do Power BI que foi validada numa área de trabalho de desenvolvimento e está pronta para a implementação na produção.

> [!TIP]
> A maioria dos tópicos discutidos neste artigo também se aplicam a um projeto de implementação do Power BI padrão.

## <a name="create-the-production-solution"></a>Criar a solução de produção

Neste momento, a mesma pessoa que procedeu à POC pode continuar com a produção da solução do Power BI pronta para produção. Pode também estar envolvido alguém diferente. Se as linhas cronológicas não forem comprometidas, será uma boa ideia envolver as pessoas que serão responsáveis pelo desenvolvimento de Power BI no futuro. Deste modo, podem aprender de forma ativa.

> [!IMPORTANT]
> Reutilize ao máximo o trabalho da POC.

### <a name="develop-new-import-dataset"></a>Desenvolver um novo conjunto de dados de importação

Pode optar por criar um conjunto de dados de Importação novo quando um conjunto de dados existente do Power BI ainda não responde às suas necessidades ou se não puder ser melhorado para responder às mesmas.

Idealmente, considere desassociar o trabalho de desenvolvimento para obter dados e relatórios logo desde o princípio. [Desassociar dados e relatórios](report-separate-from-model.md) facilitará a separação do trabalho e as permissões quando pessoas diferentes são responsáveis pela modelagem de dados e relatórios. Torna a abordagem mais dimensionável e incentiva a reutilização dos dados.

As atividades essenciais relacionadas com o desenvolvimento de conjuntos de dados de Importação incluem:

- [Adquirir dados](../connect-data/desktop-quickstart-connect-to-data.md) de uma ou mais origens de dados (que podem ser um fluxo de dados do Power BI).
- [Formar, combinar e preparar](../connect-data/desktop-shape-and-combine-data.md) os dados.
- Criar o [modelo do conjunto de dados](../transform-model/desktop-modeling-view.md), incluindo as [tabelas de datas](../transform-model/desktop-date-tables.md).
- Criar e verificar as [relações do modelo](../transform-model/desktop-create-and-manage-relationships.md).
- Definir as [medidas](../transform-model/desktop-measures.md).
- Configurar a [segurança ao nível da linha](../admin/service-admin-rls.md), se necessário.
- Configurar sinónimos e [otimizar as Perguntas e Respostas](../natural-language/q-and-a-best-practices.md).
- Planear a escalabilidade, o desempenho e a simultaneidade, que podem influenciar as decisões sobre os modos de armazenamento de dados, como utilizar um [Modelo composto](../transform-model/desktop-composite-models.md) ou [agregações](../transform-model/desktop-aggregations.md).

> [!TIP]
> Se tiver diferentes ambientes de desenvolvimento/teste/produção, considere [parametrizar](/power-query/power-query-query-parameters) as origens de dados. Tornará a implementação, descrita na [Fase 5](powerbi-migration-deploy-support-monitor.md), significativamente mais fácil.

### <a name="develop-new-reports-and-dashboards"></a>Desenvolver novos relatórios e dashboards

As atividades essenciais relacionadas com o desenvolvimento de relatórios ou dashboards do Power BI incluem:

- Decidir utilizar uma Ligação em Direto a um modelo de dados existente ou criar um novo modelo de dados
- Ao criar um novo modelo de dados, decidir o [modo de armazenamento de dados](../transform-model/desktop-storage-mode.md) das tabelas do modelo (Importação, DirectQuery ou Composto).
- Decidir qual é a melhor ferramenta de visualização de dados para cumprir os requisitos: Power BI Desktop, Paginated Report Builder ou Excel.
- Decidir quais são os [melhores elementos visuais](../consumer/end-user-visual-type.md) para mostrar a informação que o relatório tem de apresentar e para abordar as perguntas que têm de ser respondidas pelo mesmo.
- Garantir que todos os elementos visuais apresentam terminologia empresarial clara, concisa e inteligível.
- Cumprir os requisitos de interatividade.
- Ao utilizar a Ligação em Direto, adicionar [medidas ao nível do relatório](../transform-model/desktop-tutorial-create-measures.md).
- Criar um [dashboard](../create-reports/service-dashboards.md) no serviço Power BI, especialmente quando os consumidores desejam uma maneira fácil de monitorizar as principais métricas.

> [!NOTE]
> Muitas destas decisões serão feitas nas fases principais do planeamento ou na POC técnica.

## <a name="validate-the-solution"></a>Validar a solução

Existem quatro aspetos principais para a validação de uma solução do Power BI:

1. Precisão dos dados
2. Segurança
3. Funcionalidade
4. Desempenho

### <a name="validate-data-accuracy"></a>Validar a precisão dos dados

Durante a migração só terá de realizar a seguinte ação uma vez: assegurar que os dados no novo relatório correspondem ao que é apresentado no relatório legado. Ou, se existir alguma diferença, ser capaz de explicar a sua existência. É mais comum do que imagina encontrar um erro na solução legada que é resolvido na nova solução.

Como parte dos esforços contínuos de validação de dados, o novo relatório, normalmente, precisará de uma verificação cruzada com o sistema de origem original. Idealmente, esta validação ocorre de forma reproduzível sempre que publica uma alteração no relatório.

### <a name="validate-security"></a>Validar a segurança

Existem dois aspetos principais a serem considerados ao validar a segurança:

- Permissões dos dados
- Acesso aos conjuntos de dados, aos relatórios e aos dashboards

Num conjunto de dados de Importação, as permissões dos dados são aplicadas ao definir a [segurança ao nível da linha](../admin/service-admin-rls.md) (RLS). Também é possível que as permissões dos dados sejam aplicadas pelo sistema de origem ao utilizar o modo de armazenamento DirectQuery (possivelmente com um [início de sessão único](../connect-data/service-gateway-sso-overview.md)).

Principais formas de conceder acesso ao conteúdo do Power BI:

- [Funções da área de trabalho](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (para editores e visualizadores de conteúdo).
- [Permissões da aplicação](../collaborate-share/service-create-distribute-apps.md#publish-your-app) aplicadas a um conjunto agrupado de conteúdo da área de trabalho (para visualizadores).
- [Partilhar](../collaborate-share/service-share-dashboards.md) um relatório ou dashboard individual (para visualizadores).

> [!TIP]
> Recomendamos que dê formação aos autores de conteúdo sobre como gerir a segurança de forma eficaz. Também é importante ter testes, auditorias e uma monitorização robustas em vigor.

### <a name="validate-functionality"></a>Validar a funcionalidade

É a altura de verificar novamente os detalhes dos conjuntos de dados, tal como os nomes dos campos, a formatação, a ordenação e o comportamento de resumo predefinido. Também devem ser verificadas as funcionalidades interativas de relatório, como [segmentações](../visuals/power-bi-visualization-slicers.md), [desagregação](../consumer/end-user-drill.md), [pormenorização](../create-reports/desktop-drillthrough.md), [expressões](../create-reports/desktop-conditional-format-visual-titles.md), [botões](../create-reports/desktop-buttons.md) ou [marcadores](../create-reports/desktop-bookmarks.md).

Durante o processo de desenvolvimento, a solução do Power BI deve ser publicada numa área de trabalho de desenvolvimento no serviço Power BI de forma regular. Verifique se todas as funcionalidades funcionam conforme o esperado no serviço, tal como a composição de elementos visuais personalizados. Também é uma boa altura para fazer testes adicionais. Teste a [atualização agendada](../connect-data/refresh-scheduled-refresh.md), as [Perguntas e Respostas](../consumer/end-user-q-and-a.md) e qual é a aparência dos relatórios e dos dashboards num [dispositivo móvel](../consumer/mobile/mobile-apps-for-mobile-devices.md).

### <a name="validate-performance"></a>Validar o desempenho

O desempenho da solução do Power BI é importante para a experiência dos consumidores. A maioria dos relatórios deve apresentar elementos visuais em menos de 10 segundos. Se tiver relatórios que demorem mais tempo para carregar, pare e reconsidere o que pode estar a contribuir para os atrasos. O desempenho dos relatórios deve ser avaliado regularmente no serviço Power BI e também no Power BI Desktop.

Muitos problemas de desempenho devem-se a [DAX (Data Analysis eXpressions)](../transform-model/desktop-quickstart-learn-dax-basics.md) inadequadas, uma má conceção dos conjuntos de dados ou uma estrutura dos relatórios de qualidade inferior (por exemplo, tentar compor demasiados elementos visuais numa única página). Problemas de ambiente técnico, tal como a rede, um gateway de dados sobrecarregado ou o modo como uma capacidade Premium está configurada também podem contribuir para problemas de desempenho. Para obter mais informações, veja o [Guia de otimização para o Power BI](power-bi-optimization.md) e [Resolver problemas com o desempenho dos relatórios no Power BI](report-performance-troubleshoot.md).

## <a name="document-the-solution"></a>Documentar a solução

Existem dois tipos principais de documentação que são úteis para uma solução do Power BI:

- Documentação dos conjuntos de dados
- Documentação dos relatórios

A documentação pode ser armazenada numa localização que possa ser facilmente acedida pelo público-alvo. Opções comuns:

- **Num site do SharePoint:** pode existir um site do SharePoint para o Centro de Excelência ou um site interno da comunidade do Power BI.
- **Na aplicação:** os URLs podem ser configuradas ao publicar uma aplicação do Power BI para direcionar o consumidor para obter mais informações.
- **Em ficheiros individuais do Power BI Desktop:** elementos de modelo, como tabelas e colunas, podem definir uma descrição. Estas descrições aparecem como descrições no painel **Campos** ao criar os relatórios.

> [!TIP]
> Se criar um site para servir como hub para a documentação relacionada do Power BI, considere [personalizar o menu Obter Ajuda](../admin/service-admin-portal.md#publish-get-help-information) com a localização do URL.

### <a name="create-dataset-documentation"></a>Criar a documentação dos conjuntos de dados

A documentação dos conjuntos de dados destina-se aos utilizadores que vão gerir o conjunto de dados no futuro. É útil incluir:

- As decisões de design tomadas e motivos.
- Quem é o proprietário, faz a manutenção e certifica os conjuntos de dados.
- Os requisitos de atualização dos dados.
- As regras personalizadas de negócio definidas nos conjuntos de dados.
- Os requisitos específicos dos conjuntos de dados ou da privacidade dos dados.
- As futuras necessidades de manutenção.
- Os problemas conhecidos abertos ou itens pendentes deferidos.

Também pode optar por criar um registo de alterações que resume as alterações mais importantes realizadas ao conjunto de dados ao longo do tempo.

### <a name="create-report-documentation"></a>Criar a documentação dos relatórios

A documentação dos relatórios, que normalmente é estruturada como instruções destinadas aos consumidores de relatório, pode ajudá-los a tirar mais proveito dos relatórios e dos dashboards. Um pequeno tutorial em vídeo por norma funciona bem.

Também pode optar por incluir documentação dos relatórios adicional numa página oculta do relatório, que pode incluir as decisões de design e um registo das alterações.

## <a name="next-steps"></a>Passos seguintes

No [próximo artigo desta série de migração do Power BI](powerbi-migration-deploy-support-monitor.md), ficará a saber mais sobre a fase 5, que diz respeito à implementação, ao suporte e à monitorização de conteúdo ao migrar para o Power BI.

Outros recursos úteis:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre como planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Os parceiros do Power BI experientes estão disponíveis para ajudar a sua organização a realizar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
