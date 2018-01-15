---
title: "Filtragem cruzada bidirecional no Power BI Desktop (Pré-visualização)"
description: Ativar a filtragem cruzada ao utilizar o DirectQuery no Power BI Desktop
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 7946a9389897c4401e581482c0630547a764616d
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="bidirectional-cross-filtering-using-directquery-in-power-bi-desktop-preview"></a>Ativar a filtragem cruzada ao utilizar o DirectQuery no Power BI Desktop (Pré-visualização)

Ao filtrar tabelas para criar uma vista apropriada dos dados, os criadores de relatórios (e modeladores de dados) deparam-se com dificuldades ao determinar como a filtragem é aplicada a um relatório: o contexto de filtro de uma tabela foi retido num dos lados da relação, mas não no outro, requerendo habitualmente fórmulas DAX complexas para obter os resultados pretendidos.

Na filtragem cruzada bidirecional, os criadores de relatórios (e modeladores de dados) têm agora maior controlo sobre a aplicação dos filtros ao trabalhar com tabelas relacionadas, permitindo que esses filtros sejam aplicados a *ambos* os lados de uma relação entre tabelas. Para tal, é necessário que um contexto de filtro seja propagado para uma segunda tabela relacionada no outro lado de uma relação entre tabelas.

Está disponível um [documento técnico detalhado](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx), que explica a filtragem cruzada bidirecional no Power BI Desktop (o documento técnico também abrange o SQL Server Analysis Services 2016, sendo que ambos têm o mesmo comportamento).

* Transferir o documento técnico [Filtragem cruzada bidirecional para o Power BI Desktop](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)

### <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Ativar a filtragem cruzada bidirecional para o DirectQuery
Para utilizar a filtragem cruzada no DirectQuery, tem de começar por ativá-la. Trata-se de uma funcionalidade de pré-visualização, ou seja, a disponibilidade e o comportamento da mesma está sujeita a alterações em versões futuras do Power BI Desktop.

Para ativar a filtragem cruzada no DirectQuery no Power BI Desktop, selecione **Ficheiro > Opções e definições > Opções** e, em seguida, marque a caixa junto a **Permitir filtragem cruzada em ambas as direções no DirectQuery**, conforme apresentado na seguinte imagem.

![](media/desktop-bidirectional-filtering/bidirectional-filtering_1.png)

> [!NOTE]
> Ao criar fórmulas DAX de filtragem cruzada no Power BI Desktop, utilize o *UserPrincipalName* (que costuma ser igual ao início de sessão do utilizador, como *joe@contoso.com*), em vez de *UserName*. Como tal, poderá precisar de criar uma tabela relacionada que mapeie *UserName* (ou EmployeeID, por exemplo) para *UserPrincipleName*.
> 
> 

Para ativar a filtragem cruzada, na caixa de diálogo **Editar Relação** para uma relação, os seguintes itens têm de estar selecionados:

* Deve definir a **Direção de filtragem cruzada** como **Ambas**
* A definição **Aplicar filtros de segurança em ambas as direções** tem também de estar selecionada
  
  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

Para obter mais informações, e para obter exemplos do funcionamento da filtragem cruzada bidirecional, consulte o [documento técnico](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) mencionado anteriormente neste artigo.

