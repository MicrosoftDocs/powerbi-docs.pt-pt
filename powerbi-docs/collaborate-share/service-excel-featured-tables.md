---
title: Aceder às tabelas em destaque do Power BI no Excel (pré-visualização)
description: No Excel, pode encontrar dados de tabelas em destaque nos conjuntos de dados do Power BI na Galeria de Tipos de Dados.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226358"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Aceder às tabelas em destaque do Power BI no Excel (pré-visualização)

No Excel, pode encontrar dados de tabelas em destaque nos conjuntos de dados do Power BI na Galeria de Tipos de Dados. As tabelas em destaque facilitam a adição de dados da empresa às folhas do Excel. Ao utilizar as capacidades dos conjuntos de dados certificados e promovidos do Power BI, as organizações permitem que mais utilizadores encontrem e utilizem dados relevantes e atualizáveis para tomar melhores decisões. Leia mais sobre a utilização de [tipos de dados do Excel no Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) na documentação do Excel.

A Galeria de Tipos de Dados apenas mostra as tabelas em destaque que um modelador organizou em conjuntos de dados do Power BI. Também pode procurar qualquer conjunto de dados no Excel a que tenha acesso no Power BI. No Excel, selecione a opção **Conjuntos de Dados do Power BI** em **Obter Dados** no friso **Dados**.

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>Aceder aos dados do Power BI através da Galeria de Tipos de Dados do Excel
As tabelas em destaque nos conjuntos de dados do Power BI são apresentadas na galeria de Tipos de Dados Excel no friso Dados.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Friso Dados do Excel":::

Quando expandida, a galeria mostra os principais tipos de dados disponíveis.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Galeria de Tipo de Dados do Excel":::
 
Para procurar dados numa tabela em destaque do Power BI, selecione uma célula ou um intervalo na folha do Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="Selecionar uma célula":::
 
Selecione a opção **Dados organizacionais** na galeria para procurar dados nas tabelas em destaque nos conjuntos de dados certificados a que tem acesso.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Dados Organizacionais do Excel":::
 
Selecione um tipo de dados específico se souber qual o tipo de dados que procura ou se não encontrar linhas correspondentes com a opção de Dados organizacionais.

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="Selecionar um tipo de dados":::
 
Durante a procura, se encontrar uma linha correspondente com um índice elevado de confiança, a célula será imediatamente associada a essa linha. O ícone do item associado indica que a célula está associada à linha no Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Ícone do Item associado":::

Se uma célula tiver várias potenciais linhas correspondentes, será mostrado um painel do seletor de dados. A célula mostra o ícone do ponto de interrogação, que abre o painel do seletor de dados dessa linha. Aqui está um exemplo depois de o utilizador ter selecionado um intervalo de A2:A7 e pesquisado uma tabela em destaque do Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="Várias possíveis linhas correspondentes":::

O painel **Seletor de Dados** mostra as linhas potencialmente correspondentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Painel do Seletor de Dados do Excel":::
 
A opção Dados organizacionais pode devolver linhas de vários tipos de dados. O Excel agrupa as linhas potencialmente correspondentes pela proveniência do tipo de dados. O Excel ordena os tipos de dados com base na linha de correspondência com o maior potencial. Utilize as setas de divisas para fechar e expandir os tipos de dados das linhas correspondentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Painel Seletor de Dados do Excel":::
 
Para cada linha, selecione o nome da linha para ver mais detalhes na linha e ajudá-lo a escolher a linha certa. Depois de encontrar a linha correta, prima **Selecionar** para associar a linha à célula no Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="Detalhes do Seletor de Dados":::
 
Quando uma linha é selecionada, a célula é associada à linha e o valor é mostrado com o valor do campo **Etiqueta da Linha** na tabela em destaque do Power BI. 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Item associado do Excel":::
 
Ao selecionar o ícone **Célula Associada**, é mostrado um cartão com dados de quaisquer campos e campos calculados na tabela em destaque. O título do cartão mostra o valor do campo da etiqueta de linha na tabela em destaque.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Detalhes do item associado":::

Selecione o ícone **Inserir Dados** para adicionar valores de campo à grelha.

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="Inserir dados"::: 

Selecione um nome de campo na lista de campos para adicionar o valor à grelha.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Selecionar um nome de campo":::

O valor do campo é colocado na célula adjacente. A fórmula da célula refere-se à célula associada e ao nome do campo, para que possa utilizar os dados nas funções do Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Fórmula da célula do Excel":::
 
Quando formata os dados como uma tabela do Excel, a adição de campos expande a tabela e define o cabeçalho da coluna para que corresponda ao nome do campo. As linhas associadas aos mesmos tipos de dados também são preenchidas com os respetivos valores.

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="O campo é o nome da coluna"::: 

## <a name="cell-formulas"></a>Fórmulas de célula

Quando utiliza uma tabela do Excel, pode consultar a coluna da tabela associada e, em seguida, adicionar campos de dados com a referência de `.` (ponto).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Referência de ponto do Excel":::

