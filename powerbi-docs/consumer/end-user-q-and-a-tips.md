---
title: Sugestões e truques para fazer perguntas com as Perguntas e Respostas
description: Dicas e truques para fazer perguntas com as Perguntas e Respostas do Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 4f6dc7167d64385182ecbd448b6c400fa7f829df
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408179"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Dicas para fazer perguntas nas Perguntas e Respostas do Power BI
## <a name="words-and-terminology-that-qa-recognizes"></a>Palavras e terminologia reconhecidas pelas Perguntas e Respostas
A lista de palavras-chave nesta página não é exaustiva.  A melhor forma de saber se o Power BI reconhece uma palavra-chave é escrevê-la na caixa de perguntas.  Se a palavra ou o termo estiver a cinzento, o Power BI não o reconhece.

A lista abaixo utiliza o tempo verbal presente, mas todos os tempos são reconhecidos na maioria dos casos. Por exemplo, "é" inclui: **são**, **foi**, **foram**, **será**, **têm**, **tem**, **tinha**, **terá**, **teve**, **fazer**, **faz**, **fez**.  "Ordena" inclui **ordenado** e **ordenação**.  Além disso, o Power BI reconhece e inclui versões singulares e plurais de uma palavra. 

> [!NOTE]
> O P e R também está disponível na [aplicação Microsoft Power BI para iOS em iPads, iPhones e dispositivos iPod Touch](mobile/mobile-apps-ios-qna.md).
>  


|Categoria  |Palavras-chave  |Coluna3  |
|---------|---------|---------|
|**Agregados**     | total, sum, amount, number, quantity, count, average, most, least, fewest, largest, smallest, highest, biggest, maximum, max, greatest, lowest, littlest, minimum, min          |
|     |         |         
**Artigos**     |  um, uma, o/a              |
|     |         |         
|**Vazio e Booleano**     |   branco, vazio, nulo, com prefixo de "não" ou "não-", cadeia vazia, texto vazio, verdadeiro, v, falso, f          |
|     |         |         |
|**Comparações**     |   vs, versus, comparado a, comparado com            |
|     |         |         |
|**Conjunções**     |  e, ou, cada, com, versus, &, e, mas, nem, juntamente com, além de       |         
|          |         |
|**Contrações**     |  As Perguntas e Respostas reconhecem quase todas as contrações. Experimente.  Eis alguns exemplos: não foi, não fez, ele fez, ele é, não é, é, ela vai, eles fizeram, não foram, quem é, não vai, não iria          |
|        |         |
|**Datas**     |       O Power BI reconhece a maioria dos termos de datas (dia, semana, mês, ano, trimestre, década, etc.) e datas escritas em muitos formatos diferentes (veja abaixo). O Power BI também reconhece as seguintes palavras-chave: MonthName, dias 1-31, década. Exemplos: 3 de janeiro de 1995, 3 janeiro 1995, 03 jan 1995, 3 jan 1995, dia 3 de janeiro, janeiro de 1995, 1995 janeiro, 1995-01, 01/1995, nomes de meses         |
|        |         |
|**Datas relativas**     |   hoje, agora, hora atual, ontem, amanhã, atual, próximo, último, anterior, há, antes, antes de, depois de, posterior a, desde, às, em, daqui a, depois de agora, no futuro, passado, últimos, anteriores, em, ao longo de, há N dias, daqui a N dias, próximo, uma vez, duas vezes.|
|    |  Exemplo: contagem de encomendas nos últimos 6 dias.  |            |
|        |         |
|**Igualdade (Intervalo)**     |   em, igual a, =, depois de, é mais de, em, entre, antes de  |
|  |Exemplos: O ano de encomenda é antes de 2012? Preço é igual a entre 10 e 20? A idade de João é superior a 40? Vendas totais em 200-300?              |
|        |         |
|**Igualdade (Valor)**     |   é, igual, igual a, em, de, para, dentro de, está em, é em |
|   | Exemplos: Que produtos são verdes? Data de encomenda é igual a 2012. A idade de João é 40? Vendas totais que não são iguais a 200? Data de encomenda de 1/1/2016. 10 em preço? Verde para cor? 10 em preço?              |
|        |         |
|**Nomes**     |       Se uma coluna no conjunto de dados tiver a expressão "nome" (por exemplo, EmployeeName), as perguntas e respostas compreendem que os valores nessa coluna são os nomes. Pode fazer perguntas como "que colaboradores têm o nome Roberto."          |
|        |         |
**Pronomes**  | ele, lho, dele, ela, lha, dela, aquilo, daquilo, lhe, lhes, deles, isto, estes, aquilo, aqueles
|**Comandos de consulta**     |    ordenado, ordenar por, direção, agrupar por, por, mostrar, listar, mostrar, dar-me, nome, apenas, só, dispor, classificar, comparar, para, com, contra, alfabeticamente, ascendente, descendente, ordenar             |
|        |         |
|**Intervalo**     |      maior do que, mais, maior, sobre, >, menos, menor do que, menos do que, abaixo de, sob, <, pelo menos, no mínimo, >=, até, no máximo, <=, em, entre, no intervalo de, a partir de, depois de, antes de, antes, depois, em, ao, posterior a, após, desde, a começar por, a começar desde, a terminar com           |
|        |         |
**Vezes**  |am, pm, em ponto, meio-dia, meia-noite, hora, minuto, segundo, hh:mm:ss  |
|  |  Exemplos: 22:00, 22:35, 22:35:15, 10 em ponto, meio-dia, meia-noite, hora, minuto, segundo.  |
|  |  |
|**Maiores N**     |     (ordem, classificação): maiores, menores, mais altos, mais baixos, primeiro, último, seguinte, primeiros, mais recentes, mais antigos, últimos, mais recente, próximo            |
|        |         |
|**Tipos visuais**     |  todos os tipos visuais nativos do Power BI.  Se for uma opção no painel Visualizações, pode incluí-lo na sua pergunta.  A exceção à regra são os [elementos visuais personalizados](../power-bi-custom-visuals.md) que adicionou manualmente ao painel Visualização.  |
|  |  Exemplo: mostrar distritos por mês e total de vendas como gráfico de barras               |
|        |         |
|**Q (relação qualificada)**  | quando, onde, qual, quem, a quem, quantos, quanto, quantas vezes, com que frequência, montante, número, quantidade, quanto tempo, o quê                |

