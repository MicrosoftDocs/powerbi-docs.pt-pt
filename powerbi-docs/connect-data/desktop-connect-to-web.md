---
title: Ligar a uma página Web a partir do Power BI Desktop
description: Ligar-se e utilizar facilmente dados de páginas Web no Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f2e61617e060d90a30aebd1ddc47a72b712c271c
ms.sourcegitcommit: 029aacd09061a8aa45b57f05d0dc95c93dd16a74
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/12/2020
ms.locfileid: "94559899"
---
# <a name="connect-to-webpages-from-power-bi-desktop"></a>Ligar a páginas Web a partir do Power BI Desktop

Pode ligar a uma página Web e importar os respetivos dados para o Power BI Desktop para utilizar nos seus elementos visuais e modelos de dados.

No Power BI Desktop, selecione **Obter Dados > Web** do friso **Base**.

![Captura de ecrã a mostrar o Power B I Desktop com a seleção Web.](media/desktop-connect-to-web/connect-to-web-01.png)

Aparece uma caixa de diálogo a pedir o URL da página Web da qual pretende importar dados.

![Captura de ecrã a mostrar a caixa de diálogo Web com o campo de URL.](media/desktop-connect-to-web/connect-to-web-02.png)

Após escrever (ou colar) o URL, selecione **OK**. O Power BI Desktop pede-lhe para especificar como quer aceder aos conteúdos da Web.

![Credenciais a utilizar na ligação à Web](media/desktop-connect-to-web/connect-to-web-03.png)

O Power BI Desktop liga-se à página Web e, em seguida, apresenta os dados disponíveis da página na janela **Navegador**. Quando selecionar um dos elementos de dados disponíveis, como uma tabela da página inteira, a janela do **Navegador** mostra uma pré-visualização desses dados no lado direito da janela.

![Captura de ecrã a mostrar a caixa de diálogo Navegador com uma pré-visualização dos dados selecionados da tabela.](media/desktop-connect-to-web/connect-to-web-04.png)

Pode selecionar o botão **Transformar Dados** para abrir o **Editor de Consultas**, onde pode formatar e transformar os dados nessa página Web antes de importá-los para o Power BI Desktop. Pode também selecionar o botão **Carregar** e importar todos os elementos de dados que selecionou no painel à esquerda.

Quando selecionar **Carregar**, o Power BI Desktop importa os itens selecionados e disponibiliza-os no painel **Campos**, que se encontra no lado direito da vista Relatórios no Power BI Desktop.

![Captura de ecrã a mostrar o painel Campos com uma lista de tabelas selecionadas.](media/desktop-connect-to-web/connect-to-web-05.png)

É tudo o que precisa de saber sobre ligar a uma página Web e levar os seus dados ao Power BI Desktop.

A partir daí, pode arrastar esses campos para a tela de Relatório e criar as visualizações que pretender. Também pode utilizar os dados dessa página Web tal como faria com outro tipo de dados: pode formatá-los, criar relações entre os mesmos e outras origens de dados no modelo, bem como fazer o que pretende para criar o relatório do Power BI pretendido.

Para ver a ligação a páginas Web em ação e de forma mais aprofundada, consulte o [Guia de Introdução ao Power BI Desktop](../fundamentals/desktop-getting-started.md).

## <a name="certificate-revocation-check"></a>Verificação de revogação de certificados

O Power BI aplica segurança para ligações Web para proteger os seus dados. Em alguns cenários, como a captura de pedidos Web com o Fiddler, as ligações Web podem não funcionar corretamente. Para ativar esses cenários, pode desselecionar a opção **Ativar a verificação de revogação de certificados** no Power BI Desktop e, em seguida, reiniciar o Power BI Desktop. 

Para alterar esta opção, selecione **Ficheiro > Opções** e, em seguida, selecione **Segurança** no painel esquerdo. A imagem seguinte mostra a caixa de verificação. Desselecionar a caixa tornará as ligações Web menos seguras. 

![Ativar ou desativar a verificação de revogação de certificados](media/desktop-connect-to-web/connect-to-web-06.png)


## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Ligar a ficheiros CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
