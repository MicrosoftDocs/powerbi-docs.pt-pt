---
title: Filtros de formato nos relatórios Power BI
description: Você tem muito controlo sobre o formato de filtro de relatório, design e funcionalidade.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 02/08/2021
LocalizationGroup: Reports
ms.openlocfilehash: 6b509576a3fe76e3565f9c0c354155957d7ad069
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531660"
---
# <a name="format-filters-in-power-bi-reports"></a>Filtros de formato nos relatórios Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Tem muito controlo sobre a conceção e a funcionalidade dos filtros de relatórios. Este artigo explica como pode formatar o painel de filtros para se parecer com o resto do relatório. Pode bloquear e até mesmo ocultar filtros.

![A experiência de filtro](media/power-bi-report-filter/power-bi-filter-new-look.png)

O primeiro passo é [adicionar filtros ao seu relatório.](power-bi-report-add-filter.md) Depois, como designer de relatórios, há muitas formas de formatar o painel de filtros:

- Adicionar e remover campos a filtrar. 
- Alterar o estado do filtro.
- Formatar e personalizar o painel Filtros para se integrar melhor com o relatório.
- Definir se o Painel de filtros está aberto ou fechado por predefinição quando um consumidor abre o relatório.
- Ocultar o painel Filtros completo ou filtros específicos que não quer que os consumidores de relatórios vejam.
- Controlar e até mesmo marcar o estado da visibilidade, o estado aberto e o estado fechado do painel Filtros.
- Bloquear filtros que não quer que os consumidores editem.

Ao lerem um relatório, os utilizadores podem pairar sobre qualquer elemento visual para ver uma lista só de leitura de todos os filtros ou segmentações de dados que o afetam.

![Lista de filtros para um elemento visual](media/power-bi-report-filter/power-bi-filter-visual.png)

Leia sobre [como os leitores de relatórios usam filtros](../consumer/end-user-report-filter.md) no modo de leitura de relatório.

## <a name="build-the-filters-pane"></a>Criar o painel Filtros

Por predefinição, o painel de filtros é formatado com base nas definições atuais do relatório. No painel Filtros, configura os filtros a incluir e atualiza os filtros existentes. O painel filters é o mesmo para os consumidores do seu relatório quando publica o seu relatório. 

1. Quando adiciona um elemento visual a uma tela de relatórios, o Power BI adiciona automaticamente um filtro ao painel Filtros para cada campo no elemento visual.

2. Para construir o painel de filtros, arraste outros campos de interesse para o painel de filtros como filtros visuais, de página ou de nível de relatório.

## <a name="show-or-hide-the-filters-pane"></a>Mostrar ou esconder o painel de filtros

### <a name="hide-the-filters-pane-in-reading-mode"></a>Esconda o painel de filtros no modo de leitura

Se não quiser que os seus leitores vejam o painel de filtros, selecione o ícone **dos olhos** ao lado **dos Filtros**.

![Ícone de olho](media/power-bi-report-filter/power-bi-filter-eye.png) 

### <a name="hide-the-filters-pane-while-editing"></a>Ocultar o painel Filtros durante a edição

Pode esconder o painel de filtros enquanto está a editar o seu relatório, quando não estiver a usar o painel de filtros e precisar de espaço extra no ecrã. 

- No **separador Ver,** o botão **Filtros** permite-lhe mostrar ou ocultar o painel de filtros.

![Mostrar ou ocultar o painel Filtros durante a edição](media/power-bi-report-filter/power-bi-filter-hide.png)

Esta definição só oculta o painel Filtros no Power BI Desktop. Não há equivalente no modo de edição no serviço Power BI.

## <a name="lock-or-hide-filters"></a>Bloquear ou ocultar filtros

Pode bloquear ou ocultar cartões de filtros individuais. Se bloquear um filtro, os consumidores de relatórios poderão vê-lo, mas não o poderão alterar. Se o ocultar, nem sequer o poderão ver. Ocultar cartões de filtros será especialmente útil se precisar de ocultar filtros de limpeza de dados que excluem valores nulos ou valores inesperados. 

- No painel Filtros, selecione ou desmarque os ícones **Bloquear filtro** ou **Ocultar filtro** no cartão de filtro.

   ![Ocultar ou bloquear filtros](media/power-bi-report-filter/power-bi-filter-lock-hide.png)

À medida que ativa e desativa estas definições no painel Filtros, vê as alterações refletidas no relatório. Os filtros ocultos não aparecem na lista de filtros de pop-up de um elemento visual.

Também pode configurar o estado do painel Filtros de forma a criar um fluxo juntamente com os marcadores de relatório. O estado aberto, fechado e estado de visibilidade do painel são todos passíveis de marcação.
 