De igual forma, quando utiliza uma célula, pode consultar a célula e utilizar a referência de `.` (ponto) para recuperar os campos.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Referência de ponto da célula":::
 
## <a name="data-caching-and-refresh"></a>Colocação em cache e atualização dos dados

Quando o Excel associa uma célula a uma linha numa tabela em destaque do Power BI, este recupera e guarda todos os valores dos campos no ficheiro do Excel. Todas as pessoas com quem partilhar o ficheiro poderão consultar todos os campos, sem ter de pedir dados do Power BI.  

Utilize o botão **Atualizar Tudo** no friso **Dados** para atualizar os dados nas células associadas. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Atualizar Tudo":::
 
Também pode atualizar células individuais. Clique com o botão direito do rato na célula e selecione **Tipos de Dados** > **Atualizar**.

## <a name="show-a-card-change-or-convert-to-text"></a>Mostrar um cartão, alterar ou converter em texto

As células associadas adicionaram opções do menu de contexto. Clique com o botão direito do rato numa célula > selecione **Tipos de Dados** >  

- **Mostrar Cartão**
- **Atualização**
- **Alterar** 
- **Converter em Texto**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Clicar com o botão direito do rato, Converter em Texto":::
 
A opção **Converter em Texto** remove a associação à linha na tabela em destaque do Power BI. Mais importante, o texto na célula será o valor da etiqueta da linha da célula associada. Se tiver associado uma célula a uma linha que não pretendia, selecione **Anular** no Excel para restaurar os valores iniciais da célula.

## <a name="licensing"></a>Licensing
A Galeria de Tipos de Dados do Excel e as experiências ligadas para as tabelas em destaque do Power BI apenas estão disponíveis para clientes do Excel E5 e G5. 

## <a name="security"></a>Segurança

Vê apenas tabelas em destaque a partir dos conjuntos de dados aos quais tem permissão no Power BI. Ao atualizar os dados, deve ter permissão para aceder ao conjunto de dados no Power BI para recuperar as linhas. Tal requer a permissão de Compilação ou de Escrita no conjunto de dados. O Excel coloca em cache os dados devolvidos de toda a linha. Qualquer pessoa com quem partilhe o ficheiro Excel pode ver os dados de todos os campos em todas as células associadas.

Se um conjunto de dados do Power BI tiver segurança ao nível da linha ou uma etiqueta de confidencialidade do Microsoft Information Protection aplicada, as tabelas em destaque desse conjunto de dados não serão incluídas na Galeria de Tipos de Dados do Excel. Esta é uma limitação da pré-visualização inicial.

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>Organizar uma tabela em destaque no Power BI Desktop
A Galeria de Tipos de Dados do Excel mostra as tabelas em destaque nos conjuntos de dados carregados para o serviço Power BI. Utilize o Power BI Desktop para organizar as tabelas em destaque no modelo de dados e, em seguida, carregue-as para o serviço Power BI.

### <a name="turn-on-the-featured-table-preview"></a>Ativar a pré-visualização da tabela em destaque

1. No Power BI Desktop, selecione **Ficheiro** > **Opções e Definições** > **Opções** > **Funcionalidades de Pré-visualização**.
2. Selecione a caixa de verificação **Tabelas em destaque**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Opção das tabelas em destaque de pré-visualização":::

### <a name="select-a-table"></a>Selecionar uma tabela

1. No Power BI Desktop, aceda à Vista de modelo.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Vista de modelo":::
 
2. Selecione uma tabela e defina **É tabela em destaque** como **Sim**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Definir É tabela em destaque como Sim":::

4. Em **Configurar esta tabela em destaque**, preencha os campos obrigatórios:

    - Uma **Descrição**.
    - O valor do campo **Etiqueta da linha** é utilizado no Excel para que os utilizadores possam identificar facilmente a linha. Aparece como o valor da célula de uma célula associada, no painel **Seletor de Dados** e no cartão **Informações**. 
    - O valor do campo **Coluna-chave** apresenta o ID exclusivo da linha. Este valor permite ao Excel associar uma célula a uma linha específica na tabela.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Configurar tabela em destaque":::

Depois de publicar ou importar o conjunto de dados para o serviço Power BI, a tabela em destaque será apresentada na Galeria de Tipos de Dados do Excel.

- O Excel coloca a lista de tipos de dados em cache, por isso, tem de reiniciar o Excel para ver as tabelas em destaque recém-publicadas.
- Alguns conjuntos de dados não são suportados na pré-visualização, as tabelas em destaque definidas nestes conjuntos de dados não serão apresentadas no Excel. Veja as considerações e limitações para obter mais detalhes.

## <a name="administrative-control"></a>Controlo administrativo

