---
title: Atualização incremental no Power BI Premium
description: Saiba como utilizar conjuntos de dados muito grandes no serviço Power BI Premium.
author: mgblythe
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mblythe
LocalizationGroup: Premium
ms.openlocfilehash: cd8b4dcd87244f827fcabca630954353c9b6d8eb
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871875"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Atualização incremental no Power BI Premium

A atualização incremental permite utilizar conjuntos de dados muito grandes no serviço Power BI Premium, com as seguintes vantagens:

> [!div class="checklist"]
> * **As atualizações ocorrem de forma mais rápida** – apenas os dados que são alterados têm de ser atualizados. Por exemplo, atualize apenas os últimos cinco dias de um conjunto de dados de 10 anos.
> * **As atualizações são mais fiáveis** – já não é necessário manter ligações de longa duração a sistemas de origens voláteis.
> * **O consumo de recursos é reduzido** – uma quantidade menor de dados a atualizar reduz o consumo geral de memória e de outros recursos.

## <a name="configure-incremental-refresh"></a>Configurar a atualização incremental

As políticas de atualização incremental são definidas no Power BI Desktop e aplicadas assim que são publicadas no serviço Power BI.

Para começar, ative a atualização incremental nas **Funcionalidades de pré-visualização**.

![Opções – funcionalidades de pré-visualização](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Filtrar conjuntos de dados grandes no Power BI Desktop

Os conjuntos de dados grandes com potencialmente milhares de milhões de linhas poderão não ser adequados a um modelo do Power BI Desktop porque o ficheiro PBIX é limitado pelos recursos de memória disponíveis no computador. Por isso, esses conjuntos de dados são normalmente filtrados após a importação. Este tipo de filtragem aplica-se quer esteja a utilizar a atualização incremental ou não. Para a atualização incremental, o utilizador filtra ao utilizar os parâmetros de data/hora do Power Query.

#### <a name="rangestart-and-rangeend-parameters"></a>Parâmetros RangeStart e RangeEnd

Para a atualização incremental, os conjuntos de dados são filtrados ao utilizar os parâmetros de data/hora do Power Query com os nomes **RangeStart** e **RangeEnd** reservados e sensíveis às maiúsculas e minúsculas. Estes parâmetros são utilizados para filtrar os dados importados para o Power BI Desktop, bem como para particionar de forma dinâmica os dados em intervalos assim que forem publicados no serviço Power BI. Os valores do parâmetro são substituídos pelo serviço para filtrar por cada partição. Não precisa de os definir nas definições dos conjuntos de dados no serviço. Uma vez publicados, os valores de parâmetro são substituídos automaticamente pelo serviço Power BI.

Para definir os parâmetros com valores predefinidos, no Editor do Power Query, selecione **Gerir Parâmetros**.

![Gerir parâmetros](media/service-premium-incremental-refresh/manage-parameters.png)

Com os parâmetros definidos, pode então aplicar o filtro ao selecionar a opção no menu **Filtro Personalizado** de uma coluna.

![Filtro personalizado](media/service-premium-incremental-refresh/custom-filter.png)

Certifique-se de que as linhas são filtradas onde o valor da coluna *é posterior ou igual a* **RangeStart** e *anterior a* **RangeEnd**. Outras combinações de filtros podem resultar na contagem duplicada de linhas.

![Filtrar linhas](media/service-premium-incremental-refresh/filter-rows.png)

> [!IMPORTANT]
> Certifique-se de que as consultas têm um símbolo de igual (=) no parâmetro **RangeStart** ou no parâmetro **RangeEnd**, mas não em ambos. Se o símbolo de igual (=) existir em ambos os parâmetros, uma linha poderá satisfazer as condições de duas partições, o que pode levar à duplicação de dados no modelo. Por exemplo,  
> o cenário \#"Linhas Filtradas" = Table.SelectRows(dbo_Fact, cada [OrderDate] **>= RangeStart** e [OrderDate] **<= RangeEnd**) pode causar a duplicação de dados.

> [!TIP]
> Embora o tipo de dados dos parâmetros tenha de ser data/hora, é possível convertê-lo de modo a corresponder aos requisitos da origem de dados. Por exemplo, a seguinte função do Power Query converte um valor de data/hora para que se assemelhe a uma chave de substituição de número inteiro no formato *aaaammdd*, o que é comum em armazéns de dados. A função pode ser invocada pelo passo de filtragem.
>
> `(x as datetime) => Date.Year(x)*10000 + Date.Month(x)*100 + Date.Day(x)`

Selecione **Fechar e Aplicar** no Editor do Power Query. Deve ter um subconjunto do conjunto de dados no Power BI Desktop.

#### <a name="filter-date-column-updates"></a>Filtrar atualizações da coluna de datas

O filtro na coluna de datas é utilizado para particionar os dados em intervalos no serviço Power BI. A atualização incremental não foi concebida para suportar casos onde a coluna de datas filtrada é atualizada no sistema de origem. Uma atualização é interpretada como uma inserção e uma eliminação, não como uma atualização real. Se a eliminação ocorrer no intervalo histórico e não no intervalo incremental, não será registada. Isto pode causar falhas na atualização de dados devido a conflitos de chave de partição.

#### <a name="query-folding"></a>Dobragem de consultas

É importante que os filtros de partição sejam enviados para o sistema de origem quando as consultas são submetidas para as operações de atualização. Enviar a filtragem significa que a origem de dados deve suportar a dobragem de consultas. A maioria das origens de dados que suporta consultas SQL também suporta a filtragem de consultas no servidor. No entanto, as origens de dados como ficheiros simples, blobs, Web e feeds OData normalmente não a suportam. Nos casos em que o filtro não for suportado pelo back-end da origem de dados, não poderá ser enviado. Nesses casos, o motor de mashup compensa e aplica o filtro localmente, o que poderá exigir a obtenção do conjunto de dados completo a partir da origem de dados. Isto pode tornar a atualização incremental muito lenta e o processo pode ficar sem recursos no serviço Power BI ou no gateway de dados no local, se este for utilizado.

Devido aos vários níveis do suporte da dobragem de consultas para cada origem de dados, é recomendado que a verificação seja executada para garantir que a lógica de filtro está incluída nas consultas de origem. Para facilitar, o Power BI Desktop tenta executar esta verificação automaticamente. Se não for possível verificar, será apresentado um aviso na caixa de diálogo da atualização incremental ao definir a política de atualização incremental. As origens de dados baseadas em SQL, como o SQL Oracle e o Teradata, podem depender deste aviso. Outras origens de dados poderão não conseguir verificar sem as consultas de rastreio. Se o Power BI Desktop não conseguir confirmar, será apresentado o seguinte aviso.

 ![Dobragem de consultas](media/service-premium-incremental-refresh/query-folding.png)

### <a name="define-the-refresh-policy"></a>Definir a política de atualização

A atualização incremental está disponível no menu de contexto para tabelas, exceto para modelos Ligação em Direto.

![Atualizar política](media/service-premium-incremental-refresh/refresh-policy.png)

#### <a name="incremental-refresh-dialog"></a>Caixa de diálogo Atualização Incremental

A caixa de diálogo Atualização Incremental é apresentada. Utilize o botão para ativar a caixa de diálogo.

![Detalhes de atualização](media/service-premium-incremental-refresh/refresh-details.png)

> [!NOTE]
> Se a expressão do Power Query da tabela não fizer referência aos parâmetros com nomes reservados, o botão será desativado.

O texto de cabeçalho explica o seguinte:

- A atualização incremental só é suportada em áreas de trabalho com capacidades Premium. As políticas de atualização são definidas no Power BI Desktop e são aplicadas por operações de atualização no serviço.

- Se conseguir transferir o ficheiro PBIX com uma política de atualização incremental a partir do serviço Power BI, o ficheiro não poderá ser aberto no Power BI Desktop. Embora esta operação possa vir a ser suportada no futuro, tenha em atenção que estes conjuntos de dados podem tornar-se muito grandes e deixarem de ser práticos para transferir e abrir num computador normal.

#### <a name="refresh-ranges"></a>Intervalos de atualização

O seguinte exemplo define uma política de atualização para armazenar dados durante cinco anos do calendário completos, bem como dados do ano atual até à data atual. Também atualiza 10 dias de dados de forma incremental. A primeira operação de atualização carrega dados de histórico. As atualizações subsequentes são incrementais e executam as seguintes operações, se as mesmas estiverem agendadas para serem executadas diariamente:

- Adicionar um novo dia de dados.

- Atualizar 10 dias até à data atual.

- Remover os anos do calendário com mais de cinco anos antes da data atual. Por exemplo, se a data atual for 1 de janeiro de 2019, o ano 2013 será removido.

A primeira atualização no serviço Power BI poderá demorar mais tempo a importar todos os cinco anos do calendário completos. As atualizações posteriores poderão ser concluídas numa fração do tempo.

![Intervalos de atualização](media/service-premium-incremental-refresh/refresh-ranges.png)

> [!NOTE]
> Poderá apenas ter de definir estes intervalos. Se for esse o caso, pode avançar para o passo de publicação abaixo. Os menus pendentes adicionais aplicam-se a funcionalidades avançadas.

### <a name="advanced-policy-options"></a>Opções de política avançadas

#### <a name="detect-data-changes"></a>Detetar alterações de dados

Uma atualização incremental de 10 dias é muito mais eficiente do que uma atualização completa de cinco anos. No entanto, é possível fazer ainda melhor. Se selecionar a caixa de verificação **Detetar alterações de dados**, pode selecionar uma coluna de data/hora utilizada para identificar e atualizar apenas os dias em que os dados foram alterados. Isto pressupõe a existência de uma coluna deste tipo no sistema de origem, que normalmente serve para efeitos de auditoria. **Não deve ser a mesma coluna utilizada para particionar os dados com os parâmetros RangeStart/RangeEnd.** O valor máximo desta coluna é avaliado para cada um dos períodos no intervalo incremental. Se não tiver sido alterado desde a última atualização, não é necessário atualizar o período. Neste exemplo, poderia reduzir os dias atualizados incrementalmente de dez para dois.

![Detetar alterações](media/service-premium-incremental-refresh/detect-changes.png)

> [!TIP]
> O design atual requer que os dados da coluna onde se pretende detetar alterações sejam persistentes e estejam em cache na memória. Poderá optar por umas das seguintes técnicas para reduzir a cardinalidade e o consumo de memória.
>
> Mantenha apenas o valor máximo desta coluna no momento da atualização com, por exemplo, uma função do Power Query.
>
> Reduza a precisão a um nível aceitável, consoante os seus requisitos de frequência de atualização.
>
> Planeamos permitir a definição de consultas personalizadas para a deteção de alterações de dados posteriormente. Isto poderá ser utilizado para evitar manter o valor da coluna na sua totalidade.

#### <a name="only-refresh-complete-periods"></a>Atualizar apenas períodos completos

Imaginemos que a sua atualização foi agendada para começar todas as manhãs, às 04:00. Se os dados forem apresentados no sistema de origem durante essas 4 horas, é possível que não pretenda considerá-los. Algumas métricas de negócio (como os barris por dia no setor petrolífero) não fazem sentido com dias parciais.

Outro exemplo é a atualização de dados de um sistema financeiro em que os dados do mês anterior são aprovados no 12.º dia do mês. Pode definir o intervalo incremental para 1 mês e agendar a atualização para o 12.º dia do mês. Por exemplo, com esta opção selecionada, os dados de janeiro seriam atualizados a 12 de fevereiro.

![Períodos completos](media/service-premium-incremental-refresh/complete-periods.png)

> [!NOTE]
> As operações de atualização no serviço são executadas na hora UTC. Isto pode determinar a data efetiva e afetar períodos completos. Planeamos adicionar a capacidade de substituir a data efetiva para uma operação de atualização.

## <a name="publish-to-the-service"></a>Publicar no serviço

Uma vez que a atualização incremental é uma funcionalidade exclusivamente Premium, a caixa de diálogo de publicação só permite selecionar uma área de trabalho na capacidade Premium.

![Publicar no serviço](media/service-premium-incremental-refresh/publish.png)

Já pode atualizar o modelo. A primeira atualização poderá demorar mais tempo a importar os dados do histórico. As atualizações posteriores poderão ser muito mais rápidas, dado que utilizam a atualização incremental.

## <a name="query-timeouts"></a>Tempos limite de consulta

O artigo de [resolução de problemas de atualização](https://docs.microsoft.com/power-bi/refresh-troubleshooting-refresh-scenarios) explica que as operações de atualização no serviço Power BI estão sujeitas a tempos limite. As consultas também podem ser limitadas pelo tempo limite predefinido da origem de dados. A maioria das origens relacionais permite a substituição de tempos limite na expressão M. Por exemplo, a expressão abaixo utiliza a [função de acesso a dados do SQL Server](https://msdn.microsoft.com/query-bi/m/sql-database) para definir o tempo limite para 2 horas. Cada período definido pelos intervalos da política envia uma consulta que segue a definição de tempo limite do comando.

```powerquery-m
let
    Source = Sql.Database("myserver.database.windows.net", "AdventureWorks", [CommandTimeout=#duration(0, 2, 0, 0)]),
    dbo_Fact = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
    #"Filtered Rows" = Table.SelectRows(dbo_Fact, each [OrderDate] >= RangeStart and [OrderDate] < RangeEnd)
in
    #"Filtered Rows"
```

## <a name="limitations"></a>Limitações

Atualmente, a atualização incrementada de [modelos compostos](desktop-composite-models.md) só é suportada para as seguintes origens de dados: SQL Server, Base de Dados SQL do Azure, SQL Data Warehouse, Oracle e Teradata.

