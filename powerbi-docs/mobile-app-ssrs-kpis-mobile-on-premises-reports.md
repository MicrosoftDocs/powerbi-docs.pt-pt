---
title: "Visualizar relatórios locais e KPIs nas aplicações móveis do Power BI"
description: "As aplicações móveis do Power BI disponibilizam um acesso móvel, dinâmico e tátil às suas informações comerciais no local no SQL Server Reporting Services e no Power BI Report Server."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/18/2017
ms.author: maggies
ms.openlocfilehash: 5bbd2f09187e9fac16f6cc4b9ac3ff59a888ed7f
ms.sourcegitcommit: ea247cb3cfc1cac076d4b076c1ad8e2fc37e15a1
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2017
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>Ver KPIs e relatórios no local do servidor de relatórios nas aplicações móveis do Power BI
Aplica-se a:

| ![iPhone](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Telemóvel Android](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Tablet Android](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPads |Telemóveis Android |Tablets Android |

As aplicações móveis do Power BI disponibilizam um acesso móvel, dinâmico e tátil às suas informações comerciais no local no Power BI Report Server e no SQL Server 2016 Reporting Services (SSRS). 

 ![Página inicial do Report Server nas aplicações móveis](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Comecemos pelo mais importante
**As aplicações móveis são o local onde pode ver os seus conteúdos do Power BI, não onde estes são criados.**

* O utilizador e outros criadores e relatórios na sua organização [criam relatórios do Power BI no Power BI Desktop e, em seguida, publicam-nos no portal Web do Power BI Report Server](report-server/quickstart-create-powerbi-report.md). 
* Pode criar [KPIs diretamente no portal Web](https://docs.microsoft.com/sql/reporting-services/working-with-kpis-in-reporting-services), organizá-los em pastas e marcar os seus favoritos para que os possa encontrar facilmente. 
* [Crie relatórios móveis do Reporting Services](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) com o SQL Server 2016 Enterprise Edition Mobile Report Publisher e publique-os no [portal Web do Reporting Services](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).  

Depois, nas aplicações móveis do Power BI, ligue até cinco servidores de relatórios para ver KPIs e relatórios do Power BI, organizados em pastas ou reunidos como favoritos. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>Explore exemplos nas aplicações móveis sem uma ligação ao servidor
Mesmo que não tenha acesso a um portal Web do Reporting Services, ainda pode explorar as funcionalidades dos KPIs e relatórios móveis do Reporting Services. 

1. Toque no botão de navegação global ![Botão de navegação global](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-global-nav-button.png) no canto superior esquerdo e, em seguida, toque no ícone da engrenagem no canto superior direito ![Ícone de engrenagem](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-settings-icon.png).
2. Toque em **Exemplos do Reporting Services** e, em seguida, navegue para interagir com os relatórios móveis e KPIs de exemplo.
   
   ![Exemplos do Reporting Services](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-server"></a>Ligar a um servidor no local
Pode ver relatórios do Power BI no local, relatórios móveis do Reporting Services e KPIs com as aplicações móveis do Power BI. 

1. No seu dispositivo móvel, abra a aplicação Power BI.
2. Se ainda não iniciou sessão no Power BI, toque em **Report Server**.
   
   ![Iniciar sessão num servidor de relatórios](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Se já iniciou sessão na aplicação Power BI, toque no botão de navegação global ![Botão de navegação global](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-global-nav-button.png)e, em seguida, toque no ícone da engrenagem ![Ícone de engrenagem](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-settings-icon.png) no canto superior direito.
3. Toque em **Ligar ao servidor**.
   
    ![Ligar ao servidor](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

     A aplicação móvel precisa de aceder ao servidor de alguma forma. Existem algumas formas de fazê-lo:

    - Estar na mesma rede ou utilizar a VPN é a forma mais fácil.
    - É possível utilizar um Proxy de Aplicações Web para se ligar de fora da organização. Veja [Using OAuth to connect to Reporting Services (Utilizar o OAuth para se ligar ao Reporting Services)](mobile-oauth-ssrs.md) para obter detalhes. 
    - Abra uma ligação (porta) na firewall.

1. Preencha o endereço do servidor e o seu nome de utilizador e palavra-passe. Utilize este formato para o endereço do servidor:
   
     `http://<servername>/reports`
   
     OR
   
     `https://<servername>/reports`
   
   Inclua **http** ou **https** antes da cadeia de ligação.
   
    ![Caixa de diálogo Ligar ao servidor](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. (Opcional) Em **Opções avançadas**, pode dar ao servidor um nome familiar, se pretender.
6. Agora, vê o servidor na barra de navegação à esquerda (neste exemplo, intitulado "power bi report server").
   
   ![Servidor de relatórios no painel de navegação à esquerda](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Ver KPIs e relatórios do Power BI na aplicação do Power BI
Os relatórios do Power BI, relatórios móveis do Reporting Services e KPIs são apresentados nas mesmas pastas em que se encontram no portal Web do Reporting Services. 

* Toque num relatório do Power BI ![Ícone de relatório do Power BI](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). É aberto em modo horizontal e o utilizador pode interagir com o mesmo na aplicação do Power BI.
  
    ![Relatório do Power BI](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* No Power BI Desktop, os proprietários de relatórios podem [otimizar um relatório](desktop-create-phone-report.md) para as aplicações móveis do Power BI. No telemóvel, os relatórios otimizados têm um ícone ![Ícone de relatórios do Power BI otimizados](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png) e um esquema especiais.
  
    ![Relatório do Power BI otimizado para dispositivos móveis](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Toque num KPI para vê-lo no modo de detalhe.
  
    ![KPI no modo de detalhe](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Ver os seus KPIs e relatórios favoritos
Pode marcar KPIs e relatórios como favoritos no portal Web e, em seguida, vê-los numa pasta conveniente no seu dispositivo móvel, juntamente com os seus dashboards favoritos do Power BI.

* Toque em **Favoritos**.
  
   ![Favoritos no painel de navegação à esquerda](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   Os seus relatórios e KPIs favoritos do portal Web estão nesta página, juntamente com os seus dashboards do Power BI no serviço Power BI:
  
   ![Dashboard e relatórios do Power BI na página Favoritos](media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Remover uma conexão a um servidor de relatórios
1. Na parte inferior da barra de navegação à esquerda, toque em **Definições**.
2. Toque no nome do servidor ao qual não deseja estar ligado.
3. Toque em **Remover Servidor**.

## <a name="next-steps"></a>Próximos passos
* [Introdução ao Power BI](service-get-started.md)  
* Perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
