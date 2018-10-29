---
title: Gerar automaticamente as informações de dados com o Power BI
description: Saiba como obter informações sobre os conjuntos de dados e os mosaicos do dashboard.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/10/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: f68e962eacf04005d83ec0def10cf8e0e24f6e10
ms.sourcegitcommit: dc8b8a2cf2dcc96ccb46159802ebd9342a7fa840
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49112044"
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Gerar automaticamente as informações de dados com o Power BI
Cada mosaico de visualização no dashboard é uma porta para a exploração de dados. Quando seleciona um mosaico, é aberto um relatório onde pode filtrar e ordenar e aprofundar o conjunto de dados associado ao relatório. E quando executa as informações, o Power BI faz a exploração de dados por si.

Execute as informações rápidas para gerar visualizações interativas e interessantes com base nos seus dados. As informações rápidas podem ser executadas num mosaico específico do dashboard e até pode executar as informações numa informação!

A funcionalidade de informações é criada com base num [conjunto de algoritmos de análise avançados](end-user-insight-types.md) crescente, desenvolvido em conjunto com o Microsoft Research, que continuaremos a utilizar para permitir que mais pessoas descubram informações nos dados de formas novas e intuitivas.

## <a name="run-insights-on-a-dashboard-tile"></a>Executar as informações num mosaico do dashboard
Quando executa as informações num mosaico do dashboard, o Power BI procura apenas os dados utilizados para criar esse único mosaico do dashboard. 

1. [Abra um dashboard](end-user-dashboards.md).
2. Coloque o cursor sobre um mosaico, selecione as reticências (...) e escolha **Ver informações**. 

    ![modo de menu de reticências](./media/end-user-insights/power-bi-hover.png)


3. O mosaico abre-se no [Modo de detalhe](end-user-focus.md) com os cartões de informações apresentados no lado direito.    
   
    ![Modo de detalhe](./media/end-user-insights/pbi-insights-tile.png)    
4. Há alguma informação que desperte o seu interesse? Selecione esse cartão de informação para investigar melhor. A informação selecionada é apresentada à esquerda e os cartões de informações novos, com base apenas nos dados dessa informação, são apresentados à direita.    

 ## <a name="interact-with-the-insight-cards"></a>Interagir com os cartões das informações
   * Filtrar as visualizações.  Para mostrar os filtros, no canto superior direito, selecione a seta para expandir o painel Filtros.

     ![informações e menu Filtros expandido](./media/end-user-insights/power-bi-insights-on-insights.png)
   
   * Executar as informações no próprio cartão de informação. Esta operação é muitas vezes denominada **informações relacionadas**. No canto superior direito, selecione o ícone da lâmpada ![ícone Obter Informações](./media/end-user-insights/power-bi-bulb-icon.png) ou **Obter informações**.
     
     ![barra de menus a mostrar o ícone Obter Informações](./media/end-user-insights/power-bi-autoinsights-tile.png)
     
     A informação é apresentada à esquerda e os cartões novos, com base apenas nos dados dessa informação, são apresentados à direita.
     
     ![informações em informações](./media/end-user-insights/power-bi-insights-on-insights-new.png)

Para voltar à tela original das informações, no canto superior direito, selecione **Sair do Modo de detalhe**.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- **Visualizar informações**: não trabalha com o DirectQuery. Só funciona com dados carregados para o Power BI.
- **Ver informações** não funciona com todos os tipos de mosaicos do dashboard. Por exemplo, não está disponível para os elementos visuais personalizados.<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Próximos passos
Saiba mais sobre os [tipos de Informações Rápidas disponíveis](end-user-insight-types.md)

