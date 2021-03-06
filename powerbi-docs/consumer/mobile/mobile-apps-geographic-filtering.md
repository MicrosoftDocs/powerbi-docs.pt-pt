---
title: Filtrar relatório por localização geográfica numa aplicação móvel do Power BI
description: Saiba como pode filtrar um relatório com base na sua localização geográfica nas aplicações móveis do Power BI, se o proprietário do relatório tiver definido etiquetas geográficas.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.openlocfilehash: fe5ab9befcf54a617aefa5ad281872f45a59229c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388983"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Filtrar um relatório por localização geográfica nas aplicações móveis do Power BI
Aplica-se a:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Telemóvel Android](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Tablet Android](./media/mobile-apps-view-dashboard/android-tablet-logo-50-px.png) | ![Windows Phone](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Telemóveis Android |Tablets Android |Telemóveis Windows 10 |

Quando vê um relatório do Power BI no seu dispositivo móvel, vê um pequeno ícone de alfinete no canto superior direito? Se for esse o caso, pode filtrar esse relatório com base na sua localização geográfica.

> [!NOTE]
> Só pode filtrar por localização se os nomes geográficos no relatório estiverem em inglês (por exemplo, "New York City" ou "Germany"). Os tablets e PCs com Windows 10 não suportam a filtragem geográfica, mas os telemóveis com Windows 10 suportam.

>[!NOTE]
>O suporte à aplicação móvel do Power BI para **telemóveis com o Windows 10 Mobile** será descontinuado a 16 de março de 2021. [Saber mais](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="filter-your-report-by-your-geographic-location"></a>Filtrar o relatório consoante a sua localização geográfica
1. Abra um relatório na aplicação móvel do Power BI para o seu dispositivo móvel.
2. Se o relatório tiver dados geográficos, irá ver uma mensagem do Power BI a pedir acesso à sua localização. Clique em **Permitir** e, em seguida, toque novamente em **Permitir**.
3. Toque no ícone de alfinete ![Ícone de alfinete](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). Pode filtrar por cidade, distrito ou país/região, consoante os dados no relatório. O filtro só lista opções correspondentes à sua localização atual.
   
    ![Alfinete de filtro](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>Por que motivo não vejo etiquetas de localização num relatório?
Para que possa ver as etiquetas de localização, as seguintes três condições precisam de ser cumpridas. 

* A pessoa que criou o relatório no Power BI Desktop terá de ter [categorizado os dados geográficos](../../transform-model/desktop-mobile-geofiltering.md) em pelo menos uma coluna, como Cidade, Estado ou País/Região.
* Está numa das localizações que tem dados na coluna.
* Está a utilizar um dos seguintes dispositivos móveis:
  * iOS (iPad, iPhone, iPod).
  * Android (telemóvel, tablet).
  * Telemóvel Windows 10 (os outros dispositivos com Windows 10, como PCs e tablets, não suportam a filtragem geográfica).

Leia mais sobre [configurar a filtragem geográfica](../../transform-model/desktop-mobile-geofiltering.md) no Power BI Desktop.

### <a name="next-steps"></a>Próximas etapas
* [Ligar-se a dados do Power BI do mundo real](mobile-apps-data-in-real-world-context.md) com as aplicações móveis
* [Categorização de dados no Power BI Desktop](../../transform-model/desktop-data-categorization.md) 
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)