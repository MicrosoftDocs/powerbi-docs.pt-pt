---
title: "Reduza o tamanho de um livro de trabalho do Excel para vê-lo no Power BI"
description: "Reduza o tamanho de um livro de trabalho do Excel para vê-lo no Power BI"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 2d6d55b8b93ce23528490a3e72616806ebc09beb
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>Reduza o tamanho de um livro de trabalho do Excel para vê-lo no Power BI
Pode carregar qualquer livro do Excel inferior a 1 GB para o Power BI. Um livro de trabalho do Excel pode ter duas partes: um modelo de dados e o restante do relatório — conteúdo da folha de cálculo principal. Se o relatório corresponder aos seguintes limites de tamanho, pode guardá-lo no **OneDrive para Empresas**, ligando-o do Power BI e visualizando-o no Excel Online:

* O livro, como todo, pode ter até 1 GB.
* O conteúdo da folha de cálculo principal pode ser de até 10 MB.

## <a name="what-makes-core-worksheet-contents-larger-than-10-mb"></a>O que torna o conteúdo da folha de cálculo de núcleo maior do que 10 MB
Aqui estão alguns elementos que podem tornar os núcleos de conteúdos da folha de cálculo maiores que 10 MB:

* Imagens.
* Células com sombreado. [Remova um formato de sombra de célula](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e).
* Folhas de cálculo coloridas. [Remova um fundo da folha](https://support.office.com/en-US/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8).
* Caixas de texto.
* Clip-art.

Considere remover esses elementos, se possível. 

Se o relatório tiver um modelo de dados, terá algumas outras opções: 

* Remover dados de folhas de cálculo do Excel e armazená-lo no modelo de dados. Consulte "Remover dados de folhas de cálculo" abaixo para obter detalhes. 
* [Crie um Modelo de Dados com eficiência de memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70) para reduzir o tamanho geral do relatório.

Para fazer essas alterações, precisa de editar o livro de trabalho no Excel.

Leia mais sobre [limites de tamanho do ficheiro para livros de trabalho do Excel no SharePoint Online](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e).

## <a name="remove-data-from-worksheets"></a>Remover dados das folhas de cálculo
Se importar dados para o Excel da aba Power Query ou os dados do Excel, o livro de trabalho pode ter os mesmos dados numa tabela do Excel e no modelo de dados. As tabelas grandes nas folhas de cálculo do Excel podem tornar o conteúdo da folha de cálculo de núcleo maior do que 10 MB. Remover a tabela no Excel e manter os dados no modelo de dados podem reduzir significativamente o conteúdo da folha de cálculo principal do relatório. 

Quando importar dados para o Excel, siga estas dicas:

* **Power Query**: limpar a caixa **Carregar para a folha de cálculo** .
  
  Os dados são importados apenas no modelo de dados, sem dados nas folhas de cálculo do Excel.
* **No separador Dados do Excel**, caso o tenha marcado anteriormente a **Tabela** no assistente de importação: vá para **Ligações Existentes** \> clique na ligação \> **Apenas criar ligação**. Elimine a tabela ou tabelas criadas durante a importação inicial original.
* **Da aba de Dados do Excel**: não verificar a **tabela** na caixa **Importar dados**.

## <a name="workbook-size-optimizer"></a>Otimizador de tamanho do Livro de trabalho
Se a sua pasta de trabalho contiver um modelo de dados,pode executar o otimizador de tamanho do livro de trabalho para reduzir o tamanho do livro de trabalho. [Baixe o Otimizador de Tamanho do Livro de Trabalho](https://www.microsoft.com/en-us/download/details.aspx?id=38793).

## <a name="related-info"></a>Informações relacionadas
[Criar um Modelo de dados eficiente em memória](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[Utilizar as ligações do OneDrive para Empresas no Power BI Desktop](desktop-use-onedrive-business-links.md)

