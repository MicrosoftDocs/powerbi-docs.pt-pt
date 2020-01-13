---
title: A nova experiência de filtros nos relatórios do Power BI
description: Os filtros no Power BI têm novas funcionalidades e um novo design.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: e991b84dede16f35a732c54ff916ec02f5610783
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762537"
---
# <a name="work-with-filters-in-power-bi-reports"></a>Trabalhar com filtros nos relatórios do Power BI

Os filtros no Power BI têm novas funcionalidades e um novo design. Quando opta ativamente por participar na nova experiência de filtros, pode formatar o painel Filtros para se parecer com o resto do relatório. Pode bloquear e até mesmo ocultar filtros. Ao estruturar o seu relatório, já não vê o painel Filtros antigo no painel Visualizações. Faz toda a edição e formatação dos filtros num único painel Filtros. 

![Nova experiência de filtro](media/power-bi-report-filter/power-bi-filter-new-look.png)

Enquanto estruturador de relatórios, aqui estão algumas das tarefas que pode fazer no novo painel Filtros:

- Adicionar e remover campos a filtrar. 
- Alterar o estado do filtro.
- Formatar e personalizar o painel Filtros para se integrar melhor com o relatório.
- Definir se o Painel de filtros está aberto ou fechado por predefinição quando um consumidor abre o relatório.
- Ocultar o painel Filtros completo ou filtros específicos que não quer que os consumidores de relatórios vejam.
- Controlar e até mesmo marcar o estado da visibilidade, o estado aberto e o estado fechado do novo painel Filtros.
- Bloquear filtros que não quer que os consumidores editem.

Com a nova experiência de filtros, os consumidores de relatórios também podem pairar sobre qualquer elemento visual para ver uma lista só de leitura de todos os filtros ou segmentações de dados que o afetam.

