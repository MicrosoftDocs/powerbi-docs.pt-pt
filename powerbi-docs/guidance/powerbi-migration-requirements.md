---
title: Obter os requisitos para migrar para o Power BI
description: Orientação sobre como obter e priorizar os requisitos ao migrar para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: f96fa15981de8d86007c6e1fa768f95a77921280
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92680952"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>Obter os requisitos para migrar para o Power BI

Este artigo descreve a **Fase 1** , que diz respeito à obtenção e priorização dos requisitos ao migrar para o Power BI.

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="Imagem a mostrar as fases de uma migração do Power BI. A Fase 1 está realçada neste artigo.":::

> [!NOTE]
> Para obter uma explicação completa sobre o gráfico acima, veja [Descrição geral da migração do Power BI](powerbi-migration-overview.md).

A destaque da Fase 1 é a recolha de informações e o planeamento de uma solução individual que será migrada para o Power BI.

O resultado da Fase 1 inclui os requisitos detalhados que foram priorizados. No entanto, deve concluir as atividades adicionais nas Fase 2 e 3 para estimar totalmente o nível de esforço.

> [!IMPORTANT]
> As Fases 1 a 5 representam atividades relacionadas com uma solução específica. Existem decisões e atividades ao nível organizacional/de inquilino que afetam o processo ao nível da solução. Algumas dessas atividades de planeamento de nível superior são abordadas no artigo [Descrição geral da migração do Power BI](powerbi-migration-overview.md). Quando adequado, adie para as decisões de nível organizacional para obter eficiência e consistência.

> [!TIP]
> A maioria dos tópicos discutidos neste artigo também se aplicam a um projeto de implementação do Power BI padrão.

## <a name="compile-requirements"></a>Compilar os requisitos

O inventário dos artefactos de BI existentes, compilados nos [passos de pré-migração](powerbi-migration-pre-migration-steps.md), é a entrada para os requisitos da nova solução a ser criada no Power BI. A recolha dos requisitos diz respeito à compreensão do estado atual, bem como aos itens que os utilizadores gostariam de alterar ou refatorizar quando os relatórios são reformulados no Power BI. Os requisitos detalhados serão úteis para o planeamento da implementação da solução na [Fase 2](powerbi-migration-planning.md), durante a criação de uma prova de conceito na [Fase 3](powerbi-migration-proof-of-concept.md), e ao criar a solução pronta para produção na [Fase 4](powerbi-migration-create-validate-content.md).

### <a name="gather-report-requirements"></a>Obter os requisitos dos relatórios

Compile informações completas e de referência fácil sobre os relatórios, tais como:

- **Finalidade, público-alvo e ação esperada:** identifique a finalidade e o processo de negócio aplicáveis a cada relatório, bem como o público-alvo, o fluxo de trabalho analítico e a ação esperada a ser tomada pelos consumidores dos relatórios.
- **Como os consumidores utilizam o relatório:** considere a possibilidade de conversar com os consumidores do relatório existente para compreender exatamente o que estes fazem com o mesmo. Pode ficar a saber que determinados elementos do relatório podem ser eliminados ou melhorados na nova versão do Power BI. Este processo envolve um investimento de tempo adicional, mas é valioso para os relatórios críticos ou os relatórios utilizados com frequência.
- **Proprietário e especialista no assunto:** identifique o proprietário do relatório e qualquer especialista no assunto associado ao relatório ou ao domínio dos dados. Estes podem tornar-se nos proprietários do novo relatório de Power BI no futuro. Inclua todos os requisitos específicos de gestão de alterações (que normalmente diferem entre soluções geridas por TI e geridas por empresas), bem como aprovações e confirmações, que serão necessários quando as alterações forem realizadas no futuro.
- **Método de entrega de conteúdo:** esclareça quais as expectativas dos consumidores dos relatórios quanto à entrega de conteúdo. Pode ser a pedido, execução interativa, incorporada numa aplicação personalizada ou entrega com base num agendamento com uma subscrição por e-mail. Também podem existir requisitos para acionar notificações de alerta.
- **Necessidades de interatividade:** determine os requisitos de interatividade _necessários_ e _úteis_ , como filtros, desagregação ou pormenorização.
- **Origens de dados:** verifique se todas as origens de dados exigidas pelo relatório foram detetadas e se as necessidades de latência de dados (atualização dos dados) são compreendidas. Identifique os requisitos de dados históricos, tendências e instantâneos de dados de cada relatório, para que estes possam ser alinhados com os requisitos dos dados. A documentação da origem de dados também pode ser útil posteriormente ao executar a validação dos dados de um novo relatório com os dados de origem.
- **Requisitos de segurança:** esclareça os requisitos de segurança (como visualizadores permitidos, editores permitidos e quaisquer necessidades de segurança ao nível da linha), incluindo quaisquer exceções à segurança organizacional normal. Documente qualquer nível de confidencialidade de dados, privacidade de dados ou necessidades normativas/de conformidade.
- **Cálculos, KPIs e regras de negócio:** identifique e documente todos os cálculos, KPIs e regras de negócio atualmente definidos no relatório existente, para que possam ser alinhados com os requisitos dos dados.
- **Requisitos de utilização, esquema e estéticos:** identifique necessidades estéticas, de utilização e de esquema específicas relacionadas com os requisitos de agrupamento, classificação e visualizações dos dados e a visibilidade condicional. Inclua todas as considerações específicas relacionadas com a entrega de dispositivos móveis.
- **Necessidades de impressão e exportação:** determine se há requisitos específicos para impressão, exportação ou esquema de aspeto perfeito. Estas necessidades vão influenciar o tipo de relatório que poderá ser mais adequado (como um Power BI, Excel ou relatório paginado). Tenha atenção que os consumidores dos relatórios tendem a dar muita importância à forma como sempre fizeram as coisas, portanto, não se preocupe em desafiar a forma de pensar deles. Não se esqueça de falar em termos de _melhoramentos_ em vez de _alterações_ .
- **Riscos ou preocupações:** determine se há outros requisitos técnicos ou funcionais para os relatórios, bem como quaisquer riscos ou preocupações sobre as informações apresentadas nos mesmos.
- **Problemas abertos e itens de registos de tarefas pendentes:** identifique todas as manutenções futuras, problemas conhecidos ou pedidos adiados para adicionar ao registo de tarefas pendentes neste momento.

