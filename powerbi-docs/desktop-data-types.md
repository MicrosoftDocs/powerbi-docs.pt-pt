---
title: Tipos de dados no Power BI Desktop
description: Tipos de dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: reference
ms.date: 05/21/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 14b5f3d4b571df8ae672ee9731ed97555c476abd
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "34456046"
---
# <a name="data-types-in-power-bi-desktop"></a>Tipos de dados no Power BI Desktop
Este artigo descreve os tipos de dados suportados no Power BI Desktop e no Data Analysis Expressions (DAX). 

Quando carrega dados para o Power BI Desktop, ele vai tentar converter o tipo de dados da coluna de origem para um tipo de dado que suporte melhor armazenamento, cálculos e visualização de dados mais eficientes. Por exemplo, se uma coluna de valores que importa do Excel não tiver nenhum valor fracionário, o Power BI Desktop converterá toda a coluna de dados para um tipo de dados de Número Inteiro, que é mais adequado para armazenar números inteiros.

Este conceito é importante porque algumas funções do DAX têm requisitos de tipo de dados especiais. Embora em muitos casos o DAX converta implicitamente um determinado tipo de dados por si, existem alguns casos em que isso não acontecerá.  Por exemplo, se uma função do DAX requer um tipo de dados de Data e o tipo de dados para a coluna for Texto, a função do DAX não funcionará corretamente.  Assim, é importante e útil obter o tipo de dados correto para uma coluna. As conversões implícitas são descritas posteriormente neste artigo.

## <a name="determine-and-specify-a-columns-data-type"></a>Determinar e especificar o tipo de dados de uma coluna
No Power BI Desktop, pode determinar e especificar o tipo de dados de uma coluna no Editor de Consultas ou na Vista de Dados ou de Relatório:

**Tipos de dados no Editor de Consultas**

![](media/desktop-data-types/pbiddatatypesinqueryeditort.png)

**Tipos de dados na Vista de Dados ou de Relatório**

![](media/desktop-data-types/pbiddatatypesindatareportview.png)

A lista pendente do Tipo de Dados no Editor de Consultas tem dois tipos de dados atualmente não presentes nos Dados ou na Vista de Relatório: **Data/Hora/Fuso horário** e **Duração**. Quando uma coluna com estes tipos de dados é carregada para o modelo e apresentada na vista de Dados ou de Relatório, uma coluna com um tipo de dado de Data/Hora/Fuso Horário é convertida num valor de Data/Hora, enquanto que uma coluna com um tipo de dados de Duração é convertida num Número Decimal.

### <a name="number-types"></a>Tipos de número
O Power BI Desktop suporta três tipos de número:

**Número Decimal** – representa um número de vírtgula flutuante (oito bytes) de 64 bits. É o tipo de número mais comum e corresponde aos números como normalmente os imagina.  Embora seja concebido para lidar com números com valores fracionários, também lida com números inteiros.  O tipo de Número Decimal pode lidar com valores negativos de -1,79E +308 a -2,23E -308, 0, e valores positivos de 2,23E -308 a 1,79E + 308. Por exemplo, números como 34, 34,01 e 34,000367063 são números decimais válidos. O maior valor que pode ser representado num tipo de Número Decimal tem 15 dígitos.  O separador decimal pode ocorrer em qualquer parte no número. O tipo de Número Decimal corresponde a como o Excel armazena os números.

**Número Decimal Fixo** – tem um local para o separador decimal fixo. O separador decimal tem sempre quatro dígitos à direita e permite 19 dígitos de significância.  O maior valor que pode representar é 922.337.203.685.477,5807 (positivo ou negativo).  O tipo de Número Decimal Fixo é útil em casos em que o arredondamento pode introduzir erros.  Quando trabalha com muitos números que têm valores fracionários pequenos, por vezes, podem acumular e forçar um número a ficar ligeiramente fora do valor correto.  Como os valores após os quatro dígitos à direita do separador decimal são truncados, o tipo Decimal Fixo pode ajudá-lo a evitar estes tipos de erros.   Se está familiarizado com o SQL Server, este tipo de dados corresponde ao Decimal (19,4) do SQL Server ou ao tipo de Dados de Moeda no Power Pivot. 

**Número Inteiro** – representa um valor inteiro de 64 bits (oito bytes). Como é um número inteiro, não tem nenhum dígito à direita da casa decimal. Permite 19 dígitos; números inteiros positivos ou negativos entre -9.223.372.036.854.775.808 (-2^63) e 9.223.372.036.854.775.807 (2^63-1).  Pode representar o maior número possível dos diversos tipos de dados numéricos.  Assim como com o tipo Decimal Fixo, o tipo de Número Inteiro pode ser útil nos casos em que tem de controlar o arredondamento. 

