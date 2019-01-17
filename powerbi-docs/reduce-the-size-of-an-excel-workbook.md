---
title: Reduza o tamanho de um livro de trabalho do Excel para vê-lo no Power BI
description: Reduza o tamanho de um livro de trabalho do Excel para vê-lo no Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/10/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 111e38fd37bcdfa2a72986bb08a37d89345bbe69
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282270"
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>Reduza o tamanho de um livro de trabalho do Excel para vê-lo no Power BI
Pode carregar qualquer livro do Excel inferior a 1 GB para o Power BI. Um livro de trabalho do Excel pode ter duas partes: um modelo de dados e o restante do relatório — conteúdo da folha de cálculo principal. Se o relatório corresponder aos seguintes limites de tamanho, pode guardá-lo no **OneDrive para Empresas**, ligando-o do Power BI e visualizando-o no Excel Online:

* O livro, como todo, pode ter até 1 GB.
* O conteúdo da folha de cálculo principal pode ter até 30 MB.

## <a name="what-makes-core-worksheet-contents-larger-than-30-mb"></a>O que torna o conteúdo da folha de cálculo principal maior do que 30 MB
Veja a seguir alguns elementos que podem tornar o conteúdo da folha de cálculo principal maior do que 30 MB:

* Imagens.
* Células com sombreado. [Remova um formato de sombra de célula](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e).
* Folhas de cálculo coloridas. [Remova um fundo da folha](https://support.office.com/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8).
* Caixas de texto.
* Clip-art.

Considere remover esses elementos, se possível. 

Se o relatório tiver um modelo de dados, terá algumas outras opções: 

* Remover dados de folhas de cálculo do Excel e armazená-lo no modelo de dados. Consulte "Remover dados de folhas de cálculo" abaixo para obter detalhes. 
* [Crie um Modelo de Dados com eficiência de memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70) para reduzir o tamanho geral do relatório.

Para fazer essas alterações, precisa de editar o livro de trabalho no Excel.

Leia mais sobre [limites de tamanho do ficheiro para livros de trabalho do Excel no SharePoint Online](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e).

## <a name="remove-data-from-worksheets"></a>Remover dados das folhas de cálculo
Se importar dados para o Excel da aba Power Query ou os dados do Excel, o livro de trabalho pode ter os mesmos dados numa tabela do Excel e no modelo de dados. As tabelas grandes nas folhas de cálculo do Excel podem tornar o conteúdo da folha de cálculo principal maior do que 30 MB. Remover a tabela no Excel e manter os dados no modelo de dados podem reduzir significativamente o conteúdo da folha de cálculo principal do relatório. 

Quando importar dados para o Excel, siga estas dicas:

* **No Power Query**: limpe a caixa **Carregar para a folha de cálculo**.
  
  Os dados são importados apenas no modelo de dados, sem dados nas folhas de cálculo do Excel.
* **No separador Dados do Excel**, se tiver selecionado anteriormente **Tabela** no assistente de importação: aceda a **Ligações Existentes** \> clique na ligação \> **Apenas criar ligação**. Elimine a tabela ou tabelas criadas durante a importação inicial original.
* **Da aba de Dados do Excel**: não verificar a **tabela** na caixa **Importar dados**.

## <a name="workbook-size-optimizer"></a>Otimizador de tamanho do Livro de trabalho
Se a sua pasta de trabalho contiver um modelo de dados,pode executar o otimizador de tamanho do livro de trabalho para reduzir o tamanho do livro de trabalho. [Baixe o Otimizador de Tamanho do Livro de Trabalho](https://www.microsoft.com/download/details.aspx?id=38793).

## <a name="related-info"></a>Informações relacionadas
[Criar um Modelo de dados eficiente em memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[Utilizar as ligações do OneDrive para Empresas no Power BI Desktop](desktop-use-onedrive-business-links.md)

