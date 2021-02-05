---
title: Limitações das Perguntas e Respostas do Power BI
description: Limitações atuais das Perguntas e Respostas do Power BI
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 09/09/2020
ms.openlocfilehash: 74e99f42677c6adda73a8b5e2e3043e2d039f5b3
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99569905"
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

**Suporte do DirectQuery para a funcionalidade Perguntas e Respostas** (pré-visualização)

A funcionalidade Perguntas e Respostas agora suporta origens do DirectQuery do SQL, incluindo o SQL Server 2019, a Base de Dados SQL do Azure e o Azure Synapse Analytics. Pode utilizar a funcionalidade Perguntas e Respostas para efetuar perguntas sobre linguagem natural nestas origens de dados. Existe uma pequena alteração no comportamento da funcionalidade Perguntas e Respostas quando está no modo DirectQuery: Após escrever a sua pergunta, seleciona o botão **Submeter**. Esta alteração evita a sobrecarga da origem do DirectQuery com consultas desnecessárias à medida que escreve.

### <a name="data-sources-not-supported"></a>Origens de dados não suportadas

A funcionalidade Perguntas e Respostas do Power BI não suporta atualmente as seguintes configurações:

- Segurança ao nível do objeto com qualquer tipo de origem de dados
- Modelos compostos
- Reporting Services 

## <a name="tooling-limitations"></a>Limitações de ferramentas

A nova caixa de diálogo de ferramentas permite que os utilizadores personalizem e melhorem a linguagem natural nas Perguntas e Respostas. Para saber mais sobre as ferramentas, leia a [introdução às ferramentas das Perguntas e Respostas](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Limitações da funcionalidade para rever perguntas

A funcionalidade para rever perguntas só armazena as perguntas feitas sobre o seu modelo de dados durante um máximo de 28 dias. Ao utilizar a nova funcionalidade para rever perguntas, poderá reparar que algumas perguntas não são registadas. Este comportamento é predefinido, uma vez que o motor de linguagem natural executa uma série de passos de limpeza de dados para garantir que todos os batimentos de teclas de um utilizador não são registados ou mostrados.

Os administradores do Power BI podem utilizar as definições de inquilinos para gerir a capacidade de armazenar perguntas. As permissões são baseadas em grupos de segurança. 

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
