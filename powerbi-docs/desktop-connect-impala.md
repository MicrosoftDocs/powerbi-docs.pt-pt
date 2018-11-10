---
title: Ligar a uma base de dados Impala no Power BI Desktop
description: Ligar e utilizar facilmente uma base de dados Impala no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b512a3e6ef3ead8d93e1b554fbab3aaed8a2a5a
ms.sourcegitcommit: b343e44dbafc0b718c564402593d4b6e3a8ce97c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51027397"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Ligar a uma base de dados Impala no Power BI Desktop
No Power BI Desktop, pode ligar a uma base de dados **Impala** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Ligar a uma base de dados Impala
Para ligar a uma base de dados **Impala**, siga os passos seguintes: 

1. Selecione **Obter Dados** no friso **Base** do Power BI Desktop. 

2. Selecione **Base de Dados** nas categorias no lado esquerdo. Em seguida, verá **Impala**.

    ![Obter Dados](media/desktop-connect-impala/connect_impala_2.png)

3. Na janela **Impala** apresentada, escreva ou cole o nome do seu servidor Impala na caixa. Em seguida, selecione **OK**. Pode **Importar** dados diretamente para o Power BI ou utilizar o **DirectQuery**. Saiba mais acerca da [utilização do DirectQuery](desktop-use-directquery.md).

    ![Janela Impala](media/desktop-connect-impala/connect_impala_3a.png)

4. Quando lhe for pedido, introduza as suas credenciais ou ligue-se de forma anónima. O conector Impala suporta a autenticação Anónima, Básica (nome de utilizador + palavra-passe) e do Windows.

    ![Conector Impala](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > Após introduzir o nome de utilizador e a palavra-passe para um determinado servidor **Impala**, o Power BI Desktop utiliza as mesmas credenciais nas tentativas de ligação subsequentes. Pode modificar essas credenciais, acedendo a **Ficheiro > Opções e definições > Definições da origem de dados**.


5. Depois de estabelecer ligação, uma janela **Navegador** aparece e apresenta os dados disponíveis no servidor. Escolha elementos a partir destes dados para importar e utilizar no **Power BI Desktop**.

    ![Janela Navegador](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações
Existem algumas limitações e considerações a ter em conta com o conector **Impala**:

* O conector Impala é suportado no gateway de dados no local, através de qualquer um dos três mecanismos de autenticação suportados.

## <a name="next-steps"></a>Próximos passos
Existem bastantes origens de dados diferentes às quais se pode ligar com o Power BI Desktop. Para obter mais informações sobre as origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Origens de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

