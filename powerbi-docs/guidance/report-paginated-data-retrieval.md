---
title: Orientação para a obtenção de dados para relatórios paginados
description: Orientação para a criação de origens de dados e conjuntos de dados para relatórios paginados do Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 067171f7ec74beccdb5a312c1cac5bbc6c87541f
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377656"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Orientação para a obtenção de dados para relatórios paginados

O presente artigo destina-se a si, na qualidade de autor de relatório que cria [relatórios paginados](../paginated-reports/paginated-reports-report-builder-power-bi.md) do Power BI. Fornece recomendações para o ajudar a conceber uma obtenção de dados eficaz e eficiente.

## <a name="data-source-types"></a>Tipos de origem de dados

Os relatórios paginados suportam nativamente origens de dados relacionais e analíticos. Estas origens são ainda categorizadas como sendo com base na cloud ou no local. As origens de dados no local (estejam alojadas no local ou numa máquina virtual) requerem um gateway de dados para possibilitar a ligação ao Power BI. Com base na cloud significa que é possível ligar diretamente ao Power BI através de uma ligação à Internet.

Se puder escolher o tipo de origem de dados (possivelmente no caso de um novo projeto), recomendamos que utilize origens de dados com base na cloud. Os relatórios paginados permitem uma ligação com uma latência de rede mais baixa, especialmente quando as origens de dados residem na mesma região do seu inquilino do Power BI. É igualmente possível ligar a estas origens através do Início de Sessão Único (SSO). Isto significa que a identidade do utilizador do relatório pode fluir para a origem de dados, permitindo a imposição de permissões ao nível da linha por utilizador. Atualmente, o SSO não é suportado para origens de dados no local (o que significa que o SQL Server Analysis Services não pode impor permissões ao nível da linha por utilizador).

> [!NOTE]
> Embora não seja atualmente possível ligar a bases de dados no local através do SSO, ainda pode impor permissões ao nível da linha. Tal é feito através da passagem do campo incorporado **UserID** para um parâmetro de consulta de conjunto de dados. A origem de dados terá de armazenar os valores do Nome Principal de Utilizador (UPN) de forma a que possa filtrar corretamente os resultados da consulta.
>
> Por exemplo, considere que cada representante de vendas é armazenado numa linha na tabela **Representante de Vendas**.  A tabela tem colunas para o UPN, bem como a região de vendas do representante. Na altura da consulta, a tabela é filtrada pelo UPN do utilizador do relatório e relacionada a factos de vendas através de uma associação interna. Desta forma, a consulta filtra de forma eficaz as linhas de factos de vendas associadas à região de vendas do utilizador do relatório.

### <a name="relational-data-sources"></a>Origens de dados relacionais

Geralmente, as origens de dados relacionais são adequadas para relatórios de estilo operacional, como faturas de vendas. Também são adequadas para relatórios que precisem de obter conjuntos de dados muito grandes (com mais de 10 mil linhas). As origens de dados relacionais também podem definir procedimentos armazenados, que podem ser executados por conjuntos de dados de relatório. Os procedimentos armazenados proporcionam vários benefícios:

- Parametrização
- Encapsulamento de lógica de programação, o que permite uma preparação de dados mais complexa (por exemplo, tabelas temporárias, cursores ou funções escalares definidas pelo utilizador)
- Manutenção melhorada, o que permite que a lógica de procedimento armazenado seja facilmente atualizada. Em alguns casos, pode ser realizada sem a necessidade de modificar e voltar a publicar relatórios paginados (desde que os nomes das colunas e os tipos de dados permaneçam inalterados)
- Melhor desempenho, dado que os planos de execução são colocados em cache para reutilização
- Reutilização de procedimentos armazenados em múltiplos relatórios

No Power BI Report Builder, pode utilizar o estruturador de consulta relacional para construir graficamente uma instrução de consulta, mas apenas para origens de dados da Microsoft.

### <a name="analytic-data-sources"></a>Origens de dados analíticos

As origens de dados analíticos são adequadas para relatórios operacionais e de análise e podem devolver resultados de consultas resumidos rápidos, mesmo em volumes de dados muito grandes. As medidas do modelo e os KPIs podem encapsular regras de negócio complexas para alcançar o resumo dos dados. No entanto, estas origens de dados não são adequadas para relatórios que precisem de obter conjuntos de dados muito grandes (com mais de 10 mil linhas).

