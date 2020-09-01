---
title: Aprenda com as migrações do Power BI dos clientes
description: Aprenda com os clientes ao migrar para o Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a725d2763d7d044220785c2f9727ee30f14bfd5d
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803487"
---
# <a name="learn-from-customer-power-bi-migrations"></a>Aprenda com as migrações do Power BI dos clientes

Este artigo, que conclui a série sobre a migração para o Power BI, partilha as principais lições aprendidas por dois clientes que migraram com êxito para o Power BI.

## <a name="international-consumer-goods-company"></a>Empresa internacional de bens de consumo

Em 2017, uma empresa internacional de bens de consumo, que vende centenas de produtos, tomou a decisão de seguir uma estratégia de cloud prioritária. Um dos principais fatores para escolher o Power BI como a plataforma de business intelligence (BI) foi a profunda integração com o Azure e o Microsoft 365.

### <a name="conduct-a-phased-migration"></a>Realizar uma migração faseada

Em 2017, a empresa começou a utilizar o Power BI. O objetivo organizacional inicial era introduzir o Power BI como uma ferramenta de BI adicional. A decisão proporcionava aos autores de conteúdo, consumidores e equipa de TI tempo para se adaptarem às novas formas de distribuição de BI, permitiu também a expansão dos conhecimentos relativos ao Power BI.

Durante a segunda metade de 2018, foi feito um anúncio formal a declarar que o Power BI era a ferramenta de BI aprovada para a organização. E, por esse motivo, todo o novo trabalho de desenvolvimento de BI deve ser executado no Power BI. A disponibilidade do Power BI Premium era um fator-chave para tomar esta decisão. Neste momento, a organização desaconselhava a utilização da antiga plataforma de BI e iniciou o planeamento para a transição.

Perto do fim de 2019, começou o trabalho de migração do conteúdo existente da plataforma de BI legada para o Power BI. Alguns dos adotantes iniciais migraram o conteúdo rapidamente. Isso ajudou a criar ainda mais dinamismo com Power BI em toda a organização. Em seguida, foi pedido ao proprietários e autores de conteúdo para começarem as preparações para migrar totalmente para o Power BI até ao fim de 2020. A organização ainda enfrenta desafios relacionados com as competências, o tempo e o financiamento, embora nenhum dos desafios esteja relacionado com a própria plataforma tecnológica.

> [!IMPORTANT]
> O Power BI já se tinha tornado num êxito e estava consolidado dentro da organização antes de ter sido pedido às unidades de negócios que realizassem o esforço de migração formal da antiga plataforma de BI.

### <a name="prepare-to-handle-varying-responses"></a>Preparação para lidar com diferentes respostas

Nesta grande organização descentralizada, havia vários níveis de recetividade e vontade de transição para o Power BI. Além das preocupações relacionadas com o tempo e o orçamento, havia ainda o pessoal que tinha feito investimentos significativos na expansão das competências na antiga plataforma de BI. Portanto, o anúncio sobre a uniformização para o Power BI não foi uma notícia bem recebida por todos. Uma vez que cada unidade de negócios tem o seu próprio orçamento, as unidades de negócios individuais poderiam pôr em causa decisões como esta. As decisões das ferramentas de TI foram tomadas de forma centralizada, o que criou alguns desafios que patrocinador executivo e os líderes de BI tiveram de enfrentar.

> [!IMPORTANT]
> A comunicação com as equipas de liderança em todas as unidades de negócios foi essencial para garantir que todos compreendiam os benefícios organizacionais de alto nível de uniformização para o Power BI. A comunicação eficaz tornou-se ainda mais essencial à medida que a migração progrediu e a data de desativação da plataforma de BI legada se aproximava.

### <a name="focus-on-the-bigger-picture"></a>Foco na visão geral

A empresa descobriu que, embora alguns relatórios migrados pudessem replicar a estrutura original de forma semelhante, nem todos os relatórios individuais poderiam ser replicados de forma segura no Power BI. Embora essa situação fosse esperada, já que todas as plataformas de BI são diferentes, revelou que era necessário ter uma mentalidade de conceção diferente.

Foram disponibilizadas orientações aos autores de conteúdo: foco na criação de relatórios ajustados para os fins no Power BI, em vez de tentar criar uma réplica exata do relatório legado. Por este motivo, os especialistas no assunto precisam de estar ativamente disponíveis durante o processo de migração para consulta e validação. Foram realizados esforços para considerar a finalidade da estrutura do relatório e para a melhorar quando adequado.

