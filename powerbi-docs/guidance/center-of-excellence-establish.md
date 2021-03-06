---
title: Criar um Centro de Excelência
description: Saiba como um Centro de Excelência ajudou a Microsoft a criar uma plataforma de análise e de dados padronizada. Esta plataforma tem como objetivo desbloquear informações com o modelo operativo certo, envolvimento dos intervenientes e investimentos partilhados e dedicados.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: f3cdf40c0cdb17269232093f7407c61b13794a3e
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088655"
---
# <a name="establish-a-center-of-excellence"></a>Criar um Centro de Excelência

Este artigo destina-se a profissionais e gestores de TI. Irá aprender a configurar um Centro de Excelência (COE) de BI e de análise na sua organização. Também irá saber como a Microsoft configurou os seus.

Alguns têm uma ideia errada de que um COE é apenas um serviço de apoio. No entanto, esta ideia está longe da realidade.

De um modo geral, um COE de BI e de análise é uma equipa de profissionais responsáveis pela criação e manutenção de uma plataforma de BI. Também é responsável por criar uma única origem da verdade e definir um conjunto de métricas consistentes em toda a empresa para desbloquear e acelerar informações. No entanto, um COE é um termo geral. Como tal, pode ser implementado e gerido de formas diferentes e a sua estrutura e âmbito podem variar de organização para organização. Em essência, trata-se sempre de uma plataforma robusta que fornece os dados e capacidades de informação certos, às pessoas certas, no momento certo. Idealmente, também promove a evangelização, preparação e suporte. Na Microsoft, é descrito como sendo essencialmente uma _[disciplina](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ e é apresentado como sendo a nossa plataforma de BI e única origem da verdade.

Em organizações maiores, poderia encontrar múltiplos COEs, com o COE principal _alargado_ por COEs satélite, muitas vezes ao nível do departamento. Desta forma, um COE satélite é um grupo de especialistas familiarizados com taxonomias e definições, que sabem transformar dados principais naquilo que faz sentido _para o departamento deles_. Os analistas departamentais recebem permissões para aceder a dados principais e confiam nos mesmos para serem utilizados nos seus próprios relatórios. Criam soluções que dependem de dimensões, factos e lógica de negócio fundamentais e cuidadosamente preparados. Por vezes, podem também alargá-lo com conjuntos de dados mais pequenos, específicos do departamento e lógica de negócio. O importante é que os COEs satélite nunca são desligados nem agem isoladamente. Na Microsoft, os COEs satélite promovem a _[flexibilidade no limite](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

Para que este cenário alargado seja bem sucedido, os departamentos têm de _pagar para participar_. Por outras palavras, os departamentos têm de investir financeiramente no COE principal. Desta forma, não há a preocupação de que "não estejam a receber por igual" ou de que os seus requisitos sejam passados para segundo plano.

Para suportar este cenário, o COE principal tem de ser adaptado para satisfazer as necessidades departamentais financiadas. Após terem sido integrados vários conjuntos de dados, são definidas economias de escala. Na Microsoft, tornou‑se rapidamente evidente que trabalhar centralmente é mais económico e traz resultados mais depressa. Quando cada nova área temática foi integrada, observámos economias de escala ainda maiores que permitiram potenciar e contribuir em toda a plataforma, reforçando a nossa cultura de dados subjacente.

Considere um exemplo: A nossa plataforma de BI oferece dimensões, factos e lógica de negócio fundamentais para Finanças, Vendas e Marketing. Também define centenas de Indicadores‑Chave de Desempenho (KPIs). Agora, um analista no negócio do Power Platform precisa de preparar um dashboard de liderança. Alguns dos KPIs, como receitas e pipelines, vêm diretamente da plataforma de BI. No entanto, outros baseiam-se em necessidades mais granulares do negócio. Uma dessas necessidades é um KPI sobre a adoção dos utilizadores da funcionalidade específica do Power BI: os fluxos de dados. Assim, o analista produz um [modelo composto](composite-model-guidance.md) do Power BI para integrar os dados principais da plataforma de BI com dados departamentais. Em seguida, adiciona lógica de negócio para definir os seus KPIs departamentais. Por fim, cria o seu dashboard de liderança com base no novo modelo, que potencia os recursos COE em toda a empresa, amplificados com conhecimentos e dados locais.

Acima de tudo, uma divisão de responsabilidade entre o COE principal e os COEs satélite permite aos analistas departamentais fazerem novas descobertas em vez de gerirem uma plataforma de dados. Por vezes, pode até haver uma relação mutuamente benéfica entre os COEs satélite e o COE principal. Por exemplo, um COE satélite pode definir novas métricas que, tendo sido benéficas para o seu departamento, acabam por se tornar métricas principais, benéficas para toda a empresa, disponíveis e suportadas pelo COE principal.

## <a name="bi-platform"></a>Plataforma de BI

Na sua organização, o COE pode ser reconhecido por um nome diferente, como equipa ou grupo de BI. O nome é menos importante do que aquilo que realmente faz. Se não tiver uma equipa formalizada, recomendamos que cultive uma equipa que reúna os principais especialistas em BI para estabelecer a sua plataforma de BI.

Na Microsoft, o COE é conhecido como a Plataforma de BI. Esta tem muitos grupos de intervenientes que representam diferentes divisões dentro da empresa, como Finanças, Vendas e Marketing. Está organizada para executar [capacidades partilhadas](#shared-capabilities) e [entregas dedicadas](#dedicated-deliveries).

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="O diagrama mostra as capacidades partilhadas e as entregas dedicadas, que são descritas nas secções seguintes.":::

### <a name="shared-capabilities"></a>Capacidades partilhadas

As capacidades partilhadas são necessárias para estabelecer e operar a plataforma de BI. Apoiam todos os grupos intervenientes que financiam a plataforma. Consistem nas seguintes equipas:

- **Engenharia de plataformas principais:** Concebemos a plataforma de BI com uma mentalidade focada na engenharia. É, na realidade, um conjunto de estruturas que suportam a ingestão de dados, o processamento para enriquecer os dados e a entrega desses dados em modelos semânticos de BI para consumo dos analistas. Os engenheiros são responsáveis pela conceção técnica e implementação das capacidades principais da plataforma de BI. Por exemplo, concebem e implementam os pipelines de dados.
- **Infraestruturas e alojamento:** Os engenheiros de TI são responsáveis pelo aprovisionamento e gestão de todos os serviços da Azure.
- **Suporte e operação:** Esta equipa mantém a plataforma a funcionar. O suporte cuida das necessidades do utilizador, como as permissões de dados. As operações mantêm a plataforma em funcionamento ao garantirem que os Contratos de Nível de Serviço (SLAs) são cumpridos e ao comunicarem atrasos ou falhas.
- **Gestão de versões:** Alterações nas versões dos gestores de programas técnicos (PMs). As alterações podem ir de atualizações da estrutura da plataforma a alterações de pedidos feitos a modelos semânticos de BI. São a última linha de defesa para garantir que as mudanças não danificam nada.

### <a name="dedicated-deliveries"></a>Entregas dedicadas

Há uma equipa de entregas dedicada para cada grupo de intervenientes. É tipicamente composta por um engenheiro de dados, um engenheiro de análise e um PM técnico, todos financiados pelo seu grupo de intervenientes.

## <a name="bi-team-roles"></a>Funções da equipa de BI

Na Microsoft, a nossa plataforma de BI é operada por equipas de profissionais dimensionáveis. As equipas são alinhadas através de recursos dedicados e partilhados. Hoje em dia, temos as seguintes funções:

- **Gestores de programas:** Os PMs são um recurso dedicado. Funcionam como o principal contacto entre a equipa de BI e os intervenientes. A sua função é a de traduzir os requisitos de negócio dos intervenientes para uma especificação técnica. Além disso, gerem a priorização dos produtos dos intervenientes.
- **Líderes da base de dados:** São um recurso dedicado responsável por integrar novos conjuntos de dados no armazém de dados centralizado. A integração de um conjunto de dados pode implicar a criação de dimensões conformes e, consequentemente, a adição de lógica de negócio e atributos personalizados, assim como formatação e nomes padrão.
- **Líderes de análise:** são um recurso dedicado responsável pela conceção e desenvolvimento de modelos semânticos de BI. Empenham-se em aplicar uma arquitetura consistente através da utilização de formatação e nomes padrão. A otimização do desempenho é uma parte importante da sua função.
- **Operações e infraestrutura:** São um recurso partilhado responsável pela gestão de tarefas e pipelines de dados. São também responsáveis pela gestão de subscrições do Azure, capacidades do Power BI, máquinas virtuais e gateways de dados.
- **Suporte:** são um recurso partilhado responsável por escrever documentação, organizar a preparação, comunicar alterações de modelos semânticos de BI e responder a perguntas dos utilizadores.

## <a name="governance-and-compliance"></a>Governação e conformidade

Para cada grupo de intervenientes, os líderes de PMs fornecem governação e supervisão transversal aos programas. O seu objetivo principal é garantir que os investimentos em TI gerem valor de negócio e mitigam o risco. As reuniões dos comités de direção são realizadas regularmente para analisar os progressos e aprovar grandes iniciativas.

## <a name="grow-your-own-community"></a>Expandir a sua própria comunidade

Estabeleça e expanda uma comunidade dentro da sua organização ao:

- Realizar eventos regulares no “Horário de Expediente” para reservar tempo com a equipa de BI para permitir que as pessoas coloquem perguntas, façam sugestões, partilhem ideias e, até mesmo, apresentem reclamações.
- Criar um canal do Teams para dar suporte e incentivar qualquer pessoa a perguntar e responder às perguntas publicadas.
- Gerir e promover grupos de utilizadores informais e incentivar os funcionários a fazerem apresentações ou a participarem.
- Gerir eventos de preparação mais formais sobre produtos específicos e na própria plataforma de BI. Pondere proporcionar o [Dashboard do Power BI Num Dia](https://powerbi.microsoft.com/diad/), disponível como um kit de curso gratuito e uma ótima forma de apresentar o Power BI aos funcionários pela primeira vez.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre este artigo, consulte os seguintes recursos:

- [Arquitetura da solução de BI no COE](center-of-excellence-business-intelligence-solution-architecture.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)

No [próximo artigo desta série](center-of-excellence-business-intelligence-solution-architecture.md), fique a conhecer a arquitetura da solução de BI no COE, bem como as diferentes tecnologias utilizadas.

### <a name="professional-services"></a>Serviços profissionais

Os parceiros certificados do Power BI estão disponíveis para ajudar a sua organização a ser bem-sucedida na preparação de um COE. Estes podem proporcionar-lhe uma preparação económica ou uma auditoria dos dados. Para envolver um parceiro do Power BI, visite o [portal de parceiros do Power BI](https://powerbi.microsoft.com/partners/).

Também pode interagir com parceiros de consultoria experientes. Estes podem ajudar a [analisar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [avaliar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) ou [implementar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) o Power BI.
