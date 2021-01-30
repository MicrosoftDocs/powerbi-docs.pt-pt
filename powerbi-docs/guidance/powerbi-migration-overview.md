---
title: Descrição geral da migração do Power BI
description: Saiba como planear e realizar uma migração de outra ferramenta de BI de terceiros para o Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 2089e9f7538fa5a1f4d0e14711dcd877decaa718
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086838"
---
# <a name="power-bi-migration-overview"></a>Descrição geral da migração do Power BI

Os clientes estão cada vez mais a uniformizar a utilização do Power BI para impulsionar uma cultura de dados, que envolve a ativação da business intelligence de gestão personalizada (SSBI) gerida, a racionalização da disponibilização da BI empresarial e lidar com as pressões económicas. A finalidade desta série de artigos de migração do Power BI é disponibilizar orientações sobre como planear e realizar uma migração de uma ferramenta de BI de terceiros para o Power BI.

Os artigos na série de migração do Power BI incluem:

1. Descrição geral da migração do Power BI (este artigo)
1. [Preparar a migração para o Power BI](powerbi-migration-pre-migration-steps.md)
1. [Obter os requisitos para migrar para o Power BI (Fase 1)](powerbi-migration-requirements.md)
1. [Planear a implementação para migrar para o Power BI (Fase 2)](powerbi-migration-planning.md)
1. [Proceder à prova de conceito para migrar para o Power BI (Fase 3)](powerbi-migration-proof-of-concept.md)
1. [Criar conteúdo para migrar para o Power BI (Fase 4)](powerbi-migration-create-validate-content.md)
1. [Implementar no Power BI (Fase 5)](powerbi-migration-deploy-support-monitor.md)
1. [Aprenda com as migrações do Power BI dos clientes](powerbi-migration-learn-from-customers.md)

Há duas suposições: a sua organização tem uma plataforma de BI legada atualmente em vigor e foi tomada a decisão de migrar formalmente o conteúdo e os utilizadores para o Power BI. A migração para o serviço Power BI é o foco principal desta série. Podem ser aplicadas considerações adicionais para clientes da cloud nacional, além do que é discutido nesta série de artigos.

O diagrama a seguir mostra quatro fases de alto nível para a implementação do Power BI na sua organização.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="Imagem a mostrar as quatro fases de alto nível, que são descritas na tabela a seguir.":::

|Fase|Descrição|
|--------|-----------|
|![Fase 1.](media/common/icon-01-red-30x30.png)|**Configurar e avaliar o Power BI.** A primeira fase envolve estabelecer a arquitetura inicial do Power BI. A implementação preliminar e o planeamento da governação são tratados neste ponto, bem como as avaliações do Power BI, incluindo o retorno do investimento e/ou a análise custo-benefício.|
|![Fase 2.](media/common/icon-02-red-30x30.png)|**Criar rapidamente novas soluções no Power BI.** Na segunda fase, os autores da BI personalizada podem começar a utilizar e avaliar o Power BI para as suas necessidades e podem obter rapidamente valor do Power BI. As atividades na Fase 2 colocam a importância na agilidade e no rápido valor comercial, que é essencial para obter a aceitação da seleção de uma nova ferramenta de BI, como o Power BI. Por este motivo, o diagrama descreve as atividades na Fase 2 que ocorrem lado a lado com as atividades de migração na Fase 3.|
|![Fase 3.](media/common/icon-03-red-30x30.png)|**Migrar os recursos de BI da plataforma legada para o Power BI.** A terceira fase aborda a migração para o Power BI. Este é o foco desta série de artigos de migração do Power BI. Na próxima secção, vamos discutir cinco fases de migração específicas.|
|![Fase 4.](media/common/icon-04-red-30x30.png)|**Adotar, administrar e monitorizar o Power BI.** A fase final é composta pelas atividades contínuas, como incentivar uma cultura de dados, a comunicação e a formação. Estas atividades afetam significativamente a implementação efetiva do Power BI. É importante ter políticas e processos de governação e segurança adequados para a sua organização, bem como auditoria e monitorização para permitir que possa dimensionar, aumentar e melhorar continuamente.|

