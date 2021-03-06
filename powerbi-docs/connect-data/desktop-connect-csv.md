---
title: Ligar a ficheiros CSV no Power BI Desktop
description: Ligar-se e utilizar facilmente dados de ficheiros CSV no Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 3bb37d4ba3b3ca7d5fec3f8577b971432f5a9d0f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411385"
---
# <a name="connect-to-csv-files-in-power-bi-desktop"></a>Ligar a ficheiros CSV no Power BI Desktop
Ligar-se a um ficheiro de valores separados por vírgulas (*CSV*) do Power BI Desktop é muito parecido com ligar a um livro do Excel. Ambas as ações são simples e este artigo mostra-lhe os passos para ligar-se a ficheiros CSV aos quais tenha acesso.

Para começar, a partir do Power BI Desktop, selecione **Obter Dados > CSV** do friso **Base**.

![Captura de ecrã a mostrar o menu Obter Dados.](media/desktop-connect-csv/connect-to-csv_1.png)

Selecione o seu ficheiro CSV na caixa de diálogo **Abrir** que for apresentada.

![Captura de ecrã a mostrar a caixa de diálogo Abrir.](media/desktop-connect-csv/connect-to-csv_2.png)

Quando selecionar **Abrir**, o Power BI Desktop acede ao ficheiro e determina certos atributos de ficheiro, como a origem do ficheiro, o tipo de delimitador e quantas linhas devem ser utilizadas para detetar os tipos de dados no ficheiro.

Estes atributos e opções são apresentados nas seleções de menus pendentes na parte superior da caixa de diálogo **Importação CSV**, mostrada abaixo. Pode alterar manualmente qualquer uma destas definições detetadas ao selecionar outra opção a partir dos seletores pendentes.

![Captura de ecrã a mostrar a janela da caixa de diálogo de importação de CSV.](media/desktop-connect-csv/connect-to-csv_3.png)

Quando estiver satisfeito com as seleções, pode selecionar **Carregar** para importar o ficheiro para o Power BI Desktop, ou pode selecionar **Editar** para abrir o **Editor de Consultas** e formatar ou transformar os dados antes de os importar.

Após carregar os dados para o Power BI Desktop, verá a tabela e respetivas colunas (que são apresentadas como Campos no Power BI Desktop) no painel **Campos**, no lado direito da vista de Relatório no Power BI Desktop.

![Captura de ecrã da janela Power BI Desktop, a mostrar o painel Campos.](media/desktop-connect-csv/connect-to-csv_4.png)

É tudo o que precisa de fazer. Agora, os dados do seu ficheiro CSV estão no Power BI Desktop.

Pode utilizar esses dados no Power BI Desktop para criar visuais, relatórios ou interagir com outros dados aos quais se possa querer ligar e importar, como livros do Excel, bases de dados ou outra origem de dados.

> [!IMPORTANT]
> Quando importa um ficheiro CSV, o Power BI Desktop gera um campo *colunas=x* (em que *x* representa o número de colunas no ficheiro CSV durante a importação inicial) como um passo no Editor do Power Query. Se adicionar mais colunas posteriormente e a origem de dados estiver definida para ser atualizada, as colunas para além da contagem de *x* colunas iniciais não serão atualizadas. 


## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a livros do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
