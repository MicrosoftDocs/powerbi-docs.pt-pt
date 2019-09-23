---
ms.openlocfilehash: f4043a5a8deac0596b58519183988f6ae574458e
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70847722"
---
Existem dois cálculos principais que pode criar com o DAX:

* **coluna calculadas**
* **medidas calculadas**

Antes de aprofundarmos a criação de qualquer um destes cálculos, é bom ter um conhecimento sólido da sintaxe DAX para tabelas e colunas, que irá utilizar quando criar **colunas calculadas** ou **medidas calculadas**.

## <a name="dax-table-and-column-name-syntax"></a>Sintaxe de nomes de tabelas e colunas do DAX
Quer esteja a criar uma nova coluna ou medida, é importante conhecer o formato geral dos nomes de tabelas no DAX:

    'Table Name'[ColumnName]

Se existirem espaços no nome da tabela (conforme demonstrado acima), as plicas à volta do nome da tabela são obrigatórias. Se o nome da tabela não incluir espaços, as plicas podem ser omitidas e a sintaxe tem o aspeto seguinte:

    TableName[ColumnName]

A imagem seguinte mostra uma fórmula DAX a ser criada no Power BI:

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

Também pode omitir por completo o nome da tabela e utilizar apenas o nome da coluna, mas esta não é a melhor prática para escrever funções claras (e, por conseguinte, código DAX claro). Os nomes de colunas têm de incluir sempre parênteses retos.

A melhor prática é fazer *sempre* o seguinte:

* Não incluir espaços nos nomes de tabelas
* Incluir sempre o nome da tabela em fórmulas (não omitir, embora o DAX permita que o faça)

## <a name="creating-calculated-columns"></a>Criar colunas calculadas
As **colunas calculadas** são úteis quando pretende dividir ou filtrar o valor ou se quiser um cálculo para cada linha na tabela.

Pode criar colunas calculadas no Power BI Desktop, selecionando **Nova Coluna** no separador **Modelação**. É melhor estar na vista de **Dados** (em vez da vista de **Relatório** ou **Relações**), uma vez que pode ser a nova coluna criada e a **Barra de Fórmulas** está preenchida e pronta para a fórmula DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

Depois de selecionar o botão **Nova Coluna**, a **Barra de Fórmulas** é preenchida com um nome de coluna básico (que, obviamente, pode alterar de acordo com a sua fórmula) e o operador **=** , e a nova coluna aparece na grelha de dados, conforme mostra a imagem seguinte.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

Os elementos necessários para uma coluna calculada são os seguintes:

* um novo nome de coluna
* pelo menos uma função ou expressão

Se fizer referência a uma tabela ou coluna na sua fórmula de coluna calculada, não terá de especificar uma linha na tabela - o Power BI calcula a coluna para a linha atual para cada cálculo.

## <a name="creating-calculated-measures"></a>Criar medidas calculadas
Utilize uma **medida calculada** quando estiver a calcular percentagens ou rácios, ou precisará de agregações complexas. Para criar uma medida com uma fórmula DAX, selecione o botão **Nova Medida** no separador **Modelação**. Mais uma vez, é melhor estar na vista de **Dados** do Power BI Desktop, uma vez que mostra a **Barra de Fórmulas** e facilita a escrita da fórmula DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

Com **medidas**, um novo ícone de medida é apresentado no painel **Campos** com o nome da medida. A **Barra de Fórmulas** é novamente preenchida com o nome da fórmula DAX (desta vez, com a medida).

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

Os elementos necessários para uma medida calculada são os mesmos que são necessários para uma coluna calculada:

* um novo nome de medida
* pelo menos uma função ou expressão

> Conteúdo de vídeo cortesia de [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

