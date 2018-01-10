---
title: Obter dados de ficheiros
description: Saiba como obter dados do Excel, CSV e Power BI Desktop e inseri-los no Power BI
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 04/01/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: efce7d59df544a067a57db2402c6441c296b569f
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2017
---
# <a name="get-data-from-files"></a>Obter dados de ficheiros
![](media/service-get-data-from-files/file_icons.png)

No Power BI, é possível ligar-se a dados e relatórios ou importá-los através de três tipos de ficheiros.

* Microsoft Excel (.xlsx ou .xlsm)
* Power BI Desktop (.pbix)
* Valores Separados por Vírgula (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>O que significa obter dados de um ficheiro?
No Power BI, os dados explorados são provenientes de um conjunto de dados. Mas, para ter um conjunto de dados, primeiro precisa de obter dados. Neste artigo, o nosso foco consiste em como obter dados de ficheiros.

Para entender melhor a importância dos conjuntos de dados e como podemos obter dados para eles, vamos ter como exemplo um automóvel. Entre no carro, sente-se e observe o dashboard. Isso é muito parecido a sentar-se em frente ao computador e olhar para um dashboard no Power BI. O dashboard mostra tudo o que o seu carro está a fazer: até que ponto o motor está a acelerar, a temperatura, qual mudança está a ser utilizada, etc.

No Power BI, um conjunto de dados é como o motor do carro. O conjunto de dados fornece os dados, as métricas e as informações que são exibidas no dashboard do Power BI. Evidentemente, o motor, ou o conjunto de dados, precisa de combustível, e no Power BI, esse combustível são os dados. O carro tem um tanque de combustível que abastece o motor com gasolina. Da mesma forma que ocorre no Power BI, precisa de um tanque de combustível com dados que possam ser alimentados ao conjunto de dados. No nosso caso, esse tanque de combustível é um ficheiro do Power BI Desktop, um ficheiro de pasta de trabalho do Excel ou um ficheiro .CSV.

Podemos até ir um pouco mais longe. Um tanque de combustível de um carro deve ser enchido com gasolina. A gasolina para o nosso ficheiro do Power BI Desktop, Excel ou .CSV são os dados de outra origem de dados. Obtemos dados de outra origem de dados e inserimos num ficheiro do Excel, Power BI Desktop ou .CSV. Se for uma pasta de trabalho do Excel ou um ficheiro .CSV, poderemos inserir as linhas de dados manualmente. Ou podemos ligar-nos a uma origem de dados externa para consultar e carregar dados em nosso ficheiro. Assim que tivermos um ficheiro com alguns dados, podemos inseri-los no Power BI como um conjunto de dados.

> [!NOTE]
> Os dados nos livros do Excel tem de estar numa tabela ou no modelo de dados a serem importados pelo Power BI.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>O local em que o ficheiro é guardado faz a diferença
**Local** - Caso o ficheiro seja salvo numa unidade local no computador ou noutro local na sua organização, através do Power BI, é possível *importar* o ficheiro para o Power BI. Na verdade, o ficheiro permanece na unidade local; portanto, o ficheiro completo não é importado para o Power BI. O que realmente ocorre é que um novo conjunto de dados é criado no site do Power BI e os dados e, em alguns casos, o modelo de dados, são carregados para esse conjunto de dados. Se o ficheiro tiver relatórios, aparecem no site do Power BI em Relatórios.

**OneDrive - Business** – Caso tenha o OneDrive para Empresas e entre com a mesma conta utilizada para a sessão no Power BI, essa será, sem dúvida, a maneira mais eficiente de salvaguardar o seu trabalho no Excel, no Power BI Desktop ou num ficheiro .CSV em sincronia com o seu conjunto de dados, seus relatórios e dashboards no Power BI. Visto que tanto o Power BI quanto o OneDrive ficam na cloud, o Power BI liga-se ao seu ficheiro no OneDrive em intervalos aproximados de uma hora. Caso sejam encontradas alterações, o conjunto de dados, os relatórios e os dashboards são atualizados automaticamente no Power BI.

**OneDrive - Personal** – Caso os ficheiros sejam guardados na sua própria conta do OneDrive, vai aproveitar vários dos mesmos benefícios que teria com o OneDrive for Business. A maior diferença é que, na primeira ligação ao ficheiro (em Obter Dados > Ficheiros > OneDrive – Personal), será necessário entrar no OneDrive com a sua conta Microsoft que normalmente é diferente da utilizada para iniciar sessão no Power BI. Ao entrar no OneDrive com a sua conta Microsoft, certifique-se de que seleciona a opção Mantenha-me ligado. Dessa forma, o Power BI pode ligar-se ao seu ficheiro em intervalos aproximados de uma hora e garantir que o conjunto de dados no Power BI está em sincronia.

**SharePoint – Sites de Equipa** – Guardar os seus ficheiros do Power BI Desktop no SharePoint – Sites de Equipas é muito semelhante a guardá-los no OneDrive para Empresas. A maior diferença nesse caso é como se liga ao ficheiro do Power BI. É possível especificar um URL ou ligar-se à pasta raiz.

## <a name="ready-to-get-started"></a>Pronto para começar?
Veja os seguintes artigos para saber mais sobre como inserir o seu ficheiro no Power BI.

* [Get data from Excel workbook files (Obter dados de ficheiros de livro do Excel)](service-excel-workbook-files.md)
* [Get data from Power BI Desktop files (Obter dados de ficheiros do Power BI Desktop)](service-desktop-files.md)
* [Obter dados de ficheiros de Valores Separados por Vírgula](service-comma-separated-value-files.md)

