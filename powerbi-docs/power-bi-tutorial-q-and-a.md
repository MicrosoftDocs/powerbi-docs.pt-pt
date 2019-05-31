---
title: Utilizar o Power BI Q e r para explorar e criar elementos visuais
description: Como utilizar o Power BI P e r para criar novas visualizações em dashboards e relatórios.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: c6fd8967a49515af4d0614653b3d7550c335052f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625495"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Utilizar o Power BI Q e r para explorar os seus dados e criar elementos visuais

Às vezes, a maneira mais rápida de obter uma resposta dos seus dados é fazer uma pergunta em linguagem natural. A funcionalidade de perguntas e respostas no Power BI permite-lhe explorar os seus dados nas suas próprias palavras.  A primeira parte deste artigo mostra como utilizar as perguntas e respostas em dashboards no serviço Power BI. A segunda parte mostra o que pode fazer com as perguntas e respostas na criação de relatórios no serviço Power BI ou no Power BI Desktop. Para obter mais informações, veja a [perguntas e respostas para os consumidores](consumer/end-user-q-and-a.md) artigo. 

[As perguntas e respostas em aplicações móveis do Power BI](consumer/mobile/mobile-apps-ios-qna.md) e [perguntas e respostas com o Power BI Embedded](developer/qanda.md) são abordadas em artigos separados. 

O p e r são interativo e até mesmo divertida. Muitas vezes, uma pergunta nos leva a outras pessoas conforme as visualizações revelam caminhos interessantes a buscar. Veja a Amanda a demonstrar a utilização das Perguntas e Respostas para criar visualizações, aprofundar os elementos visuais e afixá-los a dashboards.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>Parte 1: Utilizar as perguntas e respostas num dashboard no serviço Power BI

No serviço Power BI (app.powerbi.com), um dashboard contém mosaicos afixados a partir de um ou mais conjuntos de dados, pelo que pode fazer perguntas sobre quaisquer dados contidos em qualquer um desses conjuntos de dados. Para ver os relatórios e conjuntos de dados que foram utilizados para criar o dashboard, selecione **ver relacionados** na barra de menus.

