---
title: Ligue-se ao Application Insights com o Power BI
description: Application Insights para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 34e3524d561fb6f6394d69fed55c1bd29bddf4bd
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100594"
---
# <a name="connect-to-application-insights-with-power-bi"></a>Ligue-se ao Application Insights com o Power BI
Use o Power BI para criar dashboards personalizados eficientes através da telemetria do [Application Insights](/azure/application-insights/app-insights-overview/). Veja a telemetria da sua aplicação de novas maneiras. Combine métricas de várias aplicações ou serviços componentes num único dashboard. Esta primeira versão do pacote de conteúdos do Power BI para o Application Insights inclui widgets de métricas comuns relacionadas com a utilização, como utilizadores ativos, exibição de página, sessões, versão do browser e do SO e distribuição geográfica de utilizadores num mapa.

Ligue-se ao [pacote de conteúdos do Application Insights para o Power BI](https://app.powerbi.com/getdata/services/application-insights).

>[!NOTE]
>Este método de integração já está **preterido**. Para saber mais sobre o método preferencial de ligação do Application Insights ao Power BI, utilize a [funcionalidade para exportar consultas de análise](https://docs.microsoft.com/azure/application-insights/app-insights-export-power-bi#export-analytics-queries).

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![Botão Obter Dados](media/service-connect-to-application-insights/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
    ![Botão Obter Serviços](media/service-connect-to-application-insights/pbi_getservices.png)
3. Selecione **Application Insights**  >  **Obter**.
   
    ![Pacote de conteúdos do Application Insights](media/service-connect-to-application-insights/appinsights.png)
4. Forneça os detalhes da aplicação à qual pretende ligar-se, incluindo **Nome de Recurso do Application Insights**, **Grupo de Recursos** e **ID da Subscrição**. Veja [Encontrar os parâmetros do Application Insights](#FindingAppInsightsParams) abaixo para obter mais detalhes.
   
    ![Caixa de diálogo de ligação do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. Selecione **Iniciar Sessão** e siga os ecrãs para ligar-se.
   
    ![Entrada de ligação do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. O processo de importação é iniciado automaticamente. Quando concluído, é mostrada uma notificação e um novo dashboard, relatório e conjunto de dados aparecerão no Painel de Navegação marcados com um asterisco.  Selecione o dashboard para ver os seus dados importados.
   
    ![Dashboard do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**E agora?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdos do Application Insights inclui as tabelas e as métricas seguintes:  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>Parâmetros de localização
O Nome do Recurso, Grupo de Recursos e o ID da Subscrição podem ser encontrados no Portal do Azure. A seleção do Nome abrirá uma vista detalhada, e poderá usar o menu pendente Essenciais para encontrar todos os valores necessários.

![Parâmetros do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

Copie e cole-os nos campos no Power BI:

![Parâmetros do Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

