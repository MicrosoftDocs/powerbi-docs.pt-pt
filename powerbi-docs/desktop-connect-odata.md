---
title: Ligar ao feed OData no Power BI Desktop
description: Ligar e utilizar facilmente um feed OData no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1b744676deecbd84890057af84e331d6e7a15e90
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>Ligar a feeds OData no Power BI Desktop
No Power BI Desktop, pode ligar-se a um **feed OData** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

Para se ligar a um feed OData, selecione **Obter Dados > Feed OData** no friso **Base** no Power BI Desktop.

![](media/desktop-connect-odata/connect-to-odata_1.png)

Na janela **Feed OData** que for apresentada, escreva ou cole o seu URL do feed OData na caixa e selecione **OK**.

![](media/desktop-connect-odata/connect-to-odata_2.png)

O Power BI Desktop liga-se ao feed OData e mostra as tabelas e outros elementos de dados disponíveis na janela do **Navegador**. Quando selecionar um elemento, o painel direito da janela do **Navegador** mostra uma pré-visualização dos dados. Pode selecionar todas as tabelas que pretender importar. A janela do **Navegador** mostra uma pré-visualização da tabela atualmente selecionada.

![](media/desktop-connect-odata/connect-to-odata_3.png)

Pode selecionar o botão **Editar** que faz abrir o **Editor de Consultas**, onde pode formatar e transformar os dados do feed OData antes de importá-los para o Power BI Desktop. Pode também selecionar o botão **Carregar** e importar todos os elementos de dados que selecionou no painel à esquerda.

Quando selecionarmos **Carregar**, o Power BI Desktop importa os itens selecionados e mostra uma janela **Carregar** do progresso de importação.

![](media/desktop-connect-odata/connect-to-odata_4.png)

Após a conclusão, o Power BI Desktop disponibiliza as tabelas e outros elementos de dados selecionados no painel **Campos**, que se encontra no lado direito da vista de *Relatórios* no Power BI Desktop.

![](media/desktop-connect-odata/connect-to-odata_5.png)

E já está!

Está pronto para utilizar os dados importados do feed OData no Power BI Desktop para criar visuais, relatórios ou interagir com outros dados aos quais se possa querer ligar e importar, como outros livros do Excel, bases de dados ou outra origem de dados.

### <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

