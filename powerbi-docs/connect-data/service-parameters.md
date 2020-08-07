---
title: Editar definições de parâmetro no serviço Power BI
description: Os parâmetros de consulta são criados no Power BI Desktop, mas podem ser revistos e atualizados no serviço Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/04/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 3b64c1dd502fd16199fbff9f64cd2c017006d1f1
ms.sourcegitcommit: a7227f6d3236e6e0a7bc1f83ff6099b5cd58bff3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768480"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Editar definições de parâmetro no serviço Power BI
Os criadores de relatórios adicionam parâmetros de consulta aos relatórios no Power BI Desktop. Os parâmetros permitem-lhes fazer com que certas partes dos relatórios dependam de um ou mais *valores* de parâmetro. Por exemplo, um criador de relatórios pode criar um parâmetro que restrinja os dados a um único país/região ou um parâmetro que defina os formatos de campo aceitáveis, tais como datas, hora e texto.

![Separador Base a mostrar a opção Gerir Parâmetros no Power BI Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Rever e editar parâmetros no serviço Power BI

Como criador de relatórios, pode definir parâmetros no Power BI Desktop. Quando [publicar esse relatório no serviço Power BI](../create-reports/desktop-upload-desktop-files.md), as definições de parâmetro e seleções também serão movidas. Pode rever e editar definições de parâmetros no serviço Power BI, mas não pode criá-las.

1. No serviço Power BI, selecione o ícone de engrenagem ![ícone de engrenagem](media/service-parameters/power-bi-cog.png) para abrir as **Definições**.

2. Selecione o separador **Conjuntos de Dados** e realce um conjunto de dados na lista. 
    
    ![Janela Definições com o separador Conjuntos de Dados selecionado](media/service-parameters/power-bi-select-dataset2.png)

3. Expanda a secção **Parâmetros**.  Se o conjunto de dados selecionado não tiver parâmetros, verá uma mensagem com uma ligação para Saber mais sobre parâmetros de consulta. Se o conjunto de dados tiver parâmetros, expandir a secção **Parâmetros** irá revelá-los. 

    ![Janela Definições com a secção Parâmetros expandida](media/service-parameters/power-bi-settings.png)

    Reveja as definições de parâmetros e faça alterações, se necessário. Os campos a cinzento não são editáveis. 


## <a name="next-steps"></a>Próximas etapas
Uma forma ad-hoc de adicionar parâmetros simples é ao [modificar o URL](../collaborate-share/service-url-filters.md).
