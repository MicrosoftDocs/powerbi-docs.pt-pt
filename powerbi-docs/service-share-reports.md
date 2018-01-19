---
title: "Partilhar relatórios do Power BI com colegas de trabalho"
description: "Saiba como partilhar relatórios do Power BI e relatórios filtrados com colegas de trabalho na sua organização."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
featuredvideoid: 0tUwn8DHo3s
qualityfocus: complete
qualitydate: 06/22/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/05/2017
ms.author: maggies
ms.openlocfilehash: 2a7b4cc652e600b9a368f6f7eda657c06e131da3
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="share-power-bi-reports-with-your-coworkers"></a>Partilhar relatórios do Power BI com os seus colegas
A *Partilha* é uma boa forma de dar a algumas pessoas acesso aos seus dashboards e relatórios. O Power BI disponibiliza [várias formas de colaborar e distribuir os seus relatórios](service-how-to-collaborate-distribute-dashboards-reports.md), uma das quais é partilhar.

Na partilha, o utilizador e os seus destinatários necessitam de uma [licença do Power BI Pro](service-free-vs-pro.md), ou os conteúdos precisam de estar numa [capacidade Premium](service-premium.md). Sugestões? A equipa do Power BI está sempre interessada nos seus comentários, por isso, vá ao [site da Comunidade do Power BI](https://community.powerbi.com/).

Pode partilhar um relatório com colegas no mesmo domínio de e-mail, a partir de A Minha Área de Trabalho ou a partir de uma área de trabalho de aplicação. Ao partilhar um relatório, as pessoas com quem o partilhar podem ver e interagir com o mesmo, mas não podem editá-lo. As pessoas verão os mesmos dados que vê no relatório, a menos que seja aplicada [RLS (Segurança em nível de linha)](service-admin-rls.md). 

## <a name="share-a-power-bi-report"></a>Partilhar um relatório do Power BI
1. No serviço Power BI, [crie um dashboard](service-dashboard-create.md) com pelo menos um mosaico que ligue ao relatório que pretende partilhar. 
   
    Mesmo que só pretenda partilhar o relatório, terá de criar um dashboard que ligue ao relatório e partilhá-lo. 

1. No canto superior direito do dashboard, selecione **Partilhar**.

     ![Selecione Partilhar](media/service-share-reports/power-bi-share-upper-right.png)
  
2. Dirija-o aos seus destinatários pretendidos. Se não pretende enviar-lhes e-mails sobre o dashboard, desmarque a caixa de verificação **Enviar notificação por e-mail aos destinatários**.

     ![Desmarcar a caixa de verificação Enviar notificação por e-mail](media/service-share-reports/power-bi-share-dont-send-mail.png)

4. Selecione **Partilhar**.

      As pessoas com quem partilha o dashboard têm agora permissão para ver o relatório correspondente. 

1. Abra o relatório no serviço Power BI, copie o URL da página de relatório e envie-o para os seus colegas. 
   
    Quando estes selecionarem a ligação, o Power BI será aberto numa versão só de leitura do relatório.

## <a name="share-a-filtered-version-of-a-report"></a>Partilhar uma versão filtrada de um relatório
E se pretender partilhar uma versão filtrada de um relatório? Por exemplo, um relatório que mostre apenas os dados de um vendedor, cidade ou ano específico. Para tal, deve criar um URL personalizado.

1. Abra o relatório na [Vista de edição](service-reading-view-and-editing-view.md), aplique o filtro e guarde o relatório.
   
   Neste caso, estamos a filtrar o [Exemplo de Análise de Revenda](sample-tutorial-connect-to-the-samples.md) de forma a mostrar apenas valores em que **Territory** (Território) seja igual a **NC**.
   
   ![Painel de filtros do relatório](media/service-share-reports/power-bi-filter-report2.png)
2. Adicione o seguinte ao final do URL da página do relatório:
   
   ?filter=*tablename*/*fieldname* eq *value*
   
    O campo tem de ser uma **cadeia**, e nem *nometabela* nem *nomecampo* podem conter espaços.
   
   No nosso exemplo, o nome da tabela é **Store** (Loja), o nome do campo é **Territory** (Território) e o valor com base no qual pretendemos filtrar é **NC**:
   
    ?filter=Store/Territory eq 'NC'
   
   ![URL de relatório filtrado](media/service-share-reports/power-bi-filter-url3.png)
   
   O browser adiciona carateres especiais para representar barras, espaços e apóstrofos pelo que o resultado será:
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-10a61f70f2f5/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

3. Envie este URL aos seus colegas. 
   
   Quando estes selecionarem a ligação, o Power BI será aberto numa versão só de leitura do relatório filtrado.

## <a name="next-steps"></a>Próximos passos
* Tem comentários? Vá ao [site da Comunidade do Power BI](https://community.powerbi.com/) e envie as suas sugestões.
* [Como devo colaborar e partilhar os meus dashboards e relatórios?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

