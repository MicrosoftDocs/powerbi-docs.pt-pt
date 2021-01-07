---
title: Deteção de conjuntos de dados com o hub de conjuntos de dados (pré-visualização)
description: Saiba como pode localizar, explorar e utilizar os conjuntos na sua organização e os relatórios relacionados.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/14/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 4e09eb9e0b44fbddf8787f474fe1a93b0b4c2d71
ms.sourcegitcommit: a92a3570eb14793a758a32e8fa1a756ec5d83f8c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97707979"
---
# <a name="datasets-discovery-using-the-datasets-hub-preview"></a>Deteção de conjuntos de dados com o hub de conjuntos de dados (pré-visualização)

O hub de conjuntos de dados facilita a localização, exploração e utilização dos conjuntos de dados na sua organização. Proporciona informações sobre os conjuntos de dados, bem como os pontos de entrada para criar relatórios sobre esses conjuntos de dados ou utilizá-los com a função Analisar no Excel.

O hub de conjuntos de dados pode ser útil em muitos cenários:
* Os proprietários de conjuntos de dados podem ver as métricas de utilização, o estado de atualização, os relatórios relacionados e a linhagem para ajudar a monitorizar e a gerir os conjuntos de dados.
* Os criadores de relatórios podem utilizar o hub para localizar conjuntos de dados adequados para criar os relatórios e utilizar ligações para criar facilmente relatórios com base no conjunto de dados, seja do zero ou a partir de modelos.
* Os consumidores de relatórios podem utilizar esta página para localizar relatórios com base em conjuntos de dados fidedignos.

Ao facilitar a localização de conjuntos de dados de qualidade e dos relatórios relacionados, o hub de conjuntos de dados ajuda a impedir a criação de relatórios redundantes. Também torna mais fácil encontrar bons relatórios a utilizar como pontos de partida para a criação de novos relatórios.

