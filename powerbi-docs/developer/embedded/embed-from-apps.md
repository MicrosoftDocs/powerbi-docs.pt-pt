---
title: Incorporar relatórios ou dashboards a partir de aplicações
description: Saiba como integrar ou incorporar um relatório ou dashboard a partir de uma aplicação do Power BI e não de uma área de trabalho.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 11/27/2018
ms.openlocfilehash: 34c5e825a589fc3f9ba9ecd7e9fe1d6b137e1cfd
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79494636"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Incorporar relatórios ou dashboards a partir de aplicações

No Power BI, pode criar aplicações para juntar dashboards e relatórios num único lugar. Em seguida, pode publicá-los em grandes grupos de pessoas na sua organização. A utilização dessas aplicações é relevante quando todos os seus utilizadores são utilizadores do Power BI. Assim, pode partilhar conteúdos com eles através das aplicações do Power BI. Este artigo fornece-lhe alguns passos rápidos para incorporar conteúdos de uma aplicação do Power BI publicada numa aplicação de terceiros.

## <a name="grab-a-report-embedurl-for-embedding"></a>Obter um embedURL de relatório para incorporar

1. Crie uma instância da aplicação numa área de trabalho de utilizador, **A Minha Área de Trabalho**. Partilhe consigo mesmo ou oriente outro utilizador para seguir este fluxo.

2. Abra o relatório que pretende no serviço Power BI.

3. Aceda a **File** > **Embed In SharePoint Online** (Ficheiro > Incorporar no SharePoint Online) e obtenha o embedURL de relatório. Um exemplo de embedURL é apresentado no instantâneo abaixo. Em alternativa, pode chamar a API REST GetReports/GetReport e extrair o campo de embedURL de relatório correspondente da resposta. A chamada REST não deve ter um identificador de área de trabalho como parte do URL, uma vez que foi criada uma instância da aplicação na área de trabalho do utilizador.

    ![Incorporar a partir de aplicações](media/embed-from-apps/embed-from-app.png)

4. Utilize o embedURL obtido no passo 3 com o SDK de JavaScript.

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Obter um embedURL de dashboard para incorporar

1. Crie uma instância da aplicação numa área de trabalho de utilizador, **A Minha Área de Trabalho**. Partilhe consigo mesmo ou oriente outro utilizador para seguir este fluxo.

2. Chame a API REST GetDashboards e extraia o campo de embedURL de dashboard correspondente da resposta. A chamada REST não deve ter um identificador de área de trabalho como parte do URL, uma vez que foi criada uma instância da aplicação na área de trabalho do utilizador.

3. Utilize o embedURL obtido no passo 2 com o SDK de JavaScript.

## <a name="next-steps"></a>Próximos passos

Reveja como incorporar áreas de trabalho para os seus clientes terceiros e a sua organização:

> [!div class="nextstepaction"]
>[Incorporar para clientes terceiros](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporar para a sua organização](embed-sample-for-your-organization.md)