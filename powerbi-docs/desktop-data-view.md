---
title: Vista de Dados no Power BI Desktop
description: Vista de Dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 567beb29ecdcaf8a07023c8c8c9b32995623534c
ms.sourcegitcommit: 2116af72f435cd30f1401bb9c7afdcbc76b1c3ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65454464"
---
# <a name="data-view-in-power-bi-desktop"></a>Vista de Dados no Power BI Desktop
A **Vista de Dados** ajuda a inspecionar, explorar e compreender os dados no modelo do **Power BI Desktop**. É diferente do modo que vê tabelas, colunas e dados no **Editor de Consultas**. Com a Vista de Dados, está a ver os seus dados *após* eles terem sido carregados no modelo.

Quando está a modelar seus dados, às vezes deseja ver o que está realmente numa tabela ou coluna, sem criar um elemento visual na tela de relatório, geralmente imediatamente abaixo do nível de linha. Isto é particularmente útil quando está a criar colunas calculadas e medidas, ou quando precisa de identificar um tipo de dados ou uma categoria de dados.

Analisemos mais detalhadamente alguns dos elementos que se encontram na **Vista de Dados**.

![Vista de dados no Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Ícone da Vista de Dados** – selecione este ícone para aceder à Vista de Dados.

2. **Grelha de Dados** – esta opção mostra a tabela selecionada e todas as colunas e linhas presentes na mesma. As colunas ocultadas da **Vista de Relatório** aparecem acinzentadas. Pode clicar com o botão direito do rato numa coluna para ver as opções.

3. **Friso de modelagem** – aqui pode gerir relações, criar cálculos, alterar o tipo de dados, a formatação ou a categoria de dados de uma coluna.

4. **Barra de fórmulas** – insira fórmulas DAX para Medidas e Colunas calculadas.

5. **Pesquisa** – procure uma tabela ou coluna no seu modelo.

6. **Lista de campos** – selecione uma tabela ou coluna para ver na grelha de dados.

## <a name="filtering-in-data-view"></a>Filtragem na Vista de Dados

Também pode filtrar e ordenar dados na **Vista de Dados**. Cada coluna mostra um ícone que identifica a direção de ordenação (se estiver aplicada).

![Ordenar e filtrar na Vista de Dados no Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Pode filtrar valores individuais ou utilizar a filtragem avançada com base nos dados na coluna. 

> [!NOTE]
> Quando um modelo do Power BI é criado numa cultura diferente da utilizada na interface do utilizador atual (por exemplo, o modelo foi criado em inglês dos EUA e está a vê-lo em espanhol), a caixa de pesquisa irá aparecer na interface do utilizador da Vista de Dados apenas para campos de texto.
