---
title: Desenvolver com as APIs REST do Power BI Report Server
description: A API REST fornece acesso programático aos objetos num catálogo do Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 8f35b7a3c19751b4537a49fa8cb30f4347f080ed
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770759"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Desenvolver com as APIs REST do Power BI Report Server

O Power BI Report Server suporta APIs REST (Representational State Transfer). As APIs REST são pontos finais de serviço que suportam um conjunto de operações HTTP (métodos), que fornecem acesso de criação, obtenção, atualização ou eliminação para recursos num servidor de relatórios.

A API REST fornece acesso programático aos objetos num catálogo do Power BI Report Server. Os exemplos de objetos incluem pastas, relatórios, KPIs, origens de dados, conjuntos de dados, planos de atualização, subscrições e muito mais. Através da API REST, pode, por exemplo, navegar na hierarquia de pastas, descobrir os conteúdos de uma pasta ou transferir uma definição de relatório. Também pode criar, atualizar e eliminar objetos. Os exemplos de utilização de objetos incluem carregar um relatório, executar um plano de atualização, eliminar uma pasta, etc.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>Componentes de um pedido/resposta da API REST

Um par pedido/resposta da API REST pode ser separado em cinco componentes:

* O **URI do pedido**, que consiste em: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Embora o URI do pedido esteja incluído no cabeçalho da mensagem de pedido, este é chamado separadamente, porque a maioria das linguagens ou estruturas requerem que seja transmitido em separado da mensagem de pedido.
  
  * Esquema do URI: indica o protocolo utilizado para transmitir o pedido. Por exemplo, `http` ou `https`.
  * Anfitrião do URI: especifica o nome de domínio ou o endereço IP do servidor onde o ponto final do serviço REST está alojado, como `myserver.contoso.com`.
  * Caminho do recurso: especifica o recurso ou a coleção de recursos, o que pode incluir vários segmentos utilizados pelo serviço para determinar a seleção desses recursos. Por exemplo: é possível utilizar `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` para obter as propriedades especificadas de CatalogItem.
  * Cadeia de consulta (opcional): fornece parâmetros simples adicionais, como a versão da API ou os critérios de seleção de recursos.
* Campos de cabeçalho da mensagem de pedido HTTP:
  
  * Um [método HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) obrigatório (também conhecido como uma operação ou verbo), que indica ao serviço o tipo de operação que está a pedir. As APIs REST do Reporting Services suportam os métodos DELETE, GET, HEAD, PUT, POST e PATCH.
  * Campos de cabeçalho adicionais opcionais, conforme exigido pelo método URI e HTTP especificado.
* Campos do **corpo da mensagem do pedido** HTTP opcionais, para suportar a operação URI e HTTP. Por exemplo, as operações POST contêm objetos com codificação MIME transmitidos como parâmetros complexos. Para operações POST ou PUT, o tipo de codificação MIME do corpo também deve ser especificado no cabeçalho do pedido `Content-type`. Alguns serviços requerem a utilização de um tipo MIME específico, como `application/json`.
* Campos de **cabeçalho da mensagem de resposta** HTTP:
  
  * Um [código de estado HTTP](http://www.w3.org/Protocols/HTTP/HTRESP.html), que varia entre 2xx códigos de êxito e 4xx ou 5xx códigos de erro. Em alternativa, pode ser devolvido um código de estado definido pelo serviço, conforme indicado na documentação da API.
  * Campos de cabeçalho adicionais opcionais, conforme necessário para suportar a resposta do pedido, como um cabeçalho de resposta `Content-type`.
* Campos do **corpo da mensagem de resposta** HTTP opcionais:
  
  * São devolvidos objetos de resposta com codificação MIME no corpo da resposta HTTP, como uma resposta a um método GET que está a devolver dados. Normalmente, estes objetos são devolvidos num formato estruturado como JSON ou XML, conforme indicado pelo cabeçalho de resposta `Content-type`.

## <a name="api-documentation"></a>Documentação da API

Uma API REST moderna chama a documentação da API moderna. A API REST é criada com base na especificação OpenAPI (conhecida como especificação swagger) e a documentação está disponível no [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0). Além da documentação da API, o SwaggerHub ajuda a gerar uma biblioteca de cliente na linguagem escolhida: JavaScript, TypeScript, C#, Java, Python, Ruby e muitas mais.

## <a name="testing-api-calls"></a>Testar as chamadas da API

Uma ferramenta para testar as mensagens de pedido/resposta HTTP é o [Fiddler](http://www.telerik.com/fiddler). O Fiddler é um proxy de depuração Web gratuito que pode intercetar os pedidos REST, o que facilita o diagnóstico das mensagens de pedido/resposta HTTP.

## <a name="next-steps"></a>Passos seguintes

Reveja as APIs disponíveis no [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).

Estão disponíveis exemplos no [GitHub](https://github.com/Microsoft/Reporting-Services). O exemplo inclui uma aplicação HTML5 criada com base no TypeScript, React e webpack, juntamente com um exemplo do PowerShell.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)