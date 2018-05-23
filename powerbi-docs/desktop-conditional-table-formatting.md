---
title: Formatação de tabela condicional no Power BI Desktop
description: Aplicar formatação personalizada a tabelas
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9599b40940c9d9cca254bb2ed2e87c161cce371f
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="conditional-formatting-in-tables"></a>Formatação condicional em tabelas
Com a formatação condicional para tabelas, pode especificar cores de fundo personalizadas para células, com base nos valores de célula ou noutros valores ou campos, e pode utilizar cores com gradação. Para aceder à formatação condicional, na área **Campos** do painel **Visualizações** no Power BI Desktop, selecione a seta para baixo junto ao valor na área **Valores** que pretende formatar (ou clique com o botão direito do rato no campo). Só pode gerir a formatação condicional para os campos na área **Valores** da área **Campos**.

![formatação condicional da tabela](media/desktop-conditional-table-formatting/table-formatting_1.png)

Na caixa de diálogo que aparece, pode configurar a cor, bem como os valores *Mínimo* e *Máximo*. Se selecionar a caixa **Divergente**, também pode configurar um valor de *Centro* opcional.

![cores divergentes](media/desktop-conditional-table-formatting/table-formatting_2.png)

Também pode basear a gradação da cor num campo do seu modelo de dados. Além disso, pode especificar o tipo de agregação para o campo selecionado (o campo selecionado é especificado no campo **Aplicar cor a**, para que não se perca).

![cores de base de um campo](media/desktop-conditional-table-formatting/table-formatting_2b.png)

Quando aplicada a uma tabela, a formatação condicional aplicada através dos passos acima descritos substitui qualquer estilo de tabela personalizado que tenha sido aplicado às células condicionalmente formatadas.

![formatação da tabela](media/desktop-conditional-table-formatting/table-formatting_3.png)

Também pode aplicar formatação condicional em campos de datas e texto, desde que selecione um valor numérico como base da formatação. 

Para remover a formatação condicional de uma visualização, clique novamente no campo com o botão direito do rato e selecione **Remover Formatação Condicional**.

![remover formatação da tabela](media/desktop-conditional-table-formatting/table-formatting_4.png)

