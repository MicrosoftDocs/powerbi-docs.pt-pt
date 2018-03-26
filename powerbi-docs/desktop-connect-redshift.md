---
title: Ligar a uma base de dados Amazon Redshift no Power BI Desktop
description: Ligar e utilizar facilmente uma base de dados Amazon Redshift no Power BI Desktop
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
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9597d056067fb1af291f46a088b94a39da57eab9
ms.sourcegitcommit: 00b4911ab5fbf4c2d5ffc000a3d95b3149909c28
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="connect-to-amazon-redshift-in-power-bi-desktop"></a>Ligar ao Redshift Amazon no Power BI Desktop
No **Power BI Desktop**, pode ligar a uma base de dados **Amazon Redshift** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

## <a name="connect-to-an-amazon-redshift-database"></a>Ligar a uma base de dados Amazon Redshift
Para ligar a uma base de dados **Amazon Redshift**, selecione **Obter Dados** a partir do friso **Base** no Power BI Desktop. Selecione **Base de Dados** nas categorias no lado esquerdo e verá **Amazon Redshift**.

![](media/desktop-connect-redshift/connect_redshift_3.png)

Na janela **Amazon Redshift** que é apresentada, escreva ou cole o nome do servidor e base de dados **Amazon Redshift** na caixa. Como parte do campo *Servidor*, os utilizadores podem especificar uma porta no seguinte formato: *ServerURL:Port*

![](media/desktop-connect-redshift/connect_redshift_4.png)

Quando lhe for pedido, introduza o seu nome de utilizador e a palavra-passe.

![](media/desktop-connect-redshift/connect_redshift_5.png)

Depois de a ligação ser concluída com êxito, é apresentada uma janela **Navegador**, que apresenta os dados disponíveis no servidor, dos quais pode selecionar um ou vários elementos para importar e utilizar no **Power BI Desktop**.

![](media/desktop-connect-redshift/connect_redshift_6.png)

Depois de efetuar as seleções na janela **Navegador** , pode **Carregar** ou **Editar** os dados.

* Se optar por **Carregar** os dados, ser-lhe-á pedido que utilize o modo de *Importação* ou o *DirectQuery* para carregar os dados. Para obter mais informações, veja este [artigo que explica o DirectQuery](desktop-use-directquery.md).
* Se optar por **Editar** os dados, o **Editor de Consultas** é apresentado, onde pode aplicar todos os tipos de transformações e filtros aos dados, muitos dos quais são aplicados à própria base de dados **Amazon Redshift** subjacente (caso seja suportada).

## <a name="next-steps"></a>Passos seguintes
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

