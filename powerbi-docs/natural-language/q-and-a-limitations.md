---
title: Limitações das Perguntas e Respostas do Power BI
description: Limitações atuais das Perguntas e Respostas do Power BI
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
ms.openlocfilehash: eebb40d81e9b59b545b30ce55dbf4a362b826455
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937591"
---
# <a name="limitations-of-power-bi-qa"></a>Limitações das Perguntas e Respostas do Power BI

A funcionalidade Perguntas e Respostas do Power BI tem atualmente algumas limitações.

## <a name="data-sources"></a>Origens de dados

### <a name="supported-data-sources"></a>Supported data sources (Origens de dados suportadas)

A funcionalidade Perguntas e Respostas do Power BI suporta as seguintes configurações de origens de dados no serviço Power BI:

- Modo de importação
- Ligação em direto ao Azure Analysis Services
- Ligação em direto ao SQL Server Analysis Services (com um gateway)
- Conjuntos de dados do Power BI.

Em cada uma destas configurações, também é suportada segurança ao nível da linha.

### <a name="data-sources-not-supported"></a>Origens de dados não suportadas

A funcionalidade Perguntas e Respostas do Power BI não suporta atualmente as seguintes configurações:

- Segurança ao nível do objeto com qualquer tipo de origem de dados
- O DirectQuery com qualquer origem. Uma alternativa é utilizar a Ligação em direto com o Azure Analysis Services, que utiliza o DirectQuery.
- Modelos compostos
- Reporting Services 

## <a name="tooling-limitations"></a>Limitações de ferramentas

A nova caixa de diálogo de ferramentas permite que os utilizadores personalizem e melhorem a linguagem natural nas Perguntas e Respostas. Para saber mais sobre as ferramentas, leia a [introdução às ferramentas das Perguntas e Respostas](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Limitações da funcionalidade para rever perguntas

A funcionalidade para rever perguntas só armazena as perguntas feitas sobre o seu modelo de dados durante um máximo de 28 dias. Ao utilizar a nova funcionalidade para rever perguntas, poderá reparar que algumas perguntas não são registadas. Este comportamento é predefinido, uma vez que o motor de linguagem natural executa uma série de passos de limpeza de dados para garantir que todos os batimentos de teclas de um utilizador não são registados ou mostrados.

Os administradores de inquilinos podem utilizar as definições de administração de inquilinos para gerir a capacidade de armazenar perguntas. As permissões são baseadas em grupos de segurança. 

Os utilizadores também podem impedir que as suas perguntas sejam registadas ao selecionar **Definições** > **Geral** e ao desselecionar **Permitir que as Perguntas e Respostas registem a minha expressão**. 

## <a name="teach-qa-limitations"></a>Limitações da funcionalidade Ensinar Perguntas e Respostas

A funcionalidade Ensinar Perguntas e Respostas permite-lhe corrigir dois tipos de erros:

- Atribuir uma palavra a um campo.
- Atribuir uma condição de filtro a uma palavra.

Atualmente, não suportamos a redefinição de um termo reconhecido ou a definição de outros tipos de condições ou frases. Além disso, ao definir condições de filtragem, só pode utilizar um subconjunto limitado de linguagem, incluindo:

- País, que é EUA
- País, que não é EUA
- Produtos > 100
- Produtos é maior do que 100
- Produtos = 100
- Produtos é 100
- Produtos < 100
- Produtos é menos do que 100

> [!NOTE]
> As ferramentas das Perguntas e Respostas só suportam o modo de importação. Ainda não suportam a ligação a uma origem de dados do Azure Analysis Services ou no local. Esta limitação atual será removida nas versões subsequentes do Power BI.

### <a name="statements-not-supported"></a>Instruções não suportadas

- Não são suportadas múltiplas condições. Como alternativa, crie uma coluna calculada DAX que avalia um valor booleano de instrução com múltiplas condições e utilize esse campo.
- Se não especificar uma condição de filtro quando a funcionalidade Perguntas e Respostas pedir um subconjunto de dados, não será possível guardar a definição, mesmo que a instrução inteira não tenha sublinhados a vermelho.

## <a name="next-steps"></a>Passos seguintes

Existem diversas melhores práticas para melhorar o motor de linguagem natural. Para obter mais informações, veja [Melhores práticas das Perguntas e Respostas](q-and-a-best-practices.md).