No Power BI Report Builder, pode escolher entre dois estruturadores de consulta: o estruturador de consulta Analysis Services DAX e o estruturador de consulta Analysis Services MDX. Estes estruturadores podem ser utilizados para origens de dados de conjuntos de dados do Power BI ou qualquer modelo do SQL Server Analysis Services ou Azure Analysis Services (tabular ou multidimensional).

Sugerimos a utilização do estruturador de consulta DAX, desde que satisfaça inteiramente as suas necessidades de consulta. Se o modelo não definir as medidas de que necessita, terá de mudar para o modo de consulta. Neste modo, pode personalizar a instrução de consulta ao adicionar expressões (para alcançar o resumo).

O estruturador de consulta MDX requer que o seu modelo inclua medidas. O estruturador tem duas capacidades não suportadas pelo estruturador de consulta DAX. Especificamente, permite-lhe:

- Definir membros calculados ao nível da consulta (no MDX).
- Configurar regiões de dados para pedir [agregados de servidores](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) em grupos não detalhados. Se o seu relatório tiver de apresentar resumos de medidas não aditivas ou semiaditivas (como cálculos de análise de tempo ou contagens distintas), será provavelmente mais eficiente utilizar agregados de servidores para obter linhas de detalhes de nível inferior e fazer com que o relatório calcule os resumos.

## <a name="query-result-size"></a>Tamanho do resultado da consulta

De forma geral, é recomendado obter apenas os dados exigidos pelo seu relatório. Posto isto, não obtenha colunas ou linhas que não sejam exigidas pelo relatório.

Para limitar as linhas, deve sempre aplicar os filtros mais restritivos e definir consultas agregadas. As consultas agregadas agrupam e resumem os dados da origem para obter resultados mais granulares. Por exemplo, considere que o seu relatório tem de apresentar um resumo de vendas de um representante. Em vez de obter todas as linhas de ordem de venda, crie uma consulta de conjunto de dados que seja agrupada por representante de vendas e resuma as vendas de cada grupo.

## <a name="expression-based-fields"></a>Campos baseados em expressões

É possível expandir um conjunto de dados de relatório com campos baseados em expressões. Por exemplo, se os dados tiverem como origem o nome próprio e o apelido do cliente, poderá querer um campo que concatena ambos os campos para produzir o nome completo do cliente. Existem duas opções para alcançar este cálculo. Pode:

- Criar um _campo calculado_, que é um campo de conjunto de dados baseado numa expressão.
- Injetar uma expressão diretamente na consulta de conjunto de dados (com a linguagem nativa da sua origem de dados), o que resulta num campo de conjunto de dados regular.

Recomendamos a última opção, sempre que possível. Existem dois bons motivos pelos quais a injeção de expressões diretamente na consulta de conjunto de dados é preferível:

- É possível que a origem de dados esteja otimizada para avaliar a expressão de forma mais eficiente do que o Power BI (principalmente no caso de bases de dados relacionais).
- O desempenho do relatório é melhorado porque não há necessidade de o Power BI materializar campos calculados antes da composição do relatório. Os campos calculados podem ampliar visivelmente o tempo de composição do relatório quando os conjuntos de dados obtêm um grande número de linhas.

## <a name="field-names"></a>Nomes de campos

Quando cria um conjunto de dados, é automaticamente atribuído um nome aos respetivos campos de acordo com as colunas da consulta. É possível que estes nomes não sejam apelativos nem intuitivos. É igualmente possível que os nomes das colunas da consulta de origem incluam carateres proibidos nos identificadores de objetos da linguagem RDL (Report Definition Language), como espaços e símbolos. Neste caso, os carateres proibidos são substituídos por um caráter de sublinhado (_).

Recomendamos que verifique primeiro se todos os nomes dos campos são apelativos, concisos e, ainda assim, significativos. Caso contrário, sugerimos que mude os respetivos nomes _antes_ de iniciar o esquema do relatório. Os campos cujos nomes foram mudados não oscilam alterações pelas expressões utilizadas no esquema do relatório. Caso opte por mudar o nome dos campos após ter iniciado o esquema do relatório, terá de localizar e atualizar todas as expressões danificadas.

