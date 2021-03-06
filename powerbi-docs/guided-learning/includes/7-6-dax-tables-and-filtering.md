---
ms.openlocfilehash: 5bc0d3bbfb2c2b67b56e6406646f6131a360b97d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73800065"
---
Uma diferença significativa entre o **DAX** e a linguagem de fórmula do Excel é o facto de o DAX permitir transmitir *tabelas inteiras* entre expressões, em vez de estar limitado a um único valor. Um efeito poderoso é o facto de o DAX permitir filtrar as tabelas nas respetivas expressões e, em seguida, trabalhar com o conjunto filtrado de valores.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

Com o DAX, pode criar tabelas calculadas completamente novas e, em seguida, tratá-las como qualquer outra tabela - incluindo criar relações entre elas e outras tabelas no modelo de dados.

## <a name="dax-table-functions"></a>Funções de tabela DAX
O DAX tem um conjunto completo de funções de **tabela**, incluindo as seguintes:

* FILTER
* TUDO
* VALUES
* DISTINCT
* RELATEDTABLE

Estas funções devolvem uma tabela completa em vez de um valor. Normalmente, irá utilizar os resultados de uma função de **tabela** numa análise mais aprofundada como parte de uma expressão maior, em vez de utilizar essa tabela devolvida como um valor final. É importante ter em atenção que, quando utiliza uma função de tabela, os resultados herdam as relações das respetivas colunas.

Pode combinar funções de tabela na sua expressão, desde que cada função utilize uma tabela e devolva uma tabela. Por exemplo, considere a seguinte expressão DAX:

    FILTER (ALL (Table), Condition)

Essa expressão colocaria um filtro sobre a totalidade da *Tabela*, ignorando qualquer conteúdo de filtro atual.

A função DISTINCT devolve os valores distintos de uma coluna que também são visíveis no contexto atual. Sendo assim, para utilizar o exemplo de expressão DAX acima, utilizar **ALL** nessa expressão ignora os filtros, enquanto substituir **ALL** por **DISTINCT** os respeitaria.

## <a name="counting-values-with-dax"></a>Contar valores com o DAX
Uma pergunta comum à qual os construtores de relatórios do Power BI querem responder é a seguinte:

* Quantos valores tenho para esta coluna?

A resposta a essa pergunta pode ser simples se tiver uma tabela à sua frente, mas o DAX tem uma abordagem diferente, especialmente quando existe uma relação entre tabelas.

Por exemplo, o Power BI e o DAX incluem valores que não possuem uma indexação cruzada correta. Se a relação de entrada for quebrada, o DAX adiciona uma nova linha à tabela relacionada com espaços em branco em todos os campos e liga essa nova linha à linha não indexada para garantir a integridade referencial. Se a sua função incluir linhas em branco, como é muitas vezes o caso ao utilizar **ALL**, essas linhas em branco serão, em seguida, incluídas no número de valores devolvidos para essa coluna.

Também pode criar tabelas calculadas completas com funções DAX. As tabelas calculadas criadas com o DAX exigem uma função **NAME** e **TABLE**. As tabelas calculadas podem ser utilizadas como qualquer outra tabela, incluindo o estabelecimento de relações.

> Conteúdo de vídeo cortesia de [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

