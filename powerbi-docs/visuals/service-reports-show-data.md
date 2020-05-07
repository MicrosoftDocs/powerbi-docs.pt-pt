---
title: Mostrar os dados que foram utilizados para criar a visualização do Power BI
description: Este documento explica como mostrar os dados utilizados para criar um elemento visual no Power BI e como exportar esses dados para um ficheiro. csv.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/4/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: f1598aabee45359b312d39f836cede8ca4198bb2
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758629"
---
# <a name="display-a-visualizations-underlying-data"></a>Apresentar dados subjacentes de uma visualização

## <a name="show-data"></a>Mostrar dados
Uma visualização do Power BI é construída com dados dos conjuntos de dados. Se estiver interessado em conhecer os bastidores, o Power BI permite-lhe *apresentar* os dados que estão a ser utilizados para criar o elemento visual. Quando seleciona **Mostrar Dados**, o Power BI apresenta os dados por baixo da visualização (ou junto da mesma).

Também pode exportar os dados que estão a ser utilizados para criar a visualização como um ficheiro .xlsx ou .csv e visualizá-los no Excel. Para obter mais informações, veja [Exportar dados de visualizações do Power BI](power-bi-visualization-export-data.md).

> [!NOTE]
> *Mostrar Dados* e *Exportar Dados* estão disponíveis no serviço Power BI e no Power BI Desktop. No entanto, o Power BI Desktop fornece uma camada adicional de detalhe; [*Mostrar Registos* apresenta as linhas atuais do conjunto de dados](../desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Utilizar *Mostrar Dados* 
1. No Power BI Desktop, selecione a visualização para ativá-la.

2. Selecione **Mais ações** (...) e escolha **Mostrar dados**. 
    ![mostrar opção para Mostrar Dados](media/service-reports-show-data/power-bi-more-action.png)


3. Por predefinição, os dados são apresentados por baixo do elemento visual.
   
   ![apresentação vertical dos dados e elemento visual](media/service-reports-show-data/power-bi-show-data-below.png)

4. Para alterar a orientação, selecione o esquema vertical ![pequena captura de ecrã do ícone utilizado para alterar para esquema vertical](media/service-reports-show-data/power-bi-vertical-icon-new.png) no canto superior direito da visualização.
   
   ![apresentação horizontal dos dados e elemento visual](media/service-reports-show-data/power-bi-show-data-side.png)
5. Para exportar os dados para um ficheiro .csv, selecione as reticências e escolha **Exportar dados**.
   
    ![selecionar Exportar dados](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Para obter mais informações sobre como exportar dados para o Excel, veja [Exportar dados de visualizações do Power BI](power-bi-visualization-export-data.md).
6. Para ocultar os dados, anule a seleção **Explorar** > **mostrar dados**.

## <a name="using-show-records"></a>Utilizar Mostrar registos
Também pode concentrar-se num registo de dados numa visualização e explorar os dados. 

1. Para utilizar a opção **Ver registos**, selecione uma visualização para ativá-la. 

2. No friso de Ambiente de trabalho, selecione o separador de **Ferramentas visuais** > **Dados/Pormenorização** > **Ver registos**. 

    ![Captura de ecrã com Ver Registos selecionado.](media/service-reports-show-data/power-bi-see-record.png)

3. Selecione um ponto de dados ou linha na visualização. Neste exemplo, selecionámos a quarta coluna a contar da esquerda. O Power BI mostra-nos o registo do conjunto de dados deste ponto de dados.

    ![Captura de ecrã de registo único do conjunto de dados.](media/service-reports-show-data/power-bi-row.png)

4. Selecione **Voltar ao relatório** para regressar à tela de relatório do Ambiente de trabalho. 

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas

- Se o botão **Ver registos** no friso estiver desativado e indisponível, significa que a visualização selecionada não suporta a opção Ver Registos.
- Não pode alterar os dados na vista Ver Registos e guardá-los novamente no relatório.
- Não pode utilizar Ver Registos quando o elemento visual utiliza uma medida calculada.
- Não pode utilizar Ver Registos quando estiver ligado a um modelo multidimensional (MD).  

## <a name="next-steps"></a>Próximas etapas
[Exportar dados de visualizações do Power BI](power-bi-visualization-export-data.md)    

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

