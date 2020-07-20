---
title: Microsoft's BI transformation (Transformação de BI da Microsoft)
description: Saiba como a Microsoft gere uma cultura de dados para a tomada de decisões empresariais com êxito. Descreve a sua estratégia e visão para BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 8e1e590f871e1840209e72eb611bde7b21610c6e
ms.sourcegitcommit: c18130ea61e67ba111be870ddb971c6413a4b632
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/09/2020
ms.locfileid: "86162373"
---
# <a name="microsofts-bi-transformation"></a>Microsoft's BI transformation (Transformação de BI da Microsoft)

Este artigo destina-se a profissionais e gestores de TI. Ficará a saber mais sobre a nossa estratégia e visão de BI, o que nos permite tirar partido dos nossos dados como um ativo constantemente. Também ficará a saber como gerimos uma cultura de dados de tomada de decisões empresariais com êxito no Power BI.

Antes de mais, algum contexto: hoje em dia, a explosão de dados está a afetar os clientes e as empresas a uma velocidade incrível. Ter êxito neste ambiente intensivo em termos de dados requer que os analistas e executivos convertam quantidades enormes de dados em informações sucintas. As inovações nas ferramentas de BI da Microsoft mudaram a forma como a própria Microsoft explora os seus dados e obtém as informações necessárias para criar impacto na empresa.

Então, como pode a sua organização revolucionar também a forma como trabalha com dados? Vamos ajudá-lo a perceber ao partilhar a história do nosso percurso de transformação de BI.

## <a name="microsoft-journey"></a>O percurso da Microsoft

Há vários anos, na Microsoft, a nossa cultura organizacional incentivou indivíduos a obterem a total propriedade dos dados e informações. Também passou por alguma resistência cultural relativamente à realização de tarefas de forma padronizada. Por isso, a cultura organizacional levou a desafios na criação de relatórios e análises. Especificamente, levou a:

- Hierarquias, métricas, Indicadores Chave de Desempenho (KPIs) e definições de dados inconsistentes. Por exemplo, cada país tinha a sua forma de criar relatórios sobre as receitas. Não havia consistência, o que gerava confusão.
- Os analistas passavam 75% do tempo a recolher e a compilar dados.
- 78% dos relatórios eram criados em "ambiente offline".
- Mais de 350 sistemas e ferramentas de finanças centralizados.
- Aproximadamente 30 milhões USD por ano gastos em "aplicações sombra".

Estes desafios incentivaram-nos a pensar sobre como poderíamos melhorar estes processos. As equipas de finanças e outras equipas internas receberam suporte executivo para transformar o processo de revisão empresarial, o que levou à criação de uma plataforma de BI unificada como a nossa fonte de verdade. (Voltaremos a abordar a plataforma de BI mais à frente no artigo.) Por fim, estas inovações levaram à transformação das revisões empresariais, de vistas tabulares densas para elementos visuais mais simples e informativos em temas chave empresariais.

Como alcançámos este resultado? Fornecer uma BI centralizada e gerida por equipas de TI e alargá-la com o BI de gestão personalizada (SSBI) levou-nos ao sucesso. Descrevemo-la em duas formas criativas: _disciplina no núcleo_ e _flexibilidade na periferia_.

### <a name="discipline-at-the-core"></a>Disciplina no núcleo

Disciplina no núcleo significa que a equipa de TI obtém o controlo ao gerir uma única origem de dados principal. Fornecer BI empresarial padronizada e definir taxonomias e hierarquias de KPIs consistentes faz parte dessa disciplina. É importante que as permissões de dados sejam impostas centralmente para garantir que as nossas pessoas conseguem ler apenas os dados necessários.

Primeiro, compreendemos que a nossa transformação de BI não era um problema tecnológico. Para alcançar o sucesso, aprendemos primeiro a definição de sucesso e, em seguida, traduzimo-lo para métricas chave. Realçamos o quão importante foi para nós alcançar a consistência da definição nos nossos dados.

A nossa transformação não aconteceu de um dia para o outro. Priorizámos o fornecimento da tabela de indicadores subsidiária com cerca de 30 KPIs. Em seguida, ao longo de vários anos, expandimos gradualmente o número e a profundidade das áreas temáticas e criámos hierarquias de KPI mais complexas. Atualmente, isto permite-nos substituir KPIs de nível mais baixo ao nível do cliente por outros superiores ao nível da empresa. O nosso total de KPIs ultrapassa agora os 2000 e cada um é uma medida de sucesso fundamental e está em conformidade com os objetivos corporativos. Em toda a empresa, os relatórios corporativos e as soluções de SSBI apresentam KPIs bem definidos, consistentes e seguros.

### <a name="flexibility-at-the-edge"></a>Flexibilidade na periferia

Na periferia do núcleo, os nossos analistas nas equipas de Finanças, Vendas e Marketing tornaram-se mais flexíveis e ágeis. Agora tiram partido da capacidade de analisar dados mais rapidamente. Mais formalmente, este cenário é descrito como _BI de gestão personalizada (SSBI)_ . Agora compreendemos que o SSBI se baseia em _benefícios mútuos_ para as equipas de TI e os analistas. Experimentámos otimizações ao impulsionar a normalização, conhecimentos e reutilização dos nossos dados e soluções de BI. Além disso, como empresa, obtivemos mais valor em conjunto, à medida que fomos encontrando o equilíbrio certo entre a BI centralizada e o SSBI.

