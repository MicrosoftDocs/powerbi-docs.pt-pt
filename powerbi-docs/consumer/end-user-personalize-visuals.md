---
title: Personalizar os elementos visuais num relatório
description: Crie a sua própria vista de um relatório sem o editar.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/13/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 718363da3bd1f66de199db8d854d8d23d6de3eb5
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256769"
---
# <a name="personalize-visuals-in-a-report"></a>Personalizar os elementos visuais num relatório

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

É difícil criar um elemento visual que satisfaça os requisitos de todos. Porém, quando um colega partilha um relatório consigo, talvez queira fazer alterações nos elementos visuais sem ter de lhe pedir para fazer as alterações por si. 

Pode querer trocar os dados no eixo, alterar o tipo de elemento visual ou adicionar algo à descrição. Com a funcionalidade **Personalizar este elemento visual** , faça as alterações e, quando tiver o elemento visual desejado, guarde-o como um [marcador](end-user-bookmarks.md) para voltar a ele mais tarde. Não precisa sequer de permissão de edição para o relatório.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="Personalizar um elemento visual":::
 
## <a name="what-you-can-change"></a>O que pode alterar

Esta funcionalidade ajuda-o a obter mais informações através de uma exploração ad hoc dos elementos visuais num relatório do Power BI. Aqui estão algumas das modificações que pode fazer. As opções disponíveis variam conforme o tipo de elemento visual. 

- Alterar o tipo de visualização
- Trocar uma medida ou dimensão
- Adicionar ou remover uma legenda
- Comparar duas ou mais medidas
- Alterar agregações, etc.

Esta funcionalidade permite novas capacidades de exploração, além de incluir formas de capturar e partilhar as alterações:

- Capturar as alterações
- Partilhar as alterações
- Repor todas as alterações de um relatório
- Repor todas as alterações de um elemento visual
- Limpar as alterações recentes

> [!IMPORTANT]
> A capacidade de personalizar um elemento visual tem de ser ativada pelo *estruturador* do relatório. Se não vir o ícone **Personalizar este elemento visual** ![ícone Personalizar este elemento visual](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png), significa que o estruturador do relatório não ativou esta funcionalidade para o relatório atual. Verifique junto do proprietário do relatório ou do administrador do Power BI para que a funcionalidade seja ativada. Para apresentar informações de contacto do proprietário do relatório, selecione o nome do relatório na barra de menus do Power BI.

## <a name="personalize-visuals-in-the-power-bi-service"></a>Personalizar elementos visuais no serviço Power BI

Ao personalizar um elemento visual, pode explorar os dados de muitas formas sem sair da [vista de leitura do relatório](end-user-reading-view.md). Os seguintes exemplos mostram diferentes formas de poder modificar uma visualização em função das suas necessidades. 

1. Abra um relatório na vista de leitura no serviço Power BI.

2. Na barra de menus do elemento visual, selecione o ícone **Personalizar este elemento visual** ![ícone Personalizar este elemento visual](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Alterar o tipo de visualização

Acha que os dados poderiam ter uma apresentação melhor como um Gráfico de colunas empilhadas? Altere o **Tipo de visualização** .

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Personalizar um elemento visual":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Trocar uma medida ou dimensão
Substitua o campo que está a ser utilizado para o eixo X ao selecionar o campo que quer substituir e, em seguida, selecione um campo diferente.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Personalizar um elemento visual":::
 
### <a name="add-or-remove-a-legend"></a>Adicionar ou remover uma legenda
Ao adicionar uma legenda, pode codificar um elemento visual por cor com base numa categoria. Neste exemplo, estamos a utilizar a codificação por cores com base no nome da empresa. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Personalizar um elemento visual":::

### <a name="change-the-placement-of-fields"></a>Alterar o posicionamento de campos

Através da ação de arrastar e largar, pode alterar o posicionamento dos campos dentro da mesma propriedade visual ou mesmo entre propriedades visuais diferentes. Por exemplo, pode mover rapidamente um campo na legenda para o eixo de um elemento visual.

:::image type="content" source="media/end-user-personalize-visuals/personalize-drag-and-drop.png" alt-text="Personalizar um elemento visual":::

Também pode reordenar rapidamente as colunas de uma tabela ou matriz.

:::image type="content" source="media/end-user-personalize-visuals/personalize-reorder-columns.png" alt-text="Personalizar um elemento visual":::

### <a name="compare-two-or-more-different-measures"></a>Comparar duas ou mais medidas diferentes
Compare e contraste os valores de diferentes medidas ao utilizar o ícone + para adicionar várias medidas a um elemento visual. Para remover uma medida, selecione **Mais opções (...)** e escolha **Remover campo** .

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Personalizar um elemento visual":::

### <a name="change-aggregations"></a>Alterar agregações
Altere a forma como uma medida é calculada ao alterar a agregação no painel **Personalizar** . Selecione **Mais opções (...)** e escolha a agregação a utilizar.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Personalizar um elemento visual":::

### <a name="capture-changes"></a>Capturar alterações 
Através de marcadores pessoais, capture as alterações para que possa voltar à sua vista personalizada. Selecione **Marcadores** > **Marcadores pessoais** e dê um nome ao marcador. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Personalizar um elemento visual":::
 
Também pode tornar o marcador na vista predefinida.

### <a name="share-changes"></a>Partilhar alterações 
Se tiver permissões de leitura e partilha, quando partilhar o relatório, poderá optar por incluir as suas alterações.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Personalizar um elemento visual":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Repor todas as alterações a um relatório

No canto superior direito da tela do relatório, selecione **Repor para predefinição** . Esta ação remove todas as alterações no relatório e volta para a última vista guardada pelo autor do relatório.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Personalizar um elemento visual":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Repor todas as alterações a um elemento visual

Na barra de menus do elemento visual, selecione **Repor este elemento visual** para remover todas as alterações a um elemento visual específico e voltar para a última vista guardada desse elemento visual.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Personalizar um elemento visual":::
 
### <a name="clear-recent-changes"></a>Limpar alterações recentes

Selecione o ícone de borracha para limpar todas as alterações recentes que efetuou desde que abriu o painel **Personalizar** .  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Personalizar um elemento visual":::

## <a name="limitations"></a>Limitações

Atualmente, a funcionalidade tem algumas limitações que devem ser tidas em conta.

- A opção **Personalizar este elemento visual** pode ser desativada para um relatório inteiro ou para um determinado elemento visual. Se não tiver a opção de personalizar um elemento visual, consulte o administrador do Power BI ou o proprietário do relatório. Para apresentar informações de contacto do proprietário do relatório, selecione o nome do relatório na barra de menus do Power BI.
- As explorações de utilizadores não persistem automaticamente. Tem de guardar a sua vista como um marcador pessoal para capturar as alterações.
- Esta funcionalidade é suportada nas aplicações móveis do Power BI para tablets iOS e Android e na aplicação Windows do Power BI; não é suportada nas aplicações móveis do Power BI para telemóveis. No entanto, qualquer alteração a um elemento visual que guardar num marcador pessoal enquanto está no serviço Power BI será respeitada em todas as aplicações móveis do Power BI.

## <a name="next-steps"></a>Próximos passos
[Copiar um elemento visual do relatório como uma imagem estática](../visuals/power-bi-visualization-copy-paste.md)    
Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