> [!TIP]
> Considere classificar os requisitos como _necessários_ ou _úteis_ . Frequentemente, os consumidores pedem tudo aquilo que poderão vir a precisar com antecedência pois acreditam que pode ser a única hipótese de fazer os pedidos. Além disso, ao estabelecer as prioridades em várias iterações, o registo de tarefas pendentes é disponibilizado aos intervenientes, o que ajuda na comunicação, tomada de decisões e acompanhamento de compromissos pendentes.

### <a name="gather-data-requirements"></a>Obter os requisitos dos dados

Compile informações detalhadas referentes aos dados, como:

- **Consultas existentes:** identifique se há consultas existentes do relatório ou procedimentos armazenados que possam ser utilizados por um [Modelo do DirectQuery](../connect-data/desktop-use-directquery.md) ou um [Modelo composto](../transform-model/desktop-composite-models.md), ou que possam ser convertidos num Modelo de importação.
- **Tipos de origens de dados:** compile os tipos de origens de dados necessários, incluindo as origens de dados centralizadas (como um armazém de dados empresarial), bem como as origens de dados não padrão (como ficheiros simples ou ficheiros do Excel que aumentam as origens de dados empresariais para fins de relatório). É igualmente importante localizar os estão as origens de dados, para fins de conectividade do [gateway de dados](../connect-data/service-gateway-onprem.md).
- **Estrutura e necessidades de limpeza de dados:** determine a estrutura de dados de cada origem de dados necessária e até que ponto as atividades de [limpeza de dados](../transform-model/desktop-query-overview.md) são necessárias.
- **Integração de dados** : avalie a forma como a integração de dados ser á processada quando existirem várias origens de dados e como as [relações](../transform-model/desktop-create-and-manage-relationships.md) podem ser definidas entre cada tabela de modelo. Identifique os elementos de dados específicos necessários para simplificar o modelo e [reduzir o tamanho](import-modeling-data-reduction.md).
- **Latência de dados aceitável:** determine as necessidades de latência de dados de cada origem de dados. Tal vai influenciar as decisões sobre qual o [modo de armazenamento de dados](../transform-model/desktop-storage-mode.md) a utilizar. Também é importante saber a frequência da atualização dos dados nas tabelas do modelo de Importação.
- **Volume e escalabilidade dos dados:** avalie as expectativas de volume dos dados, que terão em conta as decisões sobre o [suporte de modelos grandes](../admin/service-premium-large-models.md) e a reformulação do DirectQuery ou dos [Modelos compostos](../transform-model/desktop-composite-models.md). As considerações relacionadas com as necessidades de dados históricos também são de conhecimento essencial. Para conjuntos de dados maiores, também será necessária a determinação das regras de [atualização incremental dos dados](../admin/service-premium-incremental-refresh.md).
- **Medidas, KPIs e regras de negócio:** avalie as necessidades de medidas, KPIs e regras de negócio, uma vez que afetarão as decisões referentes a onde aplicar a lógica: no conjunto de dados ou no processo de integração de dados.
- **Dados globais e catálogo de dados:** considere se há problemas de dados globais que exigem atenção. Determine se a integração num catálogo de dados empresarial é apropriada para melhorar a deteção, aceder às definições ou produzir uma terminologia consistente aceite pela organização.
- **Segurança e privacidade dos dados:** determine se há considerações referentes à privacidade dos dados ou à segurança específicas para os conjuntos de dados, incluindo requisitos de [segurança ao nível da linha](../admin/service-admin-rls.md).
- **Problemas abertos e itens de registos de tarefas pendentes:** adicione todos os problemas conhecidos, defeitos de qualidade dos dados conhecidos, manutenção futura ou pedidos adiados para o registo de tarefas pendentes neste momento.