### <a name="our-solution"></a>A nossa solução

**Starlight** é o nome que damos à unificação dos nossos dados internos e plataforma de análise, que suporta finanças, vendas, marketing e engenharia. A sua missão é fornecer uma plataforma de dados dimensionável, partilhada e robusta. A plataforma foi totalmente criada pela equipa de finanças e continua atualmente em operação com os produtos Microsoft mais recentes.

O **KPI Lake** não é um Azure Data Lake. É um modelo tabular da Starlight alojado na IaaS do Azure com o Microsoft SQL Server Analysis Services. O modelo tabular fornece dados de mais de 100 origens internas e define várias hierarquias e KPIs. A sua missão é permitir comunicação do desempenho empresarial e equipas de análise nos departamentos de Finanças, Marketing e Vendas. Fá-lo para obter informações atempadas, precisas e com um bom desempenho através de modelos unificados de origens relevantes.

Quando foi implementado pela primeira vez, foi uma altura entusiasmante, porque o modelo tabular resultou em benefícios imediatos e mensuráveis. A primeira versão centralizava as plataformas de BI de Finanças e Marketing C+E. Ao longo dos últimos seis anos, foi alargada para consolidar soluções de informações empresariais adicionais. Atualmente, continua a evoluir ao criar potencial para as nossas revisões comerciais e globais, além da criação de relatórios padrão e SSBI. A sua adoção cresceu cinco vezes desde o seu lançamento. Muito além das nossas expectativas iniciais.

Eis um resumo dos principais benefícios:

- Fortalece a nossa tabela de indicadores subsidiária, as revisões empresariais em todo o mundo e a análise e relatórios de finanças, marketing e vendas.
- Suporta a análise de gestão personalizada, o que permite aos analistas descobrir informações ocultas nos dados.
- Fomenta a realização de relatórios e análises para compensação de incentivos, análise de marketing e operações, métricas de desempenho de vendas, revisões de liderança sénior e o processo de planeamento anual.
- Fornece ferramentas dinâmicas e automatizadas de análise, assim como relatórios de uma _única origem de verdade_.

O **KPI Lake** é uma história de grande sucesso. É muitas vezes apresentada aos nossos clientes para mostrar um exemplo de como utilizar eficazmente as nossas tecnologias mais recentes. Não é surpreendente que seja tão relevante para tantos deles.

#### <a name="how-it-works"></a>Como funciona

A plataforma Starlight gere o fluxo de dados desde a aquisição ao processamento e até à publicação:

1. A integração de dados ágil e robusta é agendada e consolida dados de mais de 100 origens não processadas distintas. Os sistemas de dados de origem incluem bases de dados relacionais, bases de dados do Azure Synapse e Azure Data Lake Storage. As áreas temáticas incluem finanças, marketing, vendas e engenharia.
2. Após testados, os dados são conformados e enriquecidos com lógica empresarial e dados globais. Em seguida, são carregados para tabelas de armazém de dados. O modelo tabular é atualizado.
3. Os analistas na empresa utilizam o Excel e o Power BI para fornecer informações e análises a partir do modelo tabular. Além disso, permite que os proprietários da empresa configurem definições de métricas para o respetivo negócio. Quando necessário, o dimensionamento é alcançado ao utilizar a IaaS do Azure com balanceamento de carga.

## <a name="deliver-success"></a>Sucesso no fornecimento

Todos queremos a nossa versão da verdade, desde que seja a nossa. No entanto, para algumas organizações, esta é a realidade. Têm múltiplas versões da verdade como resultado do esforço de individuais para alcançar a total propriedade dos dados e informações. Para estas organizações, esta abordagem não gerida não tende a ser o percurso para o sucesso.

É por isso que acreditamos que precisa de um _Centro de Excelência (COE)_ . Um COE é uma equipa central responsável pela definição de métricas e definições ao nível da empresa e muito mais. Também é uma função empresarial que organiza as pessoas, processos e componentes tecnológicos num conjunto completo de competências e capacidades empresariais.

Vemos muitas provas que suportam a ideia de que um COE abrangente e robusto é fundamental para oferecer valor e maximizar o sucesso empresarial. Pode incluir iniciativas de mudança, processos padrão, funções, orientações, melhores práticas, suporte, formação e muito mais.

Convidamo-lo a ler os artigos nesta série de COE para saber mais. Vamos ajudá-lo a descobrir como a sua organização pode adotar a mudança para obter sucesso.

## <a name="next-steps"></a>Próximos passos

No [próximo artigo desta série](center-of-excellence-establish.md), saiba como um COE ajudou a Microsoft a criar uma plataforma de dados e análise padrão para obter informações a partir dos nossos dados.

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Criar um Centro de Excelência](center-of-excellence-establish.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