Este artigo explica o que pode ver no hub de conjuntos de dados e descreve como o utilizar. Para os proprietários de conjuntos de dados, também inclui várias sugestões sobre como [melhorar a capacidade de deteção e de utilização dos conjuntos de dados](#make-your-dataset-discoverable).

**Que conjuntos de dados consigo ver no hub de conjuntos de dados?**
* Para que um conjunto de dados apareça no hub de conjuntos de dados, tem de estar localizado numa [nova experiência de área de trabalho](../collaborate-share/service-new-workspaces.md).
* Os conjuntos de dados que pode ver no hub de conjuntos de dados são aqueles para os quais tem, no mínimo, [permissões de compilação](service-datasets-build-permissions.md).
* Se for um utilizador gratuito, só poderá ver os conjuntos de dados em *A minha área de trabalho* ou os conjuntos de dados para os quais tem [permissões de compilação](service-datasets-build-permissions.md) e que estão localizados em áreas de trabalho com capacidade Premium.

## <a name="find-the-dataset-you-need"></a>Localizar o conjunto de dados necessário

A experiência de deteção de conjuntos de dados começa na página do hub de conjuntos de dados. Para aceder a esta página:
* No serviço Power BI: selecione **Conjuntos de dados** no painel de navegação.
* Na aplicação Power BI no Teams: selecione a separador **Conjuntos de dados** ou **Conjuntos de dados** no painel de navegação.

A imagem abaixo mostra o hub de conjuntos de dados no serviço Power BI.

![Captura de ecrã a mostrar a página do hub de conjuntos de dados](media/service-datasets-hub/datasets-hub-main-page.png)

O hub de conjuntos de dados apresenta-lhe uma seleção de conjuntos de dados recomendados e uma lista de todos os conjuntos de dados na organização para os quais tem permissões de acesso.

As secções abaixo descrevem estas secções e as ações que pode realizar.

### <a name="recommended-datasets"></a>Conjuntos de dados recomendados

Os conjuntos de dados recomendados são conjuntos de dados endossados (promovidos ou certificados) que lhe são apresentados com base num cálculo que tem em consideração a última vez foram atualizados e a última vez que acedeu aos relatórios e/ou aos dashboards relacionados.

### <a name="dataset-list"></a>Lista de conjuntos de dados

A lista de conjuntos de dados mostra-lhe os conjuntos de dados na organização para os quais tem, no mínimo, [permissões de compilação](service-datasets-build-permissions.md). A lista tem três separadores para filtrar a lista de conjuntos de dados.
* **Todos os conjuntos de dados**: mostra todos os conjuntos de dados na sua organização para os quais tem, no mínimo, [permissões de compilação](service-datasets-build-permissions.md).
* **Recentes**: mostra os conjuntos de dados cujos relatórios relacionados acedeu recentemente. Quando acede a um relatório, pode existir um atraso de vários minutos até que o conjunto de dados relacionado seja apresentado na coluna Recentes.
* **Os meus conjuntos de dados**: mostra os conjuntos de dados que possui. 

Utilize a caixa de pesquisa para filtrar ainda mais os itens no separador atual.

As colunas da lista são descritas abaixo. Clique num cabeçalho de coluna para ordenar por essa coluna. 
* **Nome**: o nome do conjunto de dados. Clique no nome do conjunto de dados para explorar os relatórios criados através deste conjunto de dados.
* **Endosso**: estado do endosso.
* **Proprietário**: o proprietário do conjunto de dados.
* **Área de trabalho**: a área de trabalho na qual o conjunto de dados está localizado.
* **Atualizado**: a hora da última atualização (arredondada para hora, dia, mês e ano. Veja as informações do conjunto de dados na página de detalhes para obter a hora exata da última atualização).
* **Confidencialidade**: confidencialidade, se definida. Clique no ícone de informações para ver a descrição da etiqueta de confidencialidade.

### <a name="create-new-reports-or-pull-data-into-excel-via-analyze-in-excel"></a>Criar novos relatórios ou solicitar dados para o Excel através da função Analisar no Excel

Para criar um novo relatório com base num conjunto de dados ou solicitar os dados para o Excel com a função [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md), selecione **Mais opções (...)** no canto inferior direito de um mosaico do conjunto de dados recomendado ou na linha de um conjunto de dados na lista de conjuntos de dados. Podem ser apresentadas outras ações no menu pendente, consoante as permissões que tiver no conjunto de dados.

Quando criar um novo relatório com base no conjunto de dados, é apresentada uma tela de edição de relatórios. Quando guardar o novo relatório, este será guardado na área de trabalho que contém o conjunto de dados se tiver permissões de escrita nessa área de trabalho. Se não tiver permissões de escrita nessa área de trabalho ou se for um utilizador gratuito e o conjunto de dados residir numa área de trabalho com capacidade Premium, o novo relatório será guardado em *A minha área de trabalho*.

## <a name="view-dataset-details-and-explore-related-reports"></a>Ver os detalhes do conjunto de dados e explorar os relatórios relacionados

Para ver mais informações sobre o conjunto de dados, explorar relatórios relacionados ou criar um novo relatório com base no conjunto de dados, do zero ou a partir de um modelo, escolha um conjunto de dados de entre os conjuntos de dados recomendados ou na lista de conjuntos de dados. Será aberta uma página que mostra informações sobre o conjunto de dados, lista os relatórios criados com base no conjunto de dados e disponibiliza pontos de entrada para criar novos relatórios baseados no conjunto de dados ou para solicitar dados para o Excel através da função [Analisar no Excel](../collaborate-share/service-analyze-in-excel.md).

![Captura de ecrã a mostrar a página Explorar relatórios relacionados do hub de conjuntos de dados](media/service-datasets-hub/datasets-hub-explore-related-reports.png)

O cabeçalho da página apresenta o nome do conjunto de dados, o endosso, se existir, e o proprietário do conjunto de dados. Para enviar um e-mail ao proprietário ou certificador do conjunto de dados (se existir algum), clique no cabeçalho e, em seguida, clique no nome do proprietário.

### <a name="dataset-details"></a>Detalhes do conjunto de dados

A secção de detalhes do conjunto de dados mostra o nome da área de trabalho onde o conjunto de dados está localizado, a hora exata da última atualização, a confidencialidade (se definida), a descrição do conjunto de dados (se existir) e o nome do certificador (se estiver certificado). Também pode abrir a linhagem do conjunto de dados aqui.

### <a name="related-reports"></a>Relatórios relacionados

A secção Explorar relatórios relacionados mostra-lhe todos os relatórios criados no conjunto de dados selecionado. Pode criar uma cópia de um relatório ao selecionar a linha de relatório na lista e ao clicar no ícone Guardar uma cópia deste relatório.

Colunas na lista de relatórios relacionados:
* **Nome**: nome do relatório. Se o nome terminar com (modelo), significa que este relatório foi criado especialmente para ser utilizado como modelo.
* **Endosso**: estado do endosso.
* **Área de trabalho**: o nome da área de trabalho onde o relatório está localizado.

### <a name="create-a-report-built-on-the-dataset"></a>Criar um relatório com base no conjunto de dados

Na secção Criar um relatório, clique no botão **Criar**. Se existir um modelo de relatório para o conjunto de dados, será apresentado um menu pendente com duas opções:
* **A partir do modelo**: cria uma cópia do modelo em *A minha área de trabalho*.
* **A partir do zero**: abre a tela de edição de relatórios para um novo relatório criado no conjunto de dados. Quando guardar o novo relatório, este será guardado na área de trabalho que contém o conjunto de dados se tiver permissões de escrita nessa área de trabalho. Se não tiver permissões de escrita na área de trabalho ou se for um utilizador gratuito e o conjunto de dados residir numa área de trabalho com capacidade Premium, o novo relatório será guardado em *A minha área de trabalho*.

Se não existirem modelos de relatório, clicar em **Criar** abrirá diretamente a tela de edição de relatórios.

>[!NOTE]
> Só será apresentado um modelo no menu pendente Criar relatório, mesmo que exista mais de um modelo de relatório para este conjunto de dados. 

### <a name="pull-the-dataset-into-excel-via-analyze-in-excel"></a>Solicitar o conjunto de dados para o Excel através da função Analisar no Excel

Na secção Analisar no Excel, selecione **Analisar** para solicitar o conjunto de dados para o Excel através da função Analisar no Excel.

## <a name="make-your-dataset-discoverable"></a>Tornar o conjunto de dados detetável

Existem várias formas de melhorar a capacidade de deteção dos conjuntos de dados:
* **Endossar o conjunto de dados**: pode promover ou certificar o conjunto de dados para tornar mais fácil para os utilizadores localizarem e serem informados de que se trata de uma origem de dados fidedigna. Os conjuntos de dados endossados são etiquetados com destaques e prontamente identificáveis no Power BI. No hub de conjuntos de dados, só são apresentados os conjuntos de dados endossados na secção de conjuntos de dados recomendados e, por predefinição, a lista de conjuntos de dados mostra primeiro os conjuntos de dados endossados.

    [Saiba como endossar os conjuntos de dados](../collaborate-share/service-endorse-content.md). 
* **Introduzir uma descrição relevante para o conjunto de dados**: pode ajudar os utilizadores a descobrirem o conjunto de dados mais adequado ao introduzir descrições úteis e significativas dos conjuntos de dados. [Pode introduzir a descrição como parte do processo de endosso do conjunto de dados](../collaborate-share/service-endorse-content.md#promote-content). 
* **Atribuir uma imagem inesquecível ao conjunto de dados**: pode tornar mais fácil para os utilizadores localizarem e memorizarem o conjunto de dados ao atribuir-lhe uma imagem inesquecível. Assim, fará com que o conjunto de dados se destaque na página do hub de conjuntos de dados e em qualquer outro local que suporte a apresentação de imagens de conjuntos de dados. Para atribuir uma imagem ao conjunto de dado, abra as definições do conjunto de dados e expanda a secção Imagem do conjunto de dados.
* **Criar um modelo de relatório com base no conjunto de dados**: pode criar um modelo de relatório que os utilizadores possam utilizar para começarem a criar os seus próprios relatórios com base no conjunto de dados. Este modelo é simplesmente um relatório normal que cria, mas para ser utilizado como um modelo. Quando o guardar, terá de adicionar o sufixo “(modelo)” ao nome do relatório, por exemplo, *Vendas Mensais (modelo)* .

    Quando um utilizador selecionar **Criar > A partir do modelo** na secção Criar um relatório na vista de detalhes do conjunto de dados do hub de conjuntos de dados, será criada uma cópia do modelo em *A minha área de trabalho* e, em seguida, aberta na tela de edição de relatórios.

    Os modelos de relatório também são facilmente identificáveis na lista de relatórios relacionados na vista de detalhes do conjunto de dados do hub de conjuntos de dados.
  
## <a name="next-steps"></a>Passos seguintes
* [Utilizar conjuntos de dados em áreas de trabalho](service-datasets-across-workspaces.md)
* [Criar relatórios baseados em conjuntos de dados de diferentes áreas de trabalho](service-datasets-discover-across-workspaces.md)
* [Endossar o conjunto de dados](../collaborate-share/service-endorse-content.md)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
