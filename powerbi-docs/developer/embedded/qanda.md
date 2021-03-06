---
title: Perguntas e Respostas na análise incorporada do Power BI para melhores informações de BI incorporadas
description: A análise incorporada do Power BI disponibiliza-lhe uma forma de incorporar as Perguntas e Respostas numa aplicação e permitir que os seus utilizadores coloquem perguntas em linguagem natural. Permita melhores informações de BI incorporadas com a análise incorporada do Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 11/20/2017
ms.openlocfilehash: 43e886e6472c6d95b900ccdb5c2e73b8dca3d4a0
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886609"
---
# <a name="qa-in-power-bi-embedded-analytics"></a>Perguntas e Respostas na análise incorporada do Power BI

A análise incorporada do Power BI disponibiliza-lhe uma forma de incorporar as Perguntas e Respostas numa aplicação e permitir que os seus utilizadores coloquem perguntas em linguagem natural e recebam respostas imediatas sob a forma de elementos visuais, como gráficos.

![Pergunta interativa das Perguntas e Respostas numa moldura incorporada](media/qanda/embedded-qanda.gif)

Existem dois modos para incorporar as Perguntas e Respostas na sua aplicação: **interativo** e **apenas resultado**. O modo **Interativo** permite-lhe escrever perguntas e tê-las apresentadas no visual. Se tiver uma pergunta guardada ou uma pergunta definida que pretenda apresentar, pode utilizar o modo de **apenas resultado** ao preencher a pergunta na sua configuração de incorporação.

Eis uma visualização do aspeto do código JavaScript.

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnaMode.Interactive | models.QnaMode.ResultOnly,
    question:    optional parameter for Explore mode (QnaMode.Interactive) and mandatory for Render Result mode (QnaMode.ResultOnly)
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

```javascript
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

```javascript
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

Crie um token de incorporação a partir de um conjunto de dados para iniciar uma peça de Perguntas e Respostas. Para obter mais informações, veja [Gerar token](/rest/api/power-bi/embedtoken).

## <a name="next-steps"></a>Passos seguintes

Para experimentar as Perguntas e Respostas, consulte o [exemplo de incorporação do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)