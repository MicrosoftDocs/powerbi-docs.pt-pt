---
title: Avoid blank pages when printing paginated reports (Evitar páginas em branco ao imprimir relatórios paginados)
description: Orientação para conceber relatórios paginados de modo a evitar páginas em branco ao imprimir.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 0fa886973105bdb4bc8a35f145168c1775ca12cb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418469"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Avoid blank pages when printing paginated reports (Evitar páginas em branco ao imprimir relatórios paginados)

O presente artigo destina-se a si, na qualidade de autor de relatório que cria [relatórios paginados](../paginated-reports/paginated-reports-report-builder-power-bi.md) do Power BI. Apresenta recomendações para o ajudar a evitar páginas em branco quando o relatório é exportado para um formato de paginação, como PDF ou Microsoft Word, ou é impresso.

## <a name="page-setup"></a>Configuração da página

As propriedades do tamanho da página do relatório determinam a orientação da página, as dimensões e as margens. Aceda a estas propriedades do relatório:

- Com o relatório **Página de Propriedades**: clique com o botão direito do rato na área cinzenta escura fora da tela de relatórios e, em seguida, selecione _Propriedades do Relatório_.
- Com o [**painel Propriedades**](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane): clique na área cinzenta escura fora da tela do relatório para selecionar o objeto do relatório. Confirme que o painel **Propriedades** está aberto.

A página **Configuração da Página** do relatório **Página de Propriedades** disponibiliza uma interface amigável para ver e atualizar as propriedades da página de configuração.

![A imagem mostra a janela Propriedades do relatório com a página Configuração da Página realçada.](media/report-paginated-blank-page/report-page-setup-properties.png)

Confirme que todas as propriedades de tamanho da página estão corretamente configuradas:

|Propriedade|Recomendação|
|---------|---------|
|Unidades da página|Selecione as unidades relevantes, polegadas ou centímetros.|
|Orientação|Selecione a opção correta, vertical ou horizontal.|
|Tamanho do papel|Selecione um tamanho do papel ou atribua valores de largura e altura personalizados.|
|Margens|Defina os valores adequados para as margens esquerda, direita, superior e inferior.|
|||

## <a name="report-body-width"></a>Largura do corpo do relatório

As propriedades de tamanho da página determinam o espaço disponível para os objetos do relatório. Os objetos do relatório podem ser regiões de dados, visualizações de dados ou outros itens de relatório.

Um motivo comum para o aparecimento das páginas em branco, é a largura do corpo do relatório _exceder o espaço disponível na página_.

Só pode ver e definir a largura do corpo do relatório com o painel **Propriedades**. Primeiro, clique em qualquer lugar numa área vazia do corpo do relatório.

![A imagem mostra o painel Propriedades com a propriedade da largura do corpo do relatório realçada.](media/report-paginated-blank-page/report-body-properties-width.png)

Confirme que o valor de largura não ultrapassa a largura disponível na página. Pode orientar-se pela seguinte fórmula:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Não é possível reduzir a largura do corpo do relatório quando já existem objetos de relatório no espaço que quer remover. Deve primeiro reposicioná-los ou redimensioná-los antes de reduzir a largura.
>
> Além disso, a largura do corpo do relatório pode aumentar automaticamente quando adiciona novos objetos ou redimensiona ou reposiciona os objetos existentes. O designer de relatórios alarga sempre o corpo para acomodar a posição e o tamanho dos objetos contidos.

## <a name="report-body-height"></a>Altura do corpo do relatório

Outro motivo para o aparecimento de uma página em branco é a existência de excesso de espaço no corpo do relatório, após o último objeto.

Recomendamos que reduza sempre a altura do corpo para remover qualquer espaço à esquerda.

![A imagem mostra a estrutura do relatório. O espaço abaixo da região de dados tablix é realçado e assinalado como desnecessário.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Opções de quebra de página

Cada região e visualização de dados tem opções de quebra de página. Pode aceder a estas opções na página de propriedades ou no painel **Propriedades**.

Confirme que a propriedade **Adicionar uma quebra de página após** não é adicionada desnecessariamente.

![A imagem mostra uma janela Propriedades tablix. A propriedade “Adicionar uma quebra de página pós” está ativada.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Consumir Espaço em Branco do Contentor

Se o problema da página em branco persistir, também poderá tentar desativar a propriedade **ConsumeContainerWhitespace** do relatório. Apenas pode ser definido no painel **Propriedades**.

![A imagem apresenta o painel Propriedades, com a propriedade ConsumeContainerWhitespace realçada.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Por predefinição, está ativada. Controla se o espaço em branco mínimo nos contentores, como o corpo do relatório ou um retângulo, deve ser consumido. Apenas o espaço em branco à direita e abaixo do conteúdo é afetado.

## <a name="printer-paper-size"></a>Tamanho do papel da impressora

Por fim, se estiver a imprimir o relatório para papel, confirme que a impressora tem o papel correto carregado. O tamanho do papel físico deve corresponder ao [tamanho do papel do relatório](#page-setup).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [O que são relatórios paginados no Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Paginação nos relatórios paginados do Power BI](../paginated-reports/paginated-reports-pagination.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com)