## <a name="format-the-filters-pane"></a>Formatar o painel Filtros

Uma parte importante da experiência de filtro passa por poder formatar o painel Filtros de acordo com o aspeto e a funcionalidade do seu relatório. Também pode formatar o painel Filtros de forma diferente para cada página do relatório. Estes são os elementos que pode formatar: 

- Cor de fundo
- Transparência do fundo
- Limite ativado ou desativado
- Cor dos limites
- Tipo de letra, cor e tamanho do texto do título e do cabeçalho

Também pode formatar estes elementos para cartões de filtros, dependendo se estão aplicados (definidos para algo) ou disponíveis (desmarcados): 

- Cor de fundo
- Transparência do fundo
- Limite: ativado ou desativado
- Cor dos limites
- Tipo de letra, cor e tamanho do texto
- Cor de caixa de entrada

### <a name="format-the-filters-pane-and-cards"></a>Formatar o painel Filtros e os Cartões de filtros

1. No relatório, clique no relatório propriamente dito ou no fundo (*imagem de fundo*), em seguida, no painel **Visualizações** e selecione **Formatar**. 
    Verá as opções de formatação da página do relatório, da imagem de fundo e também do painel Filtros e dos Cartões de filtros.

1. Expanda o **painel Filtros** para definir a cor do fundo, o ícone e o limite esquerdo, para complementar a página do relatório.

    ![Expandir o painel Filtros](media/power-bi-report-filter/power-bi-format-filter-pane.png)

1. Expanda **Cartões de filtros** para definir a cor e o limite **Disponível** e **Aplicado**. Se disponibilizar cores diferentes para cartões disponíveis e aplicados, será óbvio quais são os filtros aplicados. 
  
    ![Expandir o Cartão de filtros](media/power-bi-report-filter/power-bi-format-filter-cards.png)

## <a name="theming-for-filters-pane"></a>Temas para o painel Filtros
Agora, pode modificar as predefinições do painel Filtros com o ficheiro de tema. Segue-se um fragmento do tema de exemplo para começar:

 
```
"outspacePane": [{ 

"backgroundColor": {"solid": {"color": "#0000ff"}}, 

"foregroundColor": {"solid": {"color": "#00ff00"}}, 

"transparency": 50, 

"titleSize": 35, 

"headerSize": 8, 

"fontFamily": "Georgia", 

"border": true, 

"borderColor": {"solid": {"color": "#ff0000"}} 

}], 

"filterCard": [ 

{ 

"$id": "Applied", 

"transparency": 0, 

"backgroundColor": {"solid": {"color": "#ff0000"}}, 

"foregroundColor": {"solid": {"color": "#45f442"}}, 

"textSize": 30, 

"fontFamily": "Arial", 

"border": true, 

"borderColor": {"solid": {"color": "#ffffff"}}, 

"inputBoxColor": {"solid": {"color": "#C8C8C8"}} 

}, 

{ 

"$id": "Available", 

"transparency": 40, 

"backgroundColor": {"solid": {"color": "#00ff00"}}, 

"foregroundColor": {"solid": {"color": "#ffffff"}}, 

"textSize": 10, 

"fontFamily": "Times New Roman", 

"border": true, 

"borderColor": {"solid": {"color": "#123456"}}, 

"inputBoxColor": {"solid": {"color": "#777777"}} 

}] 
```

## <a name="sort-the-filters-pane"></a>Ordenar o painel Filtros

A funcionalidade de ordenação personalizada está disponível no painel Filtros. Ao criar relatórios, pode arrastar e largar filtros para os reorganizar por qualquer ordem.

![Reorganizar a sequência de ordenação dos filtros](media/power-bi-report-filter/power-bi-filter-sort.gif)

A sequência de ordenação predefinida dos filtros é alfabética. Para iniciar o modo de ordenação personalizada, basta arrastar qualquer filtro para uma nova posição. Só é possível reencomendar filtros dentro do nível a que se aplicam. Por exemplo, pode alterar a ordem dos filtros de nível visual dentro da secção de nível visual do painel de filtros.

## <a name="improved-filters-pane-accessibility"></a>Acessibilidade melhorada do painel Filtros

Melhorámos a navegação do teclado no painel Filtros. Pode percorrer todas as partes do painel Filtros e utilizar a tecla de contexto no seu teclado ou Shift+F10 para abrir o menu de contexto.

