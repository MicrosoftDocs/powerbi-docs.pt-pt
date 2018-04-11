---
title: "Ligar ao Adobe Analytics no Power BI Desktop (pré-visualização)"
description: Ligar e utilizar facilmente o Adobe Analytics no Power BI Desktop
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
ms.date: 03/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: efd6d066e2f98f86248730917c2f4aa0c8a39983
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2018
---
# <a name="connect-to-adobe-analytics-in-power-bi-desktop-preview"></a>Ligar ao Adobe Analytics no Power BI Desktop (pré-visualização)
No **Power BI Desktop**, pode ligar-se ao **Adobe Analytics** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop. 

![Obter Dados do Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

## <a name="enable-the-adobe-analytics-connector-preview"></a>Ativar a pré-visualização do conector do Adobe Analytics 
Uma vez que o conector do **Adobe Analytics** se encontra atualmente no modo de pré-visualização, terá de ativar a funcionalidade de pré-visualização para que o conector esteja disponível na janela **Obter Dados**. Para ativar a pré-visualização do conector, selecione **Ficheiro > Opções e Definições > Opções > Funcionalidades de Pré-visualização** no Power BI Desktop e, em seguida, selecione a caixa de verificação junto a **Marcadores**. 

![Ativar a pré-visualização do conector do Adobe Analytics em Opções](media/desktop-connect-adobe-analytics/connect-adobe-analytics_02.png)

Terá de reiniciar o **Power BI Desktop** após efetuar a seleção para ativar a pré-visualização do conector do Adobe Analytics.

## <a name="connect-to-adobe-analytics-data"></a>Ligar a dados do Adobe Analytics
Para ligar a dados do **Adobe Analytics**, selecione **Obter Dados** a partir do friso **Base** no Power BI Desktop. Selecione **Serviços Online** na lista de categorias no lado esquerdo para encontrar **Conector do Adobe Analytics**.

![Obter Dados do Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

Na janela **Adobe Analytics** que é apresentada, selecione o botão **Iniciar sessão** e forneça as suas credenciais para iniciar sessão na sua conta do Adobe Analytics. É apresentada a janela de início de sessão do Adobe, conforme ilustrado na seguinte imagem.

![Iniciar sessão no Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_03.png)

Quando lhe for pedido, introduza o seu nome de utilizador e a palavra-passe. Assim que a ligação for estabelecida, pode pré-visualizar e selecionar múltiplas dimensões e medidas na caixa de diálogo **Navegador** do para criar um único resultado em tabela. Também pode fornecer qualquer parâmetro de entrada necessário para os itens selecionados. 

![Selecionar dados através do Navegador](media/desktop-connect-adobe-analytics/connect-adobe-analytics_04.png)

Pode **Carregar** a tabela selecionada, que traz toda a tabela para o **Power BI Desktop**, ou pode **Editar** a consulta, que abre o **Editor de Consultas**, para poder filtrar e refinar o conjunto de dados que pretende utilizar, e carregar o conjunto de dados refinados para o **Power BI Desktop**.

![Carregar ou editar dados no Navegador](media/desktop-connect-adobe-analytics/connect-adobe-analytics_05.png)


## <a name="next-steps"></a>Passos seguintes
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
