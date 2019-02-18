---
title: Permissões do Power BI
description: Permissões do Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 548f84c38705e269998fd3c124b4f93d3c83d2ef
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56215464"
---
# <a name="power-bi-permissions"></a>Permissões do Power BI

## <a name="permission-scopes"></a>Âmbitos de permissão

As permissões do Power BI fornecem a uma aplicação a capacidade de executar determinadas ações em nome de um utilizador. Todas as permissões têm de ser aprovadas por um utilizador para serem válidas.

| Nome a Apresentar | Descrição | Valor do Âmbito |
| --- | --- | --- |
| Ver Todos os Conjuntos de Dados |A aplicação pode ver todos os conjuntos de dados do utilizador com sessão iniciada e os conjuntos de dados a que o utilizador tem acesso. |Dataset.Read.All |
| Ler e Escrever Todos os Conjuntos de Dados |A aplicação pode ver e escrever em todos os conjuntos de dados do utilizador com sessão iniciada e os conjuntos de dados a que o utilizador tem acesso. |Dataset.ReadWrite.All |
| Adicionar dados ao conjunto de dados de um utilizador |Dá acesso a uma aplicação para adicionar ou eliminar linhas de conjuntos de dados de um utilizador. Esta permissão não concede o acesso da aplicação aos dados do utilizador. |Data.Alter_Any |
| Create content |A aplicação pode criar conteúdos e conjuntos de dados automaticamente para um utilizador. |Content.Create |
| Ver Grupos de Utilizadores |A aplicação pode ver todos os grupos a que o utilizador com sessão iniciada pertence. |Group.Read |
| Ver todos os grupos |A aplicação pode ver todos os grupos a que o utilizador com sessão iniciada pertence. |Group.Read.All |
| Ler e escrever todos os Grupos |A aplicação pode ver e escrever em todos os grupos do utilizador com a sessão iniciada e todos os grupos a que o utilizador tenha acesso. |Group.ReadWrite.All |
| Ver todos os Dashboards |A aplicação pode ver todos os dashboards do utilizador com sessão iniciada e os dashboards a que o utilizador com sessão iniciada tem acesso. |Dashboard.Read.All |
| Ver todos os Relatórios |A aplicação pode ver todos os relatórios para o utilizador com a sessão iniciada e os relatórios a que o utilizador tem acesso. A aplicação também pode ver os dados nos relatórios, bem como a sua estrutura. |Report.Read.All |
| Ler e escrever todos os Relatórios |A aplicação pode ver e escrever para todos os relatórios para o utilizador com a sessão iniciada e quaisquer relatórios a que o utilizador tenha acesso. Isto não fornece direitos para criar um novo relatório. |Report.ReadWrite.All |
| Ler e escrever em todas as Capacidades |A aplicação pode ver e escrever em todas as capacidades do utilizador com a sessão iniciada e todas as capacidades a que o utilizador tenha acesso. Isto não concede direitos para criar uma nova capacidade. |Capacities.ReadWrite.All |
| Ler todas as Capacidades |A aplicação pode ver e escrever em todas as capacidades para o utilizador com a sessão iniciada e todas as capacidades a que o utilizador tenha acesso. Isto não concede direitos para criar uma nova capacidade. |Capacities.Read.All |
| Ler e escrever em todos os conteúdos no inquilino |A aplicação pode ver e escrever em todos os artefactos, tais como grupos, relatórios, dashboards e conjuntos de dados no Power BI. Isto desde que o utilizador com sessão iniciada seja um administrador de serviços do Power BI. |Tenant.ReadWrite.All |
| Ver todos os conteúdos no inquilino |A aplicação pode ver todos os artefactos, tais como grupos, relatórios, dashboards e conjuntos de dados no Power BI. Isto desde que o utilizador com sessão iniciada seja um administrador de serviços do Power BI. |Tenant.Read.All |

Uma aplicação pode pedir permissões quando tentar iniciar sessão pela primeira vez na página de um utilizador ao transmitir as permissões pedidas no parâmetro de âmbito da chamada. Se as permissões forem concedidas, será devolvido um token de acesso à aplicação, que pode ser utilizado nas chamadas de API futuras. O acesso pode ser utilizado apenas por uma aplicação específica.

> [!NOTE]
> As APIs do Power BI ainda se referem às áreas de trabalho de aplicações como grupos. Quaisquer referências a grupos significam que está a trabalhar com áreas de trabalho de aplicações.

## <a name="requesting-permissions"></a>Pedir Permissões

Embora possa chamar a API para autenticar com um nome de utilizador e palavra-passe, para executar ações em nome de outro utilizador, é necessário pedir permissões que o utilizador aprovará e enviar o token de acesso resultante em todas as chamadas futuras. Para este processo, seguiremos o protocolo [OAuth 2.0](http://oauth.net/2/) padrão. Embora a implementação real possa variar, o fluxo do OAuth para o Power BI tem os seguintes elementos:

* **IU de Início de Sessão** – Trata-se de uma IU que o programador pode evocar para pedir permissões. Exige que o utilizador inicie sessão, se ainda não o tiver feito. O utilizador também tem de aprovar as permissões que a aplicação está a pedir. A janela de início de sessão publicará um código de acesso ou uma mensagem de erro para um URL de redirecionamento fornecido.
  * É necessário o Power BI fornecer um URL de redirecionamento padrão para ser utilizado por aplicações nativas.
* **Código de Autorização** – Os Códigos de Autorização são devolvidos às aplicações Web após o início de sessão através dos parâmetros de URL no URL de redirecionamento. Uma vez que estão nos parâmetros, existem alguns riscos de segurança. As aplicações Web terão de trocar o código de autorização por um Token de Autorização
* **Token de Autorização** – Utilizado para autenticar chamadas de API em nome de outro utilizador. O âmbito será uma aplicação específica. Os tokens têm um tempo de vida definido e quando expiram têm de ser atualizados.
* **Atualizar Token** – Quando os tokens expiram, existe um processo para atualizá-los.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)