---
title: Afixar um mosaico num dashboard do Power BI a partir do Excel
description: "Afixe um mosaico a um dashboard do Power BI a partir do Excel no OneDrive para Empresas. Afixar intervalos, gráficos e tabelas"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: l8JoB7w0zJA
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 855ecbe74fa4bf4ab1b1f81f22f2bab278adddb9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-excel"></a>Afixar um mosaico num dashboard do Power BI a partir do Excel
Para poder afixar um mosaico a partir do livro do Excel, primeiro terá de ligar esse livro ao serviço Power BI (app.powerbi.com). Ligar um livro coloca, essencialmente, uma versão só de leitura ligada desse livro no serviço Power BI e permite-lhe afixar intervalos a dahboards. Pode até afixar uma folha de cálculo inteira a um dashboard.  
Se um livro tiver sido partilhado consigo, terá a capacidade de ver os mosaicos afixados pelo proprietário, mas não poderá criar os mosaicos do dashboard. 

Para obter informações aprofundadas sobre como o Excel e o Power BI funcionam em conjunto, veja [Obter dados de ficheiros de livro do Excel](http://go.microsoft.com/fwlink/?LinkID=521962).

Veja o Will a demonstrar várias formas de importar dados de livros do Excel e a ligar a livros do Excel.

<iframe width="560" height="315" src="https://www.youtube.com/embed/l8JoB7w0zJA" frameborder="0" allowfullscreen></iframe>

## <a name="connect-your-excel-workbook-from-onedrive-for-business-to-power-bi"></a>Ligar o seu livro do Excel ao Power BI partir do OneDrive para Empresas
Quando escolhe **Ligar**, o seu livro irá aparecer no Power BI, tal como apareceria no Excel Online. Mas, ao contrário do Excel Online, terá algumas funcionalidades fantásticas para ajudá-lo a afixar elementos das suas folhas de cálculo diretamente aos dashboards.

Não é possível o livro no Power BI. Mas se precisar de fazer algumas alterações, pode selecionar o ícone de lápis no separador **Livros** da sua área de trabalho e, em seguida, optar por editar o livro no Excel Online ou abri-lo no Excel no seu computador. Todas as alterações feitas são guardadas no livro no OneDrive.

1. Carregue o seu livro para o OneDrive para Empresas.
2. No Power BI, [ligue a esse livro](service-excel-workbook-files.md).
3. No Power BI, o livro é adicionado ao separador **Livros** da sua área de trabalho.  O ícone ![](media/service-dashboard-pin-tile-from-excel/pbi_workbookicon.png) indica que se trata de um livro do Excel e um asterisco amarelo indica que é novo.
   
    As alterações feitas ao livro no Power BI não são guardadas e não afetam o livro original no OneDrive para Empresas. Se ordenar, filtrar ou alterar os valores no Power BI, essas alterações não poderão ser guardadas ou afixadas. Para atualizar o livro, selecione o ícone de lápis para abri-lo no Excel Online. As alterações ao livro no Excel Online podem demorar alguns minutos a serem atualizadas nos mosaicos.     
   
   ![](media/service-dashboard-pin-tile-from-excel/power-bi-workbooks.png)
4. Abra o livro no Power BI, selecionando o nome do livro.
   
   ![](media/service-dashboard-pin-tile-from-excel/power-bi-opened.png)

## <a name="pin-a-range-of-cells-to-a-dashboard"></a>Afixar um intervalo de células a um dashboard
Uma forma de adicionar um novo [mosaico do dashboard](service-dashboard-tiles.md) é a partir de um livro do Excel no Power BI. Os intervalos podem ser afixados a partir de livros do Excel que foram guardados no OneDrive para Empresas ou noutra biblioteca de documentos partilhada pelo grupo. Os intervalos podem conter dados, tabelas, gráficos, Tabelas Dinâmicas, Gráficos Dinâmicos e outras partes do Excel.

1. Realce as células que pretende afixar a um dashboard.
   
    ![](media/service-dashboard-pin-tile-from-excel/pbi_selectrange.png)
2. Selecione o ícone de pino ![](media/service-dashboard-pin-tile-from-excel/pbi_pintile_small.png). 
3. Afixe o mosaico a um dashboard existente ou a um novo dashboard. 
   
   * Dashboard existente: selecione o nome do dashboard na lista pendente.
   * Novo dashboard: escreva o nome do novo dashboard.
   
   ![](media/service-dashboard-pin-tile-from-excel/pbi_dashdialog1.png)
4. Selecione **Afixar**. Uma mensagem de Êxito (perto do canto superior direito) informa que o intervalo foi adicionado, como um mosaico, ao dashboard. 
   
    ![](media/service-dashboard-pin-tile-from-excel/power-bi-go-to-dashboard.png)
5. Selecione **Ir para o dashboard**. A partir daqui, pode [mudar o nome, redimensionar, ligar e mover](service-dashboard-edit-tile.md) a visualização afixada. Por predefinição, selecionar o mosaico afixado abre o livro no Power BI.

## <a name="pin-an-entire-table-or-pivot-chart-to-a-dashboard"></a>Afixar um gráfico dinâmico ou toda uma tabela a um dashboard
Siga os passos acima, mas em vez de selecionar um intervalo de células, selecione uma tabela inteira ou uma tabela dinâmica.

Para afixar uma tabela, selecione o intervalo inteiro da tabela e certifique-se de que inclui os cabeçalhos.  Para afixar uma tabela dinâmica, certifique-se de que inclui todas as partes visíveis da tabela dinâmica, incluindo os filtros, caso sejam utilizados.

 ![](media/service-dashboard-pin-tile-from-excel/pbi_selecttable.png)

Um mosaico criado a partir de uma tabela ou de uma tabela dinâmica irá mostrar a tabela inteira.  Se adicionar/remover/filtrar linhas ou colunas no livro original, também serão adicionadas/removidas/filtradas no mosaico.

## <a name="view-the-workbook-linked-to-the-tile"></a>Ver o livro ligado ao mosaico
Selecionar um mosaico do livro abre o livro ligado no Power BI. Como o ficheiro de livro está localizado no OneDrive para Empresas do proprietário, a visualização do livro exige que tenha permissões de Leitura para o livro. Se não tiver permissão, receberá uma mensagem de erro.  

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
Funcionalidades não suportadas: o Power BI utiliza os Serviços do Excel para obter os mosaicos do livro. Por isso, como algumas das funcionalidades do Excel não são suportadas na API REST dos Serviços do Excel, não serão vistas nos mosaicos no Power BI. Por exemplo: gráficos Sparkline, formatação condicional de conjunto de ícones e segmentação de dados de tempo. Para obter uma lista completa das funcionalidades não suportadas, veja [Funcionalidades Não Suportadas na API REST dos Serviços do Excel](http://msdn.microsoft.com/library/office/ff394477.aspx)

## <a name="next-steps"></a>Próximos passos
[Partilhar um dashboard que contém ligações para um livro do Excel](service-share-dashboard-that-links-to-excel-onedrive.md)

[Obter dados de livros do Excel](service-excel-workbook-files.md)

[Dashboards no Power BI](service-dashboards.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

