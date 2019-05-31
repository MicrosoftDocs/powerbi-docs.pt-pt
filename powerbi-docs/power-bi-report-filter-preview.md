---
title: A nova experiência de filtros nos relatórios do Power BI (Pré-visualização)
description: Os filtros no Power BI têm novas funcionalidades e um novo design.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0a9e4986ae2f686eb8a8fd2d9fa07b169661ce60
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65853485"
---
# <a name="the-new-filter-experience-in-power-bi-reports-preview"></a>A nova experiência de filtros nos relatórios do Power BI (Pré-visualização)

Filtros no Power BI têm novas funcionalidades e um novo design. Quando escolher para a nova experiência de filtro, pode formatar o painel filtros para se parecer com o restante do relatório. Pode bloquear e até mesmo ocultar filtros. Ao projetar o seu relatório, já não verá o painel de filtros antigo em todos os no painel visualizações. Isso é feito o filtro de edição e formatação num único painel de filtros. 

![Nova experiência de filtro](media/power-bi-report-filter-preview/power-bi-filter-reading.png)

> [!NOTE]
> A nova experiência de filtros encontra-se no modo de pré-visualização. As novas compilações podem substituir a formatação que tiver definido.

Como um designer de relatório, este é o que pode fazer no novo painel único de filtros:

- Adicionar e remover campos a filtrar. 
- Altere o estado do filtro.
- Formatar e personalizar o painel filtros para que o que a maior parte do seu relatório.
- Definir se o Painel de filtros está aberto ou fechado por predefinição quando um consumidor abre o relatório.
- Oculta o painel de filtros todo ou filtros específicos que não pretende que os consumidores de relatórios para ver.
- Controlar e até mesmo de marcador a visibilidade, o estado aberto e fechado do painel de filtros do novo.
- Bloquear filtros que não quer que os consumidores editem.

Com a nova experiência de filtro, os consumidores de relatórios podem também passar o mouse sobre qualquer elemento visual para ver uma lista só de leitura de todos os filtros ou as segmentações de dados que afetam esse elemento visual.

