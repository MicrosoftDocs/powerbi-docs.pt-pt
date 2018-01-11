---
title: Como usar o P e R do Power BI
description: Como usar o P e R do Power BI
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
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: a6736916a4bb2e94c1f5e1e3c3c3e5339cf990ec
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-use-power-bi-qa"></a>Como usar o P e R do Power BI
## <a name="ask-questions-of-your-data-using-natural-language"></a>Faça perguntas sobre os seus dados com linguagem natural
Comece num dashboard. Na caixa de pergunta do P e R escreva a sua pergunta com linguagem natural. O P e R reconhece as palavras que escreve e descobre onde (o conjunto de dados) encontrar a resposta. O P e R também o ajuda a criar a sua pergunta com preenchimento automático, ajuste e outros auxílios textuais e visuais.

![](media/service-how-to-q-and-a/powerbi-qna.png)

A resposta à sua pergunta é apresentada como uma visualização interativa e atualiza à medida que modifica a pergunta.

O P e R é interativo e até mesmo divertido e, mais frequentemente do que o contrário, uma pergunta levará a muitas outras, conforme as visualizações revelam caminhos interessantes a buscar. Veja Amanda a demonstrar a utilização de Perguntas e Respostas para criar elementos visuais, aprofundar esses elementos visuais e afixá-los a dashboards.

> [!NOTE]
> O P e R também está disponível na [aplicação Microsoft Power BI para iOS em iPads, iPhones e dispositivos iPod Touch](mobile-apps-ios-qna.md).
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="use-natural-language-to-ask-questions-about-your-data"></a>Utilizar linguagem natural para colocar perguntas sobre os dados
1. Coloque o cursor na caixa de pergunta. Mesmo antes de começar a escrever, as Perguntas e Respostas apresentam um ecrã novo com sugestões para o ajudar a formular a sua pergunta.
   
   ![](media/service-how-to-q-and-a/powerbi-qna-cursor.png)  
   
   Esta lista contém:  
   a.  as perguntas usadas para criar [mosaicos ](service-dashboard-tiles.md) que já estão afixados no dashboard e  
   b.  o nome das tabelas no(s) [conjunto(s) de dados subjacente(s)](service-get-data.md).  
   
   Pode sempre escolher uma destas perguntas como ponto de partida e continuar a melhorar a pergunta para encontrar a resposta específica que está à procura. Ou utilize um nome de tabela para o ajudar a formar uma nova pergunta.
2. Selecione no menu suspenso ou comece a escrever a sua própria pergunta.  
   
   ![](media/service-how-to-q-and-a/powerbi-qna-list.png)
3. Ao escrever uma pergunta, o P e R do Power BI escolhe a melhor [visualização](power-bi-visualization-types-for-reports-and-q-and-a.md) para apresentar a sua resposta; a visualização, por sua vez, muda dinamicamente conforme a pergunta é modificada. O P e R também ajuda a formular a sua pergunta com preenchimento automático, ao reformular a pergunta e com outros recursos textuais e visuais.  
   ![](media/service-how-to-q-and-a/powerbi-qna-viz.png)
4. Quando escreve uma consulta, o Power BI procura uma resposta em qualquer conjunto de dados que tenha um mosaico nesse dashboard.  Se todos os mosaicos forem do *conjuntodedadosA*, a sua resposta será proveniente do *conjuntodedadosA*.  Se existirem mosaicos de *conjuntodedadosA* e *conjuntodedadosB*, as Perguntas e Respostas procuram a melhor resposta de entre esses dois conjuntos de dados.
   
   > [!TIP]
   > Por isso, tenha cuidado. Se tiver apenas um mosaico de *conjuntodedadosA* e o remover do dashboard, as Perguntas e Respostas deixam de ter acesso ao *conjuntodedadosA*.
   > 
   > 
5. Quando estiver satisfeito com o resultado, [afixe a visualização num dashboard](service-dashboard-pin-tile-from-q-and-a.md), ao selecionar o ícone para afixar no canto superior direito. Se o dashboard foi partilhado consigo ou fizer parte de uma aplicação, não poderá afixar.
   
   ![](media/service-how-to-q-and-a/pbi_qna_finish-typing-question.jpg)

