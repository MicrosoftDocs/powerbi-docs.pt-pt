---
title: Combinar ficheiros (binários) no Power BI Desktop
description: Combinar facilmente ficheiros (binários) de origens de dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 8a5b4c7cb484b296ccab395e18eb2b0089ffd5c7
ms.sourcegitcommit: e2c5d4561455c3a4806ace85defbc72e4d7573b4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327832"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combinar ficheiros (binários) no Power BI Desktop
Uma abordagem poderosa para importar dados para o **Power BI Desktop** é combinar múltiplos ficheiros com o mesmo esquema numa única tabela lógica. Esta abordagem conveniente e popular tornou-se ainda mais conveniente e abrangente, conforme descrito neste artigo.

Para começar a combinar ficheiros da mesma pasta, selecione **Obter Dados > Ficheiro > Pasta**.

![](media/desktop-combine-binaries/combine-binaries_1.png)


## <a name="combine-files-behavior"></a>Comportamento da combinação de ficheiros
Pode **combinar ficheiros (binários)** ao selecionar **combinar ficheiros**, quer a partir do separador do friso **Base** no **Editor de Consultas** ou na própria coluna.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

A transformação **combinar ficheiros** tem o seguinte comportamento:

* A transformação **combinar ficheiros** analisa cada ficheiro de entrada e determina o formato de ficheiro correto a utilizar, como *texto* ou *Livro do Excel* ou ficheiro *JSON*.
* A transformação permite-lhe selecionar um objeto específico do primeiro ficheiro (por exemplo, um *livro do Excel*) para extrair.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Em seguida, **combinar ficheiros** realiza automaticamente as seguintes consultas:
  
  * Cria uma consulta de exemplo que efetua todos os passos de extração necessários num único ficheiro.
  * Cria uma *consulta de função* que parametriza a entrada de ficheiro/binário para a *consulta de exemplo*. A consulta de exemplo e a coluna de função estão ligadas, pelo que as alterações à consulta de exemplo refletem-se na consulta de função.
  * Aplica a *consulta de função* à consulta original com binários de entrada (por exemplo, a consulta *Pasta*) para que aplique a consulta de função a entradas binárias em cada linha e, em seguida, expanda a extração de dados resultante como colunas de nível superior.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> O âmbito da sua seleção num livro do Excel irá afetar o comportamento da combinação de binários. Por exemplo, pode selecionar uma folha de cálculo específica para combinar essa folha de cálculo ou selecionar a raiz para combinar o ficheiro inteiro. Selecionar uma pasta combina todos os ficheiros nessa pasta. 


Com o comportamento de **combinar ficheiros**, pode facilmente combinar todos os ficheiros numa determinada pasta, desde que tenham o mesmo tipo de ficheiro e estrutura (tal como as mesmas colunas).

Além disso, pode facilmente aplicar passos adicionais de transformação ou extração ao modificar a *consulta de exemplo* criada automaticamente, sem ter de se preocupar em modificar ou criar passos adicionais de *consulta de função*. Todas as alterações à *consulta de exemplo* são geradas automaticamente na *consulta de função* associada.

## <a name="next-steps"></a>Próximos passos
Existem diversos tipos de dados aos quais se pode ligar através do Power BI Desktop. Para obter mais informações sobre origens de dados, consulte os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Origens de Dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e Combinar Dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Ligar a ficheiros CSV no Power BI Desktop](desktop-connect-csv.md)   
* [Introduzir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

