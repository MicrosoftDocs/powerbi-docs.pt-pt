---
title: Definir tabelas em destaque no Power BI Desktop (pré-visualização)
description: Crie tabelas em destaque no Power BI Desktop para que apareçam na Galeria de Tipos de Dados no Excel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: d2d87f16b8100424b47277360354d79ee834d467
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411937"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Definir tabelas em destaque no Power BI Desktop (pré-visualização)

Na Galeria de Tipos de Dados no Excel, os utilizadores podem encontrar dados de *tabelas em destaque* nos conjuntos de dados do Power BI. Neste artigo, irá aprender a definir tabelas como *em destaque* nos seus conjuntos de dados. Estas etiquetas facilitam a adição de dados da empresa às folhas do Excel. Aqui estão os passos básicos para definir e partilhar tabelas em destaque.

1. Identifique tabelas em destaque nos seus conjuntos de dados no Power BI Desktop (este artigo).
1. Guarde esses conjuntos de dados com tabelas em destaque numa das novas áreas de trabalho. Os criadores de relatórios podem criar relatórios com essas tabelas em destaque. 
1. O resto da organização pode ligar-se a essas tabelas em destaque, referidas como *tipos de dados* no Excel, para obter dados relevantes e atualizáveis. O artigo [Aceder às tabelas em destaque do Power BI no Excel (pré-visualização)](service-excel-featured-tables.md) descreve a utilização destas tabelas em destaque no Excel.

> [!NOTE]
> Pode [promover ou certificar conjuntos de dados no Power BI](../collaborate-share/service-endorse-content.md). A isso chama-se *recomendação*. O Excel dá prioridade a tabelas em conjuntos de dados recomendados na Galeria de Tipos de Dados. O Excel apresenta as tabelas em conjuntos de dados certificados em primeiro lugar e depois as tabelas em conjuntos de dados promovidos. Posteriormente, o Excel apresenta as tabelas em conjuntos de dados não recomendados. 

## <a name="turn-on-the-featured-table-preview"></a>Ativar a pré-visualização da tabela em destaque

1. No Power BI Desktop, selecione **Ficheiro** > **Opções e Definições** > **Opções** > **Funcionalidades de Pré-visualização**.
2. Selecione a caixa de verificação **Tabelas em destaque**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Opção das tabelas em destaque de pré-visualização":::

3. Reiniciar o Power BI Desktop.

## <a name="select-a-table"></a>Selecionar uma tabela

1. No Power BI Desktop, aceda à Vista de modelo.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Vista de modelo":::
 
2. Selecione uma tabela e defina **É tabela em destaque** como **Sim**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Definir É tabela em destaque como Sim":::

4. Em **Configurar esta tabela em destaque**, preencha os campos obrigatórios:

    - Uma **Descrição**. 
        > [!TIP]
        > Inicie a descrição com "Tabela em destaque" para ajudar os criadores de relatórios do Power BI a identificá-la.
    - O valor do campo **Etiqueta da linha** é utilizado no Excel para que os utilizadores possam identificar facilmente a linha. Aparece como o valor da célula de uma célula associada, no painel **Seletor de Dados** e no cartão **Informações**. 
    - O valor do campo **Coluna-chave** apresenta o ID exclusivo da linha. Este valor permite ao Excel associar uma célula a uma linha específica na tabela.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Configurar tabela em destaque":::

1. Depois de publicar ou importar o conjunto de dados para o serviço Power BI, a tabela em destaque será apresentada na Galeria de Tipos de Dados do Excel. Você e outros criadores de relatórios também podem criar relatórios baseados neste conjunto de dados.

1. No Excel: 
    - O Excel coloca a lista de tipos de dados em cache, por isso, tem de reiniciar o Excel para ver as tabelas em destaque recém-publicadas.
    - Alguns conjuntos de dados não são suportados na pré-visualização, as tabelas em destaque definidas nestes conjuntos de dados não serão apresentadas no Excel. Para obter mais detalhes, veja a secção seguinte Considerações e limitações.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Veja a seguir as limitações da pré-visualização inicial.

- As tabelas em destaque nos conjuntos de dados do Power BI que utilizam as seguintes capacidades não são mostradas no Excel:

    - Conjuntos de dados do DirectQuery.
    - Conjuntos de dados com uma ligação dinâmica.

- O Excel mostra apenas os dados em colunas e colunas calculadas na tabela em destaque. As medidas definidas em tabelas relacionadas e as medidas implícitas calculadas a partir de relações não fazem parte da pré-visualização.
- O Excel apresenta apenas tabelas em destaque que são armazenadas nas novas áreas de trabalho do Power BI. As tabelas em destaque armazenadas nas áreas de trabalho clássicas não são mostradas como tipos de dados no Excel. Pode [atualizar as áreas de trabalho clássicas para as novas áreas de trabalho](service-upgrade-workspaces.md) no Power BI.
- Para outras considerações sobre o Excel, veja [Considerações e limitações](service-excel-featured-tables.md#considerations-and-limitations) no artigo "Aceder às tabelas em destaque do Power BI no Excel".

## <a name="next-steps"></a>Próximos passos

- [Aceder às tabelas em destaque do Power BI no Excel](service-excel-featured-tables.md)
- Leia mais sobre a utilização de [tipos de dados do Excel no Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) na documentação do Excel.
- Perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

