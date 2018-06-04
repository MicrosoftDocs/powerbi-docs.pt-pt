---
title: Ligar a uma base de dados Impala no Power BI Desktop
description: Ligar e utilizar facilmente uma base de dados Impala no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b00120a0c4c22ba8f031663ab19d94d2c482d3b
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34287699"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Ligar a uma base de dados Impala no Power BI Desktop
No Power BI Desktop, pode ligar a uma base de dados **Impala** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Ligar a uma base de dados Impala
Para ligar a uma base de dados **Impala**, selecione **Obter Dados** do friso **Base** no Power BI Desktop. Selecione **Base de Dados** nas categorias no lado esquerdo e verá **Impala**.

![](media/desktop-connect-impala/connect_impala_2.png)

Na janela **Impala** que é apresentada, escreva ou cole o nome do seu servidor Impala na caixa e selecione **OK**. Tenha em atenção que pode optar por **Importar** dados diretamente para o Power BI ou pode utilizar o **DirectQuery**. Pode saber mais sobre [utilizar o DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-impala/connect_impala_3a.png)

Quando lhe for pedido, introduza as suas credenciais ou ligue-se de forma anónima. O conector Impala suporta a autenticação Anónima, Básica (nome de utilizador + palavra-passe) e do Windows.

![](media/desktop-connect-impala/connect_impala_4.png)

> [!NOTE]
> Depois de colocar o seu nome de utilizador e palavra-passe para um determinado servidor **Impala**, o Power BI Desktop utiliza as mesmas credenciais nas tentativas de ligação subsequentes. Pode modificar essas credenciais, acedendo a **Ficheiro > Opções e definições > Definições da origem de dados**.
> 
> 

Depois de a ligação ser concluída com êxito, é apresentada uma janela **Navegador**, que apresenta os dados disponíveis no servidor, dos quais pode selecionar um ou vários elementos para importar e utilizar no **Power BI Desktop**.

![](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Considerações e Limitações
Existem alguns limites e considerações a ter em conta com o conector **Impala**:

* O conector do Impala é suportado no gateway de dados No Local, através de qualquer um dos três mecanismos de autenticação suportados.

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