> [!IMPORTANT]
> Às vezes, a melhor abordagem é fazer melhorias durante a migração. Noutros casos, a melhor opção é disponibilizar exatamente o mesmo valor que o anterior, sem grandes melhorias, para não prejudicar a linha cronológica da migração.

### <a name="cautiously-assess-priorities"></a>Avaliar cuidadosamente as prioridades

Foi realizada uma análise da antiga plataforma de BI para entender totalmente a sua utilização. A antiga plataforma de BI incluía milhares de relatórios publicados e, no ano passado, acedeu-se a cerca de metade deles. Esse número poderia ser reduzido novamente para metade ao avaliar quais são os relatórios que proporcionam valor significativo para a organização. Esses relatórios foram priorizados para a primeira migração.

> [!IMPORTANT]
> É muito fácil sobrevalorizar a verdadeira importância de um relatório. Relativamente aos relatórios que não são utilizados com frequência, avalie se estes podem ser totalmente desativados. Por vezes, é mais barato e fácil não fazer nada.

### <a name="cautiously-assess-complexity"></a>Avaliar cuidadosamente a complexidade

Nos primeiros relatórios priorizados, foram compiladas as estimativas de tempo com base nos níveis de esforço estimados: simples, médio ou complexo. Embora pareça um processo relativamente simples, não espere que as estimativas de tempo sejam precisas para os relatórios individuais. Poderá descobrir que uma estimativa é extremamente imprecisa. Por exemplo, a empresa possuía um relatório considerado altamente complexo. Os consultores chegaram a uma estimativa de conversão de 50 dias. No entanto, o relatório reestruturado no Power BI foi concluído em cerca de 50 horas.

> [!IMPORTANT]
> Embora as estimativas de tempo sejam normalmente necessárias para obter financiamento e para fins de atribuição de pessoal, provavelmente são mais valiosas na agregação.

### <a name="decide-how-change-management-is-handled"></a>Decidir como a gestão da mudança é tratada

Com um elevado volume de ativos de BI, a gestão da mudança dos relatórios detidos pela empresa representava um desafio. Os relatórios geridos pela equipa de TI foram tratados de acordo com as práticas de gestão da mudança padrão. No entanto, devido ao elevado volume, realizar a mudança centralmente para o conteúdo detido pela empresa não era possível.

> [!IMPORTANT]
> As unidades de negócios ficam com responsabilidade adicional quando não é possível gerir a mudança a partir de uma equipa central.

### <a name="create-an-internal-community"></a>Criar uma comunidade interna

A empresa estabeleceu um Centro de Excelência (COE) para disponibilizar aulas de formação internas e recursos. O COE também serve como um grupo de consultoria interno que está pronto para ajudar os autores de conteúdo com problemas técnicos, resolução de obstáculos e orientações das melhores práticas.

Existe também uma comunidade interna do Power BI, que tem tido um enorme sucesso, com mais de 1600 membros. A comunidade é gerida no Yammer. Os membros podem fazer perguntas internamente relevantes e receber respostas que cumprem as melhores práticas e se enquadram dentro das restrições organizacionais. Este tipo de interação entre utilizadores alivia grande parte da sobrecarga de suporte do COE. No entanto, o COE monitoriza as perguntas e as respostas e participa nas conversas, quando adequado.

Uma extensão da comunidade interna é a mais recente rede de especialistas do Power BI, que inclui um pequeno número de utilizadores experientes do Power BI previamente selecionados na organização. São utilizadores entusiastas do Power BI altamente qualificados das unidades de negócios, que desejam resolver ativamente os desafios na empresa. Os membros da rede de especialistas do Power BI devem respeitar as melhores práticas e as diretrizes estabelecidas pelo COE e ajudar a comunidade interna mais ampla do Power BI a entendê-las e implementá-las. Embora a rede de especialistas do Power BI colabore com o COE e possa receber formação dedicada, os especialistas do Power BI operam de forma independente do COE. Cada especialista do Power BI pode definir os parâmetros de como opera, tendo em mente que tem outras responsabilidades e prioridades na sua função oficial.

> [!IMPORTANT]
> Tenha um âmbito bem definido para o que o COE faz, como: adoção, governação, orientação, melhores práticas, formação, suporte e, talvez, até mesmo desenvolvimento prático. Embora um COE seja incrivelmente valioso, é difícil avaliar o seu retorno sobre o investimento.

### <a name="monitor-migration-progress-and-success"></a>Monitorizar o progresso e o êxito da migração

