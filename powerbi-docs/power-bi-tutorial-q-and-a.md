---
title: "Tutorial - utilizar Perguntas e Respostas num dashboard ou num relatório"
description: "Tutorial sobre como utilizar as Perguntas e Respostas do Power BI para criar novas visualizações em dashboards e relatórios."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
editor: 
tags: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/17/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 44501e5447248164f6f04d4463213939975e18ae
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="tutorial-how-to-use-qa-to-create-visualizations-and-build-reports"></a>Tutorial: Como utilizar as Perguntas e Respostas para criar visualizações e relatórios
A [descrição geral de Perguntas e Respostas](power-bi-q-and-a.md) apresentou-lhe as Perguntas e Respostas do Power BI e fez a distinção entre *consumidores* (com quem são partilhados dashboards e relatórios) e *criadores* (os proprietários dos relatórios e conjuntos de dados subjacentes). A primeira parte deste tutorial foi concebida principalmente para pessoas que consomem dashboards com o serviço Power BI. A segunda parte é concebida para as pessoas que criam relatórios através do serviço Power BI ou do Power BI Desktop. As [Perguntas e Respostas e o Power BI mobile](mobile-apps-ios-qna.md) e [Perguntas e Respostas com o Power BI Embedded](developer/qanda.md) são abordadas em artigos separados.

O P e R é interativo e até mesmo divertido e, mais frequentemente do que o contrário, uma pergunta levará a muitas outras, conforme as visualizações revelam caminhos interessantes a buscar. Veja a Amanda a demonstrar a utilização das Perguntas e Respostas para criar visualizações, aprofundar os elementos visuais e afixá-los a dashboards.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-power-bi-service-apppowerbicom"></a>Parte 1: Utilizar as Perguntas e Respostas num dashboard no serviço Power BI (app.powerbi.com)
Um dashboard contém mosaicos afixados a partir de um ou mais conjuntos de dados, pelo que pode fazer perguntas sobre quaisquer dados contidos em qualquer um desses conjuntos de dados. Para ver os relatórios e conjuntos de dados que foram utilizados para criar o dashboard, selecione **Ver relacionados** na barra de menus.

