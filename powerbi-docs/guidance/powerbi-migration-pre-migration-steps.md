---
title: Preparar a migração para o Power BI
description: Orientação sobre os passos de pré-migração ao migrar para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: fba37d9f73ea0f61d8a43dc46cd13a5835d4d2a9
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "91525806"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Preparar a migração para o Power BI

Este artigo descreve as ações que pode considerar antes de migrar para o Power BI.

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Imagem a mostrar as fases de uma migração do Power BI. Os passos de pré-migração são realçados neste artigo.":::

> [!NOTE]
> Para obter uma explicação completa da imagem acima, veja o artigo [Power BI migration overview](powerbi-migration-overview.md) (Descrição geral da migração do Power BI).

Os passos de pré-migração realçam o planeamento adiantado, que é uma preparação importante antes de passar pelas cinco fases de migração. A maioria dos passos de pré-migração irá ocorrer uma vez. Contudo, para organizações maiores, algumas partes podem ser iterativas para cada unidade de negócio ou área departamental.

O resultado dos passos de pré-migração inclui um modelo de governação inicial, o planeamento inicial de alto nível da implementação, além de um inventário dos relatórios e dos dados a serem migrados. Serão necessárias informações adicionais de atividades nas Fases 1, 2 e 3 para estimar todo o nível de esforço da migração de soluções individuais.

> [!TIP]
> A maioria dos tópicos analisados neste artigo também se aplica a um projeto de implementação do Power BI padrão.

## <a name="create-costbenefit-analysis-and-evaluation"></a>Criar avaliação e análises de custo/benefício

Existem várias considerações principais durante a avaliação inicial, incluindo a obtenção de:

- Clareza sobre o caso empresarial e a estratégia de BI para atingir um estado futuro desejado específico.
- Clareza sobre o que significa o êxito e como medir o progresso e o êxito da iniciativa de migração.
- Estimativas de custo e resultados de cálculo de retorno sobre o investimento (ROI).
- Resultados com êxito para várias iniciativas do Power BI produtivas que são menores ao nível do âmbito e complexidade.

## <a name="identify-stakeholders-and-executive-support"></a>Identificar intervenientes e suporte executivo

Eis várias considerações para identificar os intervenientes:

- Garantir o alinhamento com os intervenientes no caso empresarial e na estratégia de BI.
- Incluir representantes de todas as unidades de negócios (mesmo que o respetivo conteúdo esteja previsto para migração num prazo posterior) para entender as respetivas motivações e preocupações.
- Envolver utilizadores experientes do Power BI antecipadamente.
- Criar e seguir um plano de comunicação com os intervenientes.

> [!TIP]
> Se começar a ter receio de que a comunicação está a tornar-se excessiva, provavelmente está na medida certa.

## <a name="generate-initial-governance-model"></a>Gerar o modelo de governação inicial

Eis vários itens importantes a serem abordados no início de uma implementação do Power BI:

- Objetivos específicos para a adoção do Power BI e onde o Power BI se adapta à estratégia geral de BI da organização.
- Como a função de administrador do Power BI será gerida, especialmente em organizações descentralizadas.
- Políticas relacionadas com a obtenção de dados de confiança: utilização de origens de dados autoritativas, resolução de problemas de qualidade de dados e utilização de terminologia consistente e definições comuns.
- Estratégia de privacidade de dados e segurança para origens de dados, modelos de dados, relatórios e entrega de conteúdos a utilizadores internos e externos.
- Como os requisitos de regulamentação, auditoria e conformidade interna e externa serão cumpridos.

