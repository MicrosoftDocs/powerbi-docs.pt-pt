---
title: Instalar o Power BI Desktop otimizado para o Power BI Report Server
description: Saiba como instalar o Power BI Desktop otimizado para o Power BI Report Server
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 06/20/2017
ms.author: asaxton
ms.openlocfilehash: 5fd5f41523ffcba03eb4749a9560922bcff42a7c
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2017
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Instalar o Power BI Desktop otimizado para o Power BI Report Server
Saiba como instalar o Power BI Desktop otimizado para o Power BI Report Server.

Terá de transferir e instalar o Power BI Desktop otimizado para o Power BI Report Server. Esta é uma versão diferente do Power BI Desktop que é utilizada no serviço Power BI. Isto é necessário para garantir que o servidor de relatórios pode interagir indiretamente com uma versão conhecida dos relatórios e do modelo. 

> [!NOTE]
> O Power BI Desktop e o Power BI Desktop otimizado para o Power BI Report Server podem ser instalados paralelamente.
> 
> 

## <a name="download-and-install"></a>Transferir e instalar
Pode transferir o Power BI Desktop otimizado para o Power BI Report Server do [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=837581) ou a partir do portal Web do seu servidor de relatórios.

Após transferir o instalador, pode instalar o Power BI Desktop.

## <a name="verify-you-are-using-the-correct-version"></a>Certificar-se de que está a utilizar a versão correta
Pode garantir que está a utilizar a versão correta do Power BI Desktop ao ver o ecrã inicial ou a barra de título no Power BI Desktop. A barra de título indica o mês e o ano de lançamento.

![](media/install-powerbi-desktop/powerbi-desktop-rs-title-bar.png "Barra de título do Power BI Desktop")

A versão do Power BI Desktop para o serviço Power BI não terá mês e ano na barra de título.

## <a name="file-extension-association"></a>Associação de extensões de ficheiros
Se instalou o Power BI Desktop e o Power BI Desktop otimizado para o Power BI Report Server no mesmo computador, a última instalação do Power BI Desktop terá a associação de ficheiro a .pbix. Significa que, sempre que fizer duplo clique num ficheiro pbix, será iniciado o último Power BI Desktop a ser instalado.

Se tinha o Power BI Desktop e, posteriormente, instalou o Power BI Desktop otimizado para o Power BI Report Server, todos os ficheiros pbix serão abertos no Power BI Desktop otimizado para o Power BI Report Server por predefinição. Se prefere que o Power BI Desktop seja iniciado por predefinição ao abrir um ficheiro pbix, reinstale o Power BI Desktop a partir do serviço Power BI.

Pode sempre começar por abrir a versão do Power BI Desktop que pretende utilizar. Em seguida, abra o ficheiro no Power BI Desktop.

Editar um relatório do Power BI a partir do Power BI Report Server, ou criar um novo relatório do Power BI a partir do portal Web, irá sempre abrir a versão correta do Power BI Desktop.

## <a name="next-steps"></a>Próximos passos
Agora que o Power BI Desktop está instalado, pode começar a criar relatórios do Power BI.

[Início rápido: Criar um relatório do Power BI para o Power BI Report Server](quickstart-create-powerbi-report.md)  
[Introdução ao Power BI Desktop](../desktop-getting-started.md)  
Aprendizagem guiada: [Introdução ao Power BI Desktop](../guided-learning/gettingdata.yml#step-2)  
[Descrição geral do manual de utilizador, Power BI Report Server](user-handbook-overview.md)

Mais perguntas? [Pergunte à Comunidade do Power BI](https://community.powerbi.com/)

