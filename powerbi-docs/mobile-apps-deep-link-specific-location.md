---
title: Criar uma ligação para uma localização específica nas aplicações móveis do Power BI
description: Saiba como criar uma ligação avançada para um dashboard, mosaico ou relatório específico na aplicação móvel do Power BI com um identificador de recurso uniforme (URI).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 3be6882219e23a2d22ee03e6805ce3a1e8e08b8f
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Criar uma ligação para uma localização específica nas aplicações móveis do Power BI
Pode criar e utilizar um identificador de recurso uniforme (URI) para ligar para uma localização específica (*ligação avançada*) nas aplicações móveis do Power BI em todas as plataformas móveis: iOS, dispositivos Android e Windows 10.

As ligações de URI podem apontar diretamente para dashboards, mosaicos e relatórios.

O destino da ligação avançada determina o formato do URI. Siga estes passos para criar ligações avançadas para localizações diferentes. 

## <a name="open-the-power-bi-mobile-app"></a>Abra a aplicação móvel do Power BI
Utilize este URI para abrir a aplicação móvel do Power BI em qualquer dispositivo:

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>Abrir num dashboard específico
Este URI abre a aplicação móvel do Power BI num dashboard específico:

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

Para encontrar o ID de objeto do dashboard, de 36 carateres, navegue para o dashboard específico no serviço Power BI (https://powerbi.com). Por exemplo, consulte a secção realçada deste URL:

https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**

Se o dashboard estiver num grupo que não A Minha Área de Trabalho, adicione `&GroupObjectId=<36-character-group-id>` antes ou depois do ID de dashboard. Por exemplo, 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Note a existência de um e comercial (&) entre os dois.

## <a name="open-to-a-specific-tile-in-focus"></a>Abrir com um mosaico específico em foco
Este URI abre um mosaico específico em foco na aplicação móvel do Power BI:

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

Para encontrar os IDs de objeto de mosaico e dashboard, de 36 carateres, navegue para o dashboard específico no serviço Power BI (https://powerbi.com) e abra o mosaico em modo de detalhe. Por exemplo, consulte as secções realçadas deste URL:

https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

Para este mosaico, o URI seria:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

Note a existência de um e comercial (&) entre os dois.

Se o dashboard estiver num grupo que não A Minha Área de Trabalho, adicione `&GroupObjectId=<36-character-group-id>`

## <a name="open-to-a-specific-report"></a>Abrir num relatório específico
Este URI abre um relatório específico na aplicação móvel do Power BI:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

Para encontrar o ID de objeto do relatório, de 36 carateres, navegue para o relatório específico no serviço Power BI (https://powerbi.com). Por exemplo, consulte a secção realçada deste URL:

https://powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

## <a name="open-to-a-specific-report-page"></a>Abrir numa página de relatório específica
Este URI abre uma página de relatório específica na aplicação móvel do Power BI:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

A página de relatório tem o nome "ReportSection", seguido de um número. Novamente, abra o relatório no serviço Power BI (https://powerbi.com) e navegue para a página de relatório específica. 

Por exemplo, consulte a secção realçada deste URL:

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**ReportSection11**

## <a name="open-in-full-screen-mode"></a>Abrir em modo de ecrã inteiro
Adicione o parâmetro a negrito para abrir um relatório específico no modo de ecrã inteiro:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

Por exemplo: 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>Adicionar contexto (opcional)
Também pode adicionar contexto na cadeia. Depois, se precisar de nos contactar, poderemos utilizar esse contexto para filtrar os nossos dados para a sua aplicação. Adicione `&context=<app-name>` à ligação

Por exemplo, consulte a secção realçada deste URL: 

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**&context=SlackDeepLink**

## <a name="next-steps"></a>Próximos passos
Os seus comentários ajudam-nos a decidir o que implementar no futuro, portanto, não se esqueça de votar noutros recursos que gostaria de ver nas aplicações móveis do Power BI. 

* [Aplicações do Power BI para dispositivos móveis](mobile-apps-for-mobile-devices.md)
* Siga o @MSPowerBI no Twitter
* Participe na conversa na [Comunidade do Power BI](http://community.powerbi.com/)
* [Introdução ao Power BI](service-get-started.md)