Os administradores do Power BI podem controlar quem na organização pode utilizar as tabelas em destaque na Galeria de Tipos de Dados do Excel. Para obter mais detalhes, veja [Definições das tabelas em destaque](../admin/service-admin-portal.md#featured-tables-settings) no artigo do Portal de administração. 
 
### <a name="auditing"></a>Auditoria

Os registos de auditoria de administração mostram estes eventos das tabelas em destaque:

- **AnalyzedByExternalApplication**: dá visibilidade aos administradores nos quais os utilizadores estão a aceder às tabelas em destaque.
- **UpdateFeaturedTables**: dá visibilidade aos administradores nos quais os utilizadores estão a publicar e atualizar as tabelas em destaque.

Para obter uma lista completa de eventos de registo de auditoria, veja [Controlar as atividades dos utilizadores no Power BI](../admin/service-admin-auditing.md).

## <a name="considerations-and-limitations"></a>Considerações e limitações

Veja a seguir as limitações da pré-visualização inicial:

- A integração está disponível nas Compilações do Excel Insiders.
- A Galeria de Tipos de Dados do Excel inclui tabelas em destaque para utilizadores com a licença adequada no Power BI Desktop e no serviço Power BI. O suporte do serviço Power BI pode não estar disponível no lançamento da pré-visualização, mas será adicionado.
- As tabelas em destaque nos conjuntos de dados do Power BI que utilizam as seguintes capacidades não são mostradas no Excel: 

    - Conjuntos de dados de segurança ao nível da linha.
    - Conjuntos de dados ativados do Microsoft Information Protection.
    - Conjuntos de dados do DirectQuery.
    - Conjuntos de dados com uma ligação dinâmica.

- O Excel mostra apenas os dados em colunas e colunas calculadas na tabela em destaque. As seguintes opções não são disponibilizadas na pré-visualização inicial:

    - Medidas definidas na tabela de recursos.
    - Medidas definidas em tabelas relacionadas e medidas implícitas calculadas a partir de relações.

- O Excel apresenta apenas tabelas em destaque que são armazenadas nas novas áreas de trabalho do Power BI. As tabelas em destaque armazenadas nas áreas de trabalho clássicas, ou em A Minha Área de Trabalho, não são mostradas como tipos de dados no Excel. Pode [atualizar as áreas de trabalho clássicas para as novas áreas de trabalho](service-upgrade-workspaces.md) no Power BI.

A experiência de Tipos de Dados no Excel é semelhante a uma função de pesquisa. Obtém um valor de célula proporcionado pela folha do Excel e procura linhas correspondentes nas tabelas em destaque do Power BI. A experiência de pesquisa tem os seguintes comportamentos:

- Ao utilizar o botão **Dados Organizacionais** para pesquisar, o Excel procura apenas em tabelas em destaque nos Conjuntos de dados certificados.
- A correspondência de linhas baseia-se nas colunas de texto na tabela em destaque. Utiliza a mesma indexação que a capacidade de Perguntas e Respostas do Power BI, que está otimizada para a pesquisa em inglês. A pesquisa noutros idiomas pode não produzir correspondências precisas. As colunas numéricas não são consideradas para correspondência.
- A correspondência baseia-se nas correspondências Exatas e de Prefixo dos termos de pesquisa individuais. O valor de uma célula é dividido com base nos espaços ou noutros caracteres de espaço em branco, como separadores. Em seguida, cada palavra é considerada um termo de pesquisa. Os valores de campo de texto de uma linha são comparados a cada termo de pesquisa para correspondências Exatas e de Prefixo. Será devolvida uma correspondência de Prefixo se o campo de texto da linha começar com o termo de pesquisa. Por exemplo, se uma célula tiver “Orange County”, “Orange” e “County” serão termos de pesquisa distintos. 

    - São devolvidas as linhas com colunas de texto cujo valor corresponde exatamente a “Orange” ou “County”. 
    - São devolvidas as linhas com colunas de texto cujo valor começa com “Orange” ou “County”. 
    - Mais importante, as linhas que contêm “Orange” ou “County”, mas que não começam com esses termos, não são devolvidas.

- O Power BI devolve, no máximo, 100 sugestões de linhas para cada célula.
- A definição ou atualização da tabela em destaque não é suportada no ponto final XMLA.
- Pode utilizar os ficheiros do Excel com um modelo de dados para publicar tabelas em destaque. Carregue os dados no ambiente de trabalho do Power BI e, em seguida, publique a tabela em destaque.
- Alterar o Nome da tabela, a Etiqueta da Linha ou a Coluna-Chave da tabela em destaque pode afetar os utilizadores do Excel com células associadas a linhas na tabela. 
- O Excel mostra quando os dados foram recuperados do conjunto de dados do Power BI. Este não é necessariamente o momento em que os dados foram atualizados no Power BI ou a hora do ponto de dados mais recente num conjunto de dados. Por exemplo, digamos que um conjunto de dados no Power BI foi atualizado há uma semana, mas os dados de origem subjacentes tinham uma semana quando ocorreu a atualização. Os dados reais teriam duas semanas, mas o Excel mostraria os dados recuperados com a data/hora na qual os dados foram solicitados para o Excel.

## <a name="next-steps"></a>Próximos passos

- Perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

