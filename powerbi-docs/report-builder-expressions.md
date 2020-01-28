---
title: Expressões no Report Builder do Power BI
description: As expressões são amplamente utilizadas nos relatórios paginados do Report Builder do Power BI para obter, calcular, apresentar, agrupar, ordenar, filtrar, parametrizar e formatar dados.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 96c62fec55f87a31970b624a79314656ced0c159
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953868"
---
# <a name="expressions-in-power-bi-report-builder"></a>Expressões no Report Builder do Power BI
  As expressões são amplamente utilizadas nos relatórios paginados do Report Builder do Power BI para obter, calcular, apresentar, agrupar, ordenar, filtrar, parametrizar e formatar dados. 
  
  Muitas propriedades de item de relatório podem ser definidas como uma expressão. As expressões ajudam a controlar os conteúdos, a estrutura e a interatividade do seu relatório. As expressões são escritas no Microsoft Visual Basic, guardadas na definição do relatório e avaliadas pelo processador do relatório, quando executa o relatório.  
  
 Ao contrário de aplicações como o Microsoft Office Excel, onde trabalha com dados diretamente numa folha de cálculo, num relatório trabalha com expressões que são marcadores de posição para os dados. Para ver os dados reais das expressões avaliadas, tem de pré-visualizar o relatório. Quando executar o relatório, o processador do relatório avalia cada expressão que combina dados do relatório e elementos de esquema do relatório, como tabelas e gráficos.  
  
 À medida que estrutura um relatório, muitas expressões para itens de relatório são definidas automaticamente. Por exemplo, quando arrasta um campo do painel de dados para uma célula de tabela na superfície de desenho do relatório, o valor da caixa de texto é definido como uma expressão simples para o campo. Na seguinte figura, o painel Dados do Relatório apresenta os campos do conjunto de dados, ID, Name, SalesTerritory, Code e Sales. Três campos foram adicionados à tabela: [Name], [Code] e [Sales]. A notação [Name] na superfície de desenho representa a expressão subjacente `=Fields!Name.Value`.  
  
