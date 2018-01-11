---
title: Ligue-se ao Office365Mon com o Power BI
description: Office365Mon para o Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 62d3b23417c1d9d4e3909ec24c6ada864bcb056a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-office365mon-with-power-bi"></a>Ligue-se ao Office365Mon com o Power BI
Analisar os seus dados de desempenho de estado de funcionamento e interrupções do Office 365 é fácil com o Power BI e o pacote de conteúdos Office365Mon. O Power BI recupera os seus dados, incluindo investigações de integridade e interrupções e, em seguida, compila um dashboard e relatórios prontos para uso com base nesses dados.

Ligue-se ao pacote de conteúdo [Office365Mon](https://app.powerbi.com/groups/me/getdata/services/office365mon) para Power BI.

>[!NOTE]
>É necessária uma conta de administrador do Office365Mon para ligar e carregar o pacote de conteúdo do Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Selecione **Office365Mon** \> **Obter**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. Como Método de Autenticação, selecione **oAuth2** \> **Iniciar Sessão**.
   
   Quando solicitado, insira as suas credenciais de administrador do Office365Mon e siga o processo de autenticação.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Após o Power BI importar os dados, verá novos elementos (dashboard, relatório e conjunto de dados) no painel de navegação esquerdo. Os novos itens são marcados com um asterisco amarelo \*; selecione a entrada do Office365Mon.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de Perguntas e Respostas](service-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="troubleshooting"></a>Resolução de problemas
Se receber um erro **"falha no inicio de sessão"** depois de usar as credenciais de subscrição do Office365Mon para iniciar sessão, a conta utilizada não tem permissões para recuperar os dados do Office365Mon da conta. Verifique se é uma conta de administrador e tente novamente.

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Obter Dados para o Power BI](service-get-data.md)

