---
title: Como afixar um mosaico num dashboard a partir das Perguntas e Respostas
description: documentação sobre como afixar um mosaico a um dashboard do Power BI a partir da caixa de Perguntas e Respostas
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/05/2021
LocalizationGroup: Dashboards
ms.openlocfilehash: 5ae148feaa294c8779a7140ef450c832bd3376d8
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2021
ms.locfileid: "97927186"
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Afixar um mosaico a um dashboard a partir das Perguntas e Respostas

A ferramenta Perguntas e Respostas do Power BI permite-lhe explorar os seus dados através de linguagem natural. Precisa de encontrar informações específicas? Faça uma pergunta sobre os dados e receba uma resposta na forma de uma visualização.

Neste artigo de procedimento, abrimos um [dashboard](../consumer/end-user-dashboards.md) no serviço Power BI (app.powerbi.com), fazemos uma pergunta com linguagem natural para criar uma visualização e afixamos essa visualização num dashboard. Os dashboards não estão disponíveis no Power BI Desktop. Para obter informações sobre como utilizar as Perguntas e Respostas com outras ferramentas e conteúdo do Power BI, veja a [Descrição geral das Perguntas e Respostas do Power BI](../consumer/end-user-q-and-a.md). 

Para acompanhar, abra o [dashboard do exemplo de Análise de Revenda](sample-retail-analysis.md).

## <a name="how-to-pin-a-tile-from-qa"></a>Como afixar um mosaico a partir das Perguntas e Respostas

1. Abra um dashboard que tenha pelo menos um mosaico afixado de um relatório. Quando fizer uma pergunta, o Power BI procura uma resposta em qualquer conjunto de dados que tenha um mosaico afixado a esse dashboard.
2. Na caixa de perguntas, na parte superior do dashboard, escreva o que pretende saber sobre os dados.  
   ![caixa de perguntas das Perguntas e Respostas](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. Por exemplo, ao escrever "vendas do ano passado por mês e território"...  
   ![escrever uma pergunta](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)

   a caixa de pergunta dá-lhe sugestões.
4. Para adicionar o gráfico ao seu dashboard como mosaico, selecione o ícone de alfinete ![Ícone de afixar](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) no canto superior direito da tela. Se o dashboard foi partilhado consigo, não poderá afixar visualizações.

5. Afixe o mosaico num dashboard existente ou num novo dashboard.

   ![Caixa de diálogo Afixar no dashboard](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin-to-dashboard.png)

   * Dashboard existente: selecione o nome do dashboard a partir da lista pendente. As suas opções estão limitadas apenas a estes dashboards na área de trabalho atual.
   * Novo dashboard: escreva o nome do novo dashboard e este será adicionado à sua área de trabalho atual.

6. Selecione **Afixar**.

   Uma mensagem de êxito (perto do canto superior direito) informa que a visualização foi adicionada, como um mosaico, ao dashboard.  

   ![Afixado ao dashboard](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Selecione **Ir para o dashboard** para ver o novo mosaico. Aqui, pode [mudar o nome, redimensionar, adicionar uma hiperligação, reposicionar o mosaico e muito mais](service-dashboard-edit-tile.md) no seu dashboard.

   ![dashboard com mosaicos](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
* Quando começa a escrever uma pergunta, o P e R começa imediatamente a procurar a melhor resposta de todos os conjuntos de dados associados ao dashboard atual.  O “dashboard atual” é o dashboard listado no painel de navegação superior. Por exemplo, esta pergunta está a ser feita no dashboard **Exemplo de Análise de Revenda**, que faz parte da área de trabalho **mihart**.

  ![trilhos](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **De que forma as Perguntas e Respostas sabem que conjuntos de dados devem utilizar**?  As Perguntas e Respostas têm acesso a todos os conjuntos de dados que têm, pelo menos, uma visualização afixada nesse dashboard.

* **Não vê a caixa de pergunta**? Fale com o seu administrador do Power BI. O administrador tem a capacidade de desativar as Perguntas e Respostas.


## <a name="next-steps"></a>Próximos passos
[Mudar o nome, redimensionar, adicionar uma hiperligação, reposicionar o mosaico e muito mais](service-dashboard-edit-tile.md)    
[Apresentar um mosaico do dashboard no Modo de detalhe](../consumer/end-user-focus.md)     
[Descrição geral das Perguntas e Respostas no Power BI](../consumer/end-user-q-and-a.md)  
Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
