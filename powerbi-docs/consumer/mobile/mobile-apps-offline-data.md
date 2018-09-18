---
title: Ver os dados offline em aplicações móveis do Power BI
description: 'Leia sobre uma vantagem da visualização do Power BI numa aplicação móvel em vez de num navegador móvel: pode ver os dados mesmo quando não estiver ligado a uma rede.'
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: maggies
ms.openlocfilehash: 2c980878f70d8cf6368b446c8ed8a2207d0b7acd
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44744224"
---
# <a name="view-your-data-offline-in-the-power-bi-mobile-apps"></a>Ver os dados offline em aplicações móveis do Power BI
Aplica-se a:

| ![iPhone](./media/mobile-apps-offline-data/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-offline-data/ipad-logo-50-px.png) | ![Telemóvel Android](./media/mobile-apps-offline-data/android-phone-logo-50-px.png) | ![Tablet Android](./media/mobile-apps-offline-data/android-tablet-logo-50-px.png) | ![Windows 10](./media/mobile-apps-offline-data/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Telemóveis Android |Tablets Android |Dispositivos Windows 10 |

Uma vantagem da visualização do Power BI numa aplicação móvel em vez de num navegador móvel é que pode ver os dados mesmo quando não estiver ligado a uma rede. 

![Nenhuma mensagem de rede](./media/mobile-apps-offline-data/power-bi-iphone-no-network.png)

Por predefinição, o Power BI atualiza os dados com frequência para que obtenha respostas atualizadas para as suas questões de negócios a qualquer momento, mesmo durante o transporte ou viagens.

## <a name="data-access-while-youre-offline"></a>Acesso a dados enquanto estiver offline
Enquanto estiver offline, pode aceder e interagir com dashboards a que tenha acedido anteriormente a partir da aplicação móvel.

Também tem acesso só de leitura a todos os relatórios do Power BI a que tiver acedido anteriormente a partir da aplicação móvel. Pode ver o relatório completo, mas não filtrar, fazer filtragem cruzada, classificar ou utilizar segmentações de dados nele.

## <a name="background-data-refresh"></a>Atualização de dados em segundo plano
A atualização em segundo plano atualiza os seus dashboards favoritos, bem como os dashboards e relatórios que visualizou nas duas últimas semanas, com os dados do serviço Power BI (não da origem de dados). Se estiver ligado ao Wi-Fi, a atualização em segundo plano atualiza a cada 2 horas. Caso contrário, se estiver numa rede 3G, o Power BI atualiza o conteúdo a cada 24 horas.

Pode desativar a atualização agendada, por exemplo, para evitar a utilização da rede. Verifique as configurações do dispositivo.

> [!NOTE]
> Se utiliza a aplicação móvel do Power BI no seu dispositivo iOS e a sua organização configurou o MAM do Microsoft Intune, a atualização de dados em segundo plano está desativada. Na próxima vez que entrar na aplicação, o Power BI atualiza os dados do serviço Power BI na Web.
> 
> Saiba mais sobre como [configurar as aplicações móveis do Power BI com o Microsoft Intune](../../service-admin-mobile-intune.md). 
> 
> 

## <a name="offline-indicators"></a>Indicadores offline
O Power BI fornece indicadores claros quando entrar e sair do modo offline, assim como indicadores de dashboards, relatórios e mosaicos ausentes que não estão disponíveis offline.

## <a name="limitations"></a>Limitações
Quando estiver offline com o Power BI no dispositivo móvel, pode encontrar estas limitações:

* O Power BI pode armazenar em cache até 250 MB de dados offline.
* Alguns tipos de mosaico exigem uma ligação de servidor ativa. Por conseguinte, não estão disponíveis offline; por exemplo, mosaicos do Bing e alguns mosaicos personalizados.
* Livros inteiros do Excel no Power BI não estão disponíveis offline.
* Pode ver relatórios móveis do Reporting Services e KPIs offline, se os tiver visualizado enquanto esteve ligado. Não são atualizados em segundo plano. São atualizados sempre que os abrir.
* Nas aplicações móveis do Power BI, não pode ver os ficheiros do Power BI Desktop (.pbix) guardados no Power BI Report Server. 

## <a name="next-steps"></a>Próximos passos
Os seus comentários ajudam-nos a decidir o que implementar no futuro, portanto, não se esqueça de votar noutros recursos que gostaria de ver nas aplicações móveis do Power BI. 

* [Aplicações do Power BI para dispositivos móveis](mobile-apps-for-mobile-devices.md)
* Siga o @MSPowerBI no Twitter
* Participe na conversa na [Comunidade do Power BI](http://community.powerbi.com/)
* [O que é o Power BI?](../../power-bi-overview.md)

