---
title: Ver relatórios no local e KPIs na aplicação Windows no Power BI
description: A aplicação móvel do Power BI para Windows 10 oferece acesso móvel atualizado e tátil às suas informações empresariais no local mais importantes.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 05/19/2020
ms.openlocfilehash: eb6b86b2810609c0ad795190afc91c40677f5e70
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413317"
---
# <a name="view-on-premises-reports-and-kpis-in-the-power-bi-windows-app"></a>Ver relatórios no local e KPIs na aplicação Windows no Power BI
A aplicação Power BI para o Windows 10 oferece acesso móvel atualizado e tátil às suas informações empresariais no local mais importantes no SQL Server 2016 Reporting Services. 

![Relatórios móveis do Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>As coisas mais importantes primeiro
[Crie relatórios móveis do Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) com o SQL Server 2016 Enterprise Edition Mobile Report Publisher e publique-os no [portal Web do Reporting Services](/sql/reporting-services/web-portal-ssrs-native-mode). Crie KPIs diretamente no portal Web. Organize-os em pastas e marque os seus favoritos para que os possa encontrar facilmente. 

Em seguida, na aplicação Power BI para o Windows 10, veja os KPS, os relatórios móveis e os relatórios do Power BI organizados em pastas e agrupados como favoritos. 

> [!NOTE]
> O seu dispositivo precisa de executar o Windows 10. A aplicação funciona melhor em dispositivos com, pelo menos, 1 GB de RAM e 8 GB de armazenamento interno.

>[!NOTE]
>O suporte à aplicação móvel Power BI para **telemóveis com o Windows 10 Mobile** será descontinuado a 16 de março de 2021. [Saiba mais](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Explorar exemplos sem um servidor do SQL Server 2016 Reporting Services
Mesmo que não tenha acesso a um portal Web do Reporting Services, ainda pode explorar as funcionalidades dos relatórios móveis do Reporting Services.

1. No seu dispositivo Windows 10, abra a aplicação do Power BI.
2. Toque no botão de navegação global ![Botão de navegação global](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) no canto superior esquerdo.
3. Toque no ícone das **Definições**![Ícone Definições](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), clique com o botão direito do rato ou mantenha premido **Ligar ao servidor** e, em seguida, toque em **Ver exemplos**.
   
   ![Ver exemplos do SSRS](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Abra a pasta Relatórios de Revenda ou Relatórios de Vendas para explorar os respetivos KPIs e relatórios móveis.
   
   ![Relatórios móveis e KPIs de exemplo](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Procure exemplos para interagir com KPIs e relatórios móveis.

## <a name="connect-to-a-reporting-services-report-server"></a>Ligar a um servidor de relatórios do Reporting Services
1. Na parte inferior do painel de navegação, toque em **Definições** ![ícone de Definições](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)
2. Toque em **Ligar ao servidor**.
3. Preencha o endereço do servidor e o seu nome de utilizador e palavra-passe. Utilize este formato para o endereço do servidor:
   
     `https://<servername>/reports` OU   `https://<servername>/reports`
   
   > [!NOTE]
   > Inclua **http** ou **https** no início da cadeia de ligação.
   > 
   > 
   
    Toque em **Opções avançadas** para, se pretender, atribuir um nome ao servidor.
4. Toque na marca de verificação para ligar. 
   
   Agora pode ver o servidor no painel de navegação.
   
   ![Servidor no painel de navegação](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Toque no botão de navegação global ![Botão de navegação global](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) a qualquer altura para alternar entre os seus relatórios móveis do Reporting Services e os dashboards no serviço Power BI. 
   > 

   >[!NOTE]
   >Os Servidores de Relatórios configurados com portas personalizadas não são suportados e não podem ser acedidos a partir da aplicação Power BI para Windows. 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Ver KPIs e relatórios móveis do Reporting Services na aplicação do Power BI
Os KPIs dos Reporting Services, os relatórios móveis e os relatórios do Power BI (pré-visualização) são apresentados nas mesmas pastas em que se encontram no portal Web do Reporting Services.

![Pastas de relatórios](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Toque num KPI para vê-lo no modo de foco.
  
    ![KPI no modo de detalhe](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Toque num relatório móvel para abri-lo e interagir com ele na aplicação do Power BI.
  
    ![Relatório móvel do Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Ver os seus KPIs e relatórios favoritos
Pode marcar KPIs, relatórios móveis e relatórios do Power BI como favoritos no portal Web do Reporting Services e, em seguida, vê-los numa pasta conveniente no seu dispositivo Windows 10, juntamente com os seus dashboards e relatórios favoritos do Power BI.

* Toque em **Favoritos**.
  
   ![Ícone Favoritos](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Os seus favoritos do portal Web encontram-se todos nesta página.
  
Saiba mais sobre os [favoritos nas aplicações móveis do Power BI](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Remover uma ligação para um servidor de relatório
Só se pode ligar a um servidor de relatórios de cada vez a partir da aplicação móvel do Power BI. Se quiser ligar-se a um servidor diferente, precisa de desligar-se do atual.

1. Na parte inferior do painel de navegação, toque em **Definições** ![ícone de Definições](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Toque e mantenha premido o nome do servidor ao qual não se deseja ligar.
3. Toque em **Remover servidor**.
   
    ![Remover servidor](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Criar relatórios móveis e KPIs do Reporting Services
Os KPIs e relatórios móveis do Reporting Services não são criados na aplicação móvel do Power BI. São criados no SQL Server Mobile Report Publisher e num portal Web do SQL Server 2016 Reporting Services.

* [Crie os seus relatórios móveis do Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher), e publique-os num portal Web do Reporting Services.
* Crie [KPIs num portal Web do Reporting Services](/sql/reporting-services/working-with-kpis-in-reporting-services)

## <a name="next-steps"></a>Próximos passos
* [Introdução à aplicação móvel Power BI para Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [O que é o Power BI?](../../fundamentals/power-bi-overview.md)  
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)