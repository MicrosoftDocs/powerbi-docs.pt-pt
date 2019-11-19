---
title: Limitações das Perguntas e Respostas do Power BI
description: Limitações atuais das Perguntas e Respostas do Power BI
author: mohaali
manager: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: fc4a605f1258bcd93e0b49b596cc3a1691ce2edb
ms.sourcegitcommit: 26123c6bb24c8174beb390f4e06fb938d31238ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72717602"
---
# <a name="limitations-of-power-bi-qa"></a>Limitações das Perguntas e Respostas do Power BI

A funcionalidade Perguntas e Respostas do Power BI tem atualmente algumas limitações.

## <a name="data-sources"></a>Origens de dados

### <a name="supported-data-sources"></a>Supported data sources (Origens de dados suportadas)

A funcionalidade Perguntas e Respostas do Power BI suporta as seguintes configurações de origens de dados no serviço Power BI:

- Modo de importação
- Ligação em direto ao Azure Analysis Services
- Ligação em direto ao SQL Server Analysis Services (com um gateway)
- Conjuntos de dados do Power BI. O Power BI Desktop comunica um erro nas Perguntas e Respostas ao utilizar um conjunto de dados do Power BI. No entanto, ao publicar o relatório no serviço Power BI, o erro desaparece.

Em cada uma destas configurações, também é suportada segurança ao nível da linha.

### <a name="data-sources-not-supported"></a>Origens de dados não suportadas

A funcionalidade Perguntas e Respostas do Power BI não suporta atualmente as seguintes configurações:

- Segurança ao nível do objeto com qualquer tipo de origem de dados
- O DirectQuery com qualquer origem. Uma alternativa para proporcionar suporte neste caso é utilizar a Ligação em direto com o Azure Analysis Services, que utiliza o DirectQuery.
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

- "País", que é "EUA"
- "País", que não é "EUA"
- "Ponderação" > 2000
- "Ponderação" = 2000
- "Ponderação" < 2000

> [!NOTE]
> As ferramentas das Perguntas e Respostas só suportam o modo de importação. Ainda não suportam a ligação a uma origem de dados do Azure Analysis Services ou no local. Esta limitação atual será removida nas versões subsequentes do Power BI.

### <a name="statements-not-supported"></a>Instruções não suportadas

- Atualmente, a utilização de medidas em condições não é suportada. Como alternativa, converta as medidas em colunas calculadas para que funcionem.
- Não são suportadas múltiplas condições. Como alternativa, crie uma coluna calculada DAX que avalia um valor booleano de instrução com múltiplas condições e utilize esse campo.
- Se não especificar uma condição de filtro quando a funcionalidade Perguntas e Respostas pedir um subconjunto de dados, não será possível guardar a definição, mesmo que a instrução inteira não tenha sublinhados a vermelho.
