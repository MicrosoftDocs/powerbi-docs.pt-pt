---
title: Filtrar um relatório e partilhá-lo com colegas de trabalho - Power BI
description: Saiba como filtrar um relatório do Power BI e partilhá-lo com colegas na sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770698"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>Filtrar um relatório do Power BI e partilhá-lo com colegas de trabalho
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. E se pretender partilhar uma versão filtrada de um relatório? Por exemplo, um relatório que mostre apenas os dados de um vendedor, cidade ou ano específico. Tente filtrar um relatório e partilhá-lo ou criar um URL personalizado. O relatório será filtrado quando os destinatários o abrirem. É possível remover o filtro ao modificar o URL. 

O Power BI também disponibiliza [várias outras formas de colaborar e distribuir os seus relatórios](service-how-to-collaborate-distribute-dashboards-reports.md). Na partilha, o utilizador e os seus destinatários necessitam de uma [licença do Power BI Pro](service-features-license-type.md), ou os conteúdos precisam de estar numa [capacidade Premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Duas formas de filtrar um relatório

### <a name="set-a-filter"></a>Defina um filtro

Abra o relatório na [Vista de edição](consumer/end-user-reading-view.md), aplique o filtro e guarde o relatório.
   
Neste caso, estamos a filtrar o [Exemplo de Análise de Revenda](sample-tutorial-connect-to-the-samples.md) de forma a mostrar apenas valores em que **Territory** (Território) seja igual a **NC**.
   
![Painel de filtros do relatório](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>Criar um filtro no URL

Adicione o seguinte ao final do URL da página do relatório:
   
?filter=*tablename*/*fieldname* eq *value*
   
O campo tem de ser do tipo número, datetime ou uma cadeia. Os valores *tablename* ou *fieldname* não podem ter espaços.
   
No nosso exemplo, o nome da tabela é **Store** (Loja), o nome do campo é **Territory** (Território) e o valor com base no qual pretendemos filtrar é **NC**:
   
?filter=Store/Territory eq 'NC'
   
![URL de relatório filtrado](media/service-share-reports/power-bi-filter-url3.png)
   
O browser adiciona carateres especiais para representar barras, espaços e apóstrofos pelo que o resultado será:
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

Consulte o artigo [filtrar um relatório com parâmetros de cadeia de caracteres de consulta no URL](service-url-filters.md) para muito mais detalhes.

## <a name="share-the-filtered-report"></a>Partilhar o relatório filtrado

1. Quando [partilhar o relatório](service-share-dashboards.md), desmarque a **enviar a notificação por e-mail aos destinatários** caixa de verificação.

    ![Caixa de diálogo Partilhar relatório](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envie a ligação com o filtro criado anteriormente.

## <a name="next-steps"></a>Próximos passos
* Tem comentários? Vá ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.
* [Como devo colaborar e partilhar os meus dashboards e relatórios?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

