---
title: Use report page drillthrough (Utilizar a pormenorização de páginas de relatórios)
description: Orientação para trabalhar com pormenorização de páginas de relatório.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: 48942b30b84706c933ccef455129c84a67ac5a1b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76040374"
---
# <a name="use-report-page-drillthrough"></a>Use report page drillthrough (Utilizar a pormenorização de páginas de relatórios)

O presente artigo destina-se a si, na qualidade de autor de relatório que cria relatórios do Power BI. Fornece sugestões e recomendações para a criação de [pormenorização de páginas de relatórios](../desktop-drillthrough.md).

É recomendável que crie o seu relatório para permitir que os utilizadores do relatório possam alcançar o seguinte fluxo:

1. Ver uma página de relatório.
2. Identificar um elemento visual para analisar em maior profundidade.
3. Clicar com o botão direito do rato no elemento visual da pormenorização.
4. Executar uma análise complementar.
5. Voltar à página de relatório de origem.

## <a name="suggestions"></a>Sugestões

Sugerimos que considere dois tipos de cenários de pormenorização:

- [Profundidade adicional](#additional-depth)
- [Perspetiva mais abrangente](#broader-perspective)

### <a name="additional-depth"></a>Profundidade adicional

Quando a sua página de relatório apresenta resultados resumidos, uma página de pormenorização pode conduzir os utilizadores do relatório aos detalhes ao nível de transação. Esta abordagem de estrutura permite-lhes ver as transações de suporte, apenas quando for necessário.

O seguinte exemplo mostra o que acontece quando um utilizador de relatório pormenoriza a partir de um resumo de vendas mensais. A página de pormenorização inclui uma lista detalhada de encomendas para um mês específico.

![Um elemento visual de matriz intitulado "Resumo de Vendas" agrupa as vendas por ano e mês nas linhas e por país nas colunas. Uma página de pormenorização também é apresentada.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Perspetiva mais abrangente

Uma página de pormenorização pode alcançar o oposto da profundidade adicional. Este cenário é ótimo para pormenorizar uma vista holística.

O seguinte exemplo mostra o que acontece quando um utilizador de relatório pormenoriza a partir de um código postal. A página de pormenorização apresenta informações gerais sobre esse código postal.

![Um elemento visual de tabela tem três colunas: Código Postal, Média de Pontos de Violação e Média de Classificação de Nível. A página de pormenorização também é apresentada.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Recomendações

No momento de criação do relatório, recomendamos as seguintes práticas:

- **Estilo:** pondere criar a sua página de pormenorização de forma a utilizar o mesmo tema e estilo do relatório. Deste modo, os utilizadores sentem que estão no mesmo relatório.
- **Filtros de pormenorização:** configure filtros de pormenorização para poder pré-visualizar um resultado realista à medida que cria a página de pormenorização. Não se esqueça de remover estes filtros antes de publicar o relatório.
- **Recursos adicionais:** uma página de pormenorização é semelhante a qualquer página de relatório. Pode até mesmo melhorá-la com recursos interativos adicionais, incluindo segmentações ou filtros.
- **Espaços em branco:** evite adicionar elementos visuais que podem exibir EM BRANCO ou produzir erros quando os filtros de pormenorização são aplicados.
- **Visibilidade de página:** pondere ocultar páginas de pormenorização. Se decidir manter uma página de pormenorização visível, certifique-se de que adiciona um botão que permita aos utilizadores limpar os filtros de pormenorização definidos anteriormente. Atribua um [marcador](../desktop-bookmarks.md) ao botão. O marcador deve ser configurado para remover todos os filtros.
- **Botão Anterior:** Um botão [Anterior](../desktop-buttons.md) é adicionado automaticamente quando atribui um filtro de pormenorização. É boa ideia mantê-lo. Deste modo, os utilizadores do seu relatório podem voltar facilmente à página de origem.
- **Deteção:** ajude a promover a deteção de uma página de pormenorização ao definir texto do ícone do cabeçalho do elemento visual ou ao adicionar instruções a uma caixa de texto. Também pode criar uma sobreposição, conforme descrito nesta [publicação de blogue](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/).

> [!TIP]
> Também é possível configurar a pormenorização para os seus relatórios paginados do Power BI. Pode fazê-lo ao adicionar ligações para relatórios do Power BI. As ligações podem definir [parâmetros de URL](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Utilizar a pormenorização no Power BI Desktop](../desktop-drillthrough.md)
- Vídeo "Guy in a cube": [Explorar a pormenorização no Power BI Desktop](https://www.youtube.com/watch?v=2x9lLHDbtDk)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
