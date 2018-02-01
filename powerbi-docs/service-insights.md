---
title: "Gerar automaticamente as informações de dados com o Power BI"
description: "Saiba como obter informações sobre os conjuntos de dados e os mosaicos do dashboard."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: et_MLSL2sA8
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: mihart
ms.openlocfilehash: 01e4f19cc1a3a57179be37cf0f36adf15ac47fdc
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2018
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Gerar automaticamente as informações de dados com o Power BI
Tem um novo conjunto de dados e não sabe exatamente por onde começar?  Precisa criar um dashboard rapidamente?  Deseja procurar informações que pode ter perdido?

Execute as informações rápidas para gerar visualizações interativas e interessantes com base nos seus dados. As informações rápidas podem ser executadas num conjunto de dados inteiro (informações rápidas) ou num mosaico específico do dashboard (informações de confinadas). Pode até executar informações numa informação!

> **NOTA**: as informações não são compatíveis com o DirectQuery. Só funcionam com dados carregados para o Power BI.
> 
> 

A funcionalidade de informações é criada com base num [conjunto de algoritmos de análise avançados](service-insight-types.md) crescente, desenvolvido em conjunto com o Microsoft Research, que continuaremos a utilizar para permitir que mais pessoas descubram informações nos dados de formas novas e intuitivas.

## <a name="run-quick-insights-on-a-dataset"></a>Executar as informações rápidas num conjunto de dados
Veja a Amanda a executar as informações rápidas num conjunto de dados, a abrir uma informação no Modo de detalhe, a afixar uma dessas informações como mosaico no dashboard dela e, em seguida, a obter as informações para um mosaico do dashboard.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Agora, é a sua vez. Explore as informações através do [exemplo de Análise de Qualidade do Fornecedor](sample-supplier-quality.md).

1. No separador **Conjuntos de dados**, selecione as reticências (...) e escolha **Obter informações**.
   
    ![](media/service-insights/power-bi-ellipses.png)
   
    ![](media/service-insights/power-bi-tab.png)
2. O Power BI usa [vários algoritmos](service-insight-types.md) para pesquisar tendências no conjunto de dados.
   
    ![](media/service-insights/pbi_autoinsightssearching.png)
3. Em poucos segundos, as informações estão prontas.  Selecione **Ver informações** para apresentar as visualizações.
   
    ![](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **NOTA**: alguns conjuntos de dados não conseguem gerar informações, porque os dados não são estatisticamente significativos.  Para saber mais, veja [Optimize your data for insights (Otimizar os dados das informações)](service-insights-optimize.md).
   > 
   > 
1. As visualizações são apresentadas numa tela especial de **Informações Rápidas** com até 32 cartões de informações diferentes. Cada cartão contém um gráfico e uma breve descrição.
   
    ![](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interagir com os cartões das informações
  ![](media/service-insights/pbi_hover.png)

1. Passe o cursor sobre um cartão e selecione o ícone do pino para adicionar a visualização a um dashboard.
2. Coloque o cursor sobre um cartão, selecione as reticências (…) e escolha **Ver informações**. Esta ação abre a informação no ecrã inteiro.
   
    ![](media/service-insights/power-bi-insight-focus.png)
3. No Modo de detalhe, pode:
   
   * Filtrar as visualizações.  Para mostrar os filtros, no canto superior direito, selecione a seta para expandir o painel Filtros.
     
        ![](media/service-insights/power-bi-insights-filter-new.png)
   * Afixe o cartão de informações a um dashboard ao selecionar o ícone do pino ![](media/service-insights/power-bi-pin-icon.png) ou **Afixar visual**.
   * Executar as informações no próprio cartão. Esta operação é muitas vezes denominada **informações confinadas**. No canto superior direito, selecione o ícone da lâmpada ![](media/service-insights/power-bi-bulb-icon.png) ou **Obter informações**.
     
       ![](media/service-insights/pbi-autoinsights-tile.png)
     
     A informação é apresentada à esquerda e os cartões novos, com base apenas nos dados dessa informação, são apresentados à direita.
     
       ![](media/service-insights/power-bi-insights-on-insights-new.png)
4. Para voltar à tela original das informações, no canto superior direito, selecione **Sair do Modo de detalhe**.

## <a name="run-insights-on-a-dashboard-tile"></a>Executar as informações num mosaico do dashboard
Em vez de procurar informações em todo um conjunto de dados, filtre a sua pesquisa de forma a procurar os dados utilizados para criar um único mosaico de dashboard. Esta operação também é muitas vezes denominada **informações confinadas**.

1. Abra um dashboard.
2. Coloque o cursor sobre um mosaico, selecione as reticências (...) e escolha **Ver informações**. O mosaico abre-se no [Modo de detalhe](service-focus-mode.md) com os cartões de informações apresentados no lado direito.    
   
    ![](media/service-insights/pbi-insights-tile.png)    
4. Há alguma informação que desperte o seu interesse? Selecione esse cartão de informação para investigar melhor. A informação selecionada é apresentada à esquerda e os cartões de informações novos, com base apenas nos dados dessa informação, são apresentados à direita.    
6. Continue a investigar os dados e, quando encontrar uma informação interessante, afixe-o ao dashboard ao selecionar **Afixar visual** no canto superior direito.

## <a name="next-steps"></a>Próximas etapas
Se é proprietário de um conjunto de dados, [otimize-o para as Informações Rápidas](service-insights-optimize.md)

Saiba mais sobre os [tipos de Informações Rápidas disponíveis](service-insight-types.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
