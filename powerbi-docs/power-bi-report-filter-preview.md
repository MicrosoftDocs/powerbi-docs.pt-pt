---
title: A nova experiência de filtros nos relatórios do Power BI (Pré-visualização)
description: Os filtros no Power BI têm novas funcionalidades e um novo design.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/14/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: b130ccbe6b3fe6fa09b9a4c4efe388f79350c500
ms.sourcegitcommit: f07520591db6c3f27ab6490612cc56384abc6633
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56298828"
---
# <a name="the-new-filter-experience-in-power-bi-reports-preview"></a>A nova experiência de filtros nos relatórios do Power BI (Pré-visualização)

Este artigo descreve a nova experiência de filtragem: Os filtros no Power BI têm novas funcionalidades e um novo design. Quando estrutura relatórios no Power BI Desktop ou no serviço Power BI, pode alterar o aspeto do Painel de filtros e fazer com que interaja com todo o relatório. Na nova experiência, o Painel de filtros antigo atua como um painel de edição de filtros e o novo painel Filtros é o único que os consumidores de relatórios veem. 
 
![Vista predefinida (sem a aplicação de personalização adicional)](media/power-bi-report-filter-preview/power-bi-filter-reading.png)

> [!NOTE]
> A nova experiência de filtros encontra-se no modo de pré-visualização. As novas compilações podem substituir a formatação que tiver definido.

Enquanto estruturador de relatórios, eis o que pode fazer com os novos filtros:

- Apresentar uma vista de filtros só de leitura no cabeçalho de elemento visual, para que os consumidores saibam exatamente quais são os filtros ou as segmentações de dados que estão a afetar um determinado elemento visual.
- Formatar e personalizar o painel de filtros para se integrar melhor com o relatório.
- Definir se o Painel de filtros está aberto ou fechado por predefinição quando um consumidor abre o relatório.
- Ocultar o painel de filtros completo ou filtros específicos que não quer que os consumidores de relatórios vejam.
- Controlar e até mesmo marcar o estado da visibilidade, o estado aberto e o estado fechado do novo painel de filtros.
- Bloquear filtros que não quer que os consumidores editem.

## <a name="turn-on-the-new-filter-experience"></a>Ativar a nova experiência de filtros 