![Ver relatórios relacionados e conjuntos de dados](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

A caixa de pergunta perguntas e respostas está localizada no canto superior esquerdo do dashboard, onde escreve a sua pergunta com linguagem natural. Não vê a caixa do p e R? Ver [considerações e resolução de problemas](consumer/end-user-q-and-a.md#considerations-and-troubleshooting) no **perguntas e respostas para os consumidores** artigo.  P e r reconhece as palavras que escreve e descobre onde (em que conjunto de dados) para encontrar a resposta. O P e R também o ajuda a criar a sua pergunta com preenchimento automático, ajuste e outros auxílios textuais e visuais.

![Caixa de perguntas das perguntas e respostas](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

A resposta à sua pergunta é apresentada como uma visualização interativa e atualiza à medida que modifica a pergunta.

1. Abra um dashboard e coloque o cursor na caixa de pergunta. No canto superior direito, selecione **novas perguntas e respostas uma experiência**.

    ![Power BI novo perguntas e respostas uma experiência](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Mesmo antes de começar a escrever, as Perguntas e Respostas apresentam um ecrã novo com sugestões para o ajudar a formular a sua pergunta. Ver expressões e perguntas completas, que contém os nomes das tabelas em conjuntos de dados subjacentes e poderá até ver perguntas completas listadas se o proprietário de conjunto de dados criou [perguntas em destaque](service-q-and-a-create-featured-questions.md),

   ![As perguntas e respostas sugerem perguntas](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Pode escolher uma destas perguntas como ponto de partida e continuar a melhorar a pergunta para encontrar uma resposta específica. Ou utilize um nome de tabela para ajudar a formar uma nova pergunta.

2. Selecione na lista de perguntas, ou comece a escrever sua própria pergunta e selecione as sugestões de lista pendente.

   ![Selecione uma pergunta na lista](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. À medida que escreve uma pergunta, o p e r escolhe a melhor visualização para apresentar a sua resposta.

   ![As perguntas e respostas armazena quantos por Estado](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. A visualização muda dinamicamente à medida que modifica a pergunta.

   ![As perguntas e respostas armazena quantos por estado como gráfico de barras](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. Quando escreve uma pergunta, o Power BI procura a melhor resposta, utilizando qualquer conjunto de dados que tenha um mosaico nesse dashboard.  Se todos os mosaicos forem do *conjuntodedadosA*, a sua resposta será proveniente do *conjuntodedadosA*.  Se existirem mosaicos a partir de *Conjuntodedadosa* e *Conjuntodedadosb*, em seguida, as perguntas e respostas procura a melhor resposta desses conjuntos de dados de 2.

   > [!TIP]
   > Por isso, tenha cuidado. Se tiver apenas um mosaico de *conjuntodedadosA* e o remover do dashboard, as Perguntas e Respostas deixam de ter acesso ao *conjuntodedadosA*.
   >

5. Quando estiver satisfeito com o resultado, afixar a visualização a um dashboard ao selecionar o ícone de pin no canto superior direito. Se o dashboard foi partilhado consigo ou fizer parte de uma aplicação, não poderá afixar.

   ![As perguntas e respostas afixar o elemento visual](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Parte 2: Utilizar as Perguntas e Respostas num relatório no serviço Power BI ou no Power BI Desktop

Utilize as Perguntas e Respostas para explorar o conjunto de dados e adicionar visualizações ao relatório e aos dashboards. Um relatório baseia-se num único conjunto de dados e pode estar completamente em branco ou conter páginas repletas de visualizações. Mas o facto de um relatório estar em branco, não significa que não existem dados para explorar – o conjunto de dados está ligado ao relatório e está à espera que explore e crie visualizações.  Para ver que conjunto de dados está a ser utilizado para criar um relatório, abra o relatório na Vista de Leitura do serviço Power BI e selecione **Ver relacionados** na barra de menus.

![Ver conjuntos de dados relacionados](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Para utilizar as perguntas e respostas em relatórios, tem de ter permissões de edição para o relatório e conjunto de dados subjacente. Na [perguntas e respostas para os consumidores](consumer/end-user-q-and-a.md) artigo, nos Referimos a isso como um *criador* cenário. Se em vez disso, *consumindo* um relatório que tenha sido partilhado consigo, as perguntas e respostas não está disponível.

1. Abra um relatório na vista de edição (serviço do Power BI) ou de relatório (Power BI Desktop) e selecione **faça uma pergunta** na barra de menus.

    **O ambiente de trabalho do Power BI**    
    ![Faça uma pergunta no Power BI Desktop, selecione](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Serviço**    
    ![Selecione a fazer uma pergunta no serviço Power BI](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Uma caixa de pergunta das Perguntas e Respostas é apresentada na tela do relatório. No exemplo abaixo, a caixa de pergunta é apresentada sobre outra visualização. Não há problema, mas pode ser melhor adicionar uma página em branco ao relatório antes de fazer uma pergunta.

    ![Caixa de perguntas das perguntas e respostas](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Coloque o cursor na caixa de pergunta. À medida que escreve, as Perguntas e Respostas apresentam sugestões para o ajudar a formular a sua pergunta.

   ![Escreva na caixa de perguntas e](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. À medida que escreve uma pergunta, as Perguntas e Respostas escolhem a melhor [visualização](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md) para apresentar a sua resposta e a visualização muda dinamicamente, à medida que modifica a pergunta.

   ![As perguntas e respostas cria uma visualização](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Quando tiver a visualização de que gosta, selecione ENTER. Para guardar a visualização com o relatório, selecione **Ficheiro > Guardar**.

6. Interaja com a nova visualização. Não interessa como criou a visualização – está disponível a mesma interatividade, formatação e funcionalidades.

   ![Interagir com a visualização](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Se tiver criado a visualização no serviço Power BI, pode até [afixá-la a um dashboard](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Informe as Perguntas e Respostas sobre qual a visualização a utilizar
Com as Perguntas e Respostas, não só pode pedir aos seus dados que falem por si próprios, como também pode indicar ao Power BI como apresentar a resposta. Basta adicionar "como um <visualization type>" ao final da pergunta.  Por exemplo, "mostrar o volume de inventário pela fábrica como um mapa" e "mostrar inventário total como um cartão".  Experimente.

## <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- Se tiver ligado a um conjunto de dados com uma ligação em direto ou gateway, as Perguntas e Respostas têm de ser [ativadas para esse conjunto de dados](service-q-and-a-direct-query.md).

- Abriu um relatório e não vê a opção Perguntas e Respostas. Se estiver a utilizar o serviço Power BI, certifique-se de que o relatório está aberto na Vista de edição. Se não conseguir abrir a vista de edição, significa que não tem permissões de edição para esse relatório e pode usar as perguntas e respostas com esse relatório específico.

## <a name="next-steps"></a>Próximos passos

- [As perguntas e respostas para os consumidores](consumer/end-user-q-and-a.md)   
- [Sugestões para fazer perguntas nas Perguntas e Respostas](consumer/end-user-q-and-a-tips.md)   
- [Preparar um livro para Perguntas e Respostas](service-prepare-data-for-q-and-a.md)  
- [Preparar um conjunto de dados no local para as perguntas e respostas](service-q-and-a-direct-query.md)   
- [Afixar um mosaico ao dashboard a partir das Perguntas e Respostas](service-dashboard-pin-tile-from-q-and-a.md)
