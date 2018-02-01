---
title: Adicionar uma coluna personalizada no Power BI Desktop
description: Crie rapidamente uma nova coluna personalizada no Power BI Desktop
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 9e2c5bb215ffee880af56a1147dcd4adfbbf17d5
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Adicionar uma coluna personalizada no Power BI Desktop
Pode adicionar facilmente uma nova coluna de dados personalizada ao seu modelo através do **Editor de Consultas** no **Power BI Desktop**. Pode criar e mudar o nome da coluna personalizado através de botões fáceis para criar [fórmulas M](https://msdn.microsoft.com/library/mt270235.aspx) que definam a coluna personalizada. A fórmula M tem um [conjunto de conteúdos de referência de função abrangente](https://msdn.microsoft.com/library/mt779182.aspx). 

![](media/desktop-add-custom-column/add-custom-column_01.png)

A criação de uma coluna personalizada é outro **Passo Aplicado** à consulta criada no **Editor de Consultas**, o que significa que pode ser alterada, movida anterior ou posteriormente ou modificada em qualquer altura.

## <a name="use-query-editor-to-add-a-new-custom-column"></a>Utilizar o Editor de Consultas para adicionar uma nova coluna personalizada
Para criar uma nova coluna personalizada, inicie o **Editor de Consultas**. Pode fazê-lo ao selecionar **Editar Consultas** no friso **Base** no **Power BI Desktop**.

![](media/desktop-add-custom-column/add-column-from-example_02.png)

Depois de iniciar o **Editor de Consultas** e ter alguns dados carregados, pode adicionar uma coluna personalizada ao selecionar o separador **Adicionar Coluna** no friso e, em seguida, ao selecionar **Coluna Personalizada**.

![](media/desktop-add-custom-column/add-custom-column_02.png)

Quando o fizer, é apresentada a janela **Adicionar Coluna Personalizada**, que abordámos na secção seguinte.

## <a name="the-add-custom-column-window"></a>Janela Adicionar Coluna Personalizada
Na janela **Adicionar Coluna Personalizada**, pode ver a lista de campos disponíveis no painel à direita, o nome da coluna personalizada na parte superior (pode mudá-lo apenas ao introduzir um novo nome nessa caixa de texto) e a [**fórmula**  M](https://msdn.microsoft.com/library/mt779182.aspx) que cria (ou escreve) com base na inserção de campos à direita, adição de operadores e criação da fórmula na qual a nova coluna personalizada será definida. 

![](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Criar fórmulas para a coluna personalizada
Pode selecionar um campo na lista **Colunas disponíveis:** à direita e selecionar **<< Inserir** para adicioná-las à fórmula da coluna personalizada. Também pode simplesmente fazer duplo clique numa coluna na lista para adicioná-la.

À medida que escreve a fórmula e cria a coluna, na parte inferior da janela, verá um indicador a informá-lo, em tempo real, se foram detetados erros de sintaxe. Se tudo estiver correto, verá uma marca de verificação verde.

![](media/desktop-add-custom-column/add-custom-column_04.png)

Se tiver algum tipo de erro na sintaxe, será apresentado um ícone de aviso amarelo, juntamente com o erro detetado, e uma ligação que coloca o cursor (na fórmula) onde foi detetado o erro.

![](media/desktop-add-custom-column/add-custom-column_05.png)

Ao selecionar **OK**, a coluna personalizada é adicionada ao modelo e o passo **Coluna Personalizada Adicionada** é adicionado aos **Passos Aplicados** da consulta.

![](media/desktop-add-custom-column/add-custom-column_06.png)

Se fizer duplo clique no passo **Coluna Personalizada Adicionada** no painel **Passos Aplicados**, a janela **Adicionar Coluna Personalizada** é apresentada novamente, com a fórmula de coluna personalizada criada já carregada e pronta para que possa modificá-la, se necessário.

## <a name="using-the-advanced-editor-for-custom-columns"></a>Utilizar o Editor Avançado para Colunas Personalizadas
Também pode criar uma coluna personalizada (e modificar qualquer passo da consulta) com o **Editor Avançado**. No **Editor de Consultas**, selecione o separador **Ver** e, em seguida, selecione **Editor Avançado** para apresentar o **Editor Avançado**.

![](media/desktop-add-custom-column/add-custom-column_07.png)

O **Editor Avançado** dá-lhe controlo total sobre a sua consulta.

## <a name="next-steps"></a>Próximos passos
Existem outras formas de criar uma coluna personalizada, incluindo a criação de uma coluna com base nos exemplos fornecidos ao **Editor de Consultas**. Veja o seguinte artigo para obter mais informações sobre a criação de colunas personalizadas a partir de exemplos:

* [Adicionar uma coluna a partir de um exemplo no Power BI Desktop](desktop-add-column-from-example.md)
* [Introdução à linguagem de fórmula M](https://msdn.microsoft.com/library/mt270235.aspx)
* [Referência à função M](https://msdn.microsoft.com/library/mt779182.aspx)  
