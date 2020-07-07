---
title: Criar tabelas de datas no Power BI Desktop
description: Técnicas e orientação para a criação de tabelas de datas no Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2020
ms.author: v-pemyer
ms.openlocfilehash: ad85ad56db907ca19af7dc14681eb34f8c2b9abc
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85398346"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Criar tabelas de datas no Power BI Desktop

Este artigo destina-se aos modeladores de dados que trabalham com o Power BI Desktop. Descreve boas práticas de conceção para criar tabelas de datas nos modelos de dados.

Para trabalhar com as [funções de análise de tempo](/dax/time-intelligence-functions-dax) DAX (Data Analysis Expressions), existe um requisito no modelo de pré-requisitos: tem de ter, pelo menos, uma _tabela de datas_ no modelo. Uma tabela de datas é uma tabela que satisfaz os seguintes requisitos:

> [!div class="checklist"]
> - Deve ter uma coluna de tipo de dados de **data** (ou **data/hora**) – conhecida como a _coluna de data_.
> - A coluna de data deve conter valores exclusivos.
> - A coluna de data não deve conter espaços EM BRANCO.
> - A coluna de data não deve ter datas em falta.
> - A coluna de data deve abranger anos completos. Um ano não é necessariamente um ano de calendário (janeiro a dezembro).
> - A tabela de datas deve ser [assinalada como uma tabela de datas](../transform-model/desktop-date-tables.md#setting-your-own-date-table).

Pode utilizar qualquer uma de várias técnicas para adicionar uma tabela de datas ao modelo:

- A opção Data/hora automática
- O Power Query para ligar a uma tabela de dimensões de datas
- O Power Query para gerar uma tabela de datas
- A DAX para gerar uma tabela de datas
- A DAX para clonar uma tabela de datas existente

> [!TIP]
> Uma tabela de datas é talvez a funcionalidade mais consistente que irá adicionar a qualquer um dos modelos. Adicionalmente, dentro de uma organização, uma tabela de datas deve ser consistentemente definida. Por isso, independentemente de qual for a técnica que decidir utilizar, recomendamos que crie um [modelo do Power BI Desktop](../create-reports/desktop-templates.md) que inclua uma tabela de datas totalmente configurada. Partilhe o modelo com todos os modeladores da sua organização. Assim, sempre que alguém desenvolver um novo modelo, podem começar com uma tabela de datas definida de forma consistente.

## <a name="use-auto-datetime"></a>Utilizar a opção Data/hora automática

A opção [Data/hora automática](../transform-model/desktop-auto-date-time.md) fornece análise de tempo conveniente, rápida e fácil de utilizar. Os autores de relatórios podem trabalhar com a análise de tempo ao filtrar, agrupar e desagregar os períodos de tempo do calendário.

Recomendamos que mantenha a opção Data/hora automática ativada apenas quando trabalha com períodos de tempo de calendário e quando tem requisitos de modelo simplistas em relação ao tempo. Esta opção pode também ser conveniente ao criar modelos ad hoc ou ao executar exploração de dados ou criação de perfis. Esta abordagem, no entanto, não suporta a conceção de tabela de data única para propagar filtros para várias tabelas. Para obter mais informações, veja [Orientação de data/hora automática no Power BI Desktop](auto-date-time.md).

## <a name="connect-with-power-query"></a>Ligar-se ao Power Query

Se as origens de dados já tiverem uma tabela de datas, recomendamos que a utilize como a origem da tabela de datas do modelo. É normalmente o caso quando se está a ligar a um armazém de dados, já que este terá uma tabela de dimensões de datas. Desta forma, o modelo tira partido de ter uma única origem de verdade para a hora na sua organização.

Se estiver a desenvolver um modelo do DirectQuery e a origem de dados não incluir uma tabela de datas, recomendamos vivamente que adicione uma tabela de datas à origem de dados. Deve cumprir todos os requisitos de modelação de uma tabela de datas. Em seguida, pode utilizar o Power Query para ligar à tabela de datas. Desta forma, os cálculos do modelo podem tirar partido das funcionalidades de análise de tempo DAX.

## <a name="generate-with-power-query"></a>Gerar com o Power Query

Pode gerar uma tabela de datas com o Power Query. Veja a seguir duas entradas de blogue que mostram como o fazer:

- [Criar uma Dimensão de Datas com um Script do Power Query](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/) por Matt Masson
- [Gerar uma Tabela de Dimensões de Datas no Power Query](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/) por Chris Webb

> [!TIP]
> Se não possuir um armazém de dados ou outra definição consistente para a hora na sua organização, considere utilizar o Power Query para publicar um [fluxo de dados](../transform-model/service-dataflows-overview.md). Em seguida, deve ligar todos os modeladores de dados ao fluxo de dados para adicionar as tabelas de datas aos modelos. O fluxo de dados torna-se na única origem de verdade para a hora na sua organização.

Se precisar de gerar uma tabela de datas, considere fazê-lo com a DAX. Poderá ser mais fácil. Adicionalmente, é provável que seja mais conveniente, dado que a DAX inclui alguma inteligência incorporada para simplificar a criação e gestão de tabelas de datas.

## <a name="generate-with-dax"></a>Gerar com a DAX

Pode gerar uma tabela de datas no modelo ao criar uma tabela calculada com as funções DAX [CALENDAR](/dax/calendar-function-dax) ou [CALENDARAUTO](/dax/calendarauto-function-dax). Cada função devolve uma tabela de datas de coluna única. Em seguida, pode estender a tabela calculada com colunas calculadas para suportar os requisitos de agrupamento e de filtragem de intervalos de datas.

- Utilize a função **CALENDAR** quando quiser definir um intervalo de datas. Transmite dois valores: a data de início e a data de fim. Estes valores podem ser definidos por outras funções DAX, como `MIN(Sales[OrderDate])` ou `MAX(Sales[OrderDate])`.
- Utilize a função **CALENDARAUTO** quando quiser que o intervalo de datas envolva automaticamente todas as datas armazenadas no modelo. Pode transmitir um único parâmetro opcional que é o fim do mês do ano (se o ano for um ano de calendário, que termina em dezembro, não precisará de transmitir nenhum valor). É uma função útil, porque garante que são devolvidos anos completos de datas – é um requisito para uma tabela de datas marcada. Além disso, não precisa de gerir a extensão da tabela para anos futuros: quando uma atualização de dados é concluída, esta aciona um novo cálculo da tabela. O novo cálculo estenderá automaticamente o intervalo de datas da tabela quando as datas para um novo ano forem carregadas no modelo.

## <a name="clone-with-dax"></a>Clonar com a DAX

Quando o modelo já incluir uma tabela de datas e precisar de uma tabela de datas adicional, poderá facilmente clonar a tabela de datas existente. É o caso quando a data é uma [dimensão de reprodução de funções](star-schema.md#role-playing-dimensions). Pode clonar uma tabela ao criar uma tabela calculada. A expressão da tabela calculada é simplesmente o nome da tabela de datas existente.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Data/Hora Automáticas no Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Orientação de data/hora automáticas no Power BI Desktop](auto-date-time.md)
- [Definir e utilizar tabelas de datas no Power BI Desktop](../transform-model/desktop-date-tables.md)
- [Preparação personalizada de dados no Power BI](../transform-model/service-dataflows-overview.md)
- [Função CALENDAR (DAX)](/dax/calendar-function-dax)
- [Função CALENDARAUTO (DAX)](/dax/calendarauto-function-dax)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
