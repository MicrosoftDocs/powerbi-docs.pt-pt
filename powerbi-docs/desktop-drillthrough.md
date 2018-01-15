---
title: "Utilizar a pormenorização no Power BI Desktop"
description: "Saiba como desagregar os dados, numa nova página de relatório, no Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: c4482b8a8b7510b54b317ef9731057a52501d47c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Utilizar a pormenorização no Power BI Desktop
Com a **pormenorização** no **Power BI Desktop**, pode criar uma página no relatório que se foca numa entidade específica, por exemplo, um fornecedor, cliente ou fabricante. Com essa página de relatório direcionada, os utilizadores podem clicar com o botão direito do rato num ponto de dados noutras páginas de relatórios e pormenorizar na página direcionada para obter detalhes filtrados em função desse contexto.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Utilizar a pormenorização
Para utilizar a **pormenorização**, crie uma página de relatório com visuais que pretenda ver relativamente ao tipo de entidade para a qual irá fornecer pormenorização. Por exemplo, se estiver interessado em fornecer uma pormenorização para fabricantes, pode criar uma página de pormenorização com visuais que demonstram vendas totais, unidades enviadas totais, vendas por categoria, vendas por região e assim por diante. Desta forma, quando pormenorizar nessa página, os visuais serão específicos do fabricante no qual clicou e cuja pormenorização selecionou.

Em seguida, na página de pormenorização, na secção **Campos** do painel **Visualizações**, arraste o campo sobre o qual pretende pormenorizar para a área **Filtros de pormenorização**.

![](media/desktop-drillthrough/drillthrough_02.png)

Quando adicionar um campo à área **Filtros de pormenorização**, o **Power BI Desktop** irá automaticamente criar um visual de botão para *voltar*. Esse visual torna-se um botão nos relatórios publicados e permite aos utilizadores que consomem o seu relatório no **serviço Power BI** regressar facilmente à página de relatório de onde vieram (a página a partir da qual optaram por fazer a pormenorização).

![](media/desktop-drillthrough/drillthrough_03.png)

Uma vez que o botão *voltar* é uma imagem, pode substituir a imagem desse visual por uma imagem à sua escolha. Continuará a funcionar devidamente como o botão que direciona os consumidores de relatórios de volta para a página original. Para utilizar a sua própria imagem para um botão de voltar, basta colocar um visual de imagem na página de pormenorização e, em seguida, selecionar o visual e ativar o controlador de deslize *Botão anterior*. Esta ação fará com que a imagem funcione como um botão *voltar*.

![](media/desktop-drillthrough/drillthrough_05.png)

Quando a sua página de **pormenorização** estiver concluída, quando os utilizadores clicarem com o botão direito do rato num ponto de dados no seu relatório que utilize o campo que colocou na área **Filtros de pormenorização** na sua página de pormenorização, é apresentado um menu de contexto que permite aos utilizadores pormenorizar nessa página.

![](media/desktop-drillthrough/drillthrough_04.png)

Quando estes decidirem pormenorizar, a página é filtrada para mostrar informações sobre o ponto de dados no qual clicaram com o botão direito do rato. Por exemplo, se tiverem clicado com o botão direito do rato num ponto de dados sobre a Contoso (um fabricante) e optado por pormenorizar, a página de pormenorização de destino será filtrada para a Contoso.

> [!NOTE]
> Apenas o campo que está na área **Filtros de pormenorização** passa para a página do relatório de pormenorização. Não são passadas outras informações contextuais.
> 
> 

E é tudo o que precisa de saber sobre a utilização da **pormenorização** nos seus relatórios. É uma excelente forma de obter uma vista expandida sobre as informações da entidade que selecionou para o seu filtro de pormenorização.

