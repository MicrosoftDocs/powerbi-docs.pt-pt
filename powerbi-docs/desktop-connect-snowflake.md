---
title: "Ligar a um armazém de informática de Snowflake no Power BI Desktop"
description: "Ligar e utilizar facilmente um armazém de informática de Snowflake no Power BI Desktop"
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: f82c0c2f0fa07e083a06ef3265001e60d797a0ed
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Ligar ao Snowflake no Power BI Desktop
No Power BI Desktop, pode ligar a um armazém de informática de **Snowflake** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop. 

> [!NOTE]
> Também *tem* de instalar o **Controlador ODBC do Snowflake** nos computadores que utilizam o conector **Snowflake**, utilizando a arquitetura que corresponda à instalação do **Power BI Desktop**, de 32 ou 64 bits. Basta seguir a seguinte ligação e [transferir o controlador ODBC do Snowflake adequado](http://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Ligar a um armazém de informática de Snowflake
Para ligar a um armazém de informática de **Snowflake**, selecione **Obter Dados** do friso **Base** no Power BI Desktop. Selecione **Base de Dados** nas categorias no lado esquerdo e verá **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

Na janela do **Snowflake** que é apresentada, escreva ou cole o nome do seu armazém de informática de Snowflake na caixa e selecione **OK**. Tenha em atenção que pode optar por **Importar** dados diretamente para o Power BI ou pode utilizar o **DirectQuery**. Pode saber mais sobre [utilizar o DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Quando lhe for pedido, introduza o seu nome de utilizador e a palavra-passe.

![](media/desktop-connect-snowflake/connect_snowflake_4.png)

> [!NOTE]
> Depois de introduzir o seu nome de utilizador e a palavra-passe para um determinado servidor **Snowflake**, o Power BI Desktop utiliza as mesmas credenciais nas tentativas de ligação subsequentes. Pode modificar essas credenciais, acedendo a **Ficheiro > Opções e definições > Definições da origem de dados**.
> 
> 

Depois de a ligação ser concluída com êxito, é apresentada uma janela **Navegador**, que apresenta os dados disponíveis no servidor, dos quais pode selecionar um ou vários elementos para importar e utilizar no **Power BI Desktop**.

![](media/desktop-connect-snowflake/connect_snowflake_5.png)

Pode **Carregar** a tabela selecionada, que traz toda a tabela para o **Power BI Desktop**, ou pode **Editar** a consulta, que abre o **Editor de Consultas**, para poder filtrar e refinar o conjunto de dados que pretende utilizar, e carregar o conjunto de dados refinados para o **Power BI Desktop**.

## <a name="next-steps"></a>Passos seguintes
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
