---
title: Proceder à prova de conceito para migrar para o Power BI
description: Orientação sobre a proceder a uma prova de conceito ao migrar para o Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 77174da7fd47470974a292ba98f6b50c268b04fd
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419136"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>Proceder à prova de conceito para migrar para o Power BI

Este artigo descreve a **Fase 3**, que diz respeito ao procedimento de uma prova de conceito (POC) para mitigar riscos e resolver problemas desconhecidos o mais cedo possível ao migrar para o Power BI.

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="Imagem a mostrar as fases de uma migração do Power BI. A Fase 3 está realçada neste artigo.":::

> [!NOTE]
> Para obter uma explicação completa sobre o gráfico acima, veja [Descrição geral da migração do Power BI](powerbi-migration-overview.md).

A Fase 3 foca-se na resolução de problemas desconhecidos e na mitigação de riscos o mais cedo possível. Uma POC técnica é útil para validar suposições. Esta pode ser feita iterativamente, juntamente com o planeamento da implementação da solução (descrito na [Fase 2](powerbi-migration-planning.md)).

O resultado desta fase é uma solução do Power BI que restringe o âmbito, aborda as perguntas iniciais abertas e está pronta para trabalho adicional na [Fase 4](powerbi-migration-create-validate-content.md) para a preparar para produção.

> [!IMPORTANT]
> Não pretendemos que a POC seja um trabalho descartável. Em vez disso, esperamos que seja uma iteração inicial da solução pronta para produção. Na sua organização, pode referir-se a esta atividade como um protótipo, um piloto, um modelo, um início rápido ou um produto mínimo viável (MVP). Nem sempre é necessário proceder a uma POC, esta pode até decorrer informalmente.

> [!TIP]
> A maioria dos tópicos discutidos neste artigo também se aplicam a um projeto de implementação do Power BI padrão. À medida que a sua organização se torna mais experiente no Power BI, a necessidade de proceder a POCs diminui. No entanto, devido à rápida cadência de lançamentos com o Power BI e à introdução contínua de novas funcionalidades, pode proceder a POCs técnicas regularmente para fins de aprendizagem.

## <a name="set-poc-goals-and-scope"></a>Definir os objetivos e o âmbito da POC

Ao proceder a uma POC, concentre-se nos seguintes objetivos:

- Verifique as suposições sobre o funcionamento de uma funcionalidade.
- Conheça as diferenças na forma como o Power BI funciona em comparação com a plataforma de BI legada.
- Valide as compreensões iniciais de determinados requisitos junto de especialistas no assunto.
- Crie um pequeno conjunto de dados com dados reais para compreender e detetar quaisquer problemas com a estrutura de dados, as relações, os tipos de dados ou os valores dos dados.
- Experimente e valide as expressões da [sintaxe DAX](/dax/) utilizadas pelos cálculos dos modelos.
- Teste a conectividade da origem de dados com um gateway (se se destinar a ser uma origem de gateway).
- Teste a atualização dos dados com um gateway (se se destinar a ser uma origem de gateway).
- Verifique as configurações de segurança, incluindo a segurança ao nível da linha, quando aplicável.
- Experimente com decisões estéticas e de esquema.
- Verifique se todas as funcionalidades no serviço Power BI funcionam conforme o esperado.

O âmbito da POC depende de quais são os fatores desconhecidos ou quais os objetivos que precisam de ser validados junto de colegas. Para reduzir a complexidade, mantenha a POC o mais restrita possível em termos de âmbito.

Geralmente, com uma migração, os requisitos são bem conhecidos, pois existe uma solução inicial. No entanto, dependendo da extensão das melhorias a serem realizadas ou as competências existentes do Power BI, uma POC ainda oferece um valor significativo. Além disso, a rápida criação de protótipos com feedback dos consumidores pode ser adequada para clarificar rapidamente os requisitos, especialmente se forem feitas melhorias.

> [!IMPORTANT]
> Mesmo que uma POC inclua apenas um subconjunto de dados ou apenas elementos visuais limitados, é muito importante realizá-la do início até ao fim. Isto é, desde o desenvolvimento no Power BI Desktop até à implementação numa área de trabalho de desenvolvimento no serviço Power BI. É a única forma de cumprir totalmente os objetivos da POC. Tal é particularmente verdadeiro quando o serviço Power BI tem de proporcionar funcionalidade crítica que não utilizou antes, como um conjunto de dados do DirectQuery com início de sessão único. Durante a POC, concentre os esforços nos aspetos sobre os quais não tem a certeza ou que precisa de verificar com outras pessoas.

