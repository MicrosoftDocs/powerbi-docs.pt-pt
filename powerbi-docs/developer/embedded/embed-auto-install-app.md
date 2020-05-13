---
title: Instalar automaticamente as aplicações do Power BI ao incorporar para a sua organização
description: Aprenda a instalar automaticamente as aplicações do Power BI ao incorporar para a sua organização.
ms.subservice: powerbi-developer
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: 10939c23a5c25a2ff4233f6b74f9efd99d8e10fd
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148080"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Instalar automaticamente as aplicações do Power BI ao incorporar para a sua organização

Para incorporar conteúdos de uma aplicação, o utilizador que o vai fazer tem de ter [acesso à mesma](../../collaborate-share/service-create-distribute-apps.md). Se a aplicação já estiver instalada para o utilizador, a incorporação será fácil. Para obter mais informações, veja [Incorporar relatórios ou dashboards a partir de aplicações](embed-from-apps.md). Pode definir que todas as aplicações sejam [instaladas automaticamente](https://powerbi.microsoft.com/blog/automatically-install-apps/) no PowerBI.com. No entanto, esta ação é efetuada ao nível do inquilino e tem efeito em todas as aplicações.

## <a name="auto-install-app-on-embedding"></a>Instalar aplicações automaticamente na incorporação

Se um utilizador tiver acesso a uma aplicação que não está instalada, a incorporação irá falhar. Para evitar estas falhas ao incorporar a partir de uma aplicação, pode permitir a instalação automática da mesma no momento da incorporação. Com esta ação, se o utilizador tentar incorporar uma aplicação que não está instalada, esta será automaticamente instalada. Assim, os conteúdos pretendidos são imediatamente incorporados, o que resulta numa melhor experiência para o utilizador.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Incorporação para os utilizadores do Power BI (o utilizador detém os dados)

Para permitir a instalação automática de aplicações para os seus utilizadores, terá de dar a permissão "Criação de Conteúdos" à sua aplicação quando [a registar](register-app.md#register-with-the-power-bi-application-registration-tool), ou adicionar a permissão, se já tiver registado a sua aplicação.

![Permissão criação de conteúdos das aplicações registadas](media/embed-auto-install-app/register-app-create-content.png)

A seguir, tem de fornecer o ID da aplicação no URL de incorporação. Para fornecer o ID da aplicação, o criador da aplicação tem de instalar a aplicação e, em seguida, utilizar uma das chamadas de [APIs Rest do Power BI](https://docs.microsoft.com/rest/api/power-bi/) suportadas – [Obter Relatórios](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) ou [Obter Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Em seguida, o criador da aplicação tem de tirar o URL de incorporação da resposta da API REST. O ID da aplicação irá aparecer no URL se os conteúdos forem de uma aplicação.  Após ter o URL de incorporação, poderá utilizá-lo para incorporar regularmente.

## <a name="secure-embed"></a>Incorporação Segura

Para utilizar a instalação automática de aplicações, o criador da aplicação tem de instalar a aplicação e, em seguida, aceder à aplicação no PowerBI.com, navegar para o relatório e obter a ligação da forma habitual. Todos os outros utilizadores com acesso à aplicação que podem utilizar a ligação também podem incorporar o relatório.

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Só pode incorporar relatórios e dashboards neste cenário.

* Atualmente, esta funcionalidade não é suportada em cenários de incorporação do SharePoint e cenários em que a aplicação detém os dados.