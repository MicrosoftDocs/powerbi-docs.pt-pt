---
title: Ligar a um ficheiro PDF no Power BI Desktop
description: Ligar a e utilizar facilmente dados de ficheiros PDF no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 07/16/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: ba0c1c6babe63c02ef0cd96a7cb5695e2c916c68
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405773"
---
# <a name="connect-to-pdf-files-in-power-bi-desktop"></a>Ligar a ficheiros PDF no Power BI Desktop
No Power BI Desktop, pode ligar a um **ficheiro PDF** e utilizar os dados incluídos do ficheiro tal como faria com outra origem de dados no Power BI Desktop.

![Ligar a dados em ficheiros PDF](media/desktop-connect-pdf/connect-pdf-04.png)

As secções seguintes descrevem como pode ligar a um **ficheiro PDF**, selecionar dados e importar esses dados para o **Power BI Desktop**.

Recomendamos sempre que atualize para a versão mais recente do **Power BI Desktop**, que pode obter através de uma ligação no artigo [Obter o Power BI Desktop](../fundamentals/desktop-get-the-desktop.md). 

## <a name="connect-to-a-pdf-file"></a>Connect to a PDF file (Ligar a um ficheiro PDF)
Para ligar a um ficheiro **PDF**, selecione **Obter Dados** no friso **Base** do Power BI Desktop. Selecione **Ficheiro** nas categorias no lado esquerdo e verá **PDF**.

![Selecionar PDF em Obter Dados](media/desktop-connect-pdf/connect-pdf-01.png)

É-lhe pedido para indicar a localização do ficheiro PDF que pretende utilizar. Depois de indicar a localização do ficheiro e de o ficheiro PDF ser carregado, é apresentada a janela **Navegador** que apresenta os dados disponíveis no ficheiro, a partir do qual pode selecionar um ou vários elementos a importar e utilizar no **Power BI Desktop**.

![Ligar a dados em ficheiros PDF](media/desktop-connect-pdf/connect-pdf-04.png)

Se selecionar a caixa de verificação junto aos elementos detetados no ficheiro PDF, estes são apresentados no painel à direita. Quando estiver pronto para importar, selecione o botão **Carregar** para importar os dados para o **Power BI Desktop**.

A partir da versão de novembro de 2018 do **Power BI Desktop**, pode especificar a **Página Inicial** e a **Página Final** como parâmetros opcionais para a sua ligação de PDF. Também pode especificar estes parâmetros na linguagem da fórmula M com o seguinte formato:

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`

## <a name="limitations-and-considerations"></a>Limitações e considerações

Ao trabalhar com o conector PDF em conjuntos de dados numa capacidade Premium, a ligação não será feita corretamente. Para permitir que o conector PDF funcione num conjunto de dados numa capacidade Premium, configure esse conjunto de dados para utilizar um gateway e confirme que a ligação a esse conjunto de dados passa pelo gateway.  


## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
