---
title: Ver KPIs e relatórios móveis do SSRS na aplicação móvel para Windows 10 - Power BI
description: A aplicação móvel do Power BI para Windows 10 oferece acesso móvel atualizado e tátil às suas informações empresariais no local mais importantes.
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: mshenhav
ms.openlocfilehash: 4666e7c0e4901a99867ea72ab404df4cbffe110b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879359"
---
# <a name="view-reporting-services-ssrs-mobile-reports-and-kpis-in-the-windows-10-power-bi-mobile-app"></a>Ver KPIs e relatórios móveis do Reporting Services (SSRS) na aplicação móvel do Power BI para Windows 10
A aplicação móvel do Power BI para Windows 10 oferece acesso móvel atualizado e tátil às suas informações empresariais no local mais importantes no SQL Server 2016 Reporting Services. 

![Relatórios móveis do Reporting Services](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>As coisas mais importantes primeiro
[Crie relatórios móveis do Reporting Services](https://msdn.microsoft.com/library/mt652547.aspx) com o SQL Server 2016 Enterprise Edition Mobile Report Publisher e publique-os no [portal Web do Reporting Services](https://msdn.microsoft.com/library/mt637133.aspx). Crie KPIs diretamente no portal Web. Organize-os em pastas e marque os seus favoritos para que os possa encontrar facilmente. 

Depois, na aplicação móvel do Power BI para Windows 10, veja os KPIs e relatórios móveis organizados em pastas e recolhidos como favoritos. 

> [!NOTE]
> O seu dispositivo precisa de executar o Windows 10. A aplicação funciona melhor em dispositivos com, pelo menos, 1 GB de RAM e 8 GB de armazenamento interno.
> 
> 

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Explorar exemplos sem um servidor do SQL Server 2016 Reporting Services
Mesmo que não tenha acesso a um portal Web do Reporting Services, ainda pode explorar as funcionalidades dos relatórios móveis do Reporting Services.

1. No seu dispositivo Windows 10, abra a aplicação do Power BI.
2. Toque no botão de navegação global ![Botão de navegação global](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) no canto superior esquerdo.
3. Toque no ícone das **Definições** ![Ícone Definições](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), clique com o botão direito do rato ou mantenha premido **Ligar ao servidor** e, em seguida, toque em **Ver exemplos**.
   
   ![Ver exemplos do SSRS](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Abra a pasta Relatórios de Revenda ou Relatórios de Vendas para explorar os respetivos KPIs e relatórios móveis.
   
   ![Relatórios móveis e KPIs de exemplo](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Procure exemplos para interagir com KPIs e relatórios móveis.

## <a name="connect-to-a-reporting-services-report-server"></a>Ligar a um servidor de relatórios do Reporting Services
1. Na parte inferior do painel de navegação, toque em **Definições** ![ícone de Definições](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)
2. Toque em **Ligar ao servidor**.
3. Preencha o endereço do servidor e o seu nome de utilizador e palavra-passe. Utilize este formato para o endereço do servidor:
   
     `https://<servername>/reports` OU   `https://<servername>/reports`
   
   > [!NOTE]
   > Inclua **http** ou **https**no início da cadeia de ligação.
   > 
   > 
   
    Toque em **Opções avançadas** para, se pretender, atribuir um nome ao servidor.
4. Toque na marca de verificação para ligar. 
   
   Agora pode ver o servidor no painel de navegação.
   
   ![Servidor no painel de navegação](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Toque no botão de navegação global ![Botão de navegação global](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) a qualquer altura para alternar entre os seus relatórios móveis do Reporting Services e os dashboards no serviço Power BI. 
   > 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Ver KPIs e relatórios móveis do Reporting Services na aplicação do Power BI
Os KPIs e os relatórios móveis do Reporting Services móveis são mostrados nas mesmas pastas em que estão contidos no portal da Web do Reporting Services.

![Pastas de relatórios](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Toque num KPI para vê-lo no modo de foco.
  
    ![KPI no modo de detalhe](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Toque num relatório móvel para abri-lo e interagir com ele na aplicação do Power BI.
  
    ![Relatório móvel do Reporting Services](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Ver os seus KPIs e relatórios favoritos
Pode marcar KPIs e relatórios móveis como favoritos no portal Web do Reporting Services e, em seguida, vê-los numa pasta conveniente no seu dispositivo Windows 10, juntamente com os seus dashboards e relatórios favoritos do Power BI.

* Toque em **Favoritos**.
  
   ![Ícone Favoritos](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Os seus favoritos do portal Web encontram-se todos nesta página.
  
   ![Página Favoritos](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-favorites.png)

Saiba mais sobre os [favoritos nas aplicações móveis do Power BI](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Remover uma ligação para um servidor de relatório
Só se pode ligar a um servidor de relatórios de cada vez a partir da aplicação móvel do Power BI. Se quiser ligar-se a um servidor diferente, precisa de desligar-se do atual.

1. Na parte inferior do painel de navegação, toque em **Definições** ![ícone de Definições](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Toque e mantenha premido o nome do servidor ao qual não se deseja ligar.
3. Toque em **Remover servidor**.
   
    ![Remover servidor](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Criar relatórios móveis e KPIs do Reporting Services
Os KPIs e relatórios móveis do Reporting Services não são criados na aplicação móvel do Power BI. São criados no SQL Server Mobile Report Publisher e num portal Web do SQL Server 2016 Reporting Services.

* [Crie os seus relatórios móveis do Reporting Services](https://msdn.microsoft.com/library/mt652547.aspx), e publique-os num portal Web do Reporting Services.
* Crie [KPIs num portal Web do Reporting Services](https://msdn.microsoft.com/library/mt683632.aspx)

## <a name="next-steps"></a>Próximos passos
* [Introdução à aplicação móvel Power BI para Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [O que é o Power BI?](../../fundamentals/power-bi-overview.md)  
* Perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

