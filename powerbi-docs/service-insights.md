---
title: Gerar automaticamente as informações de dados com o Power BI
description: Saiba como obter informações sobre os conjuntos de dados e os mosaicos do dashboard.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 8be938b1a75f754b7c23a57a5a0ccfdb4e60032b
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34561891"
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Gerar automaticamente as informações de dados com o Power BI
Tem um novo conjunto de dados e não sabe exatamente por onde começar?  Precisa criar um dashboard rapidamente?  Deseja procurar informações que pode ter perdido?

Execute as informações rápidas para gerar visualizações interativas e interessantes com base nos seus dados. As informações rápidas podem ser executadas num conjunto de dados inteiro (informações rápidas) ou num mosaico específico do dashboard (informações de confinadas). Pode até executar informações numa informação!

> **NOTA**: as Informações não são compatíveis com o DirectQuery. Só funcionam com dados carregados para o Power BI.
> 

A funcionalidade de informações é criada com base num [conjunto de algoritmos de análise avançados](service-insight-types.md) crescente, desenvolvido em conjunto com o Microsoft Research, que continuaremos a utilizar para permitir que mais pessoas descubram informações nos dados de formas novas e intuitivas.

## <a name="run-quick-insights-on-a-dataset"></a>Executar as informações rápidas num conjunto de dados
Veja a Amanda a executar as informações rápidas num conjunto de dados, a abrir uma informação no Modo de detalhe, a afixar uma dessas informações como mosaico no dashboard dela e, em seguida, a obter as informações para um mosaico do dashboard.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Agora, é a sua vez. Explore as informações através do [exemplo de Análise de Qualidade do Fornecedor](sample-supplier-quality.md).

1. No separador **Conjuntos de dados**, selecione as reticências (...) e escolha **Obter informações**.
   
    ![Separador Conjuntos de Dados](media/service-insights/power-bi-ellipses.png)
   
    ![menu de reticências](media/service-insights/power-bi-tab.png)
2. O Power BI usa [vários algoritmos](service-insight-types.md) para pesquisar tendências no conjunto de dados.
   
    ![Caixa de diálogo A procurar informações](media/service-insights/pbi_autoinsightssearching.png)
3. Em poucos segundos, as informações estão prontas.  Selecione **Ver informações** para apresentar as visualizações.
   
    ![mensagem de êxito](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **NOTA**: alguns conjuntos de dados não conseguem gerar informações, porque os dados não são estatisticamente significativos.  Para saber mais, veja [Optimize your data for insights (Otimizar os dados das informações)](service-insights-optimize.md).
   > 
   > 
1. As visualizações são apresentadas numa tela especial de **Informações Rápidas** com até 32 cartões de informações diferentes. Cada cartão contém um gráfico e uma breve descrição.
   
    ![tela Informações Rápidas](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interagir com os cartões das informações
  ![ícone afixar](media/service-insights/pbi_hover.png)

1. Passe o cursor sobre um cartão e selecione o ícone do pino para adicionar a visualização a um dashboard.
2. Coloque o cursor sobre um cartão, selecione as reticências (…) e escolha **Ver informações**. Esta ação abre a informação no ecrã inteiro.
   
    ![Informação no ecrã inteiro](media/service-insights/power-bi-insight-focus.png)
3. No Modo de detalhe, pode:
   
   * Filtrar as visualizações.  Para mostrar os filtros, no canto superior direito, selecione a seta para expandir o painel Filtros.
        ![informação e menu Filtros expandido](media/service-insights/power-bi-insights-filter-new.png)
   * Afixe o cartão de informações num dashboard ao selecionar o ícone ![ícone afixar](media/service-insights/power-bi-pin-icon.png) afixar ou **Afixar visual**.
   * Executar as informações no próprio cartão. Esta operação é muitas vezes denominada **informações confinadas**. No canto superior direito, selecione o ícone da lâmpada ![ícone Obter Informações](media/service-insights/power-bi-bulb-icon.png) ou **Obter informações**.
     
       ![barra de menus a mostrar o ícone Obter Informações](media/service-insights/pbi-autoinsights-tile.png)
     
     A informação é apresentada à esquerda e os cartões novos, com base apenas nos dados dessa informação, são apresentados à direita.
     
       ![informações em informações](media/service-insights/power-bi-insights-on-insights-new.png)
4. Para voltar à tela original das informações, no canto superior direito, selecione **Sair do Modo de detalhe**.

## <a name="run-insights-on-a-dashboard-tile"></a>Executar as informações num mosaico do dashboard
Em vez de procurar informações em todo um conjunto de dados, filtre a sua pesquisa de forma a procurar os dados utilizados para criar um único mosaico de dashboard. Esta operação também é muitas vezes denominada **informações confinadas**.

1. Abre um dashboard.
2. Coloque o cursor sobre um mosaico, selecione as reticências (...) e escolha **Ver informações**. O mosaico abre-se no [Modo de detalhe](service-focus-mode.md) com os cartões de informações apresentados no lado direito.    
   
    ![Modo de detalhe](media/service-insights/pbi-insights-tile.png)    
4. Há alguma informação que desperte o seu interesse? Selecione esse cartão de informação para investigar melhor. A informação selecionada é apresentada à esquerda e os cartões de informações novos, com base apenas nos dados dessa informação, são apresentados à direita.    
6. Continue a investigar os dados e, quando encontrar uma informação interessante, afixe-o ao dashboard ao selecionar **Afixar visual** no canto superior direito.

## <a name="next-steps"></a>Próximos passos
Se é proprietário de um conjunto de dados, [otimize-o para as Informações Rápidas](service-insights-optimize.md)

Saiba mais sobre os [tipos de Informações Rápidas disponíveis](service-insight-types.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

