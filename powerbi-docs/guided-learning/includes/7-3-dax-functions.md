---
ms.openlocfilehash: 06ee6ad7ade46d811c6340d905150c6dd3810c55
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273621"
---
Com o DAX, existem muitas funções disponíveis para moldar, formar ou analisar os seus dados. Estas funções podem ser agrupadas em algumas categorias:

* Funções de **agregação**
* Funções de **contagem**
* Funções **lógicas**
* Funções **informativas**
* Funções de **texto**
* Funções de **data**

Tal como acontece no Excel, quando começa a digitar a sua fórmula na **Barra de Fórmulas** do Power BI Desktop, é apresentada uma lista de funções disponíveis para o ajudar a determinar que função disponível pretende selecionar. Além disso, ao utilizar as teclas de seta **para cima** e **para baixo** no teclado, pode realçar qualquer uma das funções disponíveis e é apresentada uma breve descrição.

O Power BI apresenta as funções que correspondem às letras que introduziu até ao momento, pelo que, se escrever *S*, apenas são apresentadas na lista as funções que começam com a letra *S*. Se escrever *Su*, apenas são apresentadas na lista as funções que *contêm* a sequência de letras *Su* no respetivo nome (não têm de começar com *Su*, apenas têm de conter essa sequência de letras).

![](media/7-3-dax-functions/dax-functions_1.png)

Desta forma, é fácil fazer experiências com o DAX e encontrar cada uma das várias funções DAX que estão disponíveis no Power BI. Só precisa de começar a escrever e o Power BI vai ajudá-lo.

Agora que sabemos como começar a utilizar essa fórmula DAX, vamos ver cada uma destas categorias de função à vez.

## <a name="aggregation-functions"></a>Funções de agregação
O DAX inclui várias funções de **agregação**, incluindo as seguintes funções frequentemente utilizadas:

* SUM
* AVERAGE
* MIN
* MAX
* SUMX (e outras funções *X*)

Estas funções só funcionam em colunas numéricas e, geralmente, só podem agregar uma coluna de cada vez.

No entanto, as funções de agregação especiais que terminam em **X**, tais como **SUMX**, podem funcionar em várias colunas. Estas funções iteram pela tabela e avaliam a expressão para cada linha.

## <a name="counting-functions"></a>Funções de contagem
As funções de **contagem** mais utilizadas no DAX incluem as seguintes:

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Estas funções contam diferentes elementos, tais como valores distintos, valores não vazios e linhas de tabela.

## <a name="logical-functions"></a>Funções lógicas
A coleção de funções **lógicas** no DAX incluem:

* AND
* OR
* NOT
* IF
* IFERROR

Estas funções especiais também podem ser expressas com *operadores*. Por exemplo, **AND** pode ser escrita como (substituída por) **&&** na fórmula DAX.

Pode utilizar operadores (tais como **&&** ) quando precisa de mais de duas condições na sua fórmula mas, caso contrário, a melhor prática consiste em utilizar o próprio nome da função (tal como **AND**) para facilitar a leitura do código DAX.

## <a name="information-functions"></a>Funções informativas
As funções **informativas** no DAX incluem:

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Embora estas funções possam ser úteis em termos situacionais, é importante conhecer com antecedência o tipo de dados das suas colunas, em vez de depender destas funções para fornecer o tipo de dados.

O DAX utiliza as funções **MAX** e **MIN** para *agregar* valores e para *comparar* valores.

## <a name="text-functions"></a>Funções de texto
As funções de **texto** no DAX incluem as seguintes:

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Estas funções de **texto** funcionam de forma muito semelhante às funções do Excel, que têm o mesmo nome. Por isso, se estiver familiarizado com a forma como o Excel processa as funções de texto, já está um passo à frente. Caso contrário, pode sempre fazer experiências com estas funções no Power BI e saber mais sobre a forma como se comportam.

## <a name="date-functions"></a>Funções de data
O DAX inclui as seguintes funções de **data**:

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Embora estas funções sejam úteis para calcular e extrair informações de valores de *data*, não se aplicam à análise de tempo, que utiliza uma tabela de datas.

> Conteúdo de vídeo cortesia de [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