![Acessibilidade do painel Filtros](media/power-bi-report-filter/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Mudar o nome dos filtros
Durante a edição do painel Filtros, pode clicar duas vezes no título para o editar. Mudar o nome é útil se pretender atualizar o cartão de filtro de forma a que faça mais sentido para os seus utilizadores finais. Lembre-se de que mudar o nome do cartão de filtro *não* muda o nome a apresentar do campo na lista campos. Muda apenas o nome a apresentar utilizado no cartão de filtro.

![Mudar o nome de um filtro](media/power-bi-report-filter/power-bi-filter-rename.png)

## <a name="filters-pane-search"></a>Pesquisa do painel Filtros

A funcionalidade de pesquisa do painel Filtros permite-lhe procurar os seus cartões de filtros por título. Esta funcionalidade é útil se tiver vários cartões de filtros diferentes no seu painel Filtros e precisar de ajuda para encontrar os que são relevantes.

![Procurar um filtro](media/power-bi-report-filter/power-bi-filter-search.png)

Também pode formatar a caixa de pesquisa da mesma forma que formata os restantes elementos do painel Filtros.

![Formatar a caixa de pesquisa](media/power-bi-report-filter/power-bi-filter-format-search.png)

Embora esta funcionalidade de pesquisa do painel Filtros esteja ativada por predefinição, também pode optar por desativá-la ao selecionar **Ativar a pesquisa no painel de filtro** nas definições de **Relatório** da caixa de diálogo **Opções**.

![Ativar ou desativar a pesquisa](media/power-bi-report-filter/power-bi-enable-search-filter.png)

## <a name="restrict-changes-to-filter-type"></a>Restringir as alterações ao tipo de filtro

Na secção **Experiência de filtragem** das definições de **Relatório**, tem uma opção para controlar se os utilizadores podem alterar o tipo de filtro.

![Restringir a alteração do tipo de filtro](media/power-bi-report-filter/power-bi-enable-change-filter-type.png)

## <a name="allow-saving-filters"></a>Permitir que os filtros sejam guardados

Por predefinição, os seus leitores de relatórios podem guardar filtros do seu relatório. Pode optar por não permitir que estes guardem filtros.

- Ainda nas definições de **Relatório** da caixa de diálogo **Opções**, em **Filtros persistentes**, selecione **Não permitir que os utilizadores finais guardem filtros neste relatório**.

    :::image type="content" source="media/power-bi-report-filter/power-bi-persistent-filters.png" alt-text="Captura de ecrã a mostrar a opção Não permitir que os utilizadores finais guardem filtros neste relatório":::.

## <a name="apply-filters-button"></a>Botão Aplicar dos filtros

Pode adicionar um botão **Aplicar** único ao painel de filtros, o que permitirá que aplique (bem como aos utilizadores finais) todas as modificações do filtro de uma só vez. Ter este botão poderá ser útil se quiser adiar a aplicação de alterações de filtros. Só tem de esperar uma vez, depois de estar pronto para aplicar todas as alterações do filtro no relatório ou nos elementos visuais.

:::image type="content" source="media/power-bi-report-filter/apply-filter-button.png" alt-text="Botão Aplicar filtro":::

### <a name="turn-on-the-apply-button"></a>Ativar o botão Aplicar

Pode definir esta função ao nível do relatório. Contudo, por predefinição, esta funcionalidade está desativada.

1. Aceda a **Ficheiro** > **Opções e definições** > **Opções** > **Redução de consultas**.

1. Selecione **Adicionar um botão Aplicar único ao painel de filtros para aplicar as alterações de uma só vez**.

    :::image type="content" source="media/power-bi-report-filter/apply-all-filters.png" alt-text="Ativar botão Aplicar filtro":::

### <a name="format-the-apply-button"></a>Formatar o botão Aplicar

Atualmente, pode controlar parte da formatação do texto **Aplicar** do botão. Na secção do **painel Filtros** do painel **Formato**, defina estas opções:

- **Caixa de verificação e Aplicar cor** controla a cor de preenchimento. 
- **Tipo de letra e cor do ícone** controla a cor do texto.
- **Tamanho do texto do cabeçalho** controla o tamanho do texto.
- **Família do tipo de letra** controla o tipo de letra.

    :::image type="content" source="media/power-bi-report-filter/format-apply-filter.gif" alt-text="Formatar o texto do botão Aplicar filtro":::

## <a name="considerations-and-limitations"></a>Considerações e limitações

A publicação na Web não apresenta o painel Filtros. Se está a planear publicar um relatório na web, considere adicionar cortadores para filtragem.

## <a name="next-steps"></a>Próximos passos

- [Como utilizar filtros de relatório](../consumer/end-user-report-filter.md)
- [Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)
- [Different kinds of filters in Power BI](power-bi-report-filter-types.md) (Os diferentes tipos de filtros no Power BI)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)
