---
title: Ligar a um ficheiro PDF no Power BI Desktop
description: Ligar a e utilizar facilmente dados de ficheiros PDF no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0c63a62edfce62a5cee13bef3c68014027313e8b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513998"
---
# <a name="connect-to-a-pdf-file-in-power-bi-desktop"></a>Ligar a um ficheiro PDF no Power BI Desktop
No Power BI Desktop, pode ligar a um **ficheiro PDF** e utilizar os dados incluídos do ficheiro tal como faria com outra origem de dados no Power BI Desktop.

![Ligar a dados em ficheiros PDF](media/desktop-connect-pdf/connect-pdf_04.png)

As secções seguintes descrevem como pode ligar a um **ficheiro PDF**, selecionar dados e importar esses dados para o **Power BI Desktop**.

Recomendamos sempre que atualize para a versão mais recente do **Power BI Desktop**, que pode obter através de uma ligação no artigo [Obter o Power BI Desktop](desktop-get-the-desktop.md). 

## <a name="connect-to-a-pdf-file"></a>Ligar a um ficheiro PDF
Para ligar a um ficheiro **PDF**, selecione **Obter Dados** no friso **Base** do Power BI Desktop. Selecione **Ficheiro** nas categorias no lado esquerdo e verá **PDF (beta)** .

![Selecionar PDF em Obter Dados](media/desktop-connect-pdf/connect-pdf_01.png)

É-lhe pedido para indicar a localização do ficheiro PDF que pretende utilizar. Depois de indicar a localização do ficheiro e de o ficheiro PDF ser carregado, é apresentada a janela **Navegador** que apresenta os dados disponíveis no ficheiro, a partir do qual pode selecionar um ou vários elementos a importar e utilizar no **Power BI Desktop**.

![Ligar a dados em ficheiros PDF](media/desktop-connect-pdf/connect-pdf_04.png)

Se selecionar a caixa de verificação junto aos elementos detetados no ficheiro PDF, estes são apresentados no painel à direita. Quando estiver pronto para importar, selecione o botão **Carregar** para importar os dados para o **Power BI Desktop**.

A partir da versão de novembro de 2018 do **Power BI Desktop**, pode especificar a **Página Inicial** e a **Página Final** como parâmetros opcionais para a sua ligação de PDF. Também pode especificar estes parâmetros na linguagem da fórmula M com o seguinte formato:

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`


## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

