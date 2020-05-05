---
title: Ligar ao Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)
description: Como obter e instalar a aplicação de modelo COVID-19 Decision Support Dashboard (Dashboard de Suporte de Decisões da COVID-19) para respostas a emergências regionais e como ligar aos dados
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149676"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Ligar ao Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)
O Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais) é o componente de comunicação da [solução de Resposta a Emergências Regionais da Microsoft Power Platform](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview). Os administradores da organização regional podem ver o dashboard no seu inquilino do Power BI, o que lhes permite ver rapidamente dados e métricas importantes que os ajudarão a tomar decisões eficientes.

![Relatório da aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

Este artigo diz-lhe como instalar a aplicação de Resposta a Emergências Regionais através da aplicação do modelo Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais) e como se ligar às origens de dados.

Para obter informações detalhadas sobre o que é apresentado no dashboard, veja [Obter informações](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights).

Depois de ter instalado a aplicação de modelo e ligado às origens de dados, pode personalizar o relatório de acordo com as suas necessidades. Em seguida, pode distribuí-la como uma aplicação aos colegas na sua organização.

## <a name="prerequisites"></a>Pré-requisitos

Antes de instalar esta aplicação de modelo, tem de instalar e configurar a [solução Regional Emergency Response (Respostas a Emergências Regionais)](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy). A instalação desta solução cria as referências de origem de dados necessárias para preencher a aplicação com dados.

Ao instalar a solução Regional Emergency Response (Respostas a Emergências Regionais), anote o [URL da instância de ambiente do Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). Precisará do mesmo para ligar a aplicação de modelo aos dados.

## <a name="install-the-app"></a>Instalar a aplicação

1. Clique na seguinte ligação para aceder à aplicação: [Aplicação de modelo Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Na página AppSource da aplicação, selecione [**OBTER AGORA**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response).

    [![Aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais) no AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Selecione **Instalar**. 

    ![Instalar a aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    Assim que a aplicação estiver instalada, irá vê-la na página Aplicações.

   ![Aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais) na página Aplicações](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Ligar a origens de dados

1. Selecione o ícone na página Aplicações para abrir a aplicação.

1. No ecrã inicial, selecione **Explorar**.

   ![Ecrã inicial da aplicação de modelo](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   A aplicação é aberta e apresenta dados de exemplo.

1. Selecione a ligação **Ligar os dados** na faixa na parte superior da página.

   ![Ligar à ligação de dados da aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. Na caixa de diálogo que é apresentada, introduza o [URL da instância de ambiente do Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Por exemplo: https://[myenv].crm.dynamics.com. Quando terminar, clique em **Seguinte**.

   ![Caixa de diálogo do URL da aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. Na caixa de diálogo seguinte, defina o método de autenticação como **OAuth2**. Não tem de fazer nada na definição do nível de privacidade.

   Selecione **Iniciar sessão**.

   ![Caixa de diálogo de autenticação da aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. No ecrã de início de sessão da Microsoft, inicie sessão no Power BI.

   ![Ecrã de início de sessão da Microsoft](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Depois de iniciar sessão, o relatório liga às origens de dados e é preenchido com dados atualizados. Durante este tempo, o monitor de atividade é ativado.

   ![Atualização da aplicação Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais) em curso](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Agendar atualização do relatório

Quando a atualização de dados for concluída, [configure uma agenda de atualização](../refresh-scheduled-refresh.md) para manter os dados do relatório atualizados.

1. Na barra superior do cabeçalho, selecione **Power BI**.

   ![Menu de trilhos do Power BI](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. No painel de navegação esquerdo, procure a área de trabalho Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais) em **Áreas de Trabalho** e siga as instruções descritas no artigo [Configurar a atualização agendada](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizar e partilhar

Para obter detalhes, veja [Personalizar e partilhar a aplicação](../service-template-apps-install-distribute.md#customize-and-share-the-app). Certifique-se de que revê as [isenções de responsabilidade do relatório](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer) antes de publicar ou distribuir a aplicação.

## <a name="next-steps"></a>Próximos passos
* [Compreender o Regional Emergency Response Dashboard (Dashboard de Respostas a Emergências Regionais)](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Configurar e saber mais sobre o modelo de exemplo Crisis Communication (Comunicação de Crise) no Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
* [O que são as aplicações de modelo do Power BI?](../service-template-apps-overview.md)
* [Instalar e distribuir aplicações de modelo na sua organização](../service-template-apps-install-distribute.md)
