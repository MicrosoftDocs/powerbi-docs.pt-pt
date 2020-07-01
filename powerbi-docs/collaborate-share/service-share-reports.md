---
title: Filtrar e partilhar um relatório do Power BI
description: Saiba como filtrar um relatório do Power BI e partilhá-lo com colegas na sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 01/29/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 2988f02b8207eafe5155073af9acc60dcb0a81cf
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85225331"
---
# <a name="filter-and-share-a-power-bi-report"></a>Filtrar e partilhar um relatório do Power BI
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. E se pretender partilhar uma versão filtrada de um relatório? Pode querer que o relatório mostre apenas os dados de um vendedor, cidade ou ano específico. Este artigo explica como filtrar um relatório e como partilhar a versão filtrada desse relatório. Pode também partilhar um relatório filtrado ao [adicionar parâmetros de consulta ao URL do relatório](service-url-filters.md). Em ambos os casos, o relatório estará filtrado quando os destinatários o abrirem. Estes últimos podem limpar as seleções de filtro no relatório.

![Relatório filtrado](media/service-share-reports/power-bi-share-filter-pane-report.png)

O Power BI também disponibiliza [outras formas de colaborar e distribuir os relatórios](service-how-to-collaborate-distribute-dashboards-reports.md). Na partilha, o utilizador e os seus destinatários necessitam de uma [licença do Power BI Pro](../fundamentals/service-features-license-type.md), ou os conteúdos precisam de estar numa [capacidade Premium](../admin/service-premium-what-is.md). 

## <a name="follow-along-with-sample-data"></a>Seguir os dados de exemplo

Este artigo utiliza a aplicação de modelo de exemplo Marketing and Sales (Marketing e Vendas). Deseja experimentá-la? 

1. Instale a [aplicação de modelo de exemplo Marketing and Sales](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).
2. Selecione a aplicação e, em seguida, **Explorar aplicação**.

   ![Explorar os dados de exemplo](media/service-share-reports/power-bi-sample-explore-data.png)

3. Selecione o ícone do lápis para abrir a área de trabalho que instalou com a aplicação.

    ![Lápis de edição da aplicação](media/service-share-reports/power-bi-edit-pencil-app.png)

4. Na lista de conteúdos da área de trabalho, selecione **Relatórios** e, em seguida, selecione o relatório **Ficheiro PBIX de Exemplo de Vendas e Marketing**.

    ![Abrir o relatório de exemplo](media/service-share-reports/power-bi-open-sample-report.png)

    Agora está pronto para continuar.

## <a name="set-a-filter-in-the-report"></a>Definir um filtro no relatório

Abra um relatório na [Vista de edição](../consumer/end-user-reading-view.md) e aplique um filtro.

Neste exemplo, estamos a filtrar a página de Categoria do Ano da aplicação de modelo de exemplo Marketing e Vendas para mostrar apenas os valores em que a **Região** é igual a **Central**. 
 
![Painel de filtros do relatório](media/service-share-reports/power-bi-share-report-filter.png)

Guarde o relatório.

## <a name="share-the-filtered-report"></a>Partilhar o relatório filtrado

1. Selecione **Partilhar**.

   ![Selecione Partilhar](media/service-share-reports/power-bi-share.png)

2. Desmarque **Enviar notificação por e-mail aos destinatários**, para poder enviar antes uma ligação filtrada, selecione **Partilhar o relatório com os filtros e as segmentações atuais** e, em seguida, selecione **Partilhar**.

    ![Partilhar um relatório com filtros](media/service-share-reports/power-bi-share-with-filters.png)

4. Selecione **Partilhar** novamente.

   ![Selecione Partilhar](media/service-share-reports/power-bi-share.png)

5. Selecione o separador **Acesso** e, em seguida, selecione **Gerir vistas de relatórios partilhados**.

    ![Gerir vistas de relatórios partilhados](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. Clique com o botão direito do rato no URL desejado e selecione **Copiar ligação**.

    ![Copiar ligação filtrada](media/service-share-reports/power-bi-copy-filtered-link.png)

7. Ao partilhar esta ligação, os destinatários verão o relatório filtrado. 

## <a name="limitations-and-considerations"></a>Limitações e considerações
Aspetos a ter em conta sobre a partilha de relatórios:

* Quando partilha um conjunto de dados ao gerir permissões, partilhar relatórios ou dashboards, ou publicar uma aplicação, concede acesso a todo o conjunto de dados, a menos que a [segurança ao nível da linha (RLS)](../admin/service-admin-rls.md) limite o acesso. Os autores de relatórios podem utilizar funcionalidades que personalizam as experiências de utilizador ao ver ou interagir com relatórios como, por exemplo, ocultar colunas, limitar as ações em elementos visuais, etc. Estas experiências de utilizador personalizadas não restringem os dados a que os utilizadores podem aceder no conjunto de dados. Utilize a [segurança ao nível da linha (RLS)](../admin/service-admin-rls.md) no conjunto de dados para que as credenciais de cada pessoa determinem a que dados a mesma pode aceder.

## <a name="next-steps"></a>Próximos passos
* [Formas de partilhar o seu trabalho no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).
* Tem comentários? Vá ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.
