---
title: Exemplos de expressões no Report Builder do Power BI
description: As expressões são utilizadas com frequência nos relatórios paginados do Report Builder do Power BI para controlar o conteúdo e o aspeto dos relatórios.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48e81c91a4555b4c8ea847ddffb1413058bbb152
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921154"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Exemplos de expressões no Report Builder do Power BI
As expressões são utilizadas com frequência nos relatórios paginados do Report Builder do Power BI para controlar o conteúdo e o aspeto dos relatórios. As expressões são escritas no Microsoft Visual Basic e pode utilizar funções incorporadas, código personalizado, variáveis de grupos e relatórios e variáveis definidas pelo utilizador. As expressões começam com um sinal de igual (=).   

Este tópico fornece exemplos de expressões que podem ser utilizadas em tarefas comuns num relatório.  
  
-   [Funções do Visual Basic](#VisualBasicFunctions): exemplos de funções de data, de cadeias, de conversão e funções condicionais do Visual Basic.  
  
-   [Funções de Relatórios](#ReportFunctions): exemplos de agregações e outras funções de relatórios incorporadas.  
  
-   [Aspeto dos Dados de Relatórios](#AppearanceofReportData): exemplos de alterações ao aspeto de um relatório.  
  
-   [Propriedades](#Properties): exemplos de definição de propriedades de itens de relatório para controlar o formato ou visibilidade.  
  
-   [Parâmetros](#Parameters): exemplos de utilização de parâmetros numa expressão.  
  
-   [Código Personalizado](#CustomCode): exemplos de código personalizado incorporado.  
  
Para obter mais informações sobre expressões simples e complexas, onde pode utilizar expressões e os tipos de referências que pode incluir numa expressão, consulte os tópicos em [Expressions in Power BI Report Builder](report-builder-expressions.md) (Expressões no Report Builder do Power BI). 
  
## <a name="functions"></a>Funções  
 Muitas expressões num relatório contêm funções. Pode formatar dados, aplicar lógica e aceder a metadados de relatórios com estas funções. Pode escrever expressões que utilizam funções da biblioteca de runtime do Microsoft Visual Basic e dos espaços de nomes `xref:System.Convert` e `xref:System.Math`. Pode adicionar referências a funções no código personalizado. Também pode utilizar classes do Microsoft .NET Framework, incluindo `xref:System.Text.RegularExpressions`.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Funções do Visual Basic  
 Pode utilizar funções do Visual Basic para manipular os dados que são apresentados nas caixas de texto ou que são utilizados em parâmetros, propriedades ou outras áreas do relatório. Esta secção mostra exemplos que demonstram algumas dessas funções. Para obter mais informações, veja [Visual Basic Runtime Library Members (Membros da Biblioteca de Runtime do Visual Basic)](https://go.microsoft.com/fwlink/?LinkId=198941) no MSDN.  
  
 O .NET Framework fornece muitas opções de formatação personalizada, por exemplo, formatos de data específicos. Para obter mais informações, veja [Formatting Types](/dotnet/standard/base-types/formatting-types) (Tipos de Formatação).  
  
### <a name="math-functions"></a>Funções matemáticas  
  
-   A função **Round** é útil para arredondar números para o número inteiro mais próximo. A expressão seguinte arredonda 1,3 para 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     Também pode escrever uma expressão para arredondar um valor para um múltiplo que especificar, de forma semelhante à função **MARRED** no Excel. Multiplique o valor por um fator que cria um número inteiro, arredonde o número e, em seguida, divida pelo mesmo fator. Por exemplo, para arredondar 1,3 para o múltiplo de 0,2 (1,4) mais próximo, use a seguinte expressão:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> Funções de data  
  
-   A função **Today** fornece a data atual. Esta expressão pode ser utilizada numa caixa de texto para mostrar a data no relatório ou num parâmetro para filtrar dados com base na data atual.  
  
    ```  
    =Today()  
    ```  
  
-   Utilize a função **DateInterval** para extrair uma parte específica de uma data. Eis alguns parâmetros **DateInterval** válidos:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Por exemplo, esta expressão irá mostrar o número da semana no ano atual para a data de hoje:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   A função **DateAdd** é útil para fornecer um intervalo de datas com base num único parâmetro. A expressão seguinte fornece uma data que é seis meses após a data de um parâmetro denominado *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   A função **Year** mostra o ano de uma data específica. Pode utilizá-la para agrupar datas ou para mostrar o ano como uma etiqueta para um conjunto de datas. Esta expressão fornece o ano de um determinado grupo de datas de ordens de venda. A função **Month** e outras funções também podem ser utilizadas para manipular datas. Para obter mais informações, veja a documentação do Visual Basic.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Pode combinar funções numa expressão para personalizar o formato. A expressão seguinte altera o formato de uma data na forma mês-dia-ano para o número mês-semana-semana. Por exemplo, 12/23/2009 para Dezembro, Semana 3:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Quando utilizado como um campo calculado num conjunto de dados, pode utilizar esta expressão num gráfico para agregar valores por semana dentro de cada mês.  
  
-   A expressão seguinte formata o valor SellStartDate como MMM-YY. O campo SellStartDate é um tipo de dados datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   A expressão seguinte formata o valor SellStartDate como dd/MM/yyyy. O campo SellStartDate é um tipo de dados datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   A função **CDate** converte o valor numa data. A função **Now** devolve um valor de data com a data e hora atuais, segundo o seu sistema. **DateDiff** devolve um valor Extenso que especifica o número de intervalos de tempo entre dois valores de Data.  
  
     O exemplo seguinte mostra a data de início do ano atual  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   O exemplo seguinte mostra a data de início para o mês anterior com base no mês atual.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   A expressão seguinte gera os anos de intervalo entre SellStartDate e LastReceiptDate. Estes campos estão em dois conjuntos de dados diferentes, DataSet1 e DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   A função **DatePart** devolve um valor de Número inteiro com o componente especificado de um determinado valor de Data. A expressão seguinte devolve o ano do primeiro valor de SellStartDate no DataSet1. O âmbito de conjunto de dados é especificado porque existem diversos conjuntos de dados no relatório.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   A função **DateSerial** devolve um valor de Data que representa um ano, mês e dia especificados, com as informações de hora definidas para a meia-noite. O exemplo seguinte mostra a data de fim para o mês anterior com base no mês atual.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   As expressões seguintes mostram diversas datas com base num valor de parâmetro de data selecionado pelo utilizador.  
  
|Descrição de Exemplo|Exemplo|  
|-------------------------|-------------|  
|Ontem|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Há Dois Dias|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Há Um Mês|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Há Dois Meses|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Há Um Ano|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Há Dois Anos|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> Funções de cadeia  
  
-   Combine mais de um campo ao utilizar os operadores de concatenação e constantes do Visual Basic. A expressão seguinte devolve dois campos, cada um numa linha separada na mesma caixa de texto:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Formate datas e números numa cadeia de carateres com a função **Format**. A expressão seguinte mostra os valores dos parâmetros *StartDate* e *EndDate* em formato de data extenso:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Se a caixa de texto contiver apenas uma data ou número, deve utilizar a propriedade Format da caixa de texto para aplicar formatação em vez da função **Format** dentro da caixa de texto.  
  
-   As funções **Right**, **Len** e **InStr** são úteis para devolver uma subcadeia, por exemplo, cortar *DOMAIN*\\*username* para apenas o nome de utilizador. A expressão seguinte devolve a parte da cadeia de carateres à direita de um caráter de barra invertida (\\) a partir de um parâmetro denominado *User*:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     A expressão seguinte resulta no mesmo valor que o anterior, recorrendo a membros da classe do .NET Framework `xref:System.String` em vez de funções do Visual Basic:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Mostrar os valores selecionados de um parâmetro de valores múltiplos. O exemplo seguinte utiliza a função **Join** para concatenar os valores selecionados do parâmetro *MySelection* numa única cadeia de carateres que pode ser definida como uma expressão para o valor de uma caixa de texto num item de relatório:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     O exemplo seguinte faz o mesmo que o exemplo acima, além de apresentar uma cadeia de texto antes da lista dos valores selecionados.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   As funções **Regex** do .NET Framework `xref:System.Text.RegularExpressions` são úteis para alterar o formato de cadeias existentes, por exemplo, formatar um número de telefone. A expressão seguinte utiliza a função **Replace** para alterar o formato de um número de telefone de 10 dígitos num campo de "*nnn*-*nnn*-*nnnn*" para "(*nnn*) *nnn*-*nnnn*":  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Certifique-se de que o valor para Fields!Phone.Value não tem espaços adicionais e é do tipo `xref:System.String`.  
  
### <a name="lookup"></a>Pesquisa  
  
-   Ao especificar um campo de chave, pode utilizar a função **Lookup** para obter um valor de um conjunto de dados para uma relação um para um, por exemplo, um par chave-valor. A expressão seguinte mostra o nome de produto de um conjunto de dados ("Product"), tendo em conta o identificador de produto ao qual corresponder:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Ao especificar um campo de chave, pode utilizar a função **LookupSet** para obter um conjunto de valores de um conjunto de dados para uma relação de um para muitos. Por exemplo, uma pessoa pode ter múltiplos números de telefone. No exemplo seguinte, pressupõe-se que o conjunto de dados PhoneList contém um identificador pessoal e um número de telefone em cada linha. **LookupSet** devolve uma matriz de valores. A expressão seguinte combina os valores devolvidos numa única cadeia de carateres e apresenta a lista de números de telefone da pessoa especificada por ContactID:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> Funções de conversão  
 Pode utilizar funções do Visual Basic para converter um campo de um tipo de dados para outro. As funções de conversão podem ser utilizadas para converter o tipo de dados predefinido para o tipo de dados necessário para cálculos ou para combinar texto.  
  
-   A expressão seguinte converte a constante 500 para o tipo Decimal para compará-la com um tipo de dados de dinheiro Transact-SQL no campo Value para uma expressão de filtro.  
  
    ```  
    =CDec(500)  
    ```  
  
-   A expressão seguinte mostra o número de valores selecionados para o parâmetro de valores múltiplos *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> Funções de decisão  
  
-   A função **Iif** devolve um de dois valores consoante se a expressão for verdadeira ou não. A expressão seguinte utiliza a função **Iif** para devolver um valor Booleano de **True** se o valor de `LineTotal` for superior a 100. Caso contrário, devolve **False**:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Utilize múltiplas funções **IIF** (também conhecidas como "IIFs aninhados") para devolver um de três valores, consoante o valor `PctComplete`. A expressão seguinte pode ser colocada na cor de preenchimento de uma caixa de texto para alterar a cor de fundo, dependendo do valor na caixa de texto.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Os valores maiores ou iguais a 10 são apresentados com um fundo verde, entre 1 e 9 com um fundo azul e inferiores a 1 com um fundo vermelho.  
  
-   Outra forma de conseguir o mesmo é com a função **Switch**. A função **Switch** é útil quando tem três ou mais condições para testar. A função **Switch** devolve o valor associado à primeira expressão numa série que avalia como true:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Os valores maiores ou iguais a 10 são apresentados com um fundo verde, entre 1 e 9 com um fundo azul, iguais a 1 com um fundo amarelo e iguais ou inferiores a 0 com um fundo vermelho.  
  
-   Testar o valor do campo `ImportantDate` e devolver "Red" se tiver mais de uma semana e "Blue" se não. Esta expressão pode ser utilizada para controlar a propriedade Cor de uma caixa de texto num item de relatório:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Testar o valor do campo `PhoneNumber` e devolver "No Value" se for **null** (**Nothing** no Visual Basic); caso contrário, devolver o valor de número de telefone. Esta expressão pode ser utilizada para controlar o valor de uma caixa de texto num item de relatório.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Testar o valor do campo `Department` e devolver um nome de sub-relatório ou **null** (**Nothing** no Visual Basic). Esta expressão pode ser utilizada para sub-relatórios de pormenorização condicional.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Testar se um valor de campo é nulo. Esta expressão pode ser utilizada para controlar a propriedade **Oculto** de um item de relatório de imagem. No exemplo seguinte, a imagem especificada pelo campo [LargePhoto] é apresentada apenas se o valor do campo não for nulo.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   A função **MonthName** devolve um valor de cadeia de carateres com o nome do mês especificado. O exemplo seguinte apresenta NA no campo Mês, quando o campo contém o valor de 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> Funções de relatório  
 Numa expressão, pode adicionar uma referência a funções de relatório adicionais que manipulam dados num relatório. Esta secção mostra exemplos para duas destas funções. 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   A função **Sum** pode totalizar os valores num grupo ou região de dados. Essa função pode ser útil no cabeçalho ou rodapé de um grupo. A expressão seguinte mostra a soma dos dados na região de dados ou grupo Order:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   Pode também utilizar a função **Sum** para cálculos de agregação condicional. Por exemplo, se um conjunto de dados tiver um campo denominado State com possíveis valores Not Started, Started, Finished, a expressão seguinte, quando colocada num cabeçalho do grupo, calcula a soma de agregação apenas para o valor Finished:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   A função **RowNumber**, quando utilizada numa caixa de texto dentro de uma região de dados, apresenta o número de linha para cada instância da caixa de texto na qual a expressão é apresentada. Esta função pode ser útil para linhas numeradas numa tabela. Também pode ser útil para tarefas mais complexas, como fornecer quebras de página com base no número de linhas. Para obter mais informações, consulte [Quebras de Página](#PageBreaks) neste tópico.  
  
     O âmbito especificado para **RowNumber** controla quando a renumeração começa. A palavra-chave **Nothing** indica que a função começará a contar a partir da primeira linha na região de dados mais externa. Para começar a contagem dentro de regiões de dados aninhadas, utilize o nome da região de dados. Para começar a contagem de dentro de um grupo, utilize o nome do grupo.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> Aspeto de dados de relatórios  
 Pode utilizar expressões para manipular a forma como os dados são apresentados num relatório. Por exemplo, pode mostrar os valores dos dois campos numa única caixa de texto, apresentar informações sobre o relatório ou mudar a forma como as quebras de página são inseridas no relatório.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> Cabeçalhos e rodapés de página  
 Quando criar um relatório, pode querer apresentar o nome do relatório e o número da página no rodapé do relatório. Para tal, pode utilizar as expressões seguintes:  
  
-   A expressão seguinte fornece o nome do relatório e a hora em que este foi executado. Pode ser colocado numa caixa de texto no rodapé do relatório ou no corpo do relatório. A hora é formatada com a cadeia de formatação do .NET Framework para a data abreviada:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   A expressão seguinte, colocada numa caixa de texto no rodapé de um relatório, indica o número de página e o total de páginas no relatório:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 Os exemplos seguintes descrevem como mostrar os primeiros e últimos valores de uma página no cabeçalho da página, semelhante ao que poderá encontrar numa listagem de diretórios. O exemplo assume uma região de dados que contém uma caixa de texto com o nome `LastName`.  
  
-   A expressão seguinte, colocada numa caixa de texto no lado esquerdo do cabeçalho da página, fornece o primeiro valor da caixa de texto `LastName` na página:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   A expressão seguinte, colocada numa caixa de texto no lado direito do cabeçalho da página, fornece o último valor da caixa de texto `LastName` na página:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 O exemplo seguinte descreve como mostrar um total de páginas. O exemplo assume uma região de dados que contém uma caixa de texto com o nome `Cost`.  
  
-   A expressão seguinte, colocada no cabeçalho ou rodapé da página, fornece a soma dos valores na caixa de texto `Cost` da página:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Pode consultar apenas um item de relatório por expressão num cabeçalho ou rodapé de página. Além disso, pode consultar o nome na caixa de texto, mas não a expressão de dados propriamente dita na caixa de texto, nas expressões de cabeçalho e rodapé de página.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> Quebras de página  
 Em alguns relatórios, poderá querer colocar uma quebra de página no final de um número especificado de linhas em vez, ou além, de grupos ou itens de relatório. Para tal, crie um grupo que contenha os grupos ou registos de detalhe que pretende, adicione uma quebra de página ao grupo e, em seguida, adicione uma expressão de grupo para agrupar por um número especificado de linhas.  
  
-   A expressão seguinte, quando colocada na expressão de grupo, atribui um número a cada conjunto de 25 linhas. Quando uma quebra de página é definida para o grupo, esta expressão origina uma quebra de página a cada 25 linhas.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Para permitir ao utilizador definir um valor para o número de linhas por página, crie um parâmetro chamado `RowsPerPage` e baseie a expressão de grupo no parâmetro, como mostra a seguinte expressão:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> Propriedades  
 As expressões não são utilizadas apenas para mostrar dados em caixas de texto. Também podem ser utilizados para alterar a forma como as propriedades são aplicadas a itens de relatórios. Pode alterar as informações de estilo de um item de relatório ou alterar a sua visibilidade.  
  
###  <a name="formatting"></a><a name="Formatting"></a> Formatação  
  
-   A expressão seguinte, quando utilizada na propriedade Cor de uma caixa de texto, altera a cor do texto dependendo do valor do campo `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Também pode utilizar a variável de objeto `Me` do Visual Basic. Esta variável é outra maneira de fazer referência ao valor de uma caixa de texto.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   A expressão seguinte, quando utilizada na propriedade BackgroundColor de um item de relatório numa região de dados, alterna a cor de fundo de cada linha entre verde-claro e branco:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Se estiver a utilizar uma expressão para um âmbito especificado, poderá ter de indicar o conjunto de dados da função de agregação:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  As cores disponíveis provêm da enumeração KnownColor do .NET Framework.  
  
### <a name="chart-colors"></a>Cores de gráficos  
 Para especificar as cores de um Gráfico de formas, pode usar código personalizado para controlar a ordem em que as cores são mapeadas em valores de pontos de dados. Isto ajuda-o a utilizar cores consistentes em diversos gráficos que têm os mesmos grupos de categorias. 
  
###  <a name="visibility"></a><a name="Visibility"></a> Visibilidade  
 Pode mostrar e ocultar itens num relatório com as propriedades de visibilidade do item de relatório. Numa região de dados como uma tabela, pode ocultar inicialmente as linhas detalhadas com base no valor numa expressão.  
  
-   A expressão seguinte, quando utilizada para visibilidade inicial de linhas detalhadas num grupo, mostra as linhas detalhadas para todas as vendas que excedam 90% no campo `PctQuota`:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   A expressão seguinte, quando definida na propriedade Oculto de uma tabela, mostra a tabela apenas se esta tiver mais de 12 linhas:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   A expressão seguinte, quando definida na propriedade **Oculto** de uma coluna, monstra a coluna apenas se o campo existir no conjunto de dados do relatório após os dados serem obtidos da origem de dados:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URLs  
 Pode personalizar URLs ao utilizar os dados de relatório e também controlar condicionalmente se os URLs são adicionados como uma ação para uma caixa de texto.  
  
-   A expressão seguinte, quando utilizada como uma ação numa caixa de texto, gera um URL personalizado que especifica o campo do conjunto de dados `EmployeeID` como um parâmetro de URL.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   A expressão seguinte controla condicionalmente se pretende adicionar um URL numa caixa de texto. Esta expressão depende de um parâmetro chamado `IncludeURLs` que permite a um utilizador decidir se devem ser incluídos URLs ativos num relatório. Esta expressão é definida como uma ação numa caixa de texto. Ao definir o parâmetro como False e, em seguida, visualizar o relatório, pode exportar o relatório do Microsoft Excel sem hiperligações.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="report-data"></a><a name="ReportData"></a> Dados de relatório  
 As expressões podem ser utilizadas para manipular os dados que são utilizados no relatório. Pode consultar parâmetros e outras informações de relatórios. Pode até mesmo alterar a consulta que é utilizada para obter os dados do relatório.  
  
###  <a name="parameters"></a><a name="Parameters"></a> Parâmetros  
 Pode utilizar expressões num parâmetro para variar o valor predefinido do mesmo. Por exemplo, pode utilizar um parâmetro para filtrar dados para um utilizador específico com base no ID de utilizador que é utilizado para executar o relatório.  
  
-   A expressão seguinte, quando utilizada como o valor predefinido de um parâmetro, recolhe o ID de utilizador da pessoa que executa o relatório:  
  
    ```  
    =User!UserID  
    ```  
  
-   Para fazer referência a um parâmetro num parâmetro de consulta, expressão de filtro, caixa de texto ou outra área do relatório, utilize a coleção global **Parameters**. Este exemplo assume que o parâmetro tem o nome *Department*:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Podem ser criados parâmetros num relatório, mas definidos como ocultos. Quando o relatório é executado no servidor de relatórios, o parâmetro não aparece na barra de ferramentas e o leitor do relatório não pode mudar o valor predefinido. Pode utilizar um parâmetro oculto definido como um valor predefinido como constante personalizada. Pode utilizar este valor em qualquer expressão, incluindo uma expressão de campo. A expressão seguinte identifica o campo especificado pelo valor de parâmetro predefinido para o parâmetro com o nome *ParameterField*:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> Código personalizado  
 Pode utilizar código personalizado incorporado num relatório. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Utilizar variáveis de grupos para agregação personalizada  
 Pode inicializar o valor para uma variável de grupo local para um âmbito de grupo específico e, em seguida, incluir uma referência a essa variável em expressões. Uma das formas de utilizar uma variável de grupo com código personalizado é implementar uma agregação personalizada. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Suprimir valores nulos ou zeros no tempo de execução  
 Alguns valores numa expressão podem avaliar como nulos ou indefinidos no tempo de processamento do relatório. Isto pode gerar erros em tempo de execução que fazem com que seja apresentado **#Error** na caixa de texto em vez da expressão avaliada. A função **IIF** é particularmente sensível a este comportamento porque, ao contrário de uma instrução If-Then-Else, cada parte da instrução **IIF** é avaliada (incluindo chamadas de função) antes de ser passada para a rotina que testa para **true** ou **false**. A instrução `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` gera **#Error** no relatório composto se `Fields!Sales.Value` for NOTHING.  
  
 Para evitar esta condição, utilize uma das seguintes estratégias:  
  
-   Defina o numerador como 0 e o denominador como 1, se o valor do campo B for 0 ou indefinido; caso contrário, defina o numerador para o valor do campo A e o denominador para o valor do campo B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Utilize uma função de código personalizada para devolver o valor da expressão. O exemplo seguinte devolve a diferença de percentagem entre um valor atual e um valor anterior. Isto pode ser utilizado para calcular a diferença entre dois valores sucessivos e processa o caso de limite da primeira comparação (quando não existe um valor anterior) e se o valor anterior ou o valor atual é **null** (**Nothing** no Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     A expressão seguinte mostra como chamar este código personalizado de uma caixa de texto para o contentor "ColumnGroupByYear" (grupo ou região de dados).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Isto ajuda a evitar exceções de tempo de execução. Agora, pode utilizar uma expressão como `=IIF(Me.Value < 0, "red", "black")` na propriedade **Cor** da caixa de texto para mostrar texto condicionalmente, consoante os valores forem inferiores ou superiores a 0.  
  
## <a name="next-steps"></a>Próximas etapas

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
