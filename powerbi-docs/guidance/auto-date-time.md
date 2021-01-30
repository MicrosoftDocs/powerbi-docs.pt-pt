---
title: Auto date/time guidance in Power BI Desktop (Orientação de data/hora Automáticas no Power BI Desktop)
description: Orientação para utilizar a funcionalidade de data/hora automática no Power BI Desktop.
author: peter-myers
ms.author: kfollis
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 10/23/2019
ms.openlocfilehash: e7fcab58dc61735639689c4574a9ce89757882ca
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088678"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Auto date/time guidance in Power BI Desktop (Orientação de data/hora Automáticas no Power BI Desktop)

Este artigo destina-se aos modeladores de dados que criam Modelos de importação ou Composição no Power BI Desktop. Fornece orientação, recomendações e considerações ao utilizar a funcionalidade _Data/hora automática_ do Power BI Desktop em situações específicas. Para obter uma descrição geral e uma introdução geral à _Data/hora automática_, veja [Data/hora automática no Power BI Desktop](../transform-model/desktop-auto-date-time.md).

A opção _Data/hora automática_ fornece análise de tempo conveniente, rápida e fácil de utilizar. Os autores de relatórios podem trabalhar com a análise de tempo ao filtrar, agrupar e desagregar os períodos de tempo do calendário.

## <a name="considerations"></a>Considerações

A seguinte lista com marcas descreve as considerações e as possíveis limitações relacionadas à opção _Data/hora automática_.

- **Aplica-se a todas ou a nenhuma:** quando a opção _Data/hora automática_ está ativada, será aplicada a todas as colunas de data nas tabelas de Importação que não estão na parte &quot;muitas&quot; da relação. Não pode ser seletivamente ativada ou desativada numa base coluna a coluna.
- **Apenas períodos de calendário:** as colunas anual e trimestral estão relacionadas com os períodos de calendário, o que significa que o ano começa a 1 de janeiro e termina a 31 de dezembro. Não é possível personalizar a data de início (ou conclusão) do ano.
- **Personalização:** não é possível personalizar os valores utilizados para descrever os períodos de tempo. Além disso, também não é possível adicionar colunas adicionais para descrever outros períodos de tempo, por exemplo, semanas.
- **Filtragem por ano:** os valores das colunas **Trimestral**, **Mensal** e **Diário** não incluem o valor anual. Por exemplo, a coluna **Mensal** contém apenas os nomes dos meses (ou seja, janeiro, fevereiro, etc.). Os valores não são totalmente autodescritivos e, em alguns designs de relatório, podem não comunicar o contexto do filtro anual.

    É por isso que é importante que os filtros ou agrupamentos ocorram na coluna **Anual**. Ao desagregar com a hierarquia, o ano será filtrado, exceto se o nível **Anual** for intencionalmente removido. Se não existir um filtro ou grupo por ano, um agrupamento por mês, por exemplo, resumirá os valores em todos os anos para esse mês.
- **Filtragem de data de tabela única:** dado que cada coluna de datas produz a sua própria tabela de data/hora automática (oculta), não é possível aplicar um filtro de tempo a uma das tabelas e que este seja propagado a várias tabelas de modelos. A filtragem desta forma é um requisito de modelação comum ao efetuar relatórios sobre vários assuntos (tabelas de tipo de facto), como vendas e orçamento de vendas. Ao utilizar a funcionalidade de data/hora automática, o autor do relatório precisará de aplicar filtros a cada coluna de data diferente.
- **Tamanho do modelo:** para cada coluna de data que gerar uma tabela de data/hora automática oculta, resultará no aumento do tamanho de modelo e também no prolongamento do tempo de atualização.
- **Outras ferramentas de relatórios:** não é possível trabalhar com tabelas de data/hora automáticas ao:
  - Utilizar a funcionalidade [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md).
  - Utilizar estruturadores de consultas do Analysis Services em relatórios paginados do Power BI.
  - Ligar ao modelo com estruturadores de relatórios não pertencentes ao Power BI.

## <a name="recommendations"></a>Recomendações

Recomendamos que mantenha a opção _Data/hora automática_ ativada apenas quando trabalha com períodos de tempo de calendário e quando tem requisitos de modelo simplistas em relação ao tempo. Esta opção pode também ser conveniente ao criar modelos ad hoc ou ao executar exploração de dados ou criação de perfis.

Quando a origem de dados já definir uma tabela de dimensão de data, esta tabela deverá ser utilizada para definir o tempo de forma consistente na sua organização. Será certamente o caso se a origem de dados for um armazém de dados. Caso contrário, pode gerar tabelas de datas no modelo com as funções [CALENDÁRIO](/dax/calendar-function-dax)ou [CALENDARAUTO](/dax/calendarauto-function-dax) do DAX. Em seguida, pode adicionar colunas calculadas para suportar os requisitos de agrupamento e filtragem de tempo conhecidos. Esta abordagem de conceção pode permitir-lhe criar uma tabela de datas única que será propagada a todas as tabelas de tipo de facto e que poderá resultar numa tabela única para aplicar filtros de tempo. Para obter mais informações sobre a criação de tabelas de datas, leia o artigo [Definir e utilizar tabelas de datas no Power BI Desktop](../transform-model/desktop-date-tables.md).

Se a opção _Data/hora automática_ não for relevante para os seus projetos, recomendamos que desative a opção _Data/hora automática_ global. Garantirá, assim, que todos os novos ficheiros do Power BI Desktop que criar não ativarão a opção _Data/hora automática_.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Criar tabelas de data no Power BI Desktop](model-date-tables.md)
- [Data/Hora Automáticas no Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Definir e utilizar tabelas de datas no Power BI Desktop](../transform-model/desktop-date-tables.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