![Vista Estrutura do Report Builder](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 Quando pré-visualizar o relatório, o processador do relatório combinará a região de dados de tabela com os dados reais da ligação de dados e apresentará uma linha na tabela para cada linha no conjunto de resultados.  
  
 Para introduzir expressões manualmente, selecione um item na superfície de desenho e utilize os menus de atalho e as caixas de diálogo para definir as propriedades do item. Quando vir o botão ***(fx)*** ou o valor `<Expression>` numa lista pendente, sabe que pode definir a propriedade para uma expressão. 
  
##  <a name="Types"></a> Compreender as expressões simples e complexas  
 As expressões começam com um sinal de igual (=) e são escritas no Microsoft Visual Basic. As expressões podem incluir uma combinação de constantes, operadores e referências para valores internos (campos, coleções e funções) e código externo ou personalizado.  
  
 Pode utilizar expressões para especificar o valor das muitas propriedades de item de relatório. As propriedades mais comuns são valores para as caixas de texto e o texto do marcador de posição. Normalmente, se uma caixa de texto contiver apenas uma expressão, a expressão é o valor da propriedade da caixa de texto. Se uma caixa de texto contiver múltiplas expressões, cada expressão é o valor de texto do marcador de posição na caixa de texto.  
  
 Por predefinição, as expressões são apresentadas na superfície de desenho do relatório como expressões *simples* ou *complexas*.  
  
-   **Simples** Uma expressão simples contém uma referência a um único item de uma coleção incorporada, por exemplo, um campo de conjunto de dados, um parâmetro ou um campo incorporado. Na superfície de desenho, uma expressão simples entre parênteses retos. Por exemplo, `[FieldName]` corresponde à expressão subjacente `=Fields!FieldName.Value`. As expressões simples são criadas automaticamente quando cria o esquema do relatório e arrasta os itens do painel de dados do relatório para a superfície de desenho. Para obter mais informações sobre os símbolos que representam diferentes coleções incorporadas, veja [Compreender os símbolos de prefixo para expressões simples](#DisplayText).  
  
-   **Complexas** Uma expressão complexa contém referências a múltiplas referências internas, operadores e chamadas de função. Uma expressão complexa é apresentada como <\<Expr >> quando o valor da expressão inclui mais de uma referência simples. Para ver a expressão, coloque o cursor sobre a mesma e utilize a descrição. Para editar a expressão, abra-a na caixa de diálogo **Expressão**.  
  
 A seguinte figura mostra expressões simples e complexas típicas para caixas de texto e o texto do marcador de posição.  
  
![Formato padrão de expressões do Report Builder](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Para apresentar os valores de exemplo em vez de texto para expressões, aplique a formatação ao texto do marcador de posição ou da caixa de texto. A seguinte figura mostra a superfície de desenho do relatório ativada para mostrar os valores de exemplo:  
  
![Formato simples de expressões do Report Builder](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="DisplayText"></a> Compreender os símbolos de prefixo em expressões simples  

As expressões simples utilizam símbolos para indicar se a referência é relativa a um campo, a um parâmetro, a uma coleção incorporada ou à coleção ReportItems. A seguinte tabela mostra exemplos de texto de expressão e apresentação:  
  
|Item|Exemplo de texto de apresentação|Exemplo de texto de expressão|  
|----------|--------------------------|-----------------------------|  
|Campos de conjunto de dados|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Parâmetros do relatório|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Campos incorporados|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Carateres literais utilizados para apresentar texto|`\[Sales\]`|`[Sales]`|  
  
##  <a name="References"></a> Escrever expressões complexas  
 As expressões podem incluir referências a funções, operadores, constantes, campos, parâmetros e itens de coleções incorporadas, assim como a códigos personalizados incorporados ou assemblagens personalizadas.  
  
 A seguinte tabela lista os tipos de referências que pode incluir numa expressão:  
  
|Referências|Descrição|Exemplo|  
|----------------|-----------------|-------------|  
|Constantes|Descreve as constantes a que pode aceder interativamente para propriedades que necessitem de valores de constantes, como cores do tipo de letra.|`="Blue"`|  
|Operadores|Descreve os operadores que pode utilizar para combinar referências numa expressão. Por exemplo, o operador **&** é utilizado para concatenar cadeias de carateres.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Coleções incorporadas|Descreve as coleções incorporadas que pode incluir numa expressão, tais como `Fields`, `Parameters` e `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Relatório incorporado e funções de agregação|Descreve as funções internas, tais como `Sum` ou `Previous`, a que pode aceder a partir de uma expressão.|`=Previous(Sum(Fields!Sales.Value))`|  
|Código personalizado e referências de assemblagem em expressões no Report Builder |Descreve como pode aceder às classes CLR incorporadas `xref:System.Math` e `xref:System.Convert`, outras classes CLR, funções de biblioteca de tempo de execução do Visual Basic ou aos métodos de uma assemblagem externa.<br /><br /> Descreve como pode aceder ao código personalizado que está incorporado no relatório, ou compilar e instalar como uma assemblagem personalizada no relatório do cliente e no servidor de relatórios.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="Valid"></a> Validar expressões  
 Quando cria uma expressão para uma propriedade do item de relatório específica, as referências que pode incluir numa expressão dependem dos valores que a propriedade do item de relatório pode aceitar e do âmbito em que a propriedade é avaliada. Por exemplo:  
  
-   Por predefinição, a expressão [Sum] calcula a soma dos dados que estão no âmbito, no momento em que a expressão é avaliada. Para uma célula de tabela, o âmbito depende da existência de associações de grupo de linhas e colunas. 
  
-   Para o valor para uma propriedade de tipo de letra, o valor deve ser avaliado como o nome de um tipo de letra.  
  
-   A sintaxe da expressão é validada no momento da estruturação. A validação do âmbito da expressão ocorre quando publica o relatório. Para a validação, tal depende dos dados reais, os erros só podem ser detetados durante a execução. Algumas destas expressões produzem #Error, ou seja, uma mensagem de erro no relatório composto. 

## <a name="next-steps"></a>Próximos passos

- [O que são relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
