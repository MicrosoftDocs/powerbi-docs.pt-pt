---
title: Linhagem de dados (pré-visualização)
description: Em projetos modernos de business intelligence (BI), um dos principais desafios para muitos clientes é compreender o fluxo de dados desde a origem até ao destino.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: 87f0fe20a88077d58ee5d44c748d86264b2be536
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968838"
---
# <a name="data-lineage-preview"></a>Linhagem de dados (pré-visualização)
Em projetos modernos de business intelligence (BI), compreender o fluxo de dados desde a origem até ao destino pode ser um desafio. A dimensão deste desafio é ainda maior se tiver desenvolvido projetos de análise avançados que abranjam múltiplas origens de dados, artefactos e dependências.  Responder a perguntas como "O que acontece se alterar estes dados?" ou "Porque é que este relatório não está atualizado?" pode ser difícil. A compreensão destas questões pode exigir o trabalho de uma equipa de peritos ou uma investigação profunda. Para ajudar a responder a estas perguntas, criámos a vista de linhagem de dados.

[ ![Vista de linhagem de dados do Power BI](media/service-data-lineage/power-bi-lineage-view-cropped.png) ](media/service-data-lineage/power-bi-lineage-view-full-size.png#lightbox)
 
O Power BI tem vários tipos de artefactos, como dashboards, relatórios, conjuntos de dados e fluxos de dados. Muitos conjuntos de dados e fluxos de dados ligam-se a origens de dados externas, como o SQL Server, e a conjuntos de dados externos noutras áreas de trabalho. Quando um conjunto de dados é externo a uma área de trabalho que lhe pertence, é possível que esteja numa área de trabalho de um colaborador de TI ou outro analista. Os conjuntos de dados e as origens de dados externas tornam difícil perceber de onde os dados são provenientes. Apresentamos a vista de linhagem tanto para projetos simples como complexos. 

Na vista de linhagem, pode ver as relações de linhagem entre todos os artefactos numa área de trabalho, bem como todas as respetivas dependências externas. Os fluxos de dados já tinham uma vista de diagrama, mas a vista de linhagem expande-a. Mostra as ligações entre todos os artefactos da área de trabalho, incluindo as ligações a fluxos de dados de origem e destino. A vista de diagrama de fluxos de trabalho separada será descontinuada a partir de novembro.

## <a name="explore-lineage-view"></a>Explorar a vista de linhagem

Todas as áreas de trabalho, quer sejam novas ou clássicas, têm automaticamente uma vista de linhagem, exceto A Minha Área de Trabalho. Precisa de, pelo menos, uma função de Contribuidor na área de trabalho para vê-la. Veja a secção [Permissões](#permissions) neste artigo para obter mais detalhes. 

- Para aceder à vista de linhagem, aceda à vista de lista da área de trabalho. Toque na seta junto a **Vista de lista** e selecione **Vista de linhagem**.

    [ ![Mudar para a vista de linhagem](media/service-data-lineage/power-bi-lineage-list-view-cropped.png) ](media/service-data-lineage/power-bi-lineage-list-view.png#lightbox)

    Nesta vista, pode ver todos os artefactos de área de trabalho e os respetivos fluxos de dados.

**Origens de dados**

Verá as origens de dados a partir das quais os conjuntos de dados e fluxos de dados obtêm os dados. Nos cartões de origem de dados, verá mais informações que podem ajudar a identificar a origem. Por exemplo, para o Azure SQL Server, também verá o nome da base de dados.

![Origem de dados da vista de linhagem sem nenhum gateway](media/service-data-lineage/power-bi-lineage-data-source-no-gateway.png)
 
**Gateways**

Se uma origem de dados estiver ligada através de um gateway no local, as informações do gateway serão adicionadas ao cartão da origem de dados. Se tiver permissões como administrador do gateway ou utilizador da origem de dados, verá mais informações, como o nome do gateway.

![Origem de dados da vista de linhagem com um gateway](media/service-data-lineage/power-bi-lineage-data-source-with-gateway.png)

**Conjuntos de dados e fluxos de dados**
 
Nos conjuntos de dados, verá a hora da última atualização e se o conjunto de dados foi certificado ou promovido.

![Conjunto de dados certificado na vista de linhagem](media/service-data-lineage/power-bi-lineage-external-certified-dataset.png)
 
Se um relatório na área de trabalho estiver incorporado num conjunto de dados noutra área de trabalho, verá o nome da área de trabalho de origem no cartão do conjunto de dados. Selecione o nome da área de trabalho de origem para aceder a essa área de trabalho.
 
- Em qualquer artefacto, selecione as reticências (...) para ver o menu de opções. Este menu apresenta todas as ações disponíveis na vista de lista.
  
Para ver mais metadados sobre os conjuntos de dados, selecione o próprio cartão do conjunto de dados. Serão apresentadas informações adicionais sobre o conjunto de dados num painel lateral.

![Painel lateral com mais informações](media/service-data-lineage/power-bi-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Mostrar a linhagem de qualquer artefacto 

Imagine que pretende ver a linhagem de um artefacto específico.

- Selecione as setas duplas por baixo de um artefacto.

    [ ![Realçar a linhagem de um artefacto específico](media/service-data-lineage/power-bi-lineage-highlight-cropped.png) ](media/service-data-lineage/power-bi-lineage-highlight-full-size.png#lightbox)

    O Power BI realça todos os artefactos relacionados com esse artefacto e esbate os restantes conteúdos. 

## <a name="navigation-and-full-screen"></a>Navegação e ecrã inteiro 

A vista de linhagem é uma tela interativa. Pode utilizar o rato e o touchpad para navegar na tela e ampliar ou reduzir.  

- Para ampliar ou reduzir, utilize o menu no canto inferior direito, ou o seu rato ou touchpad. 

- Para ter mais espaço para o próprio gráfico, utilize a opção de ecrã inteiro no canto superior direito. 

    ![Ampliar ou reduzir, ou ecrã inteiro](media/service-data-lineage/power-bi-lineage-zoom-full-screen.png)

## <a name="permissions"></a>Permissões

- Precisa de uma licença do Power BI Pro para ver a vista de linhagem.
- A vista de linhagem só está disponível para os utilizadores com acesso à área de trabalho.
- Os utilizadores precisam de ter uma função de Administrador, Membro ou Contribuidor na área de trabalho. Os utilizadores com uma função de Visualizador não podem mudar para a vista de linhagem.

## <a name="considerations-and-limitations"></a>Considerações e limitações

A vista de linhagem não está disponível no Internet Explorer. Veja [Supported browsers for Power BI](power-bi-browsers.md) (Browsers suportados para o Power BI) para obter detalhes.

## <a name="next-steps"></a>Próximos passos

- [Introdução aos conjuntos de dados em áreas de trabalho (Pré-visualização)](service-datasets-across-workspaces.md)
