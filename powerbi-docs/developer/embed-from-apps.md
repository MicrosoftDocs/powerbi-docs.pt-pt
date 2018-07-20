---
title: Incorporar relatórios ou dashboards a partir de aplicações
description: Saiba como integrar ou incorporar um relatório ou dashboard a partir de uma aplicação do Power BI e não de uma área de trabalho de aplicação.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2817ccb25fc9aa6d3e8150c776558366dcf0ccb6
ms.sourcegitcommit: 0c870a006e525447497e678484874a2f137b9abd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088845"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Incorporar relatórios ou dashboards a partir de aplicações

No **Power BI**, pode criar aplicações para reunir **dashboards** e **relatórios** relacionados, tudo num só local, e publicá-los para grandes grupos de pessoas na sua organização. A utilização dessas aplicações é relevante quando todos os seus utilizadores usam o Power BI, pelo que pode partilhar os conteúdos com os mesmos através das Aplicações do Power BI. Pretendemos partilhar alguns passos rápidos sobre como incorporar conteúdos de uma Aplicação do Power BI publicada numa aplicação de terceiros.

## <a name="how-to-grab-report-embed-url-for-embedding"></a>Como obter URLs de incorporação de Relatórios

1. Crie uma instância da aplicação numa área de trabalho de utilizador ("A Minha Área de Trabalho") ao partilhá-la consigo ou ao orientar outro utilizador por este fluxo.

2. Abra o relatório pretendido no serviço Power BI.

3. Aceda a Ficheiro -> Incorporar no SharePoint Online e obtenha o URL de incorporação do relatório a partir daí (pode vê-lo no instantâneo abaixo). Em alternativa, chame a API REST GetReports/GetReport e extraia o campo embedURL do relatório correspondente a partir da resposta. Tenha em conta que a chamada REST não deve ter um identificador de área de trabalho como parte do URL porque foi criada uma instância da aplicação na área de trabalho do utilizador.

4. Utilize o URL de incorporação no passo 3 para utilizar com o SDK de JS.

    ![Incorporar a partir de Aplicações](media/embed-from-apps/embed-from-app.png)

## <a name="how-to-grab-dashboard-embed-url-for-embedding"></a>Como obter URLs de incorporação de Dashboards

1. Crie uma instância da aplicação numa área de trabalho de utilizador ("A Minha Área de Trabalho") ao partilhá-la consigo ou ao orientar outro utilizador por este fluxo.

2. Chame a API REST GetDashboards e extraia o campo embedURL do dashboard correspondente a partir da resposta. Tenha em conta que a chamada REST não deve ter um identificador de área de trabalho como parte do URL porque foi criada uma instância da aplicação na área de trabalho do utilizador.

3. Utilize o URL de incorporação obtido no passo 4 para utilizar com o nosso SDK de JS.

## <a name="next-steps"></a>Próximos Passos

Reveja como incorporar áreas de trabalho de aplicações para os seus clientes terceiros e a sua organização.

> [!div class="nextstepaction"]
>[Incorporar para clientes terceiros](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)