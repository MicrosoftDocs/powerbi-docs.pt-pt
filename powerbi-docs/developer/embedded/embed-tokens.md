---
title: Compreenda os tokens de permissão necessários para incorporar uma aplicação Power BI
description: Saiba quais os símbolos que a sua aplicação Power BI necessita para autenticar contra o serviço Azure e Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: amshuste
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/17/2021
ms.openlocfilehash: 6a7847b0e89086094220a51a4893ffffd59d5642
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/18/2021
ms.locfileid: "100656591"
---
# <a name="embedded-analytics-application-tokens"></a>Fichas de aplicação de análise incorporadas

Para consumir o conteúdo power bi precisa de um token de acesso. Dependendo da sua solução, este token pode ser um [token AD Azure](#azure-ad-token) ou um [símbolo incorporado](#embed-token).

Se estiver a utilizar o incorporado para a solução *dos seus clientes,* os utilizadores da sua aplicação web terão acesso ao conteúdo power BI (como relatórios, dashboards e azulejos), de acordo com o *token incorporado* que foi gerado pela sua aplicação.

>[!NOTE]
>Ao utilizar o incorporado para a solução *dos seus clientes,* pode utilizar qualquer método de autenticação para permitir o acesso à sua aplicação web.

Se estiver a utilizar o incorporado para a sua solução *de organização,* os utilizadores da sua aplicação web estarão a autenticar contra a AZure AD utilizando as suas próprias credenciais. Os utilizadores da sua aplicação terão acesso ao conteúdo Power BI a que podem aceder no serviço Power BI.

## <a name="azure-ad-token"></a>Ficha AD de Azure

Para ambos *incorporados para os seus clientes* e *incorporados para as suas* soluções de organização, você precisa de um [token AD Azure.](#azure-ad-token) Este token é necessário para todas as operações [da API REST,](/rest/api/power-bi/) e expira após uma hora.

* No *incorporado para os seus clientes,* o token AD AD Azure é usado para gerar o *token incorporado*.

* No *incorporado para a sua organização,* o token AD AZure é usado para aceder ao Power BI.

## <a name="embed-token"></a>Token de incorporação

Quando está a usar o incorporado para a solução *dos seus clientes,* a sua aplicação web precisa de saber a que conteúdo Power BI o seu utilizador pode aceder. Utilize as APIs [de ressarbios incorporados](/rest/api/power-bi/embedtoken) para gerar um *token incorporado,* que especifica o seguinte:

* Que conteúdo o seu utilizador de aplicações web pode aceder.

* O nível de acesso do utilizador da aplicação web (ver, criar ou editar).

Para obter mais informações, consulte [Considerações ao gerar um token incorporado](generate-embed-token.md).

## <a name="authentication-flows"></a>Fluxos de autenticação

Esta secção descreve os fluxos de autenticação para o *incorporado para os seus clientes* e *incorporados para a sua organização* incorporando soluções.

### <a name="embed-for-your-customers"></a>Incorporar para os seus clientes

A *solução Embed para os seus clientes* utiliza um fluxo de autenticação não interativo. Os utilizadores não precisam de iniciar seduca no Azure AD, para aceder ao Power BI. Em vez disso, a sua aplicação web utiliza uma identidade AD Azure dedicada para autenticar contra a AD Azure e gerar o *token incorporado.* A identidade dedicada pode ser uma das seguintes:

* **[Diretor de serviços](embed-service-principal.md)**

    A sua aplicação web utiliza o [principal objeto do serviço](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) AZure para autenticar contra a Azure AD e obter um *token AD Azure apenas para aplicações.* Este é um método de autenticação *apenas para aplicações,* que é recomendado pelo Azure AD.

    Ao utilizar um *principal de serviço,* é necessário ativar o acesso a [APIs power BI](embed-sample-for-customers.md#step-6---service-principal-api-access) nas definições de *administração* do serviço Power BI. Isto permite que a sua aplicação web aceda às APIs power BI REST. Para utilizar as operações da API num espaço de trabalho, o diretor de *serviço* precisa de ser *membro* ou *administrador* do espaço de trabalho.

* **Master user (Utilizador principal)**

    A sua aplicação web utiliza uma conta de utilizador para autenticar contra a AZure AD e obter o *token AD Azure*. O *utilizador principal* precisa de ter uma licença Power BI [Pro](/power-bi/admin/service-admin-purchasing-power-bi-pro) ou premium per [user (PPU).](/power-bi/admin/service-premium-per-user-faq)

    Ao utilizar um *utilizador principal,* terá de definir as [permissões delegadas](/azure/active-directory/develop/v2-permissions-and-consent) da sua aplicação (também conhecidas como âmbitos). O *principal utilizador* ou administrador de *inquilinos* é obrigado a conceder o consentimento para a utilização destas permissões utilizando as APIs power BI REST.

Após a autenticação bem sucedida contra o Azure AD, a sua aplicação web gerará um [token incorporado](/rest/api/power-bi/embedtoken) para permitir aos seus utilizadores acederem a conteúdos específicos do Power BI.

>[!NOTE]
>* Para incorporar o incorporado para a solução *dos seus clientes,* precisará de uma capacidade com um A, EM ou P SKU.
>* Para [passar para a produção](move-to-production.md) vai precisar de uma capacidade.

O diagrama seguinte mostra o fluxo de autenticação para a *solução incorporada para a solução dos seus clientes.*

>[!div class="mx-imgBorder"]
>:::image type="content" source="media\embed-tokens\paas-authentiction.png" alt-text="Um diagrama do fluxo de autenticação em uma solução de análise incorporada ao Power B I para os seus clientes.":::

1. O utilizador de aplicações web autentica-se contra a sua aplicação web (com o seu método de autenticação).

2. A sua aplicação web utiliza um *principal de serviço* ou um utilizador *principal* para autenticar contra a Azure AD.

3. A sua aplicação web obtém um *token AD Azure* da AD AZure, e usa-o para aceder a APIs power BI REST. O acesso às APIs power BI REST é dado de acordo com o seu método de autenticação, que é *o principal de serviço* ou o utilizador *principal*.

4. A sua aplicação web chama uma operação API [embed Token](/rest/api/power-bi/embedtoken) REST, solicitando o *token incorporado*. O *token incorporado* especifica quais o conteúdo power BI que pode ser incorporado.

5. A API REST devolve o *token incorporado* à sua aplicação web.

6. A aplicação web transmite o token incorporado para o navegador web do utilizador.

7. O utilizador da aplicação web usa o token incorporado para aceder ao Power BI.

### <a name="embed-for-your-organization"></a>Incorporar para a sua organização

O *Incorporado para a sua* solução de organização utiliza um fluxo de autenticação interativo. Os seus utilizadores autenticam-se contra a Azure AD utilizando as suas credenciais Power BI. Os utilizadores precisam de conceder consentimento às permissões da API que foram definidas ao registar a aplicação com Azure AD. O consentimento é concedido na janela pop-up solicitada do diálogo da Microsoft *Permissions.* Após o consentimento ser concedido, o conteúdo do Power BI, como relatórios e dashboards a que o utilizador da aplicação web tem acesso, pode ser incorporado.

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/requested-premissions.png" alt-text="Screenshot mostrando as permissões da Microsoft solicitou uma janela pop-up que pede aos clientes que concedam permissões para aceder ao Power B I.":::

>[!NOTE]
>* O *incorporado para a sua* solução de organização não suporta um SKUs.
>* Para [passar à produção,](move-to-production.md) precisará de uma das seguintes configurações:
>    * Todos os utilizadores com licenças Pro.
>    * Todos os utilizadores com licenças PPU.
>    * Uma [capacidade.](embedded-capacity.md) Esta configuração permite que todos os utilizadores tenham licenças gratuitas.

Este diagrama mostra um exemplo do fluxo de autenticação para o incorporado para a sua solução *de organização.*

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/saas-authentiction.png" alt-text="Um diagrama do fluxo de autenticação em uma solução de análise incorporada power B I para a sua organização.":::

1. O utilizador de aplicações web acede à aplicação web.

2. A aplicação web redireciona o utilizador da aplicação web para Azure AD.

3. O utilizador da aplicação web autentica-se contra a Azure AD utilizando as suas credenciais Power BI.

4. O Azure AD redireciona o utilizador da aplicação web de volta para a aplicação web com o token AD Azure (num cenário de concessão implícita, o token de acesso é devolvido ao navegador do utilizador).

5. A aplicação web passa o token AD AZure para o navegador web do utilizador.

6. A sua aplicação web Power BI utiliza o token AD AZure para incorporar conteúdo power BI, como relatórios e dashboards, aos quais o utilizador da aplicação web tem direitos de acesso.

## <a name="next-steps"></a>Passos seguintes

>[!div class="nextstepaction"]
>[Considerações ao gerar um token de incorporação](generate-embed-token.md)

>[!div class="nextstepaction"]
>[Capacidade e SKUs na análise incorporada do Power BI](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Tem alguma dúvida? Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)