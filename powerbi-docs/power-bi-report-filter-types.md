---
title: Tipos de filtros nos relatórios do Power BI
description: Adicionar um filtro de página, um filtro de visualização ou um filtro de relatório a um relatório no Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c96b4ebae574a3b6a6fa54c5f5dc99b5bc948a90
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874404"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Tipos de filtros nos relatórios do Power BI

Os filtros não se comportam todos da mesma forma porque não foram criados da mesma forma. O modo como os cria influencia o comportamento no novo painel de filtro no modo de edição. Neste artigo, descrevemos os diferentes tipos de filtros: as diferentes formas de os criar e os diferentes fins a que se destinam. Saiba mais sobre como [adicionar filtros para relatórios](power-bi-report-add-filter.md). 

![Painel de filtro](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Vamos começar com os dois tipos de filtros mais comuns: os manuais e os automáticos.

## <a name="manual-filters"></a>Filtros manuais 

Os filtros manuais são os filtros que os criadores de relatórios arrastam e soltam em qualquer ponto do novo painel de filtro. Os utilizadores com permissão de edição do relatório podem editar, eliminar, limpar, ocultar, bloquear, mudar o nome ou ordenar este filtro no novo painel.

## <a name="automatic-filters"></a>Filtros automáticos 

Os filtros automáticos são adicionados automaticamente ao nível do elemento visual do painel de filtro quando cria um elemento visual. Estes filtros baseiam-se nos campos que constituem o elemento visual. Os utilizadores com permissão de edição do relatório podem editar, limpar, ocultar, bloquear, mudar o nome ou ordenar este filtro no novo painel. Não podem eliminar os filtros automáticos, porque o elemento visual refere-se a esses campos.

## <a name="more-advanced-filters"></a>Filtros mais avançados

Os tipos de filtro descritos em seguida são menos comuns, mas também é importante compreendê-los para o caso de serem apresentados no relatório. Além disso, poderá achar que são úteis quando for necessário criar um filtro mais adequado para o relatório.

## <a name="include-and-exclude-filters"></a>Filtros de inclusão e exclusão

Os filtros de inclusão e exclusão são automaticamente adicionados ao painel de filtro quando quer incluir ou excluir um elemento visual. Os utilizadores com permissão de edição do relatório podem eliminar, bloquear, ocultar ou ordenar este filtro no novo painel. Não podem editar, limpar ou mudar o nome de um filtro de inclusão ou exclusão, porque está associado à funcionalidade de inclusão e exclusão dos elementos visuais.

![Filtro de exclusão](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Filtros de desagregação

Os filtros de desagregação são automaticamente adicionados ao painel de filtro para desagregar um elemento visual no relatório. Os utilizadores com permissão de edição do relatório podem editar ou limpar o filtro no novo painel. Não podem eliminar, ocultar, bloquear, mudar o nome ou ordenar este filtro, uma vez que está associado à funcionalidade de desagregação dos elementos visuais. Para remover o filtro de desagregação, clique no botão de desagregação do elemento visual.

![Filtro de desagregação](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Filtros de desagregação cruzada

Os filtros de desagregação cruzada são automaticamente adicionados ao novo painel quando um filtro de desagregação é passado para outro elemento visual na página de relatório através da funcionalidade de filtro cruzado ou de realce cruzado. Os utilizadores com permissão de edição do relatório não podem eliminar, limpar, ocultar, bloquear, mudar o nome ou ordenar este filtro, uma vez que está associado à funcionalidade de desagregação dos elementos visuais. Também não podem editar este filtro, porque provém de uma desagregação noutro elemento visual. Para remover o filtro de desagregação, clique no botão de desagregação do elemento visual que está associado ao filtro.

## <a name="drillthrough-filters"></a>Filtros de pormenorização

Os filtros de pormenorização são passados de uma página para outra através da funcionalidade de pormenorização. Estes filtros são apresentados no painel de pormenorização. Existem dois tipos de filtros de pormenorização. O primeiro tipo é aquele que invoca a pormenorização. Os editores do relatório podem editar, eliminar, limpar, ocultar ou bloquear este tipo de filtro. O segundo tipo é o filtro de pormenorização que está associado ao público-alvo e é baseado nos filtros ao nível da página de origem. Os editores de relatório podem editar, eliminar ou limpar esse tipo temporário de filtro de pormenorização. Não podem bloquear ou ocultar este filtro para os utilizadores finais.

## <a name="url-filters"></a>Filtros de URL

Os filtros de URL são adicionados ao novo painel ao adicionar um parâmetro de consulta de URL. Os utilizadores com permissão de edição do relatório podem editar, eliminar ou limpar o filtro no novo painel. Não podem ocultar, bloquear, mudar o nome ou ordenar este filtro, uma vez que está associado ao parâmetro de URL. Para remover o filtro, remova o parâmetro de URL. Este é um URL de exemplo com um parâmetro:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![Filtro de URL](media/power-bi-report-filter-types/power-bi-filter-url.png)

Leia mais sobre os [filtros de URL](service-url-filters.md).

## <a name="pass-through-filters"></a>Filtros de pass-through

Os filtros de pass-through são filtros ao nível dos elementos visuais e foram criados através das Perguntas e Respostas. Os autores podem eliminar, ocultar ou ordenar estes filtros no novo painel. No entanto, não podem mudar o nome, editar, limpar ou bloquear estes filtros.

![Filtro de pass-through com Perguntas e Respostas](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Comparar os tipos de filtro

Esta tabela compara o que os autores podem fazer com os diferentes tipos de filtros.

| Tipo de filtro | Edit | Limpar | Delete | Ocultar | Bloquear | Ordenar | Mudar o Nome |
|----|----|----|----|----|----|----|----|
| Filtros manuais | Y | Y | Y | Y | Y | Y | Y |
| Filtros automáticos | Y | Y | N | Y | Y | Y | Y |
| Filtros de Inclusão/Exclusão | N | N | Y | Y | Y | Y | N |
| Filtros de desagregação | Y | Y | N | N | N | N | N |
| Filtros de desagregação cruzada | N | N | N | N | N | N | N |
| Filtros de pormenorização (invoca a pormenorização) | Y | Y | Y | Y | Y | N | N |
| Filtros de pormenorização (temporários) | Y | Y | Y | N | N | N | N |
| Filtros de URL – temporário | Y | Y | Y | N | N | N | N |
| Filtros de pass-through | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>Próximas etapas

[Adicionar filtros a relatórios](power-bi-report-add-filter.md)

[ Fazer uma visita do painel Filtros](consumer/end-user-report-filter.md)

[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

