---
title: Duas formas de partilhar um relatório do Power BI filtrado
description: Fique a conhecer duas formas de filtrar um relatório do Power BI e partilhá-lo com colegas na sua organização.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 79f09b5018efcdae88d74ae26f099ff095fb161a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871450"
---
# <a name="two-ways-to-share-a-filtered-power-bi-report"></a>Duas formas de partilhar um relatório do Power BI filtrado
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. E se pretender partilhar uma versão filtrada de um relatório? Por exemplo, um relatório que mostre apenas os dados de um vendedor, cidade ou ano específico. Tente filtrar um relatório e partilhá-lo ou criar um URL personalizado. O relatório será filtrado quando os destinatários o abrirem. É possível remover o filtro ao modificar o URL. 

![Relatório filtrado](media/service-share-reports/power-bi-share-filter-pane-report.png)

O Power BI também disponibiliza [outras formas de colaborar e distribuir os relatórios](service-how-to-collaborate-distribute-dashboards-reports.md). Na partilha, o utilizador e os seus destinatários necessitam de uma [licença do Power BI Pro](service-features-license-type.md), ou os conteúdos precisam de estar numa [capacidade Premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Duas formas de filtrar um relatório

Para ambas as técnicas de filtragem, estamos a utilizar a aplicação de modelo de exemplo Marketing e Vendas. Deseja experimentá-la? Também pode instalar a [aplicação de modelo de exemplo Marketing e Vendas](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).

### <a name="set-a-filter"></a>Definir um filtro

Abra um relatório na [Vista de edição](consumer/end-user-reading-view.md) e aplique um filtro.

Neste exemplo, estamos a filtrar a página de Categoria do Ano da aplicação de modelo de exemplo Marketing e Vendas para mostrar apenas os valores em que a **Região** é igual a **Central**. 
 
![Painel de filtros do relatório](media/service-share-reports/power-bi-share-report-filter.png)

Guarde o relatório.

### <a name="create-a-filter-in-the-url"></a>Criar um filtro no URL

Quando adiciona o filtro ao final do URL da página de relatório, o comportamento é um pouco diferente. O aspeto da página filtrada não é alterado. No entanto, o Power BI adiciona o filtro a todo o relatório e remove os outros valores do painel do filtro.  

Adicione o seguinte ao final do URL da página do relatório:
   
    ?filter=*tablename*/*fieldname* eq *value*
   
O campo deve ser do tipo número, data/hora ou cadeia de caracteres. Os valores *tablename* ou *fieldname* não podem ter espaços.
   
No nosso exemplo, o nome da tabela é **Área geográfica**, o nome do campo é **Região** e o valor com base no qual pretendemos filtrar é **Central**:
   
    ?filter=Geo/Region eq 'Central'

O browser adiciona carateres especiais para representar barras, espaços e apóstrofos pelo que o resultado será parecido com este:
   
    app.powerbi.com/groups/xxxx/reports/xxxx/ReportSection4d00c3887644123e310e?filter=Geo~2FRegion%20eq%20'Central'

![Relatório com filtro de URL](media/service-share-reports/power-bi-share-report-filter-url.png)

Guarde o relatório.

Veja o artigo [Filtrar um relatório com os parâmetros de cadeia de consulta no URL](service-url-filters.md) para obter muitos mais detalhes.

## <a name="share-the-filtered-report"></a>Partilhar o relatório filtrado

1. Quando [partilha o relatório](service-share-dashboards.md), desmarque a caixa de verificação **Enviar notificação por e-mail aos destinatários**.

    ![Caixa de diálogo Partilhar relatório](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envie a ligação com o filtro criado anteriormente.

## <a name="next-steps"></a>Próximos passos
* [Formas de partilhar o seu trabalho no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).
* Tem comentários? Vá ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.

