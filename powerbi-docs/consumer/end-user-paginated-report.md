---
title: Relatórios paginados no serviço Power BI
description: Documentação a descrever os relatórios paginados e como visualizá-los no serviço Power BI
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 0ab2ececd4ede03a10094be53a2c08617463cc53
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/11/2020
ms.locfileid: "79113126"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Relatórios paginados no serviço Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Aprendeu sobre os [relatórios do Power BI](end-user-reports.md) e esses são os tipos de relatórios que provavelmente irá encontrar. No entanto, existe outro tipo de relatório chamado *relatório paginado*. Os *designers* de relatórios podem partilhar relatórios paginados consigo numa área de trabalho numa capacidade Premium ou numa aplicação a partir dessa área de trabalho. 

## <a name="what-is-a-paginated-report"></a>O que é um relatório paginado?

Estes relatórios são designados *paginados* porque são formatados para se ajustarem a uma página impressa. Uma vantagem é que apresentam todos os dados numa tabela, mesmo que a tabela ocupe múltiplas páginas. Às vezes, os relatórios paginados são chamados "imagem perfeita", uma vez que os *designers* de relatórios podem controlar o esquema de página do relatório com exatidão.

Quando os *designers* de relatórios criam um relatório paginado, estão na realidade a criar uma *definição do relatório*. ou seja, não contém os dados, especifica onde obter os dados, quais os dados a obter e como apresentar os dados. Quando executar o relatório, o processador do relatório utiliza a definição do relatório, obtém os dados e combina-os com o esquema de relatório para gerar o relatório. Por vezes, o relatório apresenta dados predefinidos. Outras vezes, tem de introduzir parâmetros para que o relatório possa apresentar dados. 

   ![Parâmetros do relatório](./media/end-user-paginated-report/power-bi-report-parameters.png)

Normalmente, a interação limita-se a isso: definir os parâmetros. Se for analista de faturação, pode utilizar relatórios paginados para criar ou imprimir faturas. Se for um gestor de vendas, pode utilizar relatórios paginados para ver as encomendas por loja ou vendedor. 

Este relatório paginado simples gera lucro por ano, após selecionar o parâmetro **Year**. 

![Relatório simples de um parâmetro](./media/end-user-paginated-report/power-bi-report-simple.png)

Em comparação com os relatórios paginados, os relatórios do Power BI são muito mais interativos. Os relatórios do Power BI permitem a criação de relatórios ad hoc e suportam muitos outros tipos de elementos visuais, incluindo elementos visuais personalizados.

## <a name="identify-a-paginated-report"></a>Identificar um relatório paginado

Nas listas de conteúdos e na Home Page de destino, os relatórios paginados podem ser identificados pelo ícone ![ícone de relatório paginado](media/end-user-paginated-report/power-bi-report-icon.png).  Um relatório paginado pode ser partilhado consigo diretamente ou como parte de uma [aplicação do Power BI](end-user-apps.md). Se o *designer* de relatórios lhe tiver concedido permissões, poderá partilhar novamente o relatório paginado e subscrever-se, e subscrever outras pessoas.

![lista de relatórios a mostrar diferentes ícones](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>Interagir com um relatório paginado

A forma como interage com um relatório paginado é diferente de outros relatórios. Pode realizar ações como imprimir, marcar, exportar e comentar, mas existe menos interatividade. Geralmente, os relatórios paginados necessitam de dados introduzidos pelo utilizador para preencher a tela de relatórios.  Noutras ocasiões, o relatório apresenta dados predefinidos e pode introduzir parâmetros para ver dados diferentes.

### <a name="print-a-paginated-report"></a>Imprimir um relatório paginado

Os relatórios *paginados* são formatados para se ajustarem a uma página que pode ser impressa. O que vê no browser é o que vê quando imprime. Além disso, se o relatório tiver uma tabela longa, a tabela inteira é impressa, mesmo que tenha múltiplas páginas. 

Os relatórios paginados podem ter muitas páginas. Por exemplo, este relatório tem 563 páginas. Cada página está disposta com exatidão, com uma página por fatura e cabeçalhos e rodapés repetidos. Quando imprimir este relatório, irá obter quebras de página entre faturas.

   ![Página um de um relatório paginado da Tailspin Toys](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Navegar pelo relatório paginado

Neste relatório de nota de venda, existem três parâmetros: Business type, Reseller e Order number. 

![relatório com três parâmetros](./media/end-user-paginated-report/power-bi-parameter.png)

Para alterar as informações a serem apresentadas, introduza novos valores para os três parâmetros e selecione **Ver relatório**. Aqui, selecionámos **Specialty bike shop**, **Alpine Ski House** e o número da encomenda **SO46085**. Selecionar **Ver relatório** atualiza a nossa tela de relatórios com esta nova nota de venda.

![alterar os parâmetros](./media/end-user-paginated-report/power-bi-order.png)

A nova nota de venda é apresentada e utiliza os parâmetros que selecionámos. 

![uma nova nota de venda](./media/end-user-paginated-report/power-bi-new-order.png)

Alguns relatórios paginados têm muitas páginas.  Utilize os controlos da página para navegar no relatório. 

![controlos da página](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>Exportar o relatório paginado
Tem uma variedade de opções para exportar relatórios paginados, incluindo PDF, Word, XML, PowerPoint, Excel e muito mais. Ao exportar, é preservada a maior parte da formatação. Os relatórios paginados exportados para o Excel, Word, PowerPoint, MHTML e PDF, por exemplo, mantêm a formatação perfeita. 

![uma nova nota de venda](./media/end-user-paginated-report/power-bi-exporting.png)

![quatro tipos diferentes de exportação](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Subscrever o relatório paginado
Quando subscreve um relatório paginado, o Power BI envia-lhe um e-mail com o relatório como um anexo. Ao configurar a sua subscrição, pode selecionar com que frequência quer receber os e-mails: diariamente, semanalmente, de hora a hora ou mensalmente. A subscrição inclui um anexo com todo o resultado do relatório, até 25 MB. Exporte o relatório inteiro ou selecione os parâmetros antecipadamente. Escolha entre vários tipos de anexos diferentes, incluindo Excel, PDF, PowerPoint e muito mais.  

![Formatos para subscrever](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

- Um relatório paginado pode aparecer em branco até selecionar parâmetros e selecionar **Ver relatório**.

- Se não tiver relatórios paginados, pode ser porque ninguém partilhou este tipo de relatório consigo. Também pode significar que o administrador do sistema não ativou os relatórios paginados. 

 

## <a name="next-steps"></a>Próximos passos
- [Relatórios do Power BI](end-user-reports.md)
- Mais perguntas? Experimente perguntar à [Comunidade do Power BI](https://community.powerbi.com/).

