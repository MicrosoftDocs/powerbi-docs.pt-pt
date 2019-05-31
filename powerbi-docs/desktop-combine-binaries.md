---
title: Combinar ficheiros (binários) no Power BI Desktop
description: Combinar facilmente ficheiros (binários) de origens de dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: f43bb105f7e17ce453e96c6eff875349efd45cb2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239635"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinar ficheiros (binários) no Power BI Desktop
Uma abordagem poderosa para importar dados para o **Power BI Desktop** é combinar múltiplos ficheiros com o mesmo esquema numa única tabela lógica. Na versão de novembro de 2016 do **Power BI Desktop** (e versões posteriores), esta abordagem cómoda e popular tornou-se mais cómoda e abrangente, conforme descrito neste artigo.

Para começar a combinar ficheiros da mesma pasta, selecione **Obter Dados > Ficheiro > Pasta**.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-files-binaries-behavior"></a>Comportamento anterior da combinação de ficheiros (binários)
Antes da versão de novembro de 2016 do **Power BI Desktop**, esta funcionalidade era chamada **Combinar Binários** e permitia combinar certos tipos de ficheiros com a transformação **combinar binários**, mas havia limitações:

* As transformações não eram consideradas para cada ficheiro individual antes de os ficheiros serem combinados numa tabela única. Como tal, era frequente ter de combinar ficheiros e retirar os *valores de cabeçalho* ao filtrar as linhas como parte do processo de edição.
* A transformação **Combinar binários** funcionava apenas para ficheiros de *texto* ou *CSV* e não funcionava noutros formatos de ficheiro suportados, como livros do Excel, ficheiros JSON, entre outros.

Os clientes pediram um funcionamento mais intuitivo da operação **combinar binários**, pelo que a transformação foi melhorada e mudou de nome para **combinar ficheiros**.

## <a name="current-combine-files-behavior"></a>Comportamento atual da combinação de ficheiros
Agora, o **Power BI Desktop** processa a operação **combinar ficheiros (binários)** com maior eficácia. Comece por selecionar **combinar ficheiros**, seja no separador do friso **Base** do **Editor de Consultas** ou na própria coluna.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

Agora, **combinar ficheiros** tem o seguinte comportamento:

* A transformação **combinar ficheiros** analisa cada ficheiro de entrada e determina o formato de ficheiro correto a utilizar, como *texto* ou *Livro do Excel* ou ficheiro *JSON*.
* A transformação permite-lhe selecionar um objeto específico do primeiro ficheiro (por exemplo, um *livro do Excel*) para extrair.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Em seguida, **combinar ficheiros** realiza automaticamente as seguintes consultas:
  
  * Cria uma consulta de exemplo que efetua todos os passos de extração necessários num único ficheiro.
  * Cria uma *consulta de função* que parametriza a entrada de ficheiro/binário para a *consulta de exemplo*. A consulta de exemplo e a coluna de função estão ligadas, pelo que as alterações à consulta de exemplo refletem-se na consulta de função.
  * Aplica a *consulta de função* à consulta original com binários de entrada (por exemplo, a consulta *Pasta*) para que aplique a consulta de função a entradas binárias em cada linha e, em seguida, expanda a extração de dados resultante como colunas de nível superior.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Com o novo comportamento de **combinar ficheiros**, pode facilmente combinar todos os ficheiros numa determinada pasta, desde que tenham o mesmo tipo de ficheiros e estrutura (tal como as mesmas colunas).

Além disso, pode facilmente aplicar passos adicionais de transformação ou extração ao modificar a *consulta de exemplo* criada automaticamente, sem ter de se preocupar em modificar ou criar passos adicionais de *consulta de função*. Todas as alterações à *consulta de exemplo* são geradas automaticamente na *consulta de função* associada.

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a ficheiros CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

