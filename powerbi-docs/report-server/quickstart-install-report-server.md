---
title: 'Início rápido: instalar o Power BI Report Server'
description: Instalar o Power BI Report Server é bastante rápido. Deve demorar poucos minutos da transferência à instalação e configuração.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/19/2018
ms.author: maggies
ms.openlocfilehash: 625864384f73260ec0f62b74ff9a95e966289da0
ms.sourcegitcommit: 93e7362fc47319959b6992dfd037effdf831d010
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/21/2018
---
# <a name="quickstart-install-power-bi-report-server"></a>Início rápido: instalar o Power BI Report Server
Instalar o Power BI Report Server é bastante rápido. Deve demorar poucos minutos da transferência à instalação e configuração.

Esta é uma vista rápida sobre como instalar um servidor de relatórios se pretender apenas começar a trabalhar com um novo servidor. Para obter informações mais detalhadas sobre como instalar um servidor de relatórios, veja [Instalar o Power BI Report Server](install-report-server.md).

## <a name="video-install-power-bi-report-server"></a>Vídeo: Instalar o Power BI Report Server

<iframe width="640" height="360" src="https://www.youtube.com/embed/zacaEb9A4F0?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>Antes de começar
Antes de instalar o Power BI Report Server, recomendamos que veja os [Requisitos de Software e Hardware para instalar o Power BI Report Server](system-requirements.md).

## <a name="step-1-download"></a>Passo 1: Transferir

Para transferir o Power BI Report Server e o Power BI Desktop otimizado para o Power BI Report Server, aceda a [On-premises reporting with Power BI Report Server](https://powerbi.microsoft.com/report-server/) (Relatórios no local com o Power BI Report Server) e selecione **Download free trial** (Transferir a versão de avaliação gratuita).

Siga as instruções para transferir localmente os ficheiros de instalação para o Power BI Report Server. 

![Transferir o Power BI Report Server](media/quickstart-install-report-server/download-pbireportserver.png)

## <a name="step-2-run-installer"></a>Passo 2: Executar o instalador
Execute o ficheiro PowerBIReportServer.exe que transferiu e percorra os ecrãs de instalação. Terá a oportunidade de selecionar o caminho de instalação, bem como selecionar a edição que pretende instalar. Pode optar entre uma avaliação que expira dentro de 180 dias, uma edição de programador ou fornecer uma chave de produto.

![Instalar o Power BI Report Server](media/quickstart-install-report-server/pbireportserver-install.png)

## <a name="step-3-configure-the-server"></a>Passo 3: Configurar o servidor
Após concluir a instalação, irá executar o gestor de configuração para concluir a configuração do seu servidor. Terá de criar uma base de dados de catálogo ReportServer e confirmar os URLs do serviço Web e do portal Web.

![Configurar o Power BI Report Server](media/quickstart-install-report-server/pbireportserver-configure.png)

## <a name="step-4-browse-to-web-portal"></a>Passo 4: Navegar para o portal Web
Agora que concluiu a configuração, deverá poder abrir um browser para o portal Web do seu servidor. Por predefinição, é `http://localhost/reports`. Também poderá navegar através do nome do computador, em vez de utilizar localhost por predefinição, assumindo que não está a ser bloqueado por nenhuma firewall.

![Portal Web do Power BI Report Server](media/quickstart-install-report-server/web-portal.png)

## <a name="next-steps"></a>Próximos passos
[Manual do administrador](admin-handbook-overview.md)  
[Como encontrar a sua chave de produto de servidor de relatório](find-product-key.md)  
[Instalar o Power BI Report Server](install-report-server.md)  
[Instalar o Power BI Desktop otimizado para o Power BI Report Server](install-powerbi-desktop.md)  
[Suporte do browser para o Power BI Report Server](browser-support.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

