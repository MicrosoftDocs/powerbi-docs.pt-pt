---
title: Adicionar hiperligações (URLs) a uma tabela
description: Este tópico ensina a adicionar hiperligações (URLs) a uma tabela. Pode utilizar o Power BI Desktop para adicionar hiperligações (URLs) a uma tabela ou matriz. Em seguida, no Power BI Desktop ou no serviço Power BI pode adicionar essas hiperligações às suas matrizes e tabelas de relatório.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: e8cad7035e752e5e344d78a22ad5fd8ea0a072ad
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2020
ms.locfileid: "73874504"
---
# <a name="add-hyperlinks-urls-to-a-table"></a>Adicionar hiperligações (URLs) a uma tabela
Este tópico ensina a adicionar hiperligações (URLs) a uma tabela. Pode utilizar o Power BI Desktop para adicionar hiperligações (URLs) a uma tabela ou matriz. Em seguida, no Power BI Desktop ou no serviço Power BI pode adicionar essas hiperligações às suas matrizes e tabelas de relatório. 

![Tabela com hiperligações](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> [!NOTE]
> Pode criar hiperligações em [mosaicos nos dashboards](service-dashboard-edit-tile.md) e [caixas de texto nos dashboards](service-dashboard-add-widget.md) no momento no serviço Power BI. Pode criar hiperligações em [caixas de texto em relatórios](service-add-hyperlink-to-text-box.md) no momento no serviço Power BI e no Power BI Desktop.
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Criar uma hiperligação numa tabela ou matriz com o Power BI Desktop
Pode criar hiperligações em tabelas e matrizes no Power BI Desktop, mas não no serviço Power BI. Também pode criar hiperligações no Power Pivot no Excel antes de importar o livro para o Power BI. Ambos os métodos são descritos abaixo.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Criar uma hiperligação de tabela ou matriz no Power BI Desktop
O procedimento para adicionar uma hiperligação depende de os dados terem sido importados ou de ter ligado aos mesmos com o DirectQuery. Ambos os cenários são descritos abaixo.

### <a name="for-data-imported-into-power-bi"></a>Para dados importados para o Power BI
1. Se a hiperligação ainda não existir como um campo no conjunto de dados, utilize o Power BI Desktop para a adicionar como uma [coluna personalizada](desktop-common-query-tasks.md).
2. Na vista de Dados, selecione a coluna e, no separador **Modelação**, escolha a lista pendente de **Categoria de Dados**.
   
    ![Lista pendente de categorias de dados](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Selecione **URL da Web**.
4. Mude para a vista de Relatório e crie uma tabela ou matriz com o campo categorizado como um URL da Web. As hiperligações estarão a azul e a sublinhado.

    ![Ligações azuis e sublinhadas](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)

    > [!NOTE]
    > Os URLs têm de começar com determinados prefixos. Veja [Considerações e resolução de problemas](#considerations-and-troubleshooting) para conhecer a lista completa.
    >
   
1. Se não quiser apresentar um URL longo numa tabela, pode apresentar, um ícone de hiperligação  ![Ícone de hiperligação](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) como alternativa. Tenha em atenção que não é possível apresentar ícones em matrizes.
   
    Selecione o gráfico para ativá-lo.

    Selecionar o ícone Formatar ![Ícone de rolo de pintura](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) para abrir o separador Formatação.

    Expanda **Valores**, localize o **ícone de URL** e defina-o como **Ativo**.

    ![Ativar o ícone de URL](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Opcional) [Publique o relatório do Power BI Desktop no serviço Power BI](/learn/modules/publish-share-power-bi/2-publish-reports) e abra o relatório no serviço Power BI. As hiperligações também funcionarão aí.

### <a name="for-data-connected-with-directquery"></a>Para dados ligados com DirectQuery
Não pode criar uma nova coluna no modo DirectQuery.  Porém, pode transformá-los em hiperligações se os dados já contiverem URLs.

1. Na vista de Relatório, crie uma tabela com um campo que contenha URLs.
2. Selecione a coluna e, no separador **Modelação**, escolha a lista pendente de **Categoria de Dados**.
3. Selecione **URL da Web**. As hiperligações estarão a azul e a sublinhado.
4. (Opcional) [Publique o relatório do Power BI Desktop no serviço Power BI](/learn/modules/publish-share-power-bi/2-publish-reports) e abra o relatório no serviço Power BI. As hiperligações também funcionarão aí.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Criar uma hiperligação de tabela ou matriz no Excel Power Pivot
Outra forma de adicionar hiperligações às tabelas e matrizes do Power BI é criar as hiperligações no conjunto de dados antes de importar/ligar a esse conjunto de dados a partir do Power BI. Este exemplo utiliza um livro do Excel.

1. Abra o livro no Excel.
2. Selecione o separador **PowerPivot** e, em seguida, escolha **Gerir**.
   
   ![Abrir o PowerPivot no Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Quando o PowerPivot abrir, selecione o separador **Avançadas**.
   
   ![Separador Avançadas do PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Coloque o cursor na coluna que contém os URLs que deseja transformar em hiperligações nas tabelas do Power BI.
   
   > [!NOTE]
   > Os URLs têm de começar com determinados prefixos. Veja [Considerações e resolução de problemas](#considerations-and-troubleshooting) para conhecer a lista completa.
   > 
   
5. No grupo **Propriedades de Relatório**, selecione na lista pendente **Categoria de Dados** e escolha **URL da Web**. 
   
   ![Lista pendente de categorias de dados no Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. No serviço Power BI ou Power BI Desktop, ligue-se a este livro ou importe-o.
7. Crie uma visualização de tabela que contenha o campo URL.
   
   ![Criar uma tabela no Power BI com o campo URL](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

Os URLs têm de começar por um dos seguintes:
- http
- https
- -mailto
- file
- ftp
- news
- telnet

P: Posso utilizar um URL personalizado como uma hiperligação numa tabela ou numa matriz?    
R: Não. Pode utilizar um ícone de ligação. Se necessitar de texto personalizado para as hiperligações e se a sua lista de URLs for pequena, considere utilizar antes uma caixa de texto.


## <a name="next-steps"></a>Próximos passos
[Visualizações em relatórios do Power BI](visuals/power-bi-report-visualizations.md)

[Conceitos básicos para designers no serviço Power BI](service-basic-concepts.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