### <a name="datetime-types"></a>Tipos de data/hora
O Power BI Desktop suporta cinco tipos de dados de Data/Hora na Vista de Consulta e três no modelo e Vista de Relatório.   Tanto Data/Hora/Fuso Horário como Duração são convertidos durante o carregamento para o modelo.

**Data/Hora** – representa um valor de data e um valor de hora.  Em segundo plano, o valor de Data/Hora é armazenado como um Tipo de Número Decimal.  Na verdade, pode converter entre os dois.   A parte de uma data referente à hora é armazenada como uma fração de múltiplos inteiros de 1/300 segundos (3,33 ms).  São suportadas datas entre os anos de 1900 e 9999.

**Data** – representa apenas uma Data (sem parte referente à hora).  Quando convertida para o modelo, uma Data é igual a um valor de Data/Hora com zero como valor fracionário.

**Hora** – representa apenas a Hora (nenhuma parte referente à Data).  Quando convertido para o modelo, um valor de Hora é igual a um valor de Data/Hora sem dígitos à esquerda da casa decimal.

**Data/Hora/Fuso horário** – representa uma Data/Hora no formato UTC.  Atualmente, é convertido em Data/Hora quando for carregado para o modelo.

**Duração** – representa um intervalo de tempo. É convertido num Tipo de Número Decimal quando for carregado para o modelo.  Como um tipo de Número Decimal, pode ser adicionado ou subtraído de um campo de Data/Hora com resultados corretos.  Como um tipo de Número Decimal, pode utilizá-lo facilmente em visualizações que mostrem a magnitude.

### <a name="text-type"></a>Tipo de texto
**Texto** - uma cadeia de carateres de dados de com carateres Unicode. Pode ser constituído por cadeias, números ou datas representadas num formato de texto. O comprimento máximo da cadeia é 268.435.456 carateres Unicode (carateres de 256 megabytes) ou 536.870.912 bytes.

### <a name="truefalse-type"></a>Tipo verdadeiro/falso
**Verdadeiro/Falso** – um valor Booleano de Verdadeiro ou Falso.