## <a name="filter-vs-parameter"></a>Filtro vs. parâmetro

É provável que a estrutura do seu relatório paginado tenha parâmetros de relatório. Estes são utilizados com frequência para pedir ao utilizador do relatório que filtre o relatório. Enquanto autor do relatório paginado, tem duas formas de alcançar a filtragem do relatório. Pode mapear um parâmetro de relatório a:

- Um _filtro_ de conjunto de dados, em que os valores do parâmetro de relatório são utilizados para filtrar os dados já obtidos pelo conjunto de dados.
- Um _parâmetro_ de conjunto de dados, em que os valores do parâmetro de relatório são injetados na consulta nativa enviada para a origem de dados.

> [!NOTE]
> Todos os conjuntos de dados do relatório são colocados em cache _individualmente para cada sessão_ até 10 minutos _além da sua última utilização_. Um conjunto de dados pode ser reutilizado ao enviar novos valores de parâmetro (filtragem), compor o relatório num formato diferente ou interagir com a estrutura do relatório de alguma forma, como alternar a visibilidade ou a ordenação.

Considere um exemplo de um relatório de vendas que tem um único parâmetro de relatório para filtrar o mesmo por um único ano. O conjunto de dados obtém as vendas para _todos os anos_. Isto acontece porque o parâmetro de relatório mapeia aos filtros do conjunto de dados. O relatório apresenta os dados referentes ao ano solicitado, que corresponde a um subconjunto dos dados do conjunto de dados. Quando o utilizador do relatório altera o parâmetro de relatório para um ano diferente e, em seguida, visualiza o relatório, o Power BI não precisa de obter dados de origem. Em vez disso, aplica um filtro diferente ao conjunto de dados já colocado em cache. Após o conjunto de dados ser colocado em cache, a filtragem pode ser muito rápida.

Considere agora uma estrutura de relatório diferente. Desta vez, a estrutura de relatório mapeia o parâmetro de relatório referente ao ano de vendas a um parâmetro do conjunto de dados. Desta forma, o Power BI injeta o valor referente ao ano na consulta nativa e o conjunto de dados obtém dados referentes apenas a esse ano. Sempre que o utilizador do relatório altera o valor do parâmetro de relatório referente ao ano e, em seguida, visualiza o relatório, o conjunto de dados obtém um novo resultado de consulta apenas para esse ano.

Ambas as abordagens à estrutura podem filtrar dados de relatório e ambas as estruturas podem ser adequadas para a estrutura do seu relatório. No entanto, uma estrutura otimizada vai depender dos volumes antecipados de dados, da volatilidade dos dados e dos comportamentos antecipados dos utilizadores do relatório.

Recomendamos a _filtragem por conjunto de dados_ quando antecipa que um subconjunto diferente de linhas do conjunto de dados será reutilizado várias vezes (poupando assim tempo de composição, uma vez que os novos dados não têm de ser obtidos). Neste cenário, reconhece que o custo da obtenção de um conjunto de dados maior pode ser vantajoso face ao número de vezes que será reutilizado. Posto isto, é útil para consultas cuja geração é mais demorada. Tenha em atenção que a colocação em cache de conjuntos de dados grandes individualmente por utilizador pode afetar negativamente o desempenho e o débito de capacidade.

Recomendamos a _parametrização de conjuntos de dados_ quando antecipar que não é provável que um subconjunto diferente de linhas do conjunto de dados seja solicitado ou quando o número de linhas do conjunto de dados a filtrar é provavelmente muito grande (e cuja colocação em cache será ineficiente). Esta abordagem de estrutura também é adequada quando o arquivo de dados é volátil. Neste caso, cada alteração ao valor do parâmetro de relatório resultará na obtenção de dados atualizados.

## <a name="non-native-data-sources"></a>Origens de dados não nativas

Se precisar de desenvolver relatórios paginados baseados em origens de dados que não são [suportadas nativamente por relatórios paginados](../paginated-reports/paginated-reports-data-sources.md), pode começar por desenvolver um modelo de dados do Power BI Desktop. Desta forma, pode ligar a mais de 100 [origens de dados do Power BI](../power-bi-data-sources.md). Uma vez publicado no serviço Power BI, pode desenvolver um relatório paginado que liga ao conjunto de dados do Power BI.

