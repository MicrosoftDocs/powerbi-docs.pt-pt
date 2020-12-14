---
title: Definir tabelas em destaque no Power BI Desktop
description: Crie tabelas em destaque no Power BI Desktop para que apareçam na Galeria de Tipos de Dados da Organização do Excel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906894"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>Defina tabelas em destaque no Power BI Desktop para aparecerem na Galeria de Tipos de Dados da Organização do Excel.

Na Galeria de Tipos de Dados no Excel, os utilizadores podem encontrar dados de *tabelas em destaque* nos conjuntos de dados do Power BI. Neste artigo, irá aprender a definir tabelas como *em destaque* nos seus conjuntos de dados. Estas etiquetas facilitam a adição de dados da empresa às folhas do Excel. Aqui estão os passos básicos para definir e partilhar tabelas em destaque.

1. Identifique tabelas em destaque nos seus conjuntos de dados no Power BI Desktop (este artigo).
1. Guarde esses conjuntos de dados com tabelas em destaque numa das novas áreas de trabalho. Os criadores de relatórios podem criar relatórios com essas tabelas em destaque. 
1. O resto da organização pode ligar-se a essas tabelas em destaque, referidas como *tipos de dados* no Excel, para obter dados relevantes e atualizáveis. O artigo [Aceder às tabelas em destaque do Power BI no Excel](service-excel-featured-tables.md) descreve a utilização destas tabelas em destaque no Excel.

> [!NOTE]
> Pode [promover ou certificar conjuntos de dados no Power BI](../collaborate-share/service-endorse-content.md). A isso chama-se *recomendação*. O Excel dá prioridade a tabelas em conjuntos de dados recomendados na Galeria de Tipos de Dados. O Excel apresenta as tabelas em conjuntos de dados certificados em primeiro lugar e depois as tabelas em conjuntos de dados promovidos. Posteriormente, o Excel apresenta as tabelas em conjuntos de dados não recomendados. 

> [!NOTE]
> A partir da versão de dezembro de 2020 do Power BI Desktop, a criação de tabelas em destaque está disponível por predefinição. Se estiver a utilizar uma versão mais antiga, atualize o Power BI Desktop ou ative a funcionalidade **Tabelas em destaque** através de **Ficheiro** > **Opções e Definições** > **Opções** > **Funcionalidades de Pré-visualização**.

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
    - Alguns conjuntos de dados não são suportados. As tabelas em destaque definidas nesses conjuntos de dados não serão apresentadas no Excel. Para obter mais detalhes, veja a secção seguinte Considerações e limitações.

## <a name="considerations-and-limitations"></a>Considerações e limitações

Eis as limitações atuais:

- A integração está disponível no Excel no canal atual.
- As tabelas em destaque nos conjuntos de dados do Power BI que utilizam as seguintes capacidades não são mostradas no Excel: 

    - Conjuntos de dados do DirectQuery.
    - Conjuntos de dados com uma ligação dinâmica.

- O Excel mostra apenas os dados em colunas, colunas calculadas e medidas definidas na tabela em destaque. Não é fornecido o seguinte:
   
    - As medidas definidas em tabelas relacionadas.
    - As medidas implícitas calculadas a partir de relações.

- O Excel apresenta apenas tabelas em destaque (*tipos de dados*) que são armazenadas nas novas áreas de trabalho do Power BI. As tabelas em destaque armazenadas nas áreas de trabalho clássicas não são mostradas como tipos de dados no Excel. Pode [atualizar as áreas de trabalho clássicas para as novas áreas de trabalho](service-upgrade-workspaces.md) no Power BI.

A experiência de Tipos de Dados no Excel é semelhante a uma função de pesquisa. Obtém um valor de célula proporcionado pela folha do Excel e procura linhas correspondentes nas tabelas em destaque do Power BI. A experiência de pesquisa tem os seguintes comportamentos:

- A correspondência de linhas baseia-se nas colunas de texto na tabela em destaque. Utiliza a mesma indexação que a capacidade de Perguntas e Respostas do Power BI, que está otimizada para a pesquisa em inglês. A pesquisa noutros idiomas pode não produzir correspondências precisas. 
- A maioria das colunas numéricas não é considerada para correspondência. Se a Etiqueta de Linha ou Coluna de Chave for numérica, é incluída para correspondência.
- A correspondência baseia-se nas correspondências Exatas e de Prefixo dos termos de pesquisa individuais. O valor de uma célula é dividido com base nos espaços ou noutros caracteres de espaço em branco, como separadores. Em seguida, cada palavra é considerada um termo de pesquisa. Os valores de campo de texto de uma linha são comparados a cada termo de pesquisa para correspondências Exatas e de Prefixo. Será devolvida uma correspondência de Prefixo se o campo de texto da linha começar com o termo de pesquisa. Por exemplo, se uma célula tiver “Orange County”, “Orange” e “County” serão termos de pesquisa distintos. 

    - São devolvidas as linhas com colunas de texto cujo valor corresponde exatamente a "Orange" ou "County". 
    - São devolvidas as linhas com colunas de texto cujo valor corresponde exatamente a "Orange" ou "County". 
    - Mais importante, as linhas que contêm “Orange” ou “County”, mas que não começam com esses termos, não são devolvidas.

- O Power BI devolve, no máximo, 100 sugestões de linhas para cada célula.
- Alguns símbolos não são suportados.
- A definição ou atualização da tabela em destaque não é suportada no ponto final XMLA.
- Pode utilizar os ficheiros do Excel com um modelo de dados para publicar tabelas em destaque. Carregue os dados no Power BI Desktop e, em seguida, publique a tabela em destaque.
- Alterar o Nome da tabela, a Etiqueta da Linha ou a Coluna de Chave da tabela em destaque pode afetar os utilizadores do Excel com células associadas a linhas na tabela. 
- O Excel mostra quando os dados foram recuperados do conjunto de dados do Power BI. Este não é necessariamente o momento em que os dados foram atualizados no Power BI ou a hora do ponto de dados mais recente num conjunto de dados. Por exemplo, digamos que um conjunto de dados no Power BI foi atualizado há uma semana, mas os dados de origem subjacentes tinham uma semana quando ocorreu a atualização. Os dados reais teriam duas semanas, mas o Excel mostraria os dados recuperados com a data/hora na qual os dados foram solicitados para o Excel.
- Para outras considerações sobre o Excel, veja [Considerações e limitações](service-excel-featured-tables.md#considerations-and-limitations) no artigo "Aceder às tabelas em destaque do Power BI no Excel".

## <a name="next-steps"></a>Próximos passos

- [Aceder às tabelas em destaque do Power BI no Excel](service-excel-featured-tables.md)
- Leia mais sobre a utilização de [tipos de dados do Excel no Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) na documentação do Excel.
- Perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

