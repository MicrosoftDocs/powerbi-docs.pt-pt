---
title: Dicas e truques para fazer perguntas com as Perguntas e Respostas do Power BI
description: Dicas e truques para fazer perguntas com as Perguntas e Respostas do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/18/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 189134a82e183819f1d48be0b420c9f92a5e69b3
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44725955"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Dicas para fazer perguntas nas Perguntas e Respostas do Power BI
## <a name="words-and-terminology-that-qa-recognizes"></a>Palavras e terminologia reconhecidas pelas Perguntas e Respostas
Esta lista de palavras-chave não é exaustiva.  A melhor forma de saber se o Power BI reconhece uma palavra-chave é escrevê-la na caixa de perguntas.  Se a palavra ou o termo estiver a cinzento, significa que o Power BI não o reconhece ou que não o reconhece no contexto atual.

A lista abaixo utiliza o tempo verbal presente, mas todos os tempos são reconhecidos na maioria dos casos. Por exemplo, "é" inclui são, foi, foram, serão, foi, irá, tem, fazer, faz, fez.  "Ordena" inclui ordenar e ordenação.  Além disso, o Power BI reconhece e inclui versões singulares e plurais de uma palavra. Por exemplo, o Power BI reconhece "ano" e "anos".

> [!NOTE]
> Também estão disponíveis perguntas e respostas na [aplicação Microsoft Power BI para iOS em iPads, iPhones e dispositivos iPod Touch](consumer/mobile/mobile-apps-ios-qna.md).
> 
> 

Se for o proprietário de um conjunto de dados, adicione expressões e sinónimos para melhorar os resultados das Perguntas e Respostas para os seus clientes.

**Agregados**: total, soma, montante, número, quantidade, contagem, média, mais, menos, menor, maior, mais pequeno, mais alto, o maior, máximo, máx, maior, mais baixo, mais pequeno, mínimo, mín

**Artigos**: o, a, um, uma

**Vazio e Booleano**: branco, vazio, nulo, com prefixo de "não" ou "não-", cadeia vazia, texto vazio, verdadeiro, v, falso, f

**Comparações**: vs, versus, comparado a, comparado com

**Conjunções**: e, ou, cada, com, versus, &, e, mas, nem, juntamente com, além de

**Contrações**: As Perguntas e Respostas reconhecem quase todas as contrações. Experimente.  Eis alguns exemplos: não foi, não fez, ele fez, ele é, não é, é, ela irá, ele fez, não foi, onde irá, quem é, não vai, não iria.

**Datas**: O Power BI reconhece a maioria dos termos de datas (dia, semana, mês, ano, trimestre, década, etc...) e datas escritas em muitos formatos diferentes (consulte abaixo). O Power BI também reconhece as seguintes palavras-chave: NomeDoMês, Dias 1-31, década.

Exemplos: 3 de janeiro de 1995, 3 janeiro 1995, 03 jan 1995, 3 jan 1995, dia 3 de janeiro, janeiro de 1995, 1995 janeiro, 1995-01, 01/1995, nomes de meses.

**Datas relativas**: hoje, agora, hora atual, ontem, amanhã, atual, próximo, último, anterior, há, antes, antes de, depois de, posterior a, desde, às, em, daqui a, depois de agora, no futuro, passado, últimos, anteriores, em, ao longo de, há N dias, daqui a N dias, próximo, uma vez, duas vezes.

Exemplo: contagem de encomendas nos últimos 6 dias.

**Igualdade (Intervalo)**: em, igual a, =, depois de, é mais de, em, entre, antes de

Exemplos: Ano de encomenda é antes de 2012? Preço é igual a entre 10 e 20? A idade de João é superior a 40? Vendas totais em 200-300?

**Igualdade (Valor)**: é. igual, igual a, em, de, para, dentro de, está em, é em

Exemplos: Que produtos são verdes? Data de encomenda é igual a 2012. A idade de João é 40? Vendas totais que não é igual a 200? Data de encomenda de 1/1/2016. 10 em preço? Verde para cor? 10 em preço?

