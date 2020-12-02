---
title: Ligar a uma base de dados Amazon Redshift no Power BI Desktop
description: Ligar e utilizar facilmente uma base de dados Amazon Redshift no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 60bf73e4500785c766a485fffc92a25bd8f2c852
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411362"
---
# <a name="connect-to-an-amazon-redshift-database-in-power-bi-desktop"></a>Ligar a uma base de dados Amazon Redshift no Power BI Desktop
No **Power BI Desktop**, pode ligar a uma base de dados **Amazon Redshift** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

## <a name="connect-to-an-amazon-redshift-database"></a>Ligar a uma base de dados Amazon Redshift
Para ligar a uma base de dados **Amazon Redshift**, selecione **Obter Dados** a partir do friso **Base** no Power BI Desktop. Selecione **Base de Dados** nas categorias no lado esquerdo e verá **Amazon Redshift**.

![Captura de ecrã a mostrar a caixa de diálogo Obter Dados, com a seleção da base de dados Amazon Redshift.](media/desktop-connect-redshift/connect_redshift_3.png)

Na janela **Amazon Redshift** que é apresentada, escreva ou cole o nome do servidor e base de dados **Amazon Redshift** na caixa. Como parte do campo *Servidor*, os utilizadores podem especificar uma porta no seguinte formato: *ServerURL:Port*

![Captura de ecrã a mostrar a caixa de diálogo do Amazon Redshift, com os campos Server (Servidor) e Database (Base de Dados).](media/desktop-connect-redshift/connect_redshift_4.png)

Quando lhe for pedido, introduza o seu nome de utilizador e a palavra-passe. Para evitar erros, deve utilizar o nome do servidor que corresponde exatamente ao certificado SSL. 

![Captura de ecrã a mostrar o pedido de credenciais do Amazon Redshift, com os campos Username (Nome de utilizador) e Password (Palavra-passe).](media/desktop-connect-redshift/connect_redshift_5.png)

Depois de a ligação ser concluída com êxito, é apresentada uma janela **Navegador**, que apresenta os dados disponíveis no servidor, dos quais pode selecionar um ou vários elementos para importar e utilizar no **Power BI Desktop**.

![Captura de ecrã a mostrar a caixa de diálogo Navegador, com os dados disponíveis no servidor.](media/desktop-connect-redshift/connect_redshift_6.png)

Depois de efetuar as seleções na janela **Navegador** , pode **Carregar** ou **Editar** os dados.

* Se optar por **Carregar** os dados, ser-lhe-á pedido que utilize o modo de *Importação* ou o *DirectQuery* para carregar os dados. Para obter mais informações, veja este [artigo que explica o DirectQuery](desktop-use-directquery.md).
* Se optar por **Editar** os dados, o **Editor de Consultas** é apresentado, onde pode aplicar todos os tipos de transformações e filtros aos dados, muitos dos quais são aplicados à própria base de dados **Amazon Redshift** subjacente (caso seja suportada).

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
