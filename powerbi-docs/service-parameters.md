---
title: Ver e editar definições de parâmetros de conjuntos de dados no serviço Power BI
description: Os parâmetros de consulta são criados no Power BI Desktop, mas podem ser revistos e atualizados no serviço Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: ac271e8013bce5824931153351a651644a716a2f
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965165"
---
# <a name="what-is-a-query-parameter"></a>O que é um parâmetro de consulta?
Os parâmetros de consulta são adicionados ao Power BI Desktop por criadores de relatórios. Os parâmetros permitem-lhes fazer com que certas partes dos relatórios dependam de um ou mais *valores* de parâmetro. Por exemplo, um criador de relatórios pode criar um parâmetro que restrinja os dados a um único país/região ou um parâmetro que defina os formatos de campo aceitáveis, tais como datas, hora e texto.

![Separador Base a mostrar a opção Gerir Parâmetros no Power BI Desktop](media/service-parameters/power-bi-manage-parameters.png)


## <a name="review-and-edit-parameters-in-power-bi-service"></a>Rever e editar parâmetros no serviço Power BI

Assim que os parâmetros forem definidos no Power BI Desktop, quando esse [relatório for publicado no serviço Power BI](desktop-upload-desktop-files.md), as definições e seleções de parâmetros são movidos juntamente com o relatório. Algumas definições de parâmetros podem ser revistas e editadas no serviço Power BI: não os parâmetros que restringem os dados disponíveis, mas aqueles que definem e descrevem os valores aceitáveis.

1. No serviço Power BI, selecione o ícone de engrenagem ![ícone de engrenagem](media/service-parameters/power-bi-cog.png) para abrir as **Definições**.

2. Selecione o separador **Conjuntos de Dados** e realce um conjunto de dados na lista. 
    
    ![Janela Definições com o separador Conjuntos de Dados selecionado](media/service-parameters/power-bi-select-dataset2.png)

3. Expanda a secção **Parâmetros**.  Se o conjunto de dados selecionado não tiver parâmetros, verá uma mensagem com uma ligação para Saber mais sobre parâmetros de consulta. No entanto, se o conjunto de dados tiver parâmetros, expandir a secção **Parâmetros** irá revelar esses parâmetros. 

    ![Janela Definições com a secção Parâmetros expandida](media/service-parameters/power-bi-settings.png)

    Reveja as definições de parâmetros e faça alterações, se necessário. Os campos a cinzento não são editáveis. 


## <a name="next-steps"></a>Próximos passos
Uma forma ad-hoc de adicionar parâmetros simples é ao [modificar o URL](service-url-filters.md).