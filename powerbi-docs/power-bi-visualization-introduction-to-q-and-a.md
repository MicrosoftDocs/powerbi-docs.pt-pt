---
title: Introdução às Perguntas e Respostas no Power BI
description: Introdução às Perguntas e Respostas do serviço Power BI com o exemplo de Análise de Revenda
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 87783b928fdec1cadf5318ae184858c37daa4acc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279257"
---
# <a name="get-started-with-power-bi-qa"></a>Introdução às Perguntas e Respostas no Power BI

Às vezes, a maneira mais rápida de obter uma resposta dos seus dados é fazer uma pergunta em linguagem natural.  Neste guia de início rápido, examinaremos duas formas diferentes de criar a mesma visualização: em primeiro lugar, criá-la num relatório e, em segundo lugar, fazer uma pergunta com as Perguntas e Respostas. Iremos utilizar o serviço Power BI, mas o processo é quase idêntico a utilizar o Power BI Desktop.

Para acompanhar, tem de utilizar um relatório que possa editar, por isso iremos utilizar um dos exemplos disponíveis com o Power BI.

## <a name="create-a-visual-in-the-report-editor"></a>Criar um elemento visual no editor de relatórios

1. Na área de trabalho do Power BI, selecione **Obter Dados** \> **Exemplos** \> **Exemplo de Análise de Revenda** > **Ligar**.
   
2. O dashboard contém um mosaico de gráfico de área para "Vendas do Último Ano e Vendas Deste Ano".  Selecione este mosaico. Se este mosaico foi criado com o P e R, selecionar o mosaico vai abrir o P e R. Mas este mosaico foi criado num relatório, portanto o relatório é aberto para a página que contém esta visualização.

    ![Dashboard de exemplo de Análise de Revenda](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Abra o relatório na Vista de Edição selecionando **Editar Relatório**.  Se não for proprietário de um relatório, não terá a opção de abrir o relatório na Vista de Edição.
   
    ![Botão Editar relatório](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecione o gráfico de área e reveja as definições no painel **Campos**.  O criador do relatório criou este gráfico ao selecionar estes três valores (**Hora > MêsFiscal**, **Vendas > Vendas Deste Ano**, **Vendas > Vendas do Ano Passado > Valor**) e organizá-los nas secções **Eixos** e **Valores**.
   
    ![Painel Visualizações](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="create-the-same-visual-with-qa"></a>Criar o mesmo elemento visual com as Perguntas e Respostas

Como podemos criar este mesmo gráfico de linhas com o P e R?

![Caixa Colocar uma questão sobre os dados](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Navegue de volta para o dashboard do Exemplo de Análise de Revenda.
2. Com linguagem natural, escreva algo como esta pergunta na caixa de perguntas:
   
   **quais foram as vendas deste ano e as vendas do ano passado por mês como um gráfico de área**
   
   Ao escrever a pergunta, o P e R escolhe a melhor visualização para apresentar a sua resposta, e a visualização muda dinamicamente, na medida em que modifica a pergunta. Além disso, as Perguntas e Respostas ajudam a formatar a sua pergunta com sugestões, preenchimento automático e correções ortográficas.
   
   Quando terminar de escrever a sua pergunta, o resultado será exatamente o mesmo gráfico que vimos no relatório.  Mas criá-lo desta forma era muito mais rápido!
   
   ![Exemplo de pergunta](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. Da mesma forma como trabalha com relatórios, dentro das Perguntas e Respostas, tem acesso aos painéis Visualizações, Filtros e Campos.  Abra estes painéis para explorar e modificar mais o seu elemento visual.
4. Para afixar o gráfico no seu dashboard, selecione o ícone de afixar ![Ícone de afixar](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Próximos passos
[Perguntas e Respostas no Power BI](consumer/end-user-q-and-a.md)

[Fazer com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI](service-prepare-data-for-q-and-a.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