> [!IMPORTANT]
> A reutilização dos dados pode ser obtida com os [conjuntos de dados partilhados](../connect-data/service-datasets-share.md), que, opcionalmente, podem ser [certificados](../collaborate-share/service-endorse-content.md) para indicar a fiabilidade e melhorar a deteção. A reutilização da preparação de dados pode ser obtida com os [fluxos de dados](../transform-model/service-dataflows-overview.md) para reduzir a lógica repetitiva em vários conjuntos de dados. Os fluxos de dados também podem reduzir significativamente a carga nos sistemas de origem, pois os dados são recuperados com menor frequência. Desta forma, vários conjuntos de dados podem assim importar dados do fluxo de dados.

## <a name="identify-improvement-opportunities"></a>Identificar oportunidades de melhoramento

Na maioria das situações, ocorrem algumas modificações e melhorias. É raro ocorrer uma migração direta um-para-um sem qualquer refatorização ou melhoria. Três tipos de melhorias a considerar:

- **Consolidação dos relatórios:** relatórios semelhantes podem ser consolidados com técnicas como filtros, marcadores ou personalização. Ter menos relatórios, que são mais flexíveis, pode melhorar significativamente a experiência dos consumidores dos relatórios. Considere otimizar os conjuntos de dados para as [Perguntas e Respostas (consulta em linguagem natural)](../natural-language/q-and-a-best-practices.md) para proporcionar ainda mais flexibilidade aos consumidores dos relatórios, ao permitir que criem as próprias visualizações.
- **Melhorias na eficiência:** durante a obtenção dos requisitos, é possível identificar muitas vezes as melhorias. Por exemplo, quando os analistas compilam os números manualmente ou quando um fluxo de trabalho pode ser simplificado. O [Power Query](../transform-model/desktop-query-overview.md) pode desempenhar um papel importante na substituição das atividades manuais que estão atualmente em execução. Se os analistas empresariais realizarem regulamente as mesmas atividades para limpar e preparar os dados, os passos de preparação de dados do Power Query repetíveis podem gerar uma economia de tempo significativa e reduzir os erros.
- **Centralização do modelo de dados:** um conjunto de dados fidedigno e certificado serve como a base para o BI personalizado gerido. Neste caso, os dados são geridos uma vez e os analistas têm a flexibilidade de utilizar e aumentar esses dados para responder às necessidades de relatório e análise.

> [!NOTE]
> Para obter mais informações acerca da centralização dos modelos de dados, leia sobre a [disciplina no núcleo](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) e a [flexibilidade na periferia](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="prioritize-and-assess-complexity"></a>Priorizar e avaliar a complexidade

Neste ponto, o inventário inicial está disponível e pode incluir requisitos específicos. Ao priorizar o conjunto inicial de artefactos de BI prontos para migração, os relatórios e os dados devem ser considerados de forma coletiva, bem como independentes uns dos outros.

Identifique relatórios de alta prioridade, que podem incluir relatórios que:

- Acrescentam valor significativo aos negócios.
- São executadas com frequência.
- São exigidos pela liderança ou executivos seniores.
- Envolvam um nível razoável de complexidade (para melhorar as hipóteses de sucesso durante as iterações de migração iniciais).

Identifique os dados de alta prioridade, que podem incluir dados que:

- Contêm elementos de dados críticos.
- São dados organizacionais comuns que servem para muitos casos de utilização.
- Podem ser utilizados para criar um conjunto de dados partilhado para reutilização por relatórios e muitos autores de relatório.
- Envolvem um nível razoável de complexidade (para melhorar as hipóteses de sucesso nas iterações de migração iniciais).

## <a name="next-steps"></a>Passos seguintes

No [próximo artigo desta série de migração do Power BI](powerbi-migration-planning.md), ficará a saber mais sobre a Fase 2, que diz respeito ao planeamento da migração de uma solução única do Power BI.

Outros recursos úteis:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre como planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Os parceiros do Power BI experientes estão disponíveis para ajudar a sua organização a realizar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