> [!IMPORTANT]
> Uma migração formal para o Power BI ocorre quase sempre em paralelo com o desenvolvimento de uma nova solução do Power BI. _Solução do Power BI_ é um termo genérico que abrange a utilização dados e dos relatórios. Um único ficheiro do Power BI Desktop (pbix) pode conter um modelo de dados ou um relatório, ou ambos. A [separação do modelo de dados dos relatórios](../guidance/report-separate-from-model.md) é incentivada para fins de reutilização dos dados, mas não é necessária.
>
> A utilização do Power BI para criar novos requisitos, enquanto planeia e realiza a migração formal, ajudará a obter adesão. As fases simultâneas proporcionam aos autores de conteúdo uma experiência prática e real com o Power BI.

## <a name="five-stages-of-a-power-bi-migration"></a>As cinco fases da migração do Power BI

A Fase 3 do diagrama aborda a migração para o Power BI. Durante esta fase, há cinco fases comuns.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="Imagem a mostrar as fases da migração do Power BI, que são descritas a seguir.":::

As fases abaixo mostradas no diagrama anterior são:

- [Passos de pré-migração](#pre-migration-steps)
- [Fase 1: obter os requisitos e atribuir prioridades](#stage-1-gather-requirements-and-prioritize)
- [Fase 2: planear a implementação](#stage-2-plan-for-deployment)
- [Fase 3: proceder à prova de conceito](#stage-3-conduct-proof-of-concept)
- [Fase 4: criar e validar conteúdo](#stage-4-create-and-validate-content)
- [Fase 5: implementar, suportar e monitorizar](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>Passos de pré-migração

Os passos de pré-migração incluem ações que pode considerar antes de iniciar um projeto para migrar o conteúdo de uma plataforma de BI legada para o Power BI. Normalmente, estes passos incluem o planeamento inicial da implementação ao nível do inquilino. Para obter mais informações sobre estas atividades, veja [Preparar a migração para o Power BI](powerbi-migration-pre-migration-steps.md).

### <a name="stage-1-gather-requirements-and-prioritize"></a>Fase 1: obter os requisitos e atribuir prioridades

A ênfase da Fase 1 é a obtenção de informações e o planeamento da migração de uma única solução. Este processo deve ser iterativo e ter como âmbito um esforço de tamanho razoável. O resultado da Fase 1 inclui um inventário de relatórios priorizado e os dados que devem ser migrados. São necessárias atividades adicionais nas Fases 2 e 3 para estimar totalmente o nível de esforço. Para obter mais informações sobre as atividades na Fase 1, veja [Obter os requisitos para migrar para o Power BI](powerbi-migration-requirements.md).

### <a name="stage-2-plan-for-deployment"></a>Fase 2: planear a implementação

O foco da Fase 2 está na forma como os requisitos definidos na Fase 1 podem ser cumpridos em cada solução específica. O resultado da Fase 2 inclui o máximo de especificações possível para guiar o processo, embora seja um processo iterativo e não linear. A criação de uma prova de conceito (na Fase 3) pode ocorrer em paralelo com esta fase. Mesmo durante a criação da solução (na Fase 4), podem ser apresentadas informações adicionais que influenciam as decisões de planeamento de implementação. Este tipo de planeamento de implementação na Fase 2 concentra-se no nível da solução, enquanto respeita as decisões já tomadas ao nível organizacional. Para obter mais informações sobre as atividades na Fase 2, veja [Planear a implementação para migrar para o Power BI](powerbi-migration-planning.md).

### <a name="stage-3-conduct-proof-of-concept"></a>Fase 3: proceder à prova de conceito

A ênfase da Fase 3 assenta na resolução de fatores desconhecidos e na atenuação de riscos o mais cedo possível. Uma prova de conceito (POC) técnica é útil para validar suposições e pode ser feita iterativamente juntamente com o planeamento de implementação (Fase 2). O resultado desta fase é uma solução do Power BI com um âmbito restrito. Observe que não pretendemos que a POC seja um trabalho descartável. No entanto, provavelmente será necessário um trabalho adicional na Fase 4 para a tornar pronta para produção. Neste aspeto, a sua organização pode referir-se a esta atividade como um protótipo, um piloto, um modelo, um início rápido ou um produto mínimo viável (MVP). Nem sempre é necessário proceder a uma POC, esta pode ser realizada informalmente. Para obter mais informações sobre as atividades na Fase 3, veja [Proceder à prova de conceito para migrar para o Power BI](powerbi-migration-proof-of-concept.md).

### <a name="stage-4-create-and-validate-content"></a>Fase 4: criar e validar conteúdo

A Fase 4 decorre quando é realizado o trabalho real para converter a POC numa solução pronta para produção. O resultado desta fase é uma solução do Power BI concluída que foi validada num ambiente de desenvolvimento. Esta deve estar pronta para implementação na Fase 5. Para obter mais informações sobre as atividades na Fase 4, veja [Criar conteúdo para migrar para o Power BI](powerbi-migration-create-validate-content.md).

### <a name="stage-5-deploy-support-and-monitor"></a>Fase 5: implementar, suportar e monitorizar

O foco principal da Fase 5 é implementar a nova solução de Power BI na produção. O resultado desta fase é uma solução de produção utilizada ativamente pelos utilizadores empresariais. Ao utilizar uma metodologia ágil, é aceitável ter algumas melhorias planeadas que serão entregues numa iteração futura. Dependendo do nível de conforto com o Power BI, como minimizar o risco e a interrupção do utilizador, pode optar por fazer uma implementação faseada. Ou, inicialmente, pode implementar num grupo de utilizadores piloto mais pequeno. O suporte e a monitorização também são importantes nesta fase e de forma contínua. Para obter mais informações sobre as atividades na Fase 5, veja [Migrar para o Power BI](powerbi-migration-deploy-support-monitor.md).

> [!TIP]
> A maioria dos conceitos discutidos em toda esta série de artigos de migração do Power BI também se aplica aos projetos de implementação do Power BI padrão.

## <a name="consider-migration-reasons"></a>Considere os motivos da migração

A capacitação de uma cultura de dados produtiva e íntegra é uma das principais metas de muitas organizações. O Power BI é uma excelente ferramenta para facilitar este objetivo. Três motivos comuns que pode considerar ao migrar para o Power BI podem ser resumidos da seguinte forma:

- **Ativar a BI de gestão personalizada gerida** ao introduzir novas capacidades que aumentam a produtividade da comunidade de utilizadores da BI de gestão personalizada. O Power BI torna o acesso às informações e à tomada de decisões mais amplamente disponível, enquanto depende menos das competências de especialistas que podem ser difíceis de encontrar.
- **Racionalizar a entrega de BI empresarial** para cumprir os requisitos que não são abordados por ferramentas de BI existentes, enquanto diminui o nível de complexidade, reduz o custo de propriedade e/ou a uniformização de várias ferramentas de BI atualmente em utilização.
- **Lidar com pressões económicas** para aumentar a produtividade com menos recursos, tempo e pessoal.

## <a name="achieve-power-bi-migration-success"></a>Obter uma migração do Power BI bem-sucedida

Cada migração é um pouco diferente. Tal pode depender da estrutura organizacional, das estratégias de dados, da maturidade da gestão de dados e dos objetivos organizacionais. No entanto, há algumas práticas que vemos consistentemente nos nossos clientes que obtêm uma migração do Power BI bem-sucedida.

- **Patrocínio executivo:** identifique um patrocinador executivo no início do processo. Esta pessoa deve ser alguém que preste suporte ativo à BI na organização e é pessoalmente responsável pela obtenção de um resultado positivo para a migração. Idealmente, o patrocinador executivo tem autoridade e responsabilidade finais para resultados relacionados com o Power BI.
- **Preparação, suporte e comunicação:** reconheça que é mais do que apenas uma iniciativa de tecnologia. Qualquer projeto de BI ou de análise também é uma iniciativa de pessoas, portanto, considere investir cedo na formação e no suporte dos utilizadores. Além disso, crie um plano de comunicação que explique de forma transparente a todos os intervenientes o que está a ocorrer, o motivo e que defina expetativas realistas. Confirme que incluiu um ciclo de comentários no plano de comunicação para receber as mensagens dos participantes.
- **Vitórias rápidas:** inicialmente, dê prioridade aos itens de valor alto que têm um valor comercial tangível e são urgentes. Em vez de tentar estritamente migrar sempre os relatórios precisamente à medida que aparecem na plataforma de BI legada, concentre-se na pergunta comercial que o relatório está a tentar responder, incluindo a ação a ser tomada, ao abordar o relatório reformulado.
- **Modernização e melhorias:** esteja disposto a reconsiderar como as coisas sempre foram feitas. A migração pode proporcionar uma oportunidade para criar melhorias. Por exemplo, pode eliminar a preparação de dados manual ou realocar as regras de negócios que estavam confinadas a um único relatório. Considere refatorizar, modernizar e consolidar soluções existentes quando o esforço puder ser justificado. Tal pode incluir a consolidação de vários relatórios num único ou a eliminação de artefactos legados que não tenham sido utilizados há algum tempo.
- **Aprendizagem contínua:** esteja preparado para utilizar uma abordagem faseada enquanto aprende e adapta continuamente. Trabalhe em ciclos iterativos curtos para agregar valor rapidamente. Torne a conclusão de pequenas POCs uma prática frequente para minimizar o risco de fatores desconhecidos, validar suposições e aprender sobre novas funcionalidades. Como o Power BI é um serviço cloud atualizado mensalmente, é importante manter-se atualizado sobre os desenvolvimentos e ajustar o curso quando apropriado.
- **Resistência a alterações:** entenda que pode haver níveis variados de resistência a alterações; alguns utilizadores vão resistir à aprendizagem de uma nova ferramenta. Além disso, alguns profissionais que dedicaram tempo e esforço significativos para se especializarem numa ferramenta de BI diferente podem sentir-se ameaçados por esta ser desalocada. Esteja preparado, pois tal pode resultar em dificuldades políticas internas, especialmente em organizações altamente descentralizadas.
- **Restrições:** seja realista com os planos de migração, incluindo financiamento, estimativas de tempo, bem como as funções e responsabilidades de todos os envolvidos.

## <a name="acknowledgments"></a>Agradecimentos

Esta série de artigos foi escrita por Melissa Coates, MVP da Plataforma de Dados e proprietária de [Coates Data Strategies](https://www.coatesdatastrategies.com/). Contribuintes e revisores: Marc Reguera, Venkatesh Titte, Patrick Baumgartner, Tamer Farag, Richard Tkachuk, Matthew Roche, Adam Saxton, Chris Webb, Mark Vaillancourt, Daniel Rubiolo, David Iseminger e Peter Myers.

## <a name="next-steps"></a>Passos seguintes

No [próximo artigo desta série de migração do Power BI](powerbi-migration-pre-migration-steps.md), ficará a saber mais sobre os passos de pré-migração ao migrar para o Power BI.

Outros recursos úteis:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre como planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Migrate SSRS reports to Power BI (Migrar relatórios SSRS para o Power BI)](migrate-ssrs-reports-to-power-bi.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Os parceiros do Power BI experientes estão disponíveis para ajudar a sua organização a realizar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
