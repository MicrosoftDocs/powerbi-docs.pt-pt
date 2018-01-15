---
title: Ligar a uma base de dados Impala no Power BI Desktop
description: Ligar e utilizar facilmente uma base de dados Impala no Power BI Desktop
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 80460bbcf8fb61bc8149304b3be359cd744c1b75
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Ligar a uma base de dados Impala no Power BI Desktop
No Power BI Desktop, pode ligar a uma base de dados **Impala** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Ligar a uma base de dados Impala
Para ligar a uma base de dados **Impala**, selecione **Obter Dados** do friso **Base** no Power BI Desktop. Selecione **Base de Dados** nas categorias no lado esquerdo e verá **Impala**.

![](media/desktop-connect-impala/connect_impala_2.png)

Na janela **Impala** que é apresentada, escreva ou cole o nome do seu servidor Impala na caixa e selecione **OK**. Tenha em atenção que pode optar por **Importar** dados diretamente para o Power BI ou pode utilizar o **DirectQuery**. Pode saber mais sobre [utilizar o DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-impala/connect_impala_3a.png)

Quando lhe for pedido, introduza o seu nome de utilizador e a palavra-passe, ou ligue anonimamente: ambos são suportados.

![](media/desktop-connect-impala/connect_impala_4.png)

> [!NOTE]
> Depois de colocar o seu nome de utilizador e palavra-passe para um determinado servidor **Impala**, o Power BI Desktop utiliza as mesmas credenciais nas tentativas de ligação subsequentes. Pode modificar essas credenciais, acedendo a **Ficheiro > Opções e definições > Definições da origem de dados**.
> 
> 

Depois de a ligação ser concluída com êxito, é apresentada uma janela **Navegador**, que apresenta os dados disponíveis no servidor, dos quais pode selecionar um ou vários elementos para importar e utilizar no **Power BI Desktop**.

![](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Considerações e Limitações
Existem alguns limites e considerações a ter em conta com o conector **Impala**:

* Os planos futuros incluem ativar o suporte de atualização com o **Gateway do Power BI**.

## <a name="next-steps"></a>Passos seguintes
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

