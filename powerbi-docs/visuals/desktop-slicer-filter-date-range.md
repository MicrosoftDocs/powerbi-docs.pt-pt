---
title: Utilizar uma segmentação ou filtro de data relativa no Power BI
description: Saiba como utilizar uma segmentação de dados ou um filtro para restringir intervalos de datas relativas no Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: f63a56ea350d089b82eb7a18470e1bcc439d1151
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866524"
---
# <a name="creating-a-relative-date-slicer-and-filter-in-power-bi"></a>Criar uma segmentação e filtro de data relativa no Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Com a **segmentação de data relativa** ou o **filtro de data relativa**, pode aplicar filtros baseados no tempo a qualquer coluna de datas no seu modelo de dados. Por exemplo, pode utilizar a **segmentação de data relativa** para mostrar apenas dados de vendas ocorridas nos últimos 30 dias (ou mês, meses de calendário, etc.). Quando atualizar os dados, o período de tempo relativo aplica automaticamente a restrição de data relativa adequada.

![Captura de ecrã a mostrar um relatório com uma seta a apontar para a segmentação de data relativa.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

Para partilhar o seu relatório com outro utilizador do Power BI, é necessário que ambos tenham licenças individuais do Power BI Pro ou que o relatório seja guardado numa capacidade Premium.

## <a name="create-the-relative-date-range-slicer"></a>Criar a segmentação de intervalo de datas relativas

Pode utilizar a segmentação de data relativa tal como qualquer outra segmentação de dados. Crie um elemento visual de **segmentação de dados** para o seu relatório e, em seguida, selecione um valor de data para o valor **Campo**. Na imagem seguinte, selecionámos o campo *DataDaEncomenda*.

![Captura de ecrã a mostrar o painel Visualizações com setas a apontar para o ícone de elemento visual da segmentação de dados e para o grupo Campo.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Selecione a segmentação de dados na sua tela e, em seguida, o menu pendente no canto superior direito do elemento visual da segmentação de dados. Se o elemento visual tiver os dados relativos à data, o menu apresentará a opção **Relativo**.

![Captura de ecrã a mostrar o elemento visual da segmentação de dados com um realce à volta do menu pendente e uma seta a apontar para a opção Relativo.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

Para a segmentação de data relativa, selecione *Relativo*.

Em seguida, pode selecionar as definições.

Na primeira definição, na *segmentação de data relativa*, tem as seguintes opções:

![Captura de ecrã a mostrar as opções de configuração de Relativo com a primeira definição destacada.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Último

* Seguinte

* Este

A segunda definição (intermédia) na *segmentação de data relativa* permite introduzir um número para definir o intervalo de datas relativas.

![Captura de ecrã a mostrar as opções de configuração de Relativo com a segunda definição destacada.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04a.png)

A terceira definição permite escolher a medida de data. Tem as seguinte opções:

![Captura de ecrã a mostrar as opções de configuração de Relativos com a terceira definição destacada.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-05.png)

* Dias

* Semanas

* Semanas (Calendário)

* Meses

* Meses (Calendário)

* Anos

* Anos (Calendário)

Nessa lista, se selecionar **Meses** e introduzir *2* na definição intermédia, eis o que ocorre:

* se hoje for dia 20 de julho

* os dados incluídos nos elementos visuais restringidos pela segmentação irão incluir os dados dos dois meses anteriores

* a partir do dia 21 de maio até dia 20 de julho (hoje)

Em comparação, se selecionar *Meses (Calendário)* , os elementos visuais restringidos mostram os dados de 1 de maio até 30 de junho (os últimos dois meses de calendário completos).

## <a name="create-the-relative-date-range-filter"></a>Criar o filtro de intervalo de datas relativas

Também pode criar um filtro de intervalo de datas relativas para a página de relatório ou todo o relatório. Para fazê-lo, arraste o campo da data para o grupo **Filtros de nível de página** ou para o grupo **Filtros de nível de relatório** no painel **Campo**:

![Captura de ecrã a mostrar o campo DataDaEncomenda a ser arrastado para o grupo de filtros de nível de página.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

Lá pode alterar o intervalo de datas relativas. É semelhante à forma de personalizar a **segmentação de data relativa**. Selecione **Filtragem de data relativa** no menu pendente **Tipo de Filtro**.

![Captura de ecrã a mostrar o Tipo de Filtro pendente, bem como o ponteiro do rato na filtragem de Data Relativa.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

Após selecionar **Filtragem de data relativa**, verá três secções para alterar, incluindo uma caixa numérica intermédia, tal qual a segmentação de dados.

![Captura de ecrã a mostrar os Filtros de nível de relatório com setas a apontar para a opção Mostrar itens.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Limitações e considerações

As seguintes limitações e considerações aplicam-se atualmente ao filtro e **segmentação de intervalo de datas relativas**.

* Os modelos de dados do **Power BI** não incluem informações sobre o fuso horário. Os modelos podem armazenar horas, mas não existe nenhuma indicação do fuso horário em que estão.

* A segmentação de dados e o filtro estão sempre baseados na hora UTC. Se configurar um filtro num relatório e o enviar para um colega num fuso horário diferente, ambos verão os mesmos dados. A menos que estejam no fuso horário UTC, ambos devem ter em conta a diferença horária que experienciam.

* Pode converter dados capturados de um fuso horário local em UTC com o **Editor do Power Query**.

## <a name="next-steps"></a>Próximos passos

- [Utilizar uma segmentação e filtro de data relativa no Power BI](desktop-slicer-filter-date-range.md)
- [Segmentação de Dados no Power BI](power-bi-visualization-slicers.md)
