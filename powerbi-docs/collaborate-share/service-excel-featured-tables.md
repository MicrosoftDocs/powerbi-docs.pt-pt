---
title: Aceder às tabelas em destaque do Power BI no Excel (pré-visualização)
description: No Excel, pode encontrar dados de tabelas em destaque nos conjuntos de dados do Power BI na Galeria de Tipos de Dados.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 08/04/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 95ccc80a37ad9703c60c82ce928d35b5e301947b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407314"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Aceder às tabelas em destaque do Power BI no Excel (pré-visualização)

*As tabelas em destaque* são uma forma de ligar os seus dados no Excel a dados no Power BI. Facilitam a adição de dados da empresa a folhas do Excel. No Excel, pode encontrar dados de tabelas em destaque nos conjuntos de dados do Power BI na Galeria de Tipos de Dados. Este artigo explica como.

Cria conjuntos de dados no Power BI? Leia sobre como [definir tabelas em destaque no Power BI Desktop](service-create-excel-featured-tables.md).

> [!NOTE]
> No Excel, também pode analisar dados de qualquer conjunto de dados a que tenha acesso no Power BI. Para obter mais detalhes, veja [Outras formas de aceder aos conjuntos de dados do Power BI a partir do Excel](service-analyze-in-excel.md#other-ways-to-access-power-bi-datasets-from-excel) no artigo "Analisar no Excel para o Power BI".
> 

## <a name="the-excel-data-types-gallery"></a>A Galeria de Tipo de Dados do Excel
As tabelas em destaque nos conjuntos de dados do Power BI são apresentadas como *tipos de dados* no friso **Dados**, na galeria de **Tipos de Dados** do Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Captura de ecrã a mostrar a galeria de Tipos de Dados, no friso Dados do Excel":::.

Quando expandida, a galeria mostra os tipos de dados genéricos, como **Ações** e **Geografia**, mais os 10 principais tipos de dados **Organização** que estão disponíveis para si: tabelas em destaque dos conjuntos de dados do Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Captura de ecrã a mostrar a Galeria de Tipo de Dados do Excel":::.

## <a name="search-for-power-bi-data-in-the-data-types-gallery"></a>Procurar dados do Power BI na Galeria de Tipos de Dados

Para procurar dados numa tabela em destaque no Power BI, selecione uma célula ou um intervalo na sua folha do Excel que contenha um valor que corresponda ao valor de uma tabela em destaque. Selecione a seta **Mais** junto à galeria de Tipos de Dados.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-more.png" alt-text="Captura de ecrã a mostrar o ícone Mais na Galeria de Tipos de Dados do Excel.":::

Se encontrar a tabela que procura, selecione-a. Caso contrário, selecione **Mais da organização**. O Excel irá procurar todas as tabelas em destaque a que tem acesso, à procura de uma correspondência.

:::image type="content" source="media/service-excel-featured-tables/excel-more-your-organization.png" alt-text="Captura de ecrã da seleção de Da organização (pré-visualização).":::
 
O Excel apresenta todas as tabelas possíveis. No painel **Seletor de Dados**, escreva na caixa **Filtrar** para reduzir as suas opções. Selecione a tabela correspondente.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-store.png" alt-text="Captura de ecrã a mostrar Dados Organizacionais do Excel, tabela de tipo de dados Fornecedores":::.
 
Se o Excel encontrar linhas correspondentes com um índice elevado de confiança, as células serão imediatamente associadas a essas linhas. O ícone do item associado indica que as células estão associadas às linhas no Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="Captura de ecrã a mostrar o ícone Item associado":::.

Se uma célula tiver mais do que uma potencial linha de correspondência, apresentará um ícone de ponto de interrogação e será apresentado o painel **Seletor de Dados**. No exemplo seguinte, o utilizador selecionou um intervalo de B3:B9 e selecionou a tabela em destaque do Power BI **Arquivo**. Todas as linhas tinham correspondência, exceto a célula B9, "508 – Pasadena Lindseys". O **Seletor de Dados** mostra duas correspondências possíveis, o mesmo valor em duas tabelas diferentes.

:::image type="content" source="media/service-excel-featured-tables/excel-question-mark-featured-table.png" alt-text="Captura de ecrã a mostrar o painel Seletor de Dados do Excel":::.
 
A opção Dados da organização pode devolver linhas de múltiplas tabelas em destaque. O Excel agrupa as linhas potencialmente correspondentes pela proveniência do tipo de dados. O Excel ordena os tipos de dados com base na linha de correspondência com o maior potencial. Utilize as setas de divisas para fechar e expandir os tipos de dados das linhas correspondentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Captura de ecrã a mostrar o painel Seletor de Dados do Excel, com múltiplas possibilidades":::.
 
Para cada sugestão, selecione o nome da linha no painel do **Seletor de Dados** para ver mais detalhes na linha, de modo a ajudá-lo a escolher a linha certa. Depois de a encontrar, prima **Selecionar** para associar a linha à célula no Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="Captura de ecrã a mostrar os detalhes do Seletor de Dados":::.

## <a name="explore-related-data"></a>Explorar dados relacionados

Agora que criou a ligação entre os valores na sua folha do Excel e os dados na tabela em destaque do Power BI, pode explorar esses dados. Utilize os dados para melhorar os seus relatórios do Excel.

### <a name="view-related-data-in-a-card"></a>Ver dados relacionados num cartão 
 
Selecione o ícone **Cartão** na célula para mostrar um cartão com os dados de todos os campos e os campos calculados na tabela em destaque. O título do cartão mostra o valor do campo da etiqueta de linha na tabela em destaque.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Captura de ecrã a mostrar a opção Detalhes do item associado":::.

### <a name="insert-related-data-from-power-bi"></a>Inserir dados relacionados a partir do Power BI 

Selecione o ícone **Inserir Dados** e, em seguida, selecione um nome de campo na lista de campos para adicionar o valor à grelha.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Captura de ecrã a mostrar a opção Selecionar um nome de campo":::.

Os valores do campo são colocados nas células adjacentes. A fórmula da célula refere-se à célula associada e ao nome do campo, para que possa utilizar os dados nas funções do Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Captura de ecrã a mostrar a fórmula da célula do Excel":::.

### <a name="use-cell-formulas"></a>Utilizar fórmulas de célula

Numa tabela do Excel, pode consultar a coluna da tabela associada e, em seguida, adicionar campos de dados com a referência de `.` (ponto final).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Captura de ecrã a mostrar a referência de ponto do Excel":::.

De igual forma, numa célula, pode consultar a célula e utilizar a referência de `.` (ponto final) para recuperar os campos.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Captura de ecrã a mostrar a referência de ponto da célula":::.

### <a name="show-a-card-change-or-convert-to-text"></a>Mostrar um cartão, alterar ou converter em texto

As células associadas adicionaram opções do menu de contexto. Clique com o botão direito do rato numa célula. Juntamente com as opções habituais, também verá:

- **Show Data Type Card** (Mostrar Cartão de Tipo de Dados).
- **Tipo de Dados** > **Converter em Texto**.
- **Tipo de Dados** > **Alterar**.
- **Atualizar**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Captura de ecrã a mostrar a ação de clicar com o botão direito do rato e a opção Converter em Texto":::.
 
A opção **Converter em Texto** remove a associação à linha na tabela em destaque do Power BI. Mais importante, o texto na célula será o valor da etiqueta da linha da célula associada. Se tiver associado uma célula a uma linha que não pretendia, selecione **Anular** no Excel para restaurar os valores iniciais da célula.
 
## <a name="data-caching-and-refresh"></a>Colocação em cache e atualização dos dados

Quando o Excel associa uma célula a uma linha numa tabela em destaque do Power BI, este recupera e guarda todos os valores dos campos no ficheiro do Excel. Todas as pessoas com quem partilhar o ficheiro poderão consultar todos os campos, sem ter de pedir dados do Power BI.  

Utilize o botão **Atualizar Tudo** no friso **Dados** para atualizar os dados nas células associadas. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Captura de ecrã a mostrar a opção Atualizar Tudo":::.
 
Também pode atualizar células individuais. Clique com o botão direito do rato na célula e selecione **Tipos de Dados** > **Atualizar**.

## <a name="licensing"></a>Licensing

A Galeria de Tipos de Dados do Excel e as experiências ligadas para as tabelas em destaque do Power BI apenas estão disponíveis para clientes do Excel E5 e G5. 

## <a name="security"></a>Segurança

Vê apenas tabelas em destaque a partir dos conjuntos de dados aos quais tem permissão no Power BI. Ao atualizar os dados, deve ter permissão para aceder ao conjunto de dados no Power BI para recuperar as linhas. Precisa de [permissão de Compilação ou de Escrita no conjunto de dados](../connect-data/service-datasets-build-permissions.md) no Power BI.
 
O Excel coloca em cache os dados devolvidos de toda a linha. Qualquer pessoa com quem partilhe o ficheiro Excel pode ver os dados de todos os campos em todas as células associadas.

Se um conjunto de dados do Power BI tiver segurança ao nível da linha ou uma etiqueta de confidencialidade do Microsoft Information Protection aplicada, as tabelas em destaque desse conjunto de dados não serão incluídas na Galeria de Tipos de Dados do Excel. Esta é uma limitação da pré-visualização inicial.

## <a name="administrative-control"></a>Controlo administrativo

Os administradores do Power BI podem controlar quem na organização pode utilizar as tabelas em destaque na Galeria de Tipos de Dados do Excel. Consulte [Permitir ligações a tabelas em destaque](../admin/service-admin-portal.md#allow-connections-to-featured-tables) no artigo do Portal de administração para obter mais detalhes. 
 
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

- O Excel apresenta apenas tabelas em destaque (*tipos de dados*) que são armazenadas nas novas áreas de trabalho do Power BI. As tabelas em destaque armazenadas nas áreas de trabalho clássicas, ou em A Minha Área de Trabalho, não são mostradas como tipos de dados no Excel. Pode [atualizar as áreas de trabalho clássicas para as novas áreas de trabalho](service-upgrade-workspaces.md) no Power BI.

A experiência de Tipos de Dados no Excel é semelhante a uma função de pesquisa. Obtém um valor de célula proporcionado pela folha do Excel e procura linhas correspondentes nas tabelas em destaque do Power BI. A experiência de pesquisa tem os seguintes comportamentos:

- Ao utilizar o botão **Dados Organizacionais** para procurar, o Excel procura apenas em tabelas em destaque nos conjuntos de dados do Power BI.
- A correspondência de linhas baseia-se nas colunas de texto na tabela em destaque. Utiliza a mesma indexação que a capacidade de Perguntas e Respostas do Power BI, que está otimizada para a pesquisa em inglês. A pesquisa noutros idiomas pode não produzir correspondências precisas. As colunas numéricas não são consideradas para correspondência.
- A correspondência baseia-se nas correspondências Exatas e de Prefixo dos termos de pesquisa individuais. O valor de uma célula é dividido com base nos espaços ou noutros caracteres de espaço em branco, como separadores. Em seguida, cada palavra é considerada um termo de pesquisa. Os valores de campo de texto de uma linha são comparados a cada termo de pesquisa para correspondências Exatas e de Prefixo. Será devolvida uma correspondência de Prefixo se o campo de texto da linha começar com o termo de pesquisa. Por exemplo, se uma célula tiver “Orange County”, “Orange” e “County” serão termos de pesquisa distintos. 

    - São devolvidas as linhas com colunas de texto cujo valor corresponde exatamente a "Orange" ou "County". 
    - São devolvidas as linhas com colunas de texto cujo valor corresponde exatamente a "Orange" ou "County". 
    - Mais importante, as linhas que contêm “Orange” ou “County”, mas que não começam com esses termos, não são devolvidas.

- O Power BI devolve, no máximo, 100 sugestões de linhas para cada célula.
- A definição ou atualização da tabela em destaque não é suportada no ponto final XMLA.
- Pode utilizar os ficheiros do Excel com um modelo de dados para publicar tabelas em destaque. Carregue os dados no ambiente de trabalho do Power BI e, em seguida, publique a tabela em destaque.
- Alterar o Nome da tabela, a Etiqueta da Linha ou a Coluna-Chave da tabela em destaque pode afetar os utilizadores do Excel com células associadas a linhas na tabela. 
- O Excel mostra quando os dados foram recuperados do conjunto de dados do Power BI. Este não é necessariamente o momento em que os dados foram atualizados no Power BI ou a hora do ponto de dados mais recente num conjunto de dados. Por exemplo, digamos que um conjunto de dados no Power BI foi atualizado há uma semana, mas os dados de origem subjacentes tinham uma semana quando ocorreu a atualização. Os dados reais teriam duas semanas, mas o Excel mostraria os dados recuperados com a data/hora na qual os dados foram solicitados para o Excel.

## <a name="next-steps"></a>Próximos passos

- [Definir tabelas em destaque no Power BI Desktop](service-create-excel-featured-tables.md)
- Leia mais sobre a utilização de [tipos de dados do Excel no Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) na documentação do Excel.
- Perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

