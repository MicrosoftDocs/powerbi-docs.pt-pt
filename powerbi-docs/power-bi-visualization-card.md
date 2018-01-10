---
title: "Visualizações de cartão (também conhecido como mosaicos de número grande)"
description: "Criar uma Visualização de cartão no Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/24/2017
ms.author: mihart
ms.openlocfilehash: 1136aae9af4481a1d55ca3d11ed300242aab187b
ms.sourcegitcommit: 74fbbca81a056dda19b3647ae058005aba5296f5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/03/2018
---
# <a name="card-visualizations"></a>Visualizações de cartão
Por vezes, um único número é a coisa mais importante que pretende controlar no seu dashboard ou relatório do Power BI, como as vendas totais, a quota de mercado ano após ano ou o total de oportunidades. Este tipo de visualização é denominado um *Cartão*. Tal como acontece com quase todas as visualizações nativas do Power BI, os Cartões podem ser criados com o editor de relatórios ou as Perguntas e Respostas.

![visualização de cartão](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Criar um cartão com o editor de relatórios
Estas instruções utilizam o Exemplo de Análise de Retalho. Para acompanhar, [transfira o exemplo](sample-datasets.md) do serviço do Power BI (app.powerbi.com) ou o Power BI Desktop.   

1. Comece numa [página do relatório em branco ](power-bi-report-add-page.md) e selecione o campo **Armazenar** \> **Contagem de arquivos abertos**. Se estiver a utilizar o serviço do Power BI, terá de abrir o relatório na [Vista de Edição](service-interact-with-a-report-in-editing-view.md).

    O Power BI cria um gráfico de colunas com um número.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. No painel de Visualizações, selecione o ícone de Cartão.

   ![](media/power-bi-visualization-card/pbi_changechartcard.png)
6. Passe o cursor sobre um cartão e selecione o ícone de afixar ![](media/power-bi-visualization-card/pbi_pintile.png) para adicionar a visualização a um dashboard.

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. Afixe o mosaico num dashboard existente ou num novo dashboard.

   * Dashboard existente: selecione o nome do dashboard no menu suspenso.
   * Novo dashboard: escreva o nome do novo dashboard.
8. Selecione **Afixar**.

   Uma mensagem de Êxito (junto ao canto superior direito) informa que a visualização foi adicionada, como um mosaico, ao dashboard.

   ![](media/power-bi-visualization-card/power-bi-pin-success-message.png)
9. Selecione **Ir para o dashboard**. Aqui, pode [editar e mover](service-dashboard-edit-tile.md) a visualização afixada.


## <a name="create-a-card-from-the-qa-question-box"></a>Criar um cartão a partir da caixa de Perguntas e Respostas
A caixa de Perguntas e Respostas é a forma mais fácil de criar um Cartão. A caixa de Perguntas e Respostas está disponível no serviço do Power BI (app.powerbi.com) de um dashboard ou relatório. Os passos abaixo descrevem a criação de um Cartão a partir de um dashboard do serviço do Power BI. Se gostaria de criar um cartão com as Perguntas e Respostas no Power BI Desktop, [siga estas instruções](https://powerbi.microsoft.com/en-us/blog/power-bi-desktop-december-feature-summary/#QandA) para a pré-visualização de Perguntas e Respostas para relatórios do Desktop.

1. Crie um [dashboard](service-dashboards.md) e [obtenha dados](service-get-data.md). Este exemplo utiliza a [Amostra de Análise de Oportunidade](sample-opportunity-analysis.md).

1. Na parte superior do dashboard, comece a escrever o que deseja saber sobre os dados na caixa de perguntas. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

>**SUGESTÃO**: a partir de um relatório de serviço do Power BI, em [Editar vista](service-reading-view-and-editing-view.md), selecione **Fazer uma pergunta** na barra de menu superior. A partir de um relatório do Power BI Desktop, encontre algum espaço livre num relatório e clique duas vezes para abrir uma caixa de perguntas.

3. Por exemplo, escreva "número de oportunidades" na caixa de perguntas.

   ![](media/power-bi-visualization-card/power-bi-q-and-a.png)

   A caixa de perguntas ajuda-o com sugestões e reformulações e, finalmente, apresenta o número total.  
4. Selecione o ícone de afixar ![](media/power-bi-visualization-card/pbi_pintile.png) no canto superior direito para adicionar o cartão a um dashboard.

   ![](media/power-bi-visualization-card/power-bi-pin.png)
5. Afixe o cartão, como um mosaico, num dashboard existente ou num novo dashboard.

   * Dashboard existente: selecione o nome do dashboard no menu suspenso. As suas escolhas estão limitadas apenas a esses dashboards na área de trabalho atual.
   * Novo dashboard: escreva o nome do novo dashboard e que será adicionado à sua área de trabalho atual.
6. Selecione **Afixar**.

   Uma mensagem de Êxito (junto ao canto superior direito) informa que a visualização foi adicionada, como um mosaico, ao dashboard.  

   ![](media/power-bi-visualization-card/power-bi-success.png)
7. Selecione **Ir para o dashboard** para ver o novo mosaico. Aqui, pode [mudar o nome, redimensionar, adicionar uma hiperligação, reposicionar o mosaico e muito mais](service-dashboard-edit-tile.md) no seu dashboard.

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- Se não vir uma caixa de perguntas, contacte o administrador do sistema ou o inquilino.    
- Se estiver a utilizar o Desktop e a clicar duas vezes em espaço vazio num relatório que não abre as Perguntas e Respostas, terá de o ativar.  Selecione **Ficheiro > Opções e Definições > Opções > Funcionalidades de pré-visualização > Perguntas e Respostas** e reinicie o Desktop.


## <a name="next-steps"></a>Próximas etapas
[Mosaicos do dashboard no Power BI](service-dashboard-tiles.md)

[Dashboards no Power BI](service-dashboards.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)