### <a name="tell-qa-which-visualization-to-use"></a>Informe ao P e R a visualização que deve ser utilizada.
Com o P e R, pode não só pedir os seus dados para falarem por si mesmo, como também pode dizer como deseja que sejam apresentados. Basta adicionar "como um <visualization type>" ao final da pergunta.  Por exemplo, "mostrar o volume de inventário pela fábrica como um mapa" e "mostrar inventário total como um cartão".  Experimente.

## <a name="how-does-qa-know-how-to-answer-questions"></a>Como é que o P e R sabe como responder às perguntas?
### <a name="which-datasets-does-qa-use"></a>Que conjuntos de dados o P e R utiliza?
Como é que o P e R sabe como responder a perguntas sobre dados específicos? Baseia-se nos nomes das tabelas, colunas e campos calculados nos conjuntos de dados subjacentes. Portanto, é importante que o utilizador (ou o proprietário do conjunto de dados) nomeie as coisas da melhor forma! 

Por exemplo, suponha que teve uma tabela do Excel como o nome "Vendas", com colunas intituladas "Produto", "Mês", "Unidades Vendidas", "Vendas Brutas" e "Lucro". Pode fazer perguntas sobre qualquer uma dessas entidades.  Pode perguntar "mostrar *vendas*, "lucro *total* por *mês*", "ordenar *produtos* por *unidades vendidas*", etc.

O Q e R pode responder a perguntas com base em como o conjunto de dados é organizado. Como funciona para dados no Salesforce? Quando se ligar à sua conta do salesforce.com, o Power BI gera automaticamente um dashboard.  Antes de começar a fazer perguntas com o P e R, veja os dados apresentados nas visualizações do dashboard e nos dados apresentados no menu suspenso do P e R.

* Se os valores e as etiquetas do eixo das visualizações incluírem "vendas", "conta", "mês" e "oportunidades", pode fazer perguntas como: "que *conta* tem a *oportunidade* mais alta" ou "mostrar *vendas* por mês como um gráfico de barras".
* Se a lista pendente incluir "vendedor", "estado" e "ano", pode fazer perguntas como: "que *vendedor* teve as *vendas* mais baixas na *Florida* em *2013*".

Se tiver dados de desempenho do site no Google Analytics, pode perguntar ao P e R sobre o tempo gasto numa página Web, o número de visitas à página exclusivo e taxas de envolvimento do utilizador. Ou, se estiver a consultar dados demográficos, pode fazer perguntas sobre a idade e a renda doméstica por local.

### <a name="which-visualization-does-qa-use"></a>Que visualização o P e R utiliza?
O P e R escolhe a melhor visualização com base nos dados que são apresentados. Às vezes, os dados nos conjuntos de dados subjacentes são definidos como um determinado tipo ou categoria, o que ajuda o P e R a saber como apresentá-los. Por exemplo, se os dados são definidos como um tipo de data, é mais provável que sejam apresentados como um gráfico de linhas. Os dados que são categorizados como uma cidade são mais prováveis de serem apresentados como um mapa.

Também pode informar ao P e R a visualização que será utilizada ao adicioná-la à sua pergunta. Mas tenha em mente que não será sempre possível apresentar os dados no tipo de visualização que pediu.

Para obter informações sobre as palavras-chave reconhecidas pelas Perguntas e Respostas, veja [Sugestões para fazer perguntas](service-q-and-a-tips.md).

## <a name="next-steps"></a>Próximos passos
Voltar ao [P e R no Power BI](service-q-and-a.md)  
[Tutorial: Utilizar Perguntas e Respostas com o exemplo de Vendas a Retalho](power-bi-visualization-introduction-to-q-and-a.md)  
[Sugestões para fazer perguntas nas Perguntas e Respostas](service-q-and-a-tips.md)  
[Preparar um livro para Perguntas e Respostas](service-prepare-data-for-q-and-a.md)  
[Afixar um mosaico ao dashboard a partir das Perguntas e Respostas](service-dashboard-pin-tile-from-q-and-a.md)  

