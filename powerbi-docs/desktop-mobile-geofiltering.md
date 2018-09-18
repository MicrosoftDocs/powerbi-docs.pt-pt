---
title: Definir filtros geográficos no Power BI Desktop para aplicações móveis
description: Ao definir filtros geográficos no seu modelo no Power BI Desktop, pode filtrar dados na sua localização automaticamente nas aplicações móveis do Power BI.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: 80d2039b2cfcac2f2c3db9c6f656561b670aa341
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44727496"
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>Definir filtros geográficos no Power BI Desktop para aplicações móveis
No Power BI Desktop, pode [categorizar dados geográficos](desktop-data-categorization.md) para uma coluna, para que o Power BI Desktop saiba como tratar os valores nos visuais num relatório. Como vantagem adicional, quando o utilizador ou os seus colegas virem esse relatório nas aplicações móveis do Power BI, o Power BI fornece automaticamente filtros geográficos correspondentes à sua localização. 

Por exemplo, suponhamos que é um gestor de vendas em viagem para se encontrar com clientes e pretende filtrar rapidamente a receita e as vendas totais do cliente específico que pretende visitar. Pretende saber os dados com base na sua localização atual, seja com base no estado, cidade ou num endereço específico. Mais tarde, se lhe sobrar tempo, pretende visitar outros clientes nas proximidades. Pode [filtrar o relatório consoante a sua localização para encontrar esses clientes](consumer/mobile/mobile-apps-geographic-filtering.md).

> [!NOTE]
> Só pode filtrar por localização na aplicação móvel se os nomes geográficos no relatório estiverem em inglês (por exemplo, "New York City" ou "Germany").
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>Identificar dados geográficos no seu relatório
1. No Power BI Desktop, mude para a Vista de Dados ![Ícone de Vista de Dados](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png).
2. Selecione uma coluna com dados geográficos (por exemplo, uma coluna de Cidade).
   
    ![Coluna Cidade](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. No separador **Modelação**, selecione **Categoria de Dados** e, em seguida, a categoria correta (neste exemplo, **Cidade**).
   
    ![Caixa Categoria de dados](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. Continue a definir as categorias de dados geográficos para outros campos no modelo. 
   
   > [!NOTE]
   > Pode definir múltiplas colunas para cada categoria de dados num modelo mas, se o fizer, o modelo não poderá filtrar com base em dados geográficos na aplicação móvel do Power BI. Para utilizar a filtragem geográfica nas aplicações móveis, defina apenas uma coluna para cada categoria de dados. Por exemplo, apenas uma coluna de **Cidade**, uma coluna de **Distrito** e uma coluna de **País**. 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>Criar visuais com os seus dados geográficos
1. Mude para a vista de Relatório ![Ícone de Vista de Relatório](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png)e crie visuais que utilizem os campos geográficos nos seus dados. 
   
    ![Relatório com mapa](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    Neste exemplo, o modelo também contém uma coluna calculada que junta cidade e estado numa só coluna. Saiba mais sobre [criar colunas calculadas no Power BI Desktop](desktop-calculated-columns.md).
   
    ![Campo Cidade + Estado](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Publique o relatório no serviço Power BI.

## <a name="view-the-report-in-power-bi-mobile-app"></a>Ver o relatório na aplicação móvel do Power BI
1. Abra o relatório numa das [aplicações móveis do Power BI](consumer/mobile/mobile-apps-for-mobile-devices.md).
2. Se estiver numa localização geográfica com dados no relatório, pode filtrá-los automaticamente com base na sua localização.
   
    ![Filtragem geográfica na aplicação móvel](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

Saiba mais sobre [filtrar um relatório por localização nas aplicações móveis do Power BI](consumer/mobile/mobile-apps-geographic-filtering.md).

## <a name="next-steps"></a>Próximos passos
* [Categorização de dados no Power BI Desktop](desktop-data-categorization.md)  
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

