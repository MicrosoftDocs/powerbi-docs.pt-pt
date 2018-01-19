---
title: Afixar um mosaico a um dashboard a partir das Perguntas e Respostas
description: "documentação sobre como afixar um mosaico a um dashboard do Power BI a partir da caixa de Perguntas e Respostas"
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
ms.date: 12/20/2017
ms.author: mihart
ms.openlocfilehash: 8a876c5a05fcdadff1a874148f5d56465bcc8c62
ms.sourcegitcommit: 6ea8291cbfcb7847a8d7bc4e2b6abce7eddcd0ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/21/2017
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Afixar um mosaico a um dashboard a partir das Perguntas e Respostas
## <a name="how-to-pin-a-tile-from-qa"></a>Como afixar um mosaico a partir das Perguntas e Respostas
P e R é a ferramenta de geração de relatórios ad hoc do Power BI. Precisa de encontrar informações específicas? Faça uma pergunta sobre os dados e receba uma resposta na forma de uma visualização.

As Perguntas e Respostas estão disponíveis nos dashboards e nos relatórios. Neste artigo, vamos abrir as Perguntas e Respostas partir de um dashboard. Os dashboards só estão disponíveis no serviço Power BI, mas não no Power BI Desktop. Para acompanhar, abra o [dashboard do exemplo de Análise de Revenda](sample-retail-analysis.md).
> 
> 

1. Abra um [dashboard](service-dashboards.md) que tenha pelo menos um mosaico afixado de um relatório. Quando fizer uma pergunta, o Power BI procura uma resposta em qualquer conjunto de dados que tenha um mosaico afixado a esse dashboard.  Para obter mais informações, veja [Obter dados](service-get-data.md).
2. Na caixa de perguntas, na parte superior do dashboard, escreva o que pretende saber sobre os dados.  
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. Por exemplo, ao escrever "vendas do ano passado por mês e território"...  
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)
   
   a caixa de pergunta dá-lhe sugestões.
4. Para adicionar o gráfico ao dashboard como um mosaico, selecione o pino ![](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) no lado direito superior da tela.
5. Afixe o mosaico num dashboard existente ou num novo dashboard. 

   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin-to-dashboard.png)

   * Dashboard existente: selecione o nome do dashboard na lista pendente. As suas opções estão limitadas apenas a estes dashboards na área de trabalho atual.
   * Novo dashboard: escreva o nome do novo dashboard e que será adicionado à sua área de trabalho atual.
6. Selecione **Afixar**.
   
   Uma mensagem de êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um mosaico, ao dashboard.  
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Selecione **Ir para o dashboard** para ver o novo mosaico. Aí, pode [mudar o nome, redimensionar, adicionar uma hiperligação, reposicionar o mosaico e muito mais](service-dashboard-edit-tile.md) no seu dashboard. 
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Quando começa a escrever uma pergunta, o P e R começa imediatamente a procurar a melhor resposta de todos os conjuntos de dados associados ao dashboard atual.  O "dashboard atual" é o dashboard, listado na barra de navegação superior. Por exemplo, esta questão está a ser feita no dashboard **Exemplo de Análise de Revenda** que faz parte da área de trabalho da aplicação **mihart**.
  
  ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **De que forma as Perguntas e Respostas sabem que conjuntos de dados devem utilizar**?  O P e R tem acesso a todos os conjuntos de dados que têm visualizações afixadas nesse dashboard.

## <a name="next-steps"></a>Próximos passos
[Mudar o nome, redimensionar, adicionar uma hiperligação, reposicionar o mosaico e muito mais](service-dashboard-edit-tile.md)    
[Apresentar um mosaico do dashboard no Modo de detalhe](service-focus-mode.md)     
[Voltar às Perguntas e Repostas no Power BI](service-q-and-a.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

