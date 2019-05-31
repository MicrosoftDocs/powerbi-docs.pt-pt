---
title: Criar um elemento visual com o Power BI Q e r
description: Aprenda a criar um elemento visual com as perguntas e respostas no serviço Power BI com o exemplo de análise de revenda
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 580b387f8c763b0457bd32a71bfbccd90d4040a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625172"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Criar um elemento visual com o Power BI Q e r

Às vezes, a maneira mais rápida de obter uma resposta dos seus dados é fazer uma pergunta em linguagem natural.  Neste artigo, vamos ver duas formas diferentes de criar a mesma visualização: primeiro, fazer uma pergunta com as perguntas e respostas e, em segundo lugar, criá-la num relatório. Utilizamos o serviço Power BI para criar o elemento visual no relatório, mas o processo é quase idêntico a utilizar o Power BI Desktop.

![Gráfico do Power BI preenchida](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Para acompanhar, tem de utilizar um relatório que possa editar, por isso iremos utilizar um dos exemplos disponíveis com o Power BI.

## <a name="create-a-visual-with-qa"></a>Criar um elemento visual com as perguntas e respostas

Como podemos sobre como criar este gráfico de linhas com as perguntas e respostas?

1. Na área de trabalho do Power BI, selecione **Obter Dados** \> **Exemplos** \> **Exemplo de Análise de Revenda** > **Ligar**.

1. Abra o dashboard de exemplo de análise de revenda e coloque o cursor numa caixa de perguntas e **faça uma pergunta sobre os seus dados**.

    ![Coloque o cursor na caixa do p e r](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Em perguntas e respostas uma caixa, escreva algo semelhante a esta pergunta:
   
    **vendas deste ano e vendas do ano passado por mês como gráfico de área**
   
    Ao escrever a pergunta, o P e R escolhe a melhor visualização para apresentar a sua resposta, e a visualização muda dinamicamente, na medida em que modifica a pergunta. Além disso, as Perguntas e Respostas ajudam a formatar a sua pergunta com sugestões, preenchimento automático e correções ortográficas. As perguntas e respostas recomenda uma alteração de texto pequeno: "vendas deste ano e vendas do ano passado por *mês de tempo* como gráfico de área".  

    ![As perguntas e respostas corrigido palavras utilizadas](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Selecione a frase para aceitar a sugestão. 
   
   Quando terminar de escrever a sua pergunta, o resultado é o mesmo gráfico que vê no dashboard.
   
   ![Gráfico de área de preenchida de perguntas e respostas](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Para afixar o gráfico no seu dashboard, selecione o ícone de afixar ![Ícone de afixar](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) no canto superior direito.

## <a name="create-a-visual-in-the-report-editor"></a>Criar um elemento visual no editor de relatórios

1. Navegue de volta para o dashboard do Exemplo de Análise de Revenda.
   
2. O dashboard contém o mesmo mosaico de gráfico de área para "Vendas do ano passado e vendas deste ano".  Selecione este mosaico. Não selecione o mosaico que criou com perguntas e respostas. Selecionando-abre as perguntas e respostas. O mosaico de gráfico de área original foi criado num relatório, para que o relatório abre a página que contém esta visualização.

    ![Dashboard de exemplo de Análise de Revenda](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Abra o relatório na Vista de Edição selecionando **Editar Relatório**.  Se não for proprietário de um relatório, não terá a opção de abrir o relatório na Vista de Edição.
   
    ![Botão Editar relatório](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecione o gráfico de área e reveja as definições no painel **Campos**.  O criador do relatório criou este gráfico selecionando estes três valores (**vendas do ano passado** e **vendas deste ano > valor** partir os **vendas** tabela, e  **FiscalMonth** partir a **tempo** tabela) e organizando-os no **eixo** e **valores** wells.
   
    ![Painel Visualizações](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Verá que fim com o mesmo elemento visual. Criá-lo dessa maneira não era muito complicado. Mas criá-lo com as perguntas e respostas foi mais fácil!

## <a name="next-steps"></a>Próximos passos

- [Utilizar as perguntas e respostas em dashboards e relatórios](power-bi-tutorial-q-and-a.md)  
- [As perguntas e respostas para os consumidores](consumer/end-user-q-and-a.md)
- [Fazer com que os seus dados funcionem bem com as Perguntas e Respostas no Power BI](service-prepare-data-for-q-and-a.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