![](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

A caixa de pergunta das Perguntas e Respostas está localizada no canto superior esquerdo do dashboard e é aqui que vai escrever a sua pergunta com linguagem natural. O P e R reconhece as palavras que escreve e descobre onde (o conjunto de dados) encontrar a resposta. O P e R também o ajuda a criar a sua pergunta com preenchimento automático, ajuste e outros auxílios textuais e visuais.

![](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

A resposta à sua pergunta é apresentada como uma visualização interativa e atualiza à medida que modifica a pergunta.

1. Abra um dashboard e coloque o cursor na caixa de pergunta. Mesmo antes de começar a escrever, as Perguntas e Respostas apresentam um ecrã novo com sugestões para o ajudar a formular a sua pergunta. Irá ver os nomes das tabelas nos [conjuntos de dados subjacentes](service-get-data.md) e poderá até ver perguntas completas listadas se o proprietário do conjunto de dados tiver criado [perguntas em destaque](service-q-and-a-create-featured-questions.md).

   ![](media/power-bi-tutorial-q-and-a/powerbi-qna-cursor.png)

   Pode sempre escolher uma destas perguntas como ponto de partida e continuar a melhorar a pergunta para encontrar a resposta específica que está à procura. Ou utilize um nome de tabela para o ajudar a formar uma nova pergunta.

2. Selecione de entre as opções do conjunto de dados ou comece a escrever a sua própria pergunta e selecione de entre as sugestões da lista pendente.

   ![](media/power-bi-tutorial-q-and-a/powerbi-qna-list.png)

3. À medida que escreve uma pergunta, as Perguntas e Respostas escolhem a melhor [visualização](power-bi-visualization-types-for-reports-and-q-and-a.md) para apresentar a sua resposta e a visualização muda dinamicamente, à medida que modifica a pergunta.

   ![](media/power-bi-tutorial-q-and-a/powerbi-qna-viz.png)

4. Quando escreve uma pergunta, o Power BI procura a melhor resposta, utilizando qualquer conjunto de dados que tenha um mosaico nesse dashboard.  Se todos os mosaicos forem do *conjuntodedadosA*, a sua resposta será proveniente do *conjuntodedadosA*.  Se existirem mosaicos de *conjuntodedadosA* e *conjuntodedadosB*, as Perguntas e Respostas procuram a melhor resposta de entre esses dois conjuntos de dados.

   > [!TIP]
   > Por isso, tenha cuidado. Se tiver apenas um mosaico de *conjuntodedadosA* e o remover do dashboard, as Perguntas e Respostas deixam de ter acesso ao *conjuntodedadosA*.
   >
   >
5. Quando estiver satisfeito com o resultado, [afixe a visualização num dashboard](service-dashboard-pin-tile-from-q-and-a.md), ao selecionar o ícone para afixar no canto superior direito. Se o dashboard foi partilhado consigo ou fizer parte de uma aplicação, não poderá afixar.

   ![](media/power-bi-tutorial-q-and-a/pbi_qna_finish-typing-question.jpg)

##    <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Parte 2: Utilizar as Perguntas e Respostas num relatório no serviço Power BI ou no Power BI Desktop

Utilize as Perguntas e Respostas para explorar o conjunto de dados e adicionar visualizações ao relatório e aos dashboards. Um relatório baseia-se num único conjunto de dados e pode estar completamente em branco ou conter páginas repletas de visualizações. Mas o facto de um relatório estar em branco, não significa que não existem dados para explorar – o conjunto de dados está ligado ao relatório e está à espera que explore e crie visualizações.  Para ver que conjunto de dados está a ser utilizado para criar um relatório, abra o relatório na Vista de Leitura do serviço Power BI e selecione **Ver relacionados** na barra de menus.

![](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Para utilizar as Perguntas e Respostas em relatórios, tem de ter permissões de edição para o relatório e o conjunto de dados subjacente. No [tópico Descrição Geral das Perguntas e Respostas](power-bi-q-and-a.md), referimo-nos a este cenário como um cenário de *criador*. Por isso, se, em vez disso, estiver a *consumir* um relatório que foi partilhado consigo, as Perguntas e Respostas não estarão disponíveis.

1. Abra um relatório na Vista de edição (serviço Power BI) ou na Vista de relatório (Power BI Desktop) e selecione **Colocar uma pergunta** na barra de menus.

    **Desktop**    
    ![](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Serviço**    
    ![](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Uma caixa de pergunta das Perguntas e Respostas é apresentada na tela do relatório. No exemplo abaixo, a caixa de pergunta é apresentada sobre outra visualização. Não há problema, mas poderá ser melhor [adicionar uma página em branco ao relatório](power-bi-report-add-page.md) antes de fazer uma pergunta.

    ![](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Coloque o cursor na caixa de pergunta. À medida que escreve, as Perguntas e Respostas apresentam sugestões para o ajudar a formular a sua pergunta.

   ![](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. À medida que escreve uma pergunta, as Perguntas e Respostas escolhem a melhor [visualização](power-bi-visualization-types-for-reports-and-q-and-a.md) para apresentar a sua resposta e a visualização muda dinamicamente, à medida que modifica a pergunta.

   ![](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Quando tiver a visualização de que gosta, selecione ENTER. Para guardar a visualização com o relatório, selecione **Ficheiro > Guardar**.

6. Interaja com a nova visualização. Não interessa como criou a visualização – está disponível a mesma interatividade, formatação e funcionalidades.

  ![](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

  Se tiver criado a visualização no serviço Power BI, pode até [afixá-la a um dashboard](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Informe ao P e R a visualização que deve ser utilizada.
Com as Perguntas e Respostas, não só pode pedir aos seus dados que falem por si próprios, como também pode indicar ao Power BI como apresentar a resposta. Basta adicionar "como um <visualization type>" ao final da pergunta.  Por exemplo, "mostrar o volume de inventário pela fábrica como um mapa" e "mostrar inventário total como um cartão".  Experimente.

##  <a name="considerations-and-troubleshooting"></a>Considerações e resolução de problemas
- Se tiver ligado a um conjunto de dados com uma ligação em direto ou gateway, as Perguntas e Respostas têm de ser [ativadas para esse conjunto de dados](service-q-and-a-direct-query.md).

- Abriu um relatório e não vê a opção Perguntas e Respostas. Se estiver a utilizar o serviço Power BI, certifique-se de que o relatório está aberto na Vista de edição. Se não conseguir abrir a Vista de edição, significa que não tem permissões de edição para esse relatório e não poderá utilizar as Perguntas e Respostas com esse relatório específico.

## <a name="next-steps"></a>Próximos passos
Voltar a [Perguntas e Respostas no Power BI](power-bi-q-and-a.md)   
[Tutorial: Utilizar Perguntas e Respostas com o exemplo de Vendas a Retalho](power-bi-visualization-introduction-to-q-and-a.md)   
[Sugestões para fazer perguntas nas Perguntas e Respostas](service-q-and-a-tips.md)   
[Preparar um livro para Perguntas e Respostas](service-prepare-data-for-q-and-a.md)  
[Preparar um conjunto de dados no local para Perguntas e Respostas](service-q-and-a-direct-query.md)
[Afixar um mosaico ao dashboard a partir das Perguntas e Respostas](service-dashboard-pin-tile-from-q-and-a.md)