## <a name="handle-differences-in-power-bi"></a>Lidar com as diferenças no Power BI

O Power BI pode ser utilizado como uma _ferramenta baseada num modelo_ ou como uma _ferramenta baseada num relatório_. Uma solução baseada num modelo envolve o desenvolvimento de um modelo de dados, por sua vez, uma solução baseada num relatório liga-se a um modelo de dados já implementado.

Devido à sua enorme flexibilidade, há alguns aspetos sobre o Power BI que podem ser fundamentalmente diferentes da plataforma de BI legada da qual está a migrar.

### <a name="consider-redesigning-the-data-architecture"></a>Considere a possibilidade de reformular a arquitetura de dados

Se estiver a migrar de uma plataforma de BI legada que tenha a sua própria camada semântica, a criação de um conjunto de dados de Importação provavelmente será uma boa opção. O Power BI funciona melhor com um design de tabela de [esquema de estrela](star-schema.md). Portanto, se a camada semântica legada não for um esquema de estrela, poderá ser necessário algum tipo de reformulação para beneficiar totalmente do Power BI. Ao empenhar-se na definição de uma camada semântica que cumpre os princípios de design do esquema de estrela (incluindo relações, medidas utilizadas com frequência e terminologia organizacional amigável) vai criar um excelente ponto de partida para os autores de relatórios self-service.

Se estiver a migrar de uma plataforma de BI legada na qual os relatórios fazem referência a origens de dados relacionais com consultas SQL ou procedimentos armazenados e, se estiver a planear utilizar o Power BI no [modo DirectQuery](../connect-data/desktop-use-directquery.md), poderá conseguir uma migração um-para-um do modelo de dados.

> [!CAUTION]
> Se vir a criação de muitos ficheiros do Power BI Desktop que incluem uma única tabela importada, normalmente será um indicador de que o design não é o ideal. Caso observe esta situação, investigue se a utilização de [conjuntos de dados partilhados](../connect-data/service-datasets-across-workspaces.md) criados com um design de [esquema de estrela](star-schema.md) poderia obter um resultado melhor.

### <a name="decide-how-to-handle-dashboard-conversions"></a>Decidir como lidar com conversões do dashboard

No setor de BI, um dashboard é uma coleção de elementos visuais que apresentam as principais métricas numa única página. No entanto, no Power BI, um dashboard representa uma funcionalidade de visualização específica que apenas pode ser criada no serviço Power BI. Ao migrar um dashboard de uma plataforma de BI legada, tem duas opções:

1. O dashboard legado pode ser recriado como um _relatório_ do Power BI. A maioria dos relatórios são criados com o Power BI Desktop. Os relatórios paginados e relatórios do Excel também são opções alternativas.
2. O dashboard legado pode ser recriado como um _dashboard_ do Power BI. Os [dashboards](../fundamentals/service-basic-concepts.md#dashboards) são uma funcionalidade de visualização do serviço Power BI. Os elementos visuais do dashboard são geralmente criados ao afixar elementos visuais de um ou mais relatórios, Perguntas e Respostas ou Informações Rápidas.

> [!TIP]
> Como os dashboards são um tipo de conteúdo do Power BI, evite utilizar a palavra _dashboard_ no nome do relatório ou do dashboard.

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>Concentre-se na visão geral ao recriar os elementos visuais

Cada ferramenta de BI tem os seus pontos fortes e áreas de foco. Por este motivo, os elementos visuais exatos de relatório dos quais dependia numa plataforma de BI legada podem não ter um equivalente próximo no Power BI.

Ao recriar elementos visuais de relatório, concentre-se mais nas perguntas de negócios do panorama geral que estão a ser abordadas pelo relatório. Tal remove a pressão para replicar o design de cada elemento visual exatamente da mesma forma. Embora os consumidores de conteúdo apreciem a consistência ao utilizar relatórios migrados, é importante não se deixar distrair com debates demorados sobre pequenos detalhes.

## <a name="next-steps"></a>Passos seguintes

No [próximo artigo desta série de migração do Power BI](powerbi-migration-create-validate-content.md), ficará a saber mais sobre a Fase 4, que diz respeito à criação e validação de conteúdo ao migrar para o Power BI.

Outros recursos úteis:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre como planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Os parceiros do Power BI experientes estão disponíveis para ajudar a sua organização a realizar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
