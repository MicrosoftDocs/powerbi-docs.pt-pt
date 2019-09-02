---
title: Ligar-se ao SendGrid com o Power BI
description: SendGrid para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a05d78cfb0c1e34f0ec263f5455982cd4064905b
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185836"
---
# <a name="connect-to-sendgrid-with-power-bi"></a>Ligar-se ao SendGrid com o Power BI
O pacote de conteúdos do SendGrid para o Power BI permite que possa extrair informações e estatísticas da sua conta do SendGrid. Com o pacote de conteúdos do SendGrid, é possível ver as estatísticas do SendGrid num dashboard.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Ligue-se ao [pacote de conteúdos do SendGrid](https://app.powerbi.com/getdata/services/sendgrid) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. Selecione o pacote de conteúdos do **SendGrid** e clique em **Obter**.
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. Quando solicitado, forneça o seu nome de utilizador e palavra-passe do SendGrid. Selecione **Entrar**.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. Depois do Power BI importar os dados, vai ver um dashboard, relatório e conjunto de dados novos no painel de navegação esquerdo, preenchidos com as suas estatísticas de e-mail correspondentes aos últimos 90 dias. Os novos itens são marcados com um asterisco amarelo \*.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**O que se segue?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento das atualizações ou tentar atualizá-lo a pedido através da opção **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
As métricas a seguir estão disponíveis no dashboard do SendGrid:

* Estatísticas globais de e-mail - Solicitações, Entregues, Devolvidos, Bloqueados por Spam, Relatório de Spam, etc.
* Estatísticas de e-mail por categoria
* Estatísticas de e-mail por geografia
* Estatísticas de e-mail por ISP
* Estatísticas de e-mail por dispositivo, cliente ou browser

## <a name="next-steps"></a>Próximos passos
[O que é o Power BI?](power-bi-overview.md)

[Obter Dados](service-get-data.md)