Os indicadores chave de desempenho (KPIs) são continuamente monitorizados durante a migração para o Power BI. Ajudam a empresa a compreender as tendências das métricas, como o número de visitas do relatório, o número de relatórios ativos e os diferentes utilizadores por mês. O aumento da utilização do Power BI é medido juntamente com a redução da utilização da antiga plataforma de BI, com o objetivo de alcançar uma relação inversa. Os objetivos são atualizados todos os meses para se adaptarem às mudanças. Se a utilização não estiver a ocorrer ao ritmo desejado, os estrangulamentos serão identificados para que a ação adequada possa ser executada.

> [!IMPORTANT]
> Crie uma tabela de indicadores da migração com business intelligence acionável para monitorizar o êxito do esforço de migração.

## <a name="large-transportation-and-logistics-company"></a>Grande empresa de transporte e logística

Uma grande empresa de transporte e logística da América do Norte está a investir ativamente na modernização da infraestrutura de dados e dos sistemas analíticos.

### <a name="allow-a-period-of-gradual-growth"></a>Permitir um período de crescimento gradual

A empresa começou a utilizar o Power BI em 2018. Em meados de 2019, o Power BI tornou-se na plataforma preferida de todos os novos casos de utilização de BI. Depois, em 2020, a empresa concentrou-se em suprimir progressivamente a plataforma de BI existente, além de uma variedade de soluções personalizadas de BI do ASP.NET.

> [!IMPORTANT]
> O Power BI tinha muitos utilizadores ativos em toda a organização antes de começar a supressão progressiva das soluções e plataformas de BI legadas.

### <a name="balance-centralized-and-distributed-groups"></a>Equilibrar os grupos centralizados e distribuídos

Na empresa, há dois tipos de equipas de BI: uma equipa central de BI e grupos de análise distribuídos por toda a organização. A equipa de BI central tem a responsabilidade da propriedade do Power BI como plataforma, mas não possui nenhum do conteúdo. Dessa forma, a equipa de BI central é um hub de ativação técnica que dá suporte aos grupos de análise distribuídos.

Cada um dos grupos de análise é dedicado a uma unidade de negócios específica ou a uma função de serviços partilhados. Um pequeno grupo pode ter um único analista, enquanto um grupo maior pode ter entre 10 e 15 analistas.

> [!IMPORTANT]
> Os grupos de análise distribuídos incluem especialistas no assunto que estão familiarizados com as necessidades empresariais diárias. Esta separação permite que a equipa de BI central se foque principalmente na ativação técnica e no suporte dos serviços e ferramentas de BI.

### <a name="focus-on-dataset-reusability"></a>Foco na reutilização dos conjuntos de dados

A dependência de soluções personalizadas de BI do ASP.NET era uma barreira para o desenvolvimento de novas soluções de BI. O conjunto de competências necessárias significava que o número de autores de conteúdo de self-service era reduzido. Como o Power BI é uma ferramenta muito mais acessível, especificamente concebida para o BI de self-service, disseminou-se rapidamente em toda a organização após o lançamento.

A capacitação dos analistas de dados na empresa permitiu obter resultados positivos imediatos. No entanto, o foco inicial do desenvolvimento do Power BI estava na visualização. Embora tenha resultado em soluções de BI valiosas, esse foco resultou num grande número de ficheiros do Power BI Desktop, cada um com uma relação um-para-um entre o relatório e o conjunto de dados, o que resultou em muitos conjuntos de dados e na duplicação dos dados e da lógica de negócios. Para reduzir a duplicação dos dados, a lógica e o esforço, a empresa disponibilizou formação e suporte aos autores de conteúdo.

> [!IMPORTANT]
> Inclua informações sobre a importância da reutilização dos dados nos esforços de formação interna. Aborde conceitos importantes logo que possível.

### <a name="test-data-access-multiple-ways"></a>Testar o acesso aos dados de várias formas

A plataforma de armazém de dados da empresa é DB2. Com base na estrutura do armazém de dados atual, a empresa descobriu que os modelos do DirectQuery funcionavam melhor do que os modelos de Importação, tendo em conta os requisitos.

> [!IMPORTANT]
> Proceda a uma prova de conceito técnica para avaliar o modo de armazenamento de modelo que funciona melhor. Além disso, explique aos modeladores de dados os modos de armazenamento de modelo e como podem escolher um modo adequado para o projeto.

### <a name="educate-authors-about-premium-licensing"></a>Dar formação aos autores sobre o licenciamento Premium

