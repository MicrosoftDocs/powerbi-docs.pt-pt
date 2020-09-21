---
title: Executar e ver informações nos mosaicos do dashboard
description: Como utilizador final do Power BI, saiba como obter informações sobre os mosaicos do dashboard.
author: mihart
ms.reviewer: mihart
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/09/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 21bccbd11f8d2060b648e22c8ed8aa9471c820f0
ms.sourcegitcommit: 002c140d0eae3137a137e9a855486af6c55ad957
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89642545"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Ver informações de dados nos mosaicos do dashboard com o Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Cada [mosaico](end-user-tiles.md) de elemento visual no dashboard é uma porta para a exploração de dados. Ao selecionar um mosaico, é aberto um relatório ou uma página de [Perguntas e Respostas](end-user-q-and-a.md) onde pode filtrar e ordenar, bem como aprofundar o conjunto de dados associado ao relatório. E quando executa as informações, o Power BI faz a exploração de dados por si.

![modo de menu de reticências a mostrar Ver informações como uma opção](./media/end-user-insights/power-bi-insight.png)

Execute as informações para gerar elementos visuais interessantes com base nos seus dados. As informações podem ser executadas num mosaico específico do dashboard e até pode executá-las com base numa informação!

A funcionalidade de informações é criada com base num [conjunto de algoritmos de análise avançados](end-user-insight-types.md) crescente, desenvolvido em conjunto com o Microsoft Research, que continuaremos a utilizar para permitir que mais pessoas descubram informações nos dados de formas novas e intuitivas.

## <a name="run-insights-on-a-dashboard-tile"></a>Executar as informações num mosaico do dashboard
Quando executa as informações num mosaico do dashboard, o Power BI procura apenas os dados utilizados para criar esse único mosaico do dashboard. 

1. [Abra um dashboard](end-user-dashboards.md).
2. Coloque o cursor sobre um mosaico, selecione **Mais opções** (...) e selecione **Ver informações**. 

    ![Captura de ecrã a mostrar que a seleção das reticências mostra o menu pendente](./media/end-user-insights/power-bi-hover.png)


3. O mosaico abre-se no [Modo de detalhe](end-user-focus.md) com os cartões de informações apresentados no lado direito.    
   
    ![Modo de detalhe](./media/end-user-insights/power-bi-insights-tiles.png)    
4. Há alguma informação que desperte o seu interesse? Selecione esse cartão de informação para investigar melhor. A informação selecionada é apresentada à esquerda e os cartões de informações novos, com base apenas nos dados dessa informação, são apresentados à direita.    

 ## <a name="interact-with-the-insight-cards"></a>Interagir com os cartões das informações
Depois de abrir uma informação, continue a explorar.

   * Filtre o elemento visual na tela.  Para mostrar os filtros, no canto superior direito, selecione a seta para expandir o painel Filtros.

      ![informações com o menu Filtros expandido](./media/end-user-insights/power-bi-filter.png)
   
   * Executar as informações no próprio cartão de informação. Esta operação é muitas vezes denominada **informações relacionadas**. Selecione um cartão de informações para torná-lo ativo. Irá mover-se para o lado esquerdo da tela do relatório e serão apresentados novos cartões à direita com base apenas nos dados nessas informações.
   
      ![Informações relacionadas e menu Filtros expandido](./media/end-user-insights/power-bi-insights-card.png)
   
     
Para voltar ao seu relatório, selecione **Sair do Modo de detalhe** no canto superior esquerdo.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- **Ver informações** não funciona com todos os tipos de mosaicos do dashboard. Por exemplo, não está disponível para elementos visuais personalizados do Power BI.<!--[Power BI visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Próximos passos

Executar informações em elementos visuais de relatório [com a funcionalidade Analisar](end-user-analyze-visuals.md)    
Saiba mais sobre os [tipos de Informações disponíveis](end-user-insight-types.md)

