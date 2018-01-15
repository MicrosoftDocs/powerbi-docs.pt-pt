---
title: "Combinar binários no Power BI Desktop"
description: "Combine facilmente origens de dados binárias no Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: d0c4f3afb7b8b103dfa59a982b067bbad24251fb
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="combine-binaries-in-power-bi-desktop"></a>Combinar binários no Power BI Desktop
Uma abordagem poderosa para importar dados para o **Power BI Desktop** é combinar múltiplos ficheiros com o mesmo esquema numa única tabela lógica. Na versão de novembro de 2016 do **Power BI Desktop** (e versões posteriores), esta abordagem cómoda e popular tornou-se mais cómoda e abrangente, conforme descrito neste artigo.

Para começar a combinar binários da mesma pasta, selecione **Obter Dados > Ficheiro > Pasta**.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-binaries-behavior"></a>Comportamento anterior de combinação de binários
Antes da versão de novembro de 2016 do **Power BI Desktop**, podia combinar certos tipos de ficheiro com a transformação **combinar binários**, mas havia limitações:

* As transformações não eram consideradas para cada ficheiro individual antes de os ficheiros serem combinados numa tabela única. Como tal, era frequente ter de combinar ficheiros e retirar os *valores de cabeçalho* ao filtrar as linhas como parte do processo de edição.
* A transformação **Combinar binários** funcionava apenas para ficheiros de *texto* ou *CSV* e não funcionava noutros formatos de ficheiro suportados, como livros do Excel, ficheiros JSON, entre outros.

Os clientes pediram um funcionamento mais intuitivo da operação **combinar binários**, pelo que a transformação foi melhorada.

## <a name="current-combine-binaries-behavior"></a>Comportamento atual de combinação de binários
Agora, o **Power BI Desktop** processa a operação **combinar binários** com maior eficácia. Comece por selecionar **combinar binários**, seja no separador do friso **Base** no **Editor de Consultas** ou na própria coluna.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

Agora, **combinar binários** tem o seguinte comportamento:

* A transformação **combinar binários** analisa cada ficheiro de entrada e determina o formato de ficheiro correto a utilizar, como *texto* ou *Livro do Excel* ou ficheiro *JSON*.
* A transformação permite-lhe selecionar um objeto específico do primeiro ficheiro (por exemplo, um *livro do Excel*) para extrair.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Depois, a operação **combinar binários** faz o seguinte, automaticamente:
  
  * Cria uma consulta de exemplo que efetua todos os passos de extração necessários num único ficheiro.
  * Cria uma *consulta de função* que parametriza a entrada de ficheiro/binário para a *consulta de exemplo*. A consulta de exemplo e a coluna de função estão ligadas, pelo que as alterações à consulta de exemplo refletem-se na consulta de função.
  * Aplica a *consulta de função* à consulta original com binários de entrada (por exemplo, a consulta *Pasta*) para que aplique a consulta de função a entradas binárias em cada linha e, em seguida, expanda a extração de dados resultante como colunas de nível superior.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Com um novo comportamento de **combinar binários**, pode facilmente combinar todos os binários numa determinada pasta, desde que tenham o mesmo tipo de ficheiro e estrutura (ou seja, as mesmas colunas).

Além disso, pode facilmente aplicar passos adicionais de transformação ou extração ao modificar a *consulta de exemplo* criada automaticamente, sem ter de se preocupar em modificar ou criar passos adicionais de *consulta de função*; quaisquer alterações à *consulta de exemplo* são geradas automaticamente na *consulta de função* associada.

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [Introdução ao Power BI Desktop](desktop-getting-started.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a ficheiros CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

