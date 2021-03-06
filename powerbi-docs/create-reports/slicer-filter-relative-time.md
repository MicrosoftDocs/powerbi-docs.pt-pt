---
title: Utilizar uma segmentação ou filtro de hora relativa no Power BI
description: Saiba como utilizar uma segmentação de dados ou um filtro para restringir intervalos de tempo relativos no Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 4b12760584df2471bf02029be0fb428d1ab21e4c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387557"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Utilizar uma segmentação e filtro de hora relativa no Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Com cenários de atualização rápida emergentes, a capacidade de filtrar para um período de tempo mais pequeno pode ser útil. Com a segmentação de hora relativa ou o filtro de hora relativa, pode aplicar filtros baseados na hora a qualquer coluna de data ou hora no seu modelo de dados. Por exemplo, pode utilizar a segmentação de dados de hora relativa para mostrar apenas visualizações de vídeo no último minuto ou hora. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Captura de ecrã do exemplo de hora relativa.":::

Não é preciso utilizar a funcionalidade em conjunto com a funcionalidade de [atualização automática de página](../create-reports/desktop-automatic-page-refresh.md). No entanto, muitos cenários de hora relativa combinam bem com a funcionalidade de atualização automática de página.  

> [!NOTE]
> Quando aplica um filtro ou segmentação de hora relativa ao nível de página ou relatório, todos os elementos visuais nessa página ou relatório são filtrados para o mesmo intervalo de tempo, através de uma hora de *âncora* partilhada. Como os elementos visuais podem ter tempos de execução ligeiramente diferentes, esta hora de âncora partilhada garante que os elementos visuais são sincronizados na sua página ou no seu relatório. Leia mais sobre a [hora de âncora](#understanding-anchor-time) neste artigo.

## <a name="create-a-relative-time-slicer-or-filter"></a>Criar uma segmentação ou filtro de hora relativa

Após ativar a funcionalidade, pode arrastar e largar o campo de data ou hora para a área de campo de uma segmentação ou para a zona de largar no painel Filtros. 

### <a name="create-a-slicer"></a>Criar uma segmentação

1. Arraste um campo de data ou hora para a tela.

2. Selecione o tipo de visualização **Segmentação de Dados**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Captura de ecrã da criação de uma segmentação de hora.":::

### <a name="create-a-filter"></a>Criar um filtro
 
- Arraste um campo de data ou hora para o painel Filtros, para **este elemento visual**, **esta página** ou **todas as páginas**.

### <a name="set-relative-time"></a>Definir a hora relativa 

Em seguida, altere o tipo de filtro para **Hora Relativa**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Captura de ecrã da alteração para a hora relativa.":::
 
Eis o aspeto uma segmentação:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Captura de ecrã da hora relativa numa segmentação.":::

Eis o aspeto num cartão de filtros: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Captura de ecrã da hora relativa num filtro.":::
 
Com este novo tipo de filtro, pode filtrar com base em **Último**, **Próximo** ou **Este período de tempo**: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Captura de ecrã da escolha de Último, Próximo ou Este período de tempo.":::
 
Especifique o período de tempo com um número inteiro e uma unidade temporal: **Minutos** ou **Horas**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Captura de ecrã da escolha de minutos ou horas.":::

Se precisar de poupar espaço na tela, também pode criar o filtro de hora relativa como cartão de filtro no painel Filtros.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Captura de ecrã da definição da hora relativa num filtro.":::
 
## <a name="understanding-anchor-time"></a>Compreender a hora de âncora

Quando um filtro for aplicado ao nível de página ou relatório, todos os elementos visuais nessa página ou relatório serão sincronizados para o mesmo intervalo de tempo. Todas estas consultas são emitidas relativamente a uma hora, chamada *hora de âncora*. A hora de âncora atualiza automaticamente quando ocorrem as seguintes condições:

- Carregamento da página inicial.
- Atualização manual.
- Atualização de página automática ou deteção de alteração.
- Uma alteração ao modelo.

### <a name="anchor-time-exceptions"></a>Exceções à hora de âncora

- Filtrar a hora relativa com o elemento visual de Perguntas e Respostas não é relativo a esta hora de âncora, até converter o elemento visual de Perguntas e Respostas num elemento visual padrão. No entanto, os restantes elementos visuais de IA, como influenciadores-chave e a árvore de decomposição, são sincronizados com a hora de âncora. 
- Além disso, os filtros ou segmentações de data relativa não são relativos à hora de âncora, salvo na presença de filtros de hora relativa. Se um filtro de data relativa e um filtro de hora relativa estiverem na mesma página, o filtro de data relativa respeitará a hora de âncora.

## <a name="limitations-and-considerations"></a>Limitações e considerações

As seguintes limitações e considerações aplicam-se atualmente ao filtro e segmentação de hora relativa.

- **Considerações sobre o fuso horário**: Os modelos de dados do Power BI não incluem informações sobre o fuso horário. Os modelos podem armazenar horas, mas não existe nenhuma indicação do fuso horário em que estão. A segmentação de dados e o filtro estão sempre baseados na hora UTC. Se configurar um filtro num relatório e o enviar para um colega num fuso horário diferente, ambos verão os mesmos dados. A menos que esteja no fuso horário UTC, assim como o seu colega, ambos devem ter em conta a possível diferença horária. Utilize o Editor de Consultas para converter dados capturados de um fuso horário local em UTC.
- Este novo tipo de filtro é suportado no Power BI Desktop, no serviço Power BI, no Power BI Embedded e nas aplicações móveis do Power BI. No entanto, não é suportado para Publicar na Web.

- **Colocação de Consultas em Cache**: Utilizamos a cache do cliente. Imagine que especifica “último minuto” e, em seguida, “últimos 5 minutos” e, depois, novamente “último minuto”. Neste ponto, vê os mesmos resultados que na primeira execução, a menos que atualize a página ou a página seja atualizada automaticamente.

## <a name="next-steps"></a>Próximos passos

- [Utilizar uma segmentação e filtro de data relativa no Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Segmentação de Dados no Power BI](../visuals/power-bi-visualization-slicers.md)