## <a name="data-integration"></a>Integração de dados

Se precisar de combinar dados de múltiplas origens de dados, tem duas opções:

- **Combinar conjuntos de dados de relatório**: se as origens de dados forem [suportadas nativamente por relatórios paginados](../paginated-reports/paginated-reports-data-sources.md), pode considerar criar campos calculados que utilizem as funções [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) ou [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function) do Report Builder.
- **Desenvolver um modelo do Power BI Desktop**: contudo, é provavelmente mais eficiente desenvolver um modelo de dados no Power BI Desktop. Pode utilizar o Power Query para combinar consultas baseadas em qualquer [origem de dados suportada](../power-bi-data-sources.md). Uma vez publicado no serviço Power BI, pode desenvolver um relatório paginado que liga ao conjunto de dados do Power BI.

## <a name="sql-server-complex-data-types"></a>Tipos de dados complexos do SQL Server

Dado que o SQL Server é uma origem de dados no local, o Power BI tem de ligar através de um gateway. No entanto, o gateway não suporta a obtenção de dados para tipos de dados complexos. Os tipos de dados complexos incluem tipos incorporados como os [tipos de dados espaciais](/sql/relational-databases/spatial/spatial-data-sql-server) de GEOMETRIA e de GEOGRAFIA, e o tipo de dados [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). Também podem incluir tipos definidos pelo utilizador implementados através de uma classe de uma assemblagem no CLR do Microsoft.NET Framework.

Desenhar dados espaciais e analíticos na visualização do mapa requer dados espaciais do SQL Server. Portanto, não é possível trabalhar com a visualização do mapa quando o SQL Server for a sua origem de dados. Para clarificar, funcionará se a sua origem de dados for a Base de Dados SQL do Azure, dado que o Power BI não consegue ligar através de um gateway.

## <a name="data-related-images"></a>Imagens relacionadas com dados

As imagens podem ser utilizadas para adicionar logótipos ou imagens à estrutura do seu relatório. Quando as imagens estão relacionadas com as linhas obtidas por um conjunto de dados do relatório, tem duas opções:

- É possível que os dados da imagem possam também ser obtidos a partir da sua origem de dados (caso já estejam armazenados numa tabela).
- Quando as imagens são armazenadas num servidor Web, pode utilizar uma expressão dinâmica para criar o caminho do URL da imagem.

Para obter mais informações e sugestões, veja [Orientação para a utilização de imagens para relatórios paginados](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Obtenção de dados redundantes

É possível que o seu relatório obtenha dados redundantes. Isto pode acontecer quando elimina campos de consulta do conjunto de dados ou quando o relatório tem conjuntos de dados não utilizados. Evite estas situações, pois resultam numa carga desnecessária para as suas origens de dados, a rede e os recursos de capacidade do Power BI.

### <a name="deleted-query-fields"></a>Campos de consulta eliminados

Na página **Campos** da janela **Propriedades do Conjunto de Dados**, é possível eliminar _campos de consulta_ do conjunto de dados (os campos de consulta mapeiam às colunas obtidas pela consulta do conjunto de dados). No entanto, o Report Builder não remove as colunas correspondentes da consulta do conjunto de dados.

Se precisar de eliminar campos de consulta do seu conjunto de dados, recomendamos que remova as colunas correspondentes da consulta do conjunto de dados. O Report Builder removerá automaticamente todos os campos de consulta redundantes. Caso elimine campos de consulta, certifique-se de que também modifica a instrução da consulta do conjunto de dados para remover as colunas.

### <a name="unused-datasets"></a>Conjuntos de dados não utilizados

Quando um relatório é executado, todos os conjuntos de dados são avaliados, mesmo que não estejam vinculados a objetos de relatório. Por este motivo, certifique-se de que remove todos os conjuntos de dados de teste ou desenvolvimento antes de publicar um relatório.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações relacionadas com este artigo, consulte os seguintes recursos:

- [Origens de dados suportadas para relatórios paginados do Power BI](../paginated-reports/paginated-reports-data-sources.md)
- Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
- Sugestões? [Contribuir com ideias para melhorar o Power BI](https://ideas.powerbi.com/)
