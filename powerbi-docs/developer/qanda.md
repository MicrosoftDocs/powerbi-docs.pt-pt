---
title: Perguntas e Respostas no Power BI Embedded
description: "O Power BI Embedded disponibiliza-lhe uma forma de incorporar as Perguntas e Respostas numa aplicação e permitir que os seus utilizadores coloquem perguntas em linguagem natural."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/20/2017
ms.author: maghan
ms.openlocfilehash: 93b4f21cd5a7a804874ab111bca61eea112cb11a
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="qa-in-power-bi-embedded"></a>Perguntas e Respostas no Power BI Embedded
O Power BI Embedded disponibiliza-lhe uma forma de incorporar as Perguntas e Respostas numa aplicação e permitir que os seus utilizadores coloquem perguntas em linguagem natural e recebam respostas imediatas sob a forma de visuais como gráficos.

![Pergunta interativa das Perguntas e Respostas numa moldura incorporada](media/qanda/embedded-qanda.gif)

Existem dois modos para incorporar as Perguntas e Respostas na sua aplicação: **interativo** e **apenas resultado**. O modo **Interativo** permite-lhe escrever perguntas e tê-las apresentadas no visual. Se tiver uma pergunta guardada ou uma pergunta definida que pretenda apresentar, pode utilizar o modo de **apenas resultado** ao preencher a pergunta na sua configuração de incorporação.

Eis uma visualização do aspeto do código JavaScript.

```
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnAMode.Interactive | models.QnAMode.ResultOnly,
    question:    optional parameter for Explore mode (QnAMode.Interactive) and mandatory for Render Result mode (QnAMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>Pergunta definida
Se utilizar o **modo de resultados** com uma pergunta definida, pode introduzir perguntas adicionais na moldura e fazer com que estas sejam imediatamente respondidas, substituindo o resultado anterior. É composto um novo visual, correspondente à nova pergunta.

Um exemplo desta utilização é uma lista de perguntas frequentes. O utilizador pode percorrer as perguntas e obter respostas para as mesmas na mesma peça incorporada.

**Fragmento de código para utilização do JS SDK:**  

```        
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>Evento de composição visual
No modo **interativo**, a aplicação pode ser notificada com um evento de alteração de dados, sempre que o visual composto for alterado em função da consulta de entrada atualizada à medida que esta é escrita.

Ouvir o evento *visualRendered* permite-lhe guardar perguntas para utilização futura. 

**Fragmento de código para utilização do JS SDK:**  

```
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>Token de incorporação
Crie um token de incorporação a partir de um conjunto de dados para iniciar uma peça de Perguntas e Respostas. Para obter mais informações, consulte [Gerar Token para as Perguntas e Respostas](https://msdn.microsoft.com/library/mt784614.aspx#qanda).

## <a name="next-steps"></a>Passos seguintes
Para experimentar as Perguntas e Respostas, consulte o [exemplo de incorporação do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

