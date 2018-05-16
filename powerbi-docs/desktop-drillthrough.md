---
title: Utilizar a pormenorização no Power BI Desktop
description: Saiba como desagregar os dados, numa nova página de relatório, no Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 4/10/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7be260a5989ffb6a9dc1b72dad90d227e0b6295b
ms.sourcegitcommit: bdb1fee3612bcc66153dcad8c4db2e99fb041014
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2018
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Utilizar a pormenorização no Power BI Desktop
Com a **pormenorização** no **Power BI Desktop**, pode criar uma página no relatório centrada numa entidade específica, por exemplo, um fornecedor, um cliente ou um fabricante. Com essa página do relatório em destaque, os utilizadores podem clicar com o botão direito do rato num ponto de dados noutras páginas do relatório e obter a pormenorização da página em destaque para obter detalhes filtrados em função desse contexto.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Utilizar a pormenorização
1. Para utilizar a **pormenorização**, crie uma página de relatório com elementos visuais que pretenda ver relativamente ao tipo de entidade para a qual irá fornecer pormenorização. 

    Por exemplo, se estiver interessado em fornecer uma pormenorização para fabricantes, pode criar uma página de pormenorização com visuais que demonstram vendas totais, unidades enviadas totais, vendas por categoria, vendas por região e assim por diante. Desta forma, quando pormenorizar nessa página, os elementos visuais serão específicos do fabricante selecionado.

2. Em seguida, na página de pormenorização, na secção **Campos** do painel **Visualizações**, arraste o campo sobre o qual pretende obter a pormenorização para a área **Filtros de pormenorização**.

    ![](media/desktop-drillthrough/drillthrough_02.png)

    Quando adicionar um campo à área **Filtros de pormenorização**, o **Power BI Desktop** irá automaticamente criar um visual de botão para *voltar*. Esse visual torna-se um botão nos relatórios publicados e permite aos utilizadores que consomem o seu relatório no **serviço Power BI** regressar facilmente à página de relatório de onde vieram (a página a partir da qual optaram por fazer a pormenorização).

    ![](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Utilizar a sua própria imagem para um botão Anterior    
 Uma vez que o botão Anterior é uma imagem, pode substituir a imagem desse elemento visual por uma imagem à sua escolha. Continuará a funcionar como o botão que direciona os consumidores de relatórios de volta para a página original.

1. No separador **Base**, clique em **Imagem** e, em seguida, localize a imagem e coloque-a na página de pormenorização.
2. Selecione a sua nova imagem na página Pormenorização e, na secção Formatar Imagem, coloque o controlo de deslize **Ligação** na posição de ativado e defina o **Tipo** como **Anterior**. A imagem funciona agora como um botão de retrocesso.

    ![](media/desktop-drillthrough/drillthrough_05.png)

    Quando a sua página de **pormenorização** estiver concluída e os utilizadores clicarem com o botão direito do rato num ponto de dados no relatório que utilize o campo que colocou na área **Filtros de pormenorização**, será apresentado um menu de contexto que permite a pormenorização nessa página.

    ![](media/desktop-drillthrough/drillthrough_04.png)

    Quando os consumidores de relatórios decidirem pormenorizar, a página será filtrada para mostrar informações sobre o ponto de dados no qual clicaram com o botão direito do rato. Por exemplo, se tiverem clicado com o botão direito do rato num ponto de dados sobre a Contoso (um fabricante) e optado por pormenorizar, a página de pormenorização de destino será filtrada para a Contoso.

    > [!NOTE]
    > Apenas o campo que está na área **Filtros de pormenorização** passa para a página do relatório de pormenorização. Não são passadas outras informações contextuais.
    > 
    > 

E é tudo o que precisa de saber sobre a utilização da **pormenorização** nos relatórios. É uma excelente forma de obter uma vista expandida sobre as informações da entidade que selecionou para o seu filtro de pormenorização.

