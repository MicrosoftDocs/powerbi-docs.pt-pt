---
title: Extending visuals with report page tooltips (Desenvolver elementos visuais com descrições de páginas de relatório)
description: Orientação para trabalhar com descrições de páginas de relatório.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: b7256a04ccdca107ef0cd8e24af8b3170a3d68cc
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74834730"
---
# <a name="extending-visuals-with-report-page-tooltips"></a>Extending visuals with report page tooltips (Desenvolver elementos visuais com descrições de páginas de relatório)

O presente artigo destina-se a si, na qualidade de autor de relatório que cria relatórios do Power BI. Fornece sugestões e recomendações para a criação de [descrições de páginas de relatório](../desktop-tooltips.md).

## <a name="suggestions"></a>Sugestões

As descrições de páginas de relatório podem otimizar a experiência para os utilizadores do seu relatório. As descrições de páginas permitem aos utilizadores do seu relatório obter informações mais aprofundadas de forma rápida e eficaz a partir de um elemento visual. Podem ser associadas a diferentes objetos do relatório:

- **Elemento visuais:** Numa base elemento visual a elemento visual, pode configurar quais os elementos visuais que irão revelar a sua descrição de página. Em cada elemento visual, é possível fazer com que o elemento visual não revele qualquer descrição, por predefinição, nas descrições do elemento visual (configuradas no painel dos campos do elemento visual) ou utilizar uma descrição de página específica.
- **Cabeçalhos de elementos visuais:** Pode configurar elementos visuais específicos para apresentarem uma descrição de página. Os utilizadores do seu relatório podem revelar a descrição da página ao pairarem o cursor sobre o ícone do cabeçalho do elemento visual. Certifique-se de que informa os seus utilizadores sobre este ícone.

> [!NOTE]
> Um elemento visual de relatório só pode revelar uma descrição de página quando os filtros de página de descrição são compatíveis com o design do elemento visual. Por exemplo, um elemento visual que agrupa por _produto_ é compatível com uma página de descrições que filtra por _produto_.
>
> As descrições de página não suportam interatividade. Se pretende que os utilizadores do seu relatório possam interagir, crie antes uma [página de pormenorização](../desktop-drillthrough.md).
>
> Os elementos visuais personalizados não suportam descrições de página.

Eis alguns cenários de estrutura sugeridos:

- [Perspetiva diferente](#different-perspective)
- [Adicionar detalhe](#add-detail)
- [Adicionar ajuda](#add-help)

### <a name="different-perspective"></a>Perspetiva diferente

Uma descrição de página pode visualizar os mesmos dados que o elemento visual de origem. Isto é conseguido através da utilização dos mesmos grupos do elemento visual e dinâmicos ou da utilização de diferentes tipos de elementos visuais. As descrições de página também podem aplicar filtros diferentes dos filtros aplicados ao elemento visual de origem.

O seguinte exemplo mostra o que acontece quando o utilizador do relatório paira o seu cursor sobre o valor **EnabledUsers**. O contexto de filtro para o valor é o Yammer em novembro de 2018.

![Um elemento visual de matriz apresenta uma grelha de valores agrupados por ano e mês nas linhas. Um utilizador de relatório pairou o cursor sobre um valor único. Foi apresentada uma descrição de página.](media/report-page-tooltips/suggestion-different-perspective.png)

É revelada uma descrição de página. Apresenta um elemento visual de dados diferente (gráfico de linhas e colunas agrupadas) e aplica um filtro de tempo contrastante. Repare que o contexto do filtro para o ponto de dados é de novembro de 2018. No entanto, a descrição da página apresenta a tendência durante _um ano inteiro de meses_.

### <a name="add-detail"></a>Adicionar detalhe

Uma descrição de página pode apresentar detalhes adicionais e adicionar contexto.

O seguinte exemplo mostra o que acontece quando o utilizador do relatório paira o seu cursor sobre o valor **Média de Pontos de Violação**, para o código postal 98022.

![Um elemento visual de tabela apresenta uma grelha de valores e a tabela inclui três colunas. Foi apresentada uma descrição de página.](media/report-page-tooltips/suggestion-add-details.png)

É revelada uma descrição de página. Apresenta os atributos e estatísticas específicos para o código postal 98022.

### <a name="add-help"></a>Adicionar ajuda

Os cabeçalhos de elementos visuais podem ser configurados para revelar descrições de página para cabeçalhos de elementos visuais. Pode adicionar conteúdos de ajuda a uma descrição de página ao utilizar caixas de texto com formatação avançada. Também é possível adicionar imagens e formas.

Curiosamente, os botões, imagens, caixas de texto e formas também podem revelar uma descrição de página de cabeçalho de elemento visual.

O seguinte exemplo mostra o que acontece quando o utilizador do relatório paira o cursor sobre o valor do cabeçalho do elemento visual.

![Um utilizador do relatório pairou o cursor sobre o ícone do cabeçalho do elemento visual (ícone de ponto de interrogação). Foi apresentada uma descrição de formatação avançada.](media/report-page-tooltips/suggestion-add-help.png)

É revelada uma descrição de página. Apresenta texto com formatação avançada que descreve as medidas apresentadas pelo elemento visual. A descrição também inclui uma forma (linha).

## <a name="recommendations"></a>Recomendações

No momento de criação do relatório, recomendamos as seguintes práticas:

- **Tamanho da página:** Configure a descrição de página para ser pequena. Pode utilizar a opção **Descrição** incorporada (320 píxeis de largura, 240 píxeis de altura). Em alternativa, pode configurar dimensões personalizadas. Tenha cuidado para não utilizar um tamanho de página demasiado grande, pois pode obscurecer os elementos visuais na página de origem.
- **Vista de página:** No estruturador de relatórios, defina a vista de página para **Tamanho Real** (a vista de página está predefinida para **Ajustar à Página**). Deste modo, pode ver o tamanho real da descrição de página ao criá-la.
- **Estilo:** pondere criar a sua descrição de página de forma a utilizar o mesmo tema e estilo do relatório. Deste modo, os utilizadores sentem que estão no mesmo relatório. Em alternativa, crie um estilo semelhante para as suas descrições e certifique-se de que aplica este estilo a todas as descrições de página.
- **Filtros de descrição:** Atribua filtros à descrição de página para que possa pré-visualizar um resultado realista ao criá-la. Não se esqueça de remover estes filtros antes de publicar o seu relatório.
- **Visibilidade de página:** Oculte sempre as páginas de descrições – os utilizadores não devem navegar diretamente para as mesmas.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Criar descrições com base em páginas de relatório no Power BI Desktop](../desktop-tooltips.md)
- [Personalizar descrições no Power BI Desktop](../desktop-custom-tooltips.md)
- Vídeo "Guy in a cube": [Descrição de página de relatório do Power BI – Como criar uma no Power BI Desktop](https://www.youtube.com/watch?v=URTA7JZsAtw)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
