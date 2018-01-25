---
title: Ligar ao MailChimp com o Power BI
description: MailChimp para Power BI
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
ms.openlocfilehash: 5a0935d9401841ee2db71fdf821621ababdd01cb
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-mailchimp-with-power-bi"></a>Ligar ao MailChimp com o Power BI
O pacote de conteúdos do Power BI extrai dados da sua conta do MailChimp e gera um dashboard, um conjunto de relatórios e um conjunto de dados para permitir que explore os seus dados. Utilize a análise para [dashboards do MailChimp](https://powerbi.microsoft.com/integrations/mailchimp) para identificar rapidamente as tendências existentes nas suas campanhas, relatórios e subscritores individuais. Os dados são configurados para serem atualizados diariamente, o que garante que os dados que está a monitorizar são atuais.

Ligue-se ao [pacote de conteúdo do MailChimp](https://app.powerbi.com/getdata/services/mailchimp) para o Power BI.

## <a name="how-to-connect"></a>Como se ligar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-mailchimp/pbi_getdata.png)
2. Na caixa **Serviços**, selecione **Obter**.
   
   ![](media/service-connect-to-mailchimp/pbi_getservices.png)
3. Selecione **MailChimp** \> **Obter**.
   
   ![](media/service-connect-to-mailchimp/mailchimp.png)
4. Como Método de Autenticação, selecione **oAuth2** \> **Iniciar Sessão**.
   
    Quando solicitado, insira as suas credenciais do MailChimp e siga o processo de autenticação.
   
    Na primeira vez que se ligar, o Power BI solicita o acesso apenas de leitura à sua conta. Selecione **Permitir** para iniciar o processo de importação, que pode demorar alguns minutos dependendo do volume de dados na conta.
   
    ![](media/service-connect-to-mailchimp/allow.png)
5. Após o Power BI importar os dados, verá novos elementos (dashboard, relatório e conjunto de dados) no painel de navegação esquerdo. Esse é o dashboard padrão criado pelo Power BI para exibir os seus dados. Pode alterar este dashboard para ver os seus dados de qualquer modo que queira.
   
   ![](media/service-connect-to-mailchimp/pbi_mailchimpnewdash.png)

**E agora?**

* Experimente [fazer uma pergunta na caixa de Perguntas e Respostas](power-bi-q-and-a.md) na parte superior do dashboard
* [Altere os mosaicos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um mosaico](service-dashboard-tiles.md) para abrir o relatório subjacente.
* Embora o seu conjunto de dados seja agendado para atualizações diárias, pode alterar o agendamento de atualização ou tentar atualizá-lo a pedido através de **Atualizar Agora**

## <a name="next-steps"></a>Próximos passos
[Introdução ao Power BI](service-get-started.md)

[Power BI - Conceitos Básicos](service-basic-concepts.md)

