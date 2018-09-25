---
title: Filtrar e partilhar relatórios do Power BI com colegas
description: Saiba como partilhar um relatório do Power BI filtrado com colegas na sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/18/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8f025c11a5269befdb7819684e10e8511ae6bc98
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/21/2018
ms.locfileid: "46545649"
---
# <a name="share-a-filtered-power-bi-report-with-your-coworkers"></a>Partilhar um relatório do Power BI filtrado com os seus colegas
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. O Power BI também disponibiliza [várias outras formas de colaborar e distribuir os seus relatórios](service-how-to-collaborate-distribute-dashboards-reports.md).

Na partilha, o utilizador e os seus destinatários necessitam de uma [licença do Power BI Pro](service-free-vs-pro.md), ou os conteúdos precisam de estar numa [capacidade Premium](service-premium.md). Sugestões? A equipa do Power BI está sempre interessada nos seus comentários, por isso, vá ao [site da Comunidade do Power BI](https://community.powerbi.com/).

Pode partilhar um relatório com os colegas no mesmo domínio de e-mail que utiliza, a partir da maioria dos locais no serviço Power BI: Favoritos, Recente, Partilhado comigo (se o proprietário o permitir), A minha área de trabalho ou outras áreas de trabalho. Ao partilhar um relatório, as pessoas com quem o partilhar podem ver e interagir com o mesmo, mas não podem editá-lo. As pessoas verão os mesmos dados que vê no relatório, a menos que seja aplicada [RLS (Segurança em nível de linha)](service-admin-rls.md). 

## <a name="filter-and-share-a-report"></a>Filtrar e partilhar um relatório
E se pretender partilhar uma versão filtrada de um relatório? Por exemplo, um relatório que mostre apenas os dados de um vendedor, cidade ou ano específico. Para tal, deve criar um URL personalizado.

1. Abra o relatório na [Vista de edição](consumer/end-user-reading-view.md), aplique o filtro e guarde o relatório.
   
   Neste caso, estamos a filtrar o [Exemplo de Análise de Revenda](sample-tutorial-connect-to-the-samples.md) de forma a mostrar apenas valores em que **Territory** (Território) seja igual a **NC**.
   
   ![Painel de filtros do relatório](media/service-share-reports/power-bi-filter-report2.png)
2. Adicione o seguinte ao final do URL da página do relatório:
   
   ?filter=*tablename*/*fieldname* eq *value*
   
    O campo tem de ser uma **cadeia**, e nem *nometabela* nem *nomecampo* podem conter espaços.
   
   No nosso exemplo, o nome da tabela é **Store** (Loja), o nome do campo é **Territory** (Território) e o valor com base no qual pretendemos filtrar é **NC**:
   
    ?filter=Store/Territory eq 'NC'
   
   ![URL de relatório filtrado](media/service-share-reports/power-bi-filter-url3.png)
   
   O browser adiciona carateres especiais para representar barras, espaços e apóstrofos pelo que o resultado será:
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

3. [Partilhe o relatório](service-share-dashboards.md), mas desmarque a caixa de verificação **Enviar notificação por e-mail aos destinatários**. 

    ![Caixa de diálogo Partilhar relatório](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envie a ligação com o filtro criado anteriormente.

## <a name="next-steps"></a>Próximos passos
* Tem comentários? Vá ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.
* [Como devo colaborar e partilhar os meus dashboards e relatórios?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

