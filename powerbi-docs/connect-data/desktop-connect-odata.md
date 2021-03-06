---
title: Ligar ao feed OData no Power BI Desktop
description: Ligar e utilizar facilmente um feed OData no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: d1a4e8f7d5a057b51de7284d0db0b2440ccb93df
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926446"
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>Ligar a feeds OData no Power BI Desktop
No Power BI Desktop, pode ligar-se a um **feed OData** e utilizar os dados subjacentes, tal como faria com outra origem de dados no Power BI Desktop.

Para se ligar a um feed OData, selecione **Obter Dados > Feed OData** no friso **Base** no Power BI Desktop.

![Captura de ecrã a mostrar o friso Obter Dados no Power B I Desktop, com a seleção de Feed OData.](media/desktop-connect-odata/connect-to-odata_1.png)

Na janela **Feed OData** que for apresentada, escreva ou cole o seu URL do feed OData na caixa e selecione **OK**.

![Captura de ecrã a mostrar a caixa de diálogo do Feed OData, com o campo de URL.](media/desktop-connect-odata/connect-to-odata_2.png)

O Power BI Desktop liga-se ao feed OData e mostra as tabelas e outros elementos de dados disponíveis na janela do **Navegador**. Quando selecionar um elemento, o painel direito da janela do **Navegador** mostra uma pré-visualização dos dados. Pode selecionar todas as tabelas que pretender importar. A janela do **Navegador** mostra uma pré-visualização da tabela atualmente selecionada.

![Captura de ecrã a mostrar a caixa de diálogo Navegador com uma pré-visualização dos dados selecionados da tabela.](media/desktop-connect-odata/connect-to-odata_3.png)

Pode selecionar o botão **Editar** que faz abrir o **Editor de Consultas**, onde pode formatar e transformar os dados do feed OData antes de importá-los para o Power BI Desktop. Pode também selecionar o botão **Carregar** e importar todos os elementos de dados que selecionou no painel à esquerda.

Quando selecionarmos **Carregar**, o Power BI Desktop importa os itens selecionados e mostra uma janela **Carregar** do progresso de importação.

![Captura de ecrã a mostrar a caixa de diálogo Carregar com o progresso de importação.](media/desktop-connect-odata/connect-to-odata_4.png)

Após a conclusão, o Power BI Desktop disponibiliza as tabelas e outros elementos de dados selecionados no painel **Campos**, que se encontra no lado direito da vista de *Relatórios* no Power BI Desktop.

![Captura de ecrã a mostrar o painel Campos com a lista de tabelas selecionadas.](media/desktop-connect-odata/connect-to-odata_5.png)

E já está!

Está pronto para utilizar os dados importados do feed OData no Power BI Desktop para criar visuais, relatórios ou interagir com outros dados aos quais se possa querer ligar e importar, como outros livros do Excel, bases de dados ou outra origem de dados.

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
