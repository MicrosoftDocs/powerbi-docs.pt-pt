---
title: Gerar informações de dados automaticamente com o Power BI
description: Saiba como obter informações sobre os conjuntos de dados e os mosaicos do dashboard.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 4178d9cc5ce6f8e671c0d996bb64ee9a1389acdb
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83306606"
---
# <a name="generate-data-insights-automatically-with-power-bi"></a>Gerar informações de dados automaticamente com o Power BI
Tem um novo conjunto de dados e não sabe exatamente por onde começar?  Precisa criar um dashboard rapidamente?  Deseja procurar informações que pode ter perdido?

Execute as informações rápidas para gerar visualizações interativas e interessantes com base nos seus dados. As informações rápidas podem ser executadas num conjunto de dados inteiro (informações rápidas) ou num mosaico específico do dashboard (informações de confinadas). Pode até executar informações numa informação!

> [!NOTE]
> As informações não são compatíveis com o DirectQuery. Só funcionam com dados carregados para o Power BI.
> 

A funcionalidade de informações é criada com base num [conjunto de algoritmos de análise avançados](../consumer/end-user-insight-types.md) crescente, desenvolvido em conjunto com o Microsoft Research, que continuaremos a utilizar para permitir que mais pessoas descubram informações nos dados de formas novas e intuitivas.

## <a name="run-quick-insights-on-a-dataset"></a>Executar as informações rápidas num conjunto de dados
Veja a Amanda a executar as informações rápidas num conjunto de dados, a abrir uma informação no Modo de detalhe, a afixar uma dessas informações como mosaico no dashboard dela e, em seguida, a obter as informações para um mosaico do dashboard.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Agora, é a sua vez. Explore as informações através do [exemplo de Análise de Qualidade do Fornecedor](sample-supplier-quality.md).

1. No separador **Conjuntos de dados**, selecione **Mais opções** (...) e selecione **Obter informações rápidas**.
   
    ![Separador Conjuntos de Dados](media/service-insights/power-bi-ellipses.png)
   
    ![Menu de reticências](media/service-insights/power-bi-tab.png)
2. O Power BI usa [vários algoritmos](../consumer/end-user-insight-types.md) para pesquisar tendências no conjunto de dados.
   
    ![Caixa de diálogo A procurar informações](media/service-insights/pbi_autoinsightssearching.png)
3. Em poucos segundos, as informações estão prontas.  Selecione **Ver informações** para apresentar as visualizações.
   
    ![Mensagem de êxito](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > Alguns conjuntos de dados não conseguem gerar informações, porque os dados não são estatisticamente significativos.  Para saber mais, veja [Optimize your data for insights (Otimizar os dados das informações)](service-insights-optimize.md).
    > 
    
4. As visualizações são apresentadas numa tela especial de **Informações Rápidas** com até 32 cartões de informações diferentes. Cada cartão contém um gráfico e uma breve descrição.
   
    ![tela Informações Rápidas](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interagir com os cartões das informações

1. Passe o cursor sobre um cartão e selecione o ícone do pino para adicionar a visualização a um dashboard.

2. Coloque o cursor sobre um cartão, selecione **Mais opções** (…) e, em seguida, selecione **Ver informações**. 

    É aberto o ecrã de informações em Modo de detalhe.
   
    ![Modo de detalhe de informações](media/service-insights/power-bi-insight-focus.png)
3. No Modo de detalhe, pode:
   
   * Filtrar as visualizações. Se o painel **Filtros** ainda não estiver aberto, expanda-o ao selecionar a seta no lado direito da janela.

       ![Menu Filtros de Informações expandido](media/service-insights/power-bi-insights-filter-new.png)
   * Afixe o cartão de informações a um dashboard ao selecionar **Afixar visual**.
   * Execute informações no próprio cartão, normalmente conhecido como *informações com âmbito*. No canto superior direito, selecione o ícone da lâmpada ![ícone Obter Informações](media/service-insights/power-bi-bulb-icon.png) ou **Obter Informações**.
     
       ![Ícone Obter Informações](media/service-insights/pbi-autoinsights-tile.png)
     
     A informação é apresentada à esquerda e os cartões novos, com base apenas nos dados dessa informação, são apresentados à direita.
     
       ![Informações sobre informações](media/service-insights/power-bi-insights-on-insights-new.png)
4. Para voltar à tela original das informações, no canto superior direito, selecione **Sair do Modo de detalhe**.

## <a name="run-insights-on-a-dashboard-tile"></a>Executar as informações num mosaico do dashboard
Em vez de procurar informações em todo um conjunto de dados, filtre a sua pesquisa de forma a obter informações apenas dos dados que são utilizados para criar um único mosaico de dashboard. 

1. Abra um dashboard.
2. Coloque o cursor sobre um mosaico, selecione **Mais opções** (...) e, em seguida, selecione **Ver informações**. O mosaico abre-se no [Modo de detalhe](../consumer/end-user-focus.md) com os cartões de informações apresentados no lado direito.    
   
    ![Modo de detalhe](media/service-insights/pbi-insights-tile.png)    
3. Há alguma informação que desperte o seu interesse? Selecione esse cartão de informação para investigar melhor. A informação selecionada é apresentada à esquerda e os cartões de informações novos, com base apenas nos dados dessa informação, são apresentados à direita.    
4. Continue a investigar os dados e, quando encontrar uma informação interessante, afixe-o ao dashboard ao selecionar **Afixar visual** no canto superior direito.

## <a name="next-steps"></a>Próximas etapas
- Se é proprietário de um conjunto de dados, [otimize-o para as Informações Rápidas](service-insights-optimize.md).
- Saiba mais sobre os [tipos de Informações Rápidas disponíveis](../consumer/end-user-insight-types.md).

Mais perguntas? [Experimente a Comunidade do Power BI](https://community.powerbi.com/).