Já que era mais fácil começar a utilizar o Power BI (em comparação com a plataforma de BI legada), muitos dos adotantes iniciais foram pessoas que não tinham uma licença para a ferramenta BI anterior. Conforme esperado, o número de autores de conteúdo cresceu consideravelmente. Estes autores de conteúdo queriam partilhar o conteúdo com outras pessoas, o que resulta numa necessidade contínua de licenças adicionais do Power BI Pro.

A empresa fez um grande investimento em áreas de trabalho Premium, principalmente para distribuir conteúdo do Power BI a muitos utilizadores com licenças gratuitas do Power BI. A equipa de suporte trabalha com os autores de conteúdo para garantir que utilizam as áreas de trabalho Premium quando adequado, o que evita a alocação desnecessária de licenças do Power BI Pro quando um utilizador só precisa de consumir conteúdo.

> [!IMPORTANT]
> Surgem muitas vezes perguntas relativas ao licenciamento. Esteja preparado para dar formação e ajudar os autores de conteúdo a lidar com as perguntas de licenciamento. Confirme se os pedidos dos utilizadores para licenças do Power BI Pro são justificados.

### <a name="understand-the-data-gateways"></a>Compreender os gateways de dados

No início, a empresa possuía muitos gateways pessoais. A utilização de um cluster de gateway de dados no local muda os esforços de gestão para a equipa de BI central, que permite que a comunidade de autores de conteúdo se concentre na produção de conteúdo. A equipa de BI central trabalhou com a comunidade interna de utilizadores do Power BI para reduzir o número de gateways pessoais.

> [!IMPORTANT]
> Tenha um plano para criar e gerir gateways de dados no local. Decida quem tem permissão para instalar e utilizar um gateway pessoal e utilize as políticas de gateway para o impor.

### <a name="formalize-your-support-plan"></a>Formalizar o plano de suporte

Como a adoção do Power BI aumentou na organização, a empresa descobriu que uma abordagem de suporte de várias camadas funcionava bem:

- **Camada 1 – dentro da equipa:** as pessoas aprendem e ensinam-se mutuamente de forma diária.
- **Camada 2 – comunidade do Power BI:** as pessoas fazem perguntas na comunidade interna do Teams para aprenderem umas com as outras e comunicam informações importantes.
- **Camada 3 – equipa de BI central e COE:** as pessoas enviam pedidos por e-mail para obter assistência. São realizadas sessões no _horário de expediente_ duas vezes por semana para discutir os problemas e partilhar ideias coletivamente.

> [!IMPORTANT]
> Embora as duas primeiras camadas sejam menos formais, são tão importantes como a terceira camada de suporte. Os utilizadores experientes tendem a confiar principalmente nas pessoas que conhecem, enquanto os utilizadores mais recentes (ou aqueles que são o único analista de dados numa unidade de negócios ou num serviço partilhado) tendem a confiar mais no suporte formal.

### <a name="invest-in-training-and-governance"></a>Investir em formação e governação

No ano passado, a empresa melhorou as ofertas de formação interna e o programa de governação de dados. A comissão de governação inclui membros-chave de cada um dos grupos de análise distribuídos, além do COE.

Tem atualmente seis cursos internos sobre o Power BI no catálogo interno. O curso [Dashboard num dia](https://powerbi.microsoft.com/diad/) continua a ser um curso popular para principiantes. Para ajudar os utilizadores a aprofundar as competências, disponibilizam uma série de três cursos sobre o Power BI e dois cursos sobre DAX.

Uma das decisões de governação de dados mais importantes relacionadas com a gestão das capacidades Premium. A empresa optou por alinhar a capacidade dedicada com as principais áreas de análise em unidades de negócios e serviços partilhados. Assim, em caso de ineficiências, o impacto será apenas dentro dessa área, e os administradores da capacidade descentralizada poderão gerir a capacidade como entenderem.

> [!IMPORTANT]
> Preste atenção ao modo como as capacidades Premium são utilizadas e como as áreas de trabalho são atribuídas às mesmas.

## <a name="next-steps"></a>Passos seguintes

Outros recursos úteis:

- [Microsoft's BI transformation (Transformação de BI da Microsoft)](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Documento técnico sobre como planear uma implementação empresarial do Power BI](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Dashboard num dia](https://powerbi.microsoft.com/diad/)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

Os parceiros do Power BI experientes estão disponíveis para ajudar a sua organização a realizar o processo de migração com êxito. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).
