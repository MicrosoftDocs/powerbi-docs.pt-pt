---
title: Gerir o armazenamento de dados nas suas áreas de trabalho
description: Saiba como pode gerir o armazenamento de dados na sua área de trabalho individual para certificar-se de que pode continuar a publicar relatórios e conjuntos de dados.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 07/27/2020
LocalizationGroup: Administration
ms.openlocfilehash: ccf9cc65cc5dc18d72ced490b18683a6a1af32ff
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408717"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Gerir o armazenamento de dados nas áreas de trabalho do Power BI

Saiba como pode gerir o armazenamento de dados na sua área de trabalho individual para que possa continuar a publicar relatórios e conjuntos de dados.

## <a name="capacity-limits"></a>Limites de capacidade

Os limites de armazenamento das áreas de trabalho, sejam para A Minha Área de trabalho ou uma área de trabalho de aplicação, dependem de se a área de trabalho está numa [capacidade Premium ou partilhada](../fundamentals/service-basic-concepts.md#capacities).

### <a name="shared-capacity-limits"></a>Limites de capacidade partilhada
Para áreas de trabalho numa capacidade partilhada: 

- Existe um limite de armazenamento de 10 GB por área de trabalho.
- Em áreas de trabalho de aplicações, a utilização total não pode exceder o limite de armazenamento do inquilino de 10 GB multiplicado pelo número de licenças Pro no inquilino.

### <a name="premium-capacity-limits"></a>Limites de capacidade Premium
Para áreas de trabalho na capacidade Premium:
- Existe um limite de 100 TB por capacidade Premium.
- Não existe um limite de armazenamento por utilizador.

Leia sobre outras funcionalidades do [modelo de preços do Power BI](https://powerbi.microsoft.com/pricing).

## <a name="whats-included-in-storage"></a>O que está incluído no armazenamento

São incluídos no armazenamento de dados os seus próprios conjuntos de dados e relatórios do Excel, assim como os itens que foram partilhados consigo. Os conjuntos de dados são as origens de dados que carregou ou às quais se ligou. Estas origens de dados incluem os ficheiros do Power BI Desktop e os livros do Excel que está a utilizar. O exemplo seguinte também está incluído na capacidade de dados.

* Intervalos do Excel afixados a um dashboard.
* Visualizações locais dos Reporting Services afixadas a um dashboard do Power BI.
* Imagens carregadas.

O tamanho de um dashboard que partilha varia consoante o que está afixado ao mesmo. Por exemplo, se afixar itens de dois relatórios que fazem parte de dois conjuntos de dados diferentes, o tamanho inclui ambos os conjuntos de dados.

## <a name="manage-items-you-own"></a>Gerir itens dos quais é proprietário

Veja a quantidade de armazenamento de dados que está a utilizar na sua conta do Power BI e faça a gestão da sua conta.

1. Para gerir o seu próprio armazenamento, aceda a **A Minha Área de Trabalho** no painel de navegação.
   
    ![Captura de ecrã a mostrar o painel de navegação, com A Minha Área de Trabalho destacada.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)

2. Selecione o ícone de engrenagem ![Ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) no canto superior direito **Gerir armazenamento pessoal**.
   
    A barra superior mostra o limite de armazenamento utilizado.
   
    ![Captura de ecrã a mostrar a opção Gerir limite de armazenamento, com a quantidade de armazenamento utilizada.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Os conjuntos de dados e os relatórios são separados em dois separadores:
   
    **Minha propriedade:** carregou estes relatórios e conjuntos de dados para a sua conta do Power BI, incluindo conjuntos de dados de serviços como o Salesforce e o Dynamics CRM.  

    **Propriedade de outros utilizadores:** outras pessoas partilharam os relatórios e conjuntos de dados consigo.
1. Para eliminar um conjunto de dados ou um relatório, selecione o ícone de caixote do lixo ![Ícone do caixote do lixo](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Tenha em atenção que tanto o utilizador como outra pessoa podem ter relatórios e dashboards com base num conjunto de dados. Se eliminar o conjunto de dados, os relatórios e dashboards deixarão de funcionar.

## <a name="manage-your-workspace"></a>Gerir a sua área de trabalho
1. Selecione a seta junto a **Áreas de trabalho** e selecione o nome da área de trabalho.
   
    ![Captura de ecrã a mostrar a seleção de Área de trabalho, com a área de trabalho Grupo de Vendas.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Selecione o ícone de engrenagem ![ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) no canto superior direito **Gerir armazenamento do grupo**.
   
    A barra superior mostra o limite de armazenamento de grupo utilizado.
   
    ![Captura de ecrã a mostrar a opção Gerir limite de armazenamento, com a quantidade de armazenamento utilizada pelo Grupo de Vendas.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Os conjuntos de dados e os relatórios são separados em dois separadores:
   
    **Nossa propriedade:** você ou outra pessoa carregou estes relatórios e conjuntos de dados para a conta do Power BI do grupo, incluindo conjuntos de dados de serviços como o Salesforce e o Dynamics CRM.

    **Propriedade de outros utilizadores:** outras pessoas partilharam os relatórios e conjuntos de dados com o seu grupo.

3. Para eliminar um conjunto de dados ou um relatório, selecione o ícone de caixote do lixo ![Ícone do caixote do lixo](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Tenha em mente que você ou outra pessoa do grupo pode ter relatórios e dashboards com base em um conjunto de dados. Se eliminar o conjunto de dados, os relatórios e dashboards deixarão de funcionar.
   
   Qualquer membro numa área de trabalho com a função de administrador, membro ou contribuidor tem permissões para eliminar conjuntos de dados e relatórios da área de trabalho.

## <a name="dataset-limits"></a>Limites do conjunto de dados
Existe um limite de 1 GB por conjunto de dados importado para o Power BI. Se tiver optado por manter a experiência do Excel, em vez de importar os dados, existe um limite de 250 MB para o conjunto de dados.

## <a name="what-happens-when-you-reach-a-limit"></a>O que acontece quando atinge um limite
Quando atinge o limite da capacidade de dados do que é possível fazer, são apresentados avisos dentro do serviço. 

Ao selecionar o ícone de engrenagem ![Ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), verá uma barra vermelha que indica que ultrapassou o limite da capacidade de dados.

![Captura de ecrã a mostrar a capacidade de armazenamento, a indicar que foi atingido o limite.](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Este limite também é indicado em **Gerir armazenamento pessoal**.

 ![Captura de ecrã a mostrar a capacidade de armazenamento pessoal, a indicar que o limite de armazenamento da Jane foi atingido.](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Ao tentar executar uma ação que atingirá um dos limites, verá uma mensagem a indicar que está acima do limite. Pode [gerir o seu armazenamento](#manage-items-you-own) para reduzir a quantidade de armazenamento e ultrapassar o limite.

 ![Captura de ecrã a mostrar a caixa de diálogo Excedeu o seu limite de armazenamento, a informar que os limites foram atingidos.](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 ## <a name="next-steps"></a>Próximos passos

 Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