![Lista de filtros para um elemento visual](media/power-bi-report-filter-preview/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>Ativar a nova experiência de filtros 

Vai ativar a nova experiência no Power BI Desktop. Em seguida, pode modificar os filtros aqui ou no serviço Power BI (https://app.powerbi.com). Uma vez que esta nova experiência de filtros está em Pré-visualização, tem de a ativar primeiro no Power BI Desktop. Se começar por criar um relatório no serviço Power BI, este não poderá conter os novos filtros.

### <a name="turn-on-new-filters-for-all-new-reports"></a>Ativar os novos filtros para todos os novos relatórios

1. No Power BI Desktop, selecione **Ficheiro** > **Opções e Definições** > **Opções** > **Funcionalidades de Pré-visualização** e, em seguida, selecione a caixa de verificação **Nova experiência de filtros**. 
2. Reinicie o Power BI Desktop para ver a nova experiência de filtros em todos os novos relatórios.

Depois de reiniciar o Power BI Desktop, a nova experiência fica ativada por predefinição para todos os novos relatórios que criar.  

### <a name="turn-on-new-filters-for-an-existing-report"></a>Ativar os novos filtros para um relatório existente

Também pode ativar os novos filtros para relatórios existentes.

1. No Power BI Desktop, num relatório existente, selecione **Ficheiro** > **Opções e Definições** > **Opções**.
2. Na barra de navegação esquerdo, sob **ficheiro atual**, selecione **comunicar definições**.
3. Sob **experiência de filtragem**, selecione **ativar o painel de filtro atualizada e mostrar os filtros no cabeçalho visual para este relatório**.

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Ver filtros de um elemento visual no Modo de leitura

No Modo de leitura, pode pairar o rato sobre um elemento visual no ícone de filtro para ver um pop-up com todos os filtros, segmentações de dados, entre outros, que afetam esse elemento visual. A formatação de pop-up é o mesmo que a formatação de painel de filtros. 

![Filtros que afetam um elemento visual](media/power-bi-report-filter-preview/power-bi-filter-per-visual.png)

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

## <a name="build-the-new-filters-pane"></a>Criar o novo painel de filtros

Depois de ativar o novo painel de filtros, vê-lo para a direita da página do relatório, formatada por predefinição, com base nas suas definições de relatório atual. Utilize o novo painel de filtros para configurar os filtros para incluir e para atualizar os filtros existentes no novo painel. O novo painel de filtros mostra que os consumidores do relatório, verá quando publicar o relatório. 

1. Por predefinição, os consumidores de relatórios podem ver o painel filtros. Se não quisê-los para vê-lo, selecione o ícone do olho junto a **filtros**.

    ![Ícone de olho de filtro do Power BI](media/power-bi-report-filter-preview/power-bi-filter-eye.png)

2. Para começar a criar o seu novo painel de filtros, arrastar campos de interesse para o novo painel de filtros como visual, página ou filtros de nível de relatório.

Quando adiciona um elemento visual para uma tela de relatório, o Power BI adiciona automaticamente um filtro para o painel filtros para cada campo no elemento visual. 

## <a name="lock-or-hide-filters"></a>Bloquear ou ocultar filtros

Pode bloquear ou ocultar cartões de filtros individuais. Se bloquear um filtro, os consumidores de relatórios poderão vê-lo, mas não o poderão alterar. Se o ocultar, nem sequer o poderão ver. Ocultar cartões de filtros será especialmente útil se precisar de ocultar filtros de limpeza de dados que excluem valores nulos ou valores inesperados. 

- No novo painel de filtros, selecione ou desmarque os **Zamknout filtr** ou **ocultar filtro** ícones num cartão de filtro.

   ![Ocultar ou bloquear filtros](media/power-bi-report-filter-preview/power-bi-filter-lock-hide.png)

Como ativar estas definições e desativado no novo painel de filtros, verá as alterações serão refletidas no relatório. Os filtros ocultos não aparecem no pop-up de filtros de um elemento visual.

Também pode configurar o novo estado do painel de filtros para o fluxo com seus indicadores de relatório. O estado aberto, fechado e estado de visibilidade do painel são todos passíveis de marcação.
 
## <a name="format-the-new-filters-pane"></a>Formatar o novo painel Filtros

Uma grande parte desta nova experiência é que pode formatar o painel de filtros de acordo com a aparência do seu relatório. Pode formatar o painel de filtros de forma diferente para cada página no relatório. Estes são os elementos que pode formatar: 

- Cor de fundo
- Transparência do fundo
- Border ativada ou desativada
- Cor dos limites
- Tamanho de fonte, cores e texto do título e o cabeçalho

Também pode formatar estes elementos para cartões de filtros, dependendo se estão aplicados (definidos para algo) ou disponíveis (desmarcados): 

- Cor de fundo
- Transparência do fundo
- Limite: ativado ou desativado
- Cor dos limites
- Tipo de letra, cor e tamanho do texto
- Cor da caixa de entrada

### <a name="format-the-filters-pane-and-cards"></a>Formatar o painel filtros e cartões

1. No relatório, clique no relatório propriamente dito ou no fundo (*imagem de fundo*), em seguida, no painel **Visualizações** e selecione **Formatar**. 
    Verá as opções de formatação a página de relatório, a imagem de fundo e também para o painel de filtros e cartões de filtro.

    ![Selecionar o ícone Formatar](media/power-bi-report-filter-preview/power-bi-filter-format.png)    

1. Expanda **Painel de filtros** para definir a cor do fundo, o ícone e o limite esquerdo, para complementar a página do relatório.

    ![Expandir o Painel de filtros](media/power-bi-report-filter-preview/power-bi-filter-format-pane-font.png)

1. Expanda **Cartões de filtros** para definir a cor e o limite **Disponível** e **Aplicado**. Se disponibilizar cores diferentes para cartões disponíveis e aplicados, será óbvio quais são os filtros aplicados. 
  
    ![Expandir o Cartão de filtros](media/power-bi-report-filter-preview/power-bi-filter-format-card-font.png)

## <a name="theming-for-filter-pane"></a>Temas para o painel de filtro
Agora pode modificar as predefinições do painel de filtro com o arquivo de tema. Este é um trecho do tema de exemplo para começar:

 
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

## <a name="sort-the-filter-pane"></a>Classificar o painel de filtro

Funcionalidade de classificação personalizada é parte da nova experiência de painel de filtro. Os criadores de relatórios podem arrastar e largar filtros para reorganizá-las na ordem que desejarem.

![Reorganizar a ordem de classificação de filtro](media/power-bi-report-filter-preview/power-bi-filter-sort.gif)

A ordem de classificação padrão é alfabética para filtros. Para iniciar o modo de tipo personalizado, basta arraste qualquer filtro para uma nova posição. Apenas pode ordenar os filtros no nível a que se aplicam – por exemplo, um filtro de nível visual, nível de página ou ao nível do relatório.

## <a name="filters-pane-scaling"></a>Dimensionamento do painel de filtros

O novo painel de filtros dimensiona com a página de relatório e os elementos visuais, por isso, a página de relatório e filtros mantenha-se de painel na mesma proporção entre si.

## <a name="improved-filters-pane-accessibility"></a>Acessibilidade melhorada de painel de filtros

Melhorámos a navegação do teclado para o novo painel de filtros. Pode percorrer todas as partes do painel de filtros e utilizar a chave de contexto no seu teclado ou SHIFT+F10 para abrir o menu de contexto.

![Acessibilidade do painel de filtros](media/power-bi-report-filter-preview/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Mudar o nome de filtros
Quando estiver a editar o painel filtros, pode clicar duas vezes o título para editá-lo. Mudar o nome é útil se pretender atualizar o cartão de filtro para fazer mais sentido para seus usuários finais. Lembre-se de mudar o nome do cartão de filtro faz *não* mudar o nome o nome a apresentar do campo na lista campos. Ela apenas muda o nome a apresentar utilizado o cartão de filtro.

![Mudar o nome de um filtro](media/power-bi-report-filter-preview/power-bi-filter-rename.png)

## <a name="restrict-changes-to-filter-type"></a>Restringir alterações para o tipo de filtro

Sob a filtragem experiência secção das definições do relatório que tem uma opção para controlar se os utilizadores podem alterar o tipo de filtro.

![Restringir o tipo de filtro de alteração](media/power-bi-report-filter-preview/power-bi-filter-restrict-change.png)

## <a name="next-steps"></a>Próximos passos

Experimente a nova experiência de filtros. Forneça seus comentários para esta funcionalidade, e como podemos continuar a melhorá-lo, no [site do Power BI ideias](https://ideas.powerbi.com/forums/265200-power-bi). 

- [Como utilizar filtros de relatório](consumer/end-user-report-filter.md)
- [Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

