---
title: Editar definições de parâmetro no serviço Power BI
description: Os parâmetros de consulta são criados no Power BI Desktop, mas podem ser revistos e atualizados no serviço Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 92bd37cca1d2e82e6be97869510919e36e9a884f
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85234393"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Editar definições de parâmetro no serviço Power BI
Os criadores de relatórios adicionam parâmetros de consulta aos relatórios no Power BI Desktop. Os parâmetros permitem-lhes fazer com que certas partes dos relatórios dependam de um ou mais *valores* de parâmetro. Por exemplo, um criador de relatórios pode criar um parâmetro que restrinja os dados a um único país/região ou um parâmetro que defina os formatos de campo aceitáveis, tais como datas, hora e texto.

![Separador Base a mostrar a opção Gerir Parâmetros no Power BI Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Rever e editar parâmetros no serviço Power BI

Como criador de relatórios, pode definir parâmetros no Desktop. Quando [publicar esse relatório no serviço Power BI](../create-reports/desktop-upload-desktop-files.md), as definições de parâmetro e seleções também serão movidas. Pode rever e editar algumas definições de parâmetro no serviço Power BI: não os parâmetros que restringem os dados disponíveis, mas aqueles que definem e descrevem os valores aceitáveis.

1. No serviço Power BI, selecione o ícone de engrenagem ![ícone de engrenagem](media/service-parameters/power-bi-cog.png) para abrir as **Definições**.

2. Selecione o separador **Conjuntos de Dados** e realce um conjunto de dados na lista. 
    
    ![Janela Definições com o separador Conjuntos de Dados selecionado](media/service-parameters/power-bi-select-dataset2.png)

3. Expanda a secção **Parâmetros**.  Se o conjunto de dados selecionado não tiver parâmetros, verá uma mensagem com uma ligação para Saber mais sobre parâmetros de consulta. No entanto, se o conjunto de dados tiver parâmetros, expandir a secção **Parâmetros** irá revelar esses parâmetros. 

    ![Janela Definições com a secção Parâmetros expandida](media/service-parameters/power-bi-settings.png)

    Reveja as definições de parâmetros e faça alterações, se necessário. Os campos a cinzento não são editáveis. 


## <a name="next-steps"></a>Próximas etapas
Uma forma ad-hoc de adicionar parâmetros simples é ao [modificar o URL](../collaborate-share/service-url-filters.md).