Vai ativar a nova experiência no Power BI Desktop. Em seguida, pode modificar os filtros aqui ou no serviço Power BI (https://app.powerbi.com). Uma vez que esta nova experiência de filtros está em Pré-visualização, tem de a ativar primeiro no Power BI Desktop. Se começar por criar um relatório no serviço Power BI, este não poderá conter os novos filtros.

### <a name="turn-on-new-filters-for-all-new-reports"></a>Ativar os novos filtros para todos os novos relatórios

1. No Power BI Desktop, selecione **Ficheiro** > **Opções e Definições** > **Opções** > **Funcionalidades de Pré-visualização** e, em seguida, selecione a caixa de verificação **Nova experiência de filtros**. 
2. Reinicie o Power BI Desktop para ver a nova experiência de filtros em todos os novos relatórios.

Depois de reiniciar o Power BI Desktop, a nova experiência fica ativada por predefinição para todos os novos relatórios que criar.  

### <a name="turn-on-new-filters-for-an-existing-report"></a>Ativar os novos filtros para um relatório existente

Também pode ativar os novos filtros para relatórios existentes.

1. No Power BI Desktop, num relatório existente, selecione **Ficheiro** > **Opções e Definições** > **Opções**.
2. Em **Definições de relatório**, selecione **Ativar o painel de filtros atualizado e apresentar filtros no cabeçalho do elemento visual deste relatório**.

## <a name="build-the-new-filter-pane"></a>Criar o novo painel de filtros

Depois de ativar o novo painel de filtros, este será apresentado à direita da página do relatório, formatado por predefinição com base nas suas definições de relatório atuais. O painel de filtros antigo agora atua como o painel de edição dos filtros. O novo painel de filtros mostra o que os consumidores do relatório verão quando publicar o relatório. Pode atualizar os filtros existentes no novo painel, mas vai utilizar o painel de filtros antigo para configurar os filtros a incluir.

1. Primeiro, vai decidir se quer que os consumidores de relatórios vejam o painel de filtros. Se quiser que o vejam, selecione o ícone de olho ![Ícone de olho](media/power-bi-report-filter-preview/power-bi-filter-off-eye-icon.png) junto a Filtros.

2. Para começar a criar o novo painel de filtros, arraste campos de interesse para o painel de edição de filtros como filtros de nível de elemento visual, de página ou de relatório. Serão apresentados no novo painel Filtros.

    ![power-bi-filters-new-filters-pane.png](media/power-bi-report-filter-preview/power-bi-filters-new-filters-pane.png)

Quando adiciona um elemento visual à tela do relatório, o Power BI adiciona automaticamente um filtro para cada campo no elemento visual. O Power BI não adiciona esses filtros automáticos ao painel de filtros só de leitura. Tem de selecionar o ícone de olho para os adicionar explicitamente.

 
## <a name="lock-or-hide-filters"></a>Bloquear ou ocultar filtros

Pode bloquear ou ocultar cartões de filtros individuais. Se bloquear um filtro, os consumidores de relatórios poderão vê-lo, mas não o poderão alterar. Se o ocultar, nem sequer o poderão ver. Ocultar cartões de filtros será especialmente útil se precisar de ocultar filtros de limpeza de dados que excluem valores nulos ou valores inesperados. 

- No painel de edição do filtro, selecione ou desmarque os ícones **Bloquear filtro** ou **Ocultar filtro** no cartão de filtro.

   ![Ocultar ou bloquear filtros](media/power-bi-report-filter-preview/power-bi-filter-hide-lock.gif)

À medida que ativa e desativa estas definições no painel de edição de filtros, verá as alterações refletidas no novo painel de filtros. Os filtros ocultos não aparecem no pop-up de filtros de um elemento visual.

Também pode configurar o estado do painel de filtros de forma a criarem um fluxo juntamente com os seus marcadores de relatório. O estado aberto, fechado e estado de visibilidade do painel são todos passíveis de marcação.
 
## <a name="format-the-new-filters-pane"></a>Formatar o novo painel Filtros

Uma parte importante desta nova experiência passa por agora poder formatar o painel de filtros de acordo com a aparência do seu relatório. Pode formatar o painel de filtros de forma diferente para cada página do relatório. Estes são os elementos que pode formatar: 

- Cor de fundo
- Transparência do fundo
- Limite do painel de filtros ativado ou desativado
- Cor do limite do painel de filtros
- Título do painel de filtros e tipo de letra, cor e tamanho do texto do cabeçalho

Também pode formatar estes elementos para cartões de filtros, dependendo se estão aplicados (definidos para algo) ou disponíveis (desmarcados): 

- Cor de fundo
- Transparência do fundo
- Limite: ativado ou desativado
- Cor dos limites
- Tipo de letra, cor e tamanho do texto
- Cor de caixa de entrada

### <a name="set-the-format-for-the-filters-pane-and-cards"></a>Definir o formato do Painel de filtros e dos cartões

1. No relatório, clique no relatório propriamente dito ou no fundo (*imagem de fundo*), em seguida, no painel **Visualizações** e selecione **Formatar**. 
    Verá as opções de formatação da página do relatório, da imagem de fundo e também do Painel de filtros e dos Cartões de filtros.

    ![Selecionar o ícone Formatar](media/power-bi-report-filter-preview/power-bi-filter-format.png)    

1. Expanda **Painel de filtros** para definir a cor do fundo, o ícone e o limite esquerdo, para complementar a página do relatório.

    ![Expandir o Painel de filtros](media/power-bi-report-filter-preview/power-bi-filter-format-pane-font.png)

1. Expanda **Cartões de filtros** para definir a cor e o limite **Disponível** e **Aplicado**. Se disponibilizar cores diferentes para cartões disponíveis e aplicados, será óbvio quais são os filtros aplicados. 
  
    ![Expandir o Cartão de filtros](media/power-bi-report-filter-preview/power-bi-filter-format-card-font.png)

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Ver filtros de um elemento visual no Modo de leitura

No Modo de leitura, pode pairar o rato sobre um elemento visual no ícone de filtro para ver um pop-up com todos os filtros, segmentações de dados, entre outros, que afetam esse elemento visual. A formatação do pop-up é igual à formatação do painel de filtros. 

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

## <a name="coming-soon"></a>Em breve

Nos próximos meses, planeamos incorporar as seguintes melhorias:
- Capacidade de alterar a ordem dos cartões de filtros
- Experiência de painel de filtros único para os criadores de relatórios 
- Mais opções de formatação

Experimente a nova experiência de filtros. Envie os seus comentários sobre esta funcionalidade e indique-nos como podemos continuar a melhorar esta experiência. 

## <a name="next-steps"></a>Próximos passos
[Como utilizar filtros de relatório](consumer/end-user-report-filter.md)

[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

[Interação com filtros e realce na Vista de Leitura do relatório](consumer/end-user-reading-view.md)

[Alterar como os elementos visuais de relatórios realizam filtragem cruzada e realce cruzado entre si](consumer/end-user-interactions.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