> [!IMPORTANT]
> O modelo de governação mais eficaz tenta equilibrar a capacitação do utilizador com o nível de controlo necessário. Obtenha mais informações, leia sobre a [disciplina no núcleo](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) e a [flexibilidade na periferia](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="conduct-initial-deployment-planning"></a>Realizar o planeamento da implementação inicial

O planeamento da implementação inicial envolve definir padrões, políticas e preferências para a implementação do Power BI da organização.

Tenha em atenção que a [Fase 2](powerbi-migration-planning.md) faz referência ao planeamento da implementação ao nível da solução. As atividades da Fase 2 devem respeitar as decisões ao nível organizacional sempre que possível.

Eis alguns itens críticos a serem abordados no início de uma implementação do Power BI:

- Decisões de [definições do inquilino do Power BI](admin-tenant-settings.md), que devem ser documentadas.
- Decisões de [gestão de áreas de trabalho](../collaborate-share/service-new-workspaces.md), que devem ser documentadas.
- Considerações e preferências relacionadas com dados e [métodos de distribuição de conteúdos](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md), como aplicações, áreas de trabalho, partilhas, subscrições e incorporação de conteúdos.
- Preferências relacionadas com [modos de conjuntos de dados](../connect-data/service-dataset-modes-understand.md), como a utilização do Modo de importação, o Modo DirectQuery ou a combinação dos dois modos num [Modelo composto](composite-model-guidance.md).
- [Proteção de dados e acesso](../admin/service-admin-power-bi-security.md).
- Trabalhar com [conjuntos de dados partilhados](../connect-data/service-datasets-share.md) para reutilização.
- Aplicar a [certificação de dados](../connect-data/service-datasets-certify.md) para promover a utilização de dados autoritativos e fidedignos.
- Utilização de diferentes [tipos de relatórios](../create-reports/index.yml), incluindo relatórios do Power BI, relatórios do Excel ou relatórios paginados para diferentes casos de utilização ou unidades de negócio.
- Alterar as abordagens de gestão para gerir artefactos de BI centralizados e artefactos de BI geridos por empresas.
- Planos de preparação para consumidores, modeladores de dados, autores de relatórios e administradores.
- Suporte para autores de conteúdos através de [modelos do Power BI Desktop](../create-reports/desktop-templates.md), [elementos visuais personalizados](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/) e padrões de estrutura do relatório documentados.
- Procedimentos e processos para gerir os requisitos de utilizador, como a solicitação de novas licenças, adição de novas origens de dados de gateway, obtenção de permissão para origens de dados de gateway, solicitação de novas áreas de trabalho, alterações às permissões de áreas de trabalho e outros requisitos comuns que podem ser encontrados regularmente.

> [!IMPORTANT]
> O planeamento da implementação é um processo iterativo. As decisões de implementação serão muitas vezes melhoradas e aumentadas à medida que a experiência da sua organização com o Power BI cresce e o Power BI evolui. As decisões tomadas durante este processo serão utilizadas durante o planeamento da implementação ao nível da solução debatido na [Fase 2](powerbi-migration-planning.md) do processo de migração.

## <a name="establish-initial-architecture"></a>Estabelecer a arquitetura inicial

A sua [arquitetura da solução de BI](center-of-excellence-business-intelligence-solution-architecture.md) irá evoluir e amadurecer ao longo do tempo. Eis algumas tarefas de configuração do Power BI a processar de imediato:

- A configuração e integração do inquilino do Power BI no Azure Active Directory.
- Definir [administradores do Power BI](../admin/service-admin-role.md).
- Obter e atribuir [licenças de utilizador](../admin/service-admin-licensing-organization.md) iniciais.
- Configurar e rever as [definições do inquilino do Power BI](admin-tenant-settings.md).
- Configurar [funções de área de trabalho](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) e atribuir o acesso aos utilizadores e grupos de segurança do Azure Active Directory.
- Configurar um cluster de [gateway de dados](../connect-data/service-gateway-deployment-guidance.md) inicial, com um plano de atualização regular.
- Obter a [licença de capacidade Premium](../admin/service-admin-premium-purchase.md) inicial (se aplicável).
- Configurar as [cargas de trabalho de capacidade Premium](../admin/service-admin-premium-workloads.md), com um plano para gerir de forma contínua.

## <a name="define-success-criteria-for-migration"></a>Definir critérios de êxito para migração

A primeira tarefa consiste em compreender o significado do êxito na migração de uma solução individual. Eis algumas questões que poderá colocar:

- **Quais são as motivações e os objetivos específicos desta migração?** Para obter mais informações, veja o artigo [Power BI migration overview > Consider migration reasons](powerbi-migration-overview.md#consider-migration-reasons) (Descrição geral da migração do Power BI > Considerar os motivos da migração). Este artigo descreve as razões mais comuns para migrar para o Power BI. Os seus objetivos devem ser especificados ao nível organizacional. Além disso, a migração de uma solução de BI legada poderá beneficiar significativamente da poupança de custos, enquanto a migração de uma solução de BI legada diferente poderá concentrar-se na obtenção de benefícios pela otimização de fluxos de trabalho.
- **Qual é o custo/benefício ou ROI esperado para esta migração?** Ter uma compreensão clara das expetativas relacionadas com o custo, as capacidades aumentadas, a complexidade reduzida ou a maior agilidade é útil para calcular o êxito. Pode fornecer princípios de orientação para ajudar na tomada de decisões durante o processo de migração.
- **Que indicadores chave de desempenho (KPIs) serão utilizados para calcular o êxito?** A lista seguinte apresenta alguns KPIs de exemplo:
    - Número de relatórios compostos a partir da plataforma de BI legada, a diminuir de mês a mês.
    - Número de relatórios compostos a partir do Power BI, a aumentar de mês a mês.
    - Número de consumidores de relatórios do Power BI, a aumentar de trimestre a trimestre.
    - Percentagem de relatórios migrados para produção por data de destino.
    - Redução de custos no custo de licenciamento de ano a ano.

> [!TIP]
> O [registo de atividades do Power BI](../admin/service-admin-auditing.md) pode ser utilizado como uma origem para calcular o progresso de KPI.

## <a name="prepare-inventory-of-existing-reports"></a>Preparar um inventário de relatórios existentes

Preparar um inventário de relatórios existentes na plataforma de BI legada é um passo crítico para compreender o que já existe. O resultado deste passo é uma entrada para avaliar o nível de esforço da migração. Eis algumas atividades que podem estar relacionadas com a preparação de um inventário:

1. **Inventário de relatórios:** compilar uma lista de relatórios e dashboards que são candidatos à migração.
2. **Inventário de origens de dados:** compilar uma lista de todas as origens de dados acedidas por relatórios existentes. Deve incluir origens de dados empresariais, bem como origens de dados departamentais e pessoais. Este processo pode revelar origens de dados que anteriormente não eram conhecidas pelo departamento de TI, frequentemente referidas como _TI sombra_.
3. **Registo de auditoria:** obter dados do registo de auditoria da plataforma de BI legada para compreender os padrões de utilização e ajudar na priorização. As informações importantes a ser obtidas a partir do registo de auditoria incluem:
    - Número médio de vezes que cada relatório foi executado por semana/mês/trimestre.
    - Número médio de consumidores por relatório, por semana/mês/trimestre.
    - Os consumidores de cada relatório, particularmente os relatórios utilizados por executivos.
    - Data mais recente em que cada relatório foi executado.

> [!NOTE]
> Em muitos casos, o conteúdo não é migrado para o Power BI exatamente como está. A migração representa uma oportunidade de recriar a arquitetura dos dados e/ou melhorar a entrega de relatórios. A compilação de um inventário de relatórios é fundamental para compreender o que existe atualmente, para que possa começar a avaliar que refatorização tem de ocorrer. Os restantes artigos desta série descrevem possíveis melhorias de forma mais detalhada.

## <a name="explore-automation-options"></a>Explorar opções de automatização

Não é possível automatizar completamente um processo de conversão do Power BI do princípio ao fim.

A compilação do inventário de dados e relatórios existente é um possível candidato à automatização quando tem uma ferramenta existente que pode fazê-lo automaticamente. Até que ponto a automatização pode ser utilizada para algumas partes do processo de migração, como a compilação do inventário existente, depende bastante das ferramentas que tiver.

## <a name="next-steps"></a>Passos seguintes

No [próximo artigo desta série da migração do Power BI](powerbi-migration-requirements.md), saiba mais sobre a Fase 1, que diz respeito à recolha e à priorização de requisitos ao migrar para o Power BI.

Outros recursos úteis incluem:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Estão disponíveis parceiros do Power BI experientes para ajudar a sua organização a efetuar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
