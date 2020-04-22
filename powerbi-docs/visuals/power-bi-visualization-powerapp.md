---
title: Incorporar um novo Power App num Relatório do Power BI
description: Incorporar uma aplicação que utiliza a mesma origem de dados e pode ser filtrada como outros itens de relatório
author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 03/17/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5628a114b872b7c0d92d5079198616a20fe85b87
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637779"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Tutorial: Incorporar um elemento visual do Power Apps num relatório Power BI

Neste tutorial, vai utilizar o elemento visual do Power Apps para criar uma nova aplicação incorporada num relatório de exemplo do Power BI. Esta aplicação interage com outros elementos visuais nesse relatório.

Se não tiver uma subscrição do Power Apps, [crie uma conta gratuita](https://web.powerapps.com/signup?redirect=marketing&email=) antes de começar.

Neste tutorial, vai aprender a:
> [!div class="checklist"]
> * Adicionar um elemento visual do Power Apps a um relatório do Power BI
> * Trabalhar no Power Apps para criar uma nova aplicação que utiliza dados do relatório do Power BI
> * Ver e interagir com o elemento visual do Power Apps no relatório

## <a name="prerequisites"></a>Pré-requisitos

* Browser [Google Chrome](https://www.google.com/chrome/browser/) ou [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)
* Uma [subscrição do Power BI](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi) com o [Exemplo de Análise de Oportunidade](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample) instalado
* Uma compreensão de como [criar aplicações no Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) e como [editar relatórios do Power BI](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)



## <a name="create-a-new-app"></a>Criar uma nova aplicação
Ao adicionar o elemento visual do Power Apps ao relatório, este inicia o Power Apps Studio com uma ligação de dados em direto entre o Power Apps e o Power BI.

1. Abra o relatório de amostra de Análise de Oportunidades e selecione a página *Oportunidades Futuras*. 


2. Mova e redimensione alguns dos mosaicos do relatório para disponibilizar espaço para um novo elemento visual.

    ![Mover e redimensionar mosaicos de relatório](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. No painel visualizações, selecione o ícone do Power Apps e redimensione o elemento visual para se ajustar ao espaço criado.

    ![Painel Visualização com o ícone do Power Apps selecionado](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. No painel **Campos**, selecione **Nome**, **Código do Produto** e **Fase de Venda**. 

    ![selecionar campos](media/power-bi-visualization-powerapp/power-bi-fields.png)

4. No elemento visual do Power Apps, selecione o ambiente do Power Apps onde quer criar a aplicação e, em seguida, selecione **Criar nova**.

    ![Criar uma nova aplicação](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    No Power Apps Studio, verá que é criada uma aplicação básica com uma *galeria* que mostra um dos campos que selecionou no Power BI.

    ![O Power Apps é aberto](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Redimensione a galeria para que ocupe apenas metade do ecrã. 

6. No painel esquerdo, selecione **Screen1** e, em seguida, defina a propriedade **Preenchimento** do ecrã como “"LightBlue” (para que seja mais visível no relatório).

    ![paleta de cores](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Arranje espaço para um controlo de etiquetas. 

    ![alterar dimensões da galeria](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. Em **galeria**, insira um controlo de etiqueta de texto.

   ![controlo de etiqueta](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Arraste a etiqueta para o fundo do elemento visual. Defina a propriedade de **Texto** como `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. É agora apresentado o número total de oportunidades no conjunto de dados.

    ![Aplicação com galeria redimensionada](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![Aplicação com etiqueta atualizada](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Guarde a aplicação com o nome “Aplicação de oportunidades”. 

    ![guardar a aplicação](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>Ver a aplicação no relatório
A aplicação está agora disponível no relatório do Power BI e interage com outros elementos visuais, porque partilha a mesma origem de dados.

![Aplicação no relatório do Power BI](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

No relatório do Power BI, selecione **Jan** na segmentação de dados que filtra todo o relatório, incluindo os dados na aplicação.

![relatório filtrado](media/power-bi-visualization-powerapp/power-bi-last.png)

Tenha em atenção que a contagem de oportunidades na aplicação corresponde à contagem no canto superior esquerdo do relatório. Pode selecionar outros itens no relatório e os dados na aplicação serão atualizados.


## <a name="clean-up-resources"></a>Limpar recursos
Se não quiser continuar a utilizar o Exemplo de Análise de Oportunidade, pode eliminar o dashboard, o relatório e o conjunto de dados.


## <a name="next-steps"></a>Próximos passos
[Q&A visual](power-bi-visualization-types-for-reports-and-q-and-a.md)   (Elemento visual Perguntas e Respostas)  
[Tutorial: Incorporar um elemento visual do Power Apps num relatório Power BI](https://docs.microsoft.com/powerapps/maker/canvas-apps/powerapps-custom-visual)