### <a name="blanksnulls-type"></a>Tipo Branco/Nulo
**Branco** - é um tipo de dados em DAX que representa e substitui nulos SQL. Também pode criar um valor em branco ao utilizar a função [BLANK](http://msdn.microsoft.com/library/ee634820.aspx) e testar brancos com a função lógica [ISBLANK](https://msdn.microsoft.com/library/ee634204.aspx).

### <a name="table-data-type"></a>Tipo de dados de tabela
O DAX utiliza um tipo de dados de tabela em muitas funções, como agregações e cálculos de inteligência de dados temporais. Algumas funções exigem uma referência a uma tabela; outras funções devolvem uma tabela que pode ser utilizada como entrada para outras funções. Em algumas funções que exigem uma tabela como entrada, pode especificar uma expressão que é avaliada como uma tabela; para algumas funções, é necessária uma referência a uma tabela base. Para mais informações sobre os requisitos de funções específicas, consulte [Referência de Função DAX](https://msdn.microsoft.com/library/ee634396.aspx).

## <a name="implicit-and-explicit-data-type-conversion-in-dax-formulas"></a>Conversão implícita e explícita de tipo de dados em fórmulas DAX
Cada função DAX tem requisitos específicos quanto aos tipos de dados que são utilizados como entradas e saídas. Por exemplo, algumas funções exigem números inteiros para alguns argumentos e datas para outros; outras funções exigem texto ou tabelas.

Se os dados na coluna que especificar como um argumento forem incompatíveis com o tipo de dados exigido pela função, em muitos casos o DAX devolverá um erro. No entanto, sempre que possível, o DAX tentará converter implicitamente os dados para o tipo de dados necessário. Por exemplo:

* Pode escrever uma data como uma cadeia e o DAX irá analisá-la e tentar transmiti-la como um dos formatos de data e hora do Windows.
* Pode adicionar TRUE + 1 e obter o resultado 2, pois TRUE é implicitamente convertido para o número 1 e é executada a operação 1+1.
* Se adicionar valores em duas colunas e um valor for representado como texto ("12") e o outro como um número (12), o DAX converte implicitamente a cadeia num número e, em seguida, faz a adição para chegar a um resultado numérico. A expressão a seguir devolve 44: = "22" + 22.
* Se tentar concatenar dois números, o Excel vai apresentá-los como cadeias e, em seguida, concatenar. A expressão a seguir devolve "1234": = 12 & 34.

### <a name="table-of-implicit-data-conversions"></a>Tabela de conversões de dados implícitas
O tipo de conversão executada é determinado pelo operador, que transmite os valores que requer antes de executar a operação pedida. Estas tabelas listam os operadores e indicam a conversão que é realizada em cada tipo de dados na coluna quando é emparelhado com o tipo de dados na linha que intersecciona essa coluna.

> [!NOTE]
>  Os tipos de dados de texto não são incluídos nessas tabelas. Quando um número é representado num formato de texto, em alguns casos o Power BI tentará determinar o tipo de número e representá-lo como um número.
> 
> 

**Adição (+)**

| Operador(+) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |Date/time |
| CURRENCY |CURRENCY |CURRENCY |REAL |Date/time |
| REAL |REAL |REAL |REAL |Date/time |
| Date/time |Date/time |Date/time |Date/time |Date/time |

Por exemplo, se um número real for utilizado numa operação de adição em combinação com dados de moedas, os dois valores são convertidos em REAL e o resultado é devolvido como REAL.

**Subtração (-)**

Na tabela a seguir, o cabeçalho de linha é o minuendo (lado esquerdo) e o cabeçalho da coluna é o subtraendo (lado direito).

| Operador(-) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |CURRENCY |REAL |REAL |
| REAL |REAL |REAL |REAL |REAL |
| Date/time |Date/time |Date/time |Date/time |Date/time |

Por exemplo, se uma data for utilizada numa operação de subtração com qualquer outro tipo de dados, ambos os valores são convertidos em datas e o valor devolvido também é uma data.

> [!NOTE]
>    Os modelos de dados também dão suporte ao operador unário, - (negativo), mas esse operador não altera o tipo de dados do operando.
> 
> 

**Multiplicação (*)**

| Operador(*) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |INTEGER |
| CURRENCY |CURRENCY |REAL |CURRENCY |CURRENCY |
| REAL |REAL |CURRENCY |REAL |REAL |

Por exemplo, se um número inteiro for combinado com um número real numa operação de multiplicação, os dois números são convertidos em números reais e o valor devolvido também é REAL.

**Divisão (/)**

Na tabela a seguir, o cabeçalho da linha é o numerador e o cabeçalho da coluna é o denominador.

| Operador(/) (Linha/Coluna) | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |REAL |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |REAL |CURRENCY |REAL |
| REAL |REAL |REAL |REAL |REAL |
| Date/time |REAL |REAL |REAL |REAL |

Por exemplo, se um número inteiro for combinado com um valor de moeda numa operação de divisão, os dois valores são convertidos em números reais e o resultado também é um número real.

### <a name="comparison-operators"></a>Operadores de comparação
Em expressões de comparação, os valores Booleanos são considerados maiores que valores de cadeia, enquanto que os valores de cadeia são considerados maiores que os valores numéricos ou de data/hora; números e valores de data/hora são considerados como tendo a mesma classificação. Nenhuma conversão implícita é executada para valores de cadeia ou Booleanos; BLANK ou um valor em branco é convertido em 0/""/false, dependendo do tipo de dados do outro valor comparado.

As seguintes expressões DAX ilustram este comportamento:

=IF(FALSE()\>"true","Expressão é verdadeira", "Expressão é falsa"), returns "Expressão é verdadeira"

=IF("12"\>12,"A expressão é verdadeira", "A expressão é falsa"), devolve "A expressão é verdadeira"

=IF("12"=12,"Expressão é verdadeira", "Expressão é falsa"), devolve "Expressão é falsa"

As conversões são executadas implicitamente para tipos numéricos ou de data/hora, conforme descrito na tabela a seguir:

| Operador de Comparação | INTEGER | CURRENCY | REAL | Date/time |
| --- | --- | --- | --- | --- |
| INTEGER |INTEGER |CURRENCY |REAL |REAL |
| CURRENCY |CURRENCY |CURRENCY |REAL |REAL |
| REAL |REAL |REAL |REAL |REAL |
| Date/time |REAL |REAL |REAL |Date/Time |

### <a name="handling-blanks-empty-strings-and-zero-values"></a>Tratamento de elementos em branco, cadeias vazias e valores zero
No DAX, um valor nulo, valor em branco, célula vazia ou um valor ausente estão todos representados pelo mesmo novo tipo de valor, BLANK. Também pode gerar elementos em branco com a função BLANK ou testar elementos em branco com a função ISBLANK.

O modo como os elementos em branco são tratados em operações como adição ou concatenação depende da função individual. A tabela a seguir resume as diferenças entre as fórmulas DAX e do Microsoft Excel, da forma que os elementos em branco são tratados.

| Expression | DAX | Excel |
| --- | --- | --- |
| BLANK + BLANK |BLANK |0(zero) |
| BLANK + 5 |5 |5 |
| BLANK * 5 |BLANK |0(zero) |
| 5/BLANK |Infinity |Error |
| 0/BLANK |NaN |Error |
| BLANK/BLANK |BLANK |Error |
| FALSE OR BLANK |FALSE |FALSE |
| FALSE AND BLANK |FALSE |FALSE |
| TRUE OR BLANK |TRUE |TRUE |
| TRUE AND BLANK |FALSE |TRUE |
| BLANK OR BLANK |BLANK |Error |
| BLANK AND BLANK |BLANK |Error |

