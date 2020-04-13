---
title: Ligar ao Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)
description: Como obter e instalar a aplicação de modelo COVID-19 Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise da COVID-19) e como ligar aos dados
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: f637bb10ed7ec27dcb3da07fc04cae39328ffebe
ms.sourcegitcommit: 34cca70ba84f37b48407d5d8a45c3f51fb95eb3c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752263"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>Ligar ao Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)

Esta aplicação do Power BI é o artefacto de relatório/dashboard na solução Microsoft Power Platform para Crisis Communication (Comunicação de Crise). Rastreia a localização do trabalhador para utilizadores da aplicação Crisis Communication (Comunicação de Crise). A solução combina funcionalidades do Power Apps, Power Automate, Teams, SharePoint e Power BI. Pode ser utilizado na Web, em dispositivos móveis ou no Teams.

![Relatório da aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

O dashboard mostra dados agregados de gestores de emergências em todo o sistema de saúde para os ajudar a tomar decisões oportunas e corretas.

Este artigo indica como instalar a aplicação e como ligar às origens de dados. Para obter mais informações sobre a aplicação Crisis Communication (Comunicação de Crise), veja [Configurar e saber mais sobre o modelo de exemplo Crisis Communication (Comunicação de Crise) no Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)

Depois de ter instalado a aplicação de modelo e ligado às origens de dados, pode personalizar o relatório de acordo com as suas necessidades. Em seguida, pode distribuí-la como uma aplicação aos colegas na sua organização.

## <a name="prerequisites"></a>Pré-requisitos

Antes de instalar esta aplicação de modelo, tem de instalar e configurar o [exemplo Crisis Communication (Comunicação de Crise)](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app). A instalação desta solução cria as referências de origem de dados necessárias para preencher a aplicação com dados.

Ao instalar o exemplo Crisis Communication (Comunicação de Crise), anote o [caminho da pasta da lista do SharePoint "CI_Employee Status" e o ID da lista](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).

## <a name="install-the-app"></a>Instalar a aplicação

1. Clique na seguinte ligação para aceder à aplicação: [Aplicação de modelo Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Na página AppSource da aplicação, selecione [**OBTER AGORA**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms).

    [![Aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise) no AppSource](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Leia as informações em **Só mais uma coisa** e selecione **Continuar**.

    ![Aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise), Só mais uma coisa](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. Selecione **Instalar**. 

    ![Instalar a aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    Assim que a aplicação estiver instalada, irá vê-la na página Aplicações.

   ![Aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise) na página Aplicações](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Ligar a origens de dados

1. Selecione o ícone na página Aplicações para abrir a aplicação.

1. No ecrã inicial, selecione **Explorar**.

   ![Ecrã inicial da aplicação de modelo](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   A aplicação é aberta e apresenta dados de exemplo.

1. Selecione a ligação **Ligar os dados** na faixa na parte superior da página.

   ![Ligação Ligar os dados da aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. Na caixa de diálogo:
   1. No campo SharePoint_Folder, introduza o [caminho da lista do SharePoint "CI_Employee Status"](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).
   1. No campo List_ID, introduza o ID da lista que obteve das definições da lista. Quando terminar, clique em **Seguinte**.

   ![Caixa de diálogo URL da aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. Na caixa de diálogo seguinte, defina o método de autenticação como **OAuth2**. Não tem de fazer nada na definição do nível de privacidade.

   Selecione **Iniciar sessão**.

   ![Caixa de diálogo Autenticação da aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise)](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. No ecrã de início de sessão da Microsoft, inicie sessão no Power BI.

   ![Ecrã de início de sessão da Microsoft](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   Depois de iniciar sessão, o relatório liga às origens de dados e é preenchido com dados atualizados. Durante este tempo, o monitor de atividade é ativado.

   ![Atualização da aplicação Crisis Communication Presence Report (Relatório de Presença de Comunicação de Crise) em curso](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Agendar atualização do relatório

Quando a atualização de dados for concluída, [configure uma agenda de atualização](../refresh-scheduled-refresh.md) para manter os dados do relatório atualizados.

1. Na barra superior do cabeçalho, selecione **Power BI**.

   ![Menu de trilhos do Power BI](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. No painel de navegação esquerdo, procure a área de trabalho Hospital Emergency Response Decision Support Dashboard (Dashboard de Suporte de Decisões de Resposta de Emergência Hospitalar) em **Áreas de Trabalho** e siga as instruções descritas no artigo [Configurar a atualização agendada](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizar e partilhar

Para obter detalhes, veja [Personalizar e partilhar a aplicação](../service-template-apps-install-distribute.md#customize-and-share-the-app). Certifique-se de que revê as [isenções de responsabilidade do relatório](../create-reports/sample-covid-19-us.md#disclaimers) antes de publicar ou distribuir a aplicação.

## <a name="next-steps"></a>Próximos passos
* [Configurar e saber mais sobre o modelo de exemplo Crisis Communication (Comunicação de Crise) no Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
* [O que são as aplicações de modelo do Power BI?](../service-template-apps-overview.md)
* [Instalar e distribuir aplicações de modelo na sua organização](../service-template-apps-install-distribute.md)
