---
title: Relatórios paginados do Power BI de exemplo
description: Neste artigo, irá aprender a transferir e utilizar relatórios paginados do Power BI de exemplo.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/28/2021
ms.openlocfilehash: 282700151e605bd3571847b3b75f08e65f948e08
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044356"
---
# <a name="sample-power-bi-paginated-reports"></a>Relatórios paginados do Power BI de exemplo


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

Este artigo fornece informações e ligações para vários relatórios paginados do Power BI de exemplo para transferir e explorar. Demonstram formas típicas de utilizar relatórios paginados.

## <a name="prerequisites"></a>Pré-requisitos

- Pode partilhar estes relatórios online, tal como estão, sem edição. Para fazê-lo, precisa de uma licença do Power BI Pro. Inscreva-se numa [avaliação gratuita de licença do Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).
- Também precisa de acesso a uma área de trabalho do Power BI numa [Capacidade Premium](../admin/service-premium-what-is.md).
- Para editar estes relatórios, tem de [instalar o Power BI Report Builder](https://aka.ms/pbireportbuilder) a partir do Centro de Transferências da Microsoft.
- Está tudo pronto para transferir estes relatórios paginados de exemplo a partir do GitHub. Não precisa de uma conta do GitHub. 

## <a name="download-the-reports"></a>Transferir os relatórios

Para transferir os relatórios com êxito, precisa de transferir o repositório como um ficheiro .zip e, em seguida, extraí-los. Os relatórios paginados são ficheiros .rdl.

1. Abra o [repositório do GitHub Reporting Services](https://github.com/microsoft/Reporting-Services).
1. Selecione a seta no botão verde **Code** (Código) > **Download ZIP** (Transferir ZIP).

    :::image type="content" source="media/paginated-reports-samples/paginated-report-download-zip.png" alt-text="Captura de ecrã a mostrar o repositório do GitHub com os relatórios paginados de exemplo do Power BI.":::
    
1. Abra o ficheiro, selecione **Extrair todos** e selecione uma localização para os ficheiros. Por predefinição, o nome da pasta é **Reporting-Services-master**.
1. Abra a pasta **Reporting-Services-master** e, em seguida, abra a pasta **PaginatedReportSamples**.

    >[!NOTE]
    >Pode eliminar todas as outras pastas na pasta **Reporting-Services-master**. Estas contêm outros exemplos de que não precisa.

1. Selecione um dos ficheiros .rdl para abrir no Power BI Report Builder.
1. Agora, pode [publicar o relatório paginado no serviço Power BI](paginated-reports-save-to-power-bi-service.md).

## <a name="invoice"></a>Fatura

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Captura de ecrã a mostrar a fatura do Relatório paginado do Power BI de exemplo.":::


Este relatório paginado é uma fatura autónoma. O cenário para este relatório é o seguinte: pretende uma fatura imprimível com um aspeto perfeito. Esta tem de mostrar o total de vendas com detalhes que apresentem as descrições, quantidades, descontos e custos dos itens.

Este exemplo destaca caraterísticas particulares para a criação de faturas reais, como:  

- Uma tablix (a região de dados subjacente às tabelas e matrizes). Apresenta conteúdos específicos do utilizador e um tema gerados dinamicamente.
- Uma região de dados retangular colocada em cada linha da tablix do corpo do relatório.
- Itens de relatório, como caixas de texto e linhas.
- Um parâmetro de relatório para selecionar dinamicamente os conteúdos. Os conteúdos mostrados aplicam-se a um assunto específico ao utilizar marcadores de posição de expressão. 

Origem de dados: incluída no ficheiro .rdl

## <a name="labels"></a>Etiquetas

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="Captura de ecrã a mostrar as etiquetas de Relatório paginado.":::

Isto é um relatório paginado autónomo de exemplo. É um relatório de várias colunas perfeitamente dimensionado para ajustar o esquema de impressão do modelo de etiqueta de correio. 

Os relatórios de etiqueta são simples, mas têm algumas caraterísticas particulares para criar uma etiqueta paginada:

- Uma tablix com uma contagem de colunas fixa de três, com espaçamento de coluna definido.
- Uma região de dados retangular que se repete em linhas e colunas na página impressa.
- Um parâmetro de relatório para selecionar o conteúdo a ser mostrado em cada região de dados retangular.

Origem de dados: incluída no .rdl

## <a name="mailing-letter"></a>Carta de correio

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Captura de ecrã a mostrar a carta do Relatório paginado do Power BI de exemplo.":::

Este relatório paginado autónomo de exemplo foi concebido para a criação de cartas de correio reais. O cenário para este relatório é o seguinte: pretende uma carta imprimível com conteúdos dinâmicos e um aspeto perfeito.

Este exemplo tem caraterísticas particulares, como: 

- Uma região de dados retangular é colocada em secções diferentes do corpo do relatório. 
- Imagens para personalizar a carta. 
- Uma região de dados tablix (a região de dados subjacente às tabelas e matrizes). A tablix apresenta conteúdos específicos do utilizador gerados dinamicamente.
- Itens de relatório, como caixas de texto e linhas.
- Um parâmetro de relatório para selecionar dinamicamente os conteúdos. Os conteúdos mostrados aplicam-se a um assunto específico ao utilizar marcadores de posição de expressão. 

Origem de dados: incluída no .rdl

## <a name="transcript"></a>Transcrição

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Captura de ecrã a mostrar a transcrição do Relatório paginado do Power BI de exemplo.":::

O cenário para este relatório é o seguinte: pretende uma transcrição imprimível com um aspeto perfeito. Tem de conter conteúdos dinâmicos com datas e detalhes de descrição do programa para cada estudante.

Este relatório paginado autónomo de exemplo tem caraterísticas particulares, como: 

- Uma região de dados tablix (a região de dados subjacente às tabelas e matrizes). A tablix apresenta conteúdos específicos do utilizador gerados dinamicamente com grupos de linhas aninhadas.
- As regiões de dados retangulares são colocadas em secções diferentes do corpo do relatório.
- Itens de relatório, como caixas de texto e linhas.

Origem de dados: incluída no .rdl

## <a name="sales-performance"></a>Desempenho de Vendas

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="Captura de ecrã a mostrar o Relatório paginado do Power BI de exemplo para Desempenho de Vendas.":::

Country Sales Performance é um relatório paginado autónomo de exemplo. O cenário para este relatório é o seguinte: pretende uma fatura imprimível com um aspeto perfeito para ver o total de vendas e os detalhes. Mostra as seguintes funcionalidades:

- A utilização de um parâmetro para expandir os detalhes na tabela.
- Cabeçalhos e rodapés.
- Itens de relatório, como caixas de texto, linhas e retângulos com marcadores de posição de expressão.
- Barras de dados.
- Linhas de tendência.
- Painéis do medidor.

Origem de dados: incluída no .rdl

## <a name="regional-sales"></a>Regional Sales

:::image type="content" source="media/paginated-reports-samples/paginated-report-regional-sales.png" alt-text="Screenshot da amostra Power BI relatório paginated para vendas regionais.":::

Regional Sales é uma amostra de relatório paginada independente. O cenário para este relatório é que você quer um relatório impresso perfeito para ver o total de vendas vs. quota. Mostra as seguintes funcionalidades:

- A utilização de um parâmetro para mostrar detalhes selecionados na tabela.
- Cabeçalhos e rodapés.
- Itens de relatório, como caixas de texto, linhas e retângulos com marcadores de posição de expressão.
- Painéis do medidor.
- Gráfico de linha colocado dentro da mesa.

Origem de dados: incluída no .rdl

## <a name="organization-expenditures"></a>Despesas da Organização

:::image type="content" source="media/paginated-reports-samples/paginated-report-organization-expenditures.png" alt-text="Screenshot da amostra Power BI relatório paginated para despesas de organização.":::

As despesas da organização são uma amostra de relatório paginado independente. O cenário para este relatório é que você quer um relatório de despesas imprimíveis perfeito para ver a quebra de despesas na sua organização. Mostra as seguintes funcionalidades:

- Cabeçalhos e rodapés.
- Itens de relatório, como caixas de texto, linhas e retângulos com marcadores de posição de expressão.
- Gráficos como mapa de árvores e explosão de sol.

Origem de dados: incluída no .rdl
  
## <a name="next-steps"></a>Próximas etapas

[Ver um relatório paginado no serviço Power BI](../consumer/paginated-reports-view-power-bi-service.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
