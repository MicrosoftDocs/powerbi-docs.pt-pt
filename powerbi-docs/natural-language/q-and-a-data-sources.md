---
title: Utilizar linguagem natural com a importação, a ligação em direto e a consulta direta
description: Neste artigo, veremos como funciona a funcionalidade Perguntas e Respostas com os diferentes tipos de origens de dados disponíveis no Power BI. Também vamos examinar os conceitos de indexação e colocação em cache.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: mohaali
ms.openlocfilehash: 85ecc5adc55daee86922c39e417db1cac5ba4a52
ms.sourcegitcommit: 0f807d3c74e5202b6e6a95fad49f2787928b9613
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706217"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>Utilizar linguagem natural com a importação, a ligação em direto e a consulta direta

A funcionalidade Perguntas e Respostas no Power BI permite-lhe obter rapidamente respostas a partir dos dados com linguagem natural para fazer perguntas sobre esses dados. Este artigo descreve como a indexação e a colocação em cache são utilizadas para melhorar o desempenho de cada configuração suportada.

## <a name="what-data-sources-are-supported-in-qa"></a>Que origens de dados são suportadas nas Perguntas e Respostas?

As Perguntas e Respostas são suportadas nas seguintes configurações:

- Modo de importação
- Modo de ligação em direto – com o SQL Server Analysis Services, o Azure Analysis Services ou os conjuntos de dados do Power BI no local
- Consulta Direta – Azure Synapse, Azure SQL e SQL Server 2019. Embora outras origens possam funcionar no modo de consulta direta, oficialmente, não suportamos a essas origens.

Por predefinição, as Perguntas e Respostas estarão ativadas num relatório se utilizar o elemento visual Perguntas e Respostas. Se estiver a utilizar a Consulta Direta ou a Ligação em direto, será apresentada uma mensagem. Pode ativar/desativar explicitamente as funções de linguagem natural de um relatório ao aceder às opções.

![Opções do ambiente de trabalho das Perguntas e Respostas](media/qna-desktop-options.png)

Para obter mais informações, veja [Limitações das Perguntas e Respostas do Power BI](q-and-a-limitations.md).

## <a name="how-does-indexing-work-with-qa"></a>Como funciona a indexação com as Perguntas e Respostas?

Quando ativa as Perguntas e Respostas, é criado um índice para disponibilizar rapidamente feedback em tempo real ao utilizador e para ajudar a interpretar as perguntas do utilizador. A criação do índice pode demorar algum tempo e terá os seguintes elementos e limitações.

- Todos os nomes de colunas e tabelas são inseridos no índice, a menos que tenham sido explicitamente desativados nas ferramentas de Perguntas e Respostas.
- Todos os valores de texto com menos de 100 carateres serão indexados. Os valores de texto com mais de 100 carateres não serão indexados. 
- As Perguntas e Respostas armazenam um máximo de 5 milhões valores exclusivos no índice. Se exceder este limiar, o índice não incluirá todos os potenciais valores, o que poderá diminuir a precisão dos resultados recebidos das Perguntas e Respostas.
- Se ocorrer um erro durante a indexação, o índice permanecerá num estado parcial e será recriado na próxima atualização, conforme descrito na próxima secção.

## <a name="how-often-is-the-index-refreshed-and-cached"></a>Com que frequência o índice é atualizado e colocado em cache?

No Power BI Desktop, o índice é criado quando utiliza as Perguntas e Respostas. É apresentado um pequeno ícone a informar que o índice está a ser criado. Durante esse tempo, o carregamento do elemento visual Perguntas e Respostas, incluindo as sugestões, pode demorar algum tempo.

No serviço Power BI, o índice é recriado aquando da publicação/republicação e atualização. O índice das Perguntas e Respostas nem sempre é criado automaticamente e, por vezes, será criado a pedido para otimizar as atualizações do conjunto de dados. Para a Consulta Direta, vamos indexar os dados, no máximo, uma vez por dia para reduzir o impacto na origem da mesma.

## <a name="next-steps"></a>Próximos passos

Pode integrar uma linguagem natural nos seus relatórios de diversas formas. Para obter mais informações, veja estes artigos:

* [Q&A visual](../visuals/power-bi-visualization-q-and-a.md) (Elemento visual Perguntas e Respostas)
* [Q&A best practices](q-and-a-best-practices.md) (Melhores práticas das Perguntas e Respostas)
