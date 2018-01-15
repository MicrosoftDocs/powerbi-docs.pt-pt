---
title: Publicar a partir do Power BI Desktop
description: Publicar a partir do Power BI Desktop
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: ccf3f2a544276f3a641be3734fb2c48387706e69
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="publish-from-power-bi-desktop"></a>Publicar a partir do Power BI Desktop
Quando publica um ficheiro do **Power BI Desktop** no **serviço do Power BI**, os dados no modelo e quaisquer relatórios criados na vista de **Relatório** são publicados na sua área de trabalho do Power BI. Verá um novo conjunto de dados com o mesmo nome e todos os relatórios no navegador da Área de Trabalho.

Publicar através do **Power BI Desktop** tem o mesmo efeito que utilizar **Obter Dados** no Power BI para ligar e carregar um ficheiro do **Power BI Desktop**.

> [!NOTE]
> Quaisquer alterações feitas ao relatório do Power BI, por exemplo, adicionar, eliminar ou alterar visualizações em relatórios, não serão guardadas no ficheiro original do **Power BI Desktop**.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Para publicar um conjunto de dados e relatórios do Power BI Desktop
1. No Power BI Desktop \> **Ficheiro** \> **Publicar** \> **Publicar no Power BI** ou clique em **Publicar** no friso.  
   ![](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)
2. Inicie sessão no Power BI.

Quando terminar, receberá uma ligação para abrir o relatório no site do Power BI.  
    ![](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Publicar novamente ou substituir um conjunto de dados publicado a partir do Power BI Desktop
Ao publicar um ficheiro do **Power BI Desktop**, o conjunto de dados e relatórios criados no **Power BI Desktop** são carregados no seu site do Power BI. Quando publicar novamente o ficheiro do **Power BI Desktop**, o conjunto de dados no seu site Power BI será substituído pelo conjunto de dados atualizado do ficheiro do **Power BI Desktop**.

Isto é tudo muito simples, mas existem alguns aspetos que deve saber:

* Se tiver dois ou mais conjuntos de dados no Power BI com o mesmo nome que o ficheiro do **Power BI Desktop**, a publicação pode falhar. Verifique se tem apenas um conjunto de dados no Power BI com o mesmo nome. Também pode mudar o nome do ficheiro e publicar ao criar um novo conjunto de dados com o mesmo nome do ficheiro.
* Se mudar o nome ou eliminar uma coluna ou medida, quaisquer visualizações já existentes no Power BI com esse campo podem ficar corrompidas. 
* O Power BI ignora as alterações de formato de colunas existentes. Por exemplo, se alterar o formato de uma coluna de 0,25 para 25%.
* Se tiver uma agenda de atualização configurada para o conjunto de dados existente no Power BI e adicionar novas origens de dados para o ficheiro e, em seguida, publicar novamente, tem de iniciar a sessão em *Gerir Origens de Dados* antes da próxima atualização agendada.

