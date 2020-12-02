---
title: Alterar as definições de relatórios do Power BI
description: Alterar as definições de relatórios no serviço Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: dbb173c65ecfc5d1ca464387ed43ae615cdcbca1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396182"
---
# <a name="change-settings-for-power-bi-reports"></a>Alterar as definições de relatórios do Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Com as definições do relatório no Power BI Desktop e no serviço Power BI, pode controlar como os leitores do relatório interagem com o seu relatório. Por exemplo, pode permitir que guardem filtros para o relatório, personalizem os elementos visuais no relatório ou apresentem as páginas do relatório como separadores na parte inferior do relatório e não de lado.

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Captura de ecrã a mostrar o painel Definições de relatório no serviço Power BI.":::

Pode ser útil ler estes artigos primeiro:

- [Criar um relatório no serviço Power BI através da importação de um conjunto de dados](service-report-create-new.md), para compreender a experiência de criação do relatório.
- [Relatórios no Power BI](../consumer/end-user-reports.md), para compreender a experiência dos leitores do relatório.

 Vamos começar!

## <a name="prerequisites"></a>Pré-requisitos

- Para criar relatórios com o Power BI Desktop, veja [Vista de relatórios do Desktop](desktop-report-view.md).
- [Inscreva-se no serviço Power BI](../fundamentals/service-self-service-signup-for-power-bi.md). 
- Tem de ter permissões de edição para o relatório no serviço Power BI. Veja as [Funções nas novas áreas de trabalho](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) para obter detalhes sobre as permissões.
- Se ainda não tiver um relatório no serviço Power BI, pode [instalar um pacote de conteúdos de exemplo](sample-datasets.md#install-built-in-content-packs) que contém um dashboard, relatório e conjunto de dados.

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>Abrir o painel Definições no Power BI Desktop

1. Selecione **Ficheiro** > **Opções e definições** > **Opções**.
1. Em **Ficheiro atual**, selecione **Definições de relatório**.

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Captura de ecrã a mostrar o painel Definições de relatório no Power BI Desktop":::

    O resto do artigo aborda algumas das definições de relatório específicas.

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>Abrir o painel Definições no serviço Power BI

1. Na vista de leitura de relatórios, selecione **Ficheiro** > **Definições**.

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="Captura de ecrã a mostrar o menu Ficheiro e a opção Definições.":::

1. No painel **Definições**, verá vários botões que pode definir, apenas para este relatório. O resto do artigo aborda alguns deles.

## <a name="set-featured-content"></a>Definir conteúdo em destaque

Pode destacar dashboards, relatórios e aplicações de forma a serem apresentados na secção Em destaque da Base do Power BI dos seus colegas. Saiba mais sobre [como destacar conteúdo](../collaborate-share/service-featured-content.md).

## <a name="set-the-pages-pane"></a>Definir o painel Páginas

Atualmente, só pode alterar a definição do painel Páginas no serviço Power BI. Quando ativar o **painel Páginas**, os leitores do relatório veem os separadores da página do relatório na parte inferior do relatório na vista de leitura e não ao lado. Na vista de edição, os separadores da página do relatório já estão na parte inferior do relatório.

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="Captura de ecrã da definição do painel Páginas.":::

## <a name="control-filters"></a>Controlar filtros

O painel **Definições** do relatório tem três definições para controlar as interações do leitor com os filtros no relatório. As ligações seguintes redirecionam para o artigo [Conceber filtros nos relatórios do Power BI](power-bi-report-filter.md) para obter detalhes sobre cada definição.

- **Os filtros persistentes** permitem que os leitores [guardem filtros no relatório](power-bi-report-filter.md#allow-saving-filters).
- **A experiência de filtragem** tem mais duas definições:
    
    Permitir que os leitores de relatórios [alterem os tipos de filtro](power-bi-report-filter.md#restrict-changes-to-filter-type).

    Ativar a [pesquisa no painel de filtro](power-bi-report-filter.md#filters-pane-search).

## <a name="export-data"></a>Exportar dados

Por predefinição, [os leitores de relatórios podem exportar dados resumidos ou subjacentes ](../consumer/end-user-export.md) de elementos visuais no seu relatório. Com a opção **Exportar dados**, pode permitir que exportem apenas dados resumidos ou que não exportem dados do seu relatório.

## <a name="personalize-visuals"></a>Personalizar elementos visuais

Permita que os leitores alterem e personalizem os elementos visuais no seu relatório. Saiba mais sobre como [permitir que os leitores do relatório personalizem elementos visuais](power-bi-personalize-visuals.md).

## <a name="next-steps"></a>Passos seguintes

* [Destacar conteúdo na Base de outras pessoas](../collaborate-share/service-featured-content.md)
* [Permitir que os leitores do relatório personalizem elementos visuais num relatório](power-bi-personalize-visuals.md)
* Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