![Lista de filtros para um elemento visual](media/power-bi-report-filter/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>Ativar a nova experiência de filtros 

Por predefinição, a nova experiência de filtros é ativada para novos relatórios. Pode ativar a nova experiência para relatórios já existentes no Power BI Desktop ou no serviço Power BI.

### <a name="turn-on-new-filters-for-an-existing-report-in-power-bi-desktop"></a>Ativar os novos filtros para um relatório existente no Power BI Desktop

1. No Power BI Desktop, num relatório existente, selecione **Ficheiro** > **Opções e Definições** > **Opções**.
2. No painel de navegação, em **Ficheiro atual**, selecione **Definições de relatório**.
3. Em **Experiência de filtragem**, selecione **Ativar o painel de filtros atualizado e apresentar filtros no cabeçalho do elemento visual deste relatório**.

### <a name="turn-on-new-filters-for-an-existing-report-in-the-service"></a>Ativar os novos filtros para um relatório existente no serviço

Se tiver ativado o **Novo aspeto** no serviço Power BI ![Novo aspeto ligado](media/power-bi-report-filter/power-bi-new-look-on.png), a nova experiência de filtro ficará automaticamente ativa. Leia mais sobre o [novo aspeto do serviço Power BI](service-new-look.md).

Mesmo que não tenha ativado o novo aspeto, pode ver a nova experiência de filtro ao seguir estes passos.

1. No serviço Power BI, selecione o separador **Relatórios** na lista de conteúdos de uma área de trabalho.
2. Localize o relatório que pretende ativar e selecione o ícone de **Definições**![ícone de Definições de Relatórios](media/power-bi-report-filter/power-bi-settings-icon.png) desse relatório.
3. Em **Experiência de filtragem**, selecione **Ativar o painel de filtros atualizado e apresentar filtros no cabeçalho do elemento visual deste relatório**.

    ![Ativar o painel dos filtros atualizados](media/power-bi-report-filter/power-bi-service-filter-enable.png)

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Ver filtros de um elemento visual no Modo de leitura

No Modo de leitura, pode pairar o rato sobre o ícone de filtro de um elemento visual para ver uma lista de filtros de pop-up com todos os filtros, segmentações de dados, entre outros, que afetam esse elemento visual. A formatação da lista de filtros de pop-up é igual à formatação do painel Filtros. 

![Filtros que afetam um elemento visual](media/power-bi-report-filter/power-bi-filter-per-visual.png)

Veja a seguir os tipos de filtros que esta vista apresenta: 
- Filtros básicos
- Segmentações
- Realce cruzado 
- Filtragem cruzada
- Filtros avançados
- Filtros de itens principais
- Filtros de Data Relativa
- Segmentações de dados síncronas
- Filtros de Inclusão/Exclusão
- Filtros passados por um URL

## <a name="build-the-new-filters-pane"></a>Criar o novo painel Filtros

Depois de ativar o novo painel Filtros, este é apresentado à direita da página do relatório, formatado por predefinição com base nas suas definições de relatório atuais. Pode utilizar o novo painel Filtros para configurar os filtros a incluir e atualizar os filtros existentes. O novo painel Filtros mostra o que os consumidores do relatório verão quando o publicar. 

1. Por predefinição, os consumidores do relatório podem ver o painel Filtros. Se não pretender que o vejam, selecione o ícone de olho junto a **Filtros**.

    ![Ícone de olho dos filtros do Power BI](media/power-bi-report-filter/power-bi-filter-eye.png)

2. Para começar a criar o novo painel Filtros, arraste campos de interesse para o mesmo como filtros de nível de elemento visual, de página ou de relatório.

Quando adiciona um elemento visual a uma tela de relatórios, o Power BI adiciona automaticamente um filtro ao painel Filtros para cada campo no elemento visual. 

## <a name="lock-or-hide-filters"></a>Bloquear ou ocultar filtros

Pode bloquear ou ocultar cartões de filtros individuais. Se bloquear um filtro, os consumidores de relatórios poderão vê-lo, mas não o poderão alterar. Se o ocultar, nem sequer o poderão ver. Ocultar cartões de filtros será especialmente útil se precisar de ocultar filtros de limpeza de dados que excluem valores nulos ou valores inesperados. 

- No novo painel Filtros, selecione ou desmarque os ícones **Bloquear filtro** ou **Ocultar filtro** no cartão de filtro.

   ![Ocultar ou bloquear filtros](media/power-bi-report-filter/power-bi-filter-lock-hide.png)

À medida que ativa e desativa estas definições no novo painel Filtros, vê as alterações refletidas no relatório. Os filtros ocultos não aparecem na lista de filtros de pop-up de um elemento visual.

Também pode configurar o estado do novo painel Filtros de forma a criar um fluxo juntamente com os seus marcadores de relatório. O estado aberto, fechado e estado de visibilidade do painel são todos passíveis de marcação.
 
## <a name="format-the-new-filters-pane"></a>Formatar o novo painel Filtros

Uma parte importante desta nova experiência passa por poder formatar o painel Filtros de acordo com o aspeto e a funcionalidade do seu relatório. Pode formatar o painel Filtros de forma diferente para cada página do relatório. Estes são os elementos que pode formatar: 

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

1. Expanda **Painel de filtros** para definir a cor do fundo, o ícone e o limite esquerdo, para complementar a página do relatório.

    ![Expandir o Painel de filtros](media/power-bi-report-filter/power-bi-format-filter-pane.png)

1. Expanda **Cartões de filtros** para definir a cor e o limite **Disponível** e **Aplicado**. Se disponibilizar cores diferentes para cartões disponíveis e aplicados, será óbvio quais são os filtros aplicados. 
  
    ![Expandir o Cartão de filtros](media/power-bi-report-filter/power-bi-format-filter-cards.png)

## <a name="theming-for-filter-pane"></a>Temas para o painel Filtros
Agora, pode modificar as predefinições do painel Filtros com o ficheiro de tema. Segue-se um recorte do tema de exemplo para começar:

 
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

## <a name="sort-the-filter-pane"></a>Ordenar o painel Filtros

A funcionalidade de ordenação personalizada faz parte da experiência do novo painel Filtros. Os criadores de relatórios podem arrastar e largar filtros para os reorganizar por qualquer ordem.

![Reorganizar a sequência de ordenação dos filtros](media/power-bi-report-filter/power-bi-filter-sort.gif)

A sequência de ordenação predefinida dos filtros é alfabética. Para iniciar o modo de ordenação personalizada, basta arrastar qualquer filtro para uma nova posição. Apenas pode ordenar os filtros no nível a que se aplicam, por exemplo, um filtro de nível de elemento visual, de nível de página ou de nível de relatório.

## <a name="improved-filters-pane-accessibility"></a>Acessibilidade melhorada do painel Filtros

Melhorámos a navegação do teclado no novo painel Filtros. Pode percorrer todas as partes do painel Filtros e utilizar a tecla de contexto no seu teclado ou Shift+F10 para abrir o menu de contexto.

![Acessibilidade do painel Filtros](media/power-bi-report-filter/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Mudar o nome dos filtros
Durante a edição do painel Filtros, pode clicar duas vezes no título para o editar. Mudar o nome é útil se pretender atualizar o cartão de filtro de forma a que faça mais sentido para os seus utilizadores finais. Lembre-se de que mudar o nome do cartão de filtro *não* muda o nome a apresentar do campo na lista campos. Muda apenas o nome a apresentar utilizado no cartão de filtro.

![Mudar o nome de um filtro](media/power-bi-report-filter/power-bi-filter-rename.png)

## <a name="restrict-changes-to-filter-type"></a>Restringir as alterações ao tipo de filtro

Na secção Experiência de filtragem das definições de relatório, tem uma opção para controlar se os utilizadores podem alterar o tipo de filtro.

![Restringir a alteração do tipo de filtro](media/power-bi-report-filter/power-bi-filter-restrict-change.png)

## <a name="next-steps"></a>Próximos passos

Experimente a nova experiência de filtros. Envie-nos os seus comentários sobre esta funcionalidade e indique-nos como a podemos continuar a melhorar no [site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

- [Como utilizar filtros de relatório](consumer/end-user-report-filter.md)
- [Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)
- [Different kinds of filters in Power BI](power-bi-report-filter-types.md) (Os diferentes tipos de filtros no Power BI)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

