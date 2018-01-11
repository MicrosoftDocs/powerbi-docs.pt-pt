---
title: "Obter Informações rápidas no Power BI"
description: "Documentação para executar e trabalhar com as Informações Rápidas no serviço Power BI."
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
ms.date: 09/01/2017
ms.author: mihart
ms.openlocfilehash: 8b069f29737992817d20396007864cc8c005ca99
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="quick-insights-with-power-bi"></a>Quick Insights com o Power BI
Tem um novo conjunto de dados e não sabe exatamente por onde começar?  Precisa criar um dashboard rápido?  Deseja procurar rapidamente informações que pode ter perdido?

Execute o Quick Insights para gerar visualizações interativas e interessantes com base nos seus dados. As Informações Rápidas podem ser executadas num conjunto de dados inteiro (Informações Rápidas) ou num mosaico de dashboard específico (Informações de Âmbito). Pode até executar Informações Rápidas numa Informação!

> **NOTA**: as Informações Rápidas não são compatíveis com o DirectQuery. Só funcionam com dados carregados para o Power BI.
> 
> 

A funcionalidade Informações Rápidas é criada com base num [conjunto crescente de algoritmos de análise avançados](service-insight-types.md), desenvolvidos em conjunto com o Microsoft Research, que continuaremos a utilizar para permitir que mais pessoas descubram informações nos seus dados de formas novas e intuitivas.

## <a name="run-quick-insights-on-a-dataset"></a>Executar o Quick Insights num conjunto de dados
Veja a Amanda a executar as Informações Rápidas num conjunto de dados, abrir uma Informação no Modo de detalhe, afixar uma dessas Informações Rápidas como mosaico no dashboard dela, e, em seguida, obter as Informações Rápidas para um visual.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Agora, é a sua vez. Explore as Informações Rápidas através do [exemplo de Análise de Qualidade do Fornecedor](sample-supplier-quality.md).

1. No separador **Conjuntos de dados**, selecione as reticências (...) e selecione **Obter Informações**.
   
    ![](media/service-insights/power-bi-ellipses.png)
   
    ![](media/service-insights/power-bi-tab.png)
2. O Power BI usa [vários algoritmos](service-insight-types.md) para pesquisar tendências no conjunto de dados.
   
    ![](media/service-insights/pbi_autoinsightssearching.png)
3. Em poucos segundos, as informações estão prontas.  Selecione **Ver Insights** para apresentar as visualizações.
   
    ![](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **NOTA**: alguns conjuntos de dados não conseguem gerar Informações Rápidas porque os dados não são estatisticamente significativos.  Para saber mais, consulte [Otimizar os seus dados para as Informações Rápidas](service-insights-optimize.md).
   > 
   > 
4. As visualizações são apresentadas numa tela especial de **Informações Rápidas** com até 32 cartões de informações diferentes. Cada cartão contém um gráfico e uma breve descrição.
   
    ![](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-quick-insight-cards"></a>Interagir com os cartões das Informações Rápidas
  ![](media/service-insights/pbi_hover.png)

1. Passe o cursor sobre um cartão e selecione o ícone do pino para adicionar a visualização a um dashboard.
2. Passe o cursor sobre um cartão e selecione o ícone do Modo de detalhe para apresentar o cartão em ecrã inteiro.
   
    ![](media/service-insights/power-bi-insight-focus.png)
3. No Modo de detalhe, pode:
   
   * [filtrar](service-interact-with-a-report-in-reading-view.md) as visualizações.  Para mostrar os filtros, no canto superior direito, selecione a seta para expandir o painel Filtros.
     
        ![](media/service-insights/power-bi-insights-filter-new.png)
   * Afixe o cartão de informações a um dashboard ao selecionar o ícone do pino ![](media/service-insights/power-bi-pin-icon.png) ou **Afixar visual**.
   * Execute as Informações Rápidas no próprio cartão. Esta operação é denominada **Informações Rápidas Confinadas**. No canto superior direito, selecione o ícone da lâmpada ![](media/service-insights/power-bi-bulb-icon.png) ou **Obter Informações**.
     
       ![](media/service-insights/pbi-autoinsights-tile.png)
     
     A Informação Rápida é apresentada à esquerda e os cartões novos, com base apenas nos dados nessa Informação Rápida, são apresentados à direita.
     
       ![](media/service-insights/power-bi-insights-on-insights-new.png)
4. Para regressar à tela original das Informações Rápidas, no canto superior direito, selecione **Sair do Modo de detalhe**.

## <a name="run-quick-insights-on-a-dashboard-tile"></a>Executar as Informações Rápidas num mosaico de dashboard
Em vez de procurar informações em todo um conjunto de dados, filtre a sua pesquisa de forma a procurar os dados utilizados para criar um único mosaico de dashboard. Esta operação é denominada **Informações Rápidas Confinadas**.

1. Abra um dashboard.
2. Selecione um mosaico e [abra o mosaico em modo de detalhe](service-focus-mode.md).
3. No canto superior direito, selecione **Obter Informações**.
   
    ![](media/service-insights/pbi-autoinsights-tile.png)
4. O Power BI apresenta os cartões de informações, no lado direito do mosaico.
   
    ![](media/service-insights/pbi-insights-tile.png)
5. Há alguma informação que desperte o seu interesse? Selecione esse cartão de informação para investigar melhor. A Informação Rápida selecionada é apresentada à esquerda e os cartões de informações novos, com base apenas nos dados nessa Informação Rápida, são apresentados à direita.
6. Continue a investigar os seus dados e, quando encontrar uma Informação Rápida interessante, afixe o respetivo visual ao seu dashboard ao selecionar **Afixar visual** no canto superior direito. Pode também enviar comentários para dizer ao proprietário do conjunto de dados se uma determinada Informação Rápida foi ou não útil.
   
    ![](media/service-insights/useful.png)

## <a name="next-steps"></a>Próximos passos
Se é proprietário de um conjunto de dados, [otimize-o para as Informações Rápidas](service-insights-optimize.md)

Saiba mais sobre os [tipos de Informações Rápidas disponíveis](service-insight-types.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