**Nomes**: se uma coluna no conjunto de dados contiver a expressão “nome” (por exemplo, NomeFuncionário), as Perguntas e Respostas entendem que os valores nessa coluna são nomes e pode fazer perguntas como "que funcionários têm o nome Roberto?".

**Pronomes**: ele, lho, dele, ela, lha, dela, aquilo, daquilo, lhe, lhes, deles, isto, estes, aquilo, aqueles

**Comandos de consulta**: ordenado, ordenar por, direção, agrupar por, por, mostrar, listar, mostrar, dar-me, nome, apenas, só, dispor, classificar, comparar, para, com, contra, alfabeticamente, ascendente, descendente, ordenar

**Intervalo**: maior do que, mais, maior, sobre, >, menos, menor do que, menos do que, abaixo de, sob, <, pelo menos, no mínimo, >=, até, no máximo, <=, em, entre, no intervalo de, a partir de, depois de, antes de, antes, depois, em, ao, posterior a, após, desde, a começar por, a começar desde, a terminar com

**Horas**: am, pm, em ponto, meio-dia, meia-noite, hora, minuto, segundo, hh:mm:ss

Exemplos: 22:00, 22:35, 22:35:15, 10 em ponto, meio-dia, meia-noite, hora, minuto, segundo.

**Maiores N** (ordem, classificação): maiores, menores, mais altos, mais baixos, primeiro, último, seguinte, primeiros, mais recentes, mais antigos, últimos, mais recente, próximo

**Tipos visuais**: todos os tipos visuais nativos do Power BI.  Se for uma opção no painel Visualizações, pode incluí-lo na sua pergunta.  A exceção são os [visuais personalizados](power-bi-custom-visuals.md) que adicionou manualmente ao painel Visualização.

Exemplo: mostrar distritos por mês e total de vendas como gráfico de barras

**Q (relação, qualificado)**: quando, onde, qual, quem, a quem, quantos, quanto, quantas vezes, com que frequência, montante, número, quantidade, quanto tempo, o quê

## <a name="qa-helps-you-phrase-the-question"></a>As Perguntas e Respostas ajudam-no a formular a pergunta
As Perguntas e Respostas fazem o melhor possível para garantir que a resposta reflete com precisão a pergunta que está a ser feita. E fá-lo de várias formas. Em todas elas é possível aceitar a ação por completo, parcialmente ou não aceitá-la. Ao escrever a sua pergunta, as Perguntas e Respostas:

* preenchem automaticamente palavras e perguntas. Utiliza várias estratégias, incluindo palavras reconhecíveis com preenchimento automático, perguntas comuns para os livros subjacentes e perguntas usadas anteriormente que devolveram respostas válidas. Se houver mais do que uma opção de preenchimento automático disponível, as mesmas serão apresentadas numa lista pendente.
* corrige a ortografia.
* apresenta uma pré-visualização da resposta sob a forma de uma visualização. A visualização é atualizada à medida que escreve e edita a pergunta (não espera até que prima Enter).
* sugere automaticamente termos de substituição do(s) conjunto(s) de dados subjacente(s) quando move o cursor de novo para a caixa de perguntas.
* reformula a pergunta com base nos dados do(s) conjunto(s) de dados subjacente(s). Isto ajuda a garantir que as Perguntas e Respostas perceberam a sua pergunta, já que substitui as palavras que usou por sinónimos do(s) conjunto(s) de dados subjacente(s).
* esbate as palavras que não são entendidas.

## <a name="dont-stop-now"></a>Não parar agora
Depois de as Perguntas e Respostas exibirem os resultados, mantenha a conversa! Use as funcionalidades interativas da visualização e as Perguntas e Respostas para descobrir mais informações.

## <a name="next-steps"></a>Passos seguintes
Voltar a [Perguntas e Respostas do Power BI](power-bi-q-and-a.md)  

[Power BI - conceitos básicos](service-basic-concepts.md)  

Mais perguntas? [Pergunte à Comunidade do Power BI](http://community.powerbi.com/)

