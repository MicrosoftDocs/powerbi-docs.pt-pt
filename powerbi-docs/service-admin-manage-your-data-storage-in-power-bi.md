---
title: Gerir o armazenamento de dados nas suas áreas de trabalho
description: Saiba como pode gerir o armazenamento de dados na sua área de trabalho individual para certificar-se de que pode continuar a publicar relatórios e conjuntos de dados.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: f8e7240b34e20a3d18443cadb5265c5d0d870790
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873646"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Gerir o armazenamento de dados nas áreas de trabalho do Power BI

Saiba como pode gerir o armazenamento de dados na sua área de trabalho individual para certificar-se de que pode continuar a publicar relatórios e conjuntos de dados.

Os utilizadores e as áreas de trabalho têm as suas próprias capacidades de dados:

* Todos os utilizadores têm um máximo de 10 GB de armazenamento de dados.
* Os utilizadores com uma licença do Power BI Pro podem criar áreas de trabalho com um máximo de 10 GB de armazenamento de dados em cada uma.
* Uma área de trabalho numa capacidade Premium não conta para o armazenamento de um utilizador do Power BI Pro.

Ao nível do inquilino, a utilização total não pode exceder os 10 GB por utilizador Pro em todos os utilizadores e áreas de trabalho Pro no inquilino.

Leia sobre outras funcionalidades do [modelo de preços do Power BI](https://powerbi.microsoft.com/pricing).

São incluídos no armazenamento de dados os seus próprios conjuntos de dados e relatórios do Excel, assim como os itens que foram partilhados consigo. Os conjuntos de dados são as origens de dados que carregou ou às quais se ligou. Estas origens de dados incluem os ficheiros do Power BI Desktop e os livros do Excel que está a utilizar. O exemplo seguinte também está incluído na capacidade de dados.

* Intervalos do Excel afixados ao dashboard.
* Visualizações locais dos Reporting Services afixadas a um dashboard do Power BI.
* Imagens carregadas.

O tamanho de um dashboard que partilha varia consoante o que está afixado ao mesmo. Por exemplo, se afixar itens de dois relatórios que fazem parte de dois conjuntos de dados diferentes, o tamanho inclui ambos os conjuntos de dados.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Gerir itens dos quais é proprietário

Veja a quantidade de armazenamento de dados que está a utilizar na sua conta do Power BI e faça a gestão da sua conta.

1. Para gerir o seu próprio armazenamento, aceda a **A Minha Área de Trabalho** no painel de navegação.
   
    ![A Minha Área de Trabalho](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Selecione o ícone de engrenagem ![Ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) no canto superior direito\> **Gerir armazenamento pessoal**.
   
    A barra superior mostra o limite de armazenamento utilizado.
   
    ![Gerir o limite de armazenamento](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Os conjuntos de dados e os relatórios são separados em dois separadores:
   
    **Minha Propriedade:** carregou estes relatórios e conjuntos de dados para a sua conta do Power BI, incluindo conjuntos de dados de serviços como o Salesforce e o Dynamics CRM.  
    **Propriedade de Outros Utilizadores:** outras pessoas partilharam os relatórios e conjuntos de dados consigo.
1. Para eliminar um conjunto de dados ou um relatório, selecione o ícone de caixote do lixo ![ícone de caixote do lixo](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Tenha em atenção que tanto o utilizador como outra pessoa podem ter relatórios e dashboards com base num conjunto de dados. Se eliminar o conjunto de dados, os relatórios e dashboards deixarão de funcionar.

## <a name="manage-your-workspace"></a>Gerir a sua área de trabalho
1. Selecione a seta junto a **Áreas de trabalho** \> selecione o nome da área de trabalho.
   
    ![Selecione uma área de trabalho](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Selecione o ícone de engrenagem ![ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) no canto superior direito\> **Gerir armazenamento do grupo**.
   
    A barra superior mostra o limite de armazenamento de grupo utilizado.
   
    ![Gerir o armazenamento da área de trabalho](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Os conjuntos de dados e os relatórios são separados em dois separadores:
   
    **Nossa Propriedade:** você ou outra pessoa carregou estes relatórios e conjuntos de dados para a conta do Power BI do grupo, incluindo conjuntos de dados de serviços como o Salesforce e o Dynamics CRM.
    **Propriedade de Outros Utilizadores:** outras pessoas partilharam os relatórios e conjuntos de dados com o seu grupo.
3. Para eliminar um conjunto de dados ou um relatório, selecione o ícone de caixote do lixo ![ícone de caixote do lixo](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Qualquer membro, com permissões de edição, de uma área de trabalho tem permissões para eliminar conjuntos de dados e relatórios da área de trabalho.
   > 
   > 

Tenha em mente que você ou outra pessoa do grupo pode ter relatórios e dashboards com base em um conjunto de dados. Se eliminar o conjunto de dados, os relatórios e dashboards deixarão de funcionar.

## <a name="dataset-limits"></a>Limites do conjunto de dados
Existe um limite de 1 GB por conjunto de dados importado para o Power BI. Se tiver optado por manter a experiência do Excel, em vez de importar os dados, existe um limite de 250 MB para o conjunto de dados.

## <a name="what-happens-when-you-reach-a-limit"></a>O que acontece quando atinge um limite
Quando atinge o limite da capacidade de dados do que é possível fazer, são apresentados avisos dentro do serviço. 

Ao selecionar o ícone de engrenagem ![ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), verá uma barra vermelha que indica que ultrapassou o limite da capacidade de dados.

![Limite de armazenamento atingido](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Este limite também é indicado em **Gerir armazenamento pessoal**.

 ![Gerir armazenamento pessoal, limite de armazenamento atingido](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Ao tentar executar uma ação que atingirá um dos limites, verá uma mensagem a indicar que está acima do limite. Pode [gerir](#manage) o armazenamento para reduzir a quantidade de armazenamento e ultrapassar o limite.

 ![Excedeu o limite de armazenamento](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

