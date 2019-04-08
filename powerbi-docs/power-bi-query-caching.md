---
title: Colocação em cache de consultas no Power BI Premium
description: Colocação em cache de consultas no Power BI Premium
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/03/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: fbfd8c98743144e0c9604aca4174d6ef32916e77
ms.sourcegitcommit: de0b72915183a8a784d3227838bd704c1c209422
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/04/2019
ms.locfileid: "58914282"
---
# <a name="query-caching-in-power-bi-premium"></a>Colocação em cache de consultas no Power BI Premium

As organizações com o Power BI Premium podem tirar partido da *colocação em cache de consultas* para acelerar os relatórios associados a um conjunto de dados. A colocação em cache de consultas dá instruções à capacidade Premium para utilizar o serviço de colocação em cache local para manter os resultados de consulta, evitando que a origem de dados subjacente efetue a computação desses resultados.

> [!IMPORTANT]
> A colocação em cache de consultas só está disponível no Power BI Premium. Não se aplica a conjuntos de dados do Live Connect que tirem partido do Azure Analysis Services ou do SQL Server Analysis Services.

Os resultados de consultas em cache são específicos do contexto do utilizador e conjunto de dados e respeitam sempre as regra de segurança. Neste momento, o serviço só efetua a colocação em cache de consultas da página inicial à qual aceder. Ou seja, as consultas não são colocadas em cache quando interagir com o relatório. A cache reflete os marcadores pessoais e filtros persistentes. Os [mosaicos do dashboard](service-dashboard-tiles.md) que são alimentados pelas mesmas consultas também beneficiam da colocação em cache da consulta. O desempenho é particularmente otimizado quando um conjunto de dados é acedido com frequência e não precisa de ser atualizado muitas vezes. A colocação em cache de consultas também pode reduzir a carga na sua capacidade Premium ao reduzir o número geral de consultas.

Pode controlar o comportamento da colocação em cache de consultas na página **Definições** do conjunto de dados no serviço Power BI. Existem três definições possíveis:

- **Predefinição de Capacidade**: o conjunto de dados herda a definição da capacidade Premium. A predefinição de capacidade é controlada pelo administrador da capacidade do Power BI Premium.

- **Inativa**: não utilizar a colocação em cache da consulta para este conjunto de dados.

- **Ativa**: utilizar a colocação em cache da consulta para este conjunto de dados.

![Caixa de diálogo da colocação em cache da consulta](media/power-bi-query-caching/power-bi-query-caching.png)

> [!NOTE]
> Ao alterar as definições de colocação em cache de **Ativa** para **Inativa**, todos os resultados da consulta guardados anteriormente para o conjunto de dados serão removidos da cache da capacidade. Pode desativar explicitamente a colocação em cache ou revertê-la para a predefinição de capacidade que um administrador tenha definido como **Inativa**. A desativação pode provocar um pequeno atraso na próxima vez que um relatório executar consultas neste conjunto de dados. O atraso é causado pelas consultas de relatório executadas a pedido que não estejam a tirar partido dos resultados guardados. Além disso, o conjunto de dados necessário poderá ter de ser carregado na memória antes de poder responder a consultas.