## <a name="qa-helps-you-phrase-the-question"></a>As Perguntas e Respostas ajudam-no a formular a pergunta
As perguntas e respostas tentam ao máximo compreender e responder à pergunta que está a ser feita. Tentam entender de várias formas. Pode aceitar a ação por completo, parcialmente ou de modo algum em todas estas expressões. Ao escrever a sua pergunta, as Perguntas e Respostas:

* preenchem automaticamente palavras e perguntas. Utilizam várias estratégias, incluindo palavras reconhecidas com preenchimento automático, palavras armazenadas e perguntas utilizadas anteriormente que devolveram respostas válidas. Se houver mais do que uma opção de preenchimento automático disponível, as mesmas serão apresentadas numa lista pendente.
* corrige a ortografia.
* apresentam uma pré-visualização da resposta sob a forma de um elemento visual. O elemento visual é atualizado à medida que escreve e edita a pergunta (não espera até que prima Enter).
* sugerem automaticamente termos de substituição do(s) conjunto(s) de dados subjacente(s) quando move o cursor de novo para a caixa de perguntas.
* reformula a pergunta com base nos dados do(s) conjunto(s) de dados subjacente(s). As perguntas e respostas substituem as palavras que utilizou por sinónimos do(s) conjunto(s) de dados subjacente(s). Ao ler a reformulação, sabe se as perguntas e respostas perceberam a sua pergunta ou não. 
* esbate as palavras que não são entendidas.

## <a name="dont-stop-now"></a>Não parar agora
Depois de as Perguntas e Respostas exibirem os resultados, mantenha a conversa! Use as funcionalidades interativas do elemento visual e as Perguntas e Respostas para descobrir mais informações.

## <a name="next-steps"></a>Próximos passos
Voltar a [Perguntas e Respostas do Power BI](end-user-q-and-a.md)  

[Power BI - conceitos básicos](end-user-basic-concepts.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

