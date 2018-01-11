---
title: "Introdução às Perguntas e Respostas do Power BI (Tutorial)"
description: "Tutorial: Introdução às Perguntas e Respostas do Power BI com o exemplo de Análise de Revenda"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 2038fb5bd4a21235c3026c8506ae30b8c3e287e4
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="get-started-with-power-bi-qa-tutorial"></a>Introdução às Perguntas e Respostas do Power BI (Tutorial)
## <a name="tutorial-use-power-bi-qa-with-the-retail-analysis-sample"></a>Tutorial: utilizar o P e R do Power BI com o exemplo de Análise de Retalho
Às vezes, a forma mais rápida de obter uma resposta dos seus dados é fazer uma pergunta com linguagem natural.  Neste tutorial, examinaremos duas formas diferentes de criar a mesma visualização: criá-la num relatório e fazer uma pergunta com o P e R.  

## <a name="method-1-using-the-report-editor"></a>Método 1: utilizar o editor de relatórios
1. Na área de trabalho do Power BI, selecione **Obter Dados** \> **Exemplos** \> **Exemplo de Análise de Revenda** > **Ligar**.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)
2. O dashboard contém um mosaico de gráfico de área para "Vendas do Último Ano e Vendas Deste Ano".  Selecione este mosaico. 
   
   * Se este mosaico foi criado com o P e R, selecionar o mosaico vai abrir o P e R. 
   * Mas este mosaico foi criado num relatório, portanto o relatório é aberto para a página que contém esta visualização.
3. Abra o relatório na Vista de Edição selecionando **Editar Relatório**.  Se não for proprietário de um relatório, não terá a opção de abrir o relatório na vista de edição.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecione o gráfico de área e reveja as definições no painel **Campos**.  O criador do relatório criou este gráfico selecionando estes 3 valores (**Hora > FiscalMonth**, **Vendas > Vendas deste ano**, **Vendas > Vendas do ano passado > Valor**) e organizando-os nas secções **Eixos** e **Valores**.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="method-2-using-qa"></a>Método 2: utilizar as perguntas e respostas
Como podemos criar este mesmo gráfico de linhas com o P e R?

![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Navegue de volta para o dashboard do Exemplo de Análise de Revenda.
2. Com linguagem natural, escreva algo deste género na caixa de pergunta:
   
   **quais foram as vendas deste ano e as vendas do ano passado por mês como um gráfico de área**
   
   Ao escrever a pergunta, o P e R escolhe a melhor visualização para apresentar a sua resposta, e a visualização muda dinamicamente, na medida em que modifica a pergunta. Além disso, o P e R ajuda-o a formatar a sua pergunta com sugestões, preenchimento automático e correções ortográficas.
   
   Quando terminar de escrever a sua pergunta, o resultado será exatamente o mesmo gráfico que vimos no relatório.  Mas criá-lo desta forma era muito mais rápido!
   
   ![](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. Da mesma forma como quando trabalha com relatórios, dentro das Perguntas e Respostas, tem acesso aos painéis de Visualizações, Filtros e Campos.  Abra estes painéis para explorar e modificar mais o seu elemento visual.
4. Para afixar o gráfico ao dashboard, selecione o ícone de pino ![](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Próximos passos
[Que tipo de perguntas posso fazer nas Perguntas e Respostas?](service-q-and-a.md)

[Perguntas e Respostas no Power BI](service-q-and-a.md)

[Fazer com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI](service-prepare-data-for-q-and-a.md)

[preparar um livro para as Perguntas e Respostas](service-prepare-data-for-q-and-a.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

